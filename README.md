# Avocado Pricing & Volume Analysis

An academic statistics final project by **Noa Cohen and Shirley**, analyzing weekly US avocado pricing and volume data with hypothesis testing.

## Dataset

The dataset contains weekly measurements of avocado prices and sales volume across the United States from 2015 to 2018, including both broad regions (e.g., total US, East, West) and individual cities. Because broader regions overlap with the cities they contain, the research questions below focus on comparing specific cities against themselves across years, to avoid double-counting.

Key columns used in this analysis:
- `4046` — total volume of PLU 4046 avocados sold (Hass, small)
- `4225`, `4770` — total volume of the other two Hass PLU codes
- `Total Bags` — total volume of avocados sold in bags
- `AveragePrice`, `type` (conventional/organic), `region`, `year`

### Exploratory statistics (Total US average, 2015–2018)

| Metric | Average |
|---|---|
| Total Volume | 17,351,302 |
| PLU 4046 volume | 6,079,693 |
| PLU 4225 volume | 5,961,573 |
| PLU 4770 volume | 462,057 |
| Total Bags volume | 4,847,931 |
| Average Price (per avocado) | $1.319 |

Since several of these values are in the millions, a **log transformation** was applied before running the statistical tests, to make the data more tractable for comparison.

**PLU 4046 volume, Total US** (2015 vs. 2016):

![PLU 4046 volume, TotalUS 2015](images/graph_1.png) ![PLU 4046 volume, TotalUS 2016](images/graph_2.png)

**Total Bags volume, Total US** (2015 vs. 2016):

![Total Bags volume, TotalUS 2015](images/graph_3.png) ![Total Bags volume, TotalUS 2016](images/graph_4.png)

Both metrics show similar seasonal patterns from January–June across years, with a notable divergence between June and September — which motivated comparing the two years directly in the research questions below.

## Research Questions & Methods

### 1. Los Angeles — Total Bags, 2015 vs. 2016 (paired t-test)

Did the average volume of bags sold in Los Angeles stay the same between 2015 and 2016, at a 90% confidence level?

- H0: μ_diff = 0
- H1: μ_diff ≠ 0
- Confidence level = 0.9, α = 0.1

Since the same population (assumed same stores) is measured under two different conditions (years), a **paired t-test** (two-tailed) was used. Sample: the first 40 weekly observations of each year (n = 40), conventional avocados only, log-transformed to handle the large-magnitude values.

Before / after log transformation, Los Angeles 2015:

![Total Bags volume, Los Angeles 2015](images/graph_5.png) ![Total Bags volume (log-transformed), Los Angeles 2015](images/graph_6.png)

Los Angeles 2016 (also log-transformed for consistency):

![Total Bags volume, Los Angeles 2016](images/graph_7.png) ![Total Bags volume (log-transformed), Los Angeles 2016](images/graph_8.png)

### 2. Chicago — PLU 4046 vs. Total Bags volume, 2015 (two-sample z-test)

Is the average volume of bags sold in Chicago in 2015 equal to the average volume of PLU 4046 avocados sold in Chicago that same year, at a 95% confidence level?

- D0 = μ(4046) − μ(Total Bags)
- H0: D0 = 0
- H1: D0 < 0
- Confidence level = 0.95, α = 0.05

Since these are two independent samples with variances estimated from the full population, a **two-sample z-test** (left-tailed) was used. Sample: the first 40 weekly observations of 2015 for each series (n1 = n2 = 40), conventional avocados only, log-transformed.

## Conclusions

Both hypothesis tests **rejected the null hypothesis (H0)**:

- **Question 1:** There is not enough evidence to assume the difference in average bag volume sold in Los Angeles between 2015 and 2016 is zero.
- **Question 2:** There is not enough evidence to assume the average bag volume sold in Chicago in 2015 equals the average PLU 4046 volume sold that year.

### Limitations & follow-up questions

- The n = 40 sample size may be too small; extending the comparison across more years (e.g., 2015–2016 vs. 2017–2018) could yield a more precise result for Question 1.
- Since the two Question 2 samples are drawn from genuinely independent series (bag volume vs. a specific PLU), a nonzero difference is a reasonable outcome — they aren't expected to track each other exactly.
- Open questions raised during the analysis: Do larger states buy more bags / PLU 4046 avocados? Is there a seasonal effect on avocado purchases? Would sampling a different state yield the same conclusions?

See `writeup.md` for the full analysis (Hebrew), including detailed statistics and discussion.

## Repository Contents

- `avocado_analysis.ipynb` — full analysis notebook (data exploration, graphs, paired t-test, two-sample z-test)
- `writeup.md` — full written analysis and discussion (Hebrew)
- `images/` — graphs referenced in `writeup.md`, exported from the notebook
- `avocado.csv` — dataset (not included; see note below)

## Note on the Dataset File

`avocado.csv` is not included in this repository. To run the notebook, place the avocado prices dataset (e.g., from Kaggle's ["Avocado Prices"](https://www.kaggle.com/datasets/neuromusic/avocado-prices) dataset) in the repository root as `avocado.csv`.
