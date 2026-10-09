---
layout: page
title: "Spotify Data Analysis"
description: Exploratory data analysis and popularity predictive modelling on 128,000+ Spotify tracks across decades using Spotipy API and Scikit-Learn.
img: assets/img/spotify.webp
importance: 6
category: Machine Learning & AI
related_publications: false
---

### Overview

This project explores musical trends and audio attributes across **128,000+ tracks** from the 1920s to 2024. Using the **Spotify Web API (`spotipy`)**, the study conducts large-scale exploratory data analysis and trains machine learning models to forecast track popularity.

- **Stack**: Python, Pandas, NumPy, Scikit-Learn, Spotipy, Seaborn, Matplotlib
- **GitHub Repository**: [TamarNoselidze/Spotify-Data-Analysis](https://github.com/TamarNoselidze/Spotify-Data-Analysis)

---

### Key Historical & Audio Trends

- **Decline in Acousticness & Instrumentalness**: Time-series tracking shows a steady decline in acoustic and instrumental compositions, reflecting the transition towards electronic synthesised instrumentation and vocal-led arrangements.
- **Loudness, Energy, and Danceability**: Energy and loudness display strong positive correlation ($r = 0.78$), trending upwards in modern decades alongside danceability ($r = -0.75$ with acousticness).
- **Explicit Content**: Explicit track percentages expanded significantly from the 1950s through the 2020s.
- **Musical Mode**: Major mode songs consistently lead catalogue volume, with minor keys showing a slight rise in modern releases.

---

### Popularity Predictive Modelling

- **Feature Engineering**: Selected numerical attributes with meaningful correlation to popularity ($\lvert r \rvert > 0.1$), including energy, loudness, acousticness, danceability, explicit flag, artist count, and release year.
- **Model Architecture**: **Random Forest Regressor** trained on 102,000+ tracks using 5-fold cross-validation.
- **Performance**:
  - Cross-validation RMSE: 0.096
  - Validation $R^2$ Score: **0.732** (RMSE: 0.095)
- **Out-of-Sample Evaluation**: Evaluated on fresh streaming releases (`new_data.csv`), verifying strong alignment between predicted scores and actual listener reception.

---

### Code & Resources

- **GitHub Repository**: [TamarNoselidze/Spotify-Data-Analysis](https://github.com/TamarNoselidze/Spotify-Data-Analysis)
- **Jupyter Notebook**: [Spotify_Analysis.ipynb](https://github.com/TamarNoselidze/Spotify-Data-Analysis/blob/main/Spotify_Analysis.ipynb)
