# Forecasting Electricity Distribution in South Africa (SARIMA)

Research project I completed during BSc Honours in Statistics studies (University of Limpopo, 2022). It forecasts monthly electricity distribution in South Africa with seasonal ARIMA (SARIMA) time-series models, focusing on Gauteng and Limpopo.

**Result:** the best of three candidate models forecast monthly distribution with a **2.45% mean absolute percentage error** (MAPE). It was then used to produce a two-year forecast with 95% confidence intervals.

---

## Problem

South Africa's electricity supply is under constant pressure. Accurate short- and medium-term forecasts of how much electricity will be distributed help with grid management, maintenance planning and energy purchasing.

## Data

- **Source:** Statistics South Africa, monthly electricity available for distribution, in gigawatt-hours (GWh)
- **Period:** monthly observations from 2002 to 2022 (full table in the thesis appendix)
- **File:** `Excel table from 2000.xlsx` (also `spss research data.sav` for SPSS)

## Method (Box-Jenkins)

1. **Explore:** time-series plots to check for trend and seasonality, which peaks in the winter months of June and July
2. **Test stationarity:** ACF/PACF plots and the Augmented Dickey-Fuller test
3. **Difference:** first-order differencing for the trend and seasonal differencing (lag 12) for seasonality
4. **Identify candidate models:** three SARIMA(p,d,q)(P,D,Q)₁₂ models chosen from the ACF/PACF patterns
5. **Diagnose:** residual checks (autocorrelation, normality)
6. **Select:** compared on RMSE, MAE, MAPE, R² and information criteria
7. **Forecast:** two years ahead with 95% confidence intervals

## Results

| Model | R² | RMSE | MAE | MAPE |
|---|---|---|---|---|
| Model 1 | 94.8% | 55.78 | 36.25 | 2.56% |
| Model 2 | 93.8% | 55.98 | 36.43 | 2.50% |
| **Model 3 (selected)** | 94.1% | **54.60** | **35.72** | **2.45%** |

Model 3 had the lowest error on every accuracy measure and lost only on BIC, to Model 1. For context, average monthly distribution was about 1,456 GWh, so an average error of about 36 GWh is small.

A sharp drop in April 2020 matches the COVID-19 lockdown. It's a good example of a real-world shock that a seasonal model can't anticipate.

## Tools

| Tool | Used for |
|---|---|
| Python (pandas, statsmodels, matplotlib) | Data preparation, stationarity tests, SARIMA modelling, plots |
| SPSS | Model fit statistics and supporting analysis |

## Files

| File | What it is |
|---|---|
| `Time Series.ipynb` | Python analysis notebook |
| `Excel table from 2000.xlsx` | Source data |
| `spss research data.sav` | Same data in SPSS format |
| `Final Research_Selowa (2).docx` | Full research report (method, diagnostics, forecasts, references) |

**Note:** the notebook reads the data from CSV files (`data.csv`, `final.csv`), which were exported from the Excel table and aren't in this repo. To re-run it, export the relevant sheet from `Excel table from 2000.xlsx` to `data.csv`.

## What I'd do now

- Make the notebook fully reproducible: read straight from the Excel file and pin package versions
- Add a hold-out test period (e.g. train to 2019, test on 2020–2021) so accuracy is measured on data the model never saw
- Compare against simple baselines (seasonal naive) and newer methods such as Prophet or gradient boosting with calendar features
