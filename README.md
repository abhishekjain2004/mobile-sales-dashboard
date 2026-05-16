# 📱 Mobile Sales Performance Dashboard | Power BI

> An interactive Power BI dashboard tracking mobile phone sales across brands, cities, and time periods — featuring DAX-powered KPIs, MTD calculations, year-over-year comparisons, and dynamic slicers for drill-down analysis.

---

## 🛠️ Tools & Technologies

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=flat)
![Power Query](https://img.shields.io/badge/Power_Query-217346?style=flat)

---

## 🎯 Objective

To build a business-ready Power BI dashboard that enables sales managers and stakeholders to:
- Track **total revenue, units sold, and transaction volume** at a glance
- Analyse sales performance **by brand, city, and mobile model**
- Monitor **month-to-date (MTD)** progress and **same period last year (SPLY)** comparisons
- Identify **top-performing brands** and **seasonal trends** to support inventory and marketing decisions
- Segment performance by **payment method** and **customer ratings**

---

## 📁 Dataset Overview

**Table:** `Sales_Data`

| Column | Description |
|--------|-------------|
| `Transaction ID` | Unique identifier for each sale |
| `Date` | Transaction date |
| `Brand` | Mobile phone brand (Samsung, Apple, OnePlus, etc.) |
| `Mobile Model` | Specific model sold |
| `Units Sold` | Quantity per transaction |
| `Price Per Unit` | Selling price |
| `City` | City where the sale occurred |
| `Customer Name` | Buyer name |
| `Customer Age` | Buyer age |
| `Payment Method` | UPI, Credit Card, Debit Card, EMI, etc. |
| `Customer Ratings` | Rating given by customer |
| `Rating Status` | Good / Average / Poor (derived column) |

**Supporting Table:** `Custom_Calendar` — date table used for all time intelligence calculations (MTD, SPLY, Month, Year, Day Name)

---

## 📊 Dashboard Pages

The report has **3 pages**:

### 1. 📋 Dashboard (Main Overview)
The primary page with all top-level KPIs and breakdowns:
- **KPI Cards:** Total Sales, Total Quantity, Transactions, Average Price
- **Sales by Brand** — Clustered bar chart
- **Sales by City** — Map visual
- **Sales by Mobile Model** — Funnel chart
- **Sales by Payment Method** — Pie chart
- **Monthly Sales Trend** — Area/Line chart
- **Slicers:** Brand, City, Payment Method, Year, Month, Day Name

### 2. 📅 MTD Report
- Month-to-date sales vs. previous MTD using `TOTALMTD()` DAX function
- Tracks in-month progress with date-level granularity

### 3. 📆 Same Period Last Year
- Year-over-year comparison using `SAMEPERIODLASTYEAR()` DAX function
- Lets stakeholders benchmark current performance against prior year

---

## 🔢 DAX Measures Built

```dax
Total_Sales     = SUMX(Sales_Data, Sales_Data[Units Sold] * Sales_Data[Price Per Unit])
Total_Quantity  = SUM(Sales_Data[Units Sold])
Transactions    = COUNTROWS(Sales_Data)
Average_Price   = AVERAGE(Sales_Data[Price Per Unit])
MTD             = TOTALMTD([Total_Sales], Custom_Calendar[Date].[Date])
Same Period Last Year = CALCULATE([Total_Sales], SAMEPERIODLASTYEAR(Custom_Calendar[Date].[Date]))
```

---

## 📈 Key Insights

- **4 core KPIs tracked** on the main dashboard: Total Sales, Total Quantity, Transactions, and Average Price — all dynamically filtered by slicers
- **MTD vs SPLY comparison** enables quick identification of sales growth or decline without manual calculation
- **Map visual by City** surfaces geographic sales concentration — useful for regional inventory planning
- **Funnel chart by Mobile Model** highlights the distribution of sales across models, making it easy to spot top sellers
- **Customer Rating segmentation** (Good / Average / Poor) links product satisfaction to sales volume — useful for brand health monitoring
- **Payment Method breakdown** via pie chart reveals customer payment preferences — critical for partnerships with UPI/EMI providers
- **Custom Calendar table** powers all time intelligence measures, ensuring accurate MTD and year-over-year calculations

---

## 📸 Dashboard Screenshots


![Main Dashboard]<img width="1920" height="968" alt="Dashboard_main" src="https://github.com/user-attachments/assets/749208ab-95a5-4c5e-a4e2-2f4ed282ebda" />

![MTD Report]<img width="1920" height="984" alt="MTD_report" src="https://github.com/user-attachments/assets/8ab6e139-aabc-416f-8c1c-96d79df300e3" />

![Same Period Last Year]<img width="1920" height="981" alt="sply_report" src="https://github.com/user-attachments/assets/4dc0c20f-3ba5-44fc-814b-9d9fe660054f" />


---

## 🚀 How to Open

1. Download `Mobiles_Sales_Dashboard.pbix`
2. Open with **Power BI Desktop** (free — [download here](https://powerbi.microsoft.com/en-us/desktop/))
3. All data is embedded — no external connections needed
4. Use the **slicers** (Brand, City, Payment Method, Year, Month) to filter the dashboard interactively
5. Navigate between the 3 pages using the **page navigator** at the bottom

> ⚠️ Power BI Desktop is required to open `.pbix` files. It is free to download for Windows.

---

## 📂 Project Structure

```
mobile-sales-dashboard/
├── Mobiles_Sales_Dashboard.pbix    ← Main Power BI file (data + dashboard)
├── images/
│   ├── dashboard_main.png          ← Main dashboard screenshot
│   ├── mtd_report.png              ← MTD report page screenshot
│   └── sply_report.png             ← Same Period Last Year page screenshot
└── README.md
```

---

## 💡 What I Learned

- Building a multi-page interactive Power BI report with page navigation
- Writing DAX time intelligence functions: `TOTALMTD()`, `SAMEPERIODLASTYEAR()`, `CALCULATE()`
- Creating a Custom Calendar table to power accurate date-based analysis
- Using dynamic slicers to enable self-service filtering across all visuals
- Designing KPI cards, map visuals, funnel charts, and area charts for business storytelling
- Deriving a `Rating Status` column (Good/Average/Poor) using conditional logic

---

## 🙋 About Me

Made by **[Abhishek Jain](https://github.com/abhishekjain2004)**  
Aspiring Data Analyst | PG in Data Science & Analytics with Gen AI @ Imarticus Learning  
📧 abhishek2004.jain@gmail.com · [LinkedIn]www.linkedin.com/in/abhishek-jain-297014277
