# Sovereign Market OS: Fleet V18 Live Execution Tape (First 1,000 Lines)

**Source Log File**: C:\Users\chndr\.gemini\antigravity\brain\c2784aac-d70d-48fc-9f7f-e4b2da2f4d60\.system_generated\tasks\task-42240.log  
**Target Process**: python -u sovereign_fleet/run_fleet.py --capital 25 (PID 	ask-42240)  
**Line Span**: Lines 1 to 1,000 (Inclusive)  
**Total Characters**: 128,799 bytes  
**Capture Timestamp**: 2026-10-01T18:28:20.021002+00:00  

---

## 1. Tape Architecture & Header Telemetry

The following log extract captures the exact initialization, WebSocket multiplex handshake, Discrete Capital Dispatcher calibration ( capital pool, 3 discrete  slots,  reserve), Autonomous Hivemind background daemons, and live multi-corridor market making cycles.

---

## 2. Verbatim First 1,000 Receipted Execution Lines

`	ext
================================================================================================================================================
 LAUNCHING SOVEREIGN MARKET OS: NESTED HIVEMIND & SENTINEL V18 (AUTONOMOUS MULTI-LAYER EXECUTION)
 Portfolio Capital: $25.00 USD | Max Leverage: 0.6x | Reserve: $10.00
 Active Quoting (22): MMTUSDT, ESPORTSUSDT, CHZUSDT, OPGUSDT, SPELLUSDT, PRLUSDT, CFGUSDT, OPENUSDT, MITOUSDT, ARKMUSDT, ATUSDT, ONUSDT, GRAMUSDT, TOSHIUSDT, RIVERUSDT, AZTECUSDT, DEXEUSDT, RENDERUSDT, APEUSDT, ORCAUSDT, DIAUSDT, WOOUSDT | Bench / Shadow (0): 
 Quarantined / Closed: HANAUSDT, APRUSDT, BEATUSDT | Banned: ROBOUSDT
 ACID SQLite WAL: D:\sovereign_market_os\paper_trading\sovereign_fleet_v17.db
================================================================================================================================================
[MarketDataWS] Initializing connection to Binance Multiplex (23 assets, 47 feeds)...
[MarketDataWS] >>> CONNECTED to Binance Futures. Real-time stream active.

================================================================================================================================================================
 SOVEREIGN MARKET OS: NESTED HIVEMIND & SENTINEL V18 [0.00h /   0.3m] | WAL: sovereign_fleet_v17.db
 Pool Capital: $25.00 | Active Margin: $0.00 (0.00x) | Reserve: $10.00 | Net PnL: $+0.0000 | Win%:   0.0%
 Peak PnL: $+0.0000 | Current DD: $0.0000 | Max DD: $0.0000 | Breaker: ARMED | BTC: NORMAL ($84851.2)
 DISCRETE DISPATCHER | Slots: 0/3 Filled ($0.00) | Free: $15.00 | Atomic Breaker: ARMED (Last: 0.0000ms) | Positions: None (All idle quoting) | Top Spinu: MMTUSDT (S=0.00), ESPORTSUSDT (S=0.00), CHZUSDT (S=0.00)
 AUTONOMOUS HIVEMIND | Quarantined (0): None (Clean) | Screener Top: RIVERUSDT, GRAMUSDT, TRXUSDT | Lead-Lag Snipes: 0 | Protected Quotes: 0
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | MODE         | P/DELTA (ZONE) | SENTINEL   | MID / MICRO         | SPREAD   | KAL/VR     | ETA    | I_ENEMY   | CYC | FILL | NET PNL    
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | DEEP_PYRAMID | 1878 (DILU)    | ROTATE     | 0.18780/0.18775     | 10.65b   | +9.6b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 ESPORTSUSDT | DEEP_PYRAMID | 1098 (FORT)    | NONE       | 0.01098/0.01098     | 9.11b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 CHZUSDT     | DEEP_PYRAMID | 1625 (DILU)    | ROTATE     | 0.01625/0.01625     | 6.15b    | -0.3b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 OPGUSDT     | DEEP_PYRAMID | 1290 (DILU)    | ROTATE     | 0.12895/0.12894     | 7.75b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 SPELLUSDT   | DEEP_PYRAMID |  980 (FORT)    | NONE       | 0.00010/0.00010     | 10.20b   | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 PRLUSDT     | DEEP_PYRAMID | 1180 (FORT)    | MONITOR    | 0.11795/0.11791     | 8.48b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 CFGUSDT     | DEEP_PYRAMID | 1460 (DILU)    | ROTATE     | 0.14595/0.14599     | 6.85b    | -0.0b|0.96 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 OPENUSDT    | DEEP_PYRAMID | 1300 (DILU)    | ROTATE     | 0.12995/0.12999     | 7.70b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 MITOUSDT    | DEEP_PYRAMID | 1568 (DILU)    | ROTATE     | 0.01568/0.01569     | 6.38b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 ARKMUSDT    | DEEP_PYRAMID | 1318 (DILU)    | ROTATE     | 0.13175/0.13179     | 7.59b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 ATUSDT      | DEEP_PYRAMID | 1594 (DILU)    | ROTATE     | 0.15945/0.15950     | 6.27b    | +0.0b|0.86 | 0.700  | $+898.0   |   0 |    0 | $+0.0000   
 ONUSDT      | DEEP_PYRAMID | 1072 (FORT)    | MONITOR    | 0.10725/0.10722     | 9.32b    | -4.6b|1.07 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 GRAMUSDT    | DEEP_PYRAMID | 1552 (DILU)    | ROTATE     | 1.552/1.552         | 6.44b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 TOSHIUSDT   | DEEP_PYRAMID | 1236 (FORT)    | MONITOR    | 0.00012/0.00012     | 8.09b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 RIVERUSDT   | DEEP_PYRAMID | 1216 (FORT)    | MONITOR    | 1.216/1.217         | 8.22b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 AZTECUSDT   | DEEP_PYRAMID | 1754 (DILU)    | ROTATE     | 0.01754/0.01753     | 5.70b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 DEXEUSDT    | DEEP_PYRAMID | 1886 (DILU)    | ROTATE     | 1.885/1.886         | 5.30b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 RENDERUSDT  | DEEP_PYRAMID | 1926 (DILU)    | ROTATE     | 1.926/1.926         | 5.19b    | +0.4b|0.98 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 APEUSDT     | DEEP_PYRAMID | 1487 (DILU)    | ROTATE     | 0.14875/0.14878     | 6.72b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 ORCAUSDT    | DEEP_PYRAMID | 1678 (DILU)    | ROTATE     | 1.679/1.679         | 5.96b    | +0.1b|0.98 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 DIAUSDT     | DEEP_PYRAMID | 1664 (DILU)    | ROTATE     | 0.16635/0.16634     | 6.01b    | +0.1b|0.96 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 WOOUSDT     | DEEP_PYRAMID | 1372 (DILU)    | ROTATE     | 0.01372/0.01372     | 7.29b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 SHADOW GRADUATION GATE EVALUATOR (Stage 1 Target: 40 Events | Wilson LB >= 0.60 | Net K2 >= +8 bps)
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | STATUS           | CENSUS       | WILSON 95% LB  | SNAP LAW   | FLOW AUC   | GATE VERDICT   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ESPORTSUSDT | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CHZUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPGUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 SPELLUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 PRLUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CFGUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPENUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 MITOUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ARKMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ATUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ONUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 GRAMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 TOSHIUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RIVERUSDT   | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 AZTECUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DEXEUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RENDERUSDT  | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 APEUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ORCAUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DIAUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 WOOUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
================================================================================================================================================================


================================================================================================================================================================
 SOVEREIGN MARKET OS: NESTED HIVEMIND & SENTINEL V18 [0.01h /   0.5m] | WAL: sovereign_fleet_v17.db
 Pool Capital: $25.00 | Active Margin: $0.00 (0.00x) | Reserve: $10.00 | Net PnL: $+0.0000 | Win%:   0.0%
 Peak PnL: $+0.0000 | Current DD: $0.0000 | Max DD: $0.0000 | Breaker: ARMED | BTC: NORMAL ($84868.1)
 DISCRETE DISPATCHER | Slots: 0/3 Filled ($0.00) | Free: $15.00 | Atomic Breaker: ARMED (Last: 0.0000ms) | Positions: None (All idle quoting) | Top Spinu: MMTUSDT (S=0.00), ESPORTSUSDT (S=0.00), CHZUSDT (S=0.00)
 AUTONOMOUS HIVEMIND | Quarantined (5): APRUSDT, ONUSDT, HANAUSDT, RIVERUSDT, ATUSDT | Screener Top: RIVERUSDT, GRAMUSDT, TRXUSDT | Lead-Lag Snipes: 0 | Protected Quotes: 0
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | MODE         | P/DELTA (ZONE) | SENTINEL   | MID / MICRO         | SPREAD   | KAL/VR     | ETA    | I_ENEMY   | CYC | FILL | NET PNL    
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | DEEP_PYRAMID | 1878 (DILU)    | ROTATE     | 0.18785/0.18781     | 5.32b    | -0.0b|0.69 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 ESPORTSUSDT | DEEP_PYRAMID | 1098 (FORT)    | NONE       | 0.01098/0.01097     | 9.11b    | +0.0b|1.00 | 0.800  | $+0.0     |   0 |    0 | $+0.0000   
 CHZUSDT     | DEEP_PYRAMID | 1625 (DILU)    | ROTATE     | 0.01625/0.01626     | 6.15b    | -0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 OPGUSDT     | DEEP_PYRAMID | 1290 (DILU)    | ROTATE     | 0.12895/0.12896     | 7.75b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 SPELLUSDT   | DEEP_PYRAMID |  982 (FORT)    | NONE       | 0.00010/0.00010     | 10.19b   | -5.2b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 PRLUSDT     | DEEP_PYRAMID | 1180 (FORT)    | MONITOR    | 0.11795/0.11792     | 8.48b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 CFGUSDT     | DEEP_PYRAMID | 1460 (DILU)    | ROTATE     | 0.14605/0.14602     | 6.85b    | -0.2b|0.76 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 OPENUSDT    | DEEP_PYRAMID | 1300 (DILU)    | ROTATE     | 0.13000/0.13006     | 15.38b   | +0.1b|0.62 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 MITOUSDT    | DEEP_PYRAMID | 1568 (DILU)    | ROTATE     | 0.01568/0.01569     | 6.38b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 ARKMUSDT    | DEEP_PYRAMID | 1320 (DILU)    | ROTATE     | 0.13195/0.13194     | 7.58b    | -0.0b|0.91 | 0.450  | $+0.0     |   0 |    0 | $+0.0000   
 ATUSDT      | DEEP_PYRAMID | 1596 (DILU)    | ROTATE     | 0.15965/0.15967     | 6.26b    | +0.0b|1.00 | 0.850  | $+3900.0  |   0 |    0 | $+0.0000   
 ONUSDT      | DEEP_PYRAMID | 1072 (FORT)    | NONE       | 0.10725/0.10728     | 9.32b    | -0.0b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 GRAMUSDT    | DEEP_PYRAMID | 1555 (DILU)    | ROTATE     | 1.555/1.555         | 6.43b    | -0.0b|1.16 | 0.900  | $+13416.6 |   0 |    0 | $+0.0000   
 TOSHIUSDT   | DEEP_PYRAMID | 1236 (FORT)    | MONITOR    | 0.00012/0.00012     | 8.09b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 RIVERUSDT   | DEEP_PYRAMID | 1218 (FORT)    | MONITOR    | 1.218/1.218         | 8.21b    | -0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 AZTECUSDT   | DEEP_PYRAMID | 1754 (DILU)    | ROTATE     | 0.01754/0.01753     | 5.70b    | -0.0b|0.22 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 DEXEUSDT    | DEEP_PYRAMID | 1886 (DILU)    | ROTATE     | 1.886/1.887         | 5.30b    | -0.0b|0.42 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 RENDERUSDT  | DEEP_PYRAMID | 1928 (DILU)    | ROTATE     | 1.927/1.927         | 5.19b    | +0.0b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 APEUSDT     | DEEP_PYRAMID | 1487 (DILU)    | ROTATE     | 0.14875/0.14877     | 6.72b    | -0.1b|1.07 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 ORCAUSDT    | DEEP_PYRAMID | 1678 (DILU)    | ROTATE     | 1.679/1.679         | 5.96b    | -0.0b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 DIAUSDT     | DEEP_PYRAMID | 1664 (DILU)    | ROTATE     | 0.16645/0.16644     | 6.01b    | -0.0b|1.08 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 WOOUSDT     | DEEP_PYRAMID | 1372 (DILU)    | ROTATE     | 0.01372/0.01372     | 7.29b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 SHADOW GRADUATION GATE EVALUATOR (Stage 1 Target: 40 Events | Wilson LB >= 0.60 | Net K2 >= +8 bps)
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | STATUS           | CENSUS       | WILSON 95% LB  | SNAP LAW   | FLOW AUC   | GATE VERDICT   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ESPORTSUSDT | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CHZUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPGUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 SPELLUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 PRLUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CFGUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPENUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 MITOUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ARKMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ATUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ONUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 GRAMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 TOSHIUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RIVERUSDT   | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 AZTECUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DEXEUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RENDERUSDT  | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 APEUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ORCAUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DIAUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 WOOUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
================================================================================================================================================================


================================================================================================================================================================
 SOVEREIGN MARKET OS: NESTED HIVEMIND & SENTINEL V18 [0.01h /   0.8m] | WAL: sovereign_fleet_v17.db
 Pool Capital: $25.00 | Active Margin: $0.00 (0.00x) | Reserve: $10.00 | Net PnL: $+0.0000 | Win%:   0.0%
 Peak PnL: $+0.0000 | Current DD: $0.0000 | Max DD: $0.0000 | Breaker: ARMED | BTC: NORMAL ($84856.6)
 DISCRETE DISPATCHER | Slots: 0/3 Filled ($0.00) | Free: $15.00 | Atomic Breaker: ARMED (Last: 0.0000ms) | Positions: None (All idle quoting) | Top Spinu: MMTUSDT (S=0.00), ESPORTSUSDT (S=0.00), CHZUSDT (S=0.00)
 AUTONOMOUS HIVEMIND | Quarantined (5): APRUSDT, ONUSDT, HANAUSDT, RIVERUSDT, ATUSDT | Screener Top: RIVERUSDT, GRAMUSDT, TRXUSDT | Lead-Lag Snipes: 0 | Protected Quotes: 0
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | MODE         | P/DELTA (ZONE) | SENTINEL   | MID / MICRO         | SPREAD   | KAL/VR     | ETA    | I_ENEMY   | CYC | FILL | NET PNL    
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | DEEP_PYRAMID | 1878 (DILU)    | ROTATE     | 0.18785/0.18781     | 5.32b    | -3.3b|1.07 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 ESPORTSUSDT | DEEP_PYRAMID | 1098 (FORT)    | NONE       | 0.01098/0.01097     | 9.11b    | +0.0b|1.00 | 0.800  | $+0.0     |   0 |    0 | $+0.0000   
 CHZUSDT     | DEEP_PYRAMID | 1625 (DILU)    | ROTATE     | 0.01625/0.01626     | 6.15b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 OPGUSDT     | DEEP_PYRAMID | 1290 (DILU)    | ROTATE     | 0.12895/0.12897     | 7.75b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 SPELLUSDT   | DEEP_PYRAMID |  982 (FORT)    | NONE       | 0.00010/0.00010     | 10.19b   | -0.0b|1.02 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 PRLUSDT     | DEEP_PYRAMID | 1180 (FORT)    | MONITOR    | 0.11795/0.11792     | 8.48b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 CFGUSDT     | DEEP_PYRAMID | 1460 (DILU)    | ROTATE     | 0.14595/0.14595     | 6.85b    | +0.1b|1.07 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 OPENUSDT    | DEEP_PYRAMID | 1300 (DILU)    | ROTATE     | 0.13000/0.13006     | 15.38b   | +0.4b|0.69 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 MITOUSDT    | DEEP_PYRAMID | 1570 (DILU)    | ROTATE     | 0.01570/0.01570     | 12.74b   | -5.6b|0.85 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 ARKMUSDT    | DEEP_PYRAMID | 1318 (DILU)    | ROTATE     | 0.13185/0.13189     | 7.58b    | +0.0b|1.02 | 0.450  | $+257.9   |   0 |    0 | $+0.0000   
 ATUSDT      | DEEP_PYRAMID | 1598 (DILU)    | ROTATE     | 0.15975/0.15976     | 6.26b    | -0.0b|0.99 | 0.750  | $+7371.7  |   0 |    0 | $+0.0000   
 ONUSDT      | DEEP_PYRAMID | 1072 (FORT)    | NONE       | 0.10725/0.10726     | 9.32b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 GRAMUSDT    | DEEP_PYRAMID | 1555 (DILU)    | ROTATE     | 1.555/1.556         | 6.43b    | +0.0b|0.86 | 0.800  | $+0.0     |   0 |    0 | $+0.0000   
 TOSHIUSDT   | DEEP_PYRAMID | 1236 (FORT)    | MONITOR    | 0.00012/0.00012     | 8.09b    | +23.3b|0.64 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 RIVERUSDT   | DEEP_PYRAMID | 1216 (FORT)    | RETREAT    | 1.216/1.217         | 8.22b    | -0.0b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 AZTECUSDT   | DEEP_PYRAMID | 1752 (DILU)    | ROTATE     | 0.01752/0.01753     | 5.71b    | +0.0b|0.73 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 DEXEUSDT    | DEEP_PYRAMID | 1886 (DILU)    | ROTATE     | 1.886/1.887         | 5.30b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 RENDERUSDT  | DEEP_PYRAMID | 1928 (DILU)    | ROTATE     | 1.927/1.928         | 5.19b    | -0.0b|0.40 | 0.800  | $+0.0     |   0 |    0 | $+0.0000   
 APEUSDT     | DEEP_PYRAMID | 1487 (DILU)    | ROTATE     | 0.14875/0.14876     | 6.72b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 ORCAUSDT    | DEEP_PYRAMID | 1678 (DILU)    | ROTATE     | 1.677/1.678         | 5.96b    | -0.0b|0.99 | 0.950  | $-819.0   |   0 |    0 | $+0.0000   
 DIAUSDT     | DEEP_PYRAMID | 1666 (DILU)    | ROTATE     | 0.16655/0.16658     | 6.00b    | +0.0b|0.91 | 0.950  | $+5.8     |   0 |    0 | $+0.0000   
 WOOUSDT     | DEEP_PYRAMID | 1372 (DILU)    | ROTATE     | 0.01372/0.01372     | 7.29b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 SHADOW GRADUATION GATE EVALUATOR (Stage 1 Target: 40 Events | Wilson LB >= 0.60 | Net K2 >= +8 bps)
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | STATUS           | CENSUS       | WILSON 95% LB  | SNAP LAW   | FLOW AUC   | GATE VERDICT   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ESPORTSUSDT | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CHZUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPGUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 SPELLUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 PRLUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CFGUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPENUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 MITOUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ARKMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ATUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ONUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 GRAMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 TOSHIUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RIVERUSDT   | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 AZTECUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DEXEUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RENDERUSDT  | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 APEUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ORCAUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DIAUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 WOOUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
================================================================================================================================================================


================================================================================================================================================================
 SOVEREIGN MARKET OS: NESTED HIVEMIND & SENTINEL V18 [0.02h /   1.0m] | WAL: sovereign_fleet_v17.db
 Pool Capital: $25.00 | Active Margin: $0.00 (0.00x) | Reserve: $10.00 | Net PnL: $+0.0000 | Win%:   0.0%
 Peak PnL: $+0.0000 | Current DD: $0.0000 | Max DD: $0.0000 | Breaker: ARMED | BTC: NORMAL ($84833.8)
 DISCRETE DISPATCHER | Slots: 0/3 Filled ($0.00) | Free: $15.00 | Atomic Breaker: ARMED (Last: 0.0000ms) | Positions: None (All idle quoting) | Top Spinu: MMTUSDT (S=0.00), ESPORTSUSDT (S=0.00), CHZUSDT (S=0.00)
 AUTONOMOUS HIVEMIND | Quarantined (5): APRUSDT, ONUSDT, HANAUSDT, RIVERUSDT, ATUSDT | Screener Top: RIVERUSDT, GRAMUSDT, TRXUSDT | Lead-Lag Snipes: 0 | Protected Quotes: 0
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | MODE         | P/DELTA (ZONE) | SENTINEL   | MID / MICRO         | SPREAD   | KAL/VR     | ETA    | I_ENEMY   | CYC | FILL | NET PNL    
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | DEEP_PYRAMID | 1878 (DILU)    | ROTATE     | 0.18785/0.18782     | 5.32b    | -0.1b|0.94 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 ESPORTSUSDT | DEEP_PYRAMID | 1098 (FORT)    | NONE       | 0.01098/0.01097     | 9.11b    | +0.0b|1.00 | 0.800  | $+0.0     |   0 |    0 | $+0.0000   
 CHZUSDT     | DEEP_PYRAMID | 1625 (DILU)    | ROTATE     | 0.01625/0.01625     | 6.15b    | -0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 OPGUSDT     | DEEP_PYRAMID | 1290 (DILU)    | ROTATE     | 0.12895/0.12897     | 7.75b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 SPELLUSDT   | DEEP_PYRAMID |  982 (FORT)    | NONE       | 0.00010/0.00010     | 10.19b   | -0.0b|0.64 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 PRLUSDT     | DEEP_PYRAMID | 1180 (FORT)    | MONITOR    | 0.11795/0.11792     | 8.48b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 CFGUSDT     | DEEP_PYRAMID | 1460 (DILU)    | ROTATE     | 0.14595/0.14592     | 6.85b    | -0.0b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 OPENUSDT    | DEEP_PYRAMID | 1300 (DILU)    | ROTATE     | 0.12995/0.13000     | 7.70b    | +1.7b|0.69 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 MITOUSDT    | DEEP_PYRAMID | 1570 (DILU)    | ROTATE     | 0.01570/0.01570     | 12.74b   | -0.0b|0.91 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 ARKMUSDT    | DEEP_PYRAMID | 1318 (DILU)    | ROTATE     | 0.13185/0.13188     | 7.58b    | +0.0b|1.00 | 0.450  | $+257.9   |   0 |    0 | $+0.0000   
 ATUSDT      | DEEP_PYRAMID | 1596 (DILU)    | ROTATE     | 0.15965/0.15964     | 6.26b    | +0.0b|0.99 | 0.650  | $+6574.9  |   0 |    0 | $+0.0000   
 ONUSDT      | DEEP_PYRAMID | 1072 (FORT)    | NONE       | 0.10725/0.10727     | 9.32b    | -0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 GRAMUSDT    | DEEP_PYRAMID | 1555 (DILU)    | ROTATE     | 1.555/1.556         | 6.43b    | -0.0b|1.00 | 0.800  | $+19.6    |   0 |    0 | $+0.0000   
 TOSHIUSDT   | DEEP_PYRAMID | 1234 (FORT)    | MONITOR    | 0.00012/0.00012     | 8.10b    | -0.8b|0.87 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 RIVERUSDT   | DEEP_PYRAMID | 1216 (FORT)    | MONITOR    | 1.216/1.216         | 8.22b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 AZTECUSDT   | DEEP_PYRAMID | 1754 (DILU)    | ROTATE     | 0.01754/0.01753     | 5.70b    | +0.0b|1.12 | 0.950  | $+116.9   |   0 |    0 | $+0.0000   
 DEXEUSDT    | DEEP_PYRAMID | 1886 (DILU)    | ROTATE     | 1.886/1.887         | 5.30b    | -0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 RENDERUSDT  | DEEP_PYRAMID | 1928 (DILU)    | ROTATE     | 1.927/1.927         | 5.19b    | -0.0b|1.00 | 0.800  | $+273.4   |   0 |    0 | $+0.0000   
 APEUSDT     | DEEP_PYRAMID | 1487 (DILU)    | ROTATE     | 0.14875/0.14872     | 6.72b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 ORCAUSDT    | DEEP_PYRAMID | 1678 (DILU)    | ROTATE     | 1.677/1.678         | 5.96b    | +0.0b|0.86 | 0.950  | $+6.0     |   0 |    0 | $+0.0000   
 DIAUSDT     | DEEP_PYRAMID | 1666 (DILU)    | ROTATE     | 0.16655/0.16658     | 6.00b    | -0.0b|0.99 | 0.950  | $+6.5     |   0 |    0 | $+0.0000   
 WOOUSDT     | DEEP_PYRAMID | 1372 (DILU)    | ROTATE     | 0.01372/0.01372     | 7.29b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 SHADOW GRADUATION GATE EVALUATOR (Stage 1 Target: 40 Events | Wilson LB >= 0.60 | Net K2 >= +8 bps)
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | STATUS           | CENSUS       | WILSON 95% LB  | SNAP LAW   | FLOW AUC   | GATE VERDICT   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ESPORTSUSDT | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CHZUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPGUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 SPELLUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 PRLUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CFGUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPENUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 MITOUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ARKMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ATUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ONUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 GRAMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 TOSHIUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RIVERUSDT   | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 AZTECUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DEXEUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RENDERUSDT  | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 APEUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ORCAUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DIAUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 WOOUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
================================================================================================================================================================


================================================================================================================================================================
 SOVEREIGN MARKET OS: NESTED HIVEMIND & SENTINEL V18 [0.02h /   1.3m] | WAL: sovereign_fleet_v17.db
 Pool Capital: $25.00 | Active Margin: $0.00 (0.00x) | Reserve: $10.00 | Net PnL: $+0.0000 | Win%:   0.0%
 Peak PnL: $+0.0000 | Current DD: $0.0000 | Max DD: $0.0000 | Breaker: ARMED | BTC: NORMAL ($84806.1)
 DISCRETE DISPATCHER | Slots: 0/3 Filled ($0.00) | Free: $15.00 | Atomic Breaker: ARMED (Last: 0.0000ms) | Positions: None (All idle quoting) | Top Spinu: MMTUSDT (S=0.00), ESPORTSUSDT (S=0.00), CHZUSDT (S=0.00)
 AUTONOMOUS HIVEMIND | Quarantined (5): APRUSDT, ONUSDT, HANAUSDT, RIVERUSDT, ATUSDT | Screener Top: RIVERUSDT, GRAMUSDT, TRXUSDT | Lead-Lag Snipes: 0 | Protected Quotes: 0
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | MODE         | P/DELTA (ZONE) | SENTINEL   | MID / MICRO         | SPREAD   | KAL/VR     | ETA    | I_ENEMY   | CYC | FILL | NET PNL    
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | DEEP_PYRAMID | 1878 (DILU)    | ROTATE     | 0.18775/0.18777     | 5.33b    | -0.1b|0.70 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 ESPORTSUSDT | DEEP_PYRAMID | 1098 (FORT)    | NONE       | 0.01098/0.01097     | 9.11b    | +0.0b|1.00 | 0.800  | $-80.1    |   0 |    0 | $+0.0000   
 CHZUSDT     | DEEP_PYRAMID | 1623 (DILU)    | ROTATE     | 0.01623/0.01624     | 6.16b    | +0.0b|0.91 | 0.850  | $-691.1   |   0 |    0 | $+0.0000   
 OPGUSDT     | DEEP_PYRAMID | 1290 (DILU)    | ROTATE     | 0.12895/0.12898     | 7.75b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 SPELLUSDT   | DEEP_PYRAMID |  980 (FORT)    | NONE       | 0.00010/0.00010     | 10.20b   | +0.0b|1.80 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 PRLUSDT     | DEEP_PYRAMID | 1180 (FORT)    | MONITOR    | 0.11795/0.11791     | 8.48b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 CFGUSDT     | DEEP_PYRAMID | 1458 (DILU)    | ROTATE     | 0.14585/0.14582     | 6.86b    | +0.0b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 OPENUSDT    | DEEP_PYRAMID | 1300 (DILU)    | ROTATE     | 0.12995/0.12996     | 7.70b    | +0.0b|0.31 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 MITOUSDT    | DEEP_PYRAMID | 1568 (DILU)    | ROTATE     | 0.01568/0.01569     | 6.38b    | +0.1b|0.89 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 ARKMUSDT    | DEEP_PYRAMID | 1318 (DILU)    | ROTATE     | 0.13175/0.13176     | 7.59b    | -0.0b|0.99 | 0.450  | $+56.5    |   0 |    0 | $+0.0000   
 ATUSDT      | DEEP_PYRAMID | 1594 (DILU)    | ROTATE     | 0.15940/0.15942     | 12.55b   | -7.1b|0.67 | 0.700  | $-225.4   |   0 |    0 | $+0.0000   
 ONUSDT      | DEEP_PYRAMID | 1073 (FORT)    | NONE       | 0.10730/0.10729     | 18.64b   | +0.0b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 GRAMUSDT    | DEEP_PYRAMID | 1554 (DILU)    | ROTATE     | 1.554/1.555         | 6.43b    | +3.1b|0.99 | 0.850  | $-11360.7 |   0 |    0 | $+0.0000   
 TOSHIUSDT   | DEEP_PYRAMID | 1234 (FORT)    | MONITOR    | 0.00012/0.00012     | 8.10b    | +0.0b|0.86 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 RIVERUSDT   | DEEP_PYRAMID | 1216 (FORT)    | MONITOR    | 1.216/1.216         | 8.22b    | +0.0b|1.00 | 0.650  | $+0.0     |   0 |    0 | $+0.0000   
 AZTECUSDT   | DEEP_PYRAMID | 1754 (DILU)    | ROTATE     | 0.01754/0.01753     | 5.70b    | -0.0b|1.07 | 0.950  | $+116.9   |   0 |    0 | $+0.0000   
 DEXEUSDT    | DEEP_PYRAMID | 1886 (DILU)    | ROTATE     | 1.885/1.885         | 5.30b    | +0.0b|0.99 | 0.700  | $-1707.8  |   0 |    0 | $+0.0000   
 RENDERUSDT  | DEEP_PYRAMID | 1926 (DILU)    | ROTATE     | 1.926/1.926         | 5.19b    | -0.0b|0.99 | 0.800  | $-535.9   |   0 |    0 | $+0.0000   
 APEUSDT     | DEEP_PYRAMID | 1486 (DILU)    | ROTATE     | 0.14855/0.14859     | 6.73b    | -8.1b|0.84 | 0.650  | $-33.4    |   0 |    0 | $+0.0000   
 ORCAUSDT    | DEEP_PYRAMID | 1676 (DILU)    | ROTATE     | 1.676/1.677         | 5.96b    | +0.0b|0.99 | 0.950  | $-243.7   |   0 |    0 | $+0.0000   
 DIAUSDT     | DEEP_PYRAMID | 1664 (DILU)    | ROTATE     | 0.16645/0.16643     | 6.01b    | -0.0b|0.99 | 0.950  | $-631.8   |   0 |    0 | $+0.0000   
 WOOUSDT     | DEEP_PYRAMID | 1371 (DILU)    | ROTATE     | 0.01371/0.01372     | 7.29b    | -0.0b|1.80 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 SHADOW GRADUATION GATE EVALUATOR (Stage 1 Target: 40 Events | Wilson LB >= 0.60 | Net K2 >= +8 bps)
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | STATUS           | CENSUS       | WILSON 95% LB  | SNAP LAW   | FLOW AUC   | GATE VERDICT   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ESPORTSUSDT | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CHZUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPGUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 SPELLUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 PRLUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CFGUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPENUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 MITOUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ARKMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ATUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ONUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 GRAMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 TOSHIUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RIVERUSDT   | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 AZTECUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DEXEUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RENDERUSDT  | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 APEUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ORCAUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DIAUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 WOOUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
================================================================================================================================================================

[ACTIVE] [OPGUSDT] ENTRY FILL: SELL 40.0 @ 0.1291 ($5.16) | slot2
[ACTIVE] [OPGUSDT] PASSIVE EXIT HARVEST: +15.49 bps | Net: $+0.0061 | Total: $+0.0061

================================================================================================================================================================
 SOVEREIGN MARKET OS: NESTED HIVEMIND & SENTINEL V18 [0.03h /   1.5m] | WAL: sovereign_fleet_v17.db
 Pool Capital: $25.00 | Active Margin: $0.00 (0.00x) | Reserve: $10.00 | Net PnL: $+0.0061 | Win%: 100.0%
 Peak PnL: $+0.0061 | Current DD: $0.0000 | Max DD: $0.0000 | Breaker: ARMED | BTC: NORMAL ($84796.7)
 DISCRETE DISPATCHER | Slots: 0/3 Filled ($0.00) | Free: $15.00 | Atomic Breaker: ARMED (Last: 0.0000ms) | Positions: None (All idle quoting) | Top Spinu: MMTUSDT (S=0.00), ESPORTSUSDT (S=0.00), CHZUSDT (S=0.00)
 AUTONOMOUS HIVEMIND | Quarantined (5): APRUSDT, ONUSDT, HANAUSDT, RIVERUSDT, ATUSDT | Screener Top: RIVERUSDT, GRAMUSDT, TRXUSDT | Lead-Lag Snipes: 0 | Protected Quotes: 0
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | MODE         | P/DELTA (ZONE) | SENTINEL   | MID / MICRO         | SPREAD   | KAL/VR     | ETA    | I_ENEMY   | CYC | FILL | NET PNL    
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | DEEP_PYRAMID | 1876 (DILU)    | ROTATE     | 0.18765/0.18768     | 5.33b    | +1.3b|0.83 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 ESPORTSUSDT | DEEP_PYRAMID | 1098 (FORT)    | NONE       | 0.01098/0.01098     | 9.11b    | +0.0b|1.00 | 0.800  | $+0.0     |   0 |    0 | $+0.0000   
 CHZUSDT     | DEEP_PYRAMID | 1623 (DILU)    | ROTATE     | 0.01623/0.01624     | 6.16b    | -0.4b|1.29 | 0.850  | $+292.1   |   0 |    0 | $+0.0000   
 OPGUSDT     | DEEP_PYRAMID | 1288 (DILU)    | ROTATE     | 0.12885/0.12889     | 7.76b    | -7.5b|0.92 | 0.950  | $+603.5   |   0 |    1 | $+0.0061   
 SPELLUSDT   | DEEP_PYRAMID |  980 (FORT)    | NONE       | 0.00010/0.00010     | 10.20b   | -0.0b|1.80 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 PRLUSDT     | DEEP_PYRAMID | 1178 (FORT)    | MONITOR    | 0.11785/0.11785     | 8.49b    | -0.0b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 CFGUSDT     | DEEP_PYRAMID | 1458 (DILU)    | ROTATE     | 0.14585/0.14581     | 6.86b    | -0.0b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 OPENUSDT    | DEEP_PYRAMID | 1300 (DILU)    | ROTATE     | 0.12995/0.12998     | 7.70b    | -4.3b|0.99 | 0.800  | $+1041.8  |   0 |    0 | $+0.0000   
 MITOUSDT    | DEEP_PYRAMID | 1568 (DILU)    | ROTATE     | 0.01568/0.01568     | 6.38b    | +7.6b|0.87 | 0.950  | $+620.8   |   0 |    0 | $+0.0000   
 ARKMUSDT    | DEEP_PYRAMID | 1318 (DILU)    | ROTATE     | 0.13175/0.13179     | 7.59b    | -0.0b|1.00 | 0.450  | $+0.0     |   0 |    0 | $+0.0000   
 ATUSDT      | DEEP_PYRAMID | 1598 (DILU)    | ROTATE     | 0.15975/0.15971     | 6.26b    | +0.2b|1.15 | 0.850  | $+2644.3  |   0 |    0 | $+0.0000   
 ONUSDT      | DEEP_PYRAMID | 1074 (FORT)    | RETREAT    | 0.10735/0.10731     | 9.32b    | +0.0b|0.64 | 0.300  | $-75.8    |   0 |    0 | $+0.0000   
 GRAMUSDT    | DEEP_PYRAMID | 1555 (DILU)    | ROTATE     | 1.555/1.555         | 6.43b    | +0.8b|0.99 | 0.900  | $-5277.1  |   0 |    0 | $+0.0000   
 TOSHIUSDT   | DEEP_PYRAMID | 1234 (FORT)    | MONITOR    | 0.00012/0.00012     | 8.10b    | +0.0b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 RIVERUSDT   | DEEP_PYRAMID | 1216 (FORT)    | RETREAT    | 1.216/1.216         | 8.22b    | +0.0b|1.00 | 0.650  | $+0.0     |   0 |    0 | $+0.0000   
 AZTECUSDT   | DEEP_PYRAMID | 1752 (DILU)    | ROTATE     | 0.01752/0.01753     | 5.71b    | -0.4b|1.54 | 0.950  | $-96.8    |   0 |    0 | $+0.0000   
 DEXEUSDT    | DEEP_PYRAMID | 1886 (DILU)    | ROTATE     | 1.885/1.885         | 5.30b    | +0.0b|1.00 | 0.700  | $+13.3    |   0 |    0 | $+0.0000   
 RENDERUSDT  | DEEP_PYRAMID | 1926 (DILU)    | ROTATE     | 1.926/1.926         | 5.19b    | +0.0b|1.00 | 0.650  | $-572.6   |   0 |    0 | $+0.0000   
 APEUSDT     | DEEP_PYRAMID | 1486 (DILU)    | ROTATE     | 0.14855/0.14859     | 6.73b    | +1.9b|1.07 | 0.650  | $-307.6   |   0 |    0 | $+0.0000   
 ORCAUSDT    | DEEP_PYRAMID | 1676 (DILU)    | ROTATE     | 1.676/1.677         | 5.96b    | -0.0b|1.00 | 0.950  | $+13.2    |   0 |    0 | $+0.0000   
 DIAUSDT     | DEEP_PYRAMID | 1664 (DILU)    | ROTATE     | 0.16645/0.16649     | 6.01b    | +3.9b|0.84 | 0.800  | $+93.2    |   0 |    0 | $+0.0000   
 WOOUSDT     | DEEP_PYRAMID | 1371 (DILU)    | ROTATE     | 0.01371/0.01372     | 7.29b    | +2.5b|0.96 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 SHADOW GRADUATION GATE EVALUATOR (Stage 1 Target: 40 Events | Wilson LB >= 0.60 | Net K2 >= +8 bps)
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | STATUS           | CENSUS       | WILSON 95% LB  | SNAP LAW   | FLOW AUC   | GATE VERDICT   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ESPORTSUSDT | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CHZUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPGUSDT     | SHADOW_QUARANTINE |  1/40 (0.0h) | 0.207          | FAIL/PEND  | 8.00       | MONITOR        
 SPELLUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 PRLUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CFGUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPENUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 MITOUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ARKMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ATUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ONUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 GRAMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 TOSHIUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RIVERUSDT   | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 AZTECUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DEXEUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RENDERUSDT  | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 APEUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ORCAUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DIAUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 WOOUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 RECENT EXECUTION & AUDIT FEED
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 [18:16:19] [OPGUSDT   ] ENTRY_FILL             | SELL 40.0 @ 0.1291 ($5.16) | slot2
 [18:16:21] [OPGUSDT   ] PASSIVE_HARVEST        | +15.49 bps | Net: $+0.0061 | Total: $+0.0061
================================================================================================================================================================


================================================================================================================================================================
 SOVEREIGN MARKET OS: NESTED HIVEMIND & SENTINEL V18 [0.03h /   1.8m] | WAL: sovereign_fleet_v17.db
 Pool Capital: $25.00 | Active Margin: $0.00 (0.00x) | Reserve: $10.00 | Net PnL: $+0.0061 | Win%: 100.0%
 Peak PnL: $+0.0061 | Current DD: $0.0000 | Max DD: $0.0000 | Breaker: ARMED | BTC: NORMAL ($84804.2)
 DISCRETE DISPATCHER | Slots: 0/3 Filled ($0.00) | Free: $15.00 | Atomic Breaker: ARMED (Last: 0.0000ms) | Positions: None (All idle quoting) | Top Spinu: MMTUSDT (S=0.00), ESPORTSUSDT (S=0.00), CHZUSDT (S=0.00)
 AUTONOMOUS HIVEMIND | Quarantined (5): APRUSDT, ONUSDT, HANAUSDT, RIVERUSDT, ATUSDT | Screener Top: RIVERUSDT, GRAMUSDT, TRXUSDT | Lead-Lag Snipes: 0 | Protected Quotes: 0
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | MODE         | P/DELTA (ZONE) | SENTINEL   | MID / MICRO         | SPREAD   | KAL/VR     | ETA    | I_ENEMY   | CYC | FILL | NET PNL    
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | DEEP_PYRAMID | 1877 (DILU)    | ROTATE     | 0.18770/0.18764     | 10.66b   | -0.0b|0.78 | 0.450  | $+0.0     |   0 |    0 | $+0.0000   
 ESPORTSUSDT | DEEP_PYRAMID | 1098 (FORT)    | NONE       | 0.01098/0.01097     | 9.11b    | +0.0b|1.00 | 0.800  | $-47.6    |   0 |    0 | $+0.0000   
 CHZUSDT     | DEEP_PYRAMID | 1625 (DILU)    | ROTATE     | 0.01625/0.01625     | 6.16b    | -0.0b|0.99 | 0.850  | $-56.4    |   0 |    0 | $+0.0000   
 OPGUSDT     | DEEP_PYRAMID | 1288 (DILU)    | ROTATE     | 0.12885/0.12889     | 7.76b    | +0.0b|1.07 | 0.950  | $+603.5   |   0 |    1 | $+0.0061   
 SPELLUSDT   | DEEP_PYRAMID |  980 (FORT)    | NONE       | 0.00010/0.00010     | 10.20b   | +0.0b|1.80 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 PRLUSDT     | DEEP_PYRAMID | 1178 (FORT)    | MONITOR    | 0.11785/0.11785     | 8.49b    | -0.0b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 CFGUSDT     | DEEP_PYRAMID | 1456 (DILU)    | ROTATE     | 0.14555/0.14559     | 6.87b    | +0.0b|0.99 | 0.950  | $+21.4    |   0 |    0 | $+0.0000   
 OPENUSDT    | DEEP_PYRAMID | 1300 (DILU)    | ROTATE     | 0.12995/0.12999     | 7.70b    | +0.0b|1.00 | 0.800  | $+1041.8  |   0 |    0 | $+0.0000   
 MITOUSDT    | DEEP_PYRAMID | 1568 (DILU)    | ROTATE     | 0.01568/0.01568     | 6.38b    | +0.3b|0.85 | 0.950  | $-53.8    |   0 |    0 | $+0.0000   
 ARKMUSDT    | DEEP_PYRAMID | 1318 (DILU)    | ROTATE     | 0.13175/0.13179     | 7.59b    | +0.0b|1.00 | 0.450  | $+0.0     |   0 |    0 | $+0.0000   
 ATUSDT      | DEEP_PYRAMID | 1598 (DILU)    | ROTATE     | 0.15975/0.15973     | 6.26b    | +0.0b|0.99 | 0.850  | $+4586.9  |   0 |    0 | $+0.0000   
 ONUSDT      | DEEP_PYRAMID | 1074 (FORT)    | RETREAT    | 0.10735/0.10737     | 9.32b    | +0.0b|1.00 | 0.300  | $+127.8   |   0 |    0 | $+0.0000   
 GRAMUSDT    | DEEP_PYRAMID | 1555 (DILU)    | ROTATE     | 1.555/1.555         | 6.43b    | +0.0b|1.07 | 0.900  | $-56.4    |   0 |    0 | $+0.0000   
 TOSHIUSDT   | DEEP_PYRAMID | 1234 (FORT)    | MONITOR    | 0.00012/0.00012     | 8.10b    | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 RIVERUSDT   | DEEP_PYRAMID | 1216 (FORT)    | RETREAT    | 1.216/1.216         | 8.22b    | -0.0b|1.00 | 0.650  | $-166.3   |   0 |    0 | $+0.0000   
 AZTECUSDT   | DEEP_PYRAMID | 1752 (DILU)    | ROTATE     | 0.01752/0.01753     | 5.71b    | +0.0b|1.58 | 0.950  | $-55.9    |   0 |    0 | $+0.0000   
 DEXEUSDT    | DEEP_PYRAMID | 1886 (DILU)    | ROTATE     | 1.885/1.886         | 5.30b    | -0.0b|1.00 | 0.700  | $-23.0    |   0 |    0 | $+0.0000   
 RENDERUSDT  | DEEP_PYRAMID | 1926 (DILU)    | ROTATE     | 1.926/1.927         | 5.19b    | -0.0b|1.00 | 0.700  | $+557.9   |   0 |    0 | $+0.0000   
 APEUSDT     | DEEP_PYRAMID | 1486 (DILU)    | ROTATE     | 0.14855/0.14851     | 6.73b    | +0.0b|1.07 | 0.650  | $-399.4   |   0 |    0 | $+0.0000   
 ORCAUSDT    | DEEP_PYRAMID | 1676 (DILU)    | ROTATE     | 1.676/1.676         | 5.96b    | -0.0b|1.36 | 0.700  | $-1767.3  |   0 |    0 | $+0.0000   
 DIAUSDT     | DEEP_PYRAMID | 1664 (DILU)    | ROTATE     | 0.16645/0.16646     | 6.01b    | +0.0b|0.86 | 0.800  | $+93.2    |   0 |    0 | $+0.0000   
 WOOUSDT     | DEEP_PYRAMID | 1371 (DILU)    | ROTATE     | 0.01371/0.01372     | 7.29b    | -4.8b|0.23 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 SHADOW GRADUATION GATE EVALUATOR (Stage 1 Target: 40 Events | Wilson LB >= 0.60 | Net K2 >= +8 bps)
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | STATUS           | CENSUS       | WILSON 95% LB  | SNAP LAW   | FLOW AUC   | GATE VERDICT   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ESPORTSUSDT | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CHZUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPGUSDT     | SHADOW_QUARANTINE |  1/40 (0.0h) | 0.207          | FAIL/PEND  | 8.00       | MONITOR        
 SPELLUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 PRLUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CFGUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPENUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 MITOUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ARKMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ATUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ONUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 GRAMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 TOSHIUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RIVERUSDT   | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 AZTECUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DEXEUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RENDERUSDT  | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 APEUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ORCAUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DIAUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 WOOUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 RECENT EXECUTION & AUDIT FEED
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 [18:16:19] [OPGUSDT   ] ENTRY_FILL             | SELL 40.0 @ 0.1291 ($5.16) | slot2
 [18:16:21] [OPGUSDT   ] PASSIVE_HARVEST        | +15.49 bps | Net: $+0.0061 | Total: $+0.0061
================================================================================================================================================================


================================================================================================================================================================
 SOVEREIGN MARKET OS: NESTED HIVEMIND & SENTINEL V18 [0.03h /   2.0m] | WAL: sovereign_fleet_v17.db
 Pool Capital: $25.00 | Active Margin: $0.00 (0.00x) | Reserve: $10.00 | Net PnL: $+0.0061 | Win%: 100.0%
 Peak PnL: $+0.0061 | Current DD: $0.0000 | Max DD: $0.0000 | Breaker: ARMED | BTC: NORMAL ($84789.2)
 DISCRETE DISPATCHER | Slots: 0/3 Filled ($0.00) | Free: $15.00 | Atomic Breaker: ARMED (Last: 0.0000ms) | Positions: None (All idle quoting) | Top Spinu: MMTUSDT (S=0.00), ESPORTSUSDT (S=0.00), CHZUSDT (S=0.00)
 AUTONOMOUS HIVEMIND | Quarantined (5): APRUSDT, ONUSDT, HANAUSDT, RIVERUSDT, ATUSDT | Screener Top: RIVERUSDT, GRAMUSDT, TRXUSDT | Lead-Lag Snipes: 0 | Protected Quotes: 0
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | MODE         | P/DELTA (ZONE) | SENTINEL   | MID / MICRO         | SPREAD   | KAL/VR     | ETA    | I_ENEMY   | CYC | FILL | NET PNL    
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | DEEP_PYRAMID | 1877 (DILU)    | ROTATE     | 0.18770/0.18764     | 10.66b   | +0.0b|0.75 | 0.450  | $+0.0     |   0 |    0 | $+0.0000   
 ESPORTSUSDT | DEEP_PYRAMID | 1098 (FORT)    | NONE       | 0.01098/0.01097     | 9.11b    | +0.0b|1.00 | 0.800  | $+0.0     |   0 |    0 | $+0.0000   
 CHZUSDT     | DEEP_PYRAMID | 1625 (DILU)    | ROTATE     | 0.01625/0.01625     | 6.16b    | +0.0b|1.00 | 0.850  | $-56.4    |   0 |    0 | $+0.0000   
 OPGUSDT     | DEEP_PYRAMID | 1288 (DILU)    | ROTATE     | 0.12885/0.12888     | 7.76b    | +0.0b|1.07 | 0.950  | $+603.5   |   0 |    1 | $+0.0061   
 SPELLUSDT   | DEEP_PYRAMID |  980 (FORT)    | NONE       | 0.00010/0.00010     | 10.20b   | -0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 PRLUSDT     | DEEP_PYRAMID | 1178 (FORT)    | MONITOR    | 0.11785/0.11785     | 8.49b    | +0.0b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 CFGUSDT     | DEEP_PYRAMID | 1456 (DILU)    | ROTATE     | 0.14565/0.14568     | 6.87b    | -0.0b|0.99 | 0.950  | $+125.9   |   0 |    0 | $+0.0000   
 OPENUSDT    | DEEP_PYRAMID | 1300 (DILU)    | ROTATE     | 0.12995/0.12999     | 7.70b    | +0.0b|1.00 | 0.800  | $+1041.8  |   0 |    0 | $+0.0000   
 MITOUSDT    | DEEP_PYRAMID | 1568 (DILU)    | ROTATE     | 0.01568/0.01568     | 6.38b    | +0.0b|0.88 | 0.950  | $-62.9    |   0 |    0 | $+0.0000   
 ARKMUSDT    | DEEP_PYRAMID | 1318 (DILU)    | ROTATE     | 0.13175/0.13176     | 7.59b    | -0.0b|1.00 | 0.450  | $-134.2   |   0 |    0 | $+0.0000   
 ATUSDT      | DEEP_PYRAMID | 1598 (DILU)    | ROTATE     | 0.15975/0.15972     | 6.26b    | +0.0b|1.00 | 0.650  | $+6820.4  |   0 |    0 | $+0.0000   
 ONUSDT      | DEEP_PYRAMID | 1072 (FORT)    | RETREAT    | 0.10725/0.10726     | 9.32b    | +0.0b|0.99 | 0.800  | $-228.1   |   0 |    0 | $+0.0000   
 GRAMUSDT    | DEEP_PYRAMID | 1555 (DILU)    | ROTATE     | 1.555/1.556         | 6.43b    | -0.0b|1.00 | 0.800  | $-318.8   |   0 |    0 | $+0.0000   
 TOSHIUSDT   | DEEP_PYRAMID | 1234 (FORT)    | MONITOR    | 0.00012/0.00012     | 8.10b    | -0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 RIVERUSDT   | DEEP_PYRAMID | 1216 (FORT)    | RETREAT    | 1.216/1.216         | 8.22b    | -0.0b|1.00 | 0.650  | $+64.1    |   0 |    0 | $+0.0000   
 AZTECUSDT   | DEEP_PYRAMID | 1752 (DILU)    | ROTATE     | 0.01752/0.01753     | 5.71b    | +0.0b|1.58 | 0.950  | $-55.9    |   0 |    0 | $+0.0000   
 DEXEUSDT    | DEEP_PYRAMID | 1886 (DILU)    | ROTATE     | 1.885/1.885         | 5.30b    | -0.0b|1.00 | 0.700  | $-670.9   |   0 |    0 | $+0.0000   
 RENDERUSDT  | DEEP_PYRAMID | 1926 (DILU)    | ROTATE     | 1.926/1.926         | 5.19b    | -0.0b|1.00 | 0.800  | $+0.0     |   0 |    0 | $+0.0000   
 APEUSDT     | DEEP_PYRAMID | 1486 (DILU)    | ROTATE     | 0.14855/0.14851     | 6.73b    | -0.0b|1.00 | 0.650  | $-399.4   |   0 |    0 | $+0.0000   
 ORCAUSDT    | DEEP_PYRAMID | 1676 (DILU)    | ROTATE     | 1.676/1.676         | 5.96b    | -0.0b|1.00 | 0.700  | $-15.8    |   0 |    0 | $+0.0000   
 DIAUSDT     | DEEP_PYRAMID | 1664 (DILU)    | ROTATE     | 0.16645/0.16645     | 6.01b    | +0.0b|0.86 | 0.800  | $+93.2    |   0 |    0 | $+0.0000   
 WOOUSDT     | DEEP_PYRAMID | 1371 (DILU)    | ROTATE     | 0.01371/0.01372     | 7.29b    | -4.1b|0.22 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 SHADOW GRADUATION GATE EVALUATOR (Stage 1 Target: 40 Events | Wilson LB >= 0.60 | Net K2 >= +8 bps)
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | STATUS           | CENSUS       | WILSON 95% LB  | SNAP LAW   | FLOW AUC   | GATE VERDICT   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ESPORTSUSDT | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CHZUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPGUSDT     | SHADOW_QUARANTINE |  1/40 (0.0h) | 0.207          | FAIL/PEND  | 8.00       | MONITOR        
 SPELLUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 PRLUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CFGUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPENUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 MITOUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ARKMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ATUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ONUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 GRAMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 TOSHIUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RIVERUSDT   | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 AZTECUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DEXEUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RENDERUSDT  | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 APEUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ORCAUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DIAUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 WOOUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 RECENT EXECUTION & AUDIT FEED
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 [18:16:19] [OPGUSDT   ] ENTRY_FILL             | SELL 40.0 @ 0.1291 ($5.16) | slot2
 [18:16:21] [OPGUSDT   ] PASSIVE_HARVEST        | +15.49 bps | Net: $+0.0061 | Total: $+0.0061
================================================================================================================================================================


================================================================================================================================================================
 SOVEREIGN MARKET OS: NESTED HIVEMIND & SENTINEL V18 [0.04h /   2.3m] | WAL: sovereign_fleet_v17.db
 Pool Capital: $25.00 | Active Margin: $0.00 (0.00x) | Reserve: $10.00 | Net PnL: $+0.0061 | Win%: 100.0%
 Peak PnL: $+0.0061 | Current DD: $0.0000 | Max DD: $0.0000 | Breaker: ARMED | BTC: NORMAL ($84819.9)
 DISCRETE DISPATCHER | Slots: 0/3 Filled ($0.00) | Free: $15.00 | Atomic Breaker: ARMED (Last: 0.0000ms) | Positions: None (All idle quoting) | Top Spinu: MMTUSDT (S=0.00), ESPORTSUSDT (S=0.00), CHZUSDT (S=0.00)
 AUTONOMOUS HIVEMIND | Quarantined (5): APRUSDT, ONUSDT, HANAUSDT, RIVERUSDT, ATUSDT | Screener Top: RIVERUSDT, GRAMUSDT, PLUMEUSDT | Lead-Lag Snipes: 0 | Protected Quotes: 0
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | MODE         | P/DELTA (ZONE) | SENTINEL   | MID / MICRO         | SPREAD   | KAL/VR     | ETA    | I_ENEMY   | CYC | FILL | NET PNL    
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | DEEP_PYRAMID | 1878 (DILU)    | ROTATE     | 0.18775/0.18776     | 5.33b    | +0.6b|0.94 | 0.450  | $+194.5   |   0 |    0 | $+0.0000   
 ESPORTSUSDT | DEEP_PYRAMID | 1098 (FORT)    | MONITOR    | 0.01098/0.01097     | 9.11b    | +0.0b|1.00 | 0.800  | $+10.3    |   0 |    0 | $+0.0000   
 CHZUSDT     | DEEP_PYRAMID | 1625 (DILU)    | ROTATE     | 0.01625/0.01625     | 6.16b    | +0.0b|1.00 | 0.850  | $+30.1    |   0 |    0 | $+0.0000   
 OPGUSDT     | DEEP_PYRAMID | 1288 (DILU)    | ROTATE     | 0.12885/0.12887     | 7.76b    | -0.0b|0.99 | 0.950  | $+603.5   |   0 |    1 | $+0.0061   
 SPELLUSDT   | DEEP_PYRAMID |  980 (FORT)    | NONE       | 0.00010/0.00010     | 10.20b   | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 PRLUSDT     | DEEP_PYRAMID | 1180 (FORT)    | MONITOR    | 0.11795/0.11795     | 8.48b    | -7.7b|0.85 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 CFGUSDT     | DEEP_PYRAMID | 1456 (DILU)    | ROTATE     | 0.14565/0.14563     | 6.87b    | -0.0b|1.00 | 0.950  | $-506.2   |   0 |    0 | $+0.0000   
 OPENUSDT    | DEEP_PYRAMID | 1300 (DILU)    | ROTATE     | 0.13005/0.13003     | 7.69b    | -6.3b|0.99 | 0.800  | $+55.1    |   0 |    0 | $+0.0000   
 MITOUSDT    | DEEP_PYRAMID | 1568 (DILU)    | ROTATE     | 0.01568/0.01568     | 6.38b    | -0.0b|1.00 | 0.950  | $+44.4    |   0 |    0 | $+0.0000   
 ARKMUSDT    | DEEP_PYRAMID | 1318 (DILU)    | ROTATE     | 0.13185/0.13181     | 7.58b    | -2.1b|0.99 | 0.450  | $+71.7    |   0 |    0 | $+0.0000   
 ATUSDT      | DEEP_PYRAMID | 1596 (DILU)    | ROTATE     | 0.15965/0.15964     | 6.26b    | +0.0b|0.99 | 0.700  | $+764.2   |   0 |    0 | $+0.0000   
 ONUSDT      | DEEP_PYRAMID | 1073 (FORT)    | RETREAT    | 0.10730/0.10723     | 18.64b   | +11.8b|0.42 | 0.800  | $+52.2    |   0 |    0 | $+0.0000   
 GRAMUSDT    | DEEP_PYRAMID | 1554 (DILU)    | ROTATE     | 1.554/1.555         | 6.43b    | +0.0b|0.62 | 0.800  | $+703.8   |   0 |    0 | $+0.0000   
 TOSHIUSDT   | DEEP_PYRAMID | 1234 (FORT)    | RETREAT    | 0.00012/0.00012     | 8.10b    | -26.8b|0.61 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 RIVERUSDT   | DEEP_PYRAMID | 1216 (FORT)    | RETREAT    | 1.216/1.217         | 8.22b    | +0.0b|1.00 | 0.650  | $-426.7   |   0 |    0 | $+0.0000   
 AZTECUSDT   | DEEP_PYRAMID | 1755 (DILU)    | ROTATE     | 0.01755/0.01755     | 11.40b   | +0.6b|0.99 | 0.950  | $+647.5   |   0 |    0 | $+0.0000   
 DEXEUSDT    | DEEP_PYRAMID | 1886 (DILU)    | ROTATE     | 1.885/1.885         | 5.30b    | -0.0b|1.00 | 0.700  | $+0.0     |   0 |    0 | $+0.0000   
 RENDERUSDT  | DEEP_PYRAMID | 1928 (DILU)    | ROTATE     | 1.927/1.927         | 5.19b    | +0.0b|0.99 | 0.800  | $+209.5   |   0 |    0 | $+0.0000   
 APEUSDT     | DEEP_PYRAMID | 1486 (DILU)    | ROTATE     | 0.14865/0.14864     | 6.73b    | +0.0b|0.99 | 0.650  | $+11006.7 |   0 |    0 | $+0.0000   
 ORCAUSDT    | DEEP_PYRAMID | 1676 (DILU)    | ROTATE     | 1.676/1.676         | 5.96b    | -0.0b|1.07 | 0.700  | $-198.1   |   0 |    0 | $+0.0000   
 DIAUSDT     | DEEP_PYRAMID | 1664 (DILU)    | ROTATE     | 0.16645/0.16641     | 6.01b    | +0.0b|1.00 | 0.800  | $-194.2   |   0 |    0 | $+0.0000   
 WOOUSDT     | DEEP_PYRAMID | 1372 (DILU)    | ROTATE     | 0.01372/0.01372     | 7.29b    | -2.2b|0.27 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 SHADOW GRADUATION GATE EVALUATOR (Stage 1 Target: 40 Events | Wilson LB >= 0.60 | Net K2 >= +8 bps)
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | STATUS           | CENSUS       | WILSON 95% LB  | SNAP LAW   | FLOW AUC   | GATE VERDICT   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ESPORTSUSDT | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CHZUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPGUSDT     | SHADOW_QUARANTINE |  1/40 (0.0h) | 0.207          | FAIL/PEND  | 8.00       | MONITOR        
 SPELLUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 PRLUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CFGUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPENUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 MITOUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ARKMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ATUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ONUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 GRAMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 TOSHIUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RIVERUSDT   | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 AZTECUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DEXEUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RENDERUSDT  | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 APEUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ORCAUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DIAUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 WOOUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 RECENT EXECUTION & AUDIT FEED
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 [18:16:19] [OPGUSDT   ] ENTRY_FILL             | SELL 40.0 @ 0.1291 ($5.16) | slot2
 [18:16:21] [OPGUSDT   ] PASSIVE_HARVEST        | +15.49 bps | Net: $+0.0061 | Total: $+0.0061
================================================================================================================================================================


================================================================================================================================================================
 SOVEREIGN MARKET OS: NESTED HIVEMIND & SENTINEL V18 [0.04h /   2.5m] | WAL: sovereign_fleet_v17.db
 Pool Capital: $25.00 | Active Margin: $0.00 (0.00x) | Reserve: $10.00 | Net PnL: $+0.0061 | Win%: 100.0%
 Peak PnL: $+0.0061 | Current DD: $0.0000 | Max DD: $0.0000 | Breaker: ARMED | BTC: NORMAL ($84833.1)
 DISCRETE DISPATCHER | Slots: 0/3 Filled ($0.00) | Free: $15.00 | Atomic Breaker: ARMED (Last: 0.0000ms) | Positions: None (All idle quoting) | Top Spinu: MMTUSDT (S=0.00), ESPORTSUSDT (S=0.00), CHZUSDT (S=0.00)
 AUTONOMOUS HIVEMIND | Quarantined (5): APRUSDT, ONUSDT, HANAUSDT, RIVERUSDT, ATUSDT | Screener Top: RIVERUSDT, GRAMUSDT, PLUMEUSDT | Lead-Lag Snipes: 0 | Protected Quotes: 0
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | MODE         | P/DELTA (ZONE) | SENTINEL   | MID / MICRO         | SPREAD   | KAL/VR     | ETA    | I_ENEMY   | CYC | FILL | NET PNL    
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | DEEP_PYRAMID | 1878 (DILU)    | ROTATE     | 0.18775/0.18778     | 5.33b    | +0.0b|1.06 | 0.450  | $+200.5   |   0 |    0 | $+0.0000   
 ESPORTSUSDT | DEEP_PYRAMID | 1098 (FORT)    | NONE       | 0.01098/0.01097     | 9.11b    | +0.0b|1.00 | 0.600  | $+0.0     |   0 |    0 | $+0.0000   
 CHZUSDT     | DEEP_PYRAMID | 1625 (DILU)    | ROTATE     | 0.01625/0.01625     | 6.15b    | +0.0b|0.99 | 0.700  | $+1068.2  |   0 |    0 | $+0.0000   
 OPGUSDT     | DEEP_PYRAMID | 1288 (DILU)    | ROTATE     | 0.12885/0.12886     | 7.76b    | -0.0b|1.00 | 0.950  | $-118.0   |   0 |    1 | $+0.0061   
 SPELLUSDT   | DEEP_PYRAMID |  980 (FORT)    | NONE       | 0.00010/0.00010     | 10.20b   | -0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 PRLUSDT     | DEEP_PYRAMID | 1180 (FORT)    | MONITOR    | 0.11795/0.11795     | 8.48b    | -0.5b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 CFGUSDT     | DEEP_PYRAMID | 1456 (DILU)    | ROTATE     | 0.14565/0.14568     | 6.87b    | -0.0b|1.00 | 0.950  | $-506.2   |   0 |    0 | $+0.0000   
 OPENUSDT    | DEEP_PYRAMID | 1300 (DILU)    | ROTATE     | 0.13005/0.13003     | 7.69b    | -0.1b|0.99 | 0.800  | $+93.4    |   0 |    0 | $+0.0000   
 MITOUSDT    | DEEP_PYRAMID | 1568 (DILU)    | ROTATE     | 0.01568/0.01568     | 12.76b   | -0.2b|0.99 | 0.700  | $-15.5    |   0 |    0 | $+0.0000   
 ARKMUSDT    | DEEP_PYRAMID | 1318 (DILU)    | ROTATE     | 0.13185/0.13183     | 7.58b    | +0.0b|0.99 | 0.550  | $-14.1    |   0 |    0 | $+0.0000   
 ATUSDT      | DEEP_PYRAMID | 1598 (DILU)    | ROTATE     | 0.15985/0.15985     | 6.26b    | -0.0b|0.99 | 0.700  | $+4195.0  |   0 |    0 | $+0.0000   
 ONUSDT      | DEEP_PYRAMID | 1072 (FORT)    | RETREAT    | 0.10725/0.10730     | 9.32b    | +0.0b|1.07 | 0.650  | $+36.8    |   0 |    0 | $+0.0000   
 GRAMUSDT    | DEEP_PYRAMID | 1554 (DILU)    | ROTATE     | 1.554/1.555         | 6.43b    | -0.0b|1.00 | 0.850  | $+3352.4  |   0 |    0 | $+0.0000   
 TOSHIUSDT   | DEEP_PYRAMID | 1234 (FORT)    | RETREAT    | 0.00012/0.00012     | 8.10b    | +0.0b|1.07 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 RIVERUSDT   | DEEP_PYRAMID | 1218 (FORT)    | RETREAT    | 1.218/1.218         | 8.21b    | -0.0b|0.99 | 0.650  | $+1158.0  |   0 |    0 | $+0.0000   
 AZTECUSDT   | DEEP_PYRAMID | 1754 (DILU)    | ROTATE     | 0.01754/0.01755     | 5.70b    | +0.1b|1.07 | 0.800  | $+0.0     |   0 |    0 | $+0.0000   
 DEXEUSDT    | DEEP_PYRAMID | 1886 (DILU)    | ROTATE     | 1.885/1.886         | 5.30b    | +0.0b|1.00 | 0.700  | $-11.9    |   0 |    0 | $+0.0000   
 RENDERUSDT  | DEEP_PYRAMID | 1928 (DILU)    | ROTATE     | 1.929/1.928         | 5.19b    | +0.0b|0.99 | 0.850  | $+3608.8  |   0 |    0 | $+0.0000   
 APEUSDT     | DEEP_PYRAMID | 1488 (DILU)    | ROTATE     | 0.14885/0.14884     | 6.72b    | +0.0b|0.99 | 0.650  | $+1185.9  |   0 |    0 | $+0.0000   
 ORCAUSDT    | DEEP_PYRAMID | 1678 (DILU)    | ROTATE     | 1.679/1.678         | 5.96b    | +0.0b|0.91 | 0.750  | $+229.4   |   0 |    0 | $+0.0000   
 DIAUSDT     | DEEP_PYRAMID | 1664 (DILU)    | ROTATE     | 0.16645/0.16642     | 6.01b    | +0.0b|1.00 | 0.800  | $-194.2   |   0 |    0 | $+0.0000   
 WOOUSDT     | DEEP_PYRAMID | 1372 (DILU)    | ROTATE     | 0.01372/0.01372     | 7.29b    | -0.1b|0.30 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 SHADOW GRADUATION GATE EVALUATOR (Stage 1 Target: 40 Events | Wilson LB >= 0.60 | Net K2 >= +8 bps)
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | STATUS           | CENSUS       | WILSON 95% LB  | SNAP LAW   | FLOW AUC   | GATE VERDICT   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ESPORTSUSDT | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CHZUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPGUSDT     | SHADOW_QUARANTINE |  1/40 (0.0h) | 0.207          | FAIL/PEND  | 8.00       | MONITOR        
 SPELLUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 PRLUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CFGUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPENUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 MITOUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ARKMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ATUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ONUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 GRAMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 TOSHIUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RIVERUSDT   | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 AZTECUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DEXEUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RENDERUSDT  | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 APEUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ORCAUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DIAUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 WOOUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 RECENT EXECUTION & AUDIT FEED
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 [18:16:19] [OPGUSDT   ] ENTRY_FILL             | SELL 40.0 @ 0.1291 ($5.16) | slot2
 [18:16:21] [OPGUSDT   ] PASSIVE_HARVEST        | +15.49 bps | Net: $+0.0061 | Total: $+0.0061
================================================================================================================================================================


================================================================================================================================================================
 SOVEREIGN MARKET OS: NESTED HIVEMIND & SENTINEL V18 [0.05h /   2.8m] | WAL: sovereign_fleet_v17.db
 Pool Capital: $25.00 | Active Margin: $0.00 (0.00x) | Reserve: $10.00 | Net PnL: $+0.0061 | Win%: 100.0%
 Peak PnL: $+0.0061 | Current DD: $0.0000 | Max DD: $0.0000 | Breaker: ARMED | BTC: NORMAL ($84793.9)
 DISCRETE DISPATCHER | Slots: 0/3 Filled ($0.00) | Free: $15.00 | Atomic Breaker: ARMED (Last: 0.0000ms) | Positions: None (All idle quoting) | Top Spinu: MMTUSDT (S=0.00), ESPORTSUSDT (S=0.00), CHZUSDT (S=0.00)
 AUTONOMOUS HIVEMIND | Quarantined (5): APRUSDT, ONUSDT, HANAUSDT, RIVERUSDT, ATUSDT | Screener Top: RIVERUSDT, GRAMUSDT, PLUMEUSDT | Lead-Lag Snipes: 0 | Protected Quotes: 0
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | MODE         | P/DELTA (ZONE) | SENTINEL   | MID / MICRO         | SPREAD   | KAL/VR     | ETA    | I_ENEMY   | CYC | FILL | NET PNL    
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | DEEP_PYRAMID | 1878 (DILU)    | ROTATE     | 0.18775/0.18775     | 5.33b    | -0.0b|1.00 | 0.450  | $+71.7    |   0 |    0 | $+0.0000   
 ESPORTSUSDT | DEEP_PYRAMID | 1098 (FORT)    | NONE       | 0.01098/0.01098     | 9.11b    | +0.0b|1.00 | 0.600  | $+0.0     |   0 |    0 | $+0.0000   
 CHZUSDT     | DEEP_PYRAMID | 1625 (DILU)    | ROTATE     | 0.01625/0.01624     | 6.16b    | +0.0b|0.99 | 0.700  | $+0.0     |   0 |    0 | $+0.0000   
 OPGUSDT     | DEEP_PYRAMID | 1288 (DILU)    | ROTATE     | 0.12885/0.12882     | 7.76b    | +0.0b|1.00 | 0.950  | $+13.1    |   0 |    1 | $+0.0061   
 SPELLUSDT   | DEEP_PYRAMID |  980 (FORT)    | NONE       | 0.00010/0.00010     | 10.20b   | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 PRLUSDT     | DEEP_PYRAMID | 1180 (FORT)    | MONITOR    | 0.11795/0.11794     | 8.48b    | -0.0b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 CFGUSDT     | DEEP_PYRAMID | 1456 (DILU)    | ROTATE     | 0.14555/0.14558     | 6.87b    | +2.1b|0.99 | 0.950  | $-101.5   |   0 |    0 | $+0.0000   
 OPENUSDT    | DEEP_PYRAMID | 1300 (DILU)    | ROTATE     | 0.12995/0.12999     | 7.70b    | +0.0b|0.99 | 0.800  | $-486.3   |   0 |    0 | $+0.0000   
 MITOUSDT    | DEEP_PYRAMID | 1568 (DILU)    | ROTATE     | 0.01568/0.01568     | 6.38b    | -0.7b|0.50 | 0.700  | $-124.3   |   0 |    0 | $+0.0000   
 ARKMUSDT    | DEEP_PYRAMID | 1318 (DILU)    | ROTATE     | 0.13175/0.13173     | 7.59b    | -0.0b|0.99 | 0.550  | $-210.9   |   0 |    0 | $+0.0000   
 ATUSDT      | DEEP_PYRAMID | 1598 (DILU)    | ROTATE     | 0.15985/0.15987     | 6.26b    | -0.0b|1.00 | 0.750  | $+5988.1  |   0 |    0 | $+0.0000   
 ONUSDT      | DEEP_PYRAMID | 1072 (FORT)    | RETREAT    | 0.10720/0.10723     | 18.66b   | +0.4b|1.07 | 0.950  | $-357.0   |   0 |    0 | $+0.0000   
 GRAMUSDT    | DEEP_PYRAMID | 1554 (DILU)    | ROTATE     | 1.554/1.555         | 6.43b    | -0.0b|1.00 | 0.850  | $+3450.1  |   0 |    0 | $+0.0000   
 TOSHIUSDT   | DEEP_PYRAMID | 1234 (FORT)    | RETREAT    | 0.00012/0.00012     | 8.10b    | +0.0b|0.85 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 RIVERUSDT   | DEEP_PYRAMID | 1216 (FORT)    | RETREAT    | 1.216/1.216         | 8.22b    | +0.0b|0.99 | 0.650  | $-269.2   |   0 |    0 | $+0.0000   
 AZTECUSDT   | DEEP_PYRAMID | 1754 (DILU)    | ROTATE     | 0.01754/0.01755     | 5.70b    | +0.0b|0.73 | 0.800  | $+0.0     |   0 |    0 | $+0.0000   
 DEXEUSDT    | DEEP_PYRAMID | 1886 (DILU)    | ROTATE     | 1.885/1.885         | 5.30b    | +0.0b|1.00 | 0.700  | $+43.6    |   0 |    0 | $+0.0000   
 RENDERUSDT  | DEEP_PYRAMID | 1928 (DILU)    | ROTATE     | 1.927/1.927         | 5.19b    | +0.0b|0.99 | 0.850  | $+3238.7  |   0 |    0 | $+0.0000   
 APEUSDT     | DEEP_PYRAMID | 1488 (DILU)    | ROTATE     | 0.14885/0.14881     | 6.72b    | +0.0b|1.07 | 0.650  | $-217.8   |   0 |    0 | $+0.0000   
 ORCAUSDT    | DEEP_PYRAMID | 1676 (DILU)    | ROTATE     | 1.676/1.676         | 5.96b    | -0.6b|1.05 | 0.750  | $-76.1    |   0 |    0 | $+0.0000   
 DIAUSDT     | DEEP_PYRAMID | 1664 (DILU)    | ROTATE     | 0.16635/0.16636     | 6.01b    | +0.0b|0.99 | 0.800  | $+13.6    |   0 |    0 | $+0.0000   
 WOOUSDT     | DEEP_PYRAMID | 1372 (DILU)    | ROTATE     | 0.01372/0.01372     | 7.29b    | -0.6b|0.28 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 SHADOW GRADUATION GATE EVALUATOR (Stage 1 Target: 40 Events | Wilson LB >= 0.60 | Net K2 >= +8 bps)
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | STATUS           | CENSUS       | WILSON 95% LB  | SNAP LAW   | FLOW AUC   | GATE VERDICT   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ESPORTSUSDT | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CHZUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPGUSDT     | SHADOW_QUARANTINE |  1/40 (0.0h) | 0.207          | FAIL/PEND  | 8.00       | MONITOR        
 SPELLUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 PRLUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CFGUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPENUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 MITOUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ARKMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ATUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ONUSDT      | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 GRAMUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 TOSHIUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RIVERUSDT   | A_OPEN           |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 AZTECUSDT   | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DEXEUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RENDERUSDT  | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 APEUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ORCAUSDT    | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DIAUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 WOOUSDT     | SHADOW_QUARANTINE |  0/40 (0.0h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 RECENT EXECUTION & AUDIT FEED
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 [18:16:19] [OPGUSDT   ] ENTRY_FILL             | SELL 40.0 @ 0.1291 ($5.16) | slot2
 [18:16:21] [OPGUSDT   ] PASSIVE_HARVEST        | +15.49 bps | Net: $+0.0061 | Total: $+0.0061
================================================================================================================================================================


================================================================================================================================================================
 SOVEREIGN MARKET OS: NESTED HIVEMIND & SENTINEL V18 [0.05h /   3.0m] | WAL: sovereign_fleet_v17.db
 Pool Capital: $25.00 | Active Margin: $0.00 (0.00x) | Reserve: $10.00 | Net PnL: $+0.0061 | Win%: 100.0%
 Peak PnL: $+0.0061 | Current DD: $0.0000 | Max DD: $0.0000 | Breaker: ARMED | BTC: NORMAL ($84796.2)
 DISCRETE DISPATCHER | Slots: 0/3 Filled ($0.00) | Free: $15.00 | Atomic Breaker: ARMED (Last: 0.0000ms) | Positions: None (All idle quoting) | Top Spinu: MMTUSDT (S=0.00), ESPORTSUSDT (S=0.00), CHZUSDT (S=0.00)
 AUTONOMOUS HIVEMIND | Quarantined (5): APRUSDT, ONUSDT, HANAUSDT, RIVERUSDT, ATUSDT | Screener Top: RIVERUSDT, GRAMUSDT, PLUMEUSDT | Lead-Lag Snipes: 0 | Protected Quotes: 0
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | MODE         | P/DELTA (ZONE) | SENTINEL   | MID / MICRO         | SPREAD   | KAL/VR     | ETA    | I_ENEMY   | CYC | FILL | NET PNL    
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | DEEP_PYRAMID | 1878 (DILU)    | ROTATE     | 0.18775/0.18776     | 5.33b    | -0.0b|1.00 | 0.450  | $+0.0     |   0 |    0 | $+0.0000   
 ESPORTSUSDT | DEEP_PYRAMID | 1098 (FORT)    | NONE       | 0.01098/0.01099     | 9.10b    | -0.0b|0.99 | 0.600  | $+0.0     |   0 |    0 | $+0.0000   
 CHZUSDT     | DEEP_PYRAMID | 1625 (DILU)    | ROTATE     | 0.01625/0.01625     | 6.16b    | -0.0b|1.00 | 0.700  | $+0.0     |   0 |    0 | $+0.0000   
 OPGUSDT     | DEEP_PYRAMID | 1288 (DILU)    | ROTATE     | 0.12885/0.12882     | 7.76b    | +0.0b|1.00 | 0.950  | $-18.9    |   0 |    1 | $+0.0061   
 SPELLUSDT   | DEEP_PYRAMID |  980 (FORT)    | RETREAT    | 0.00010/0.00010     | 10.20b   | -0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 PRLUSDT     | DEEP_PYRAMID | 1180 (FORT)    | MONITOR    | 0.11795/0.11795     | 8.48b    | -0.0b|0.99 | 0.550  | $+0.5     |   0 |    0 | $+0.0000   
 CFGUSDT     | DEEP_PYRAMID | 1456 (DILU)    | ROTATE     | 0.14555/0.14557     | 6.87b    | +0.0b|0.99 | 0.950  | $-101.5   |   0 |    0 | $+0.0000   
 OPENUSDT    | DEEP_PYRAMID | 1300 (DILU)    | ROTATE     | 0.12995/0.12999     | 7.70b    | -0.0b|1.00 | 0.800  | $-486.3   |   0 |    0 | $+0.0000   
 MITOUSDT    | DEEP_PYRAMID | 1568 (DILU)    | ROTATE     | 0.01568/0.01567     | 6.38b    | +0.2b|0.50 | 0.700  | $+0.0     |   0 |    0 | $+0.0000   
 ARKMUSDT    | DEEP_PYRAMID | 1318 (DILU)    | ROTATE     | 0.13175/0.13177     | 7.59b    | -0.0b|0.99 | 0.550  | $-210.9   |   0 |    0 | $+0.0000   
 ATUSDT      | DEEP_PYRAMID | 1599 (DILU)    | ROTATE     | 0.15995/0.15994     | 6.25b    | -0.0b|0.99 | 0.700  | $+8419.2  |   0 |    0 | $+0.0000   
 ONUSDT      | DEEP_PYRAMID | 1072 (FORT)    | RETREAT    | 0.10725/0.10730     | 9.32b    | -7.4b|1.00 | 0.950  | $-336.3   |   0 |    0 | $+0.0000   
 GRAMUSDT    | DEEP_PYRAMID | 1554 (DILU)    | ROTATE     | 1.554/1.554         | 6.43b    | -0.0b|1.00 | 0.850  | $+2909.1  |   0 |    0 | $+0.0000   
 TOSHIUSDT   | DEEP_PYRAMID | 1234 (FORT)    | RETREAT    | 0.00012/0.00012     | 8.10b    | -0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 RIVERUSDT   | DEEP_PYRAMID | 1216 (FORT)    | RETREAT    | 1.216/1.217         | 8.22b    | -0.0b|1.00 | 0.650  | $+896.3   |   0 |    0 | $+0.0000   
 AZTECUSDT   | DEEP_PYRAMID | 1754 (DILU)    | ROTATE     | 0.01754/0.01755     | 5.70b    | +0.0b|0.73 | 0.800  | $+0.0     |   0 |    0 | $+0.0000   
 DEXEUSDT    | DEEP_PYRAMID | 1886 (DILU)    | ROTATE     | 1.885/1.885         | 5.30b    | +0.0b|1.00 | 0.700  | $+0.0     |   0 |    0 | $+0.0000   
 RENDERUSDT  | DEEP_PYRAMID | 1928 (DILU)    | ROTATE     | 1.927/1.928         | 5.19b    | -0.0b|1.00 | 0.850  | $+72.9    |   0 |    0 | $+0.0000   
 APEUSDT     | DEEP_PYRAMID | 1488 (DILU)    | ROTATE     | 0.14885/0.14881     | 6.72b    | +0.0b|0.99 | 0.650  | $-217.8   |   0 |    0 | $+0.0000   
 ORCAUSDT    | DEEP_PYRAMID | 1678 (DILU)    | ROTATE     | 1.677/1.677         | 5.96b    | +0.5b|1.07 | 0.750  | $+925.2   |   0 |    0 | $+0.0000   
 DIAUSDT     | DEEP_PYRAMID | 1664 (DILU)    | ROTATE     | 0.16635/0.16636     | 6.01b    | -0.0b|0.99 | 0.800  | $+0.0     |   0 |    0 | $+0.0000   
 WOOUSDT     | DEEP_PYRAMID | 1372 (DILU)    | ROTATE     | 0.01372/0.01372     | 7.29b    | -1.2b|0.27 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 SHADOW GRADUATION GATE EVALUATOR (Stage 1 Target: 40 Events | Wilson LB >= 0.60 | Net K2 >= +8 bps)
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | STATUS           | CENSUS       | WILSON 95% LB  | SNAP LAW   | FLOW AUC   | GATE VERDICT   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ESPORTSUSDT | A_OPEN           |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CHZUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPGUSDT     | SHADOW_QUARANTINE |  1/40 (0.1h) | 0.207          | FAIL/PEND  | 8.00       | MONITOR        
 SPELLUSDT   | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 PRLUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CFGUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPENUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 MITOUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ARKMUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ATUSDT      | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ONUSDT      | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 GRAMUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 TOSHIUSDT   | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RIVERUSDT   | A_OPEN           |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 AZTECUSDT   | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DEXEUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RENDERUSDT  | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 APEUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ORCAUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DIAUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 WOOUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 RECENT EXECUTION & AUDIT FEED
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 [18:16:19] [OPGUSDT   ] ENTRY_FILL             | SELL 40.0 @ 0.1291 ($5.16) | slot2
 [18:16:21] [OPGUSDT   ] PASSIVE_HARVEST        | +15.49 bps | Net: $+0.0061 | Total: $+0.0061
================================================================================================================================================================


================================================================================================================================================================
 SOVEREIGN MARKET OS: NESTED HIVEMIND & SENTINEL V18 [0.05h /   3.3m] | WAL: sovereign_fleet_v17.db
 Pool Capital: $25.00 | Active Margin: $0.00 (0.00x) | Reserve: $10.00 | Net PnL: $+0.0061 | Win%: 100.0%
 Peak PnL: $+0.0061 | Current DD: $0.0000 | Max DD: $0.0000 | Breaker: ARMED | BTC: NORMAL ($84814.7)
 DISCRETE DISPATCHER | Slots: 0/3 Filled ($0.00) | Free: $15.00 | Atomic Breaker: ARMED (Last: 0.0000ms) | Positions: None (All idle quoting) | Top Spinu: MMTUSDT (S=0.00), ESPORTSUSDT (S=0.00), CHZUSDT (S=0.00)
 AUTONOMOUS HIVEMIND | Quarantined (5): APRUSDT, ONUSDT, HANAUSDT, RIVERUSDT, ATUSDT | Screener Top: RIVERUSDT, GRAMUSDT, PLUMEUSDT | Lead-Lag Snipes: 0 | Protected Quotes: 0
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | MODE         | P/DELTA (ZONE) | SENTINEL   | MID / MICRO         | SPREAD   | KAL/VR     | ETA    | I_ENEMY   | CYC | FILL | NET PNL    
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | DEEP_PYRAMID | 1878 (DILU)    | ROTATE     | 0.18780/0.18772     | 10.65b   | +5.4b|0.31 | 0.450  | $-224.8   |   0 |    0 | $+0.0000   
 ESPORTSUSDT | DEEP_PYRAMID | 1098 (FORT)    | NONE       | 0.01098/0.01099     | 9.10b    | +0.0b|0.99 | 0.600  | $+0.0     |   0 |    0 | $+0.0000   
 CHZUSDT     | DEEP_PYRAMID | 1625 (DILU)    | ROTATE     | 0.01625/0.01625     | 6.15b    | +10.8b|0.62 | 0.700  | $+311.1   |   0 |    0 | $+0.0000   
 OPGUSDT     | DEEP_PYRAMID | 1288 (DILU)    | ROTATE     | 0.12885/0.12885     | 7.76b    | -0.0b|1.00 | 0.950  | $-18.9    |   0 |    1 | $+0.0061   
 SPELLUSDT   | DEEP_PYRAMID |  980 (FORT)    | RETREAT    | 0.00010/0.00010     | 10.20b   | +0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 PRLUSDT     | DEEP_PYRAMID | 1180 (FORT)    | MONITOR    | 0.11795/0.11795     | 8.48b    | +0.0b|0.99 | 0.550  | $+0.5     |   0 |    0 | $+0.0000   
 CFGUSDT     | DEEP_PYRAMID | 1456 (DILU)    | ROTATE     | 0.14555/0.14558     | 6.87b    | -0.0b|0.81 | 0.950  | $-101.5   |   0 |    0 | $+0.0000   
 OPENUSDT    | DEEP_PYRAMID | 1300 (DILU)    | ROTATE     | 0.12995/0.12999     | 7.70b    | -0.0b|1.00 | 0.800  | $-486.3   |   0 |    0 | $+0.0000   
 MITOUSDT    | DEEP_PYRAMID | 1568 (DILU)    | ROTATE     | 0.01568/0.01567     | 6.38b    | +0.0b|0.50 | 0.700  | $+0.0     |   0 |    0 | $+0.0000   
 ARKMUSDT    | DEEP_PYRAMID | 1318 (DILU)    | ROTATE     | 0.13185/0.13182     | 7.58b    | +10.8b|0.92 | 0.550  | $+0.0     |   0 |    0 | $+0.0000   
 ATUSDT      | DEEP_PYRAMID | 1598 (DILU)    | ROTATE     | 0.15985/0.15986     | 6.26b    | +0.0b|0.99 | 0.700  | $+10178.7 |   0 |    0 | $+0.0000   
 ONUSDT      | DEEP_PYRAMID | 1073 (FORT)    | RETREAT    | 0.10730/0.10726     | 18.64b   | -0.5b|0.54 | 0.700  | $-71.7    |   0 |    0 | $+0.0000   
 GRAMUSDT    | DEEP_PYRAMID | 1554 (DILU)    | ROTATE     | 1.554/1.555         | 6.43b    | +0.0b|1.00 | 0.700  | $+21.1    |   0 |    0 | $+0.0000   
 TOSHIUSDT   | DEEP_PYRAMID | 1234 (FORT)    | RETREAT    | 0.00012/0.00012     | 8.10b    | -0.0b|1.00 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 RIVERUSDT   | DEEP_PYRAMID | 1216 (FORT)    | RETREAT    | 1.216/1.217         | 8.22b    | -0.0b|1.00 | 0.700  | $+17.9    |   0 |    0 | $+0.0000   
 AZTECUSDT   | DEEP_PYRAMID | 1754 (DILU)    | ROTATE     | 0.01754/0.01755     | 5.70b    | +0.0b|1.48 | 0.800  | $+0.0     |   0 |    0 | $+0.0000   
 DEXEUSDT    | DEEP_PYRAMID | 1886 (DILU)    | ROTATE     | 1.885/1.886         | 5.30b    | +0.0b|1.00 | 0.700  | $+140.3   |   0 |    0 | $+0.0000   
 RENDERUSDT  | DEEP_PYRAMID | 1928 (DILU)    | ROTATE     | 1.927/1.928         | 5.19b    | -0.0b|1.00 | 0.850  | $-2528.4  |   0 |    0 | $+0.0000   
 APEUSDT     | DEEP_PYRAMID | 1488 (DILU)    | ROTATE     | 0.14885/0.14883     | 6.72b    | +0.0b|1.00 | 0.650  | $-217.8   |   0 |    0 | $+0.0000   
 ORCAUSDT    | DEEP_PYRAMID | 1678 (DILU)    | ROTATE     | 1.677/1.677         | 5.96b    | -0.0b|0.99 | 0.750  | $+925.2   |   0 |    0 | $+0.0000   
 DIAUSDT     | DEEP_PYRAMID | 1664 (DILU)    | ROTATE     | 0.16645/0.16642     | 6.01b    | -0.0b|0.99 | 0.750  | $+407.0   |   0 |    0 | $+0.0000   
 WOOUSDT     | DEEP_PYRAMID | 1372 (DILU)    | ROTATE     | 0.01372/0.01372     | 7.29b    | +0.0b|0.26 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 SHADOW GRADUATION GATE EVALUATOR (Stage 1 Target: 40 Events | Wilson LB >= 0.60 | Net K2 >= +8 bps)
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | STATUS           | CENSUS       | WILSON 95% LB  | SNAP LAW   | FLOW AUC   | GATE VERDICT   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ESPORTSUSDT | A_OPEN           |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CHZUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPGUSDT     | SHADOW_QUARANTINE |  1/40 (0.1h) | 0.207          | FAIL/PEND  | 8.00       | MONITOR        
 SPELLUSDT   | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 PRLUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CFGUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPENUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 MITOUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ARKMUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ATUSDT      | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ONUSDT      | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 GRAMUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 TOSHIUSDT   | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RIVERUSDT   | A_OPEN           |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 AZTECUSDT   | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DEXEUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RENDERUSDT  | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 APEUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ORCAUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DIAUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 WOOUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 RECENT EXECUTION & AUDIT FEED
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 [18:16:19] [OPGUSDT   ] ENTRY_FILL             | SELL 40.0 @ 0.1291 ($5.16) | slot2
 [18:16:21] [OPGUSDT   ] PASSIVE_HARVEST        | +15.49 bps | Net: $+0.0061 | Total: $+0.0061
================================================================================================================================================================


================================================================================================================================================================
 SOVEREIGN MARKET OS: NESTED HIVEMIND & SENTINEL V18 [0.06h /   3.6m] | WAL: sovereign_fleet_v17.db
 Pool Capital: $25.00 | Active Margin: $0.00 (0.00x) | Reserve: $10.00 | Net PnL: $+0.0061 | Win%: 100.0%
 Peak PnL: $+0.0061 | Current DD: $0.0000 | Max DD: $0.0000 | Breaker: ARMED | BTC: NORMAL ($84837.5)
 DISCRETE DISPATCHER | Slots: 0/3 Filled ($0.00) | Free: $15.00 | Atomic Breaker: ARMED (Last: 0.0000ms) | Positions: None (All idle quoting) | Top Spinu: MMTUSDT (S=0.00), ESPORTSUSDT (S=0.00), CHZUSDT (S=0.00)
 AUTONOMOUS HIVEMIND | Quarantined (5): APRUSDT, ONUSDT, HANAUSDT, RIVERUSDT, ATUSDT | Screener Top: RIVERUSDT, GRAMUSDT, PLUMEUSDT | Lead-Lag Snipes: 0 | Protected Quotes: 0
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | MODE         | P/DELTA (ZONE) | SENTINEL   | MID / MICRO         | SPREAD   | KAL/VR     | ETA    | I_ENEMY   | CYC | FILL | NET PNL    
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | DEEP_PYRAMID | 1880 (DILU)    | ROTATE     | 0.18795/0.18794     | 5.32b    | -2.2b|0.32 | 0.500  | $+0.0     |   0 |    0 | $+0.0000   
 ESPORTSUSDT | DEEP_PYRAMID | 1098 (FORT)    | MONITOR    | 0.01098/0.01098     | 9.10b    | -0.0b|1.00 | 0.600  | $+0.0     |   0 |    0 | $+0.0000   
 CHZUSDT     | DEEP_PYRAMID | 1625 (DILU)    | ROTATE     | 0.01625/0.01626     | 6.15b    | +0.0b|1.00 | 0.700  | $+311.1   |   0 |    0 | $+0.0000   
 OPGUSDT     | DEEP_PYRAMID | 1288 (DILU)    | ROTATE     | 0.12885/0.12885     | 7.76b    | -0.0b|1.00 | 0.950  | $-18.9    |   0 |    1 | $+0.0061   
 SPELLUSDT   | DEEP_PYRAMID |  980 (FORT)    | RETREAT    | 0.00010/0.00010     | 10.20b   | +0.0b|0.64 | 0.450  | $+238.3   |   0 |    0 | $+0.0000   
 PRLUSDT     | DEEP_PYRAMID | 1180 (FORT)    | RETREAT    | 0.11805/0.11804     | 8.47b    | +0.0b|0.99 | 0.550  | $+332.6   |   0 |    0 | $+0.0000   
 CFGUSDT     | DEEP_PYRAMID | 1457 (DILU)    | ROTATE     | 0.14575/0.14572     | 6.86b    | +0.0b|0.91 | 0.850  | $+7.9     |   0 |    0 | $+0.0000   
 OPENUSDT    | DEEP_PYRAMID | 1300 (DILU)    | ROTATE     | 0.13005/0.13005     | 7.69b    | +0.0b|0.99 | 0.800  | $+4.4     |   0 |    0 | $+0.0000   
 MITOUSDT    | DEEP_PYRAMID | 1568 (DILU)    | ROTATE     | 0.01568/0.01568     | 6.38b    | +0.3b|0.68 | 0.700  | $+16.5    |   0 |    0 | $+0.0000   
 ARKMUSDT    | DEEP_PYRAMID | 1320 (DILU)    | ROTATE     | 0.13195/0.13193     | 7.58b    | +3.1b|0.97 | 0.750  | $+45.1    |   0 |    0 | $+0.0000   
 ATUSDT      | DEEP_PYRAMID | 1598 (DILU)    | ROTATE     | 0.15985/0.15987     | 6.26b    | -0.0b|1.00 | 0.700  | $+12111.8 |   0 |    0 | $+0.0000   
 ONUSDT      | DEEP_PYRAMID | 1074 (FORT)    | RETREAT    | 0.10735/0.10732     | 9.32b    | -0.0b|0.76 | 0.700  | $+5.5     |   0 |    0 | $+0.0000   
 GRAMUSDT    | DEEP_PYRAMID | 1554 (DILU)    | ROTATE     | 1.554/1.555         | 6.43b    | -5.6b|1.50 | 0.750  | $-8895.5  |   0 |    0 | $+0.0000   
 TOSHIUSDT   | DEEP_PYRAMID | 1236 (FORT)    | RETREAT    | 0.00012/0.00012     | 8.09b    | +0.0b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 RIVERUSDT   | DEEP_PYRAMID | 1216 (FORT)    | RETREAT    | 1.216/1.217         | 8.22b    | +3.3b|1.07 | 0.700  | $-264.8   |   0 |    0 | $+0.0000   
 AZTECUSDT   | DEEP_PYRAMID | 1756 (DILU)    | ROTATE     | 0.01756/0.01756     | 5.70b    | -0.1b|0.99 | 0.800  | $-154.1   |   0 |    0 | $+0.0000   
 DEXEUSDT    | DEEP_PYRAMID | 1886 (DILU)    | ROTATE     | 1.885/1.886         | 5.30b    | +0.0b|1.00 | 0.650  | $+28.4    |   0 |    0 | $+0.0000   
 RENDERUSDT  | DEEP_PYRAMID | 1930 (DILU)    | ROTATE     | 1.929/1.929         | 5.18b    | +0.0b|0.99 | 0.900  | $-16.6    |   0 |    0 | $+0.0000   
 APEUSDT     | DEEP_PYRAMID | 1490 (DILU)    | ROTATE     | 0.14895/0.14894     | 6.71b    | +0.0b|0.99 | 0.850  | $+1271.6  |   0 |    0 | $+0.0000   
 ORCAUSDT    | DEEP_PYRAMID | 1680 (DILU)    | ROTATE     | 1.679/1.680         | 5.95b    | -0.2b|0.91 | 0.800  | $+0.0     |   0 |    0 | $+0.0000   
 DIAUSDT     | DEEP_PYRAMID | 1664 (DILU)    | ROTATE     | 0.16645/0.16646     | 6.01b    | +0.0b|0.99 | 0.750  | $-24.8    |   0 |    0 | $+0.0000   
 WOOUSDT     | DEEP_PYRAMID | 1372 (DILU)    | ROTATE     | 0.01372/0.01373     | 7.29b    | -0.0b|0.12 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 SHADOW GRADUATION GATE EVALUATOR (Stage 1 Target: 40 Events | Wilson LB >= 0.60 | Net K2 >= +8 bps)
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | STATUS           | CENSUS       | WILSON 95% LB  | SNAP LAW   | FLOW AUC   | GATE VERDICT   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ESPORTSUSDT | A_OPEN           |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CHZUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPGUSDT     | SHADOW_QUARANTINE |  1/40 (0.1h) | 0.207          | FAIL/PEND  | 8.00       | MONITOR        
 SPELLUSDT   | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 PRLUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CFGUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPENUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 MITOUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ARKMUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ATUSDT      | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ONUSDT      | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 GRAMUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 TOSHIUSDT   | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RIVERUSDT   | A_OPEN           |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 AZTECUSDT   | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DEXEUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RENDERUSDT  | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 APEUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ORCAUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DIAUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 WOOUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 RECENT EXECUTION & AUDIT FEED
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 [18:16:19] [OPGUSDT   ] ENTRY_FILL             | SELL 40.0 @ 0.1291 ($5.16) | slot2
 [18:16:21] [OPGUSDT   ] PASSIVE_HARVEST        | +15.49 bps | Net: $+0.0061 | Total: $+0.0061
================================================================================================================================================================


================================================================================================================================================================
 SOVEREIGN MARKET OS: NESTED HIVEMIND & SENTINEL V18 [0.06h /   3.8m] | WAL: sovereign_fleet_v17.db
 Pool Capital: $25.00 | Active Margin: $0.00 (0.00x) | Reserve: $10.00 | Net PnL: $+0.0061 | Win%: 100.0%
 Peak PnL: $+0.0061 | Current DD: $0.0000 | Max DD: $0.0000 | Breaker: ARMED | BTC: NORMAL ($84843.1)
 DISCRETE DISPATCHER | Slots: 0/3 Filled ($0.00) | Free: $15.00 | Atomic Breaker: ARMED (Last: 0.0000ms) | Positions: None (All idle quoting) | Top Spinu: MMTUSDT (S=0.00), ESPORTSUSDT (S=0.00), CHZUSDT (S=0.00)
 AUTONOMOUS HIVEMIND | Quarantined (5): APRUSDT, ONUSDT, HANAUSDT, RIVERUSDT, ATUSDT | Screener Top: RIVERUSDT, GRAMUSDT, PLUMEUSDT | Lead-Lag Snipes: 0 | Protected Quotes: 0
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | MODE         | P/DELTA (ZONE) | SENTINEL   | MID / MICRO         | SPREAD   | KAL/VR     | ETA    | I_ENEMY   | CYC | FILL | NET PNL    
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | DEEP_PYRAMID | 1881 (DILU)    | ROTATE     | 0.18815/0.18817     | 5.31b    | -0.0b|0.91 | 0.500  | $+284.9   |   0 |    0 | $+0.0000   
 ESPORTSUSDT | DEEP_PYRAMID | 1098 (FORT)    | MONITOR    | 0.01098/0.01098     | 9.10b    | -0.0b|1.00 | 0.600  | $+242.0   |   0 |    0 | $+0.0000   
 CHZUSDT     | DEEP_PYRAMID | 1627 (DILU)    | ROTATE     | 0.01627/0.01627     | 6.14b    | +0.8b|0.99 | 0.700  | $+25.9    |   0 |    0 | $+0.0000   
 OPGUSDT     | DEEP_PYRAMID | 1288 (DILU)    | ROTATE     | 0.12885/0.12886     | 7.76b    | -0.0b|1.00 | 0.950  | $+30.3    |   0 |    1 | $+0.0061   
 SPELLUSDT   | DEEP_PYRAMID |  980 (FORT)    | RETREAT    | 0.00010/0.00010     | 10.20b   | +0.0b|0.64 | 0.450  | $+0.0     |   0 |    0 | $+0.0000   
 PRLUSDT     | DEEP_PYRAMID | 1180 (FORT)    | RETREAT    | 0.11805/0.11804     | 8.47b    | -0.0b|0.99 | 0.550  | $+332.6   |   0 |    0 | $+0.0000   
 CFGUSDT     | DEEP_PYRAMID | 1457 (DILU)    | ROTATE     | 0.14575/0.14579     | 6.86b    | +0.0b|1.00 | 0.850  | $-7.4     |   0 |    0 | $+0.0000   
 OPENUSDT    | DEEP_PYRAMID | 1300 (DILU)    | ROTATE     | 0.13005/0.13009     | 7.69b    | +0.0b|1.00 | 0.800  | $+4.4     |   0 |    0 | $+0.0000   
 MITOUSDT    | DEEP_PYRAMID | 1568 (DILU)    | ROTATE     | 0.01568/0.01568     | 6.38b    | -0.0b|0.99 | 0.700  | $+0.0     |   0 |    0 | $+0.0000   
 ARKMUSDT    | DEEP_PYRAMID | 1320 (DILU)    | ROTATE     | 0.13195/0.13200     | 7.58b    | +0.0b|1.06 | 0.750  | $+456.7   |   0 |    0 | $+0.0000   
 ATUSDT      | DEEP_PYRAMID | 1602 (DILU)    | ROTATE     | 0.16015/0.16016     | 6.24b    | -0.0b|1.04 | 0.700  | $+15346.2 |   0 |    0 | $+0.0000   
 ONUSDT      | DEEP_PYRAMID | 1075 (FORT)    | RETREAT    | 0.10750/0.10748     | 18.60b   | -0.0b|1.01 | 0.700  | $+1163.4  |   0 |    0 | $+0.0000   
 GRAMUSDT    | DEEP_PYRAMID | 1554 (DILU)    | ROTATE     | 1.554/1.555         | 6.43b    | +0.0b|1.00 | 0.700  | $-9168.9  |   0 |    0 | $+0.0000   
 TOSHIUSDT   | DEEP_PYRAMID | 1236 (FORT)    | RETREAT    | 0.00012/0.00012     | 8.09b    | +0.0b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
 RIVERUSDT   | DEEP_PYRAMID | 1218 (FORT)    | RETREAT    | 1.218/1.217         | 8.21b    | +0.0b|1.00 | 0.700  | $+0.0     |   0 |    0 | $+0.0000   
 AZTECUSDT   | DEEP_PYRAMID | 1756 (DILU)    | ROTATE     | 0.01756/0.01757     | 5.69b    | -8.8b|0.56 | 0.800  | $-115.8   |   0 |    0 | $+0.0000   
 DEXEUSDT    | DEEP_PYRAMID | 1886 (DILU)    | ROTATE     | 1.885/1.886         | 5.30b    | -0.0b|1.00 | 0.650  | $+0.2     |   0 |    0 | $+0.0000   
 RENDERUSDT  | DEEP_PYRAMID | 1930 (DILU)    | ROTATE     | 1.930/1.931         | 5.18b    | +0.0b|1.00 | 0.900  | $-482.5   |   0 |    0 | $+0.0000   
 APEUSDT     | DEEP_PYRAMID | 1490 (DILU)    | ROTATE     | 0.14905/0.14905     | 6.71b    | -0.0b|1.00 | 0.850  | $-42.5    |   0 |    0 | $+0.0000   
 ORCAUSDT    | DEEP_PYRAMID | 1680 (DILU)    | ROTATE     | 1.680/1.680         | 5.95b    | +0.0b|0.99 | 0.800  | $+0.0     |   0 |    0 | $+0.0000   
 DIAUSDT     | DEEP_PYRAMID | 1664 (DILU)    | ROTATE     | 0.16645/0.16648     | 6.01b    | +0.0b|0.99 | 0.850  | $+35.8    |   0 |    0 | $+0.0000   
 WOOUSDT     | DEEP_PYRAMID | 1374 (DILU)    | ROTATE     | 0.01374/0.01373     | 7.28b    | -0.0b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 SHADOW GRADUATION GATE EVALUATOR (Stage 1 Target: 40 Events | Wilson LB >= 0.60 | Net K2 >= +8 bps)
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | STATUS           | CENSUS       | WILSON 95% LB  | SNAP LAW   | FLOW AUC   | GATE VERDICT   
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ESPORTSUSDT | A_OPEN           |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CHZUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPGUSDT     | SHADOW_QUARANTINE |  1/40 (0.1h) | 0.207          | FAIL/PEND  | 8.00       | MONITOR        
 SPELLUSDT   | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 PRLUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 CFGUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 OPENUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 MITOUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ARKMUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ATUSDT      | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ONUSDT      | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 GRAMUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 TOSHIUSDT   | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RIVERUSDT   | A_OPEN           |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 AZTECUSDT   | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DEXEUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 RENDERUSDT  | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 APEUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 ORCAUSDT    | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 DIAUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
 WOOUSDT     | SHADOW_QUARANTINE |  0/40 (0.1h) | N/A            | FAIL/PEND  | 8.00       | PENDING        
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 RECENT EXECUTION & AUDIT FEED
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 [18:16:19] [OPGUSDT   ] ENTRY_FILL             | SELL 40.0 @ 0.1291 ($5.16) | slot2
 [18:16:21] [OPGUSDT   ] PASSIVE_HARVEST        | +15.49 bps | Net: $+0.0061 | Total: $+0.0061
================================================================================================================================================================


================================================================================================================================================================
 SOVEREIGN MARKET OS: NESTED HIVEMIND & SENTINEL V18 [0.07h /   4.1m] | WAL: sovereign_fleet_v17.db
 Pool Capital: $25.00 | Active Margin: $0.00 (0.00x) | Reserve: $10.00 | Net PnL: $+0.0061 | Win%: 100.0%
 Peak PnL: $+0.0061 | Current DD: $0.0000 | Max DD: $0.0000 | Breaker: ARMED | BTC: NORMAL ($84833.6)
 DISCRETE DISPATCHER | Slots: 0/3 Filled ($0.00) | Free: $15.00 | Atomic Breaker: ARMED (Last: 0.0000ms) | Positions: None (All idle quoting) | Top Spinu: MMTUSDT (S=0.00), ESPORTSUSDT (S=0.00), CHZUSDT (S=0.00)
 AUTONOMOUS HIVEMIND | Quarantined (5): APRUSDT, ONUSDT, HANAUSDT, RIVERUSDT, ATUSDT | Screener Top: RIVERUSDT, GRAMUSDT, PLUMEUSDT | Lead-Lag Snipes: 0 | Protected Quotes: 0
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 ASSET       | MODE         | P/DELTA (ZONE) | SENTINEL   | MID / MICRO         | SPREAD   | KAL/VR     | ETA    | I_ENEMY   | CYC | FILL | NET PNL    
----------------------------------------------------------------------------------------------------------------------------------------------------------------
 MMTUSDT     | DEEP_PYRAMID | 1880 (DILU)    | ROTATE     | 0.18805/0.18810     | 5.32b    | +1.2b|1.04 | 0.500  | $-196.1   |   0 |    0 | $+0.0000   
 ESPORTSUSDT | DEEP_PYRAMID | 1098 (FORT)    | NONE       | 0.01098/0.01098     | 9.10b    | +0.0b|1.00 | 0.600  | $+242.0   |   0 |    0 | $+0.0000   
 CHZUSDT     | DEEP_PYRAMID | 1626 (DILU)    | ROTATE     | 0.01627/0.01626     | 6.15b    | +0.0b|0.96 | 0.700  | $-5.6     |   0 |    0 | $+0.0000   
 OPGUSDT     | DEEP_PYRAMID | 1288 (DILU)    | ROTATE     | 0.12885/0.12886     | 7.76b    | +0.0b|1.00 | 0.950  | $-21.9    |   0 |    1 | $+0.0061   
 SPELLUSDT   | DEEP_PYRAMID |  980 (FORT)    | RETREAT    | 0.00010/0.00010     | 10.20b   | +0.0b|1.00 | 0.450  | $+0.0     |   0 |    0 | $+0.0000   
 PRLUSDT     | DEEP_PYRAMID | 1180 (FORT)    | RETREAT    | 0.11805/0.11804     | 8.47b    | -0.0b|0.99 | 0.550  | $+0.0     |   0 |    0 | $+0.0000   
 CFGUSDT     | DEEP_PYRAMID | 1457 (DILU)    | ROTATE     | 0.14575/0.14573     | 6.86b    | -0.0b|1.00 | 0.850  | $-7.4     |   0 |    0 | $+0.0000   
 OPENUSDT    | DEEP_PYRAMID | 1300 (DILU)    | ROTATE     | 0.13005/0.13009     | 7.69b    | +0.0b|1.00 | 0.800  | $+0.0     |   0 |    0 | $+0.0000   
 MITOUSDT    | DEEP_PYRAMID | 1568 (DILU)    | ROTATE     | 0.01568/0.01568     | 6.38b    | -1.2b|0.80 | 0.700  | $+208.3   |   0 |    0 | $+0.0000   
 ARKMUSDT    | DEEP_PYRAMID | 1320 (DILU)    | ROTATE     | 0.13195/0.13197     | 7.58b    | +0.0b|1.07 | 0.750  | $-87.2    |   0 |    0 | $+0.0000   
 ATUSDT      | DEEP_PYRAMID | 1602 (DILU)    | ROTATE     | 0.16015/0.16013     | 6.24b    | -0.0b|0.99 | 0.800  | $+16331.4 |   0 |    0 | $+0.0000   
 ONUSDT      | DEEP_PYRAMID | 1074 (FORT)    | RETREAT    | 0.10745/0.10747     | 9.31b    | -0.6b|1.05 | 0.700  | $+52.7    |   0 |    0 | $+0.0000   
 GRAMUSDT    | DEEP_PYRAMID | 1554 (DILU)    | ROTATE     | 1.554/1.555         | 6.43b    | -0.0b|1.07 | 0.700  | $+0.0     |   0 |    0 | $+0.0000   
 TOSHIUSDT   | DEEP_PYRAMID | 1236 (FORT)    | RETREAT    | 0.00012/0.00012     | 8.09b    | -0.0b|0.99 | 0.000  | $+0.0     |   0 |    0 | $+0.0000   

`
