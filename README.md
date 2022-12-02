# Apple Stock Price Prediction with Autoregression

## Overview
The goal is to build machine learning models that can predict Apple's stock closing prices. The approach I used in the project is **autoregression**. For a given date, I used the prices from its previous 10 days to predict the closing stock price on that date. Since stock data is missing for some dates (when the stock market is closed), I experimented with two different approaches-ML algorithms with XGBoost with an uninterpolated dataset vs. a linearly interpolated dataset.

## Preface
This is my term project for DATA1030: Hands-on Data Science. Time series data is one of the most common data types that a data scientist handles on a daily basis. However, it is also one of the trickiest data types to deal with. Since I have little experience in analyzing time series, I believe this project would be an excellent opportunity for me to sharpen such skills.

## Data
The dataset is downloaded from [Kaggle](https://www.kaggle.com/datasets/whenamancodes/alphabet-inc-google-founding-years-analysis) and can be found in the `data` folder. It contains Apple's stock prices from Dec. 15, 1980 to Sept. 19, 2022. The data is collected from Yahoo Finance.

## Method
I generated the feature matrix with the number of lag days of 10, i.e., predicting the closing price on a given date with features from its previous 10 days. I split the feature matrix with a 60%-20%-20% ratio without shuffling to avoid information leakage. I also standardized all the features.

Please see `src/Apple_Stock_Price_Prediction.ipynb` for more details.

## Results
<img src="https://github.com/leehengpan/AAPL-StockPricePrediction/blob/main/figures/test_pred.png" width="600"/>


## Python Environment
