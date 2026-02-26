Time Series Forecasting Project – Sales Prediction
Dataset: Kaggle – Store Sales Time Series Forecasting
https://www.kaggle.com/competitions/store-sales-time-series-forecasting
Objective:
Predict sales for thousands of product families across multiple stores in Ecuador using historical sales, promotions, store metadata, oil prices, and holiday effects.
Dataset Understanding
Main File – train.csv
• date
• store_nbr
• family
• sales (target variable)
• onpromotion
Additional Files
• test.csv (15 future days to predict)
• stores.csv (city, state, type, cluster)
• oil.csv (daily oil price)
• holidays_events.csv (holidays, transfers, bridge days)
Important Business Context
• Public wages paid on 15th and last day of month
• Oil price impacts Ecuador economy
• Earthquake on 2016-04-16 affected sales
• Transferred holidays must be handled correctly
Project Data Splitting Strategy
Step 1 – Reserve Final 30 Days
• Sort by date
• Remove last 30 days from train.csv
• Keep completely unseen for final validation
Step 2 – Train/Test Split
• Use remaining data
• First 80% → Training set
• Last 20% → Test set
• No random shuffling
Step 3 – Final Validation
• Retrain best model on full data except last 30 days
• Forecast those 30 days
• Compare with actual sales
Data Preparation
• Convert date to datetime
• Set date as index
• Sort chronologically
• Handle missing oil prices (interpolation)
• Merge stores.csv
• Merge oil.csv
• Merge holidays_events.csv
• Handle transferred holidays correctly
Exploratory Data Analysis
Global Sales Trend
• Total daily sales across all stores
• Rolling averages (7-day, 30-day)
Store-Level Analysis
• Sales by store_nbr
• Cluster-based comparison
Product Family Analysis
• Sales by family
• Top and low performing families
Promotion Impact
• Compare sales with onpromotion
• Promotion vs non-promotion days
Oil Price Impact
• Sales vs oil price trend
• Correlation analysis
Holiday & Event Impact
• Holiday vs normal days
• Bridge days effect
• Transferred holidays handling
Special Event Analysis
• Earthquake period sales spike
• Pre and post earthquake comparison
Wage Effect Analysis
• Sales near 15th and month-end
• Compare mid-month spikes
Feature Engineering
Time-Based Features
• Year
• Month
• Day
• Day of week
• Week of year
• Is weekend
• Is month start
• Is month end
• Is wage period (15th or last day)
Lag Features
• Sales lag 1
• Sales lag 7
• Sales lag 14
• Sales lag 30
Rolling Features
• 7-day rolling mean
• 30-day rolling mean
• Rolling standard deviation
Promotion Features
• Total items on promotion
• Promotion rolling average
Holiday Features
• Is holiday
• Is transferred holiday
• Is bridge day
External Features
• Oil price
• Oil price rolling average
• Store cluster
• Store type
Model Training
Training Phase
• Train on 80% training data
• Evaluate on 20% test data
Models
• ARIMA
• SARIMA
• Linear Regression
• Random Forest
• XGBoost
Evaluation Metrics
• MAE
• RMSE
• MAPE
• R²
Model Comparison
• Compare all models on test set
• Select best performing model
Final 30-Day Forecast Validation
Validation Setup
• Use reserved last 30 days
• Train best model on all prior data
• Forecast next 30 days
Validation Evaluation
• MAE
• RMSE
• MAPE
• R²
Validation Plots
• Actual vs Predicted (30 days)
• Residual error plot
• Residual distribution
Future Forecast
• Retrain model on full dataset
• Forecast next 15 days (matching Kaggle test set)
• Prepare prediction output format
• Generate submission file
Deliverables
• Cleaned and merged dataset
• Full EDA analysis
• Feature engineering implementation
• Train-test evaluation results
• Final 30-day validation results
• Forecast plots
• Model comparison table
• Submission-ready predictions
