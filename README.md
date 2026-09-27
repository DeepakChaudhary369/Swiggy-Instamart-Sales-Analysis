# 🛒 Insta Mart Grocery Stores Dashboard

An end-to-end **Power BI** analytics dashboard built on grocery store sales data, styled around the Swiggy Instamart brand.

![Dashboard Preview](./Final%20Dashboard.jpg)


## 📌 Overview

This dashboard analyzes item-level sales across 10 grocery shops, covering **8,523 transactions** and **1,559 unique products**. It answers questions like:

- How do sales and order volume vary by city tier, shop size, and shop type?
- Which product categories drive the most revenue?
- How has store performance trended by opening year?
- What's the average customer rating, and how does it break down by shop?

## 📊 Dataset

- **Source file:** `Instamart_Data.xlsx`
- **Rows:** 8,523 (one row per item sold)
- **Shops:** 10
- **Columns:**
  | Column | Description |
  |---|---|
  | Item Code | Unique product identifier |
  | Category | Product category (e.g. Fruits and Vegetables, Snack Foods, Dairy) |
  | Shop Code | Unique shop identifier |
  | Shop City Type | City tier (Tier 1 / Tier 2 / Tier 3) |
  | Shop Size | Shop footprint (Small / Medium / High) |
  | Shop Type | Grocery Store / Supermarket Type1 / Type2 / Type3 |
  | Item Weight | Product weight (has some missing values) |
  | Sales | Sales value for that item |
  | Rating | Customer rating |
  | Shop Opening Year | Year the shop opened (2021–2024) |

## 🧹 Data Cleaning (Power Query)

Before loading into the model, the raw data was cleaned to fix inconsistent category labels and stray text values:

- Standardized category typos: `"Health & Hy"` → `"Health and Hygiene"`, `"Frz Foods"` → `"Frozen Foods"`
- Fixed malformed year entries: `"20 22"` → `2022`, `"20 24"` → `2024`

## 🧮 DAX Measures

```DAX
Total_Sales = SUM('Grocery Shop'[Sales])
Avg_Sales   = AVERAGE('Grocery Shop'[Sales])
Total_Order = COUNTROWS('Grocery Shop')
Avg_Rating  = AVERAGE('Grocery Shop'[Rating])
```

## 🖥️ Dashboard Features

- **KPI cards** — Total Sales, Average Sales, Total Order, Average Rating
- **Dynamic metric switcher** — a Field Parameter table lets a single donut chart swap between Total_Sales / Avg_Sales / Total_Order / Avg_Rating on click
- **Interactive slicers** — filter by Shop Opening Year, Shop Size, and City Type
- **Breakdowns by:**
  - City Type (bar chart + donut)
  - Shop Size (donut)
  - Category (horizontal bar, top revenue drivers)
  - Shop Type (detail table)
  - Opening Year (trend line)
- **One-click reset** — a "Clear Filter" button clears all active slicer selections

## 🔑 Key Insights

- Supermarket Type1 accounts for the majority of both sales (₹787K+) and order volume (5,577 items) among the five shop types.
- Tier 3 cities generate the highest order volume, despite Tier 1 shops posting the highest total sales — suggesting Tier 1 sees fewer but higher-value transactions.
- Fruits & Vegetables and Snack Foods are the top two revenue categories, each contributing ~0.18M.
- Average customer rating sits at 3.92 across all shops, with little variation by shop type (3.91–3.93).

## 🛠️ Tools Used

- **Power BI Desktop** — data modeling, DAX, report design
- **Power Query (M)** — data cleaning and transformation
- **Excel** — source data format

## 🚀 How to Use

1. Clone this repo
2. Open `Insta_Mart_Grocery_stores_Dashboard_.pbix` in Power BI Desktop
3. If prompted, update the data source path to point to your local copy of `Instamart_Data.xlsx`
4. Explore the dashboard using the slicers and metric-switcher buttons

## 📂 Repo Structure

```
├── Insta_Mart_Grocery_stores_Dashboard_.pbix
├── Instamart_Data.xlsx
├── dashboard_screenshot.png
└── README.md
```

## 🔍 Notes / Future Improvements

- Convert `Shop Opening Year` from text to a whole number and sort the year-trend chart chronologically (currently sorted by order volume).
- Store `Rating` as a decimal rather than a whole number to preserve precision in the `Avg_Rating` measure.
- Handle missing `Item Weight` values (currently ~17% null) if the field is used in future analysis.

## 👤 Author

**Deepak Chaudhary**
B.Tech Computer Science (Data Science)
