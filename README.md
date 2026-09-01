# Weather Time Series Forecasting (Freelance)

Freelance project analyzing ~45 years (1976–2020) of monthly meteorological data — precipitation, temperature, and relative humidity — with exploratory time-series analysis and SARIMA forecasting.

## What it does

- **Data cleaning** (`data_cleaning.ipynb`): reads the raw meteorological Excel workbook (one sheet per variable), reshapes each from wide (year x month) to long format, maps month names to numbers, builds a proper date column, and exports one clean CSV per variable (`precipitaciones_mensual.csv`, `temperaturas_mensual.csv`, `humedad_mensual.csv`).
- **Time-series analysis & forecasting** (`model_aplication.ipynb`), applied to each of the three variables:
  1. Line plots of the full series, the last 4 years, and grouped by decade-ish ranges to spot trends.
  2. Seasonal decomposition (trend/seasonality/residual) plus ACF/PACF plots to characterize autocorrelation structure.
  3. A **SARIMA** (Seasonal ARIMA) model fit to capture both trend and seasonality.
  4. Forecast plots at 1, 2, and 5-year horizons.
- Every generated chart is saved under `figs/<variable>/` (`eda*.png` for exploratory plots, `model*.png` for the decomposition/ACF/PACF/forecast plots).

## Tech stack

Python, pandas, NumPy, statsmodels (seasonal decomposition, ACF/PACF, SARIMAX), seaborn/matplotlib.

## Project structure

```
data_cleaning.ipynb     # Excel -> long-format CSV per variable
model_aplication.ipynb  # EDA, decomposition, SARIMA, forecasts (run once per variable)
data/                   # Raw Excel + cleaned CSVs
figs/humedad/            # Humidity plots
figs/precipitaciones/    # Precipitation plots
figs/temperatura/         # Temperature plots
docs/                    # Written report (escrito.docx) and HTML exports of both notebooks
```

## How to run

```bash
pip install pandas numpy statsmodels seaborn matplotlib
```

Run `data_cleaning.ipynb` first to generate the three CSVs in `data/`, then `model_aplication.ipynb` — it repeats the same EDA → decomposition → SARIMA → forecast workflow for precipitation, temperature, and humidity in turn.
