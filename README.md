#Geospatial PCA & Clustering Analysis

##Overview

This project performs dimensionality reduction and geospatial clustering using multispectral remote-sensing data. The workflow applies PCA to compress spectral features, uses K-Means clustering for land-cover segmentation, computes NDVI & NDWI indices, and visualizes spatial structure across coordinates using georeferenced grid mapping.

##Tools & Libraries

Python

Pandas, NumPy

Matplotlib, Seaborn

Scikit-learn (PCA, KMeans, Silhouette Score)

Yellowbrick (Elbow method)

SciPy (linear assignment, contingency matrix)

Optional: GeoPandas for geospatial export

##Project Tasks
###1. Data Loading & Cleaning

Imported CSV pixel data with spectral bands and coordinates.

Converted fields to numeric and handled null/missing values.

###2. Vegetation & Water Index Computation

Computed NDVI from NIR and Red bands.

Computed NDWI from Green and NIR bands.

Produced 2D raster-style index maps.

###3. PCA Dimensionality Reduction

Reduced 7 spectral bands to 3 components.

Displayed scree plots and loadings.

Preserved most of the statistical variance.

###4. Clustering

Selected optimal k using Elbow & Silhouette.

Applied K-Means on:

Original spectral data

PCA-reduced data

Compared internal cluster cohesion.

###5. Spatial Visualization

Reshaped flattened pixels back into 2D spatial grids.

Generated maps for:

PC1–PC3

Original clustering

PCA-aligned clustering

PCA RGB composite

NDVI and NDWI overlays

###6. Statistical Interpretation

Analyzed cluster sizes and group consistency.

Used contingency metrics to align PCA clusters.

##Summary of Findings

PCA-based clustering produced more stable spatial grouping.

Original spectral clustering showed finer micro-scale distinctions.

NDVI & NDWI overlays supported water and vegetation interpretation.

##Challenges & Improvements

PCA may smooth out small-scale local anomalies.

Cluster selection depends partly on geoscientific context.

##Future enhancements:

Add terrain & soil layers

Experiment with DBSCAN / Gaussian Mixtures

Use time-series satellite data

##Conclusion

This project demonstrates a professional geospatial ML workflow integrating spectral analysis, PCA-based feature compression, and unsupervised clustering. It highlights technical skill in remote sensing analytics, geostatistical modelling, and geospatial engineering.
