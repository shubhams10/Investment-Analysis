# Quantitative Analysis of Risk and Return for a Three-Stock Portfolio

A clean, reproducible Python notebook that compares Morgan Stanley, JP Morgan, and Bank of America. It turns raw prices into returns, builds one clear performance chart, and adds risk and performance metrics you can reuse on any tickers.

## What this project does

Pulls daily historical prices for MS, JPM, and BAC from Stooq.

Aligns trading dates, handles missing values, and computes daily simple returns and log returns.

Builds cumulative return so you can see the performance path over time in a single chart.

Includes an optional section with common risk and performance metrics: Alpha, Beta, Sharpe, Sortino, Treynor, Standard Deviation, Maximum Drawdown, Value at Risk (VaR), and Conditional Value at Risk (CVaR).

## Why it is useful

Price alone can fool you. Returns, drawdowns, and risk-adjusted ratios help you judge quality, not just outcome. This notebook gives you a tidy flow you can apply to other assets or portfolios without rewriting everything.

## Data sources

Historical price data used in this project: Stooq daily OHLCV, fetched programmatically.

Optional alternative if you want to switch later: Yahoo Finance via yfinance for daily data. If you use Yahoo, consider polite settings to avoid rate limits.

## Project structure

1=> Investment Analysis.ipynb        # Main notebook
2=> README.md                        # you are here

## Setup

Python 3.10 or newer.

Install packages:

pip install pandas numpy matplotlib plotly


If you want to use Stooq via pandas-datareader:

pip install pandas-datareader


If you later decide to try Yahoo Finance:

pip install yfinance

## How to run

Open the notebook and run all cells in order.

jupyter notebook "Investment Analysis.ipynb"


By default it uses dates from 2024-01-01 to today. You can change start_date and end_date at the top of the notebook.

## Core methodology

1) Load daily prices for MS, JPM, BAC from Stooq.

2) Align dates to keep only days where all names traded.

3) Compute returns

4) Daily simple returns: (P_t / P_{t-1}) - 1

5) Log returns: ln(P_t / P_{t-1})

6) Build cumulative return to visualise the growth path over the period.

7) Plot a single chart that shows the performance paths together for a clean comparison.

## Risk and performance metrics

 If you enable the metrics cells, the notebook can compute:

   Alpha and Beta vs a chosen benchmark, to see excess return and market sensitivity.
  
  Sharpe to judge return per unit of total volatility.
  
  Sortino to focus on downside volatility only.
  
  Treynor to judge return per unit of market risk.
  
  Standard Deviation for overall variability.
  
  Maximum Drawdown for the worst peak-to-trough fall.
  
  VaR and CVaR to estimate tail risk and stress days.
  
  You can switch the benchmark, window lengths, or confidence levels inside the metrics cell.

## Customising the analysis

Change tickers by editing the tickers list. For Stooq you can also use symbols like ms.us, jpm.us, bac.us if you are pulling direct CSVs.

Adjust the date range to fit your case study window.

Add a weight vector if you want to aggregate into a single portfolio series.

## Reproducibility notes

Cache raw price data to data/ if you want fully offline runs.

Record package versions in a requirements.txt if you share the project.

Set a random seed if you simulate anything.

## Troubleshooting

Empty dataframe: check the symbol format for Stooq and your date window.

Missing days: the notebook aligns dates across all tickers. If one asset has a holiday, that day is dropped to keep a fair comparison.

If you switch to Yahoo and hit rate limits: set threads=False, fetch one ticker at a time, or add simple retries.
