# D502 Capstone: Magic: The Gathering Card Market Price Analysis

## Overview
This is the capstone project for the Bachelor of Science in Data Analytics program at Western Governors University (D502). It investigates whether a statistically significant correlation exists between a Magic: The Gathering card's converted mana cost (CMC) and its USD secondary market price, using a dataset of over 81,000 cards sourced live from the Scryfall API.

The project follows the **CRISP-DM** methodology across all six phases: Business Understanding, Data Understanding, Data Preparation, Modeling, Evaluation, and Deployment.

---

## Research Question
**Is there a statistically significant correlation between a Magic: The Gathering card's converted mana cost (CMC) and its USD market price?**

---

## Dataset
- **Source:** Scryfall Bulk Data API (`default_cards` file)
- **Collection method:** Programmatic HTTP GET request via Python `requests` library
- **Raw records:** 113,185 card entries (snapshot: April 2, 2026)
- **After cleaning:** 81,558 English-language cards with valid, non-zero USD prices and CMC ≤ 17
- **Price source:** TCGplayer market prices aggregated by Scryfall

---

## Results

| Metric | Value |
|--------|-------|
| Pearson r | −0.0252 |
| P-value | 5.67e-13 |
| Alpha | 0.05 |
| Statistically significant | ✅ Yes |
| Practical significance | ❌ Negligible (r² ≈ 0.06%) |

The null hypothesis was rejected — a statistically significant correlation was found. However, with r = −0.0252, the relationship is effectively meaningless as a predictive tool. CMC accounts for only 0.06% of the variance in card prices, meaning **mana cost should not be used as a pricing signal** in the MTG secondary market.

**Median price by rarity:**
| Rarity | Median Price | n |
|--------|-------------|---|
| Common | $0.15 | 26,728 |
| Uncommon | $0.23 | 21,202 |
| Rare | $0.74 | 27,603 |
| Mythic | $3.59 | 5,776 |

Rarity showed a far more meaningful relationship with price than CMC, consistent with existing literature on MTG secondary market pricing.

---

## Visualizations
- **Scatter plot:** CMC vs. USD market price (log scale) with trend line overlay and Pearson statistics in the title
- **Bar chart:** Median USD price by rarity tier (Common → Uncommon → Rare → Mythic)

---

## Tools & Skills
- **Language:** Python
- **Environment:** Google Colab
- **Libraries:** `requests`, `pandas`, `numpy`, `matplotlib`, `scipy.stats`
- **Techniques:** API data retrieval, JSON parsing, data cleaning and filtering, Pearson correlation test, log-scale visualization, statistical significance vs. practical significance interpretation
- **Methodology:** CRISP-DM

---

## Files
| File | Description |
|------|-------------|
| `panopto_capstone.ipynb` | Google Colab notebook with full code, outputs, and visualizations |
| `D502_Task3_Capstone_Report.docx` | Full written capstone report including methodology, results, and recommendations |
