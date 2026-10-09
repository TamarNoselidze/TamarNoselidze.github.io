---
layout: page
title: "Global Drivers of Respiratory Mortality"
description: Multi-decadal machine learning analysis (1980-2023) across 180+ countries evaluating meteorological stress and satellite pollution data with spatial leakage control.
img: assets/img/climate.webp
importance: 5
category: Machine Learning & AI
related_publications: false
---

### Overview

This project quantifies multi-decadal relationships between meteorological stress, satellite-derived air quality, and respiratory mortality across **180+ countries over 43 years (1980-2023)**. Conducted as part of the *Data Analysis at Large Scale (DALAS)* curriculum at **Sorbonne Université** (January 2026), the study isolates environmental drivers from baseline demographics and global healthcare improvements.

- **Institution**: Sorbonne Université (Paris, France)
- **Collaborators**: Tamar Noselidze, Abdel Razak Sharafdin
- **Data Scope**: 43 years (1980-2023), 180+ countries, monthly and seasonal aggregations
- **Data Sources**: ERA5 Reanalysis (ECMWF climate), CAMS Reanalysis (Copernicus atmospheric pollutants), and IHME Global Burden of Disease (GBD 2021)

---

### Controlling Spatial Leakage

Standard random 80/20 train-test splits fail in spatial epidemiology because models memorise country identities, yielding artificially inflated metrics ($R^2 > 0.90$).

<div class="row justify-content-sm-center my-4">
  <div class="col-sm-10 text-center">
    <a href="{{ '/assets/img/dalas_spatial_leakage.png' | relative_url }}" target="_blank" rel="noopener noreferrer">
      <img src="{{ '/assets/img/dalas_spatial_leakage.png' | relative_url }}" class="img-fluid rounded z-depth-1" alt="Impact of Spatial Leakage Control on Model Accuracy" style="width: 100%; border: 1px solid var(--global-divider-color);">
    </a>
    <div class="caption text-muted mt-2" style="font-size: 0.85rem;">
      Comparison between standard random train-test splits (inflated $R^2 > 0.90$ from spatial leakage) versus Stratified Group K-Fold cross-validation ($R^2 \approx 0.30 - 0.44$).
    </div>
  </div>
</div>

We implemented **Stratified Group K-Fold Cross-Validation**:
- **Strict Spatial Holdout**: Entire nations are held out of training folds, forcing models to learn universal physical associations rather than geographical proxies.
- **Climate Stratification**: Folds are balanced across climate zones (Tropical, Arid, Temperate) to prevent covariate shift on unseen regions.
- **Secular Trend Controls**: Time controls isolate environmental signals from decade-over-decade healthcare gains.

---

### Key Findings & The "Ozone-Cold Nexus"

<div class="row justify-content-sm-center my-4">
  <div class="col-sm-10 text-center">
    <a href="{{ '/assets/img/dalas_feature_importance.png' | relative_url }}" target="_blank" rel="noopener noreferrer">
      <img src="{{ '/assets/img/dalas_feature_importance.png' | relative_url }}" class="img-fluid rounded z-depth-1" alt="Top Predictors for Lower Respiratory Infections" style="width: 100%; border: 1px solid var(--global-divider-color);">
    </a>
    <div class="caption text-muted mt-2" style="font-size: 0.85rem;">
      Top feature importances for Lower Respiratory Infection (LRI) mortality, highlighting the role of Tropospheric Ozone ($O_3$) and winter minimum temperature.
    </div>
  </div>
</div>

- **Tropospheric Ozone ($O_3$) vs. $\text{PM}_{2.5}$**: Across multi-pollutant models, **Tropospheric Ozone ($O_3$)** consistently emerged as a stronger global predictor of acute respiratory mortality than fine particulate matter ($\text{PM}_{2.5}$), displaying a non-linear threshold for oxidative mucosal stress.
- **Lower Respiratory Infections (LRI, $R^2 \approx 0.44$)**: Driven primarily by cold stress (winter minimum temperatures), where cold air impairs airway clearance and compounds ozone-induced inflammation.
- **Asthma ($R^2 \approx 0.39$)**: Strongly pollution-driven. Incorporating CAMS satellite data increased predictive accuracy (+120% gain, $\Delta R^2: 0.176 \to 0.387$).
- **COPD Negative Control ($R^2 < 0.15$)**: Environmental predictors explained minimal variance for COPD (predominantly driven by smoking and occupational exposure), verifying that models avoided spurious macro correlations.

---

### Feature Engineering

- **Seasonal Stress Indices**: Derived physiological metrics including the *Winter Severity Index*, *Summer Heat Stress Index*, and dewpoint depression ($\Delta T_{\text{dew}} = T_{\text{air}} - T_{\text{dewpoint}}$).
- **Dual-Track PCA**: Decomposed 60+ collinear atmospheric variables into orthogonal meteorological and chemical pollution modes across ERA5 (1980-2023) and CAMS (2003-2023) records.

---

### Code & Resources

- **GitHub Repository**: [TamarNoselidze/DALAS-Project](https://github.com/TamarNoselidze/DALAS-Project)
- **Technical Report**: [Download Full Project Report (PDF, 2.6 MB)]({{ '/assets/pdf/dalas_final_report.pdf' | relative_url }})

---

### References

1. Noselidze, T., & Sharafdin, A. R. (2026). *Climate and Respiratory Health Analysis: A Multi-Decadal Global Study (1980-2023)*. Technical Project Report, Sorbonne Université.
2. Hersbach, H., et al. (2020). *The ERA5 global reanalysis*. Quarterly Journal of the Royal Meteorological Society, 146(730), 1999-2049.
3. Inness, A., et al. (2019). *The CAMS reanalysis of atmospheric composition*. Atmospheric Chemistry and Physics, 19(6), 3515-3556.
