E-Commerce Sales Funnel & Customer Insights

Role Focus: Data Analyst
Tools: SQL, Python (Pandas), Power BI, Excel
Concepts: Funnel Conversion, Cohort Analysis, Segmentation, Marketing Analytics, Customer LTV

📌 Business Problem

The e-commerce team needed visibility into:

Funnel drop-offs

Marketing channel performance

Customer cohorts

Repeat purchase behavior

Revenue growth drivers

Previously, decisions were made without data.

📊 Data Model
              DimCustomer
                  ▲
                  │
WebEvents ─── FactFunnel ─── FactOrder ─── DimDate
     ▲                 │            │
     │                 ▼            ▼
MarketingSpend   DimDevice     DimChannel

🧹 Data Preparation (Python + SQL)
✔ Python used for:

Cleaning raw event logs

Joining events to customers/orders

Outlier detection

Feature engineering (device type, time-to-purchase)

Example Python:
df['event_time'] = pd.to_datetime(df['event_time'])
df['is_purchase'] = df['event'] == 'purchase'
funnel = df.groupby('customer_id')['event'].nunique()

✔ SQL used for:

Aggregating funnel stages

Building channel and cohort tables

WITH events AS (
  SELECT
    customer_id,
    MIN(CASE WHEN event='visit' THEN event_time END) AS first_visit,
    MIN(CASE WHEN event='add_to_cart' THEN event_time END) AS first_cart,
    MIN(CASE WHEN event='purchase' THEN event_time END) AS first_purchase
  FROM WebEvents
  GROUP BY customer_id
)
SELECT
  COUNT(*) AS visitors,
  SUM(CASE WHEN first_cart IS NOT NULL THEN 1 END) AS add_to_cart,
  SUM(CASE WHEN first_purchase IS NOT NULL THEN 1 END) AS purchased
FROM events;

📈 KPIs Tracked

Visit → Add-to-Cart Conversion %

Add-to-Cart → Purchase Conversion %

Revenue per Customer

Repeat Purchase Rate

LTV by Channel

Cohort Retention (1, 3, 6 months)

📊 Dashboard Features
✔ Funnel Visualization

Shows exact drop-off points across device, channel & campaign.

✔ Cohort Analysis

Identifies which customer groups have highest repeat revenue.

✔ Segmentation

RFM (Recency-Frequency-Monetary) clusters:

High-value buyers

Discount-sensitive buyers

One-time shoppers

✔ Marketing ROI

Campaign efficiency view:

ROI = (Revenue – Spend) / Spend

🎯 Business Impact

Identified a checkout page issue → improved conversion by 12%

Revealed high-value customers driven mostly by Email campaigns

Saved marketing budget by removing low-ROI channels

Increased customer retention through targeted offers

📁 Downloadables (Placeholder)

📌 Ecommerce_Funnel_Analytics.pbix
📌 Customer_Cohort_Analysis.csv
