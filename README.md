# Apple Stock Price Prediction with Autoregression

## Overview
The goal is to build machine learning models that can predict Apple's stock prices. The approach I used in the project is **autoregression**. For a given date, I used the prices from its previous 10 days to predict the stock price on that date. Since stock prices are missing for some dates (when the stock market is closed), I experimented with two different approaches-ML algorithms with a linearly interpolated dataset vs. XGBoost with an uninterpolated dataset.

## Preface
This is my term project for DATA1030: Hands-on Data Science. Time series data is one of the most common data types that a data scientist handles on a daily basis. However, it is also one of the trickiest data types to deal with. Since I have little experience in analyzing time series, I believe this project would be an excellent opportunity for me to sharpen such skills.

## Data
The dataset is downloaded from [Kaggle](https://www.kaggle.com/datasets/whenamancodes/alphabet-inc-google-founding-years-analysis) and can be found in the `data` folder. It contains Apple's stock prices from Dec. 15, 1980 to Sept. 19, 2022. The data is collected from Yahoo Finance.

## Method

## Results

## Python Environment
