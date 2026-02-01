# MLB Team Wins Forecast Model

A machine learning model that predicts next-season MLB team win totals using historical team and player statistics from the MLB Stats API.

## Overview

This R-based forecasting system combines team-level performance metrics with aggregated player statistics to generate win predictions using XGBoost regression. The model incorporates rolling averages and lagged features to capture team trajectory and momentum.

## Features

- **Live Data Integration**: Fetches real-time data from the official MLB Stats API including rosters, standings, and individual player statistics
- **Multi-Year Analysis**: Processes historical data from 2019-2024 to identify predictive patterns
- **Comprehensive Feature Engineering**: Combines 19 features including batting stats (R, HR, RBI, OPS), pitching metrics (ERA, SO, WHIP, IP), player-level aggregations (OBP, SLG, WAR, BA), and 3-year rolling averages
- **XGBoost Model**: Tuned gradient boosting with regularization for robust predictions
- **Caching System**: Efficient roster caching to minimize redundant API calls

## Technical Details

**Dependencies**: httr, jsonlite, dplyr, tidyr, xgboost, caret, ggplot2, zoo, purrr, stringr

**Data Sources**: MLB Stats API (`statsapi.mlb.com/api/v1`)

**Output**: Team-by-team win predictions with year-over-year change projections

## Usage

```r
source("mlb_forecast.R")
main()
```

## Model Architecture

The pipeline follows four stages:
1. **Data Collection** — API calls for standings, team stats, and player stats
2. **Feature Preparation** — Aggregation, rolling windows, and lag variables
3. **Training** — XGBoost with preprocessing (centering/scaling)
4. **Forecasting** — Predictions for the upcoming season based on most recent data
