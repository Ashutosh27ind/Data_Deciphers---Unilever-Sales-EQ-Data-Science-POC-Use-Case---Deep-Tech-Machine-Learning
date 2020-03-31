# Data_Deciphers---Unilever-Sales-EQ-Data-Science-POC-Use-Case---Deep-Tech-Machine-Learning
Determination of major drivers of sales and forecasting sales for next 6 periods


**Project Title: Unilever Data Science POC Use Case** 

**Problem Statement:** The titled project is a part of the MishMash diversity hackathon and we are exposed, here, to a diverse set of problems. Firstly, one of Unilever’s brands is going through some major changes in business execution plans and to dive deeper, they want to know the major drivers of sales. Additionally, they also want to foresee sales for the coming six periods.  

**Data Description:**  
We are provided with four datasets:
a) daily basis data (data-1) with 12000 rows and 38 columns,    
b) A test dataset (data-2), based on some period (a period has 13 intervals and each interval reflects 4 weeks). 
c) To make the hackathon more challenging by creating data scarcity, the test data in (b) was then further divided into new train (data-3) and test data (data-4).

**Approach:** To identify the major drivers, the data-1 with 12000 data points was divided into train and test datasets. We could realize that log1p transformation of the target variable (EQ) was necessary to achieve higher accuracy. After scaling, the data were fed to three different algorithms: Linear Regression (OLS), ElasticNet, and XGBoost. For Linear Regression, the automatic feature selection was done by utilizing RFE.
Let’s now move to the forecasting. Firstly, the time-steps in train (data-1) and test (data-2) are different. To make them uniform, each 28 consecutive rows were aggregated by taking their mean. Interestingly, the target variable did not show any underlying trend. To keep all the values in positive side, a log transformation of EQ has been performed. The proper lag value was judiciously chosen from ACF and PACF plots. After screening several p, q & d, the best ones were selected to get the best fit in ARIMA. All the coefficients in AR part are negative, indicating underlying negative trend. After prediction, we have checked for residual series’ stationarity with Augmented Dickey-Fuller and KPSS tests and both suggested the residual as white noise. Finally, MAPE on test and train series were calculated.  

**Results:** In the first part, we could successfully predict the sales and identified the major drivers. In total, three algorithms were attempted: Linear Regression (OLS), ElasticNet and XGBoost. Models from all the three landed up with same top seven features. By considering the majority vote, the top three drivers are: 1) Median_Rainfall, 2) Social_Search_Impressions and 3) pct_PromoMarketDollars_Category. As far the accuracy is concerned, the XGBoost regressor outperforms the other two, with an accuracy of 0.99.
As expected, the larger data (data-1) leads to a model with more accurate forecasting capability. The ARIMA based model, here, forecasted with a MAPE of 26.3445. On the other hand, the model with smaller data (data-3) was found to be bit overfitted and projected sales with a MAPE of 44.2956.

**Project Learnings:** Forecasting was completely new to the ‘Data_Deciphers’ and we were successfully able to cross this bottleneck. This hackathon surely elevated our confidence level as well as it improved our team working ability.

