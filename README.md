# Efficiency Scoring Algorithm

This repository contains R Markdown notebooks for analyzing and modeling driver telematics data. The method can be generalized to other applications beyond driver efficiency scoring.

The goal of this project is to turn raw telematics data into meaningful, fair insights about driver behavior, producing a scoring method that is **agnostic to geography**, so drivers across different regions can be compared fairly.

## Project Components

### 1. Driver Location Clustering (`Driver Location Clustering.Rmd`)
**Purpose:** Identify geographic hotspots so drivers are compared against peers operating in similar areas.  

**Key Steps:**
- Load heartbeat/event data from MongoDB or local cache.
- Extract driver IDs, timestamps, and relevant attributes.
- Apply DBSCAN for spatial clustering.
- Overlay clusters on maps using shapefiles (`sf`, `tigris`).
- Visualize clusters and movement patterns with `ggplot2`.

### 2. Driver Performance (`Driver Performance.Rmd`)
**Purpose:** Derive feature weights for efficiency scoring using machine learning and SHAP, with MPG as a reference target (not for prediction).  

**Key Steps:**
- Load performance data (`dperf.csv`) or pull from MongoDB.
- Engineer features using `dplyr` and `data.table`.
- Train `xgboost` models.
- Determine feature importance and weights with SHAP (`vip`).
- Run statistical tests and bootstrapping to validate results.

## Setup Requirements

- **R** ≥ 4.0  
- **RStudio** recommended for working with `.Rmd` files  

**Required Packages:**

| Category              | Packages                                      |
|-----------------------|-----------------------------------------------|
| Core                  | `dplyr`, `data.table`, `jsonlite`, `lubridate` |
| Database              | `mongolite`                                   |
| Geospatial            | `sf`, `dbscan`, `geosphere`, `tigris`       |
| Modeling & Explanation| `xgboost`, `vip`                             |
| Visualization         | `ggplot2`                                     |

