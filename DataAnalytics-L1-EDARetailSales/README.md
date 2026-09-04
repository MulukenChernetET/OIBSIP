# EDA on Retail Sales Data

## Objective
Perform exploratory data analysis on a retail sales dataset (Superstore Sales) to uncover patterns in sales trends, customer segments, product performance, and discount/profit relationships, and translate these findings into actionable business recommendations.

## Dataset
Superstore Sales Dataset — 9,994 orders across 21 columns, covering order/ship dates, customer segments, product categories, sales, quantity, discount, and profit.

## Tools Used
Python, pandas, numpy, matplotlib, seaborn, Jupyter Notebook (via Google Colab)

## Key Steps
- Data inspection and cleaning (column names, date conversion)
- Descriptive statistics (mean, median, mode, standard deviation)
- Monthly and quarterly sales trend analysis
- Customer segment analysis (order volume vs. sales value)
- Top 10 best-selling products and category-level revenue
- Correlation heatmap (Sales, Quantity, Discount, Profit)
- Discount vs. Profit scatter plot (non-obvious insight)

## Key Findings
1. Sales grew consistently from 2014-2017, with strong seasonality — dipping in Q1 and peaking in Q3-Q4.
2. The Consumer segment drives the most orders and revenue, followed by Corporate and Home Office, in the same proportion for both metrics.
3. High-value equipment (copiers, binding machines) contributes disproportionately to revenue despite low order frequency.
4. Discounts above ~30-40% are frequently unprofitable, with losses growing sharply at higher discount levels — while discount shows almost no correlation with sales volume.

## Business Recommendations
See the Conclusion section in the notebook for 3 detailed, actionable recommendations based on these findings.
