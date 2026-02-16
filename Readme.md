# Classic Model — Business analysis & Power BI dashboard

## Table of contents
- [Introduction](#introduction)
- [Dataset / Inputs](#dataset--inputs)
- [Tech stack](#tech-stack)
- [Installation](#installation)
- [Usage](#usage)
- [Analysis — business questions](#analysis---business-questions)
- [Results / Insights (what to expect)](#results--insights-what-to-expect)
- [Project structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## Introduction
This repository contains an end-to-end business analysis built from the Classic Models dataset. The analysis covers sales, payments, orders, products, customers, employees and offices. SQL exploration and metric development were carried out in **MySQL Workbench**, and the final interactive report was developed in **Power BI Desktop**.

## Methodology
- SQL exploration & metric creation — MySQL Workbench: run the scripts in `sql_classic_model_scripty` to join tables, compute KPIs (revenue, order counts, customer lifetime value), and create analytical extracts.
- Data preparation — use provided SQL queries to create aggregated tables or export CSVs for Power BI.
- Visualization — Power BI Desktop: build interactive pages for product-line performance, customer segmentation, time-series trends, and office/employee performance.
- Reproducibility — all transformation logic is captured in the SQL scripts; run them in MySQL Workbench to reproduce the analysis and exports.

## Dataset / Inputs
- Core tables used: `products`, `productlines`, `orders`, `orderdetails`, `payments`, `employees`, `customers`, `offices`.
- SQL scripts and extracts are stored in the repository (`sql_classic_model_scripty` and `business_report/sql_classic_model_script.txt`).
- Data source: local database or exported CSVs (replace with your source). Use the SQL scripts to recreate or extract the dataset.

> Note: replace database connection details and file paths below with your environment-specific values.

## Tech stack
- Microsoft Power BI Desktop (dashboard / visualization)
- SQL (use your dialect: MySQL / PostgreSQL / SQL Server — replace as needed)
- Optional: Excel / CSV exports for ad‑hoc checks

## Installation
1. Clone the repository:

   ```bash
   git clone <repository-url>
   cd classic-model-business-analysis
   ```

2. Load the data:
   - Run the SQL scripts in `sql_classic_model_scripty` or open `business_report/sql_classic_model_script.txt` in your SQL client and execute against your database.
   - Example (MySQL):
     ```bash
     mysql -u <user> -p classicmodels < path/to/script.sql
     ```
   - If you only have CSVs, import them into your database or connect Power BI directly to the files.

3. Open the Power BI report (create or import a `.pbix` in the `business_report` folder) and point the data source to your database or CSV files.

## Usage
- Open the SQL script to inspect or modify the data-extraction queries.
- In Power BI Desktop, connect to your database and refresh the dataset to populate visuals.
- Typical workflow:
  1. Run the SQL extraction / ETL script
  2. Open `Power BI Desktop` → `Get Data` → connect to the database
  3. Load the model and refresh visuals

Example query (total revenue by product line):
```sql
SELECT p.productLine, SUM(od.quantityOrdered * od.priceEach) AS revenue
FROM orderdetails od
JOIN products p ON od.productCode = p.productCode
GROUP BY p.productLine
ORDER BY revenue DESC;
```

## Analysis — business questions
- Which product lines generate the most revenue?
- Who are the top customers by lifetime value?
- How does revenue trend by month / quarter / year?
- Which offices / territories outperform others?
- Which employees (sales reps) drive the most sales?
- Are there notable payment or order-fulfillment patterns?

## Results / Insights (what to expect)
- Interactive dashboards showing revenue by product line, top customers, time-series trends, and payment breakdowns.
- Filterable views for office, product line, customer segment and date ranges.
- Actionable insight examples (replace with your findings):
  - Product lines with sustained growth
  - Seasonal revenue patterns
  - Top customers driving majority of sales

## Project structure
- `LICENSE` — project license
- `Readme.md` — this file
- `sql_classic_model_scripty/` — SQL scripts used to extract / prepare the Classic Models dataset
- `business_report/` — Power BI report assets and example SQL extract (`sql_classic_model_script.txt`)

## Contributing
- Found an issue or want to add an analysis? Please open an issue first.
- Fork the repository, create a feature branch, add changes, and submit a pull request.
- Keep SQL scripts readable and comment queries. If adding visuals, include screenshots and describe the insight.

## License
This project is licensed under the **MIT License** — see the `LICENSE` file for details.

## Contact
- Author: **Kanchi Sukheja** — kanchisukheja20@gmail.com
- For questions or feedback: open an issue in this repository.

---

Thank you — feel free to update the dataset path or add a `.pbix` file in `business_report/` for a runnable dashboard.
