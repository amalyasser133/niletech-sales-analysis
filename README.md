<div align="center">

# 📊 NileTech Electronics — Retail Sales Intelligence

### End-to-End Excel Data Analysis & Interactive Dashboards (FY2023 – FY2025)

![Excel](https://img.shields.io/badge/Microsoft%20Excel-Data%20Analysis-217346?logo=microsoftexcel&logoColor=white)
![Data Model](https://img.shields.io/badge/Data%20Model-Star%20Schema-1F4E79)
![Dashboards](https://img.shields.io/badge/Dashboards-3-orange)
![Transactions](https://img.shields.io/badge/Transactions-11%2C345-blue)

</div>

---

## 📌 Table of Contents

1. [Project Overview](#-project-overview)
2. [Business Questions](#-business-questions)
3. [Dataset at a Glance](#-dataset-at-a-glance)
4. [Data Model](#-data-model)
5. [Workbook Structure](#-workbook-structure)
6. [Dashboards](#-dashboards)
7. [Key Insights & Recommendations](#-key-insights--recommendations)
8. [Techniques & Skills Demonstrated](#-techniques--skills-demonstrated)
9. [How to Use](#-how-to-use)
10. [Notes & Disclaimer](#-notes--disclaimer)

---

## 🎯 Project Overview

**NileTech Electronics** is a fictional electronics retail chain operating **9 physical stores across Egypt plus 1 online channel**. This project analyses three years of sales (2023–2025) to turn raw transactions into decisions: what sells, where, to whom, and how profitably.

The workbook is built as a complete analytics solution, from a clean **star-schema data model** through **pivot-style summaries** to **three interactive dashboards** that respond to shared slicers (Year, Region, Category).

---

## ❓ Business Questions

- How much revenue and profit did the business generate, and at what margin?
- Which product categories and individual products drive the most revenue?
- Which regions and stores lead or lag, and how do margins compare?
- Who are the customers (segment, gender) and how do they pay?
- How big is the online channel compared with physical stores?
- When are the peak months, and how should inventory and campaigns be planned?

---

## 🗂️ Dataset at a Glance

| Metric | Value |
|---|---|
| Transactions | **11,345** |
| Customers | **520** |
| Products (SKUs) | **40** |
| Sales points | **10** (9 stores + online) |
| Period | **Jan 2023 – Dec 2025** (3 fiscal years) |
| Total Revenue | **166.2M EGP** |
| Total Profit | **31.6M EGP** |
| Profit Margin | **19.0%** |
| Average Order Value | **14,646 EGP** |
| Online Share of Revenue | **20.3%** |

---

## 🧩 Data Model

The data follows a **star schema**: one thin fact table surrounded by four dimension tables, joined 1-to-many on key columns.

```
   Dim_Date ──┐                    ┌── Dim_Stores
              │                    │
              ├──►  Fact_Sales  ◄──┤
              │                    │
 Dim_Customers┘                    └── Dim_Products
```

| Table | Role | Key |
|---|---|---|
| `Fact_Sales` | Transactions (quantity, price, discount, cost, channel, payment method) | `SalesID` |
| `Dim_Date` | Calendar attributes (year, quarter, month, weekday, weekend flag) | `DateID` |
| `Dim_Stores` | Store name, city, region, format, open date | `StoreID` |
| `Dim_Products` | Product name, brand, category, unit cost and price | `ProductID` |
| `Dim_Customers` | Name, gender, age, segment, city, join date | `CustomerID` |

Descriptive attributes (Category, Region, Segment, …) are resolved into the fact table with `INDEX/MATCH` lookups, mirroring the relationship logic of a Power Pivot model while keeping every number auditable with native Excel formulas.
<img width="933" height="666" alt="model" src="https://github.com/user-attachments/assets/c9fd7086-588a-4bd0-a2c7-7fa954a8f787" />

---

## 📁 Workbook Structure

| Sheet | Purpose |
|---|---|
| **Cover** | Project introduction, scenario and scope |
| **Data Model** | Star-schema diagram and relationships |
| **Dashboard 1 – Overview** | Executive KPIs, category, region, monthly trend, store scatter |
| **Dashboard 2 – Customers** | Segments, payment methods, channel, gender-by-category |
| **Dashboard 3 – Stores** | Store ranking, top products, revenue vs margin |
| **Pivot_Summary** | `SUMIFS` / `COUNTIFS` summary tables feeding all charts |
| **Fact_Sales** | Transactions with calculated Revenue, COGS, Profit and Margin |
| **Dim_Date / Dim_Stores / Dim_Products / Dim_Customers** | Dimension tables |
| **Chart Guide** | Documentation of every chart: type, data source, filters |
| **Key Insights** | Auto-generated findings and suggested actions |

---

## 📈 Dashboards

All three dashboards are linked to the same **Year / Region / Category slicers**, so one click re-filters every KPI and chart.

### 1️⃣ Executive Overview
KPIs: Revenue · Profit · Margin % · Orders · Average Order Value · Online Share
Charts: Revenue share by category (doughnut) · Revenue by region (bar) · Monthly revenue & profit trend (line) · Store revenue vs margin (scatter)

<img width="1280" height="672" alt="1" src="https://github.com/user-attachments/assets/88180055-2a88-4fa8-803f-9a9be8a618ab" />

### 2️⃣ Customer & Segment Insights
KPIs: Active Customers · Average Discount · VIP Revenue Share · Orders per Customer
Charts: Revenue by segment (pie) · Orders by payment method (doughnut) · Revenue by channel (doughnut) · Male vs Female revenue by category (butterfly)

<img width="1272" height="675" alt="2" src="https://github.com/user-attachments/assets/56e5b761-2b40-4724-a265-90023cd4ec9b" />

### 3️⃣ Store & Operations Performance
KPIs: Stores + Online · Top Store Revenue · Best Store Margin · Average Units per Order
Charts: Revenue by store, ranked (bar) · Top 10 products (bar) · Revenue vs margin % by store (combo)

<img width="1271" height="672" alt="3_" src="https://github.com/user-attachments/assets/65d14b41-ea75-40d7-8f30-5ab86f436197" />

---

## 💡 Key Insights & Recommendations

| Area | Finding | Suggested Action |
|---|---|---|
| **Overall** | 166.2M EGP revenue, 31.6M EGP profit, 19.0% margin across 11,345 orders | Track average order value (14,646 EGP) monthly and set a growth target |
| **Category** | **Laptops** lead with 33% of revenue; **Accessories** are lowest at 1% | Protect stock and margin on Laptops; review pricing and promotions for Accessories |
| **Region** | **Greater Cairo** generates 58% of physical-store revenue; **Upper Egypt** the lowest at 6% | Use Greater Cairo as the benchmark and test its best practices elsewhere |
| **Store** | **Online Store** is the top sales point (20%); **Aswan** is the lowest (5%) | Investigate Aswan's traffic, assortment and staffing |
| **Margin** | Best: **Tanta** (19.7%); lowest: **Mansoura** (18.3%) | Margins are tight across stores, so growth should come from volume and mix, not store-level pricing |
| **Segment** | **Retail** brings 62% of revenue; VIP share is 7.0% | Launch a loyalty or upgrade offer to move Retail customers toward VIP |
| **Channel** | Online accounts for 20.3% of revenue | Compare online vs in-store growth monthly before extra online investment |
| **Payment** | **Installment** is the most used method (26% of orders) | Payment mix is balanced; negotiate fees with the highest-volume provider |
| **Seasonality** | Best month: **Dec 2025** (5.9M EGP) | Plan inventory and campaigns ahead of peak months |

---

## 🛠️ Techniques & Skills Demonstrated

- **Data modelling:** star schema, primary/foreign keys, thin fact table
- **Excel Tables** and **structured references**
- **Relational lookups** with `INDEX / MATCH` (with `IFERROR` handling)
- **Aggregation formulas:** `SUMIFS`, `COUNTIFS` for pivot-style summaries
- **Calculated fields:** Gross/Net Revenue, Discount, COGS, Profit, Margin %
- **Interactive dashboards** with shared **slicers**
- **Advanced chart types:** doughnut, pie, line, scatter, combo, butterfly/tornado
- **Dashboard storytelling:** KPI cards, consistent layout, chart documentation
- **Business insight writing:** findings paired with actionable recommendations

---

## 🚀 How to Use

1. Download `NileTech_Sales_Analysis.xlsx` and open it in **Microsoft Excel (desktop)**. Slicers work best in Excel 2013 or later.
2. Start with **Cover** and **Data Model** to understand the structure.
3. Open any **Dashboard** sheet and use the slicers on the right to filter by Year, Region and Category.
4. Check **Chart Guide** to see which data feeds each chart.
5. Read **Key Insights** for findings, which update with the slicers.

> ⚠️ Opening the file in Excel Online, Google Sheets or LibreOffice may limit slicer interactivity.

---

## 📝 Notes & Disclaimer

All company names, people and transactions in this workbook are **synthetic sample data**, generated for demonstration and portfolio purposes only. Any resemblance to real businesses or individuals is coincidental.

---

<div align="center">

**Built with Microsoft Excel** · 

</div>
