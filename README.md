# treasury_bonds_hedging

This project builds a complete pipeline for measuring and hedging interest rate risk in a Treasury bond portfolio. Using U.S. Treasury yield data and ETF prices (IEF, TLT), the workflow estimates portfolio sensitivities, constructs a key-rate DV01 hedge, and evaluates its performance through both historical backtesting and Monte Carlo simulations.

We construct a small toy portfolio of Treasury bonds, compute its DV01 and key-rate DV01s, and then design an ETF-based hedge to neutralize interest rate exposure. The hedge is sized using a least-squares regression on historical yield and ETF returns.
Performance is validated over real data (2018–2025) and hundreds of simulated yield paths generated with a Vasicek mean-reverting model.

1_fetch_data.ipynb: Pulls Treasury yields (2y, 5y, 10y, 30y) from FRED and ETF price data (IEF, TLT) from Yahoo Finance. Cleans, aligns, and saves the datasets.
2_build_curve.ipynb: Interpolates discrete yields into a smooth zero-coupon yield curve and computes discount factors for bond pricing.
3_analytics.ipynb: Prices each bond using discounted cash flows, computes duration, DV01, and key-rate DV01s (KRDV01s).
4_hedge_design.ipynb: Estimates ETF sensitivities to yield movements via regression and solves for hedge weights using least squares.
5_hedge_real_data.ipynb: Applies the hedge to historical data, rebalancing monthly. Calculates volatility, variance reduction, VaR, and drawdowns.
6_what_if.ipynb: Stress-tests hedge performance under simulated future rate paths using a Vasicek model and PCA-based yield curve dynamics.
7_analyze.ipynb: Aggregates results and produces summary statistics and plots comparing unhedged vs. hedged portfolios.
