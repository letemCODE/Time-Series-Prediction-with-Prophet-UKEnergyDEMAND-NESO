# UK Power Forecasting with Prophet

## 1. Project Overview
This project forecasts UK electricity demand using historical data from 2014 to 2025.  
The model leverages **Facebook Prophet** for time series forecasting to predict **Total System Demand (TSD)** and provides insights into National Demand (ND), interconnector flows, and embedded renewable generation.  

Forecasts can help energy operators, policy makers, and analysts plan for peak demand periods, optimise energy distribution, and support strategic decision-making in the UK electricity system.

## 2. Data Source
Data is sourced from the **National Energy System Operator (NESO)** Historic Demand Data Portal:

- [NESO Historic Demand Data 2025](https://www.neso.energy/data-portal/historic-demand-data/historic_demand_data_2025)  
- All electricity-related columns are measured in megawatts (MW).

### Key Columns:
- **ND (National Demand):** Sum of metered generation, excluding station load, hydro pumping, and interconnector exports.  
- **TSD (Transmission System Demand):** ND plus additional generation required to meet station load, pumping, and interconnector exports.  
- **EMBEDDED_WIND_GENERATION / EMBEDDED_SOLAR_GENERATION:** Estimates of distribution-level generation reducing TSD.  
- **Interconnector Flows:** IFA_FLOW, IFA2_FLOW, BRITNED_FLOW, MOYLE_FLOW, EAST_WEST_FLOW, NEMO_FLOW, NSL_FLOW, ELECLINK_FLOW, VIKING_FLOW, GREENLINK_FLOW. Positive = import to GB, negative = export.  

**Relationship:**  
TSD ≈ ND + Station_Load + Pumped_Storage + Interconnector_Exports − Embedded_Generation  

## 3. Libraries Used
- **pandas, numpy:** Data manipulation and numerical operations  
- **matplotlib, seaborn:** Data visualisation  
- **prophet:** Time series forecasting  
- **holidays:** UK holiday dates for inclusion in Prophet model  
- **requests, urllib:** Data retrieval from URLs if needed  

## 4. Installation

To run this project locally, follow these steps:

1. Download the following files:
   - `UK_Power_Forecast_Prophet.ipynb`
   - `uk_power_data.csv`
2. Ensure you have **Jupyter Notebook** installed on your device.
3. Install the required Python libraries:
   ```bash
   pip install pandas numpy matplotlib seaborn prophet holidays```
4. Open the Notebook:

Launch Jupyter Notebook and open `Prophet_Project_UKEnergyDEMAND_NESO_CLEAN.ipynb`.

## 4. Files Included

### 1. `Prophet_Project_UKEnergyDEMAND_NESO_CLEAN.ipynb`
- Performs initial data exploration, cleaning, and preprocessing.  
- Builds the Prophet forecasting model and generates predictions.  
- Produces visualizations for historical data, forecasts, and model components.  
- Libraries used: pandas, numpy, matplotlib, seaborn, prophet, plotly.

### 2. `demanddata_2014_2025_combined.csv`
- Historical electricity demand and interconnector data for the UK (2014–2025). Key columns include:  
  - `SETTLEMENT_DATE` – Date of the observation  
  - `SETTLEMENT_PERIOD` – Half-hourly settlement period (1–48, with occasional 49–50 for daylight savings)  
  - `ND` – National Demand (total metered generation, excluding station load, pumped storage, and interconnector exports)  
  - `TSD` – Transmission System Demand (ND plus adjustments for station load, pumped storage, and interconnectors)  
  - `ENGLAND_WALES_DEMAND` – Demand specifically for England and Wales  
  - `EMBEDDED_WIND_GENERATION` – Estimated wind generation from distribution-connected wind farms  
  - `EMBEDDED_SOLAR_GENERATION` – Estimated solar generation from distribution-connected solar farms  
  - `PUMP_STORAGE_PUMPING` – Energy used for pumped storage  
  - `IFA_FLOW`, `BRITNED_FLOW`, `EAST_WEST_FLOW` – Key interconnector flows (imports/exports)

## 5. Data Sources

### Source 1: `demanddata_2014_2025_combined.csv`
- Contains historical electricity consumption data for the UK. Key columns include:  
  - `SETTLEMENT_DATE` – Date of the observation  
  - `SETTLEMENT_PERIOD` – Half-hourly settlement period (1–48, with occasional 49–50 for daylight savings)  
  - `ND` – National Demand (total metered generation, excluding station load, pumped storage, and interconnector exports)  
  - `TSD` – Transmission System Demand (ND plus adjustments for station load, pumped storage, and interconnectors)  
  - `ENGLAND_WALES_DEMAND` – Demand specifically for England and Wales  
  - `EMBEDDED_WIND_GENERATION` – Estimated wind generation from distribution-connected wind farms  
  - `EMBEDDED_SOLAR_GENERATION` – Estimated solar generation from distribution-connected solar farms  
  - `PUMP_STORAGE_PUMPING` – Energy used for pumped storage  
  - `IFA_FLOW`, `BRITNED_FLOW`, `EAST_WEST_FLOW` – Key interconnector flows (imports/exports) 

## 6. Libraries Used

This project uses the following Python libraries:

1. **pandas** – Data manipulation and cleaning  
2. **numpy** – Numerical computations and transformations  
3. **matplotlib** – Static visualizations of data and forecasts  
4. **seaborn** – Enhanced plotting and heatmaps  
5. **prophet** – Time series forecasting with trend and seasonality modeling  
6. **plotly** – Interactive visualizations for exploration of predictions

## 7. How to Use

### Running the Notebook

#### Data Preparation
- Open `Prophet_Project_UKEnergyDEMAND_NESO_CLEAN.ipynb`.  
- Load and inspect the `demanddata_2014_2025_combined.csv` dataset.  
- Handle missing values and ensure timestamps are properly formatted.

#### Building the Forecast Model
- Initialize and fit the Prophet model on historical data.  
- Include seasonalities, holidays, or additional regressors as needed.  
- Generate future predictions.

#### Visualizing Forecasts
- Plot forecasts with confidence intervals using Prophet's `plot` function.  
- Decompose forecasts into trend, weekly, and yearly seasonality components.  
- Optionally, use Plotly for interactive visualizations.

#### Evaluation
- Compute MAE and RMSE to assess model performance.  
- Compare predicted values to actual data for accuracy validation.

#### Conclusion
- Successfully forecasted TSD using Prophet from 2014–2025 data.
- Achieved low MAPE (~4%) on cross-validation.
- Forecast includes UK holidays and seasonal patterns.
- Visualisations highlight historical trends, seasonal cycles, and 1-year forward predictions.
- This project can be extended by:
- Including interconnector flows as regressors.
- Using ND or embedded generation features to improve forecast accuracy.
- Building interactive dashboards with Plotly for exploration.
