Efficiency ScoringnAlgorithm

Algorithm for geographic clustering and feature weight determination for generating scoring rules.

This repository contains R Markdown notebooks for analyzing and modeling driver telematics data. The method can be easily generalized to other applications beyond drivers.

The purpose of this iteration was to build a scoring method for driver efficiency that is agnostic to geography, so drivers across different regions can be compared fairly.

The project has two main components:


Driver Location Clustering – partitioning drivers into comparable groups using geospatial event clustering.

Driver Performance – generating feature weights for efficiency scoring using machine learning and SHAP, followed by statistical validation.


The overall goal is to turn raw telematics data into meaningful, fair insights about driver behavior and efficiency.


Notebooks

Driver Location Clustering (Driver Location Clustering.Rmd)

Purpose: Identify geographic hotspots so drivers are only compared against peers who operate in similar areas.


Key steps:

Load heartbeat/event data from MongoDB or local cache.

Extract driver IDs, timestamps, and attributes.

Apply DBSCAN for spatial clustering.

Overlay clusters on maps using shapefiles (sf, tigris).

Visualize clusters and movement patterns with ggplot2.




Driver Performance (Driver Performance.Rmd)

Purpose: Derive feature weights for efficiency scoring, using MPG as a target only to surface feature importance (not to predict MPG).


Key steps:

Load performance data (dperf.csv) or pull from MongoDB.

Engineer features with dplyr / data.table.

Train xgboost models.

Use SHAP / feature importance (vip) to determine weights.

Run statistical tests and bootstrapping to validate results.



Setup
Requirements

R ≥ 4.0

RStudio recommended for working with .Rmd files

Packages

Core: dplyr, data.table, jsonlite, lubridate

Database: mongolite

Geospatial: sf, dbscan, geosphere, tigris

Modeling & explanation: xgboost, vip

Visualization: ggplot2
