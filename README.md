# Interpolation Methods for Cu% (IDW, SK, OK)

## Overview
This project compares deterministic and geostatistical interpolation methods for a Copper (Cu%) dataset. Methods implemented include:
- **Inverse Distance Weighting (IDW)**  
- **Simple Kriging (SK)**  
- **Ordinary Kriging (OK)**  

The workflow covers data preprocessing, declustering, normal score transformation, variogram modeling, interpolation on a regular grid, and model validation using 5-fold cross-validation.

## Tools & Libraries
- Python
- Pandas, NumPy
- Matplotlib, Seaborn
- Scikit-learn
- PyKrige (Ordinary Kriging)
- GSTools (Simple Kriging)
- scikit-gstat (Variogram analysis)
- GeoPandas / Shapely (optional for spatial outputs)
- SciPy

## Project Workflow

### 1. Data Loading & Preprocessing
- Loaded Cu% dataset (`CuMineBH.csv`) and standardized column names.
- Filtered for relevant columns (Easting, Northing, Cu%) and removed missing values.
- Visualized Cu% distribution via scatter plots.

### 2. Declustering
- Computed nearest-neighbor distances and suggested cell size for declustering.
- Applied weights to correct spatial sampling bias.
- Compared naive vs declustered Cu% statistics.

### 3. Normal Score Transformation (NST)
- Transformed Cu% to normal scores to stabilize variance for kriging.
- Generated forward/backward interpolation functions for back-transformation.
- Verified transformation using QQ plots.

### 4. Variogram Modeling
- Calculated experimental variogram for normal scores.
- Fitted spherical, exponential, and gaussian models; selected **spherical** as best fit.
- Converted fitted model for use in GSTools and kriging methods.

### 5. Interpolation Grid & Search Strategy
- Created a regular grid (10 m spacing) covering data extent.
- Defined search neighborhood: radius = 1.25 × variogram range, min 3 and max 16 neighbors.

### 6. Interpolation Methods
- **IDW**: Tested powers p = 1–5; p = 2 selected as best balance.
- **Simple Kriging (SK)**: Applied on normal scores, back-transformed to Cu%.
- **Ordinary Kriging (OK)**: Used local mean estimation, implemented via PyKrige.

### 7. Validation & Comparative Analysis
- Conducted 5-fold cross-validation for IDW, SK, and OK.
- Metrics computed: RMSE, MAE, R².
- **Findings:** OK performed marginally better than SK and IDW.

### 8. Results & Insights
- IDW: Smooth at low powers, localized "bullseye" at high powers.
- SK: Smooth maps, constrained to global mean; higher variance in sparse regions.
- OK: Locally adaptive estimates; realistic variations; variance reflects sample density.
- Conclusion: **Ordinary Kriging is the most reliable for this dataset**.

### 9. Challenges & Future Improvements
- Current model assumes isotropy; directional continuity not considered.
- Improvements:
  - Incorporate anisotropy in variogram modeling.
  - Use larger datasets for better training and validation.
  - Apply advanced kriging variants (e.g., universal kriging).

## Usage
1. Install dependencies:
```bash
pip install pykrige gstools scikit-gstat geopandas matplotlib seaborn pandas numpy scikit-learn
