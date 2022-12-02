# Apple Stock Price Prediction with Autoregression

## Overview
The goal is to build machine learning models that can predict Apple's stock closing prices. The approach I used in the project is **autoregression**. For a given date, I used the prices from its previous 10 days to predict the closing stock price on that date. Since stock data is missing for some dates (when the stock market is closed), I experimented with two different approaches-ML algorithms with XGBoost with an uninterpolated dataset vs. a linearly interpolated dataset.

## Preface
This is my term project for DATA1030: Hands-on Data Science. Time series data is one of the most common data types that a data scientist handles on a daily basis. However, it is also one of the trickiest data types to deal with. Since I have little experience in analyzing time series, I believe this project would be an excellent opportunity for me to sharpen such skills.

## Data
The dataset is downloaded from [Kaggle](https://www.kaggle.com/datasets/whenamancodes/alphabet-inc-google-founding-years-analysis) and can be found in the `data` folder. It contains Apple's stock prices from Dec. 15, 1980 to Sept. 19, 2022. The data is collected from Yahoo Finance.

## Method
I generated the feature matrix with the number of lag days of 10, i.e., predicting the closing price on a given date with features from its previous 10 days. I split the feature matrix with a 60%-20%-20% ratio without shuffling to avoid information leakage. I also standardized all the features.

For the uninterpolated dataset, I trained an XGBoost model since it is one of the models that allow missing values. For the linearly-interpolated dataset, I trained models with Lasso Regression, Support Vector Machine, Random Forest, and XGBoost. The evaluation metric used is root-mean-square error (RMSE).

Please see `src/Apple_Stock_Price_Prediction.ipynb` for more details.

## Results
<img src="https://github.com/leehengpan/AAPL-StockPricePrediction/blob/main/figures/test_pred.png" width="600"/>
The plot shows the predictions of different models in the interpolated dataset. 
Lasso Regression performs the best (R<sup>2</sup>=0.99) since it only uses features from the previous day to make its predictions. 
Tree-based models (Random Forest and XGBoost) perform poorly on the dataset due to the property of the dataset and the splitting approach.
Tree-based models always give a constant prediction when encountering an outlier. To be more specific, the tree models are trained with data from 1980 to 2004, whereas all of the data points in the test set (from 2014 to 2022) are well beyond the scope of the training set. That's the reason why both models give constant predictions in the test set.

## Python Environment
