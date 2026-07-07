# Aviation Accident Analysis

## Overview

This project analyzes commercial and passenger jet airline safety from 1948–2023, focusing on aircraft makes, models, and operational factors that influence accident severity. The goal was to identify aircraft with low rates of total destruction and low likelihood of fatal or serious passenger injuries—providing actionable recommendations for an airline/airplane insurer.

## Objectives

- Identify aircraft makes and models with the best safety records (low injury fractions and destruction rates)
- Separate recommendations for **small aircraft** (<20 passengers) vs. **large aircraft** (≥20 passengers)
- Determine which operational factors (weather, engine type, phase of flight) most influence safety
- Ensure all findings are **statistically robust** with sufficient sample sizes (≥5–10 accidents per group)

## Data Source

- **AviationData.csv** — U.S. aviation accident data spanning 1948–2023
- Contains appriximately 90,000 records with 31 fields, including accident details, aircraft specifications, injuries, and weather conditions

## Methodology

### 1. Data Cleaning & Preprocessing

- Filtered to **1983–2023** (40-year max aircraft lifetime)
- Created `Plane.Size` (Small/Large) based on passenger count (threshold = 20)
- Engine type imputation using group-mode imputation
- Removed rows with missing `Make`/`Model` and zero passengers
- Derived metrics:
  - `Injury_Fraction` = (Fatal + Serious Injuries) / Total Passengers
  - `Is_Destroyed` = True if `Aircraft.damage == "Destroyed"`

### 2. Exploratory Data Analysis

- **Comparative visualizations**: bar charts, violin plots, stripplots
- **Injury fraction analysis**: by make, model, size category
- **Destruction rate analysis**: by make, size category
- **Operational factors**: weather, engine type, number of engines, phase of flight, purpose of flight

### 3. Statistical Rigor

- Filtered groups to ensure minimum accident counts (≥5 for makes, ≥10 for types)
- Mean and distribution-based comparisons
- No statistical tests were used, but results are descriptive and based on aggregate statistics

## Key Findings

### Safest Aircraft Makes

**Small Aircraft** – The safest makes for small planes (based on lowest mean injury fractions and destruction rates) include: Waco, Grumman‑Schweizer, Maule, Helio, and Boeing.

**Large Aircraft** – For larger passenger aircraft, the top‑performing makes are: Aerospatiale, Bombardier INC, Airbus Industrie, McDonnell Douglas, and Lockheed.

### Safest Aircraft Models

**Large Aircraft** – The models with the lowest injury fractions and destruction rates are: Boeing 747‑200, Boeing 747‑400, Boeing 767‑300, McDonnell Douglas MD‑80, and Boeing 737‑300.

**Small Aircraft** – The safest small aircraft models include: Beech 19, Bell 47D‑1, Cessna 180C, Cessna 310B, Diamond Aircraft DA 20 C1, Grumman G164B, Maule M‑7‑235C, and Maule MX‑7‑235.

### Operational Factors

**Weather** – Instrument Meteorological Conditions (IMC) are associated with a destruction rate of 0.567, which is more than three times higher than Visual Meteorological Conditions (VMC) at 0.170. This highlights IMC as a major risk multiplier.

**Engine Type** – Turbo Fan engines have the lowest destruction rate (0.071) and injury fraction (0.071). In contrast, Reciprocating engines show a substantially higher destruction rate (0.203), making them riskier.

**Phase of Flight** – Takeoff and landing phases exhibit elevated risk compared to cruise and other phases (analysis was conducted but is not detailed here).

**Purpose of Flight** – Personal and instructional flights tend to have higher risk profiles than commercial or other operations (analysis was conducted but is not detailed here).

## Recommendations

### For Insurers

1. **Prioritize coverage** for:
   - Aerospatiale, Bombardier, Airbus Industrie (large)
   - Waco, Grumman-Schweizer, Maule (small)
   - Turbo Fan and Turbo Jet engines
2. **Increase premiums** or enforce stricter underwriting for:
   - Older reciprocating engine aircraft
   - Aircraft frequently flying in IMC conditions
   - High-risk makes/models (not listed here)

## Technologies Used

- **Python 3.14.3**
- **pandas** — data manipulation
- **numpy** — numerical operations
- **matplotlib** — static visualizations
- **seaborn** — statistical visualizations
- **Jupyter Notebook** — analysis environment

## Files in this Repository

- **`Aviation_Accidents_Cleaning.ipynb`** – Data cleaning, preprocessing, and feature engineering (handling missing values, creating derived metrics, filtering relevant records).
- **`Aviation_Accidents_Data_Analysis.ipynb`** – Exploratory data analysis, visualisations, and the final recommendations for insurers and operators.
- **`AviationData.csv`** – The raw accident dataset (not included in this repository for privacy and size reasons).
- **`AviationData_Cleaned.csv`** – The cleaned dataset (not included in this repository for privacy and size reasons).

## Limitations

- Missing data for latitude/longitude prevents geospatial analysis
- No statistical hypothesis tests were conducted (descriptive only)
- Time-series trends were not analyzed
- Engine type may be correlated with aircraft size and purpose (confounding)

## Next Steps

- Add **multivariate regression** to isolate independent effects
- Incorporate **survival analysis** for time-between-accidents
- Build a **predictive model** for accident severity
- Perform **cost-benefit analysis** for insurance premium adjustments

## Author

Shaun Raymond Macharia Okwuosa
