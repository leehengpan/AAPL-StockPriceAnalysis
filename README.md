# Apple Stock Price Prediction with Autoregression

## Overview
The goal is to build machine learning models that can predict Apple's stock closing prices. The approach I used in the project is **autoregression**. For a given date, the prices and volumes from its previous 10 days are used to predict the closing stock price on that date. Since stock data is missing for some dates (when the stock market is closed), I experimented with two different approaches—XGBoost with an uninterpolated dataset vs. ML algorithms with a linearly-interpolated dataset.

## Motivation
This is my term project for DATA1030: Hands-on Data Science at Brown University. Time series data is one of the most common data types that a data scientist handles on a daily basis. However, it is also one of the trickiest data types to deal with. Since I have little experience in analyzing time series, I believe this project would be an excellent opportunity for me to sharpen such skills.

## Data
The dataset is downloaded from [Kaggle](https://www.kaggle.com/datasets/whenamancodes/alphabet-inc-google-founding-years-analysis) and can be found in the `data` folder. It contains Apple's stock prices from Dec. 15, 1980 to Sept. 19, 2022. The data is collected from Yahoo Finance.

## Method
I generated the feature matrix with the number of lag days of 10, i.e., predicting the closing price on a given date with features from its previous 10 days. I split the feature matrix with a 60%-20%-20% ratio without shuffling to avoid information leakage. I also standardized all the features.

For the uninterpolated dataset, I trained an XGBoost model since it is one of the models that allow missing values. 

For the linearly-interpolated dataset, I trained models with Lasso Regression, Support Vector Machine, Random Forest, and XGBoost. The evaluation metric used is root-mean-square error (RMSE).

Please see `src/Apple_Stock_Price_Prediction.ipynb` for more details.

## Results
<img src="https://github.com/leehengpan/AAPL-StockPricePrediction/blob/main/results/test_pred.png" width="600"/>

The plot shows the predictions of different models in the interpolated test set.

- The tree-based models (Random Forest and XGBoost) perform poorly on the dataset due to the property of the dataset and the splitting approach. They always give a constant prediction when encountering an outlier. To be more specific, the tree models are trained with data from 1980 to 2004, whereas all of the data points in the test set (from 2014 to 2022) are well beyond the scope of the training set. That's the reason why both models give constant predictions in the test set.
- The Lasso Regression model performs the best (RMSE=1.26) since it linearly extrapolates when encountering outliers.
- The Support Vector Machine model also performs decently because it handles outliers with non-linear extrapolation. 

## Environment
```
- python=3.10.5
- matplotlib=3.5.2
- pandas=1.4.2
- scikit-learn=1.1.1
- numpy=1.22.4
- xgboost=1.5.1
- shap=0.40.0
- jupyter_client=7.3.1
- jupyter_core=4.10.0
- jupyterlab=3.4.2
- jupyter_server=1.17.0
- jupytext=1.13.8
- rise=5.7.1
- plotly=5.8.0
- ipywidgets=7.7.0
- openpyxl=3.0.10
- seaborn=0.12.1
```
