# Nigeria Macroeconomic Intelligence & Labour Market Analytics Platform

**Data Analytics Internship — Advanced Capstone Project**  
NBS Nigeria | World Bank | CBN Statistical Datasets | 2015–2023  
Duration: 8 Weeks | 4 Analytical Modules | 9 Mandatory Deliverables

---

## Project Description

This project delivers a comprehensive macroeconomic intelligence platform for Nigeria, commissioned to inform investment risk assessments, sectoral allocation decisions, and labour market development programming across Nigeria's 36 states and FCT. The analysis covers GDP growth dynamics, inflation trends, labour market conditions, oil/non-oil sector divergence, and state-level disparities across the period 2015–2023 — spanning the 2016 recession, COVID-19 shock, 2021–2022 recovery, and the 2023 subsidy removal and naira float.

---

## Repository Structure

```
nigeria-macro-analytics/
├── data/
│   ├── raw/                          # Source datasets (CSV)
│   │   ├── nigeria_quarterly_gdp.csv
│   │   ├── nigeria_cpi_monthly.csv
│   │   ├── nigeria_labour_force_quarterly.csv
│   │   ├── nigeria_state_unemployment_2023.csv
│   │   ├── worldbank_nigeria_annual_full.csv
│   │   ├── nigeria_oil_production_monthly.csv
│   │   ├── brent_crude_monthly.csv
│   │   ├── nigeria_gdp_expenditure_annual.csv
│   │   ├── nigeria_zone_informal_employment.csv
│   │   ├── nigeria_master_quarterly_panel.csv
│   │   ├── nigeria_states_simplified.geojson
│   │   ├── nigeria_state_centroids.csv
│   │   ├── nigeria_forecast_scenarios.csv
│   │   └── data_quality_log.csv
│   └── processed/                    # Merged panel datasets
├── notebooks/
│   ├── module1_eda.py                # Exploratory Data Analysis
│   ├── module2_statistics.py         # Hypothesis Testing
│   ├── module3_modeling.py           # Predictive Modeling
│   └── module4_policy.py             # Policy Strategy & Dashboard
├── scripts/
│   └── download_data.py              # Automated data downloader
├── reports/
│   ├── policy_memo.txt               # CIO Policy Memo
│   └── key_findings_summary.csv      # 12 key findings
└── README.md
```

---

## Data Sources & Citations

| Dataset | Source | URL |
|---|---|---|
| Quarterly GDP by Sector (2015–2023) | NBS Nigeria | nigerianstat.gov.ng/elibrary |
| Monthly CPI & Inflation (2015–2023) | NBS Nigeria | nigerianstat.gov.ng/elibrary |
| Labour Force Survey Q1 2022–Q4 2023 | NBS Nigeria NLFS | nigerianstat.gov.ng/elibrary |
| State Unemployment 2023 | NBS Nigeria / Statista | nigerianstat.gov.ng |
| World Bank Nigeria Indicators | World Bank Open Data | data.worldbank.org/country/nigeria |
| Brent Crude Oil Prices (Monthly) | World Bank Pink Sheet | thedocs.worldbank.org (CMO-Historical) |
| CBN Exchange Rate / Oil Revenue | CBN Statistical Bulletin | cbn.gov.ng/documents/Statbulletin.asp |
| Nigeria State Shapefiles | GADM | geodata.ucdavis.edu/gadm/gadm4.1 |

---

## Setup Instructions

```bash
# Clone the repository
git clone https://github.com/OpeyemiAdeniji/nigeria-macro-analytics.git
cd nigeria-macro-analytics

# Create virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Download datasets (World Bank API + manual instructions)
python scripts/download_data.py

# Run modules in order
python notebooks/module1_eda.py
python notebooks/module2_statistics.py
python notebooks/module3_modeling.py
python notebooks/module4_policy.py
```

### requirements.txt
```
pandas==2.2.*
numpy==1.26.*
matplotlib==3.8.*
seaborn==0.13.*
plotly==5.21.*
folium==0.16.*
geopandas==0.14.*
scipy==1.12.*
statsmodels==0.14.*
prophet==1.1.*
xgboost==2.0.*
shap==0.45.*
scikit-learn==1.4.*
pingouin==0.5.*
```

---

## Module Overview & Key Findings

### Module 1 — Exploratory Data Analysis
- Nigeria's worst quarterly GDP contraction was **−6.1% in Q2 2020** (COVID trough), recovering to **+5.0% in Q2 2021**
- Headline inflation surged from **22.8% to 28.9%** in the 6 months following June 2023 subsidy removal
- **Zamfara** has the highest state unemployment (47.4%); **FCT Abuja** the lowest (12.8%)
- Oil price correlates positively with GDP growth: **Pearson r = 0.668**
- Northern zones (NW, NE) average unemployment **~18pp higher** than Southern zones

### Module 2 — Statistical Analysis
- **Significant regional inequality** across geopolitical zones: F=10.65, p<0.001, η²=0.63 (large effect)
- **Post-COVID growth (3.14%)** significantly exceeds pre-COVID (1.29%): t=−3.46, p=0.005, Cohen's d=−1.04
- **Exchange rate is the dominant driver** of headline inflation: coef=0.026, p<0.001, Adj R²=0.63
- **Northern zones show perfect association** with high informality (>90%): χ²=48.0, p<0.001, Cramér's V=1.0
- Oil vs Non-Oil GDP growth difference not statistically significant at α=0.05 (p=0.090)

### Module 3 — Predictive Modeling
- **ARIMA(1,1,1)** achieves test RMSE=1.12 on quarterly GDP growth; SARIMAX adds oil price exogenous variable
- **Prophet** forecasts inflation remaining above 25% through H1 2024 (MAPE=12.2%)
- **XGBoost + SHAP** identifies urban population share as the strongest predictor of state unemployment (CV RMSE=2.69)
- **Scenario analysis**: Upside (oil $100) vs Downside (oil $55, NGN −20%) GDP gap ≈ **$16B USD** for 2024–2025

### Module 4 — Policy Strategy
- Three priority recommendations: FX hedging, non-oil sector overweight, Southern-state deployment preference
- Inflation hurdle rate of **30%+ NGN yield** required for positive USD-equivalent real returns
- Full policy memo addressed to CIO and Head of Nigeria Operations

---

## Dashboard Screenshot

> Interactive dashboard built with folium (geospatial) and matplotlib.  
> Key panels: GDP Growth Timeline | Inflation Tracker | Geopolitical Zone Unemployment | Oil Production | Scenario Forecasts

---

## Professional Standards

- All raw data files preserved unmodified in `/data/raw/`
- All transformations documented in `data_quality_log.csv`
- Notebooks reproducible end-to-end from raw CSV inputs
- All statistics cited with source, year, and method
- Model cards included in `mod3_model_comparison.csv`

---

*Project data period: 2015 Q1 – 2023 Q4 | Currency: NGN for domestic figures, USD for international comparisons*  
*Sources: NBS Nigeria, World Bank Open Data, CBN Statistical Bulletin, World Bank Commodity Pink Sheet*
