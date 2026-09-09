# Customer Segmentation Analysis

## Objective
Apply clustering algorithms to segment an e-commerce company's customer base 
into distinct groups based on purchasing behavior, enabling targeted marketing 
strategies.

## Dataset
**Online Retail** dataset (UCI Machine Learning Repository), containing 
transaction-level data for a UK-based online retailer between 2009–2011. 
Original size: ~1,067,371 rows, 8 columns (Invoice, StockCode, Description, 
Quantity, InvoiceDate, Price, Customer ID, Country).

## Data Cleaning
- Dropped rows with missing `Customer ID` (transactions can't be attributed 
  to a customer for segmentation purposes)
- Removed duplicate rows
- Removed cancelled orders (Invoice numbers starting with "C")
- Removed rows with non-positive `Quantity` or `Price` (returns/data errors)
- Final cleaned dataset: 779,425 rows, zero nulls

## Methodology
1. **Feature Engineering (RFM)** :- calculated Recency, Frequency, and Monetary 
   value per customer:
   - Recency: days since each customer's last purchase
   - Frequency: number of unique invoices per customer
   - Monetary: total revenue per customer (Quantity × Price, summed)
2. **Scaling** — standardized RFM features using `StandardScaler` before clustering
3. **Optimal K Selection**  :-used the Elbow Method to evaluate inertia across 
   K=1 to K=10. The inertia curve dropped sharply through K=3 and flattened 
   afterward, so **K=3** was selected.
4. **Clustering** :- applied K-Means (K=3) to the scaled RFM features
5. **Profiling**:- computed mean Recency, Frequency, and Monetary value per 
   cluster to interpret customer segments

## Results

| Cluster | Recency (days) | Frequency (orders) | Monetary (£) | Customer Count |
|---|---|---|---|---|
| 0 | 66.3 | 7.6 | ~3,136 | ~3,800 |
| 1 | 461.9 | 2.2 | ~747 | ~2,000 |
| 2 | 23.1 | 143.0 | ~173,124 | ~20-30 |

**Cluster 0 — Regular Customers:** Moderate recency, frequency, and spend — 
the core, steadily engaged customer base.
**Recommendation:** Loyalty programs and periodic cross-sell campaigns.

**Cluster 1 — At-Risk / Dormant Customers:** High recency (over a year since 
last purchase), low frequency and spend — signs of churn.
**Recommendation:** Low-cost win-back campaigns (discount codes, re-engagement 
emails).

**Cluster 2 — VIP / High-Value Customers:** Very recent, extremely frequent, 
and disproportionately high-spending — a small elite group driving outsized 
revenue.
**Recommendation:** Dedicated account management and exclusive perks; 
retention here has outsized revenue impact.

## Tech Stack
Python, pandas, scikit-learn (KMeans, StandardScaler), matplotlib, seaborn, 
Jupyter Notebook (Google Colab)

## Files
- `Customer_Segmentation.ipynb` full notebook: data cleaning, RFM feature 
  engineering, elbow method, K-Means clustering, cluster visualization and 
  profiling, and marketing recommendations
