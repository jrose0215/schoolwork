# Real-World Data Wrangling: School Neighborhood Poverty Analysis

## Overview
A full data wrangling pipeline applied to two real-world datasets from the U.S. Department of Education, available on data.gov. The project gathers, assesses, cleans, and combines the data to answer a research question about how neighborhood poverty levels vary across public schools in the United States.

## Research Question
**How do neighborhood poverty levels vary across public schools and geographic areas in the United States?**

## Datasets
| Dataset | Source | Gathering Method |
|---------|--------|-----------------|
| School Neighborhood Poverty Estimates | U.S. Dept. of Education (data.gov) | Manual download (CSV) |
| Public School Locations | U.S. Dept. of Education (data.gov) | Programmatic download via pandas |

Both datasets were joined on the NCES school identifier (`NCESSCH` / `School ID`).

## Project Workflow

### 1. Gather
Retrieved both datasets using two distinct methods — manual CSV download and programmatic loading via URL — and saved raw versions before any modifications.

### 2. Assess
Identified four data issues across quality and tidiness dimensions:

- **Quality Issue 1:** Misaligned reporting years across datasets (poverty data: 2021–22, locations data: 2022–23) — single-value columns with no analytical value
- **Quality Issue 2:** Redundant geographic coordinate columns (`LAT/LON` and `X/Y`) representing identical location data with only floating-point precision differences
- **Tidiness Issue 1:** Inconsistent column naming conventions between datasets (e.g., `School ID` vs `NCESSCH`, mixed case and spacing)
- **Tidiness Issue 2:** Non-essential administrative and system-generated columns (`OBJECTID`, `CBSA`, `NECTA`, etc.) cluttering both datasets

### 3. Clean
Applied targeted cleaning for each issue: dropped misaligned year fields, removed redundant coordinate columns, standardized all column names to lowercase with underscores, and eliminated administrative metadata columns. Raw and cleaned versions were preserved separately.

### 4. Combine & Store
Merged the two cleaned datasets on the NCES school ID, producing a unified dataset with school identity, geographic location, locale classification, and neighborhood poverty estimate. Raw and cleaned CSVs were saved with informative filenames.

### 5. Analyze & Visualize
- **Bar chart:** Average neighborhood income-to-poverty ratio (IPR) by state — reveals substantial geographic variation in school neighborhood poverty across the U.S.
- **Box plot:** IPR distribution by NCES locale code (urban, suburban, town, rural) — shows that community type is meaningfully associated with neighborhood poverty levels

## Tools & Skills
- **Language:** Python
- **Libraries:** pandas, matplotlib
- **Techniques:** Multi-source data gathering, data quality assessment (visual and programmatic), data cleaning, dataset merging (`pd.merge`), grouped aggregation, data visualization
- **Concepts:** Tidy data principles, raw vs. cleaned data versioning, research question framing

## Files
| File | Description |
|------|-------------|
| `Data_Wrangling_Project.ipynb` | Full notebook with code, assessments, cleaning steps, and visualizations |
