# 🌧️ Rainfall Prediction in Uttarakhand Using Deep Learning Models (ERA5: 2020–2025)

![Python](https://img.shields.io/badge/Python-3.10-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)
![ERA5](https://img.shields.io/badge/Data-ERA5%20Reanalysis-green)
![License: CC BY](https://img.shields.io/badge/License-CC%20BY-lightgrey)

## 📌 Overview
This repository contains the full workflow for **daily rainfall prediction** in the Uttarakhand region using **deep learning models (MLP, LSTM, GRU, CNN1D)** and ERA5 reanalysis data from **2020–2025**.  
The goal is to understand rainfall dynamics in complex Himalayan terrain while comparing the performance of different models.

---

## 📂 Dataset
We use the **ERA5 Derived Daily Single-Level Statistics** dataset from the Copernicus Climate Data Store.

🔗 Dataset Link:  
https://cds.climate.copernicus.eu/datasets/derived-era5-single-levels-daily-statistics?tab=download

- **Variables used**
  - Daily precipitation (mm/day)
  - 3-hourly mean sea-level pressure → resampled to daily
  - Derived features:  
    - month_sin / month_cos  
    - 7-day rolling mean/std  
    - pressure tendency (daily diff)

- **Region**: Uttarakhand (clipped using regionmask + GeoJSON)  
- **Period**: 2020–2025  
- **License**: CC BY (Copernicus C3S)

---

## 🛠️ Preprocessing Pipeline
1. Download ERA5 raw NetCDF files.
2. Clip the region to Uttarakhand using regionmask.
3. Resample pressure data (3-hourly → daily).
4. Align precipitation & pressure timestamps.
5. Create engineered features.
6. Export:
   - `uttarakhand_daily_features_area_mean.csv`
   - Optional grid-level parquet.

---

## 🤖 Models Implemented
| Model | Framework | Notes |
|-------|-----------|-------|
| **MLP** | TensorFlow | Best performance (R² ≈ 0.805) |
| **LSTM** | TensorFlow | Captures temporal dependencies |
| **GRU** | TensorFlow | Faster than LSTM |
| **CNN1D** | TensorFlow | Convolutions on time window |
| **KNN / Decision Tree (Optional)** | sklearn | Baselines |

All metrics (MAE, RMSE, R²) saved in `<model>_metrics.csv`.

---

## 📊 Results Summary
- **MLP performed the best**:  
  - R² ≈ **0.805**  
  - Lowest MAE & RMSE  
- Reanalysis showed strong seasonal patterns and pressure–rainfall coupling.
- Visualisations (saved in `/figures/`):
  - Seasonal cycle plots  
  - Histogram & distribution  
  - Extreme rainfall time-series  
  - Model comparison plots  

---
