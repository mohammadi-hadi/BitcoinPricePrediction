<div align="center">

# Bitcoin Price Prediction with SARIMAX and LSTM

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21804037.svg)](https://doi.org/10.5281/zenodo.21804037)
[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Dataset: Kaggle](https://img.shields.io/badge/Dataset-Kaggle-20BEFF.svg)](https://www.kaggle.com/datasets/mczielinski/bitcoin-historical-data)

*Time-series forecasting of Bitcoin prices with a seasonal ARIMA model and an LSTM network.*

</div>

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

- **Preprocessing**: cleaning of the minute-level OHLC data (forward-filling prices, zero-filling volume for empty candles) and resampling for analysis.
- **Exploration**: interactive visualization of historical prices and trading volume with Plotly.
- **Diagnostics**: seasonal decomposition of the price series and stationarity checks with the augmented Dickey-Fuller test, plus ACF/PACF plots.
- **SARIMAX**: model selection via a grid search over (p, q, P, Q) orders, comparing candidates by AIC, followed by residual diagnostics.
- **LSTM**: a Keras model with a single 128-unit LSTM layer and a dense output layer, trained on MinMax-scaled prices.
- **Evaluation**: predictions compared against actual prices using MSE and MAE, with forecast-vs-actual plots.

## Quick Start

```bash
git clone https://github.com/mohammadi-hadi/BitcoinPricePrediction.git
cd BitcoinPricePrediction
pip install -r requirements.txt

git checkout Model   # the analysis script lives on this branch
```

1. Download the Kaggle minute-level dataset linked above and update the file paths at the top of `Bitcoin-ARIMA08.py`.
2. Run the script section by section (it was written as an exploratory script, e.g. in Spyder or a notebook environment).
3. Opening `bitcoin.wf1` requires [EViews](https://www.eviews.com/).

## Repository Structure

```
main branch
├── Bitcoin Price.xlsx   # Daily OHLC / volume / market cap data
├── requirements.txt     # Python dependencies
├── CONTRIBUTING.md
├── LICENSE
└── README.md

Model branch (analysis files)
├── Bitcoin-ARIMA08.py   # Main analysis script (SARIMAX + LSTM)
└── bitcoin.wf1          # EViews workfile with ARIMA analysis
```

## License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.

## Contact

- **Hadi Mohammadi** — Utrecht University
- Website: [mohammadi.cv](https://mohammadi.cv)
