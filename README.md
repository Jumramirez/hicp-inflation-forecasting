# Euro Area HICP Inflation Forecasting

Comparison of three forecasting models for euro area headline inflation (HICP),
evaluated on a 24-month hold-out period.

## Research question

How well do standard statistical models and a simple neural network forecast euro area
inflation over a two-year horizon, compared with the actual data and the ECB's 2% target?

## Data

- **Source:** ECB Data Portal, series `ICP.M.U2.N.000000.4.ANR`
- **Variable:** euro area HICP, annual rate of change (%), monthly
- Data are downloaded directly from the ECB API when the notebook runs.

## Method

- **Train/test split:** the last 24 months are held out as the test set; models are
  estimated on the remaining data only.
- **Models:**
  - **ARIMA**, with order selected automatically (`auto.arima`)
  - **ETS** (exponential smoothing), with model selected automatically
  - **NNAR**, a feed-forward neural network using lagged values of the series as inputs
- **Evaluation:** RMSE and MAE on the test set.

## Limitations

- Univariate models: forecasts use only past inflation, not drivers such as energy
  prices, wages or monetary policy.
- The data include the 2021–2023 inflation surge, an unusual episode that is hard
  to forecast for any model based on history alone.
- A single train/test split; rolling-origin evaluation would give more robust results.

## How to run

1. Install the packages in R: `install.packages(c("forecast", "ggplot2"))`
2. Open `hicp_forecasting.ipynb` in Jupyter with an R kernel and run all cells.

## References

- Hyndman, R.J. & Athanasopoulos, G. *Forecasting: Principles and Practice* (3rd ed.), OTexts.
- ECB Data Portal: https://data.ecb.europa.eu
