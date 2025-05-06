# Green space and violence: 
# Using machine learning and deep learning to assess the relationship between local NDVI values and firearm assaults in Philadelphia
-----------------------------------------------------------------
## Project Overview

This project investigates the spatial relationship between urban greenness and firearm assaults in Philadelphia using artificial intelligence (AI) techniques. Firearm violence is a leading cause of injury and death in the city, and understanding environmental correlates like green space can inform urban planning and violence prevention strategies. By leveraging high-resolution NAIP satellite imagery and point-level incident data, we apply both traditional machine learning and deep learning models to predict firearm assault locations based on NDVI greenness values.

## Data Sources

- **Firearm Assault Data:** Geocoded point locations of fatal and nonfatal shootings in Philadelphia. Data includes spatial coordinates and incident classification. (Source: Philadelphia Police Department via OpenDataPhilly and Nick Hand's [Mapping Philadelphia's Gun Violence](https://www.nickhand.dev/philly-gun-violence-map/) project.)

- **NAIP Imagery:** 4-band aerial imagery (RGB + Near-Infrared) obtained from the National Agriculture Imagery Program. Used to compute NDVI at high spatial resolution. Must be downloaded from 

- **Control Points:** Randomly sampled background locations across the city, used for model training and comparison.

## Methods

- **NDVI Calculation:** NDVI derived from 4-band NAIP imagery.
- **Data Sampling:** Positive class: firearm assault points; Negative class: background/control points.
- **Modeling Approaches:**
  - **Random Forest** (scikit-learn)
  - **XGBoost** (XGBoost Python API)
  - **CNN** (PyTorch; trained on raster patches centered on each location)
- **Evaluation Metrics:**
  - Area under Precision-Recall Curve (AP)
  - Precision, recall, and AUC metrics
  - Spatial prediction map visualizations

## Results

- **Performance:** CNN achieved the highest average precision and showed improved ability to detect spatial structure in the NDVI raster.
- **PR Curves:** Precision-recall curves showed superior class separation by CNN.
- **Maps:** CNN prediction maps revealed spatial clustering of high-risk zones, consistent with known violence hotspots.

## Limitations

- No adjustment for socioeconomic or demographic covariates (e.g., income, policing, built environment).
- NDVI imagery represents a single time snapshot; does not capture seasonal or longitudinal changes.
- Model generalizability limited by sample size and computational constraints (MacBook M1, no GPU).

**Note:** CNN was trained on an M1 MacBook Pro using the Metal Performance Shaders (MPS) backend.

## Credits & Acknowledgments

- **Author:** Jamie Song, MPH, research and program coordinator @ Penn Trauma
- **Data Sources:**
  - Philadelphia shooting data (processed)
  - NAIP imagery from USDA
- **Libraries Used:** scikit-learn, xgboost, PyTorch, geopandas, rasterio, matplotlib

## License

This repository is part of a student project for academic purposes. Not licensed for commercial use.

