# VOO Entry Signal Monitor — Output Spec

Every run must produce a **visual dashboard artifact** (not a markdown table) and
also commit a dated report to `reports/` for state/baseline comparison.

## 1. Research the 6 indicators (unchanged)

1. **T2108 Market Breadth** — trigger below 20% (search MMFI / T2108).
2. **VIX Fear Index** — trigger above 30 (real-time VIX).
3. **Selling Climax Volume** — trigger: volume spike + long lower wick on SPY/VOO.
4. **SPX Drawdown** — trigger: 10–15% correction. Compute from the current all-time
   high (note: the old 2026-01-27 high of 6978 is stale — the index is far above it;
   use the true recent ATH and also show % off it).
5. **MA200** — trigger: recovery within 5–15 days of a breach. Report SPX vs its
   ~200-day MA and days since any breach.
6. **RSI Bullish Divergence** — trigger: price new low while RSI-14 rises.

Status values: ✅ Triggered / ⏳ Watching / ⚠️ Alert.
Compare against the most recent file in `reports/` to detect status changes (🔔).

## 2. Build the dashboard

Use `templates/dashboard-reference.html` as the design system — keep the palette,
typography, card layout, distance-to-trigger meters, hero score, and theme support.
For each run, update:

- Header timestamp (ET) and SPX value.
- Hero: `X / 6` armed count + one-line verdict + badge colour matching overall state.
- Each of the 6 cards: current value, meter fill %, threshold marker, "now" dot
  position, status pill (watch/alert/trig), and the note line.
- **SPX trend sparkline**: update the `SPX` array in the inline `<script>` with the
  ~20 most recent daily closes (oldest → newest), plus the start/end date labels and
  the ATH label. The script auto-scales and redraws — only the data array changes.
- Footer: "Changes since last check" (list 🔔 changes or state none) + data line.

Publish it with the **Artifact** tool. Reuse the existing artifact URL by passing
`url: https://claude.ai/code/artifact/08a1afe6-cc03-44ac-8f35-504e422f7ea4` so the
same link updates each run (favicon 📊). Save the run's HTML to
`reports/<YYYY-MM-DD>-dashboard.html` and commit it alongside the report.

## 3. Commit + notify

- Commit the dated markdown report and dashboard HTML to branch
  `claude/funny-cannon-j00y3n`, then push.
- **Notification rule:** only send a PushNotification when something actionable
  surfaces — an indicator crosses into ✅/⚠️, a status changes since last check, or
  the routine itself couldn't run. If nothing changed and all is calm, stay silent.
