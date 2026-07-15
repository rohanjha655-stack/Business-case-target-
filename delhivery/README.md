# Delhivery Logistics & Supply Chain Analytics

> Why does Delhivery's routing engine consistently underestimate delivery time, and where should the network expand?

## Overview
- **Domain:** Logistics / Supply Chain
- **Dataset:** 144,867 shipment segment records → aggregated to 14,817 trips (2018)
- **Tools:** Python, Pandas, NumPy, SciPy, Scikit-Learn

## Business Problem
Delhivery's data team needed to understand where actual delivery performance diverges from routing-engine (OSRM) estimates, which regions drive order volume, and where operational investment would have the most impact.

## Approach
- Cleaned and restructured raw segment-level data into trip-level records via groupby aggregation rules
- Engineered features: state/city extraction from location names, segment keys, trip duration, running totals
- Applied IQR-based outlier removal on time and distance columns (reduced 14,817 → 10,521 clean trips)
- Ran Wilcoxon Signed-Rank tests comparing actual vs. OSRM-estimated time and distance
- One-hot encoded route type (FTL vs. Carting) and normalized numeric features for downstream modeling

## Key Findings
- Two distinct trip types dominate: **FTL** (Full Truck Load — long-distance, direct) and **Carting** (short-distance, last-mile)
- **Maharashtra, Gujarat, Karnataka, and Tamil Nadu** generate the majority of order origin volume
- **Within-state deliveries dominate** the network — long-haul is the minority case
- OSRM (routing engine) time estimates are **statistically significantly different** from actual delivery time (Wilcoxon test, p < 0.000001 across all four comparisons) — OSRM systematically underestimates real-world time, likely due to unmodeled loading/unloading time, traffic, and checkpoint delays
- A data-quality gap exists between segment-level actual time sums and total trip actual time, suggesting a reconciliation issue worth investigating further

## Business Recommendation
1. Expand sorting/delivery capacity in Maharashtra, Gujarat, and Karnataka, where order volume concentrates
2. Add real-world delay factors (traffic, loading time) to OSRM-based routing rather than relying on theoretical shortest-path time
3. Investigate the segment-vs-trip time discrepancy as a data quality/forecasting risk
4. Prepare for festive-season demand spikes by hiring and adding vehicle capacity a month ahead
5. Prioritize optimizing within-state (Carting) routes over long-haul, since that's where most volume sits

## Visuals
[Add the boxplot outlier chart or a bar chart of order volume by state — this is the single highest-impact addition]

## How to Run
```
pip install pandas numpy scipy scikit-learn matplotlib seaborn
jupyter notebook delhivery_analysis.ipynb
```

## Files
- `delhivery_analysis.ipynb` — main analysis notebook
- `data/` — dataset (Delhivery public logistics dataset)
- `README.md` — this file
