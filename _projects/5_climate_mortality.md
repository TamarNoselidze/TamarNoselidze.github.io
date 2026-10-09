---
layout: page
title: "Global Drivers of Respiratory Mortality"
description: Multi-decadal machine learning analysis (1980–2023) across 180+ countries evaluating meteorological stress and satellite pollution data with spatial leakage control.
img: assets/img/climate.webp
importance: 5
category: Machine Learning & AI
related_publications: false
---

### Overview

Understanding whether environmental conditions determine population-scale respiratory mortality requires disentangling global weather patterns, atmospheric pollution, and baseline demographics. Conducted as part of the *Data Analysis at Large Scale (DALAS)* curriculum at **Sorbonne Université** (January 2026), this project quantifies the multi-decadal relationships between meteorological stress, satellite-derived air quality, and respiratory mortality across **180+ countries over 43 years (1980–2023)**.

- **Institution**: Sorbonne Université (Paris, France)
- **Collaborators**: Tamar Noselidze, Abdel Razak Sharafdin
- **Data Scope**: 43 years (1980–2023), 180+ countries, monthly and seasonal aggregations
- **Data Sources**: ERA5 Reanalysis (ECMWF climate), CAMS Reanalysis (Copernicus atmospheric pollutants), and IHME Global Burden of Disease (GBD 2021)

---

### Methodological Innovation: Controlling Spatial Leakage

Standard random 80/20 train–test splits fail drastically in spatial epidemiology because models "memorise" geographical entities (e.g. learning that a specific developed country has low mortality baselines), generating artificially inflated metrics ($R^2 > 0.90$).

<div class="row justify-content-sm-center my-4">
  <div class="col-sm-10 text-center">
    <a href="{{ '/assets/img/dalas_spatial_leakage.png' | relative_url }}" target="_blank" rel="noopener noreferrer">
      <img src="{{ '/assets/img/dalas_spatial_leakage.png' | relative_url }}" class="img-fluid rounded z-depth-1" alt="Impact of Spatial Leakage Control on Model Accuracy" style="width: 100%; border: 1px solid var(--global-divider-color);">
    </a>
    <div class="caption text-muted mt-2" style="font-size: 0.85rem;">
      Comparison between standard random train-test splits (showing inflated \(R^2 > 0.90\) due to spatial leakage) versus rigorous Stratified Group K-Fold cross-validation (\(R^2 \approx 0.30 - 0.44\)).
    </div>
  </div>
</div>

To overcome this, we implemented **Stratified Group K-Fold Cross-Validation with Temporal Control**:
- **Strict Spatial Holdout**: Entire countries are held out of the training folds, forcing the Random Forest models to learn universal physical associations rather than geographical proxies.
- **Climate Stratification**: Folds are balanced across climate clusters (Tropical, Arid, Temperate) to prevent covariate shift when evaluating unseen nations.
- **Secular Trend Controls**: Time controls isolate environmental signals from general decade-over-decade healthcare improvements.

---

### Key Findings & The "Ozone-Cold Nexus"

<div class="row justify-content-sm-center my-4">
  <div class="col-sm-10 text-center">
    <a href="{{ '/assets/img/dalas_feature_importance.png' | relative_url }}" target="_blank" rel="noopener noreferrer">
      <img src="{{ '/assets/img/dalas_feature_importance.png' | relative_url }}" class="img-fluid rounded z-depth-1" alt="Top Predictors for Lower Respiratory Infections" style="width: 100%; border: 1px solid var(--global-divider-color);">
    </a>
    <div class="caption text-muted mt-2" style="font-size: 0.85rem;">
      Top 10 feature importances for Lower Respiratory Infection (LRI) mortality, highlighting the dominance of Tropospheric Ozone (\(O_3\)) and Winter Temperature.
    </div>
  </div>
</div>

#### 1. Tropospheric Ozone (\(O_3\)) vs. \(PM_{2.5}\)
Across modern multi-pollutant evaluations, **Tropospheric Ozone (\(O_3\))** consistently emerged as a stronger global predictor of acute respiratory mortality than fine particulate matter (\(PM_{2.5}\)). Partial dependence analysis revealed a sharp non-linear threshold where oxidative stress overwhelms respiratory mucosal defences.

#### 2. Disease-Specific Driver Profiles
- **Lower Respiratory Infections (LRI, \(R^2 \approx 0.44\))**: Primarily driven by cold stress (winter minimum temperatures). Cold air suppresses airway ciliary clearance, which, coupled with oxidative ozone damage, creates a biological "double-hit" vulnerability to viral infections.
- **Asthma (\(R^2 \approx 0.39\))**: Strongly pollution-driven. Adding CAMS satellite air quality data more than doubled predictive accuracy (**+120% gain**, \(\Delta R^2: 0.176 \to 0.387\)), with significant gender divergence in susceptibility.
- **COPD as a Negative Control (\(R^2 < 0.15\))**: Environmental predictors explained minimal variance in Chronic Obstructive Pulmonary Disease, as COPD mortality is heavily dominated by lifelong tobacco smoking and occupational hazards. This negative result confirmed that the pipeline was not fitting spurious macro-level correlations.

---

### Dual-Track Pipeline & Feature Engineering

To handle the temporal discrepancy between historical climate records (ERA5, from 1980) and satellite chemical reanalysis (CAMS, from 2003) without discarding 23 years of meteorological data, we engineered two parallel pipelines:
- **Seasonal Stress Indices**: Extracted targeted physiological proxies including the *Winter Severity Index*, *Summer Heat Stress Index*, and dewpoint depression (\(\Delta T_{\text{dew}} = T_{\text{air}} - T_{\text{dewpoint}}\)) as an indicator of airway-irritating dry air.
- **Dual-Track PCA**: Reduced 60+ collinear atmospheric variables into orthogonal meteorological modes (Radiative-Thermal, Hydrological, Aerodynamic) and chemical pollution modes.

---

### Code & Resources

- **GitHub Repository**: [TamarNoselidze/DALAS-Project](https://github.com/TamarNoselidze/DALAS-Project)
- **Technical Report**: [Download Full Project Report (PDF, 2.6 MB)]({{ '/assets/pdf/dalas_final_report.pdf' | relative_url }})

---

### References

1. Noselidze, T., & Sharafdin, A. R. (2026). *Climate and Respiratory Health Analysis: A Multi-Decadal Global Study (1980–2023)*. Technical Project Report, Sorbonne Université.
2. Hersbach, H., et al. (2020). *The ERA5 global reanalysis*. Quarterly Journal of the Royal Meteorological Society, 146(730), 1999-2049.
3. Inness, A., et al. (2019). *The CAMS reanalysis of atmospheric composition*. Atmospheric Chemistry and Physics, 19(6), 3515-3556.
