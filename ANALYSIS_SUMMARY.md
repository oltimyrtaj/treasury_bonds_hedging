# Step 7 — Analysis Summary

## Historical Backtest (2018 → latest)
- **Ann. Vol (Unhedged → Hedged):** 13.3088 → 5.5428
- **Variance Reduction:** 82.6548%
- **Max Drawdown (Unhedged → Hedged):** -73.064 → -30.4559
- **VaR95 (Unhedged → Hedged):** -1.3505 → -0.5417
- **Sharpe-like (Unhedged → Hedged):** -0.2095 → -0.578

See CSVs:
- `data/backtest_summary_overall.csv`
- `data/backtest_summary_by_year.csv`

Key figures saved under `figs/`:
- `bt_cum_pnl.png`, `bt_rolling_vol.png`, `bt_pnl_hist.png`, `bt_hedge_ratios.png`, `bt_turnover_hist.png`

## Simulation (1y horizon, 500 paths)
**Parallel model (median path):**
- Ann. Vol (Unhedged → Hedged): 13.842 → 0.85
- Variance Reduction: 99.619%
- Max DD (Unhedged → Hedged): -14.766 → -0.746
- VaR95 (Unhedged → Hedged): -1.427 → -0.082

**Level+Slope model (median path):**
- Ann. Vol (Unhedged → Hedged): 14.282 → 1.062
- Variance Reduction: 99.441%
- Max DD (Unhedged → Hedged): -16.517 → -1.034
- VaR95 (Unhedged → Hedged): -1.461 → -0.106

Percentile tables saved under:
- `data/sim_summary_parallel_percentiles.csv`
- `data/sim_summary_level_slope_percentiles.csv`

## Caveats & Assumptions
- CMT treated as zeros; ETFs approximated via KRD splits; linear MTM for ETFs.
- Vasicek (Gaussian) dynamics; fat tails and basis risk understated.
- Monthly rebalances; transaction costs optional (see cost-aware variant).
