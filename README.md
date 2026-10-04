# ETF Performance & Economic Dashboard

A Streamlit app for ranking ETFs across multiple time horizons, analyzing individual ETFs, testing historical investments, backtesting portfolios, and monitoring key U.S. economic indicators from FRED.

## Features

- Best ETF of the day, week, 2 weeks, month, 3 months, 6 months, 1 year, 3 years, 5 years, and 10 years
- ETF analyzer with price chart, return metrics, volatility, and max drawdown
- Historical "What if I invested $X?" calculator
- Multi-ETF historical portfolio backtest
- Strategy rankings for Balanced, Momentum, Long-Term Growth, Consistency, and Aggressive Growth
- FRED economic dashboard with inflation, labor, interest rates, yield curve, GDP, industrial production, retail sales, sentiment, and housing
- Uses the included ETF workbook as the investment universe

## Run locally

```bash
pip install -r requirements.txt
streamlit run app.py
```

## FRED API key

Do not put your FRED API key directly in `app.py`.

Create `.streamlit/secrets.toml` locally:

```toml
FRED_API_KEY = "your-fred-api-key"
```

The real secrets file is excluded by `.gitignore`.

For Streamlit Community Cloud, add the same line in the app's **Settings → Secrets** section.

## Deploy

1. Upload the repository to GitHub.
2. Open https://share.streamlit.io/
3. Select the repository.
4. Set the main file to `app.py`.
5. Add `FRED_API_KEY` under Streamlit Secrets.
6. Deploy.

## Data notes

ETF price history is retrieved at runtime through `yfinance` and uses adjusted prices when available. The uploaded workbook supplies the ETF universe and can provide long-term CAGR fallbacks when live history is insufficient.

FRED indicators are retrieved with the FRED API.

## Ranking note

The ranking system is transparent and quantitative. It scores ETFs relative to the selected universe using historical returns across multiple periods. It does not provide individualized buy/sell advice.

Historical performance does not guarantee future results.
