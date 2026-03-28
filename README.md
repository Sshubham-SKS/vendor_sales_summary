# 📊 Vendor Sales Performance Dashboard

An interactive Power BI dashboard built to analyze vendor-level sales, profitability, and performance insights using Python, SQL, and DAX.
This project transforms raw vendor sales data into meaningful business insights for better decision-making.

<img width="1118" height="705" alt="vendor_sales_summary" src="https://github.com/user-attachments/assets/10dbb431-2220-4216-ab15-86ab86fdf7c9" />

---

## 🚀 Project Overview

This dashboard focuses on analyzing:

* Vendor-wise sales and profit
* Purchase vs revenue comparison
* Profit margin insights
* Brand-level performance
* High and low performing vendors

---

## 🛠️ Tech Stack

* Power BI → Dashboard & Visualization
* SQL → Data aggregation & querying
* Python (Pandas) → Data cleaning & preprocessing
* DAX → Measures and calculations

---

## 📂 Dataset

The dataset contains vendor-level sales information, including:

* Vendor Name
* Brand
* Purchase Price
* Sales Amount
* Quantity Sold
* Gross Profit
* Profit Margin

---

## 📈 Key Metrics (DAX Measures)

### 🔹 Sales & Profit Metrics

```
Total Sales = SUM(vendor_sales_summary[TotalSalesDollars])

Total Purchase = SUM(vendor_sales_summary[TotalPurchaseDollars])

Total Profit = SUM(vendor_sales_summary[GrossProfit])

Profit Margin % = DIVIDE([Total Profit], [Total Sales], 0)
```

### 🔹 Performance Metrics

```
Avg Profit per Vendor = 
AVERAGE(vendor_sales_summary[GrossProfit])

Avg Sales per Vendor = 
AVERAGE(vendor_sales_summary[TotalSalesDollars])
```

### 🔹 Efficiency Metrics

```
Sales to Purchase Ratio = 
DIVIDE([Total Sales], [Total Purchase], 0)

Profit per Unit = 
DIVIDE([Total Profit], SUM(vendor_sales_summary[TotalSalesQuantity]), 0)
```

### 🔹 Contribution Analysis

```
% Contribution Sales = 
DIVIDE(
    [Total Sales],
    CALCULATE([Total Sales], ALL(vendor_sales_summary)),
    0
)

% Contribution Profit = 
DIVIDE(
    [Total Profit],
    CALCULATE([Total Profit], ALL(vendor_sales_summary)),
    0
)
```

### 🔹 Ranking Measures

```
Vendor Rank by Sales = 
RANKX(
    ALL(vendor_sales_summary[VendorName]),
    [Total Sales],
    ,
    DESC
)

Vendor Rank by Profit = 
RANKX(
    ALL(vendor_sales_summary[VendorName]),
    [Total Profit],
    ,
    DESC
)
```

### 🔹 Category Segmentation

```
Profit Category = 
SWITCH(
    TRUE(),
    [Profit Margin %] > 0.4, "High",
    [Profit Margin %] > 0.2, "Medium",
    "Low"
)
```

### 🔹 Top N Filtering

```
Top 10 Vendor Sales = 
CALCULATE(
    [Total Sales],
    TOPN(
        10,
        ALL(vendor_sales_summary[VendorName]),
        [Total Sales],
        DESC
    )
)
```

### 🔹 Variance Analysis

```
Sales vs Purchase Difference = 
[Total Sales] - [Total Purchase]

Profit % of Purchase = 
DIVIDE([Total Profit], [Total Purchase], 0)
```

### 🔹 Conditional KPI Indicator

```
Profit Status = 
IF(
    [Profit Margin %] > 0.3,
    "Good",
    "Needs Improvement"
)
```

```
Avg Profit per Vendor = AVERAGE(vendor_sales_summary[GrossProfit])
```

---

## 📊 Dashboard Features

### 🔹 KPI Cards

* Total Sales
* Total Purchase
* Total Profit
* Profit Margin %
* Average Profit per Vendor

### 🔹 Vendor Analysis

* Top vendors by sales
* Vendor profitability comparison

### 🔹 Brand Analysis

* Brand-wise sales distribution
* Identification of top-performing brands

### 🔹 Profitability Analysis

* Scatter plot (Sales vs Profit Margin)
* Identifies high-value vendors

### 🔹 Cost vs Revenue

* Comparison of purchase cost and sales revenue

### 🔹 Interactive Filters

* Vendor slicer for dynamic analysis

---

## 📌 Key Insights

* Top vendors contribute significantly to overall revenue
* Some vendors generate high sales but lower margins
* Strong correlation between sales and profit
* Certain brands dominate revenue generation
* Profitability varies significantly across vendors

---

## 🧠 Data Engineering Approach

* Cleaned and processed raw data using Python (Pandas)
* Aggregated and structured data using SQL queries
* Built calculated measures using DAX in Power BI
* Designed an interactive and user-friendly dashboard

---

## 🎯 Outcome

This project demonstrates how raw sales data can be converted into actionable insights for:

* Performance monitoring
* Vendor evaluation
* Profitability analysis
* Business decision-making

---

## 👤 Author

**Shubham Kumar**
Aspiring Data Analyst

