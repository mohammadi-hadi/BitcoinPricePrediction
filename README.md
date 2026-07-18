# Bitcoin Price Prediction

Time-series analysis of historical Bitcoin prices using seasonal ARIMA (SARIMAX) and an LSTM neural network.

[![Python](https://img.shields.io/badge/python-3.x-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## Overview

This is a study project on forecasting Bitcoin prices from historical market data. It explores the price series (trend, seasonality, stationarity) and compares two forecasting approaches:

- a classical statistical model — seasonal ARIMA (SARIMAX), selected by grid search over model orders, and
- a deep learning model — an LSTM network trained on the scaled price series.

An EViews workfile with a complementary ARIMA analysis is also included alongside the Python script.

## Data

- `Bitcoin Price.xlsx` (this branch): daily Bitcoin open/high/low/close prices, trading volume, and market capitalization, roughly 2013 to early 2019 (about 2,160 daily records).
- The Python script itself reads the [Bitcoin Historical Data](https://www.kaggle.com/datasets/mczielinski/bitcoin-historical-data) from Kaggle (`coinbaseUSD` 1-minute bars, December 2014 to January 2019), which is not committed here due to its size. It works with the `Weighted_Price` column after resampling.

## Methods

Implemented in `Bitcoin-ARIMA08.py` (on the [`Model`](../../tree/Model) branch):

- Cleaning of the minute-level OHLC data (forward-filling prices, zero-filling volume for empty candles) and resampling for analysis.
- Interactive visualization of historical prices and trading volume with Plotly.
- Seasonal decomposition of the price series and stationarity checks with the augmented Dickey-Fuller test, plus ACF/PACF plots.
- SARIMAX model selection via a grid search over (p, q, P, Q) orders, comparing candidates by AIC, followed by residual diagnostics.
- An LSTM model (Keras) with a single 128-unit LSTM layer and a dense output layer, trained on MinMax-scaled prices.
- Evaluation of predictions against actual prices using MSE and MAE, with forecast-vs-actual plots.

## Repository structure

```
main branch
├── Bitcoin Price.xlsx   # Daily OHLC / volume / market cap data
├── CONTRIBUTING.md
├── LICENSE
└── README.md

Model branch (analysis files)
├── Bitcoin-ARIMA08.py   # Main analysis script (SARIMAX + LSTM)
└── bitcoin.wf1          # EViews workfile with ARIMA analysis
```

## Requirements / How to run

Python 3 with:

```
pandas numpy matplotlib seaborn plotly scipy statsmodels scikit-learn tensorflow keras pytz
```

1. Check out the `Model` branch to get `Bitcoin-ARIMA08.py`.
2. Download the Kaggle minute-level dataset linked above and update the file paths at the top of the script.
3. Run the script section by section (it was written as an exploratory script, e.g. in Spyder or a notebook environment).

Opening `bitcoin.wf1` requires EViews.

## License

MIT — see [LICENSE](LICENSE).

## Author

Hadi Mohammadi — [mohammadi.cv](https://mohammadi.cv)
