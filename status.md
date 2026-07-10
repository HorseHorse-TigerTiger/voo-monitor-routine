# VOO Entry Indicator Status Log

Machine-readable-ish log of the 6-indicator check, most recent entry last.
Used by the monitoring routine to detect status changes between runs.

## 2026-07-10 (ET, based on data through July 9 close / July 10 premarket)

| # | Indicator | Status |
|---|---|---|
| 1 | T2108 Market Breadth | Watching (est. healthy, not oversold) |
| 2 | VIX Fear Index | Watching (~15.6-15.75, calm) |
| 3 | Selling Climax Volume | Watching (no spike, below-avg volume) |
| 4 | SPX Drawdown | Watching (at new highs, +8.1% above 1/27 high) |
| 5 | MA200 | Watching (SPX above MA200 by ~8.6%) |
| 6 | RSI Bullish Divergence | Watching (no divergence setup; price at highs) |

Total triggered: 0/6

Note: SPX has exceeded the 2026-01-27 reference high of 6978 (now ~7543-7596),
so the original correction/drawdown thesis no longer applies. Future runs
should consider re-baselining the reference high if this persists.
