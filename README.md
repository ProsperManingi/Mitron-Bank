# Mitron-Bank-Sample-Dashboard
## Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Preparation](#data-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results/Findings](#results/findings)
- [Recommendations](#recommendations)

## Project Overview
This a sample dataset provided by Mitron Bank management as they consider launching a new credit card for their customers based on the findings of the analysis. The sample dataset has a total of 4000 customers who are spread across 5 different cities.

![Screenshot (63)](https://github.com/user-attachments/assets/d0f6ba44-5944-4fb7-8e1d-277d00ad2829)

## Data Source
The primary datasets include: "dim_cusomer.csv" and "facts_spends.csv" these contain the the key information of the customers of Mitron bank.

## Tools Used
- MS Ecel
- MS SQL Server
- MS Power BI

## Data Cleaning & Preparation
In the intial data preparation phase, we peformed the following tasks:

- Clean the datasets usin Ms Excel to remove any duplicates or to correct any missing values.
- Created a database on SQL server for Mitron Bank.
- Then added tables to the database using the csv files.
- Joined the tables to form 1 with comprehensive report.
- Then transformed the data to Power BI for visualisation.

## Explanatory Data Analysis
EDA involved looking at the sample dataset provided by the bank as they seek to launch the new credit card and answer key questions such as:
1. Which city amongst the 5 have the highest earners in terms of income?
2. Which age group has the highest paid people?
3. What do these customers spend their income on?
4. Which payment method is prefered to use when making the different payment?
5. Between married and single people who are the most paid and who spend the most?

## Data Analysis

``` sql
WITH customer_spend_summary AS (
    SELECT 
        c.customer_id,
        c.age_group,
        c.marital_status,
        c.city,
        
        -- Include average income directly from dim_customers
        c.avg_income,

        s.month,
        s.category,
        s.payment_type,
        s.spend
    FROM dim_customers c
    JOIN fact_spends s ON c.customer_id = s.customer_id
)
SELECT * 
FROM customer_spend_summary
ORDER BY age_group, month, category;
```

## Results/Findings

#### Target Demographic:

- The 25-34 age group is the most valuable segment for both spending and income.

- Married individuals spend more and have higher average incomes.

#### Preferred Payment Method:

- Credit cards dominate payment methods, followed by debit cards.

- UPI is growing but still lags behind traditional card-based payments.

#### Geographic Focus:

- Mumbai and Chennai represent the most lucrative markets based on average income.

#### Spending Trends:

- Essentials like bills, groceries, and electronics are the biggest spending categories

## Recommendations
Based on The Analysis we recommend the following actions:
#### Target Audience:

- Prioritize marketing toward the 25-34 age group and married individuals.

- Tailor offers for high-income cities like Mumbai and Chennai.

#### Product Features:

- Offer cashback and reward points for high-spending categories (bills, groceries, electronics).

- Provide flexible credit limits for high-income groups.

 #### Payment Incentives:

- Introduce special incentives for credit card use to maintain dominance.

- Consider UPI-linked credit card features to attract younger customers.

#### Marketing Strategy:

- Personalize campaigns for married customers with family-centric benefits.

- Create city-specific promotions focusing on major metropolitan areas.


