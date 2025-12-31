# NYC Taxi & Weather Data (January–June 2024)

Analyze how hourly weather conditions affect New York City Yellow Taxi trips for the first half of 2024. The repository includes simple download scripts and notebooks for cleaning, merging, and exploring the data.

## Data Sources

- **Taxi trips:** NYC TLC Yellow Taxi Parquet files (one per month) from the [TLC trip record data distribution](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page).
- **Weather:** Hourly observations from the NOAA Global Hourly dataset for LaGuardia Airport (station `06806599999`).

Downloaded files are stored in a local `data/` directory that is ignored by Git.

## Repository Layout

- `download_taxi_data.py` — Downloads January–June 2024 Yellow Taxi Parquet files.
- `download_weather_data.py` — Downloads the LaGuardia hourly weather CSV for 2024.
- `Clean_weather_hourly.ipynb` — Cleans and filters raw weather data to hourly observations.
- `Clean_yellow_trip_hourly.ipynb` — Prepares hourly taxi trip aggregates.
- `Final_merge.ipynb` — Combines cleaned taxi and weather data for analysis/visualization.
- `requirements.txt` — Minimal Python dependencies (pandas, pyarrow, notebook, urllib3).
- `data/` — Target directory for downloaded raw files (created automatically; contents are not versioned).

## Getting Started

### 1) Install dependencies

Python 3.10+ is recommended.

```bash
pip install -r requirements.txt
```

### 2) Download raw data

Run the download scripts from the repo root. They create the `data/` folder if it does not already exist.

```bash
python download_taxi_data.py      # 6 Parquet files, ~10–15 GB total
python download_weather_data.py   # 2024 LaGuardia hourly CSV
```

> Tip: Downloads can take several minutes depending on your connection.

### 3) Explore and process in notebooks

1. Launch Jupyter:
   ```bash
   jupyter notebook
   ```
2. Open the notebooks in order:
   - `Clean_weather_hourly.ipynb`
   - `Clean_yellow_trip_hourly.ipynb`
   - `Final_merge.ipynb`

Each notebook documents its own steps for cleaning, aggregation, and merging.

## Outputs

- Hourly aggregated taxi metrics (pickups, drop-offs, fares) paired with weather features (temperature, precipitation, etc.) for January–June 2024.
- Visual summaries of relationships between weather conditions and taxi demand are generated in `Final_merge.ipynb`.

## Notes & Troubleshooting

- Ensure you have sufficient disk space for the taxi Parquet files (~2 GB per month uncompressed).
- If a download fails, re-run the corresponding script; files are overwritten when re-downloaded.
- Network-restricted environments may require configuring proxies for `urllib`.
