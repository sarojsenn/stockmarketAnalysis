
# Stock Market Analysis Using News Sentiment and Machine Learning

## Overview

This project explores the relationship between financial news sentiment and stock market movements using the NIFTY 50 index. It combines financial news headlines with historical market data to investigate whether sentiment-related and market-based features can help classify the next day's market direction.

The project uses Natural Language Processing (NLP) techniques for lexicon-based sentiment scoring and machine learning models for binary market-direction classification.

## Problem Statement

Stock market movements are influenced by multiple factors, including market trends, trading activity, and investor reactions to financial news. Analyzing news and historical price data separately may overlook potentially useful relationships between market sentiment and price movements.

The objective of this project is to investigate whether financial news sentiment, historical price movements, trading volume, and volatility-related features can help predict the next trading day's NIFTY 50 market direction.

## Objectives

- Clean and preprocess financial news and historical NIFTY 50 data.
- Combine news headlines with stock market data using dates.
- Calculate sentiment scores from financial news headlines.
- Engineer features using sentiment trends, historical market movements, trading volume, and price ranges.
- Train and compare multiple machine learning classification models.
- Evaluate model performance against a majority-class baseline.
- Visualize model results and feature importance.
- Explore a simple trading strategy through historical backtesting.

## Dataset

The project uses two input datasets:

### 1. Financial News Dataset
Contains financial news information, including fields such as:
- Date
- Title
- Description
- Author
- Content
- Keywords

The analysis primarily uses the news date and headline title.

### 2. NIFTY 50 Historical Market Dataset
Contains historical market information, including:
- Date
- Open price
- High price
- Low price
- Close price
- Shares traded
- Turnover (in crores)

Place both CSV files in the project directory and update their file paths in the notebook if necessary.

Expected filenames:
- `news.csv`
- `nifty50.csv`

## Methodology

### 1. Data Preprocessing
- Load financial news and NIFTY 50 data using Pandas.
- Remove missing values and duplicate news records.
- Standardize relevant column names.
- Convert date columns into datetime format.
- Group news headlines by date.
- Merge news and market data using the corresponding dates.

### 2. Sentiment Analysis

A lexicon-based sentiment scoring method assigns scores to financial news headlines.

- Positive financial keywords contribute positive scores.
- Negative financial keywords contribute negative scores.
- The combined score represents the headline sentiment signal.

The sentiment score is used to examine its relationship with observed market movements.

### 3. Feature Engineering

The machine learning pipeline uses the following features:

- Daily sentiment score
- Three-day rolling average of sentiment
- Seven-day rolling average of sentiment
- Three-day rolling sentiment standard deviation
- One-day lagged market movement
- Two-day lagged market movement
- Percentage change in shares traded
- High-low price spread relative to the opening price

The target variable represents the next trading day's market direction, classified as Up or Down.

### 4. Machine Learning Models

The notebook implements and evaluates the following models:

- Logistic Regression
- Random Forest Classifier
- XGBoost Classifier

Random Forest hyperparameters are also tuned using GridSearchCV with TimeSeriesSplit cross-validation.

### 5. Model Evaluation

The project evaluates model performance using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrix
- Majority-class baseline comparison

The dataset is divided chronologically into training and testing periods to preserve temporal ordering.

### 6. Visualization and Backtesting

The notebook generates visualizations to examine:

- Distribution of news sentiment scores
- Average sentiment by observed market direction
- Relationship between sentiment and market movement
- Confusion matrix of the tuned Random Forest model
- Feature importance
- Simulated strategy performance compared with a buy-and-hold benchmark

## Technology Stack

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- Jupyter Notebook

Generated CSV files and plots will appear after running the corresponding notebook cells.

## Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/sarojsenn/stockmarketAnalysis.git
cd stockmarketAnalysis
```

### 2. Create a virtual environment (optional)

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost jupyter
```

### 4. Add the datasets

Place `news.csv` and `nifty50.csv` in the project directory.

Update the CSV paths in the notebook to match their actual locations. The current notebook uses absolute paths, which may need to be changed when running locally.

### 5. Run the notebook

```bash
jupyter notebook stockMarketAnalysis.ipynb
```

Execute the cells in order to preprocess the data, train models, evaluate predictions, and generate visualizations.

## Expected Outcomes

The project is designed to produce:

- A cleaned and merged news-market dataset.
- Sentiment scores for financial news headlines.
- Engineered features for market-direction classification.
- Trained machine learning models and evaluation reports.
- A confusion matrix and feature-importance visualization.
- A comparison of a simple simulated trading strategy against buy-and-hold performance.

Actual results depend on the datasets, preprocessing, model configuration, and evaluation period. No performance figures are assumed in this README.

## Limitations

- Lexicon-based sentiment scoring may not capture context, sarcasm, or complex financial language.
- Financial news sentiment alone cannot explain all market movements.
- Historical model performance does not guarantee future performance.
- Backtesting results may be affected by transaction costs, slippage, execution assumptions, and other practical trading constraints.
- The project is intended for educational and analytical purposes, not as financial advice or a guarantee of profitable trading.

## Future Improvements

- Implement finance-specific NLP models such as FinBERT.
- Explore more advanced time-series forecasting approaches.
- Improve feature engineering and validate features against data leakage.
- Add transaction costs and more realistic execution assumptions to backtesting.
- Evaluate models across different market periods and benchmark indices.
- Experiment with probability calibration and risk-aware trading rules.

## Author

**Saroj Sen**

GitHub: [@sarojsenn](https://github.com/sarojsenn)

---

*This project is an exploration of financial news sentiment, historical market data, and machine learning for market-direction classification.*
