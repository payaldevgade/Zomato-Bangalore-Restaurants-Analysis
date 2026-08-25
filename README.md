# Zomato Bangalore Restaurant Analysis

Exploratory data analysis of Bangalore restaurant listings from Zomato, built with
**Python, NumPy, Pandas, Matplotlib, Seaborn, and Plotly** — cleaning, KPIs, and business
insights, no ML.

## Project Overview

This project analyzes `zomato.csv`, a dataset of Bangalore restaurants, to understand:

- Where restaurants are concentrated across the city
- Which restaurant types and cuisines are most common
- How online ordering and table booking relate to ratings and pricing
- Which restaurants and locations perform best, once vote count and sample size are
  accounted for
- What this means for restaurant owners and the platform

## Business Questions

1. Which areas of Bangalore have the most restaurants?
2. Which restaurant types are most common?
3. What percentage of restaurants accept online orders / offer table booking?
4. Does online ordering relate to restaurant ratings?
5. Does table booking relate to restaurant price and ratings?
6. Does higher price lead to higher ratings?
7. Which cuisines are most popular, and which are highest-rated?
8. Which restaurants are most popular based on votes?
9. Which locations have the best-rated restaurants?
10. Which locations look promising for expansion, and which need more investigation?

## Repository Structure

```
├── Zomato_Bangalore_Analysis.ipynb   # Main analysis notebook
├── zomato.csv                        # Dataset 
└── README.md
```

## Tech Stack

| Tool | Purpose |
|---|---|
| **NumPy** | Numerical operations, binning, derived metrics |
| **Pandas** | Data loading, cleaning, grouping, aggregation |
| **Matplotlib / Seaborn** | Static statistical visualizations |
| **Plotly** | Interactive charts and KPI dashboard |

## Data Cleaning

The raw dataset required several cleaning steps before analysis:

- **Malformed rows** — some rows had values shifted into the wrong columns (e.g. rating
  text like `"Rated 4.0"` appearing in `online_order`/`book_table`); these were filtered out.
- **Duplicates** — exact duplicate rows were identified and removed.
- **`rate`** — converted from strings like `"4.1/5"` / `"NEW"` / `"-"` into numeric values.
- **`votes`** — coerced to numeric.
- **`approx_cost(for two people)`** — stripped thousands-separator commas and converted to
  numeric.
- **`online_order` / `book_table`** — mapped to 0/1 flags for numeric analysis.
- **Missing values** — numeric columns filled with the median; categorical columns filled
  with `"Unknown"`.

## 📈 Analysis Sections

1. Data Understanding
2. Data Cleaning
3. KPI Dashboard (total restaurants, average rating, online order %, table booking %, etc.)
4. Univariate Analysis (ratings, locations, restaurant types, cost, cuisines)
5. Bivariate Analysis (cost vs rating, votes vs rating, online order vs rating, table
   booking vs cost/rating)
6. Correlation Analysis
7. Price Segment Analysis (Budget → Luxury)
8. Location Analysis + a custom exploratory "opportunity score"
9. Cuisine Analysis
10. Restaurant Popularity Analysis (vote-adjusted)
11. Interactive Plotly Visualizations
12. Key Findings
13. Business Recommendations

## 💡 Key Findings

**KPI Summary (from the cleaned dataset):**

| KPI | Value |
|---|---|
| Total Restaurants | 36,402 |
| Average Rating | 3.73 / 5 |
| Total Votes | 11,258,976 |
| Average Cost for Two | Rs. 574.85 |
| Online Order % | 60.23% |
| Table Booking % | 13.92% |
| Number of Locations | 94 |
| Most Common Restaurant Type | Quick Bites |

**Observations:**

- After removing malformed rows and duplicates, **36,402** restaurant records remain for
  analysis, spread across **94** locations.
- **Quick Bites** is the most common restaurant type — the market leans toward casual,
  fast-turnaround dining rather than fine dining.
- **60.23%** of restaurants accept online orders, but only **13.92%** offer table booking —
  table booking is a much rarer, more premium feature.
- Restaurants offering **table booking** show notably higher average ratings and cost,
  suggesting they skew toward premium/fine-dining establishments.
- Restaurants with **online ordering** show a slightly higher average rating than those
  without — an association, not a proven cause.
- **Cost** and **votes** both show a modest positive correlation with rating.
- A handful of central locations (e.g. Koramangala, Indiranagar, BTM, HSR Layout) account
  for a large share of restaurants but also face the most competition.

## 💼 Business Recommendations

1. Improve digital ordering adoption for restaurants that lack it.
2. Focus on service quality and experience in the premium/table-booking segment.
3. Treat high-density locations as high-competition, not automatically high-opportunity.
4. Investigate high-rating, lower-density locations as possible expansion areas.
5. Use popular/highly-rated cuisine combinations to inform menu strategy.
6. Evaluate restaurant performance using rating **and** votes together, not rating alone.

## 🚀 How to Run

1. Clone this repo and place `zomato.csv` in the project root.
2. Install dependencies:
   ```bash
   pip install numpy pandas matplotlib seaborn plotly jupyter
   ```
3. Launch the notebook:
   ```bash
   jupyter notebook Zomato_Bangalore_Analysis.ipynb
   ```
4. Run all cells top to bottom.

## 🔭 Next Steps

This project intentionally stays within NumPy/Pandas/Matplotlib/Seaborn/Plotly and doesn't
use machine learning. A natural follow-up project would use `scikit-learn` on this same
cleaned dataset to predict restaurant ratings or classify restaurant success.

## 📄 License

Feel free to use or adapt this project for learning purposes.
