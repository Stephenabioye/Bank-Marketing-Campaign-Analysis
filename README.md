# Bank Marketing Campaign Analysis — Business Analytics Case Study

## Overview
A full business analytics case study built in **Power BI**, analyzing 11,162 customer records from a Portuguese banking institution's direct marketing campaign. The goal was to identify why some customers subscribe to term deposits while others do not, and to deliver actionable recommendations to improve future campaign conversion rates.

This project was completed as **Week 5** of the AnalystLab Africa Data Analytics Internship Programme (2026).

## Business Problem
> *"Why do some customers subscribe to term deposits while others do not — and which customer segments should the bank prioritise to maximise conversion and reduce wasted campaign spend?"*

## Tools Used
- Microsoft Power BI (data modeling, DAX measures, dashboard design)
- Power Query (data transformation and feature engineering)

## Dataset
| Field | Details |
|---|---|
| Source | Bank Marketing Dataset (Kaggle) |
| Rows | 11,162 customer records |
| Columns | 17 variables |
| Target Variable | `deposit` (yes = subscribed, no = did not subscribe) |
| Missing Values | Zero — clean dataset |
| Key Fields | Age, Job, Education, Marital Status, Balance, Contact Method, Call Duration, Month, Previous Campaign Outcome, Housing Loan, Personal Loan |

## Data Preparation Steps
- Created `Age Group` column from `age` field (Under 25, 25–34, 35–44, 45–54, 55–64, 65+)
- Created `Age Sort` column for correct age group ordering in charts
- Created `Month Number` column from `month` field for correct month ordering
- Sorted `Age Group` by `Age Sort` and `month` by `Month Number` in Data View
- Created all KPI measures using DAX in Power BI

## Key Metrics (KPI Cards)
| Metric | Value |
|---|---|
| Total Customers Contacted | 11,162 |
| Total Subscriptions | 5,289 |
| Overall Conversion Rate | 47.4% |
| Avg Call Duration (Subscribers) | 537 seconds |
| Avg Call Duration (Non-Subscribers) | 223 seconds |
| Avg Balance (Subscribers) | $1,804 |

## DAX Measures Created
```
Total Customers = COUNTROWS('bank')

Total Subscriptions = COUNTROWS(FILTER('bank', 'bank'[deposit] = "yes"))

Conversion Rate % = DIVIDE(
    COUNTROWS(FILTER('bank', 'bank'[deposit] = "yes")),
    COUNTROWS('bank')
) * 100

Avg Duration Subscribers = CALCULATE(AVERAGE('bank'[duration]), 'bank'[deposit] = "yes")

Avg Duration Non-Subscribers = CALCULATE(AVERAGE('bank'[duration]), 'bank'[deposit] = "no")

Avg Balance Subscribers = CALCULATE(AVERAGE('bank'[balance]), 'bank'[deposit] = "yes")
```

## Key Insights

### 1. Previous Campaign Success is the Strongest Predictor
Customers who subscribed in a previous campaign re-convert at **91.3%** — nearly guaranteed. This group must be the first priority in every future campaign.

### 2. Students and Retirees Are High-Value Underserved Segments
Students convert at **74.7%** and retired customers at **66.3%** — both far above the 47.4% average. These segments likely receive less campaign attention than lower-converting groups like blue-collar workers (36.4%).

### 3. U-Shaped Age Pattern
Customers under 25 (73.4%) and over 65 (80.2%) convert best. Middle-aged customers (35–54) are the hardest segment to convert at approximately 41%.

### 4. Campaign Timing is Poorly Optimised
December (90.9%), March (89.9%), September (84.3%), and October (82.4%) deliver the highest conversion rates. May — likely the heaviest campaign month — delivers only **32.8%**.

### 5. Longer Calls = More Subscriptions
Subscribers averaged **537 seconds** on calls vs 223 seconds for non-subscribers. Agent engagement quality is a direct and controllable conversion lever.

### 6. Debt Burden Reduces Conversion
Customers with housing loans convert at 36.6% vs 57.0% for debt-free customers. Existing financial obligations are a measurable barrier to term deposit subscription.

## Business Recommendations

| # | Recommendation | Priority |
|---|---|---|
| 1 | Build a priority re-engagement list targeting previous subscribers first | HIGH |
| 2 | Shift campaign budgets to March, September, October, and December | HIGH |
| 3 | Create tailored campaigns for student and retired segments | HIGH |
| 4 | Train agents to extend call duration and build genuine rapport | MED |
| 5 | Improve CRM data quality — require valid cellular numbers before campaigning | MED |
| 6 | De-prioritise customers with both housing and personal loans | MED |

## Dashboard Visuals
- KPI Cards — Total Customers, Subscriptions, Conversion Rate, Avg Call Duration, Avg Balance
- Pie Chart — Overall Subscription Split (Subscribed vs Not Subscribed)
- Bar Chart — Conversion Rate by Job Type
- Column Chart — Conversion Rate by Age Group
- Bar Chart — Conversion Rate by Education Level
- Bar Chart — Conversion Rate by Contact Method
- Bar Chart — Conversion Rate by Previous Campaign Outcome
- Line Chart — Conversion Rate by Month
- Bar Chart — Avg Call Duration by Outcome
- Bar Chart — Conversion Rate by Housing and Personal Loan Status
- Slicers — Deposit, Job, Education, Age Group, Month

## Project Files
| File | Description |
|---|---|
| `bank.csv` | Raw dataset |
| `BankMarketing_Dashboard.pbix` | Power BI dashboard file |
| `BankMarketing_CaseStudy_Report.docx` | Full business analytics report |
| `BankMarketing_Presentation.pptx` | Presentation slides |

## About
This project was completed as part of a **Data Analytics Internship at AnalystLab Africa (2026)** — Week 5: Business Analytics Case Study. It demonstrates skills in exploratory data analysis, conversion rate analysis, DAX measure creation, business insight generation, and actionable recommendation writing.

**Portfolio:** [github.com/Stephenabioye](https://github.com/Stephenabioye)
