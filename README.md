# Insurance Claims & Portfolio Risk Dashboard

A descriptive insurance analytics and business intelligence project built with **Python, Pandas, and Tableau** to analyze motor-insurance claim frequency, severity, regional patterns, portfolio segments, and claim-cost concentration.

The project uses the public **freMTPL2 French Motor Third-Party Liability dataset** and transforms raw insurance data into management-focused KPIs, interactive Tableau dashboards, and evidence-based business recommendations.

---

## Project Objectives

The project answers the following business questions:

1. What is the overall health of the insurance portfolio?
2. Which regions generate the greatest claim burden?
3. Which driver and vehicle segments show different claim patterns?
4. Are frequent-claim segments also expensive-claim segments?
5. Is claim cost concentrated in a small number of claims?
6. Which unusual claims or segments deserve management attention?
7. What should management monitor in future reporting cycles?
8. What data-driven actions should management consider?

> This is a **descriptive analytics / BI project**, not a pricing, underwriting, fraud-detection, or causal modeling project.

---

## Dataset

This project uses the public **freMTPL2** French Motor Third-Party Liability dataset.

The data contains:

- Policy-level exposure
- Claim counts
- Driver characteristics
- Vehicle characteristics
- Bonus-Malus information
- Regional information
- Claim-level severity data

### Portfolio Size

- **677,991 policies**
- **358.48K policy-years of exposure**
- **26,444 observed claims**

Official dataset documentation:

https://dutangc.github.io/CASdatasets/reference/freMTPL.html

Premium information is not available in this dataset; therefore, **Loss Ratio is not calculated**.

---

## Tech Stack

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook
- Tableau
- Git / GitHub

---

## Data Preparation Workflow

All major data preparation steps were performed in Python before the data was used in Tableau.

The workflow included:

1. Data structure and data-type inspection
2. Missing-value review
3. Policy ID and table-grain validation
4. Duplicate review
5. Numeric range and unusual-value checks
6. Claim severity aggregation at policy level
7. Frequency and severity table merge
8. Post-merge claim reconciliation
9. Driver, vehicle, and Bonus-Malus segment creation
10. Portfolio and segment KPI calculation
11. Frequency-vs-severity analysis
12. Pareto claim-cost concentration analysis
13. Extreme-claim analysis
14. Tableau-ready data export

Large claims were retained and investigated rather than automatically removed as outliers.

---

## Core Insurance KPIs

| KPI | Definition |
|---|---|
| Policy Count | Number of unique policies |
| Total Exposure | Sum of policy exposure in years |
| Claim Count | Total number of observed claims |
| Claim Frequency | Claim Count / Total Exposure |
| Total Claim Cost | Sum of claim amounts |
| Average Claim Severity | Total Claim Cost / Number of observed claims |

> **Note:** Claim Frequency is exposure-adjusted and should not be interpreted as the percentage of drivers who experienced an accident.

---

## Portfolio Overview

| KPI | Result |
|---|---:|
| Policy Count | **677,991** |
| Total Exposure | **358.48K policy-years** |
| Claim Count | **26,444** |
| Claim Frequency | **7.38%** |
| Total Claim Cost | **59.91M** |
| Average Claim Severity | **2,266** |

These values were validated in both Python and Tableau.

---

# Key Findings

## 1. Regional Performance

**Rhone-Alpes** recorded the highest regional claim frequency at approximately **9.34%**.

The region also generated approximately **10.28M** in total claim cost and had average claim severity above the overall portfolio baseline.

Regional performance was evaluated using exposure-adjusted metrics rather than raw claim counts alone.

---

## 2. Driver Age

Drivers aged **18–25** showed:

- Claim Frequency: approximately **14.81%**
- Average Claim Severity: approximately **5,122**

This segment showed both higher claim occurrence and higher average claim cost relative to the overall portfolio.

---

## 3. Vehicle Age

Vehicles aged **6–10 years** showed the highest claim frequency among the vehicle-age groups.

Vehicles aged **11–15 years** showed the highest average claim severity.

This demonstrates why claim frequency and claim severity should be analyzed separately.

---

## 4. Bonus-Malus

The **Bonus-Malus 100+** segment stood out across several measures:

- Claim Frequency: approximately **26.25%**
- Average Claim Severity: approximately **4,948**
- Highest extreme-claim rate among Bonus-Malus groups

This segment also appeared in the **high-frequency / high-severity** area of the frequency-vs-severity analysis.

---

## 5. Claim Cost Concentration

Claim costs are highly concentrated among the largest claims.

- Top 1% of claims account for approximately **37.99%** of total claim cost
- Top 5% account for approximately **52.09%**
- Top 10% account for approximately **59.92%**
- Approximately **40.62%** of the highest-cost claims account for **80%** of total claim cost

The portfolio therefore shows substantial claim-cost concentration, although it does not follow a strict 80/20 pattern.

---

## 6. Extreme Claims

The **99.9th percentile of ClaimAmount** was used as an analytical threshold for identifying extreme claims.

- Extreme-claim threshold: approximately **152,223**
- Extreme Claim Count: **27**
- Extreme Claim Cost Share: approximately **21.63%**

Only about 0.1% of observed claims therefore generate more than one-fifth of total claim cost.

These claims were flagged for business review and were not interpreted as evidence of fraud or incorrect data.

---

# Tableau Dashboard

The final Tableau solution contains three dashboard pages.

## Page 1 — Executive Portfolio Overview
![executive_portfolio_overview](figures/executive_portfolio_overview.png)
Provides:

- Policy Count
- Total Exposure
- Claim Count
- Claim Frequency
- Total Claim Cost
- Average Claim Severity
- Claim Frequency by Region
- Claim Frequency by Bonus-Malus Group
- Interactive filters

![Executive Portfolio Overview](figures/executive_portfolio_overview.png)

---

## Page 2 — Claims & Risk Segments
![Claims & Risk Segments](figures/claims_risk_segments.png)
Provides:

- Claim Frequency by Driver Age
- Claim Frequency by Vehicle Age
- Frequency vs Severity analysis
- Portfolio baseline reference lines
- Policy Count as segment-size context
- Region and fuel filters

![Claims & Risk Segments](figures/claims_risk_segments.png)

---

## Page 3 — Claim Cost Concentration & Large Claims
![Claim Cost Concentration](figures/claim_cost_concentration.png)
Provides:

- Extreme Claim Count
- Extreme Claim Cost Share
- Top 1% Cost Share
- Pareto claim-cost concentration analysis
- Top 10 highest-cost claims
- Management recommendations

![Claim Cost Concentration](figures/claim_cost_concentration.png)

---

# Management Recommendations

## 1. Conduct a Rhone-Alpes Regional Deep-Dive

### Evidence

Rhone-Alpes has the highest regional claim frequency at approximately **9.34%**, generates approximately **10.28M** in total claim cost, and has average severity above the portfolio baseline.

### Action

Create a dedicated regional drill-down for Rhone-Alpes in the next reporting cycle.

Break the region down by:

- Driver age
- Vehicle age
- Bonus-Malus group
- Fuel type

Identify which subsegments contribute most to the elevated claim frequency and total claim cost.

The largest individual claims in the region should also be reviewed separately and compared with equivalent subsegments in other regions.

This allows management to determine whether the regional result is broadly distributed or concentrated within specific subsegments or high-cost claims.

### KPI

- Claim Frequency
- Total Claim Cost
- Average Claim Severity
- Exposure
- Top-Claim Cost Share by subsegment

---

## 2. Create a Dedicated Bonus-Malus 100+ Review Workflow

### Evidence

The Bonus-Malus 100+ segment shows approximately **26.25% claim frequency**, average claim severity of approximately **4,948**, and the highest extreme-claim rate among Bonus-Malus groups.

### Action

Create a dedicated analytical review view for the Bonus-Malus 100+ segment and break its results down by:

- Driver age
- Region
- Vehicle age

High-cost claims within this segment should be highlighted separately so management can distinguish broad segment behavior from the impact of a small number of unusually large claims.

Claims above the large-claim threshold can be added to a secondary review queue containing their main policy and segment characteristics.

The purpose is to provide deeper operational insight without automatically making pricing, underwriting, or causal assumptions.

### KPI

- Claim Frequency
- Average Claim Severity
- Extreme Claim Rate
- Total Claim Cost
- Exposure

---

## 3. Establish a Formal Large-Claim Review Process

### Evidence

The top 1% of claims generate approximately **37.99%** of total claim cost, while only **27 extreme claims** generate approximately **21.63%** of total claim cost.

### Action

Use the **99.9th percentile of ClaimAmount** as an initial analytical threshold for a dedicated large-claim exception process.

Claims above this threshold should appear in a separate management view containing:

- Claim amount
- Region
- Driver segment
- Vehicle segment
- Bonus-Malus group
- Contribution to total claim cost

Management should review the largest claims individually and monitor the share of total portfolio cost generated by the:

- Top 1% of claims
- Top 5% of claims
- Extreme claims

The threshold should be recalculated whenever new reporting-cycle data becomes available.

This creates an operational early-warning view for claim-cost concentration and prevents a small number of high-cost claims from being hidden within portfolio averages.

### KPI

- Top 1% Cost Share
- Top 5% Cost Share
- Extreme Claim Count
- Extreme Claim Cost Share
- Maximum Claim Amount

---

# Limitations

- The dataset is historical and mainly represents policies observed during **2011–2013**.
- The insurer is anonymous.
- Premium data is unavailable, so **Loss Ratio cannot be calculated**.
- The analysis is descriptive and does not establish causal relationships.
- The available fields do not capture every factor relevant to insurance risk.
- Small segments may produce unstable frequency or severity estimates.
- Large claims can materially influence severity and total claim cost.
- The dataset does not contain a date/month field, so true month-over-month trend analysis cannot be performed.

---

# Repository Structure

```text
insurance-claims-portfolio-risk-dashboard/
│
├── README.md
├── requirements.txt
│
├── notebooks/
│   └── insurance_analysis.ipynb
│
├── data/
│   └── README.md
│
├── tableau/
│   └── insurance_claims_dashboard.twbx
│
├── figures/
│   ├── executive_portfolio_overview.png
│   ├── claims_risk_segments.png
│   └── claim_cost_concentration.png
│
└── report/
    └── business_summary.md
```

---

# Reproducing the Analysis

1. Download the original `freMTPL2` dataset from the official source.

2. Install the required Python packages:

```bash
pip install -r requirements.txt
```

3. Open and run:

`notebooks/insurance_analysis.ipynb`

4. The notebook performs the complete cleaning, validation, aggregation, segmentation, KPI calculation, Pareto analysis, extreme-claim analysis, and Tableau data preparation workflow.

---

# Processed Data Note

The full policy-level Tableau-ready CSV is approximately **57 MB** and is not included in this repository to keep the repository lightweight.

The processed dataset can be reproduced by running:

`notebooks/insurance_analysis.ipynb`

All major cleaning, aggregation, segmentation, and data-preparation steps are performed reproducibly in Python.

---

# Author

**Ali Ahmad Khanbeigi**

Data Analysis & Business Intelligence Portfolio Project
