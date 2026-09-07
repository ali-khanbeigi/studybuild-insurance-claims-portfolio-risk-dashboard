# Data

This project uses the public French Motor Third-Party Liability dataset:

**freMTPL2**

Official dataset documentation:

https://dutangc.github.io/CASdatasets/reference/freMTPL.html

The original data contains policy-level frequency information and claim-level severity information linked by policy ID.

## Processed Data

The Python notebook performs all major data preparation steps before Tableau:

- data type inspection
- missing-value checks
- duplicate and key validation
- severity aggregation by policy
- policy-level merge
- driver, vehicle and Bonus-Malus segmentation
- KPI calculation
- Pareto and extreme-claim analysis
- Tableau-ready export

Two processed datasets are created:

### `tableau_portfolio.csv`

One row per insurance policy.

Used for:

- portfolio KPIs
- regional analysis
- driver and vehicle segment analysis
- Bonus-Malus analysis
- claim frequency and severity comparisons

### `tableau_claims.csv`

One row per observed claim.

Used for:

- Pareto analysis
- high-cost claim analysis
- extreme-claim analysis
- Top 10 highest-cost claims

## File Size Note

The full `tableau_portfolio.csv` file is approximately 57 MB and is not included in this repository because of browser-based GitHub upload limits.

The file can be reproduced directly by running the project notebook:

`notebooks/insurance_analysis.ipynb`

This keeps the repository lightweight while preserving a fully reproducible workflow.

## Important Notes

- No manual data cleaning was performed inside Tableau.
- Large claims were retained and investigated rather than automatically removed as outliers.
- Premium information is not available in `freMTPL2`, so Loss Ratio is not calculated.
