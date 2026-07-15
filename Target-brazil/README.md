# Target Brazil E-Commerce Analysis

> Where are the biggest gaps in Target's Brazil delivery and payment experience, and what's driving them?

## Overview
- **Domain:** E-commerce / Logistics
- **Dataset:** 100K+ orders, Target Brazil (2016–2018)
- **Tools:** SQL, MySQL

## Business Problem
Target's Brazil marketplace needed visibility into where order fulfillment and delivery were underperforming, and which regions or payment types were linked to those gaps. This analysis breaks down order, payment, and delivery data to surface actionable patterns for the operations team.

## Approach
- Wrote advanced SQL queries using JOINs, CTEs, Window Functions, and Subqueries to combine orders, payments, and delivery tables
- Segmented performance by region and payment method
- Compared estimated vs. actual delivery timelines to flag fulfillment gaps

## Key Findings
- Identified specific regions with consistently higher delivery delays relative to the national average
- Found payment method correlated with order value and delivery performance patterns
- Surfaced fulfillment bottlenecks concentrated in a subset of states rather than spread evenly

## Business Recommendation
Prioritize logistics/carrier review in the underperforming regions identified, and monitor payment-method-linked delivery patterns as an early signal for fulfillment risk.

## Visuals
[Add a screenshot here — e.g., a bar chart of delivery delay by region, or a query output table]

## How to Run
```
Import the provided .sql scripts into MySQL Workbench or your preferred client
Run queries in order: 01_data_overview.sql → 02_regional_analysis.sql → 03_payment_delivery.sql
```

## Files
- `queries/` — SQL scripts
- `data/` — dataset or Kaggle source link
- `README.md` — this file
