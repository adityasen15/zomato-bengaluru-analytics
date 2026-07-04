# Bengaluru Restaurant Analytics — A Zomato Data Study

An end-to-end data analytics project analyzing **51,717 Zomato restaurant listings across Bengaluru**, exploring how locality, cuisine, pricing, and platform features (online ordering, table booking) shape customer ratings and engagement — with the analysis translated into concrete recommendations for pricing, expansion, marketing, and restaurant partnerships.

> Built as a portfolio project demonstrating a complete Data Analyst workflow: data cleaning, EDA, statistical hypothesis testing, business Q&A, and dashboard-ready outputs.

---

## Project Overview

Zomato's Bengaluru restaurant market is large, competitive, and highly heterogeneous. This project asks — and answers with real numbers — the kind of questions a Zomato analytics or strategy team would actually be asked:

- Which restaurant segments, localities, and service strategies most reliably predict customer satisfaction?
- Does online ordering or table booking actually move the needle on ratings — and if so, by how much, and is it statistically real?
- Where should Zomato prioritize restaurant partner expansion, and where is the market already oversaturated?

**33 business questions answered** · **3 formal hypothesis tests** · **17 visualizations** · **Full data cleaning pipeline with documented reasoning at every step**

### Headline findings
| Finding | Detail |
|---|---|
| Table booking is the strongest quality signal | +0.52 rating points (95% CI [0.51, 0.53], p < 0.001) |
| Online ordering has a real but small effect | +0.06 rating points (p < 0.001) — an engagement booster, not a quality driver |
| Price only matters meaningfully at Premium tier | Premium 3.99 vs Budget 3.56 / Mid-range 3.62 |
| Zomato's biggest segment is its weakest-rated | "Delivery" listings: 25,858 rows (largest category), 3.65 avg rating (lowest) |
| Chain scale ≠ chain quality | Cafe Coffee Day: widest footprint (34 localities), lowest rating (3.26) of major chains |

---

## Tech Stack

- **Python** — Pandas, NumPy (data cleaning, feature engineering, aggregation)
- **Matplotlib, Seaborn** — visualization (histograms, boxplots, violin plots, scatter plots, heatmaps, pairplots)
- **SciPy** — statistical testing (Pearson correlation, Shapiro-Wilk normality test, Welch's t-test, one-way ANOVA)
- **Jupyter Notebook** — primary deliverable format
- **Power BI** *(recreation guide included, not built here)* — for an interactive, stakeholder-facing dashboard version

---

## Dataset

- **Source:** Zomato Bengaluru restaurant listings (public dataset, originally scraped from Zomato's website).
- **Size:** 51,717 raw rows × 11 columns → 51,588 rows after cleaning (99.75% retained).
- **Columns:** `name`, `online_order`, `book_table`, `rate`, `votes`, `location`, `rest_type`, `cuisines`, `approx_cost(for two people)`, `listed_in(type)`, `listed_in(city)`.
- **Granularity:** one row = one restaurant × one Zomato listing category (a restaurant can have multiple rows if listed under multiple categories, e.g. both "Delivery" and "Dine-out").
- **Note:** this dataset covers Bengaluru only — `location`/`listed_in(city)` represent neighborhoods/zones within the city, not separate Indian cities.

Full data dictionary and known data-quality issues are documented in Section 4/5 of the notebook.

---

## Installation

```bash
# Clone the repository
git clone <your-repo-url>
cd zomato-bengaluru-analytics

# Install dependencies
pip install pandas numpy matplotlib seaborn scipy jupyter

# Launch the notebook
jupyter notebook notebooks/Zomato_Bengaluru_Analytics.ipynb
```

**Requirements:** Python 3.9+, ~50MB disk space for the dataset and generated charts.

### Project structure
```
zomato-bengaluru-analytics/
├── data/
│   ├── zomato_raw.csv          # original dataset
│   └── zomato_clean.csv        # cleaned, feature-engineered dataset
├── notebooks/
│   └── Zomato_Bengaluru_Analytics.ipynb   # full analysis notebook
├── outputs/
│   └── *.png                   # 17 exported charts
├── README.md
```

---

## Results

The notebook is organized into 15 sections following a full analytics lifecycle:

1. Introduction & Business Problem
2. Objectives, Dataset Description, Data Dictionary
3. Questions to Answer (33 business questions)
4. Data Cleaning (missing values, duplicates, datatypes, outliers, inconsistent categories, feature engineering, validation)
5. Exploratory Data Analysis (17 visualizations across ratings, votes, cost, delivery, booking, locality, cuisine, chains)
6. Business Questions — full answers
7. Statistical Analysis (correlation testing, normality testing, hypothesis testing, confidence intervals)
8. Dashboard Preparation (KPI definitions + Power BI recreation guide)
9. Code Quality Notes
10. Insights — consolidated summary
11. Final Recommendations (pricing, expansion, marketing, satisfaction, partnerships)
12. Conclusion

See the notebook for full charts, code, and detailed interpretation after every analysis step.

---

## Screenshots

*(Add rendered notebook screenshots or exported chart images here once finalized — suggested: the locality opportunity map, the correlation heatmap, and the feature-combination rating chart make strong portfolio thumbnails.)*

```
outputs/22_expansion_opportunity_map.png
outputs/18_correlation_heatmap.png
outputs/23_feature_combination.png
```

---

## Future Improvements

- **Rebuild the Power BI dashboard** described in Section 11 as an actual `.pbix` file with live slicers and cross-filtering.
- **Add a time dimension.** This dataset is a single snapshot — a scraped monthly series would enable trend analysis (is a locality's rating improving or declining over time?).
- **Incorporate review text.** The original raw dataset includes a `reviews_list` column (excluded here for size/scope) — NLP sentiment analysis on review text could validate or deepen the numeric-rating findings.
- **Causal analysis.** Current findings are correlational; a matched-comparison or regression-with-controls approach could better isolate the true causal effect of table booking vs. its correlation with being a premium restaurant in the first place.
- **Geospatial mapping.** Plotting `location` on an actual Bengaluru map (via lat/long geocoding) would make the expansion/oversaturation findings far more visually compelling for a stakeholder audience.

---

## Author

*(Your Name)* — Data Analyst / Business Analyst portfolio project. Feel free to reach out with questions or feedback on this analysis.
