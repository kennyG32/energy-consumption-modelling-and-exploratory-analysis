# Energy Consumption Modelling and Exploratory Analysis

## Overview

This project analyses OLED TV energy-consumption data and explores how playback context affects power use. The work combines exploratory data analysis with predictive modelling to understand relationships between device type, video content, bitrate, luminance reduction, duration, and measured power.

The repository contains the original notebook-based analysis and a Python script export of the same workflow.

## Project Objectives

- Clean and inspect the energy-consumption dataset.
- Explore summary statistics and distributions for key variables.
- Compare energy behaviour across devices and video conditions.
- Flag unusual observations and possible outliers.
- Build baseline, explanatory, and predictive models for energy consumption.

## Repository Contents

- `energy_measurement.csv`: main dataset used throughout the analysis.
- `energy_consumption_analysis.ipynb`: original notebook containing the full exploratory analysis and modelling workflow.
- `energy_consumption_analysis.py`: Python script version of the notebook workflow.
- `.gitignore`: excludes temporary files and local-only artifacts from version control.

## Analysis Workflow

The project covers the following stages:

1. Data loading and cleaning
2. Duplicate and missing-value handling
3. Descriptive statistics for numeric measures
4. Univariate analysis of luminance reduction
5. Device and video-level comparisons
6. Outlier detection using IQR, z-score, and plausibility checks
7. Energy modelling using:
   - Mean baseline
   - Linear regression
   - Random forest regression
   - XGBoost regression when available

## Key Findings

- The modelling dataset contains 704 observations covering 4 devices, 4 video scenarios, 11 luminance-reduction levels, and 4 bitrate settings.
- The average recorded power consumption across the analysed dataset is 57.11 W.
- Outlier screening found no unusual patterns in luminance reduction or bitrate, while only 8 power observations were flagged as potential realistic extremes; 696 of 704 rows remained in the normal range.
- In the grouped holdout by video, Random Forest delivered the strongest predictive performance with RMSE = 0.008176 Wh and R2 = 0.951044.
- In the grouped holdout by device and video, the linear model with controls performed best with RMSE = 0.017782 Wh and R2 = 0.947683, showing that device and content context explain a large share of energy variation.

## Main Variables Used

The analysis primarily uses the following fields from the dataset:

- `device`
- `videoName`
- `luminanceReduction`
- `bitrate`
- `Power`

Additional derived fields such as playback duration, bitrate in Mbps, and energy in Wh are created during the modelling stage.

## Tools and Libraries

The project uses Python with the following libraries:

- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- xgboost (optional)
- openpyxl
- xlrd

## Running the Project

### Notebook

Open `energy_consumption_analysis.ipynb` in VS Code or Jupyter and run the cells in order.

### Python script

Run the script from the project folder:

```bash
python energy_consumption_analysis.py
```

## Notes

- Some sections of the workflow reference additional folders such as `objective-score`, `subjective-score`, and `test-sequence`. Those directories are expected only if you want to run the parts of the analysis that depend on them.
- The repository keeps the original project structure while improving naming and presentation for portfolio use.

## Author

Kehinde Ogundele