# Northwind Sales Performance Dashboard

## Overview

This project is an interactive Power BI dashboard built on the Northwind sample database, providing a sales performance overview through KPI cards, revenue trends, category and customer rankings, and a geographic revenue breakdown. It builds directly on the SQL business questions answered in the [Northwind SQL Business Analysis](https://github.com/RyanKennon/sql-business-analysis-northwind) project, translating several of those same questions into an interactive visual format.

---

## Dataset

This project uses the same Northwind sample database as the SQL analysis project — an expanded/synthetic version with significantly more order volume than the classic Northwind dataset (600K+ rows in Order Details vs. ~2,000 in the original). As a result, revenue figures are much larger than realistic small-business scale, and should be read as relative comparisons rather than real-world dollar amounts. See the [SQL project's Dataset section](https://github.com/RyanKennon/sql-business-analysis-northwind#dataset) for full details.

---

## Setup / Prerequisites
- Install [Power BI Desktop](https://www.microsoft.com/en-us/power-platform/products/power-bi/downloads) (free, Windows only)
- Download the `.pbix` file from this repo
- Open it in Power BI Desktop to explore the dashboard interactively

---

## Tools Used
- **Power BI Desktop** — used to build the data model, DAX measures, and all visuals
- **SQLite ODBC Driver** — used to connect Power BI to the Northwind SQLite database

---

## Dashboard Overview

📊 [Download the interactive dashboard (.pbix file)](dashboards/dashboard_full.pbix) 
— requires [Power BI Desktop](https://www.microsoft.com/en-us/power-platform/products/power-bi/downloads) to open

<p align="center">
  <img width="1445" height="810" alt="image" src="https://github.com/user-attachments/assets/25c4da67-0d38-4346-9fc5-2a3d7deb04ea" />
</p>

### KPI Summary
The top of the dashboard shows three key metrics at a glance: Total Revenue ($448.39M), Total Orders (16K), and Average Order Value ($27.54K) across the full dataset.

### Revenue Trend by Year

<p align="center">
  <img width="1147" height="640" alt="image" src="https://github.com/user-attachments/assets/03bb7690-74e2-4ee9-85b3-25d97bd5d0f5" />
</p>

- What it shows: Total revenue by year, from 2012 through 2023.
- Finding: Revenue holds steady between roughly $38M and $41.4M from 2013 through 2022, with lower totals in 2012 and 2023 due to partial-year data — consistent with the finding from the SQL analysis.

### Total Revenue by Category

<p align="center">
  <img width="1150" height="644" alt="image" src="https://github.com/user-attachments/assets/012776f1-5618-425f-83aa-2958bd4b3e61" />
</p>

- What it shows: Total revenue broken down by product category, sorted highest to lowest.
- Finding: Beverages leads at roughly $92M, followed by Confections and Meat/Poultry, with revenue fairly evenly distributed across the remaining categories — matching the SQL project's findings exactly.

### Total Revenue by Country

<p align="center">
  <img width="1149" height="645" alt="image" src="https://github.com/user-attachments/assets/ba6e7231-cd4d-465a-83c7-5857d9dda048" />
</p>

- What it shows: A map visual sizing revenue by customer country.
- Finding: Revenue is concentrated in Europe and North America, with the largest bubbles clustered in those regions, consistent with the customer base represented in the dataset.

### Total Revenue by Company

<p align="center">
  <img width="1151" height="645" alt="image" src="https://github.com/user-attachments/assets/dc391f3f-1f8f-4d6f-8702-28778a06826f" />
</p>

- What it shows: The top 10 customers by total revenue.
- Finding: B's Beverages is the top customer at roughly $6.15M, consistent with the SQL project's findings. While building this chart, two customer records sharing the placeholder company name "IT" (CustomerIDs Val2 and VALON) initially inflated into one combined bar — the same data quality issue identified in the SQL analysis. A calculated column was used to append the CustomerID only where a company name wasn't unique, correctly splitting these into two distinct, appropriately-sized bars while keeping all other labels clean.

### Interactivity
All visuals on the dashboard are cross-filterable — clicking on a category, country, or customer bar filters the other visuals to show only data related to that selection.

---

## Next Steps

With more time, this dashboard could be extended with a dedicated page for employee or shipping performance, drill-through pages for individual customers or categories, or a year/category slicer to let users filter the whole dashboard interactively rather than relying solely on cross-filtering.
