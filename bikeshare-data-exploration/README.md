# Bikeshare Data Exploration

## Overview
Exploratory data analysis of bikeshare trip data from three U.S. cities — **New York City**, **Chicago**, and **Washington, DC** — using R in a Jupyter Notebook environment. This project was completed as part of a data analysis course and focuses on asking and answering meaningful questions from real-world transportation data.

## Questions Explored

**Q1: What hour of the day has the highest number of bike trips?**  
Peak trip hours differ by city. New York City and Chicago both peak at **5 PM (17:00)**, reflecting evening commute patterns. Washington, DC peaks at **8 AM**, suggesting a stronger morning commute trend. One Washington record with an invalid start time was identified and excluded from the analysis.

**Q2: What are the most commonly used start stations in each city?**  
Identified the top start stations per city by aggregating trip counts, revealing location-specific usage patterns across the three markets.

**Q3: How does trip duration differ between cities?**  
Washington, DC has a notably higher mean trip duration compared to New York and Chicago, while median durations are more similar across all three cities. The gap between mean and median in all cities indicates right-skewed distributions driven by a smaller number of unusually long rides.

## Tools & Skills
- **Language:** R
- **Environment:** Jupyter Notebook (R kernel)
- **Techniques:** Data loading and inspection, feature engineering (extracting hour from datetime), frequency aggregation, summary statistics (mean, median), comparative analysis across datasets
- **Data:** CSV files containing trip start/end times, station names, trip duration, user type, and (for NYC and Chicago) gender and birth year

## Files
| File | Description |
|------|-------------|
| `Explore_bikeshare_data.html` | Rendered notebook with full code, outputs, and written summaries |

## Key Takeaways
- Commute patterns vary meaningfully by city — a single national narrative doesn't hold
- Mean trip duration can be misleading without also examining the median, especially in right-skewed data
- Cleaning and validating datetime fields is a necessary step before any time-based analysis
