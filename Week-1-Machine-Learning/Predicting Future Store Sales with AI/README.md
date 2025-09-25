#  Predicting Future Store Sales with AI

##  Project Overview
This project applies **time series forecasting** techniques to predict future store sales using historical data. The workflow includes **Exploratory Data Analysis (EDA)**, **stationarity testing**, **feature engineering**, and the development of ARIMA and SARIMA models for forecasting. The dataset consists of monthly passenger counts, a classic benchmark time series.

---

##  Dataset
The dataset contains **144 monthly records** with the following columns:

- **Month**: Timestamp of observation (1949–1960).
- **Passengers**: Number of airline passengers in that month.

---

##  Exploratory Data Analysis (EDA)
- The time series plot showed a **clear upward trend** and **strong seasonality** (annual cycles).
- Variance increased over time, indicating **non-stationarity**.
- Seasonal decomposition confirmed three components:
  - **Trend**: long-term increase in passenger numbers.
  - **Seasonality**: repeating yearly fluctuations.
  - **Residuals**: random noise not explained by trend/seasonality.
- Rolling statistics and autocorrelation plots further confirmed that the data was **non-stationary**.

---

##  Stationarity Testing
The **Augmented Dickey-Fuller (ADF) test** was applied at multiple stages:

1. **Original Series**  
   - p-value ≈ 0.99 → Non-stationary.  

2. **Log Transformation**  
   - p-value ≈ 0.42 → Reduced variance but still non-stationary.  

3. **Log + First Differencing**  
   - p-value ≈ 0.07 → Closer to stationarity, but seasonal patterns remained.  

4. **Feature Engineering: Box-Cox Transformation + Differencing**  
   - Box-Cox transformation automatically optimized λ to stabilize variance.  
   - After differencing, p-value < 0.05 → series became **stationary**.  

---

##  Model Development

### ARIMA (Non-Seasonal)
- Built on the **log-transformed data**.  
- Performed poorly due to **non-stationarity and strong seasonality**.  
- Residual plots showed patterns, and forecast accuracy was limited.  

### SARIMA (Seasonal ARIMA)
- Built on the **Box-Cox transformed and differenced series**.  
- Captured both **trend** and **seasonality** effectively.  
- Residuals resembled white noise, indicating a good fit.  
- Outperformed ARIMA on accuracy metrics (e.g., lower RMSE and MAE).  

---

##  Results & Insights
- ARIMA struggled because the series retained seasonal structure.  
- SARIMA, which explicitly models seasonality, achieved **better accuracy and more reliable forecasts**.  
- Feature engineering with **Box-Cox + differencing** was essential to achieve stationarity and unlock strong model performance.  

---

##  Conclusion
- The dataset is **non-stationary** with clear trend and seasonality.  
- Standard log transforms and differencing were insufficient, but **Box-Cox + differencing achieved stationarity**.  
- SARIMA significantly outperformed ARIMA, making it the preferred choice for forecasting future store sales.  
- This workflow highlights the importance of **EDA, stationarity testing, and feature engineering** in time series forecasting.  

---

##  Tools & Libraries
- **Python** (Pandas, NumPy)  
- **Statsmodels** (ADF Test, ARIMA, SARIMA, Seasonal Decompose)  
- **Matplotlib, Seaborn** (Visualization)  
- **SciPy** (Box-Cox Transformation)  

---
