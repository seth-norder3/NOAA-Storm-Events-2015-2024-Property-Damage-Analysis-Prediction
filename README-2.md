# NOAA Storm Events (2015–2024): Property Damage Analysis & Prediction

Analysis of ~639,000 severe weather records from the NOAA/NCEI Storm Events Database: event frequency, property damage, injuries, and deaths by event type, state, month, and season, plus geospatial hotspot maps and a Random Forest model predicting property damage.

## Contents
- `storm_events_analysis.ipynb` — full analysis (data loading, EDA, geospatial, temporal, modeling)
- `requirements.txt` — Python dependencies

## Running it
```
pip install -r requirements.txt
jupyter notebook storm_events_analysis.ipynb
```
The notebook downloads the yearly CSVs directly from NOAA, so it needs an internet connection. The URLs include NOAA's revision date (e.g. `c20260323`); NOAA replaces these files periodically, so if a download 404s, update the filename from https://www.ncei.noaa.gov/pub/data/swdi/stormevents/csvfiles/. Running the geospatial cells writes two standalone interactive maps (`storm_event_hotspots.html`, `property_damage_hotspots.html`).

## Results (summary)
- Thunderstorm wind and hail dominate event counts, but tornadoes account for disproportionate damage, injuries, and deaths.
- Random Forest beat linear regression in 5-fold CV (log-scale MAE 1.88 vs. 2.94). Held-out test R² is only 0.067: event type, state, season, injuries, and deaths carry limited signal without storm magnitude/severity fields.

## Known data caveat
2024 property damage values are largely unpopulated in the NOAA release used, so 2024 is excluded from the yearly damage plot. See the Limitations section of the notebook.
