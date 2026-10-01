# Sovereign Market OS: Fill-Tape Database Specification & Ledger Audit

**Database Path (Absolute Windows)**: `D:\sovereign_market_os\paper_trading\sovereign_fleet_v17.db`  
**Database Path (Repository Relative)**: `paper_trading/sovereign_fleet_v17.db`  
**Storage Engine**: SQLite 3 (WAL Mode — Write-Ahead Logging, `PRAGMA synchronous = NORMAL`)  
**Active Writing Process**: `python -u sovereign_fleet/run_fleet.py --capital 25` (Task PID `task-42240`)  

---

## 1. Executive Summary & Live State

The Sovereign Market OS V18 nested execution engine writes all state transitions, order placements, trade fills, position exits, and adversarial risk events to an ACID SQLite database.

### Current Record Census (Live As of Run):
| Table Name | Record Count | Description |
| :--- | :--- | :--- |
| `orders` | **21,825+** | All quote placements, cancellations, and modifications across all active corridors |
| `fills` | **80** | Executed trade fills (Maker passive fills and Taker lead-lag snipes) |
| `trade_cycles` | **63** | Completed round-trip trade cycles with entry, exit, PnL (bps/USD), MAE/MFE |
| `shield_events` | **29** | Microstructure defense triggers (skew shifts, toxic sweep freezes, circuit breaker events) |
| `markout_snapshots` | **0** | Periodic 1s/5s/30s post-trade markout counterfactual evaluations |
| `telemetry_snapshots` | **0** | Periodic fleet-wide capital, leverage, and margin snapshots |
| `graduation_events` | **0** | Autonomous promotion/demotion/quarantine state transitions |

---

## 2. Complete Database Schema

### A. Table `orders`
```sql
CREATE TABLE orders (
    order_id TEXT PRIMARY KEY,
    symbol TEXT NOT NULL,
    side TEXT NOT NULL,
    px REAL NOT NULL,
    qty REAL NOT NULL,
    notional REAL NOT NULL,
    order_type TEXT NOT NULL,
    slot TEXT NOT NULL,
    state TEXT NOT NULL,
    queue_ahead REAL NOT NULL,
    anchor_px REAL NOT NULL,
    created_ns INTEGER NOT NULL,
    updated_ns INTEGER NOT NULL,
    is_shadow INTEGER DEFAULT 0
);
```

### B. Table `fills`
```sql
CREATE TABLE fills (
    fill_id INTEGER PRIMARY KEY AUTOINCREMENT,
    cid TEXT NOT NULL,
    symbol TEXT NOT NULL,
    side TEXT NOT NULL,
    px REAL NOT NULL,
    qty REAL NOT NULL,
    notional REAL NOT NULL,
    fee_usd REAL NOT NULL,
    role TEXT NOT NULL,         -- 'MAKER' (1.80 bps fee) or 'TAKER' (4.50 bps fee)
    fill_ns INTEGER NOT NULL,
    is_shadow INTEGER DEFAULT 0
);
```

### C. Table `trade_cycles`
```sql
CREATE TABLE trade_cycles (
    cid TEXT PRIMARY KEY,
    symbol TEXT NOT NULL,
    side TEXT NOT NULL,
    entry_px REAL NOT NULL,
    exit_px REAL NOT NULL,
    qty REAL NOT NULL,
    anchor_px REAL NOT NULL,
    entry_fee_usd REAL NOT NULL,
    exit_fee_usd REAL NOT NULL,
    gross_pnl_usd REAL NOT NULL,
    net_pnl_usd REAL NOT NULL,
    pnl_bps REAL NOT NULL,
    mae_bps REAL NOT NULL,
    mfe_bps REAL NOT NULL,
    hold_time_sec REAL NOT NULL,
    resolution TEXT NOT NULL,   -- e.g. 'PASSIVE_MAKER_HARVEST', 'KINEMATIC_EJECT'
    is_taker INTEGER DEFAULT 0,
    entry_ns INTEGER NOT NULL,
    exit_ns INTEGER NOT NULL,
    is_shadow INTEGER DEFAULT 0
);
```

### D. Table `shield_events`
```sql
CREATE TABLE shield_events (
    event_id INTEGER PRIMARY KEY AUTOINCREMENT,
    symbol TEXT NOT NULL,
    event_type TEXT NOT NULL,   -- 'SKEW_DRIFT', 'TOXIC_SWEEP_FREEZE', 'CORRIDOR_QUARANTINE'
    details TEXT NOT NULL,
    timestamp_ns INTEGER NOT NULL
);
```

---

## 3. Sample Recent Fill Tape (Verbatim Records)

| Fill ID | Symbol | Side | Price | Qty | Notional ($) | Fee ($) | Role | Epoch Timestamp (ns) |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **80** | `AZTECUSDT` | SELL | 0.01755 | 288.0 | $5.0544 | $0.000910 | MAKER | 1790879000778457400 |
| **79** | `OPGUSDT` | SELL | 0.12910 | 40.0 | $5.1640 | $0.000930 | MAKER | 1790878579097777100 |
| **78** | `APRUSDT` | SELL | 0.13410 | 75.0 | $10.0575 | $0.001810 | MAKER | 1790877152186693100 |
| **77** | `APRUSDT` | SELL | 0.13400 | 38.0 | $5.0920 | $0.000917 | MAKER | 1790877152129514000 |
| **76** | `APRUSDT` | SELL | 0.13390 | 38.0 | $5.0882 | $0.000916 | MAKER | 1790877152108280600 |
| **75** | `APRUSDT` | BUY | 0.13140 | 76.0 | $9.9864 | $0.001798 | MAKER | 1790876954163583200 |
| **74** | `APRUSDT` | BUY | 0.13150 | 39.0 | $5.1285 | $0.000923 | MAKER | 1790876954140355300 |
| **73** | `APRUSDT` | BUY | 0.13160 | 39.0 | $5.1324 | $0.000924 | MAKER | 1790876954076715900 |
| **72** | `ATUSDT` | BUY | 0.16240 | 32.0 | $5.1968 | $0.000935 | MAKER | 1790876793794988400 |
| **71** | `ATUSDT` | SELL | 0.16220 | 32.0 | $5.1904 | $0.000934 | MAKER | 1790876714241503800 |

---

## 4. Sample Recent Trade Cycles (Round-Trip Settlements)

| Cycle ID | Symbol | Entry Px | Exit Px | Qty | Gross PnL | Net PnL | Return (bps) | Hold Duration | Resolution |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| `OPGUSDT_8490230_1` | `OPGUSDT` | 0.12910 | 0.12890 | 40.0 | +$0.0080 | **+$0.0061** | **+11.89 bps** | 2.36s | PASSIVE_MAKER_HARVEST |
| `AZTECUSDT_8490338_1` | `AZTECUSDT` | 0.01755 | 0.01758 | 288.0 | -$0.0086 | -$0.0105 | -20.70 bps | 47.00s | PASSIVE_MAKER_HARVEST |
| `APRUSDT_4840580_19` | `APRUSDT` | 0.13410 | 0.13470 | 75.0 | -$0.0450 | -$0.0486 | -48.35 bps | 0.45s | PASSIVE_MAKER_HARVEST |
| `APRUSDT_4840580_18` | `APRUSDT` | 0.13400 | 0.13470 | 38.0 | -$0.0266 | -$0.0284 | -55.85 bps | 0.50s | PASSIVE_MAKER_HARVEST |
| `APRUSDT_4840580_17` | `APRUSDT` | 0.13390 | 0.13470 | 38.0 | -$0.0304 | -$0.0322 | -63.36 bps | 0.53s | PASSIVE_MAKER_HARVEST |

---

## 5. Direct Forensic Query Scripts

To inspect the database in real time without locking the file (WAL mode allows concurrent non-blocking reads):

### Inspecting Last 10 Fills:
```bash
python -c "
import sqlite3
conn = sqlite3.connect('D:/sovereign_market_os/paper_trading/sovereign_fleet_v17.db')
cur = conn.cursor()
for r in cur.execute('SELECT fill_id, symbol, side, px, qty, notional, fee_usd, role FROM fills ORDER BY fill_id DESC LIMIT 10'):
    print(r)
"
```

### Inspecting Cycle Win Rate & Cumulative PnL:
```bash
python -c "
import sqlite3
conn = sqlite3.connect('D:/sovereign_market_os/paper_trading/sovereign_fleet_v17.db')
cur = conn.cursor()
pnl, count, wins, avg_bps = cur.execute('SELECT SUM(net_pnl_usd), COUNT(*), SUM(CASE WHEN net_pnl_usd > 0 THEN 1 ELSE 0 END), AVG(pnl_bps) FROM trade_cycles').fetchone()
print(f'Total Cycles: {count} | Wins: {wins} ({wins/count*100:.1f}%) | Net PnL: ${pnl:.4f} | Avg Return: {avg_bps:.2f} bps')
"
```
