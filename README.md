# Bitcoin Sentiment-Based Price Prediction

A Python machine learning project that explores Bitcoin price prediction using X (Twitter) sentiment and historical price features.

## Features

- Six prediction horizons: n+0 through n+5
- FinBERT sentiment analysis for real X posts
- Persistence, Linear Regression and Gradient Boosting models
- Chronological walk-forward validation with leakage controls
- Trading backtests with transaction costs and slippage
- Interactive Streamlit dashboard
- SQLite storage, evaluation reports and charts

## Demo Data

The dashboard uses synthetic data and requires no API keys.

Demo results demonstrate the software pipeline only. They are not real market performance or investment advice.

## Installation

Requires Python 3.12.

```bash
git clone https://github.com/Nimishyadav/bitcoin-sentiment-price-prediction.git
cd bitcoin-sentiment-price-prediction
python -m venv .venv
```

Activate the environment on Windows:

```powershell
.venv\Scripts\Activate.ps1
```

On macOS/Linux:

```bash
source .venv/bin/activate
```

Install dependencies:

```bash
python -m pip install -r requirements.txt
```

## Run the Dashboard

```bash
python -m streamlit run app.py
```

The dashboard includes:

- Price and sentiment overview
- Forecast explorer
- Strategy performance and drawdowns
- Model comparison
- Methodology and report downloads

## Run the Demo Pipeline

```bash
python scripts/run_pipeline.py
```

Set `DEMO_MODE=true` when using a local `.env` file.

## Prediction Horizons

At the completed hourly bar cutoff t:

| Target | Predicted close |
|---|---|
| n+0 | t + 1 hour |
| n+1 | t + 2 hours |
| n+2 | t + 3 hours |
| n+3 | t + 4 hours |
| n+4 | t + 5 hours |
| n+5 | t + 6 hours |

## Validation

Models use expanding chronological training windows.
Six training origins are purged before each test window.
Preprocessing is fitted only on training data.

Metrics include MAE, RMSE, R² and directional accuracy.

Backtests include Sharpe ratio, Sortino ratio, maximum drawdown,
returns, volatility and win rate.

## Data Sources

- Apify: X posts
- Yahoo Finance through yfinance: historical prices
- Tavily: news context
- Exa: optional research context

Only X sentiment and price-derived features enter the models.
News and research context are excluded from predictive inputs.

## Real-Data Status

An exported sample of 20 real X posts was used to verify Actor mapping.
Complete 180-day X history and real-data model evaluation remain unavailable.

Automatic Apify runs are disabled in the free workflow.
The public dashboard uses only the synthetic demo snapshot.

## Tests

```bash
python -m pytest -q
```

The latest verified project version passed 21 tests.

## Reports and Deployment

- Evaluation: `reports/evaluation_report.md`
- Charts: `reports/figures/`
- Setup and hosting: `DEPLOYMENT.md`

## Security

Never upload `.env`, API keys or private raw datasets.
Use `.env.example` as a configuration reference.


<img width="1917" height="967" alt="Screenshot 2026-10-18 135723" src="https://github.com/user-attachments/assets/494d6a91-5a4c-4cde-91af-c8d817b00bec" />
