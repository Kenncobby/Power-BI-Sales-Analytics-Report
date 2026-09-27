# 📊 Power BI Sales Analytics Report

A star-schema Power BI semantic model, DAX measure library, and interactive report, built on top of a SQL Server Medallion warehouse (Bronze/Silver/Gold).

> **Work in progress.** This repo is being built alongside the semantic model and report; the measure catalog, screenshots, and report pages are added as each phase completes.

## Architecture

`CSV (ERP, CRM) → Bronze → Silver → Gold (star schema) → Power BI semantic model → Report`

This repo holds only the Power BI layer. The SQL Server data warehouse it connects to — schemas, load procedures, quality checks, and the Gold views this model imports from — lives in the companion repo: [Kenncobby/SQL-Server-Data-Warehouse](https://github.com/Kenncobby/SQL-Server-Data-Warehouse).

## Contents

- `powerbi/SalesAnalytics.pbip` — Power BI project (PBIR report + TMDL semantic model)
- `docs/powerbi_reconciliation_results.md` — SQL-source-of-truth totals every DAX measure reconciles to
- `docs/powerbi_measures.md` — full measure catalog *(added once Phase 6 is complete)*
- `docs/images/` — report and model screenshots *(added once Phase 7-9 are complete)*

## Model summary

- **Star schema**: `Fact Sales` + `Dim Customer`, `Dim Product`, `Dim Date` (marked date table, calendar + fiscal-year hierarchies)
- Single-direction, many-to-one relationships; two inactive date relationships (Shipping Date, Due Date) for alternate time analysis
- Fiscal year starts in July, named by its end year (e.g. Jul 2012-Jun 2013 = FY2013)

## How to run

1. Set up and load the warehouse per the instructions in the [companion repo](https://github.com/Kenncobby/SQL-Server-Data-Warehouse).
2. Open `powerbi/SalesAnalytics.pbip` in Power BI Desktop (version 2.141.1451.0 or later).
3. Set the `ServerName`, `DatabaseName`, and `FiscalYearStartMonth` parameters.
4. Refresh.

## Author

Kenneth Appiah — SQL Developer specializing in database design, query optimization, and ETL solutions. Built as part of a Microsoft Certified: Power BI Data Analyst Associate (PL-300) portfolio.

## License

MIT — see [LICENSE](LICENSE).
