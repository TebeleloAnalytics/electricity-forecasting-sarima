# Forecasting Electricity Distribution in South Africa Using SARIMA Models

## Overview

This project was completed as part of my Bachelor of Science Honours in Statistics 
at the University of Limpopo (2022). The study applies Seasonal Autoregressive 
Integrated Moving Average (SARIMA) time series models to forecast short-term 
electricity distribution in South Africa, focusing on Gauteng and Limpopo provinces.

The research contributes to the existing time series literature by comparing multiple 
SARIMA models and selecting the best-performing model for two-year electricity 
distribution forecasts.

---

## Problem Statement

South Africa faces significant electricity supply and distribution challenges. 
Accurate short-term forecasting of electricity distribution is critical for grid 
management, infrastructure planning, and policy decisions. This study addresses 
the need for reliable forecasting models using historical monthly electricity 
distribution data.

---

## Data

- **Source:** Statistics South Africa (Stats SA) — Eskom electricity distribution records
- **Period:** January 2000 to January 2022 (264 monthly observations)
- **Variable:** Electricity available for distribution (GWh — Gigawatt-hours)
- **Provinces analysed:** Gauteng and Limpopo
- **File:** `data/electricity_data.xlsx`

---

## Methodology

### Tools Used
| Tool | Purpose |
|------|---------|
| Python | Data cleaning, manipulation, feature engineering, ARIMA modelling, visualisation |
| R | Hypothesis testing (ADF, KPSS, Ljung-Box tests) |
| SPSS | Supporting statistical analysis |

### Process

**1. Exploratory Data Analysis**
- Time series plot of raw electricity distribution data
- Visual inspection for trend, seasonality and irregular components

**2. Stationarity Testing**
- ACF and PACF plots to identify non-stationarity
- Augmented Dickey-Fuller (ADF) test
- Kwiatkowski-Phillips-Schmidt-Shin (KPSS) test

**3. Differencing**
- First non-seasonal differencing to remove trend
- Seasonal differencing (lag 12) to remove seasonality
- Confirmed stationarity of differenced series via ADF test

**4. Model Identification and Estimation**
- Identified candidate SARIMA(p,d,q)(P,D,Q)₁₂ models from ACF and PACF patterns
- Estimated three competing SARIMA models per province
- Used Box-Jenkins methodology for model selection

**5. Model Diagnostics**
- Ljung-Box test for residual autocorrelation
- Q-Q plots for normality of residuals
- Residual ACF and PACF plots

**6. Model Selection**
- Compared models using AIC, BIC, and forecast error metrics
- Selected best-performing SARIMA model per province

**7. Forecasting**
- Generated two-year forecasts with 95% confidence intervals
- Evaluated forecast accuracy using MAE, MAPE, and MSE

---

## Key Results

- All three candidate SARIMA models produced acceptable fits for both provinces
- The best-performing model was selected based on lowest information criteria 
  and residual diagnostics
- The selected SARIMA model successfully captured both the upward trend and 
  monthly seasonal pattern (peaking in winter months — June/July)
- Notable anomaly detected: April 2020 shows a significant drop consistent 
  with COVID-19 lockdown impact on electricity demand

---

## Repository Structure
