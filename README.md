# Authors:
Zubair Abdullah-Vetter,

This is a copy of relevant codes to run the grid-based cell segmentation of EL module images

# Environment install instructions
- Python version 3.10.11
- Use pipenv to create a venv with the packages in the pipfile

# Installing additional packages
- Navigate to project folder
- pipenv shell to activate the venv
- replace "pip install" with "pipenv install" 
- necessary example = pytorch: use the webpage commands but replace "pip3 install" with "pipenv install"

# Examples
- one module is 6 by 10 cells
- one module is 6 by 12 cells

# Summary
This is a grid-based cell segmentation pipeline for analyzing electroluminescence (EL) images of solar photovoltaic modules. Here's what it does:

## Main Purpose:
Automatically detects and extracts individual solar cells from EL/IR images of Sandia modules (6×12 grid layout)
Segments cells, optionally processes both high-bias and low-bias variants, and saves extracted cells as separate images

## Key Components:

Setup & Utility Functions (lines 1-100)

Matplotlib styling configuration for publication-quality plots
Pickle utilities and image visualization helpers

## Core Segmentation Functions:

adjust_cluster_centres() - Iteratively refines grid line detection by fixing spacing anomalies

grid_mask_from_median_peak() - Creates a grid mask using edge detection and clustering on gradient aggregates

mask_modules() - Complete pipeline combining trimming, gradient computation, and filtering

clean_mask() - Removes edge artifacts and ensures correct cell count

## Cell Extraction & Filtering:

extract_cells() - Extracts individual cell cropsfrom the segmented mask

median_pxl_filter() & aspect_ratio_filter() - Remove outlier cells based on size/shape

cells_pad() - Pads extracted cells to uniform dimensions

## Main Execution:

run_cell_segmentation() - Coordinates the full pipeline, saves cells as individual TIFF/PNG images

Test section processes a single image with configurable parameters (grid dimensions, smoothing, thresholds, etc.)

Output: Individual cell images organized in folders, plus visualization plots of the segmentation results.