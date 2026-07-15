# IPL Match Strategy & Performance Analysis

> Does winning the toss and choosing to field actually improve your odds of winning an IPL match?

## Overview
- **Domain:** Sports Analytics
- **Dataset:** 636 IPL matches + 150,460 ball-by-ball deliveries (2008–2017)
- **Tools:** Python, Pandas, NumPy, SciPy, Matplotlib, Seaborn

## Business Problem
Move beyond surface-level cricket stats to validate, with formal hypothesis testing, whether toss strategy and match phase (powerplay vs. death overs) meaningfully affect outcomes — the kind of question a team's strategy analyst would need answered with statistical confidence, not gut feel.

## Approach
- Merged match-level (`matches.csv`) and ball-by-ball (`deliveries.csv`) datasets in Pandas
- Computed win rates by toss decision and validated significance using a Chi-Square Test of Independence
- Segmented deliveries by over number to compare powerplay (overs 1–6) vs. death-over (overs 16–20) scoring
- Aggregated batting/bowling stats across 10 seasons, applying a minimum-sample filter (200+ balls) for bowler economy rankings to avoid small-sample noise
- Visualized comparisons with Matplotlib/Seaborn

## Key Findings
- Teams that won the toss and chose to **field first won 55.4%** of matches (n=363) vs. **45.4%** when choosing to bat first (n=273) — confirmed statistically significant via Chi-Square test (χ²=5.78, p=0.016), not random variation
- Consistent with this, **339 matches were won chasing** vs. **287 won defending** a total
- Powerplay overs outscore death overs: **90.3 runs/innings** (overs 1–6) vs. **83.6 runs/innings** (overs 16–20)
- Top run scorers (2008–2017): SK Raina (4,548), V Kohli (4,423), RG Sharma (4,207), G Gambhir (4,132), DA Warner (4,014)
- Most economical death-over bowlers (min. 200 balls): SP Narine (7.14), DE Bollinger (7.36), SL Malinga (7.43), MA Starc (7.57), R Ashwin (7.58 runs/over)

## Business Recommendation
Toss decision is a measurable, statistically validated lever, not superstition — teams should default to fielding first when conditions are neutral, and death-over bowling selection should weight the economy leaderboard above raw wicket counts.

## Visuals
Win rate by toss decision and top 5 run scorers, 2008–2017:
[Insert `ipl_analysis_charts.png` here]

## How to Run
```
pip install pandas numpy scipy matplotlib seaborn
python ipl_analysis.py
```

## Files
- `ipl_analysis.py` — full analysis script (data load → hypothesis testing → visualization)
- `data/matches.csv`, `data/deliveries.csv` — dataset (public IPL dataset, Kaggle, via Manas Garg)
- `ipl_analysis_charts.png` — output visualization
- `README.md` — this file
