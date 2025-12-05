Executive Financial Performance Dashboard (Power BI)

Role Focus: Power BI Developer
Tools: Power BI, Power Query, DAX, SQL
Concepts: Time Intelligence, Star Schema Modeling, KPI Frameworks, RLS, Performance Optimization

📌 Business Problem

Executive leadership needed a unified financial reporting dashboard to replace multiple Excel files stored across teams.
They wanted:

Revenue, expenses, and profit KPIs

Actual vs Budget comparisons

YoY performance

Region & department breakdowns

Dynamic drillthrough navigation

Secure access (RLS)

The Power BI dashboard replaces manual consolidation and enables real-time financial insights.

📊 Data Model (Star Schema)
                DimAccount
                    ▲
                    │
DimBusiness ─── FactFinance ─── DimDate
    ▲               │              ▲
    │               ▼              │
DimRegion       DimDepartment    DimScenario


FactFinance:

RevenueAmount

ExpenseAmount

BudgetAmount

DateKey

AccountKey

DepartmentKey

RegionKey

📈 KPIs
KPI	Description
Total Revenue	SUM(RevenueAmount)
Total Expenses	SUM(ExpenseAmount)
Profit	Revenue – Expenses
Gross Margin %	Profit ÷ Revenue
Budget Variance	Actual – Budget
YoY Growth %	(Current – Last Year) ÷ Last Year
🧮 Sample DAX Measures
Total Revenue =
SUM(FactFinance[RevenueAmount])

Total Expense =
SUM(FactFinance[ExpenseAmount])

Profit =
[Total Revenue] - [Total Expense]

Gross Margin % =
DIVIDE([Profit], [Total Revenue])

Revenue LY =
CALCULATE([Total Revenue], DATEADD(DimDate[Date], -1, YEAR))

Revenue YoY % =
DIVIDE([Total Revenue] - [Revenue LY], [Revenue LY])

📌 Dashboard Features
✔ Executive Summary View

KPI cards (Revenue, Expenses, Margin)

Trend line visuals for Current vs LY

Budget variance bar charts

✔ P&L Breakdown

Account category hierarchy

Drillthrough to row-level account detail

✔ Region & Department Insights

Heatmaps for performance by location

Filters for scenario: Actual, Budget, Forecast

✔ Security (RLS)

Business unit managers see ONLY their department

Executives see all data

✔ Performance Optimization

Reduced refresh time by 35%

DAX optimization with variables

Aggregated fact table for faster visuals

🎯 Business Impact

Reduced manual Excel reporting by 40%

Improved accuracy of financial reporting

Enabled leaders to make decisions 2–3x faster

Increased monthly reporting efficiency by 30%

📁 Downloadables (Placeholder)

📌 Executive_Financial_Dashboard.pbix
📌 Financial_Dataset.xlsx
