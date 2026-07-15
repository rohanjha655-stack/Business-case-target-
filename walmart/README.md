# Walmart Black Friday Purchase Behavior Analysis

> Do spending patterns really differ by gender and marital status — or is that assumption wrong?

## Overview
- **Domain:** Retail
- **Dataset:** 550,068 Black Friday transactions, Walmart
- **Tools:** Python, Pandas, NumPy, SciPy, Matplotlib, Seaborn

## Business Problem
Marketing wanted to know whether gender, age, and marital status meaningfully predict spending, to decide whether segment-based targeting is worth the investment — validated with confidence intervals and the Central Limit Theorem rather than assumption.

## Approach
- Cleaned and retyped the dataset (550K+ rows, 10 columns, no missing values)
- Computed mean/median purchase value and compared across gender, age, and marital status segments
- Applied the Central Limit Theorem via bootstrapped sampling (1,000 iterations, sample sizes 30–100) to visualize how sample means stabilize
- Built 95% confidence intervals for male vs. female and married vs. unmarried spend to test whether differences are statistically meaningful, not just numerically different

## Key Findings
- Average purchase: **₹9,264** (mean) vs. **₹8,047** (median) — a right-skewed distribution, meaning a smaller group of high-value purchases pulls the average up
- **Gender gap is real and statistically significant**: male average spend (₹9,438) vs. female (₹8,735) — their 95% confidence intervals (Male: 9,422–9,453; Female: 8,709–8,760) **don't overlap**, confirming the difference isn't due to chance
- **Marital status gap is not significant**: married (₹9,265) vs. unmarried (₹9,261) — confidence intervals overlap almost entirely, meaning marketing shouldn't treat this as a real behavioral difference
- Highest-spending age groups: 51–55 (₹9,535) and 36–45 (₹9,331); lowest: 0–17 (₹8,933)
- The CLT simulation visually confirms that as sample size grows (30 → 100), the sampling distribution of the mean tightens and approaches normality — validating that the confidence intervals above are reliable

## Business Recommendation
Build gender-based and age-based targeting (26–55 age band, with a premium tilt toward 51–55) — but **don't** invest in marital-status-based segmentation, since the data shows no statistically real difference there despite what intuition might suggest.

## Visuals
[Add the CLT sample-mean histograms or the age/gender grouped bar chart — this is the single highest-impact addition]

## How to Run
```
pip install pandas numpy scipy matplotlib seaborn
jupyter notebook walmart_analysis.ipynb
```

## Files
- `walmart_analysis.ipynb` — main analysis notebook
- `data/` — dataset (Walmart Black Friday public dataset)
- `README.md` — this file
