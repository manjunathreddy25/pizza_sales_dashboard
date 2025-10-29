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

## Example SQL snippets
-- Daily sales and AOV
SELECT
  CAST(order_date AS DATE) AS sale_date,
  COUNT(DISTINCT order_id) AS orders,
  SUM(total_amount) AS total_sales,
  ROUND(SUM(total_amount) * 1.0 / NULLIF(COUNT(DISTINCT order_id),0), 2) AS aov
FROM pizza_sales
GROUP BY CAST(order_date AS DATE)
ORDER BY sale_date;

-- Top selling pizzas by store
SELECT store_id, pizza_name, SUM(quantity) AS units_sold
FROM pizza_sales
GROUP BY store_id, pizza_name
ORDER BY store_id, units_sold DESC;

## Data contract
- Input: `pizza_sales.csv` — expected columns include `order_id`, `order_date` (parseable), `store_id`, `pizza_name`, `category`, `quantity`, `price`, `total_amount`.
- Output: aggregated tables and reports (daily/monthly sales, top SKUs, KPI metrics).
- Error modes: missing/invalid dates and null totals; queries defensively handle NULLs and avoid divide-by-zero using `NULLIF`.

## How to reproduce locally
1. Clone the repo:
   git clone https://github.com/manjunathreddy25/pizza_sales_dashboard.git
2. Open `Pizza_sales_dashboard.xlsx` in Excel. If prompted, enable content and use Data → Refresh All to update PivotTables from the `pizza_sales.csv` table.
3. To run SQL locally, import `pizza_sales.csv` into your SQL engine (SQLite/Postgres) as `pizza_sales` and run queries from `PIZZA SALES SQL QUERIES.docx`.

## Next steps / suggestions
- Add a `queries.sql` file with the core SQL queries for easy reuse.
- Add a short script (Python/R) to auto-run SQL and export summary tables.
- Add a brief Findings/Recommendations section summarizing the top business insights.

If you'd like, I can also move SQL queries into a `queries.sql` file and add a small script to refresh the Excel dashboard automatically. Tell me if you want me to commit those changes now.

---
Generated on 2025-10-29
