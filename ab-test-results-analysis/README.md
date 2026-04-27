# A/B Test Results Analysis

## Overview
Statistical analysis of an e-commerce A/B test to determine whether a new landing page produces a meaningfully higher conversion rate than the existing page. The analysis progresses from descriptive statistics through probability, simulation-based hypothesis testing, and logistic regression — reaching a consistent conclusion across all methods.

## Research Question
**Does the treatment (new) landing page convert users at a higher rate than the control (existing) page?**

## Dataset
`ab_data.csv` — user-level records containing group assignment (control/treatment), landing page received, conversion outcome (0/1), and country (US, UK, CA).

## Project Workflow

### Part I – Descriptive Statistics
Explored the dataset structure, checked for missing values, calculated overall conversion rates, and visualized visit counts by country.

### Part II – Probability
Calculated conditional conversion probabilities broken down by group and country:

| | US | UK | CA |
|---|---|---|---|
| Control | 10.7% | 10.2% | 9.4% |
| Treatment | 15.8% | 14.9% | 15.4% |

The treatment group showed a consistent ~5 percentage point lift across all three countries, with no strong evidence of a country-group interaction.

### Part III – Hypothesis Testing (Simulation)
- **Null hypothesis:** The control page converts at a rate greater than or equal to the treatment page
- **Alternative hypothesis:** The treatment page converts at a higher rate
- Simulated 500 differences in conversion rates under the null hypothesis to build a sampling distribution
- Calculated the p-value as the proportion of simulated differences exceeding the observed difference
- **Result:** p-value < 0.05 → rejected the null hypothesis

### Part IV – Logistic Regression
Confirmed the hypothesis test results using logistic regression (statsmodels):
- **Model 1:** `converted ~ ab_page` — treatment page coefficient was statistically significant (p < 0.05)
- **Model 2:** `converted ~ ab_page + US + UK` — country variables were not statistically significant, confirming conversion differences are driven by page, not geography

## Conclusion
Both the simulation-based test and logistic regression consistently indicate the treatment page converts at a significantly higher rate (~15.5% vs ~10.5%). The observed ~5 percentage point lift is practically meaningful for an e-commerce context. The evidence supports implementing the new page.

## Tools & Skills
- **Language:** Python
- **Libraries:** pandas, numpy, matplotlib, statsmodels
- **Techniques:** Descriptive statistics, conditional probability, hypothesis testing, Monte Carlo simulation, logistic regression, dummy variable encoding (`pd.get_dummies`)
- **Concepts:** Null/alternative hypotheses, Type I error rate, p-values, sampling distributions, logistic regression interpretation

## Files
| File | Description |
|------|-------------|
| `Analyze_ab_test_results_notebook.ipynb` | Full notebook with all analysis, visualizations, and written interpretations |
