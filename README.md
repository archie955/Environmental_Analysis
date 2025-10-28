# Assessing Socioeconomic Influences on Air Quality Change in the UK (2007–2024)

This repository investigates how socioeconomic deprivation (IMD) has influenced long-term air quality outcomes across the UK at the MSOA level between 2007 and 2024.  
Using $PM_{2.5}$, $PM_{10}$, and $NO_{2}$ concentration data, we explore whether more deprived areas experienced slower improvements in air quality despite national policy interventions.

---

## Overview

- **Goal:** Model the relationship between socioeconomic deprivation (IMD) and air quality change from 2007–2024.  
- **Methods:** Data cleaning, exploratory analysis, and multiple linear regression modelling.  
- **Tools:** Python (`pandas`, `statsmodels`, `sqlalchemy`, `matplotlib`, `seaborn`), SQL (PostgreSQL), Power BI, Jupyter Notebooks.  
- **Outputs:** Annotated notebooks, regression summary (provided below), and an interactive Power BI dashboard.


---

## Data Sources

| Dataset | Description | Source |
|----------|--------------|---------|
| **Air Quality (PM₂.₅ & NO₂)** | Annual mean concentrations, modelled at 1x1 km  resolution | [UK-AIR (DEFRA)](https://uk-air.defra.gov.uk/data/pcm-data) |
| **Index of Multiple Deprivation (IMD 2007, 2019)** | Composite measure of area-level deprivation at the MSOA level | [GOV.UK IMD data](https://www.gov.uk/government/statistics/english-indices-of-deprivation-2007) |
| **Geographies (MSOA Boundaries)** | 2011 MSOA boundaries | [ONS Geoportal](https://statistics.ukdataservice.ac.uk/dataset/2011-census-geography-boundaries-middle-layer-super-output-areas-and-intermediate-zones/resource/50432737-a23a-4ec7-8258-ff962e1fdcca) |
    Contains National Statistics data © Crown copyright and database right [2025]
    Contains NRS data © Crown copyright and database right [2025]
    Contains OS data © Crown copyright [and database right] [2025]

All datasets are publicly available. See notebooks for preprocessing steps.

---

## 🧮 Methodology

1. **Data Cleaning:**  
   - Harmonised pollutant and IMD datasets at MSOA level.  
   - Removed missing or mismatched geographic entries.

2. **Exploratory Analysis:**  
   - Visualised spatial and temporal trends in PM₂.₅ and NO₂.  
   - Examined correlations between IMD and pollutant levels.

3. **Regression Modelling:**  
   - Model:  
     \[
     \text{Pollutant}_{2024} = \beta_0 + \beta_1 \text{Pollutant}_{2007} + \beta_2 \text{IMD}_{2007} + \varepsilon
     \]
   - Checked VIF for multicollinearity (all ≈ 1.0).  
   - Evaluated significance, confidence intervals, and adjusted \(R^2\).

4. **Diagnostics:**  
   - Residual analysis, outlier detection, and intercept interpretation.  

5. **Visualisation:**  
   - Interactive Power BI dashboard summarising spatial patterns and model results.

---

## 📈 Key Results

| Pollutant | Adjusted R² | IMD Coefficient | Significance | Interpretation |
|------------|--------------|-----------------|---------------|----------------|
| **PM₂.₅ (2024)** | 0.75 | +0.017 ± 0.0005 | p < 0.001 | More deprived areas tend to have slightly higher PM₂.₅ after controlling for 2007 levels. |
| **NO₂ (2024)** | 0.68 | +0.013 ± 0.0007 | p < 0.001 | Similar but weaker effect, suggesting socioeconomic disparities persist. |

> **Summary:** Historical pollution remains the dominant driver of 2024 air quality,  
> but deprivation explains a small yet significant share of variation, indicating unequal progress across communities.
