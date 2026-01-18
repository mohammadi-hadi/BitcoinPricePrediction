<div align="center">

# Bitcoin Price Prediction

### Time Series Analysis and Machine Learning for Cryptocurrency Forecasting

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/)

*Comparing SARIMAX, XGBoost, and LSTM for Bitcoin price prediction*

---

</div>

## Overview

This project investigates Bitcoin price prediction using time series analysis and machine learning approaches. We compare three different methods:
- **SARIMAX**: Seasonal ARIMA with exogenous variables for time series forecasting
- **XGBoost**: Gradient boosting method with parallelized decision trees
- **LSTM**: Long Short-Term Memory neural network for sequence prediction

## Key Results

| Model | R² Score (Test Data) |
|-------|---------------------|
| LSTM | **98.51%** |
| XGBoost | 95.2% |
| SARIMAX | 89.7% |

LSTM achieved the best prediction accuracy with an R² of 98.51% on the test data.

## Dataset

- **Period**: Late 2014 to Early 2019
- **Train/Test Split**: 80% training, 20% testing
- **Source**: Historical Bitcoin price data

## Methods

### SARIMAX (Seasonal ARIMA)
Time series analysis model incorporating seasonal patterns and external factors.

### XGBoost
Gradient boosting framework that accelerates model learning by parallelizing decision tree construction.

### LSTM Neural Network
Deep learning approach using Long Short-Term Memory cells to capture long-term dependencies in sequential data.

## Repository Structure

```
BitcoinPricePrediction/
├── Bitcoin Price.xlsx  # Historical price data
├── LICENSE             # MIT License
├── CONTRIBUTING.md     # Contribution guidelines
└── README.md          # This file
```

## Quick Start

```bash
# Clone the repository
git clone https://github.com/mohammadi-hadi/BitcoinPricePrediction.git
cd BitcoinPricePrediction

# Install dependencies
pip install pandas numpy matplotlib scikit-learn xgboost tensorflow statsmodels
```

## Requirements

- Python 3.8+
- pandas
- numpy
- matplotlib
- scikit-learn
- xgboost
- tensorflow/keras
- statsmodels

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For questions or collaboration inquiries:
- **Hadi Mohammadi** - Utrecht University
- **Email**: [h.mohammadi@uu.nl](mailto:h.mohammadi@uu.nl)
- **Website**: [mohammadi.cv](https://mohammadi.cv)
