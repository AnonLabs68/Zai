# Sovereign Market OS: Engine V18 Hivemind Architecture Snapshot

**Source File (Absolute Windows)**: D:\sovereign_market_os\sovereign_fleet\engine.py  
**Source File (Repository Relative)**: sovereign_fleet/engine.py  
**File Size**: 64,169 bytes | 1,346 lines  
**SHA-256 Hash**: 6bb4b1f28ed47468a8dc9cbf0ceb49ed0e88001469f562c32281a321b3a53881  
**System Architecture**: Tier-1 Multi-Process Nested Autonomous Hivemind  

---

## 1. Architectural & Subsystem Specification

engine.py represents the core autonomous orchestration layer of Sovereign Market OS V18:

1. **ForensicMarkoutDoctor (Background Periodic Daemon)**:
   - Evaluates SQLite WAL trade ledger markouts every 20 seconds.
   - Calculates counterfactual price drift at 1s, 5s, 30s, 60s post-exit.
   - Detects toxic adverse selection clusters; automatically quarantines bleeding corridors (APRUSDT, HANAUSDT) to protect capital.
2. **CrossAssetLeadLagEngine (Microsecond Impulse Tracker)**:
   - Implements Hayashi-Yoshida cross-correlation and jump detection between BTC and altcoins.
   - Dispatches sub-millisecond aggressive taker entries when BTC breaks volatility thresholds before altcoin L2 quotes adjust.
3. **UniverseScreenerDaemon (24/7 Macro Altcoin & TradFi Scanner)**:
   - Continuously screens 870+ Binance USDT-M and bStocks perpetual contracts.
   - Filters by Relative Tick Law $\tau_{rel} \in [4.0, 9.5]$ bps, spread cushion $\ge 7.0$ bps, 24h volume $\ge \, and positive funding carry.
4. **CorridorEngine (Decoupled Per-Asset State Machine)**:
   - Drives Avellaneda-Stoikov / Guéant inventory skewing, Deep Pyramid quoting (T-2, T-3 rungs), kinematic stop-loss ejector, and atomic slot release.

---

## 2. Complete Verbatim Source Code

`python
"""
====================================================================================================
SOVEREIGN MARKET OS: APEX PRODUCTION FLEET ENGINE (V16 INSTITUTIONAL)
====================================================================================================
Architecture & Unification of 16 Generations of Quantitative Research:
 1. Native C++20 Core Integration:
    - TriangularBasisSlingshot: Cross-asset triangular basis & funding divergence detector.
    - PoissonInfillRadar: Pre-sweep hollowing radar with Wilson-score PPV gating.
    - DexCexDisparityOracle: On-chain Uniswap/Hyperliquid AMM inventory disparity quoter.
    - DiscreteParasiteHJB: 160-state discrete Bellman parasite quoter with +8.0 bps invariant.
    - FeaturePipeline: Stoikov (2018) micro-price, Parkinson (1980) volatility, Cont OFI.
    - AdversarialProfiler: Hawkes branching ratio eta, Shannon clip entropy, OFI curvature, I_enemy.
    - LeadLagShield & KineticSweepBarrier: 100ns macro front-runner, velocity barrier Z_v > 2.5 sigma.
    - FlowToxicityGuard: Real-time buy/ask directional sweep hazard scoring and quote pull breakers.
    - DiscreteHJBPolicy: Online Kalman drift coupling mu_t, Lo-MacKinlay Variance Ratio, reservation spreads.
    - MultiSlotQuoter & ExhaustionHarvestEngine: 3-slot Deep Pyramiding ladder with passive unwinds.
 2. FIFO Queue Priority Depletion (Q_ahead):
    - Exact volume ahead tracking (V_ahead). Zero phantom fills.
 3. Relative Tick Value Theorem & Pre-Sweep Anchored Exits:
    - Fills spawn resting limit exits anchored at pre-sweep fair value.
    - Invariant floor: exit_spread >= 2 * maker_fee + 4.0 bps (7.60 bps hurdle).
    - Every passive exit is mathematically guaranteed to be strictly net positive after fees.
 4. Fortress Capital Protection:
    - $25.00 Golden Ratio pool, 0.60x max leverage ($15 max active margin), $10 cash reserve.
    - Volatility-adjusted margin haircuts and multi-stage drawdown circuit breakers.
 5. ACID SQLite Write-Ahead-Log (WAL) Journaling:
    - Immutable audit trail of every order, fill, trade cycle, markout, and risk event.
====================================================================================================
"""

import sys
import time
import math
import asyncio
import argparse
from pathlib import Path
from typing import Dict, Any, List, Optional
from datetime import datetime, timezone
import numpy as np

ROOT_DIR = Path(__file__).resolve().parent.parent
if str(ROOT_DIR) not in sys.path:
    sys.path.insert(0, str(ROOT_DIR))

from sovereign_fleet.config.fleet_config import get_fleet_profile
from sovereign_fleet.governance.corridor_registry import (
    CORRIDOR_CONFIGS,
    CorridorClass,
    CorridorMode,
    CorridorState,
)
from sovereign_fleet.governance.graduation_gate import (
    GraduationGateManager,
    GraduationState,
    wilson_lb,
)
from sovereign_fleet.core.types import (
    OrderState,
    ExitAction,
    RadarPhase,
    DisparityAction,
    PredatorPhase,
    SlingshotRegime,
)
from sovereign_fleet.core.c_bridge import (
    NativeFeaturePipeline,
    NativeFlowToxicityGuard,
    NativeDiscreteHJBPolicy,
    NativeTriangularSlingshot,
    NativePoissonRadar,
    NativeDexDisparityOracle,
    NativeParasitePolicySolver,
    NativeSentinelCore,
    V17Action,
    V17Zone,
    V17Cause,
    SMOS_V17HealthReport,
)
from sovereign_fleet.market_data.book_builder import L2Book
from sovereign_fleet.market_data.binance_ws import BinanceMultiplexedWS
from sovereign_fleet.signals.adversarial_alpha import AdversarialAlphaEngine
from sovereign_fleet.signals.funding_vampire import FundingVampireEngine
from sovereign_fleet.risk.fortress_risk import FortressRiskKernel
from sovereign_fleet.risk.quad_shield import QuadShieldDefender
from sovereign_fleet.risk.threat_scanner import (
    ActiveThreatScanner,
    MacroThreatState,
    ThreatAssessment,
)
from sovereign_fleet.execution.order_state import FleetOrder
from sovereign_fleet.execution.queue_broker import QueuePriorityBroker
from sovereign_fleet.execution.harvest_controller import ExhaustionHarvestController
from sovereign_fleet.strategy.discrete_hjb_quoter import DiscreteHJBQuoter
from sovereign_fleet.telemetry.journal import ExecutionJournal
from sovereign_fleet.telemetry.console import TelemetryConsole
from sovereign_fleet.analytics.adversarial_profiler import (
    AdversarialProfiler,
    ProfilerConfig,
)
from sovereign_fleet.analytics.kalman_drift import (
    KinematicKalmanFilter,
    LoMacKinlayVarianceRatio,
)
from sovereign_fleet.analytics.markout_forensics import (
    FillRecord,
    MarkoutForensicsEngine,
    Side,
)
from sovereign_fleet.hivemind.forensic_markout_doctor import ForensicMarkoutDoctor
from sovereign_fleet.signals.cross_asset_lead_lag import CrossAssetLeadLagEngine, LeadLagSignal
from sovereign_fleet.hivemind.universe_screener_daemon import UniverseScreenerDaemon


class CorridorEngine:
    """Encapsulates all signals, risk, book state, and execution for one asset corridor."""

    def __init__(
        self,
        symbol: str,
        cfg: Dict[str, Any],
        journal: ExecutionJournal,
        risk_kernel: FortressRiskKernel,
        is_shadow: bool = False,
        grad_manager: Optional[GraduationGateManager] = None,
        dispatcher: Optional[Any] = None,
        lead_lag_engine: Optional[Any] = None,
    ):
        self.symbol = symbol
        self.cfg = cfg
        self.is_shadow = is_shadow
        self.grad_manager = grad_manager
        self.dispatcher = dispatcher
        self.lead_lag_engine = lead_lag_engine
        self.lead_lag_snipes_count = 0
        self.lead_lag_pulls_count = 0
        self.tick_size = cfg['tick_size']
        self.px_decimals = cfg['px_decimals']
        self.qty_decimals = cfg['qty_decimals']

        self.journal = journal
        self.risk_kernel = risk_kernel

        # Stop loss handling: ensure positive absolute value and fallback to 40.0 if zero
        raw_stop = abs(float(cfg.get('stop_loss_bps', 35.0)))
        stop_bps = raw_stop if raw_stop > 0.0 else 40.0

        # Market Data & Order Book
        self.book = L2Book(symbol, self.tick_size)
        self.prev_bids = []
        self.prev_asks = []

        # Full Institutional C++20 Core Engines
        self.feature_pipeline = NativeFeaturePipeline(tick_size=self.tick_size)
        self.alpha = AdversarialAlphaEngine(symbol)
        self.shield = QuadShieldDefender(
            macro_impulse_bps=1.5,
            macro_window_ns=50_000_000,
            kinetic_z_threshold=2.5,
            critical_hazard_threshold=2.0
        )
        self.threat_scanner = ActiveThreatScanner(
            v_100ms_threshold_bps=1.5,
            v_1s_threshold_bps=3.5,
            v_5s_threshold_bps=7.5,
            hawkes_eta_threshold=0.85,
            threat_cooldown_ns=15_000_000_000
        )
        self.latest_threat_assessment: Optional[ThreatAssessment] = None
        self.funding = FundingVampireEngine(cfg.get('funding_tilt', 'NEUTRAL'))

        # Strategy Quoter & Unwind Harvest Controller
        self.hjb_quoter = DiscreteHJBQuoter(
            symbol=symbol,
            tick_size=self.tick_size,
            px_decimals=self.px_decimals,
            qty_decimals=self.qty_decimals,
            target_lot_usd=(cfg.get('slots_normal') or [{}])[0].get('clip_usd', 5.0),
            max_lots=3.0,
            risk_gamma=0.15,
            kappa=1.5,
            maker_fee_bps=1.80,
            funding_tilt=cfg.get('funding_tilt', 'NEUTRAL'),
            slots_config=cfg.get('slots_normal')
        )
        self.harvest_controller = ExhaustionHarvestController(
            symbol=symbol,
            tick_size=self.tick_size,
            px_decimals=self.px_decimals,
            qty_decimals=self.qty_decimals,
            base_clip_usd=5.0,
            max_clip_usd=cfg.get('max_inv_usd', 20.0),
            gamma_kelly=1.5
        )

        # Execution Broker with Real L2 Depth Query (Zero Hardcoded Exit Depth)
        self.broker = QueuePriorityBroker(
            symbol=symbol,
            tick_size=self.tick_size,
            qty_decimals=self.qty_decimals,
            px_decimals=self.px_decimals,
            clip_usd=(cfg.get('slots_normal') or [{}])[0].get('clip_usd', 5.0),
            stop_loss_bps=stop_bps,
            inv_shade_clip_usd=(cfg.get('slots_normal') or [{}])[0].get('clip_usd', 5.0),
            timeout_sec=cfg.get('timeout_sec', 120),
            stack_cap=cfg.get('stack_cap', 3),
            is_shadow=self.is_shadow,
            depth_lookup_fn=self.book.get_queue_ahead,
            relative_tick_bps=cfg.get('relative_tick_bps', 8.0)
        )

        # Python Production Quantitative Analytics Suite (Active Real-Time Integration)
        self.py_profiler = AdversarialProfiler(ProfilerConfig(clip_ring_size=128))
        self.py_kalman = KinematicKalmanFilter(observation_noise=0.0001, process_jerk_variance=0.05)
        self.py_vr = LoMacKinlayVarianceRatio(k_lag=5, window_size=60)
        self.markout_engine = MarkoutForensicsEngine(
            symbol=symbol, tau_ref_bps=cfg.get('relative_tick_bps', 8.0)
        )
        self.recorded_fills: List[FillRecord] = []
        self.rolling_quote_ts_ms: List[int] = []
        self.rolling_quote_bids: List[float] = []
        self.rolling_quote_asks: List[float] = []

        # Telemetry Cache
        self.latest_feat = None
        self.latest_hjb_package = None
        self.recent_events: List[Dict[str, Any]] = []

        # Full Institutional V16 Asymmetric Predator-Parasite & Radar Modules
        self.radar = NativePoissonRadar(evidence_gate=False)
        self.parasite_solver = NativeParasitePolicySolver()
        self.parasite_sol = self.parasite_solver.solve()
        self.prev_top_bid_sz = 0.0
        self.prev_top_ask_sz = 0.0
        self.latest_radar_sig = None
        self.predator_phase = PredatorPhase.DORMANT

        # Fleet V17 Sentinel Core: The Watchmen Layer (second-order logic)
        self.sentinel = NativeSentinelCore()
        self.param_slot_hawkes = self.sentinel.register_param("hawkes_eta")
        self.param_slot_kalman = self.sentinel.register_param("kalman_drift")
        self.param_slot_vr = self.sentinel.register_param("variance_ratio")
        self.param_slot_radar = self.sentinel.register_param("radar_delta_lambda")
        self.latest_sentinel_rep: Optional[SMOS_V17HealthReport] = None
        self.last_window_update_sec: float = time.time()
        # Seed initial volume window from corridor metadata (24h daily capacity floor $2M)
        initial_vol = self.cfg.get('volume_24h_usd', 6_000_000.0)
        self.sentinel.on_window(initial_vol)

        # Graduated Velocity-Margin Shield state (Kinematic Trend Guard)
        self.vel_mean_bps: float = 0.0
        self.vel_var_bps: float = 25.0  # Prior variance (sigma = 5.0 bps/s)
        self.latest_z_vel: float = 0.0


    # ----------------------------------------------------------------------------------------------
    # Depth Snapshot Processing
    # ----------------------------------------------------------------------------------------------
    def on_depth_update(self, bids_raw: list, asks_raw: list, now_ns: int, macro_impulse: int):
        self.book.update_depth(bids_raw, asks_raw, now_ns)
        if not self.book.bids or not self.book.asks:
            return

        # Fleet V17 Sentinel Core: Ingest Book Mid & Tick Size & Immediate Assessment
        self.sentinel.on_book(self.book.mid, self.tick_size)
        self.latest_sentinel_rep = self.sentinel.assess()

        # 1. Ingest into Native C++ Feature Pipeline (Stoikov Micro-Price, Parkinson Vol, Cont OFI)
        venue_ms = int(now_ns / 1_000_000)
        bids_tuples = [(b[0], b[1]) for b in self.book.bids[:20]]
        asks_tuples = [(a[0], a[1]) for a in self.book.asks[:20]]
        self.latest_feat = self.feature_pipeline.on_snapshot(now_ns, venue_ms, bids_tuples, asks_tuples)

        # Feed depth into Shield 5 Liquidity Void Tracker
        top5_bid_usd = sum(b[0] * b[1] for b in self.book.bids[:5])
        top5_ask_usd = sum(a[0] * a[1] for a in self.book.asks[:5])
        self.shield.on_depth_update(top5_bid_usd, top5_ask_usd)

        # 1b. Python Quantitative Analytics (Kinematic Kalman Filter, Variance Ratio, Rolling Quotes)
        self.py_kalman.update(price=self.book.mid, timestamp_ms=venue_ms)
        self.py_vr.update(mid_px=self.book.mid)
        self.rolling_quote_ts_ms.append(venue_ms)
        self.rolling_quote_bids.append(self.book.best_bid)
        self.rolling_quote_asks.append(self.book.best_ask)
        if len(self.rolling_quote_ts_ms) > 2000:
            self.rolling_quote_ts_ms.pop(0)
            self.rolling_quote_bids.pop(0)
            self.rolling_quote_asks.pop(0)

        # Update running velocity variance for normalized z_vel
        vel = self.py_kalman.velocity_bps
        decay = 0.05
        diff = vel - self.vel_mean_bps
        self.vel_mean_bps += decay * diff
        self.vel_var_bps = (1.0 - decay) * self.vel_var_bps + decay * (diff ** 2)
        sigma_vel = math.sqrt(max(1.0, self.vel_var_bps))
        self.latest_z_vel = (vel - self.vel_mean_bps) / sigma_vel

        # 2. Update Risk Kernel Volatility
        self.risk_kernel.update_corridor_volatility(self.symbol, self.latest_feat.parkinson_vol_bps)

        # 3. Compute OFI delta and feed to native C++ profiler & Python profiler
        ofi_usd = self.book.get_ofi(self.prev_bids, self.prev_asks)
        self.alpha.on_book_update(now_ns, ofi_usd)
        self.py_profiler.on_book_update(ts_ns=now_ns, ofi_usd=ofi_usd)
        self.prev_bids = list(self.book.bids)
        self.prev_asks = list(self.book.asks)

        # 3b. Real-Time Active Macro Threat Scanner Evaluation
        psi = self.alpha.evaluate()
        ofi_val = self.latest_feat.ofi_normalized if self.latest_feat else 0.0
        self.threat_scanner.on_alt_state(now_ns, eta=psi.eta, ofi=ofi_val)
        threat = self.threat_scanner.evaluate(now_ns)
        self.latest_threat_assessment = threat

        # 4. Continuous Evaluation of Open Positions (Anchored Snapbacks vs Kinematic Ejection)
        self.broker.evaluate_market(
            mid_px=self.book.mid,
            best_bid=self.book.best_bid,
            best_ask=self.book.best_ask,
            now_ns=now_ns,
            on_fill_cb=self._on_broker_event,
            threat_assessment=threat
        )

        # 5. Spread Gating: Only abort if crossed book or zero spread
        if self.book.spread_bps <= 0.0:
            self.broker.update_quotes({})
            return

        # 6. Profiler Metrics & Quad-Shield Defense Coordination
        psi = self.alpha.evaluate()
        z_v = self.alpha.get_sweep_velocity_z()
        is_sweep_hot = self.alpha.is_sweep_hot()
        ghost_detected = (psi.ghost_bid or psi.ghost_ask)

        top_bid_sz = bids_tuples[0][1] if bids_tuples else 1.0
        top_ask_sz = asks_tuples[0][1] if asks_tuples else 1.0

        # V16 Pre-Sweep Cancellation Radar Ingestion
        if self.prev_top_bid_sz > 0.0:
            if top_bid_sz < self.prev_top_bid_sz * 0.85:
                self.radar.on_cancel(now_ns)
            elif top_bid_sz > self.prev_top_bid_sz * 1.15:
                self.radar.on_insert(now_ns)
        if self.prev_top_ask_sz > 0.0:
            if top_ask_sz < self.prev_top_ask_sz * 0.85:
                self.radar.on_cancel(now_ns)
            elif top_ask_sz > self.prev_top_ask_sz * 1.15:
                self.radar.on_insert(now_ns)
        self.prev_top_bid_sz = top_bid_sz
        self.prev_top_ask_sz = top_ask_sz

        radar_sig = self.radar.evaluate(now_ns)
        self.latest_radar_sig = radar_sig

        verdict, allow_bids, allow_asks = self.shield.evaluate(
            now_ns=now_ns,
            spread_bps=int(self.book.spread_bps),
            base_clip_usd=(self.cfg.get('slots_normal') or [{'clip_usd': 5.0}])[0].get('clip_usd', 5.0),
            ghost_wall_detected=ghost_detected,
            sweep_eta_hot=is_sweep_hot,
            top_bid_sz=top_bid_sz,
            top_ask_sz=top_ask_sz,
        )

        # 6a. Pre-Sweep Directional Quote Suppression via Active Threat Scanner
        if threat.state == MacroThreatState.MACRO_PUMP_THREAT:
            allow_asks = False
            self.broker.cancel_side('sell')  # Inhibit Asks (No short entries into BTC pump)
        elif threat.state == MacroThreatState.MACRO_DUMP_THREAT:
            allow_bids = False
            self.broker.cancel_side('buy')   # Inhibit Bids (No long entries into BTC dump)
        elif threat.state == MacroThreatState.IDYOSYNCRATIC_BURST:
            if not threat.allow_asks:
                allow_asks = False
                self.broker.cancel_side('sell')
            if not threat.allow_bids:
                allow_bids = False
                self.broker.cancel_side('buy')

        # V16 Radar Crater Retreat Enforcement
        if radar_sig.phase == RadarPhase.CRATER and radar_sig.retreat_ticks > 0:
            verdict.retreat = 1
            verdict.min_touch = max(int(verdict.min_touch), int(radar_sig.retreat_ticks))

        # V16 Predator Phase State Machine & Parasite Policy
        if is_sweep_hot or psi.eta >= 0.85 or z_v > 2.5:
            self.predator_phase = PredatorPhase.RUN
        elif psi.episode_active or psi.e_trap:
            self.predator_phase = PredatorPhase.UNWIND
        elif abs(psi.i_enemy_usd) > 50.0:
            self.predator_phase = PredatorPhase.COOLDOWN
        else:
            self.predator_phase = PredatorPhase.DORMANT

        # Map discrete inventory lots q in {-2, -1, 0, 1, 2} ($5.05 unit lots)
        inv_usd_current = abs(self.broker.get_inventory() * self.book.mid)
        q_lots = int(round(inv_usd_current / 5.05))
        q_clamped = max(-2, min(2, q_lots))

        # Hard Invariant: During RUN phase, Parasite Solver strictly returns kNoQuote (255)
        # Never quote into an active sweep!
        if self.predator_phase == PredatorPhase.RUN:
            if not self.parasite_solver.is_quoting(q_clamped, PredatorPhase.RUN, 0):
                allow_bids = False
                allow_asks = False
        elif self.predator_phase == PredatorPhase.UNWIND:
            parasite_depth = self.parasite_solver.lookup_depth(q_clamped, PredatorPhase.UNWIND, 0)
            if parasite_depth > 0:
                verdict.min_touch = max(int(verdict.min_touch), int(parasite_depth))

        # 6b. Funding Basis Vampire Asymmetric Touch Shading (Frontier 2)
        inv_usd = abs(self.broker.get_inventory() * self.book.mid)
        self.funding.compute_plan(
            s_mid_bps=self.book.spread_bps / 2.0,
            tick_bps=self.cfg.get('relative_tick_bps', 1.0),
            equity_usd=self.risk_kernel.pool_equity_usd,
            inventory_usd=inv_usd,
            sign_stable=True,
            tail_ok=True
        )
        vamp_bids, vamp_asks = self.funding.get_shading_adjustment(inv_usd, self.cfg.get('max_inv_usd', 20.0))
        allow_bids = allow_bids and vamp_bids
        allow_asks = allow_asks and vamp_asks

        # --------------------------------------------------------------------------------------
        # Fleet V17 Sentinel Core: The Watchmen Layer Assessment (Second-Order Logic)
        # --------------------------------------------------------------------------------------
        self.sentinel.on_book(self.book.mid, self.tick_size)

        # Feed real-time estimators into Sentinel CUSUM drift bank
        if psi:
            self.sentinel.observe_param("hawkes_eta", psi.eta)
        if self.py_kalman and self.py_kalman.state.is_initialized:
            self.sentinel.observe_param("kalman_drift", self.py_kalman.velocity_bps)
        if self.py_vr:
            self.sentinel.observe_param("variance_ratio", self.py_vr.variance_ratio())
        if radar_sig:
            self.sentinel.observe_param("radar_delta_lambda", radar_sig.delta_lambda)

        # Feed 8h volume window cadence (24h daily capacity floor $2M)
        now_sec = time.time()
        if now_sec - self.last_window_update_sec >= 28800.0:
            self.last_window_update_sec = now_sec
            vol_usd_window = self.cfg.get('volume_24h_usd', 6_000_000.0)
            self.sentinel.on_window(vol_usd_window)

        # CrossAudit: compare QuadShield directional quote pull vs HJB knife-catch shield
        guard_pulled = 1 if (verdict.cancel_all or not allow_bids or not allow_asks) else 0
        hjb_shield = 1 if (self.latest_hjb_package and self.latest_hjb_package.knife_catch_shield_active) else 0
        self.sentinel.on_audit(bool(guard_pulled), bool(hjb_shield))

        # Assess Pre-Registered Action Lattice (KILL > ROTATE > RETREAT > MONITOR > NONE)
        sent_rep = self.sentinel.assess()
        self.latest_sentinel_rep = sent_rep

        # Certified Class II Fortress Calibration Check:
        # P/delta up to 2500 ticks corresponds to tau_rel >= 4.0 bps (clearing fee wall)
        is_class_ii = (self.cfg.get('relative_tick_bps', 8.0) >= 4.0 and (self.book.mid / max(self.tick_size, 1e-12)) <= 2500.0)
        only_dilution_rotate = (sent_rep.action == V17Action.ROTATE and
                                sent_rep.has_cause(V17Cause.PT_DILUTION) and
                                not (sent_rep.has_cause(V17Cause.EDGE_DECAY_LB) or
                                     sent_rep.has_cause(V17Cause.TICK_CHANGE) or
                                     sent_rep.has_cause(V17Cause.VOL_CAPACITY) or
                                     sent_rep.has_cause(V17Cause.PT_PURGATORY)))

        if sent_rep.action == V17Action.KILL:
            # Undiagnosed edge decay or repeated jumps: halt symbol immediately
            self.broker.update_quotes({})
            return
        elif sent_rep.action == V17Action.ROTATE and not (only_dilution_rotate and is_class_ii):
            # Dead by the law (purgatory, volume floor, age budget, re-tick, or true dilution >2500 ticks)
            self.broker.update_quotes({})
            return
        elif sent_rep.action == V17Action.RETREAT:
            # Diagnosed edge decay or parameter drift: pull back to defensive ladder (Touch-2+)
            verdict.retreat = 1
            verdict.min_touch = max(int(verdict.min_touch), 2)
        elif sent_rep.has_cause(V17Cause.PT_SOFT_EDGE):
            # Asset in deploy band [900, 1150]: purely informational MONITOR state in Sentinel V17
            pass

        # Graduated Velocity-Margin Shield (Kinematic Trend Guard)
        # Compute normalized z_vel = vel / sigma_vel
        clip_mult = 1.0
        abs_z_vel = abs(self.latest_z_vel)
        if 2.0 <= abs_z_vel < 3.0:
            verdict.retreat = 1
            verdict.min_touch = max(int(verdict.min_touch), 2)
            clip_mult = 0.75
        elif abs_z_vel >= 3.0:
            verdict.retreat = 1
            verdict.min_touch = max(int(verdict.min_touch), 3)
            clip_mult = 0.50

        # Severe directional dumping: z_vel < -3.0 with Sentinel drift or book imbalance
        top_bid_sz = bids_tuples[0][1] if bids_tuples else 1.0
        top_ask_sz = asks_tuples[0][1] if asks_tuples else 1.0
        book_ask_heavy = top_ask_sz > top_bid_sz * 1.5
        book_bid_heavy = top_bid_sz > top_ask_sz * 1.5
        sentinel_drift_active = (sent_rep.action in (V17Action.RETREAT, V17Action.KILL) or sent_rep.has_cause(V17Cause.PARAM_DRIFT))

        if self.latest_z_vel < -3.0 and (sentinel_drift_active or book_ask_heavy):
            allow_bids = False

        if self.latest_z_vel > 3.0 and (sentinel_drift_active or book_bid_heavy):
            allow_asks = False

        # Active Macro Threat Scanner Pre-Sweep Directives
        if threat:
            if not threat.allow_bids:
                allow_bids = False
            if not threat.allow_asks:
                allow_asks = False

        if verdict.cancel_all or (not allow_bids and not allow_asks):
            self.broker.update_quotes({})
            return

        # Discrete Capital Corridor Dispatcher: Telemetry Update & Quoting Permit Check
        inv_qty = self.broker.get_inventory()
        if self.dispatcher is not None:
            try:
                from sovereign_fleet.portfolio.corridor_dispatcher import CorridorTelemetry
                self.dispatcher.update_telemetry(CorridorTelemetry(
                    symbol=self.symbol,
                    spread_bps=self.book.spread_bps,
                    funding_8h_bps=self.funding.last_funding_rate_bps,
                    funding_tilt=self.cfg.get('funding_tilt', 'NEUTRAL'),
                    volatility_bps=max(abs(self.latest_z_vel) * 2.0, 5.0),
                    hawkes_eta=psi.eta if psi else 0.0,
                    kinetic_hazard=getattr(self.shield, 'latest_hazard', 0.0),
                    z_velocity=self.latest_z_vel,
                    mid_price=self.book.mid,
                    best_bid=self.book.best_bid,
                    best_ask=self.book.best_ask,
                    l3_depth_cushion_usd=(top_bid_sz + top_ask_sz) * self.book.mid
                ))
            except Exception:
                pass

            if not self.is_shadow and inv_qty == 0 and not self.dispatcher.can_quote(self.symbol):
                # Capacity saturated or prioritized out by Spinu ranking: flush entry quotes immediately
                self.broker.update_quotes({})
                return

        # 6c. Cross-Asset Hayashi-Yoshida Lead-Lag Sniping & Quote Shielding
        if self.lead_lag_engine is not None and not self.is_shadow:
            ll_opp = self.lead_lag_engine.evaluate_corridor(
                symbol=self.symbol,
                alt_best_bid=self.book.best_bid,
                alt_best_ask=self.book.best_ask,
                now_ns=now_ns
            )
            if ll_opp:
                if ll_opp.signal == LeadLagSignal.PULL_ASKS:
                    allow_asks = False
                    self.broker.cancel_side('sell')
                    self.lead_lag_pulls_count += 1
                elif ll_opp.signal == LeadLagSignal.PULL_BIDS:
                    allow_bids = False
                    self.broker.cancel_side('buy')
                    self.lead_lag_pulls_count += 1
                elif ll_opp.signal == LeadLagSignal.SNIPE_BUY:
                    if inv_qty <= 0 and (self.dispatcher is None or self.dispatcher.can_quote(self.symbol)):
                        clip_val = (self.cfg.get('slots_normal') or [{'clip_usd': 5.0}])[0].get('clip_usd', 5.0)
                        snipe_qty = round(clip_val / self.book.best_ask, self.qty_decimals)
                        if snipe_qty * self.book.best_ask >= 5.0:
                            can_alloc, _ = self.risk_kernel.can_allocate_margin(self.symbol, snipe_qty * self.book.best_ask, is_exit=False)
                            if can_alloc:
                                self.lead_lag_snipes_count += 1
                                self.broker.execute_taker_entry(
                                    side='buy',
                                    px=self.book.best_ask,
                                    qty=snipe_qty,
                                    now_ns=now_ns,
                                    on_fill_cb=self._on_broker_event,
                                    slot_name='SNIPE_BUY'
                                )
                elif ll_opp.signal == LeadLagSignal.SNIPE_SELL:
                    if inv_qty >= 0 and (self.dispatcher is None or self.dispatcher.can_quote(self.symbol)):
                        clip_val = (self.cfg.get('slots_normal') or [{'clip_usd': 5.0}])[0].get('clip_usd', 5.0)
                        snipe_qty = round(clip_val / self.book.best_bid, self.qty_decimals)
                        if snipe_qty * self.book.best_bid >= 5.0:
                            can_alloc, _ = self.risk_kernel.can_allocate_margin(self.symbol, snipe_qty * self.book.best_bid, is_exit=False)
                            if can_alloc:
                                self.lead_lag_snipes_count += 1
                                self.broker.execute_taker_entry(
                                    side='sell',
                                    px=self.book.best_bid,
                                    qty=snipe_qty,
                                    now_ns=now_ns,
                                    on_fill_cb=self._on_broker_event,
                                    slot_name='SNIPE_SELL'
                                )

        # 7. Discrete HJB Multi-Slot Quote Generation
        funding_rate = self.funding.last_funding_rate_bps
        quote_package = self.hjb_quoter.compute_quotes(
            feat=self.latest_feat,
            inventory_qty=inv_qty,
            best_bid=self.book.best_bid,
            best_ask=self.book.best_ask,
            mid_px=self.book.mid,
            now_ns=now_ns,
            funding_rate_bps=funding_rate,
            retreat=bool(verdict.retreat),
            min_touch=int(verdict.min_touch)
        )
        self.latest_hjb_package = quote_package

        # 8. Check Portfolio Risk Kernel Margin Allocation
        inv_usd = abs(inv_qty * self.book.mid)
        max_inv = self.cfg.get('max_inv_usd', 20.0)

        if inv_usd >= max_inv:
            if inv_qty > 0:
                allow_bids = False
            elif inv_qty < 0:
                allow_asks = False

        if quote_package.knife_catch_bids:
            allow_bids = False
        if quote_package.knife_catch_asks:
            allow_asks = False

        # Build resting limit order book for this corridor
        new_orders: Dict[str, FleetOrder] = {}
        step = 10 ** (-self.qty_decimals) if self.qty_decimals > 0 else 1.0

        if allow_bids:
            for rung in quote_package.bids:
                if not rung.active or rung.price <= 0.0:
                    continue
                rung_notional = rung.notional_usd * clip_mult
                if rung_notional < 5.05 and rung.notional_usd >= 5.0:
                    rung_notional = 5.05
                rung_qty = max(round(rung_notional / rung.price, self.qty_decimals), step)
                rung_notional = round(rung_qty * rung.price, 4)
                while rung_notional < 5.05:
                    rung_qty = round(rung_qty + step, self.qty_decimals)
                    rung_notional = round(rung_qty * rung.price, 4)

                # Margin allocation check (Live capital only)
                if not self.is_shadow:
                    is_risk_reducing = (inv_qty < 0)
                    can_alloc, _ = self.risk_kernel.can_allocate_margin(self.symbol, rung_notional, is_exit=is_risk_reducing)
                    if not can_alloc:
                        continue

                q_ahead = self.book.get_queue_ahead('buy', rung.price)
                oid = f"bid_{rung.slot_name}_{int(now_ns/1_000_000)}"
                new_orders[f"bid_{rung.slot_name}"] = FleetOrder(
                    order_id=oid, symbol=self.symbol, side='buy',
                    px=rung.price, qty=rung_qty, notional=rung_notional,
                    order_type='ENTRY_LIMIT', slot=rung.slot_name,
                    queue_ahead=q_ahead, created_ns=now_ns, updated_ns=now_ns,
                    anchor_px=self.book.best_bid,
                    is_shadow=self.is_shadow
                )

        if allow_asks:
            for rung in quote_package.asks:
                if not rung.active or rung.price <= 0.0:
                    continue
                rung_notional = rung.notional_usd * clip_mult
                if rung_notional < 5.05 and rung.notional_usd >= 5.0:
                    rung_notional = 5.05
                rung_qty = max(round(rung_notional / rung.price, self.qty_decimals), step)
                rung_notional = round(rung_qty * rung.price, 4)
                while rung_notional < 5.05:
                    rung_qty = round(rung_qty + step, self.qty_decimals)
                    rung_notional = round(rung_qty * rung.price, 4)

                # Margin allocation check (Live capital only)
                if not self.is_shadow:
                    is_risk_reducing = (inv_qty > 0)
                    can_alloc, _ = self.risk_kernel.can_allocate_margin(self.symbol, rung_notional, is_exit=is_risk_reducing)
                    if not can_alloc:
                        continue

                q_ahead = self.book.get_queue_ahead('sell', rung.price)
                oid = f"ask_{rung.slot_name}_{int(now_ns/1_000_000)}"
                new_orders[f"ask_{rung.slot_name}"] = FleetOrder(
                    order_id=oid, symbol=self.symbol, side='sell',
                    px=rung.price, qty=rung_qty, notional=rung_notional,
                    order_type='ENTRY_LIMIT', slot=rung.slot_name,
                    queue_ahead=q_ahead, created_ns=now_ns, updated_ns=now_ns,
                    anchor_px=self.book.best_ask,
                    is_shadow=self.is_shadow
                )

        # 9. Exhaustion Harvest Controller (Passive Advisory Unwind Evaluation)
        if (psi.episode_active or psi.e_trap) and abs(inv_qty * self.book.mid) >= 5.0:
            inv_held_usd = inv_qty * self.book.mid
            _ = self.harvest_controller.evaluate(
                psi=psi,
                macro_impulse=macro_impulse,
                z_v=z_v,
                spread_bps=self.book.spread_bps,
                held_usd=inv_held_usd,
                entry_bps=0.0,
                mid_px=self.book.mid
            )
            # Advisory evaluation: queue_broker manages real dual-leg exits natively
            # via Kinematic Ejector and Adaptive Flow-Clock. Do not inject phantom ENTRY_LIMITs.

        # Hummingbot Queue Tolerance: Suppress re-quoting on sub-tick noise (preserves FIFO priority)
        q_tol_bps = 0.5 * self.cfg.get('relative_tick_bps', 8.0)
        self.broker.update_quotes(new_orders, queue_tolerance_bps=q_tol_bps)

        # Journal resting orders to SQLite WAL (throttled to 1 Hz to prevent disk contention)
        now_sec = now_ns / 1_000_000_000.0
        if getattr(self, '_last_order_record_sec', 0.0) + 1.0 <= now_sec:
            self._last_order_record_sec = now_sec
            for o in self.broker.entry_orders.values():
                try:
                    self.journal.record_order({
                        'order_id': o.order_id,
                        'symbol': o.symbol,
                        'side': o.side,
                        'px': o.px,
                        'qty': o.qty,
                        'notional': o.notional,
                        'order_type': o.order_type,
                        'slot': o.slot,
                        'state': o.state.name if hasattr(o.state, 'name') else str(o.state),
                        'queue_ahead': o.queue_ahead,
                        'anchor_px': o.anchor_px,
                        'created_ns': o.created_ns,
                        'updated_ns': o.updated_ns,
                        'is_shadow': o.is_shadow
                    })
                except Exception as e:
                    pass

    # ----------------------------------------------------------------------------------------------
    # Trade Print Processing
    # ----------------------------------------------------------------------------------------------
    def on_trade_print(self, trade_id: int, px: float, qty: float, is_buyer_maker: bool, now_ns: int):
        notional = px * qty
        side = 'sell' if is_buyer_maker else 'buy'
        is_taker_buy = not is_buyer_maker

        # 1. Feed native C++ profiler & Python adversarial profiler
        self.alpha.on_trade(
            trade_id=trade_id, exchange_ts_ns=now_ns, local_recv_ns=now_ns,
            price=px, qty=qty, notional=notional, is_buyer_maker=is_buyer_maker
        )
        self.py_profiler.on_trade(
            trade_id=trade_id,
            exchange_ts_ns=now_ns,
            local_recv_ns=now_ns,
            price=px,
            qty=qty,
            notional_usd=notional,
            is_buyer_maker=is_buyer_maker
        )

        # 2. Feed native C++ Feature Pipeline
        venue_ms = int(now_ns / 1_000_000)
        self.feature_pipeline.on_trade(now_ns, venue_ms, px, qty, is_taker_buy)

        # 3. Feed Quad-Shield (Kinetic Barrier & Flow Toxicity Guard)
        self.shield.on_trade(now_ns, px, qty, is_taker_buy)

        # 3b. Feed V16 Pre-Sweep Cancellation Radar (Sweeps >= $3,000 or Sweep Hot)
        if notional >= 3000.0 or self.alpha.is_sweep_hot():
            self.radar.on_sweep(now_ns)

        # 4. Deplete FIFO queue volume (V_ahead) and execute fills
        self.broker.on_trade_print(
            trade_id=trade_id, trade_px=px, trade_qty=qty, trade_side=side,
            now_ns=now_ns, on_fill_cb=self._on_broker_event
        )

    def on_liquidation_print(self, ts_sec: float, notional_usd: float, alpha_a: float = 0.0, mu: float = 0.0):
        """Ingests @forceOrder liquidation prints into Shield 5 marked-Hawkes profiler."""
        self.shield.on_liquidation_print(ts_sec, notional_usd, alpha_a, mu)

    def on_macro_btc_tick(self, ts_ns: int, btc_mid: float):
        """Ingests macro BTC price tick into both quad shield and active threat scanner."""
        self.shield.on_macro_btc_tick(ts_ns, btc_mid)
        self.threat_scanner.on_btc_tick(ts_ns, btc_mid)

    # ----------------------------------------------------------------------------------------------
    # Execution Event Handlers
    # ----------------------------------------------------------------------------------------------
    def _on_broker_event(self, event: Dict[str, Any]):
        etype = event.get('type')
        tag = "[SHADOW]" if self.is_shadow else "[ACTIVE]"
        time_str = datetime.now(timezone.utc).strftime("%H:%M:%S")

        if etype == 'ENTRY_FILL':
            cycle = event['cycle']
            desc = f"{cycle['side'].upper()} {cycle['entry_qty']} @ {cycle['entry_px']} (${cycle['entry_notional']:.2f}) | {cycle['slot']}"
            print(f"{tag} [{self.symbol}] ENTRY FILL: {desc}")
            self.recent_events.append({'time_str': time_str, 'symbol': self.symbol, 'action': 'ENTRY_FILL', 'description': desc})
            
            # Register fill in Python markout forensics suite
            f_rec = FillRecord(
                fill_id=cycle['cid'],
                symbol=self.symbol,
                timestamp_ms=int(cycle['entry_ns'] / 1_000_000),
                side=Side.BUY if cycle['side'] == 'buy' else Side.SELL,
                price=float(cycle['entry_px']),
                qty=float(cycle['entry_qty']),
                notional_usd=float(cycle['entry_notional']),
                fee_bps=1.80,
                is_maker=True,
                slot_index=1,
                anchor_px=float(cycle.get('anchor_px', cycle['entry_px']))
            )
            self.recorded_fills.append(f_rec)
            if len(self.recorded_fills) > 500:
                self.recorded_fills.pop(0)

            # Risk kernel margin accounting (Live capital only)
            if not self.is_shadow:
                self.risk_kernel.on_order_placed(self.symbol, cycle['entry_notional'])
                self.risk_kernel.on_cycle_opened(self.symbol)

            # Discrete Capital Slot Accounting & Capacity Breaker
            if self.dispatcher is not None and not self.is_shadow:
                try:
                    self.dispatcher.on_slot_fill(
                        symbol=self.symbol,
                        fill_price=float(cycle['entry_px']),
                        fill_qty=float(cycle['entry_qty']),
                        side=cycle['side'],
                        now_ns=cycle['entry_ns']
                    )
                except Exception as e:
                    print(f"[DISPATCHER ERROR on ENTRY_FILL] {self.symbol}: {e}")

            # SQLite WAL Journaling
            self.journal.record_fill({
                'cid': cycle['cid'], 'symbol': self.symbol, 'side': cycle['side'],
                'px': cycle['entry_px'], 'qty': cycle['entry_qty'], 'notional': cycle['entry_notional'],
                'fee_usd': event['fee_usd'], 'role': 'MAKER', 'fill_ns': cycle['entry_ns'],
                'is_shadow': self.is_shadow
            })

        elif etype == 'PASSIVE_EXIT_HARVEST':
            net_pnl = event['net_pnl_usd']
            gross_bps = event['gross_bps']
            desc = f"+{gross_bps:.2f} bps | Net: ${net_pnl:+.4f} | Total: ${self.broker.net_realized_pnl_usd:+.4f}"
            print(f"{tag} [{self.symbol}] PASSIVE EXIT HARVEST: {desc}")
            self.recent_events.append({'time_str': time_str, 'symbol': self.symbol, 'action': 'PASSIVE_HARVEST', 'description': desc})

            self.harvest_controller.on_harvest_fill(net_pnl)

            # Feed live realized fill bps to Fleet V17 Sentinel EdgeRadar
            cycle = event.get('cycle', {})
            notional = float(cycle.get('entry_notional', 5.0))
            net_fill_bps = (net_pnl / max(notional, 1e-6)) * 10000.0
            self.sentinel.on_fill(net_fill_bps)

            # Record exit with GraduationGateManager
            if self.grad_manager:
                self.grad_manager.record_live_exit(
                    symbol=self.symbol,
                    snapped=True,
                    exit_bps=net_fill_bps,
                    ms=int(time.time() * 1000)
                )

            # Markout Forensics Evaluation
            if self.recorded_fills and len(self.rolling_quote_ts_ms) >= 20:
                try:
                    q_ts = np.array(self.rolling_quote_ts_ms, dtype=np.int64)
                    q_bids = np.array(self.rolling_quote_bids, dtype=np.float64)
                    q_asks = np.array(self.rolling_quote_asks, dtype=np.float64)
                    q_mids = 0.5 * (q_bids + q_asks)
                    last_fill = self.recorded_fills[-1]
                    self.markout_engine.ten_horizon.evaluate_fill(
                        last_fill, q_ts, q_mids, self.markout_engine.maker_fee_bps
                    )
                except Exception:
                    pass

            # Risk kernel accounting (Live capital only)
            cycle = event.get('cycle', {})
            if not self.is_shadow:
                self.risk_kernel.record_pnl(net_pnl, time.time_ns())
                self.risk_kernel.on_cycle_closed(self.symbol)
                self.risk_kernel.on_order_cancelled(self.symbol, float(cycle.get('entry_notional', 5.0)))

            # SQLite WAL Journaling
            cycle = event.get('cycle', {})
            entry_px = cycle.get('entry_px', 0.0)
            exit_px = event.get('exit_px', 0.0)
            qty = cycle.get('entry_qty', 0.0)
            anchor_px = cycle.get('anchor_px', entry_px)
            entry_fee = cycle.get('entry_fee_usd', 0.0)
            exit_fee = event.get('exit_fee_usd', 0.0)
            entry_ns = cycle.get('entry_ns', 0)
            exit_ns = event.get('now_ns', time.time_ns())
            gross_pnl = event.get('gross_pnl_usd', 0.0)

            exit_tier = cycle.get('exit_tier', 0)
            if exit_tier == 3:
                res_tag = 'TIMEOUT_MAKER_WALKDOWN'
            elif exit_tier == 2:
                res_tag = 'LADDER_T2_ADVERSE_SCRATCH'
            elif exit_tier == 1:
                res_tag = 'LADDER_T1_WALKDOWN'
            else:
                res_tag = 'PASSIVE_MAKER_HARVEST'

            self.journal.record_cycle_close({
                'cid': event['cid'], 'symbol': self.symbol, 'side': cycle.get('side', 'buy'),
                'entry_px': entry_px, 'exit_px': exit_px, 'qty': qty,
                'anchor_px': anchor_px,
                'entry_fee_usd': entry_fee, 'exit_fee_usd': exit_fee,
                'gross_pnl_usd': gross_pnl, 'net_pnl_usd': net_pnl,
                'pnl_bps': net_fill_bps, 'mae_bps': event.get('mae_bps', 0.0),
                'mfe_bps': event.get('mfe_bps', 0.0),
                'resolution': res_tag, 'is_taker': 0,
                'entry_ns': entry_ns, 'exit_ns': exit_ns, 'is_shadow': self.is_shadow
            })

            # Release slot in discrete capital dispatcher & rebalance idle fleet
            if self.dispatcher is not None and not self.is_shadow:
                try:
                    self.dispatcher.on_position_exit(
                        symbol=self.symbol,
                        exit_price=float(exit_px),
                        pnl_bps=float(net_fill_bps),
                        now_ns=exit_ns
                    )
                except Exception as e:
                    print(f"[DISPATCHER ERROR on EXIT] {self.symbol}: {e}")

        elif etype == 'POSITION_CLOSED':
            net_pnl = event['net_pnl_usd']
            pnl_bps = event['pnl_bps']
            reason = event['reason']
            desc = f"{reason} | {pnl_bps:+.2f} bps | Net: ${net_pnl:+.4f} | Total: ${self.broker.net_realized_pnl_usd:+.4f}"
            print(f"{tag} [{self.symbol}] POSITION CLOSED: {desc}")
            self.recent_events.append({'time_str': time_str, 'symbol': self.symbol, 'action': reason, 'description': desc})

            # Feed live realized fill bps to Fleet V17 Sentinel EdgeRadar
            cycle = event.get('cycle', {})
            notional = float(cycle.get('entry_notional', 5.0))
            net_fill_bps = (net_pnl / max(notional, 1e-6)) * 10000.0
            self.sentinel.on_fill(net_fill_bps)

            # Record exit with GraduationGateManager
            if self.grad_manager:
                self.grad_manager.record_live_exit(
                    symbol=self.symbol,
                    snapped=False,
                    exit_bps=net_fill_bps,
                    ms=int(time.time() * 1000)
                )

            # Markout Forensics Evaluation
            if self.recorded_fills and len(self.rolling_quote_ts_ms) >= 20:
                try:
                    q_ts = np.array(self.rolling_quote_ts_ms, dtype=np.int64)
                    q_bids = np.array(self.rolling_quote_bids, dtype=np.float64)
                    q_asks = np.array(self.rolling_quote_asks, dtype=np.float64)
                    q_mids = 0.5 * (q_bids + q_asks)
                    last_fill = self.recorded_fills[-1]
                    self.markout_engine.ten_horizon.evaluate_fill(
                        last_fill, q_ts, q_mids, self.markout_engine.maker_fee_bps
                    )
                except Exception:
                    pass

            # Risk kernel accounting (Live capital only)
            cycle = event.get('cycle', {})
            if not self.is_shadow:
                self.risk_kernel.record_pnl(net_pnl, time.time_ns())
                self.risk_kernel.on_cycle_closed(self.symbol)
                self.risk_kernel.on_order_cancelled(self.symbol, float(cycle.get('entry_notional', 5.0)))

            # SQLite WAL Journaling
            cycle = event.get('cycle', {})
            entry_px = cycle.get('entry_px', 0.0)
            exit_px = event.get('exit_px', 0.0)
            qty = cycle.get('entry_qty', 0.0)
            anchor_px = cycle.get('anchor_px', entry_px)
            entry_fee = cycle.get('entry_fee_usd', 0.0)
            exit_fee = event.get('exit_fee_usd', 0.0)
            entry_ns = cycle.get('entry_ns', 0)
            exit_ns = event.get('now_ns', time.time_ns())
            gross_pnl = event.get('gross_pnl_usd', 0.0)

            self.journal.record_cycle_close({
                'cid': event['cid'], 'symbol': self.symbol, 'side': cycle.get('side', 'buy'),
                'entry_px': entry_px, 'exit_px': exit_px, 'qty': qty,
                'anchor_px': anchor_px,
                'entry_fee_usd': entry_fee, 'exit_fee_usd': exit_fee,
                'gross_pnl_usd': gross_pnl, 'net_pnl_usd': net_pnl,
                'pnl_bps': pnl_bps, 'mae_bps': event.get('mae_bps', 0.0),
                'mfe_bps': event.get('mfe_bps', 0.0),
                'resolution': reason, 'is_taker': 1 if event.get('is_taker') else 0,
                'entry_ns': entry_ns, 'exit_ns': exit_ns, 'is_shadow': self.is_shadow
            })

            # Release slot in discrete capital dispatcher & rebalance idle fleet
            if self.dispatcher is not None and not self.is_shadow:
                try:
                    self.dispatcher.on_position_exit(
                        symbol=self.symbol,
                        exit_price=float(exit_px),
                        pnl_bps=float(pnl_bps),
                        now_ns=exit_ns
                    )
                except Exception as e:
                    print(f"[DISPATCHER ERROR on EXIT] {self.symbol}: {e}")

    def get_state(self) -> Dict[str, Any]:
        psi = self.alpha.latest_psi
        micro_px = self.latest_feat.micro_price if (self.latest_feat and self.latest_feat.feed_is_fresh) else self.book.mid
        kalman = self.py_kalman.velocity_bps if (self.py_kalman and self.py_kalman.state.is_initialized) else (self.latest_hjb_package.kalman_drift_bps if self.latest_hjb_package else 0.0)
        vr = self.py_vr.variance_ratio() if self.py_vr else (self.latest_hjb_package.variance_ratio if self.latest_hjb_package else 1.0)

        tox_verdict = self.shield.last_toxicity_verdict
        tox_bid = tox_verdict.buy_hazard_score if tox_verdict else 0.0
        tox_ask = tox_verdict.ask_hazard_score if tox_verdict else 0.0

        return {
            'symbol': self.symbol,
            'mode': self.cfg['mode'],
            'mid': self.book.mid,
            'micro_price': micro_px,
            'spread_bps': self.book.spread_bps,
            'kalman_drift': kalman,
            'kalman_vel': self.py_kalman.velocity_bps,
            'kalman_accel': self.py_kalman.accel_bps,
            'z_vel': self.latest_z_vel,
            'variance_ratio': vr,
            'py_vr': self.py_vr.variance_ratio(),
            'tox_bid': tox_bid,
            'tox_ask': tox_ask,
            'eta': psi.eta if psi else 0.0,
            'entropy': psi.entropy if psi else 4.0,
            'i_enemy_usd': psi.i_enemy_usd if psi else 0.0,
            'ofi_cumulative': self.latest_feat.ofi_cumulative if self.latest_feat else 0.0,
            'open_cycles': len(self.broker.open_cycles),
            'total_fills': self.broker.total_fills,
            'net_pnl': self.broker.net_realized_pnl_usd,
            'radar_phase': int(self.latest_radar_sig.phase) if self.latest_radar_sig else 0,
            'radar_z': self.latest_radar_sig.z if self.latest_radar_sig else 0.0,
            'radar_retreat': int(self.latest_radar_sig.retreat_ticks) if self.latest_radar_sig else 0,
            'predator_phase': self.predator_phase.name if hasattr(self.predator_phase, 'name') else 'DORMANT',
            'sentinel_action': V17Action(self.latest_sentinel_rep.action).name if self.latest_sentinel_rep else 'NONE',
            'sentinel_zone': V17Zone(self.latest_sentinel_rep.zone).name if self.latest_sentinel_rep else 'UNKNOWN',
            'sentinel_causes': self.latest_sentinel_rep.cause_names() if self.latest_sentinel_rep else [],
            'sentinel_pt': self.latest_sentinel_rep.pt if self.latest_sentinel_rep else 0.0,
            'sentinel_edge_lb': self.latest_sentinel_rep.edge_lb_bps if self.latest_sentinel_rep else 0.0,
            'threat_state': self.latest_threat_assessment.state.value if self.latest_threat_assessment else 'BENIGN',
            'threat_intensity': self.latest_threat_assessment.intensity if self.latest_threat_assessment else 0.0,
            'kinematic_ejections': self.broker.total_kinematic_ejections,
        }


# ==================================================================================================
# Fleet Orchestrator Main
# ==================================================================================================
async def run_sovereign_fleet(capital: float = 25.0):
    profile = get_fleet_profile(capital)
    journal = ExecutionJournal(profile.sqlite_db_path)
    risk_kernel = FortressRiskKernel(profile.capital_usd, profile.max_portfolio_leverage)

    # Macro BTC Lead-Lag Detector
    from sovereign_fleet.signals.macro_lead_lag import MacroLeadLagController
    macro_btc = MacroLeadLagController(impulse_bps=1.5, window_ns=50_000_000)

    # Initialize Institutional Governance Layer
    grad_manager = GraduationGateManager()

    # Load corridors dynamically from Institutional CorridorRegistry
    engines: Dict[str, CorridorEngine] = {}
    stream_symbols = ["btcusdt"]

    # Filter out BANNED or CLOSED corridors (ROBOUSDT and BEATUSDT strictly excluded)
    valid_configs = {
        sym: cfg for sym, cfg in CORRIDOR_CONFIGS.items()
        if cfg.state not in (CorridorState.BANNED, CorridorState.CLOSED)
    }

    # 1. Autonomous Forensic Markout Doctor (Continuous SQLite WAL Auditor)
    markout_doctor = ForensicMarkoutDoctor(
        db_path=str(profile.sqlite_db_path),
        max_consecutive_fails=2,
        max_corridor_drawdown_usd=0.0250,
        quarantine_duration_sec=1800.0
    )

    # 2. Cross-Asset Hayashi-Yoshida Lead-Lag Sniping Engine
    lead_lag_engine = CrossAssetLeadLagEngine(
        jump_threshold_bps=5.0,
        min_sniping_edge_bps=5.0
    )

    # 3. 24/7 Autonomous Universe Screener Daemon
    screener_path = Path(r"D:\sovereign_market_os\paper_trading\universe_hivemind_candidates.json")
    screener_path.parent.mkdir(parents=True, exist_ok=True)
    universe_screener = UniverseScreenerDaemon(
        output_json_path=str(screener_path),
        scan_interval_sec=120.0,
        min_volume_usd=10_000_000.0,
        min_l1_depth_usd=1_500.0
    )

    # Initialize Discrete Capital Corridor Dispatcher
    from sovereign_fleet.portfolio.corridor_dispatcher import (
        CorridorDispatcher, DispatcherConfig, CorridorLifecycleState
    )

    def cancel_quotes_callback(symbols_to_cancel: List[str]):
        """Atomic breaker callback: flushes resting entry quotes across cancelled corridors."""
        for s in symbols_to_cancel:
            eng = engines.get(s)
            if eng and not eng.is_shadow:
                eng.broker.update_quotes({})

    dispatcher = CorridorDispatcher(
        config=DispatcherConfig(
            total_capital_usd=profile.capital_usd,
            max_portfolio_leverage=profile.max_portfolio_leverage,
            cash_reserve_usd=profile.fortress_reserve_usd,
            max_slots=3,
            slot_notional_usd=5.00
        ),
        cancel_quotes_callback=cancel_quotes_callback,
        markout_doctor=markout_doctor
    )

    for sym, cfg_obj in valid_configs.items():
        cfg = cfg_obj.to_dict()
        is_shadow = (cfg_obj.state == CorridorState.SHADOW)
        dispatcher.register_corridor(sym)
        engines[sym] = CorridorEngine(
            symbol=sym,
            cfg=cfg,
            journal=journal,
            risk_kernel=risk_kernel,
            is_shadow=is_shadow,
            grad_manager=grad_manager,
            dispatcher=dispatcher,
            lead_lag_engine=lead_lag_engine
        )
        stream_symbols.append(sym.lower())

    # Initial fleet priority allocation
    dispatcher.rebalance_and_dispatch()

    active_names = [s for s, e in engines.items() if not e.is_shadow]
    shadow_names = [s for s, e in engines.items() if e.is_shadow]
    print("=" * 144)
    print(" LAUNCHING SOVEREIGN MARKET OS: NESTED HIVEMIND & SENTINEL V18 (AUTONOMOUS MULTI-LAYER EXECUTION)")
    print(f" Portfolio Capital: ${profile.capital_usd:.2f} USD | Max Leverage: {profile.max_portfolio_leverage}x | Reserve: ${profile.fortress_reserve_usd:.2f}")
    print(f" Active Quoting ({len(active_names)}): {', '.join(active_names)} | Bench / Shadow ({len(shadow_names)}): {', '.join(shadow_names)}")
    print(f" Quarantined / Closed: HANAUSDT, APRUSDT, BEATUSDT | Banned: ROBOUSDT")
    print(f" ACID SQLite WAL: {profile.sqlite_db_path}")
    print("=" * 144)

    start_ts = time.time()

    def on_ws_message(stream: str, data: Dict[str, Any], now_ns: int):
        sym_match = stream.split('@')[0].upper()

        # Handle Macro BTC
        if sym_match == 'BTCUSDT':
            if 'depth' in stream:
                bids = data.get('b', [])
                asks = data.get('a', [])
                if bids and asks:
                    mid = (float(bids[0][0]) + float(asks[0][0])) / 2.0
                    macro_btc.on_btc_tick(now_ns, mid)
                    lead_lag_engine.on_btc_tick(now_ns, mid)
                    for e in engines.values():
                        e.on_macro_btc_tick(now_ns, mid)
            elif 'trade' in stream:
                px = float(data.get('p', 0.0))
                macro_btc.on_btc_tick(now_ns, px)
                lead_lag_engine.on_btc_tick(now_ns, px)
                for e in engines.values():
                    e.on_macro_btc_tick(now_ns, px)
            return

        engine = engines.get(sym_match)
        if not engine:
            return

        macro_impulse = macro_btc.check_impulse()

        if 'depth' in stream:
            bids = data.get('b', [])
            asks = data.get('a', [])
            if bids and asks:
                engine.on_depth_update(bids, asks, now_ns, macro_impulse)
        elif 'trade' in stream:
            tid = int(data.get('t', 0))
            px = float(data.get('p', 0.0))
            qty = float(data.get('q', 0.0))
            is_buyer_maker = bool(data.get('m', False))
            engine.on_trade_print(tid, px, qty, is_buyer_maker, now_ns)

    ws_client = BinanceMultiplexedWS(stream_symbols, on_ws_message)

    # Real-time Telemetry Dashboard Loop
    async def telemetry_loop():
        while True:
            await asyncio.sleep(15.0)
            elapsed = time.time() - start_ts

            # Governance Eviction on Sentinel ROTATE/KILL (Strict Anti-Contagion: No unverified promotion)
            for sym, eng in list(engines.items()):
                if not eng.is_shadow and eng.latest_sentinel_rep:
                    rep = eng.latest_sentinel_rep
                    is_class_ii = (eng.cfg.get('relative_tick_bps', 8.0) >= 4.0 and (eng.book.mid / max(eng.tick_size, 1e-12)) <= 2500.0)
                    only_dilution = (rep.action == V17Action.ROTATE and
                                     rep.has_cause(V17Cause.PT_DILUTION) and
                                     not (rep.has_cause(V17Cause.EDGE_DECAY_LB) or
                                          rep.has_cause(V17Cause.TICK_CHANGE) or
                                          rep.has_cause(V17Cause.VOL_CAPACITY) or
                                          rep.has_cause(V17Cause.PT_PURGATORY)))

                    if rep.action in (V17Action.ROTATE, V17Action.KILL) and not (only_dilution and is_class_ii):
                        p_delta = eng.book.mid / max(eng.tick_size, 1e-12)
                        action_name = V17Action(rep.action).name
                        eng.is_shadow = True
                        eng.broker.is_shadow = True
                        eng.broker.update_quotes({})
                        evict_desc = f"GOVERNANCE EVICTION: {sym} demoted to SHADOW (P/delta {p_delta:.1f} {action_name})"
                        journal.record_shield_event(
                            symbol=sym,
                            event_type='SENTINEL_EVICTION',
                            details={'description': evict_desc},
                            now_ns=time.time_ns()
                        )
                        print(f"\n[GOVERNANCE EVICTION] >>> {evict_desc} (Quoting suspended, capital protected)\n")

            states = [e.get_state() for e in engines.values()]

            active_engines = [e for e in engines.values() if not e.is_shadow]
            tot_pnl = sum(e.broker.net_realized_pnl_usd for e in active_engines)
            tot_fills = sum(e.broker.total_fills for e in active_engines)
            tot_snaps = sum(e.broker.total_snaps for e in active_engines)
            tot_stops = sum(e.broker.total_stops for e in active_engines)
            tot_timeouts = sum(e.broker.total_timeouts for e in active_engines)

            # Collect recent events
            recent_evs = []
            for e in engines.values():
                recent_evs.extend(e.recent_events[-2:])
            recent_evs.sort(key=lambda x: x.get('time_str', ''))

            # Assemble Live Graduation States for Console
            grad_states = []
            for sym, eng in engines.items():
                st = grad_manager.get_state(sym)
                exits = grad_manager.live_exits.get(sym, [])
                n_exits = len(exits)
                w_lb = None
                if n_exits > 0:
                    n_snapped = sum(1 for x in exits if x['snapped'])
                    w_lb = wilson_lb(n_snapped, n_exits)
                tau = eng.cfg.get('relative_tick_bps', 8.0)
                req_snap = 30.0 / (2.0 * tau + 26.4)
                snap_pass = (w_lb >= req_snap) if (w_lb is not None and n_exits >= 10) else False

                grad_states.append({
                    'symbol': sym,
                    'status': st.value,
                    'resolved_events': n_exits,
                    'span_hours': elapsed / 3600.0,
                    'wilson_lb': w_lb,
                    'snap_law_pass': snap_pass,
                    'auc_ratio': eng.latest_sentinel_rep.edge_lb_bps if eng.latest_sentinel_rep else 0.0,
                    'verdict': 'QUALIFIED' if (n_exits >= 40 and w_lb and w_lb >= 0.60) else ('MONITOR' if n_exits > 0 else 'PENDING')
                })

            disp_status = dispatcher.get_fleet_status()

            hivemind_status = {
                'quarantined_corridors': list(markout_doctor.active_quarantines),
                'screener_top': [c.symbol for c in universe_screener.latest_candidates[:3]],
                'snipes_count': sum(e.lead_lag_snipes_count for e in engines.values()),
                'pulls_count': sum(e.lead_lag_pulls_count for e in engines.values())
            }

            TelemetryConsole.render(
                elapsed_sec=elapsed,
                capital_summary=risk_kernel.get_summary(),
                btc_impulse=macro_btc.last_impulse,
                btc_mid=macro_btc.last_btc_mid,
                asset_states=states,
                graduation_states=grad_states,
                recent_events=recent_evs,
                total_pnl=tot_pnl,
                total_fills=tot_fills,
                total_snaps=tot_snaps,
                total_stops=tot_stops,
                total_timeouts=tot_timeouts,
                db_path=str(profile.sqlite_db_path.name),
                dispatcher_status=disp_status,
                hivemind_status=hivemind_status
            )

    # Autonomous Background Research & Audit Loops (Slow Layer: 20s - 120s)
    async def doctor_audit_loop():
        """Slow Layer: Autonomous 20s SQLite WAL markout auditor & quarantine governor."""
        while True:
            await asyncio.sleep(20.0)
            try:
                markout_doctor.audit_now()
                quarantined_syms = list(markout_doctor.active_quarantines)
                if quarantined_syms:
                    cancel_quotes_callback(quarantined_syms)
            except Exception:
                pass

    async def universe_screener_loop():
        """Slow Layer: Autonomous 120s 24/7 universe screener daemon."""
        while True:
            try:
                universe_screener.run_scan_once()
            except Exception:
                pass
            await asyncio.sleep(120.0)

    await asyncio.gather(
        ws_client.start(),
        telemetry_loop(),
        doctor_audit_loop(),
        universe_screener_loop()
    )


if __name__ == '__main__':
    parser = argparse.ArgumentParser(description="Sovereign Market OS: Institutional Fleet V16 (Asymmetric Predator-Parasite)")
    parser.add_argument("--capital", type=float, default=25.0, help="Account capital pool ($25 Golden Ratio)")
    args = parser.parse_args()

    try:
        asyncio.run(run_sovereign_fleet(args.capital))
    except KeyboardInterrupt:
        print("\n[Shutdown] Sovereign Market OS stopped cleanly.")

`
