# Operational Resilience Audit: Multi-Variable Risk Modeling & Logistics Efficiency Optimization

**Author:** Paul Kamande

A comprehensive R-based analytics pipeline for evaluating supply chain operational resilience through multi-variable risk modeling, predictive analytics, and logistics efficiency optimization.

## Project Overview

This project analyzes dynamic supply chain logistics data to identify vulnerabilities, predict delivery delays, and optimize operational efficiency. The analysis spans four key pillars:

- **Pillar A:** ETA variation prediction using traffic and weather conditions
- **Pillar B:** Inventory risk assessment and failure rate analysis
- **Pillar C:** Risk band calibration and performance metrics
- **Pillar D:** Geospatial hotspot identification for resource drainage

## Features

- **Automated data cleaning and feature engineering** with unit-aware transformations
- **Predictive modeling** for ETA variations using interaction effects
- **Geospatial clustering** (DBSCAN) to identify high-risk operational zones
- **Risk stratification** across multiple operational dimensions
- **Professional visualizations** using viridis color-blind friendly palettes
- **Comprehensive model diagnostics** and performance metrics

## Requirements

### R Version
- R 4.0.0 or higher recommended

### Required Packages

The script will automatically install missing packages. Dependencies include:

```r
tidyverse, lubridate, janitor, ggcorrplot, broom, yardstick,
rsample, splines, dbscan, here, glue, patchwork, readr,
viridisLite, scales
```

## Data Requirements

The script expects a CSV file named `dynamic_supply_chain_logistics_dataset.csv` located in a `data/` directory.

**Required columns:**
- `timestamp` - Date/time of observation
- `vehicle_gps_latitude`, `vehicle_gps_longitude` - GPS coordinates
- `fuel_consumption_rate` - Fuel efficiency (MPG)
- `eta_variation_hours` - Deviation from expected arrival time
- `traffic_congestion_level` - Traffic severity (1-10 scale)
- `weather_condition_severity` - Weather impact score
- `warehouse_inventory_level` - Current inventory levels
- `handling_equipment_availability` - Equipment availability score
- `shipping_costs` - Cost per shipment
- `lead_time_days` - Delivery lead time
- `driver_behavior_score` - Driver performance metric
- `fatigue_monitoring_score` - Fatigue assessment
- `disruption_likelihood_score` - Risk prediction score

## Project Structure

```
project-root/
├── data/
│   └── dynamic_supply_chain_logistics_dataset.csv
├── outputs/
│   ├── figures/          # All visualizations (PNG, 300 DPI)
│   └── tables/           # All analytical outputs (CSV)
├── README.md
└── operational_resilience_audit.R
```

## Usage

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/operational-resilience-audit.git
   cd operational-resilience-audit
   ```

2. **Place your data file** in the `data/` directory

3. **Run the analysis:**
   ```r
   source("operational_resilience_audit.R")
   ```

4. **View outputs** in the `outputs/` directory:
   - `/figures/` - Visualizations and diagnostic plots
   - `/tables/` - Summary statistics, model coefficients, and rankings

## Key Outputs

### Tables (`outputs/tables/`)
- `cleaned_logistics_data.csv` - Processed dataset with engineered features
- `model_eta_coefficients.csv` - Regression model parameters
- `model_eta_performance.csv` - RMSE, MAE, R² metrics
- `pillarB_inventory_failure_by_quartile.csv` - Inventory-failure analysis
- `pillarC_risk_band_summary.csv` - Risk stratification results
- `pillarD_drainage_hotspots_top10.csv` - High-cost operational zones
- `efficiency_ranking.csv` - Fuel-to-lead-time efficiency scores

### Figures (`outputs/figures/`)
- `histograms.png` - Distribution analysis of key metrics
- `correlation_matrix.png` - Variable relationship heatmap
- `predicted_vs_actual_eta.png` - Model validation plot
- `residual_diagnostics.png` - Regression diagnostic plots
- `reliability_boundary.png` - Traffic-weather risk contours
- `pillarB_failure_vs_inventory.png` - Inventory impact on failures
- `pillarC_eta_by_risk_band.png` - ETA by risk stratification
- `pillarD_top10_hotspots.png` - Geographic efficiency drains

## Methodology

### Feature Engineering
- **Planned Lead Time:** Adjusted for ETA variations (hours → days conversion)
- **Fuel-to-Cost Ratio:** Efficiency metric normalized by shipping costs
- **Fuel-to-Lead-Time Ratio:** Primary efficiency ranking metric
- **Inventory Risk Flag:** Binary classification based on median thresholds

### Modeling Approach
- **Linear regression** with interaction terms (traffic × weather)
- **Time-aware train/test split** (80/20) preserving temporal ordering
- **Logistic regression** for binary failure prediction
- **DBSCAN clustering** (eps=0.01, minPts=10) for geospatial analysis

### Validation
- RMSE, MAE, and R² on held-out test set
- Residual diagnostics (normality, homoscedasticity)
- Predicted vs. actual scatter plots

## Customization

Key parameters can be adjusted in the script:

- **Outlier detection:** IQR multiplier (default: 1.5)
- **Risk thresholds:** Percentile cutoffs (default: 90th, 95th)
- **Risk bands:** Tercile splits (default: 33rd, 67th percentiles)
- **Clustering parameters:** `eps` and `minPts` for DBSCAN
- **Color palette:** viridis options (A-E)

## Reproducibility

- Random seed set to `42`
- Session info saved to `outputs/tables/session_info.txt`
- All file paths use `here()` for cross-platform compatibility

## Known Issues

- GPS clustering requires ≥10 valid coordinate pairs
- Model assumes linear relationships (may underfit complex patterns)
- Reliability boundary plot requires sufficient prediction range

## Future Enhancements

- Machine learning models (random forest, XGBoost)
- Real-time dashboard integration (Shiny)
- Automated reporting (RMarkdown/Quarto)
- External weather API integration

## License

[ MIT.]

## Contact

**Paul Kamande**  
[paulkamande9@gmail.com]

---

*This project demonstrates advanced R proficiency in data wrangling, statistical modeling, geospatial analysis, and reproducible research workflows.*
