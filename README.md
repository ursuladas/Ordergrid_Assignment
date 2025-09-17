# Ordergrid_Assignment
This assignment focuses on generating 30-day daily demand forecasts for a set of 10 SKUs.

Models Implemented

1. XGBoost – for SKUs with low zero share.

2. Zero-Inflated Poisson (ZIP) – for SKUs with high zero share and sufficient history.

3. Croston’s Method – for intermittent demand with limited history.

4. Ensemble (XGBoost + LightGBM) – for SKUs with moderate zero share.
