# Skyscrapers Explorer

An interactive [Streamlit](https://streamlit.io/) dashboard for exploring a dataset of more than 2,400 skyscrapers from around the world. Filter by year, height, and city, then explore the results through summary statistics, charts, and an interactive 3D map.

## Features

- **Interactive filters** — narrow the dataset by year of completion, height range, and one or more cities.
- **3D map** — visualize skyscraper heights on an interactive `pydeck` map with a dark Mapbox style.
- **Summary statistics** — view the tallest, shortest, average, and median heights for the current selection.
- **Top cities chart** — bar chart of the ten cities with the most skyscrapers in the filtered set.
- **Construction trend** — line chart showing the number of skyscrapers completed each year.
- **Data export** — download the currently filtered dataset as CSV.
- **Custom theme** — dark UI styled via `.streamlit/config.toml` and inline CSS.

## Project Structure

```text
.
├── .devcontainer/
│   └── devcontainer.json     # Dev Container configuration
├── .streamlit/
│   └── config.toml           # Streamlit theme configuration
├── main.py                   # Streamlit application entry point
├── requirements.txt          # Python dependencies
├── skyscrapers.csv           # Source dataset
└── README.md
```

## Requirements

- Python 3.9 or newer
- The packages listed in `requirements.txt`:
  - `pandas`
  - `streamlit`
  - `numpy`
  - `matplotlib`
  - `pydeck`

## Getting Started

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd skyscrapers
```

### 2. Create a virtual environment (recommended)

```bash
python -m venv .venv
source .venv/bin/activate          # macOS / Linux
.venv\Scripts\activate             # Windows
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the app

```bash
streamlit run main.py
```

Streamlit will start a local server and open the dashboard in your browser (typically at `http://localhost:8501`).

## Using the Dashboard

The sidebar exposes three filters that drive every tab:

| Filter | Description |
| --- | --- |
| **Year Built Range** | Restricts skyscrapers by their completion year. |
| **Height Range (m)** | Restricts skyscrapers by structural height. |
| **Select Cities** | Optionally narrows the data to one or more cities. Leave empty to include every city. |

The main view is split into six tabs:

1. **Filtered Data** — table view of the active selection.
2. **3D Map** — pick a city to fly to and inspect skyscrapers as 3D columns.
3. **Statistics** — quick summary of heights and counts for the selection.
4. **Top Cities** — bar chart of the top 10 cities by skyscraper count.
5. **Trend Over Time** — yearly construction trend across the selection.
6. **Download Data** — export the currently filtered rows as CSV.

## Dataset

`skyscrapers.csv` contains roughly 2,400 records with fields such as material, location (city, country, latitude, longitude), structural statistics (floors, height, rank), and status information (completed/started flags and years). Some records contain placeholder zero values for unknown completion years, which the app converts to `NaN` during data preparation.

## Development

The repository ships with a `.devcontainer` configuration so the project can be opened directly in a [VS Code Dev Container](https://code.visualstudio.com/docs/devcontainers/containers) or [GitHub Codespaces](https://github.com/features/codespaces) with all dependencies pre-installed.

To deploy a hosted version, [Streamlit Community Cloud](https://streamlit.io/cloud) can run this app directly from a GitHub repository — point it at `main.py` and it will install the dependencies from `requirements.txt`.

## License

MIT
