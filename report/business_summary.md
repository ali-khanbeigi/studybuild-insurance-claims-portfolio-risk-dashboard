# Insurance Claims & Portfolio Risk
## Business Summary

## Portfolio Overview

The analyzed motor-insurance portfolio contains **677,991 policies** representing approximately **358.48K policy-years of exposure**.

A total of **26,444 claims** were observed, corresponding to an overall claim frequency of approximately **7.38%**.

Total claim cost was approximately **59.91M**, with average claim severity of approximately **2,266**.

---

## Key Business Findings

### Regional Performance

**Rhone-Alpes** recorded the highest regional claim frequency at approximately **9.34%**.

The region also generated approximately **10.28M** in total claim cost and had average claim severity above the overall portfolio baseline.

This makes Rhone-Alpes an appropriate candidate for a more detailed regional review.

---

### Driver and Vehicle Segments

Drivers aged **18–25** showed both elevated claim frequency and elevated average claim severity relative to the overall portfolio.

Vehicle-age analysis showed that claim occurrence and claim cost intensity do not necessarily move together:

- Vehicles aged **6–10 years** showed the highest claim frequency.
- Vehicles aged **11–15 years** showed the highest average claim severity.

This indicates that claim frequency and severity should be monitored separately.

---

### Bonus-Malus

The **Bonus-Malus 100+** segment showed one of the strongest patterns in the analysis.

The segment recorded:

- approximately **26.25% claim frequency**
- approximately **4,948 average claim severity**
- the highest extreme-claim rate among Bonus-Malus groups

This segment deserves additional analytical and claims-management attention, while the result should be interpreted as a descriptive association rather than causal evidence.

---

## Claim Cost Concentration

Claim costs are strongly concentrated among high-cost claims.

- The highest-cost **1% of claims account for approximately 37.99%** of total claim cost.
- The top 5% account for approximately **52.09%**.
- The top 10% account for approximately **59.92%**.
- Approximately **40.62% of the highest-cost claims account for 80%** of total claim cost.

The portfolio therefore shows meaningful cost concentration, although it does not follow a strict 80/20 pattern.

---

## Extreme Claims

Using the **99.9th percentile of ClaimAmount** as the extreme-claim threshold, **27 extreme claims** were identified.

These claims represent only about **0.1% of observed claims**, but account for approximately **21.63% of total claim cost**.

Large claims therefore have a substantial financial impact on the portfolio and should be managed as a separate analytical category.

---

# Recommendations

## 1. Conduct a Rhone-Alpes Regional Deep-Dive

### Evidence

Rhone-Alpes has the highest regional claim frequency at approximately **9.34%**, total claim cost of approximately **10.28M**, and average claim severity above the portfolio baseline.

### Action

Break Rhone-Alpes down by:

- Driver age
- Vehicle age
- Bonus-Malus group
- Fuel type

Identify which subsegments contribute most to the elevated frequency and claim cost.

Compare those subsegments with equivalent groups in other regions and separately review the region's highest-cost claims.

This helps determine whether the regional pattern is broadly distributed or concentrated within specific subsegments or large claims.

### KPI

- Claim Frequency
- Total Claim Cost
- Average Claim Severity
- Exposure
- Top-Claim Cost Share by subsegment

---

## 2. Create a Dedicated Bonus-Malus 100+ Review Workflow

### Evidence

The Bonus-Malus 100+ segment has approximately **26.25% claim frequency**, average claim severity of approximately **4,948**, and the highest extreme-claim rate among Bonus-Malus groups.

### Action

Create a dedicated review view for the Bonus-Malus 100+ segment and analyze it by:

- Driver age
- Region
- Vehicle age

High-cost claims within the segment should be highlighted separately so management can distinguish broad segment behavior from the effect of a small number of unusually large claims.

Claims above the large-claim threshold can be included in a secondary review queue containing their main policy and segment characteristics.

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

The top 1% of claims generate approximately **37.99% of total claim cost**, while only **27 extreme claims** generate approximately **21.63%**.

### Action

Use the **99.9th percentile of ClaimAmount** as an initial analytical threshold for a dedicated large-claim exception process.

Claims above this threshold should appear in a separate management view containing:

- Claim amount
- Region
- Driver segment
- Vehicle segment
- Bonus-Malus group
- Contribution to total claim cost

Management should review the largest claims individually and track the share of total cost generated by:

- Top 1% of claims
- Top 5% of claims
- Extreme claims

The threshold should be recalculated whenever new reporting-cycle data becomes available so that it remains aligned with the current claim distribution.

### KPI

- Top 1% Cost Share
- Top 5% Cost Share
- Extreme Claim Count
- Extreme Claim Cost Share
- Maximum Claim Amount

---

## Limitations

This project is a **descriptive business intelligence analysis** and does not establish causal relationships.

Premium information is unavailable, so **Loss Ratio cannot be calculated**.

The dataset does not include a date/month field, preventing true month-over-month trend analysis.

Small segments may produce unstable frequency or severity estimates and should be interpreted together with exposure and claim counts.

Large claims were retained and investigated rather than automatically removed as outliers.
