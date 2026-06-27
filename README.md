# Big Data Analytics - Million Song Dataset ETL Pipeline

This repository contains a Databricks ETL pipeline for analyzing the Million Song Dataset.

## Repository Structure

```
BigDataAnalytics/
├── transformations/           # ETL pipeline transformations
│   └── my_transformation.py   # Main pipeline code
└── explorations/              # Analysis and exploration notebooks
    └── DataBrickExploration.sql  # SQL queries for data analysis
```

## Pipeline Components

### Transformations (`transformations/my_transformation.py`)

**1. songs_raw** (Streaming Table)
- Ingests raw song data from `/databricks-datasets/songs/data-001/`
- Uses Auto Loader for incremental processing
- Includes full schema definition for the Million Song Dataset

**2. songs_prepared** (Materialized View)
- Cleans and prepares data for analysis
- Includes data quality expectations:
  - Valid artist name (not null)
  - Valid song title (not null)
  - Valid duration (> 0)
- Selects key columns for downstream analysis

**3. top_artists_by_year** (Materialized View)
- Aggregates song counts by artist and year
- Sorted by total number of songs and year

### Explorations (`explorations/DataBrickExploration.sql`)

Contains SQL queries for analyzing the processed data:
- Top artists by year (1990+)
- Songs with 4/4 beat and danceable tempo (100-140 BPM)

## Setup

1. Import this repository as a Databricks Git folder
2. Configure the pipeline to use the `transformations/` directory
3. Set catalog and schema in pipeline settings
4. Run the pipeline to create and populate tables

## Data Source

The pipeline uses the Million Song Dataset, a collection of features and metadata for contemporary music tracks, available in Databricks sample datasets.
