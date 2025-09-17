# Ordergrid_Assignment
This assignment focuses on generating 30-day daily demand forecasts for a set of 10 SKUs.

## Exploratory Data Analysis:
1. Daily Series Plots
2. Time Series Decomposition
3. Zero Share Analysis
4. Distribution Patterns
5. Yearly Seasonality

## Preprocessing
1. Outlier removal - Winsorization using percentile / IQR
2. Fill NaN Values with 0

## Feature Engineering
1. Calendar Features - Day of Week, Day of Year, Month of Year, Cyclical encoding of the same, Summer Indicator
2. Lag Features, Lag Differences, Lag Ratios
3. Level Shifts, Trends, Momentum
4. Rolling Statistics
5. Label Encoding of categorical variable GROUP

## Splitting Strategy
1. Time-based splitting with variations depending on zero share

## Models Implemented
1. XGBoost – for SKUs with low zero share.

2. Zero-Inflated Poisson (ZIP) – for SKUs with high zero share and sufficient history.

3. Croston’s Method – for intermittent demand with limited history.

4. Ensemble (XGBoost + LightGBM) – for SKUs with moderate zero share.

## Evaluation Metrics
  1. MAE
  2. MSE
  3. RMSE
  4. R^2
  5. MAPE

## Prediction Intervals
1. For XGBoost and Ensemble Models - Prediction intervals are computed using residuals from historical forecasts: the standard deviation of the residuals is multiplied by the z-score for the desired confidence level and added/subtracted from the point forecast, giving a data-driven uncertainty range around predictions.
2. For Zero Inflated Model - Prediction intervals are calculated using the Poisson distribution, where the model predicts the mean count for each forecast date, and the lower and upper bounds are obtained from the Poisson percent-point function (PPF) for the desired confidence levels, ensuring non-negative values.
3. For the Croston model - Intervals are derived from an approximation using the forecasted values and a smoothing parameter, with standard normal z-scores applied to compute lower and upper bounds, and negative values are clipped to zero.
