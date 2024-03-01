# Sales Management Dashboard

## [Dashboard Link]([Paste your Power BI link here](https://app.powerbi.com/groups/me/reports/ab779c24-d05b-412f-abaa-9a8e48bab8b0/ReportSection?experience=power-bi))

## Business Request & User Stories

This project was initiated to fulfill a business request for an executive sales report aimed at providing valuable insights to sales managers. To meet this demand, user stories were formulated, aligning with the business request and ensuring adherence to acceptance criteria.

| #   | I Want (Request/Demand)                     | So That I (User Value)                                                | Acceptance Criteria                                          |
| --- | ------------------------------------------ | --------------------------------------------------------------------- | ------------------------------------------------------------ |
| 1   | To get a dashboard overview of Internet Sales | Can follow better which customers and products sell the best        | A Power BI dashboard updating data daily                     |
| 2   | A detailed overview of Internet Sales per Customers | Can follow up on my customers who buy the most and identify potential upsell opportunities | A Power BI dashboard allowing me to filter data for each customer |
| 3   | A detailed overview of Internet Sales per Products | Can follow up on Products that sell the most                        | A Power BI dashboard allowing me to filter data for each Product |
| 4   | A dashboard overview of internet sales      | Follow sales over time against budget                                 | A Power BI dashboard with graphs and KPIs comparing against the budget |

## Data Cleansing & Transformation (SQL)

To establish the essential data model for analysis and meet the outlined business requirements, the following tables were extracted through SQL. Additionally, sales budgets, initially available in Excel format, were integrated into the data model in a later stage.

### DIM_Calendar:

```sql
-- Cleansed DIM_Date Table --
SELECT 
  [DateKey], 
  [FullDateAlternateKey] AS Date, 
  [EnglishDayNameOfWeek] AS Day, 
  [EnglishMonthName] AS Month, 
  Left([EnglishMonthName], 3) AS MonthShort, 
  [MonthNumberOfYear] AS MonthNo, 
  [CalendarQuarter] AS Quarter, 
  [CalendarYear] AS Year 
FROM 
  [AdventureWorksDW2019].[dbo].[DimDate]
WHERE 
  CalendarYear >= 2019
