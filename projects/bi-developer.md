Operational BI & ETL Analytics for Insurance

Role Focus: BI Developer / Business Intelligence
Tools: SQL Server, SSIS, Azure Data Factory, Power BI, SSRS
Concepts: ETL Pipelines, Dimensional Modeling, Data Quality, SCD Type 2, Operational Reporting

📌 Business Problem

The insurance company needed a unified BI framework to analyze:

Policy lifecycle

Claims performance

Broker productivity

Customer segments

But data came from multiple operational systems (Policy Admin, Claims, CRM) and required a robust ETL process.

The goal was to create:

A clean staging layer

Transformed integration layer

A dimensional warehouse

Power BI & SSRS reports

🏗️ BI Architecture Overview
 Source Systems  →  Staging  →  Integration  →  Data Warehouse  →  Power BI & SSRS
(Policy/Claims)      (Raw)      (Cleaned)         (Star Schema)       (Reports)

📊 Dimensional Model (Example)
               DimCustomer
                   ▲
                   │
DimBroker ─── FactPolicy ─── DimProduct
                   │
                   ▼
               FactClaim ─── DimClaimType ─── DimDate

🛠️ ETL Highlights
✔ Staging Layer

Loaded via SSIS/ADF Copy activities

Maintains 1:1 raw structure

Includes audit columns (LoadDate, SourceFile, BatchID)

✔ Integration Layer

Standardized IDs & reference data

Cleans nulls, trims strings, fixes data types

✔ SCD Type 2 Dimensions

Applied to:

Customer

Broker

Policy

Tracks historical changes over time.

🧮 Example SQL Transformations
Policy Duration Calculation
SELECT
    PolicyNumber,
    DATEDIFF(DAY, InceptionDate, ExpiryDate) AS PolicyDurationDays,
    CASE
        WHEN DATEDIFF(DAY, InceptionDate, ExpiryDate) <= 365 THEN 'Short Term'
        WHEN DATEDIFF(DAY, InceptionDate, ExpiryDate) <= 730 THEN 'Medium Term'
        ELSE 'Long Term'
    END AS DurationBand
FROM Integration.Policy;

📌 Reporting Outputs
✔ SSRS (Operational)

Daily Policy Register

Claims Exception Reports

Broker Performance Lists

✔ Power BI (Analytical)

Premium Trends

Loss Ratio Insights

Claims Volume by Region

Broker Sales Rankings

🎯 Business Impact

Reduced manual reconciliation by 50%

Improved underwriting visibility

Enabled leadership to track loss ratios in real-time

Centralized BI ecosystem across departments

📁 Downloadables (Placeholder)

📌 Insurance_ETL_Flow.dtsx
📌 Operational_Analytics_Dashboard.pbix
