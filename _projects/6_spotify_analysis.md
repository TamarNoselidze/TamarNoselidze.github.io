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

This project investigates multi-decadal musical trends and audio features across more than **128,000 unique tracks** spanning from the early 20th century to modern streaming releases (1920s–2024). Leveraging the **Spotify Web API (`spotipy`)**, the study conducts large-scale exploratory data analysis and trains predictive machine learning models to forecast track popularity.

- **Stack**: Python, Pandas, NumPy, Scikit-Learn, Spotipy (Spotify Web API), Seaborn, Matplotlib
- **GitHub Repository**: [TamarNoselidze/Spotify-Data-Analysis](https://github.com/TamarNoselidze/Spotify-Data-Analysis)

---

### Key Historical & Audio Trends

Analysis of tracks aggregated across decades revealed clear cultural and acoustic shifts in mainstream music:

- **Decline in Acousticness & Instrumentalness**: Long-term time-series tracking shows a sharp decrease in acoustic and purely instrumental tracks, capturing the evolution towards electronic synthesised instrumentation and vocal-centric arrangements.
- **Rise of Loudness, Energy, and Danceability**: Energy and loudness display a strong positive correlation (\(r = 0.78\)), with both attributes trending upwards in recent decades alongside danceability (\(r = -0.75\) with acousticness).
- **Surge in Explicit Content**: Explicit track percentages grew dramatically from the 1950s through the 2020s, reflecting broader cultural shifts and artistic freedom in recorded music.
- **Musical Mode**: Major mode songs consistently dominate the catalogue across all periods, though minor keys have experienced a slight increase in recent years.
- **Catalogue Depth**: While contemporary streaming hits dominate average popularity, legacy and classical artists (such as J.S. Bach, Frank Sinatra, and Bob Dylan) lead total track volume, demonstrating the vast archival breadth of the platform.

---

### Popularity Predictive Modelling

To determine whether acoustic features and metadata alone can predict listener engagement, we engineered a supervised machine learning pipeline:

- **Feature Engineering**: Filtered numerical attributes showing significant correlation with popularity (\(\lvert r \rvert > 0.1\)), including acousticness, energy, loudness, danceability, instrumentalness, explicit flag, artist count, and release year.
- **Model Architecture**: Trained a **Random Forest Regressor** (100 estimators) on 102,000+ training tracks using 5-fold cross-validation.
- **Performance**:
  - Cross-validation Root Mean Squared Error (RMSE): \(\approx 0.096\)
  - Validation \(R^2\) Score: **\(0.732\)** (RMSE: \(0.095\))
- **Out-of-Sample Evaluation**: Tested on newly harvested tracks (`new_data.csv`), confirming that high predicted popularity scores successfully capture genuine streaming hit candidates.

---

### Code & Resources

- **GitHub Repository**: [TamarNoselidze/Spotify-Data-Analysis](https://github.com/TamarNoselidze/Spotify-Data-Analysis)
- **Jupyter Notebook**: [Spotify_Analysis.ipynb](https://github.com/TamarNoselidze/Spotify-Data-Analysis/blob/main/Spotify_Analysis.ipynb)
