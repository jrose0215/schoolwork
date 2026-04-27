# Unsupervised Learning: Identifying Customer Segments

## Overview
Applied unsupervised learning techniques to demographic data from Germany to identify which population segments are over- and under-represented in a mail-order company's customer base. The analysis uses PCA for dimensionality reduction and K-Means clustering to surface meaningful customer profiles from nearly 900,000 general population records.

## Research Question
**Which demographic segments of the German population are most and least likely to be customers of a mail-order sales company?**

## Datasets
- `Udacity_AZDIAS_Subset.csv` — German general population demographics (891,211 rows × 85 features)
- `Udacity_CUSTOMERS_Subset.csv` — Mail-order company customer demographics (191,652 rows × 85 features)
- `AZDIAS_Feature_Summary.csv` — Feature metadata including data types and missing value codes

Data provided by Bertelsmann Arvato Analytics.

## Project Workflow

### 1. Preprocessing
- Converted custom missing/unknown codes to NaN using the feature summary file
- Removed columns with >20% missing data (high-missing outliers identified via histogram)
- Split rows into low-missing (≤10 missing values) and high-missing (>10) subsets; retained the low-missing subset
- Re-encoded categorical features: binary variables kept as-is, non-numeric binary re-encoded, multi-level categoricals one-hot encoded
- Engineered mixed-type features and dropped columns not suitable for analysis
- Imputed remaining missing values using column medians

### 2. Dimensionality Reduction (PCA)
- Scaled features using StandardScaler before applying PCA
- Selected 20 principal components, capturing ~78% of total variance
- Interpreted top components:
  - **PC1:** Urbanization & Wealth (rural/lower-income vs. urban/higher-income)
  - **PC2:** Life stage / family orientation
  - **PC3:** Financial conservatism

### 3. Clustering (K-Means)
- Tested k=2 through k=15; used elbow plot of inertia scores to select **k=10**
- Applied the same preprocessing, PCA transformation, and cluster model fitted on the general population to the customer dataset

### 4. Comparing Segments
Compared cluster proportions between general population and customers to identify target and non-target segments:

- **Most overrepresented (Cluster 2 — 4.49x):** Urban, wealthy, family-oriented individuals with a traditional outlook — the core customer profile
- **Most underrepresented (Cluster 1 — 0.12x):** Rural, lower-income individuals — least likely to be customers

## Tools & Skills
- **Language:** Python
- **Libraries:** pandas, numpy, matplotlib, seaborn, scikit-learn
- **Techniques:** Missing data assessment (column and row level), feature re-encoding, median imputation, StandardScaler, PCA, elbow method, K-Means clustering, cluster comparison
- **Concepts:** Dimensionality reduction, unsupervised segmentation, customer profiling

## Files
| File | Description |
|------|-------------|
| `Identify_Customer_Segments.ipynb` | Full notebook with preprocessing, PCA, clustering, and segment interpretation |
