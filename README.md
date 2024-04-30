# Credit Card Transaction Report

### Dashboard Link : https://app.powerbi.com/groups/me/reports/d9416143-6669-4b55-9c09-9f406797d55d/ReportSection6693b3ea2bbb793d079e?experience=power-bi

## Problem Statement

This dashboard helps to understand a comprehensive credit card weekly transactions that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.

Streamlined data processing & analysis to monitor key performance metrics and trends.

Created actionable insights for stakeholders based on dashboard findings to support decision-making processes.


# DAX Queries

AgeGroup = SWITCH(
TRUE(),
'public cust_detail'[customer_age] < 30, "20-30",
'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
'public cust_detail'[customer_age] >= 60, "60+",
"unknown"
)
IncomeGroup = SWITCH(
TRUE(),
'public cust_detail'[income] < 35000, "Low",
'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
'public cust_detail'[income] >= 70000, "High",
"unknown"
)
week_num2 = WEEKNUM('public cc_detail'[week_start_date])
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]
Current_week_Reveneue = CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])))
Previous_week_Reveneue = CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))

# Insights

A two page report was created on Power BI Desktop & it was then published to Power BI Service.

![1](https://github.com/Arunima221994/Credit-Card-Transaction-Report/assets/154328968/07b8a031-757e-4dc7-a110-995b494247ca)



![2](https://github.com/Arunima221994/Credit-Card-Transaction-Report/assets/154328968/e362ca77-b4fb-4487-b7aa-4a5d65514654)

Following inferences can be drawn from the dashboard;


Overview YTD:

- Overall revenue is 55M
- Total interest is 8M
- Total transaction amount is 45M
- Male customers are contributing more in revenue 30M, female 25M
- Blue & Silver credit card are contributing to 93% of overall transactions
- TX, NY & CA states are contributing to 68%
