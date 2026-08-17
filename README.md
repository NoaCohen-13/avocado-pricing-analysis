# Avocado Pricing & Volume Analysis

This is a two-person academic statistics project, co-authored by **Noa Cohen and Shirley**. It is a joint final project, not solo work — both authors contributed equally to the analysis and write-up.

## Dataset

The dataset contains weekly measurements of avocado prices and sales volume across the United States from 2015 to 2018, including both broad regions (e.g., total US, East, West) and individual cities. Because broader regions overlap with the cities they contain, the research questions below focus on comparing specific cities against themselves across years, to avoid double-counting.

Key columns used in this analysis:
- `4046` — total volume of PLU 4046 avocados sold
- `Total Bags` — total volume of avocados sold in bags
- `AveragePrice`, `type` (conventional/organic), `region`, `year`

Since several of these values are in the millions, a **log transformation** was applied before running the statistical tests, to make the data more tractable for comparison.

## Research Questions & Methods

**1. Los Angeles — Total Bags, 2015 vs. 2016 (paired t-test)**
Did the average volume of bags sold in Los Angeles stay the same between 2015 and 2016, at a 90% confidence level? Since the same population (assumed same stores) is measured under two different conditions (years), a **paired t-test** (two-tailed, α = 0.1) was used on the first 40 weekly samples of each year (conventional avocados only).

**2. Chicago — PLU 4046 vs. Total Bags volume, 2015 (two-sample z-test)**
Is the average volume of bags sold in Chicago in 2015 equal to the average volume of PLU 4046 avocados sold in Chicago that same year, at a 95% confidence level? Since these are two independent samples with variances estimated from the full population, a **two-sample z-test** (left-tailed, α = 0.05) was used, again on the first 40 weekly samples (conventional avocados only).

## Conclusions

Both hypothesis tests **rejected the null hypothesis (H0)**:

- **Question 1:** There is not enough evidence to assume the difference in average bag volume sold in Los Angeles between 2015 and 2016 is zero.
- **Question 2:** There is not enough evidence to assume the average bag volume sold in Chicago in 2015 equals the average PLU 4046 volume sold that year.

See `writeup.md` for the full analysis, including sample statistics, graphs description, and discussion of possible limitations (e.g., small sample size of 40 weeks) and follow-up questions.

## Repository Contents

- `avocado_analysis.ipynb` — full analysis notebook (data exploration, graphs, paired t-test, two-sample z-test)
- `writeup.md` — full written analysis and discussion (Hebrew)
- `avocado.csv` — dataset (not included; see note below)

## Note on the Dataset File

`avocado.csv` is not included in this repository. To run the notebook, place the avocado prices dataset (e.g., from Kaggle's ["Avocado Prices"](https://www.kaggle.com/datasets/neuromusic/avocado-prices) dataset) in the repository root as `avocado.csv`.
