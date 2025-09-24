# EfficiencyScoringAlgorithm
Algorithm for geographic clustering and feature weight determination for generating scoring rules 

This repository contains R Markdown notebooks for analyzing and modeling driver telematics data, but the idea can be easily abstracted to other subjects.
The purpose of this iteration was to create a scoring method for driver efficiency that was agnostic towards differences in geography to eliminate unfair comparisons amongst driver in the CONUS. 
It covers two main areas:

Driver Location Clustering – Creates clusters based on geospatial data of trips drivers take to partition scoring/ranking.

Driver Performance – Uses machine learning and SHAP to create feature weights for scoring and then applies statistical tests for sanity checks.

The goal is to make sense of raw telematics data and extract insights about driver behavior and performance

Notebooks
1. Driver Location Clustering (Driver Location Clustering.Rmd)

Purpose: Identify hotspots so that drivers can be compared amongst themselves.

Key steps:

Load heartbeat/event data from MongoDB or local cache.

Extract driver IDs, timestamps, and event attributes.

Apply geospatial clustering (DBSCAN) to group nearby events.

Map event clusters using shapefiles (sf, tigris) for context.

Visualize hotspots and movement patterns with ggplot2.



2. Driver Performance (Driver Performance.Rmd)

Purpose: Create feature weights for scoring by using xgboost and SHAP with MPG as a target variable. I tried maximizing R^2 as we are not interested in predicting MPG, but defining feature importance. 

Key steps:

Load performance data (dperf.csv) or pull directly from MongoDB.

Feature engineering with dplyr/data.table.

Train predictive models with xgboost.

Assess model performance and feature importance (vip)

Statistical testing and bootstrapping for verification



Setup
Requirements

R (≥ 4.0)

Recommended: RStudio for running .Rmd files

Packages used:
dplyr
xgboost
vip
data.table
mongolite
jsonlite
lubridate
sf
dbscan
geosphere
ggplot2
tigris
