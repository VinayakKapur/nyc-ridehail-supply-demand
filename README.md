# NYC Ride-Hailing Supply-Demand Prediction

A machine learning project that predicts taxi and ride-hailing vehicle supply per geohash cell in Lower Manhattan using NYC TLC trip record data. The model helps identify under-served zones and time windows where supply consistently falls short of demand.

**[Live interactive maps →](https://vinayakkapur.github.io/nyc-ridehail-supply-demand/)**

## What It Does

- Buckets Manhattan trip data into geohash precision-6 cells (~610m × 610m)
- Engineers time-series features: hour of day, day of week, weather conditions, historical rolling averages
- Trains a regression model to predict per-cell supply for the next time window
- Visualizes predictions and actual supply as interactive folium maps

## Key Results

Prediction plots are in [Predictions/](Predictions/). Interactive maps are hosted on GitHub Pages above.

## Tech Stack

- Python 3, Pandas, NumPy
- scikit-learn (regression model)
- geohash2 (spatial bucketing)
- folium (interactive map visualizations)
- matplotlib (static plots)

## Data Source

Raw trip data: **[NYC TLC Trip Record Data](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)** (public dataset, multiple GB — not included in this repo).

The `weather.csv` and aggregated `combined_per_minute_supply.csv` are included for reference.

## Running the Notebooks

Run notebooks in this order:

```
1. Data_code/RawData_final.ipynb        — load and clean TLC trip records
2. Data_code/Encoding_final.ipynb       — encode geohash cells and time features
3. Data_code/freesupply_final.ipynb     — compute free supply metric per cell
4. Data_code/LowerManhattanFull.ipynb   — filter to Lower Manhattan bounding box
5. Data_code/Model_Testing_final.ipynb  — train and evaluate the model
6. Data_code/modelevaluation_lowermanhattan-2.ipynb — detailed evaluation
7. Data_code/heatmap_and_geohashmap.ipynb — generate interactive map outputs
```

```bash
pip install pandas scikit-learn geohash2 folium matplotlib jupyter
jupyter notebook
```

## Docs

- [Final Presentation](docs/FinalPresentationV2.pdf)
- [Executive Summary](docs/Executive_Summary.pdf)
- [Live Maps](https://vinayakkapur.github.io/nyc-ridehail-supply-demand/)

## Context

Built as a professional data science project analyzing NYC mobility patterns. The large raw data files (~6.5 GB of geohash-bucketed CSVs) are not included. Download source data from NYC TLC and run the notebooks in order to reproduce.
