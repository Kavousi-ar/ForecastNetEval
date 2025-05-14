Weather Forecast Model Evaluation Using Complex Network Analysis

This repository contains a collection of Python scripts developed for evaluating weather forecast models through complex network analysis. The workflow includes extracting relevant meteorological data, constructing correlation matrices, filtering by spatial distance, building networks, and quantitatively comparing forecast networks against reference data.

Repository Contents

Grib2Ex.py	Extracts temperature and total precipitation variables from GRIB2 files and converts them into compressed NetCDF files for efficient storage and processing. Supports parallel processing with Dask.

tsEx.py	Processes ERA5 NetCDF files to extract normalized temperature time series for each spatial grid point, saving individual time series files for network construction.

corrMat.py	Reads extracted time series files, normalizes the data, and computes the correlation matrix between all spatial points, saving the matrix for further analysis.

distCalc.py	Filters the correlation matrix by applying minimum and maximum geographic distance thresholds, zeroing correlations outside the specified spatial range to focus on 
relevant scales.

NetConst.py	Constructs a network graph from the filtered correlation matrix, assigns geographic coordinates as node attributes, relabels nodes with integer IDs, and saves the graph in GEXF and edge list formats. Also generates a histogram of correlation values.

fscore.py	Compares predicted forecast networks against reference ERA5 networks across multiple spatial distance ranges. Computes precision, recall, and F1-score metrics to quantify network similarity and saves the results as CSV files.

Getting Started
Prerequisites
Ensure the following Python packages are installed:

    xarray

    netCDF4

    numpy

    pandas

    networkx

    matplotlib

    scikit-learn

    dask (for parallel processing in Grib2Ex)

Usage Overview

    Data Extraction:
    Use Grib2Ex.py to convert raw GRIB2 files into NetCDF format with selected variables.

    Time Series Extraction:
    Run tsEx.py to extract and normalize temperature time series from ERA5 NetCDF files.

    Correlation Matrix Calculation:
    Use corrMat.py to compute the correlation matrix from the extracted time series.

    Distance Filtering:
    Apply distCalc.py to filter the correlation matrix based on spatial distance thresholds.

    Network Construction:
    Construct the network graph with NetConst.py and save it for visualization or analysis.

    Network Evaluation:
    Evaluate forecast networks against ERA5 reference using fscore.py to calculate precision, recall, and F1-score metrics.

Directory Structure
Organize your data directories to match the paths specified in each script or update the directory variables accordingly.

License
[MIT License]

Contact
For questions or contributions, please contact [AR.Kavousi] at [alireza.kvc@gmail.com].
