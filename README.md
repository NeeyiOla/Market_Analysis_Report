# Market Analysis Report for National Clothing Chain

!-- Attached the Overhead Picture before Table of Content

# [Table of Content
- [Project Title](#Project_Title)
- [My Role](#My_Role)
- [Project Overview](#Project_Overview)
- [Problem Statement](#Problem_Statement)
- [Stakeholder Engagement](#Stakeholder_Engagement)
  - [Targetd Stakeholder](#Targeted_Stakeholder)
  - [Use Cases](#Uses_Cases)
  - [Stakeholder Stories](#Stakeholder_Stories)
  - [Acceptance Criteria](#Acceptance_Criteria)
  - [Success Criteria](#Success_Criteria)
- [Data Source](#Data_Source)
  - [Dataset](#Dataset)
  - [Data Model Structure](#Data_Model_Structure)
- [Methodology](#Methodology)
  - [Tools Used](#Tools_Used)
  - [Development](#Development)
    - [ETL Process](#ETL_Process)
    - [Project Planning & Requirement](#Project_Planning_&_Reqquirement)
    - [Data Exploration & Profiling](#Data_Exploration_&_Profiling)
    - [ETL with Power Query & Data Modelling](#ETL_with_Power_Query_&_Data_Modelling)
    - [Measures & Calculations](#Measures_&_Calculations)
    - [Dashboard Design & Visualisation (3 Dashboards)](#Dashboard_Design_&_Visualisation_(3_Dashboards))
    - [Polishing_&_Collaboration](#Polishing_&_Collaboration)
    - [Documentation & Version Control](#Documentation_&_Version_Comtrol)
    - [Review & Iteration](#Review_&_Iteration)
- [Detailed Insights & Recommendation](#Detailed_Insights_&_Recommendation)
  - [Dashboard 1 - Income Distribution& Geography](#Dashboard_1_-_Income_Distribution_&_Geography)
  - [Dashboard 2 - Avg_Purchase_to_Avg_Income_(Regression)](#Dashboard_2_-_Avg_Purchase_to_Avg_Income_(Regression))
  - [Dashboard 3 - Population to Total Purchases (Regression)](#Dashboard_3_-_Population_to_Total_Purchases_(Regression))
- [Stakeholder_Summary](#Stakeholder_Sumamery)
- [Data Governance, Assumption & Risks](#Data_Governanc,_Assumptions_&_Risk)

# Project Title
Market Analysis & Targeted Product Recommendations for a National Clothing Chain

# My Role
**Market & Business Intelligence Analyst (Marketing Analyst)**
- Led the end-to-end marketing analysis, regression modelling, and scenario forecasting.
- Built the Power Bi data model, DAX measures, decision rules, and executives dashboards
- Partnered with CRM for audience activation and with **Merchandising** for inventory alignment.

# Project Overview 
This project converts raw purchase and census data into an **actionable target map** We:
1. Model **Income to Purchasing** at state grain to produce a transparent linear model.
2. Predict **Customer-level income using recent purchases, segment customers into **income bins**, and map bins to **recommended products**
3. Validate promotion risk using **Customer Rating to Return Rate** correlation.
4. Provide **scenario planning (what-if targets, response, margin, return rates) for **forecasting revenue**, **ROI and profit**

# Problem Statement
Sales have stagnated and lapsed customers are difficult to re-engage without **precise targeting**. The business needs to know needs to know which product each customer is most likely to buy and where to focus media so that spend converts onto incremental profit.

# Stakeholder Engagement

## Targeted Stakeholder
Decision makers and operators who convert analytics into **campaigns**, **inventory plans**, and **budget allocations**.

- **CMO/VP Growth** - Owns budget & KPIs; approves targeting/cereatives.
- **Head of CRM & Lifecycle** - Activates segments in ESP & paid social.
- **Merchandising/Supply** - Aligns stocks/fulfilment with forecasted demand.
- **E-commerce PM** Onsites personalisation, landing pages.
- **Finance** Validates ROI assumptions, approves profit model.

## Use Cases
- **Targetiing**: Export list of customers with **Predicted Incomes Bin** and **Recommended Product**.
- **Geo Prioritisation**: Rank **states/regions by income potential & purchase propensity.
- **Forecasting**: Use what-if control to plan **expected orders**, **revenue**, **returns**, and **profit**
- **Quality Gate**: Suppress products with high Return Rate given a rating threshold.

## Stakeholders Stories

- As a CMO, I need a defensible model linking purchasing to income so I can allocate budget with confidence.
- As a CRM Manager, I need a clean customer table with product recommendations and clear filters.
- As Merchandising, I need SKU‑level visibility of forecasted demand to adjust buys and avoid stockouts/overstock.

## Acceptance Criteria

- Power BI report includes: income map, income histogram, scatter with trendline and R² card, customer recommendation table, and a scenario/forecast block.
- DAX measures for slope (m), intercept (b), Pearson r, R², Predicted Income, Recommended Product, and Forecast KPIs (orders, revenue, returns, profit).
- PDF summary answers the five core questions and states the go‑to‑market plan.

## Success Criteria

- Evidence of positive, material correlation between income and purchases at state level.
- A ranked customer list with counts per product and clear geo lenses.
- A forecasting panel that shows ROI sensitivity to response rate and return rate.
- Stakeholders sign off target segments and budget split.

## Data Source

- **US Census Bureau**: Avg income, population, industries.
- **Business Data**: Product inventory, prices, Customer Rating, Return Rate.
- **Customer Data**: Customer list, purchase history.
- **Reference**: State list/regions.
- **Optional**: Weather, unemployment, competition density for further robustness.

## Dataset

Initially 4 dataset was provided by stakeholder for the completion of this project (or can be dowloaded in the provided GitHub repository). These four data are census data, customer list, purchase list and state list spreadsheets. Finally, after integrating the various spreadsheet into power BI, result into 7 tables listed below;
- Avg Income by State

| Column Name | Data type | Description |
| --- | ---| --- |
| State | Text | Name of State and Foreign Key |
| Average Income | Decimal Number | Average income across each state |

- Customer List

| Column Name | Data type | Description |
| --- | ---| --- |
| Customer ID  | Text | Foreign key |
| First Name | Text | customer first name |
| Last Name | Text | Customer Last Name |
| Date of Birth | Date | customers date of birth |
| State | Text | State which each customers comes from |
| Last 6 Months Purchase | Decimal Number | Total sum of purchases in the last 6months by each customers |
| Duration | Time | Duration in hours from the day each customer was born till date |
| Age | Whole Number | Age of customer |

- Income by State

| Column Name | Data type | Description |
| --- | ---| --- |
| State | Text | foriegn key |
| Label | Text | salary range in each Country |
| Percentage | Decimal Number | each salary range percentage breakdown to the overal percentage |
| Estimated Income | Whole Number | each state salary range estimation |

- Industries

| Column Name | Data type | Description |
| --- | ---| --- |
| Sate | Text | Primary Key linking to Fact table |
| Industry | Text | Various indudtries that existed in each state |
| Population | Whole Number | Total Population that existed by industry in each state |

- Product Inventory

| Column Name | Data type | Description |
| --- | ---| --- |
| Product ID | Text | Primary key linking fact and Dim together |
| Product Name | Text | Name of Product |
| Current Price | Whole Number | Price tag for each product |
| Number in stock | Whole Number | each product total stock available |
| Customer rating | Decimal Number | overall rating for each product |
| Return Rates | Decimal Number | rate at which each product are being returned |

- Purchasing List Table

| Column Name | Data type | Description |
| --- | ---| --- |
| Customer ID | Text |  |
| Date | Date | Date at which customers purchases |
| Purchase | Decimal Number | Purchases made by each customers |

- State List

| Column Name | Data type | Description |
| --- | ---| --- |
| State | Text | Primary Key |  


# Data Model Structure 
Star schema with conformed dimensions and supporting regression tables:  

- FactOurchases: CustomnerID, ProductID, Date, Quantity, Unit Price, Amount
- DimCustomer: CustomerID, Name, DOB, City, State, ZIP, Segment.
- DimProduct: ProductID, Name, Category, ListPrice, CustomerRating, ReturnRate.
- DimState: State, StateCode, Region.
- DimIncome: State, AvgIncome (joins via DimState).
- DimDate: Date, Year, Quarter, Month.
- Regression_Tbl (state grain): x_AvgIncome, y_AvgSales6M, helpers (x2, y2, xy).
- ProdCorr_Tbl (product grain): rating, returnRate for quality correlation.

![Data model image](Asset/Image_Folder/Data_Model.png)


