# Best Buy Case

## Introduction

Georgia Tech's 2023 Master of Science in Analytics Project Week consisted of a collaboration with Best Buy to develop an efficient and accurate model to forecast its slow-moving SKUs. Historically, highly accurate neural network models have taken days to run, and Best Buy needed a model that was both fast and accurate to meet its business needs. Our challenge was to use a time series dataset with five years of selling and stock rate data for 575 SKUs to predict the next seven days of sales by SKU.

## Findings

An initial exploratory analysis revealed the intermittency of our data, in addition to a few features we imputed or engineered:  
-Missing values: Imputed missing values as 0, since the unit did not sell on those days   
-Trend and seasonality: Sales are much higher on Fridays, Saturdays, and Sundays than other days of the week. They are also higher on holidays. Sales show clear seasonality trends, peaking in December   
-We engineered some additional features, including Global Supply Chain Pressure Index, an inflation index, day of the week, and holiday   

## Conclusions

Ultimately, we think an ensemble model that combines the lightweight and efficient approach of the Croston time series model and the flexibility and feature advantages of an XGBoost or Random Forest model would be most effective. This would involve splitting the data into 'most slow-moving' and 'less slow-moving' SKUs and developing a Croston model for the most slow-moving SKUs and an XGBoost or Random Forest regression model for the highest-selling of the SKUs in this dataset. This is an area for further research and development. However, in the meantime, the Croston model provides a lightweight, easy-to-use forecasting methodology that is fairly accurate and very fast to run.

## Files
-HTS_Model: We developed a hierarchical time series model to predict selling values by each subclassification of the SKUs (individual SKU, subclass, class, category, etc.). We found that this model was highly accurate in predicting selling volumes for higher class levels, but could not accurately predict individual SKU sales.   
-Croston_Model_3: A Croston time series model to predict individual SKU selling units based only on historical sales data.   
-03_xgboost_trial: The advantage of the XGBoost model is it could include key features such as a consumer inflation index, holidays, day of the week data, and other feature data. However, it ultimately performed poorly on the validation set. Further tuning could potentially improve RMSE.   
-RF_importance, heatmap_corr, heatmap_corr_after: describe feature engineering for the XGBoost and Random Forest regression models we tested   
-Alpha_RMSE: shows values of alpha we tested to tune our Croston model   
