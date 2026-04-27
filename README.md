# Main Causes of Traffic Accidents: Econometrics Project

## Overview
This project investigates how driver behavior, vehicle characteristics, and crash conditions relate to severe, high-cost traffic accidents. Using the **CRSS 2023 microdata**, the project models the probability of a `HIGH_COST` vehicle outcome (e.g., towed, rollover, fire, or severe deformation). The results provide actionable insights for leasing companies and insurers regarding residual value risk, underwriting rules, and risk-based product design.

## Authors
* **Iryna Svyrydenko**
* **Yurii Bobas**
* **Vladyslav Vasylchenko**

*Ukrainian Catholic University, Faculty of Applied Sciences (April 2026)*

## Dataset
* **Source:** NHTSA Crash Report Sampling System (CRSS) 2023.
* **Files Used:** `accident.csv`, `vehicle.csv`, `person.csv` and `weather.csv`.
* **Details:** The data is a nationally representative probability sample of police-reported crashes. Because the dataset uses unequal selection probabilities, the analysis applies survey weights (`WEIGHT`) to recover accurate, population-representative statistical patterns.

## Project Structure

The repository contains three Jupyter Notebooks for analysis and modeling, alongside the final written report:

1. **`data_analysis.ipynb`**
   * **Purpose:** Exploratory Data Analysis (EDA) and data wrangling. 
   * **Details:** Loads the CRSS data, applies helper functions for weighted sums and rates, and derives new fields such as time-of-day (`NIGHT`/`DAY`) and seasonality (`SEASON`). 

2. **`initial_model.ipynb`**
   * **Purpose:** First iteration of the Logit model.
   * **Details:** Predicts the binary `HIGH_COST` outcome using variables like continuous speed, weather, lighting, region, and driver covariates (age, sex, unbuckled, alcohol, and drugs). Fits a Generalized Linear Model (GLM) using `statsmodels` with survey weights and cluster-robust standard errors grouped by crash (`CASENUM`).

3. **`final_model.ipynb`**
   * **Purpose:** Refined Logit model optimized for interpretation.
   * **Details:** Drops the weather variable and converts continuous features into categorical bins (e.g., `SPEED_BIN`, `VEH_AGE_BIN`, `AGE_BIN`) to capture non-linear relationships. Outputs the McFadden Pseudo R² and computes odds ratios to identify the most significant crash severity factors.

4. **`final_report.pdf`**
   * **Purpose:** The comprehensive project report.
   * **Details:** Contains the motivation, literature review, methodology, and business conclusions tailored for leasing risk management. 

## Key Findings
Based on the modeling results, the highest predicted risk for a high-cost vehicle outcome is associated with:
* **Impairment & Behavior:** Alcohol and drug involvement, as well as seat belt non-use, dramatically increase high-cost probabilities.
* **Speed:** Upper-speed bins exhibit substantially higher risks relative to low-speed driving.
* **Environment:** Night-time driving and adverse operating environments (e.g., icy/slushy roads) are significant risk markers. 
* **Vehicle Age:** Older vehicles exhibit moderately higher probabilities of costly outcomes compared to newer vehicles.

## Requirements and Usage
To reproduce this analysis:
1. Colne out GitHub repository.
2. Ensure you have Python 3 installed with the following packages: `pandas`, `numpy`, `matplotlib`, and `statsmodels`.
3. Run the notebooks in the following order:
   * `data_analysis.ipynb`
   * `initial_model.ipynb`
   * `final_model.ipynb`
