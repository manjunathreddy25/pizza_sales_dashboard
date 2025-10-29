# Pizza Sales Analysis Project

This repository contains the work for a Pizza Sales Analysis project. The focus is on SQL-based data transformation and Excel-based reporting/dashboarding to produce business-ready insights from the raw sales data.

## Contents
- `pizza_sales.csv` — raw transactional dataset (orders, timestamps, products, quantities, prices).
- `PIZZA SALES SQL QUERIES.docx` — documented SQL queries used to transform and aggregate the data.
- `Pizza_sales_dashboard.xlsx` — Excel workbook with pivot tables, charts and the interactive dashboard.
- `Pizza Background.jpg` — background/visual asset used in the dashboard.

## What I did (Data Analyst summary)
- Data preparation: cleaned and normalized the raw data (date parsing, deduplication, standardizing product names).
- SQL: wrote reusable queries to parse dates, aggregate sales by day/week/month, compute KPIs (total sales, AOV, units sold), and generate top-SKU/store summaries. Queries use CTEs and window functions for readability and performance. See `PIZZA SALES SQL QUERIES.docx` for the full SQL.
- Excel: built `Pizza_sales_dashboard.xlsx` with an imported data table, PivotTables, PivotCharts, Slicers and Timeline controls for interactive filtering and KPI cards (Total Sales, AOV, Units Sold, Top SKU).





