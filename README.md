
#  Amazon Sales Performance Dashboard - Power BI
## Project Overview
- This project presents a fully interactive **Amazon Sales Performance Dashboard** built using **Power BI**. It provides deep insights into sales, customer behavior, product performance, and regional distribution.
- The dataset used in this project was downloaded from **Kaggle**, containing realistic e-commerce transaction data. This project highlights strong capabilities in **data visualization, business intelligence, and advanced DAX calculations**.

---
##  Dashboard Preview
<p align="center">
  <img src="https://github.com/Nagendra7290/Amazon-Sales-Analysis/blob/main/Screenshot%202026-03-22%20025024.png" width="full"/>
  <br>
  <em>Amazon Sales Performance Dashboard</em>
</p>

----
##  Dataset Information
- **Source:** Kaggle (Amazon / E-commerce Sales Dataset)
- **Format:** CSV
- **Data Fields:**
  - Order ID
  - Order Date
  - Product Category
  - Price
  - Quantity Sold
  - Revenue
  - Customer Region
  - Payment Method
  - Rating
  - Discount %

---

##  Tools & Technologies
- Power BI Desktop  
- Power Query (ETL)  
- DAX (Advanced Calculations)  
- Excel / CSV  

---

##  Project Workflow

### 1️⃣ Data Collection
- Downloaded dataset from Kaggle  
- Imported into Power BI  

### 2️⃣ Data Cleaning (Power Query)
- Removed null values  
- Changed data types  
- Handled duplicates  
- Standardized column names  

### 3️⃣ Data Modeling
- Created relationships  
- Optimized data model  
- Built calculated columns and measures  

---

##  Key KPIs
-  Total Revenue: **32.87M**  
-  Total Orders: **50K**  
-  Quantity Sold: **150K**  
-  Avg Order Value: **657.33**  
-  Avg Rating: **3.00**  

---

##  Dashboard Visuals
- Revenue by Product Category  
- Monthly Sales Trend  
- Customer Region Analysis  
- Payment Method Distribution  
- Rating vs Revenue  
- Yearly Orders Comparison  
- Discount Impact (Waterfall)  
- Geographic Sales Map  

---

##  Advanced DAX Measures

### 🔹 Basic Measures
```DAX
Total Revenue = SUM('Sales'[Revenue])

Total Orders = DISTINCTCOUNT('Sales'[Order ID])

Total Quantity = SUM('Sales'[Quantity])

Average Rating = AVERAGE('Sales'[Rating])
````

---

###  Time Intelligence

```DAX
Revenue YTD = 
TOTALYTD(
    [Total Revenue],
    'Sales'[Order Date]
)

Revenue MTD = 
TOTALMTD(
    [Total Revenue],
    'Sales'[Order Date]
)

Revenue YoY Growth % = 
VAR CurrentYear = [Total Revenue]
VAR PreviousYear = 
    CALCULATE(
        [Total Revenue],
        SAMEPERIODLASTYEAR('Sales'[Order Date])
    )
RETURN 
DIVIDE(CurrentYear - PreviousYear, PreviousYear, 0)
```

---

###  Advanced Business Metrics

```DAX
Average Order Value = 
DIVIDE([Total Revenue], [Total Orders], 0)

Revenue per Customer = 
DIVIDE(
    [Total Revenue],
    DISTINCTCOUNT('Sales'[Customer ID]),
    0
)

Top Category Revenue = 
CALCULATE(
    [Total Revenue],
    TOPN(
        1,
        VALUES('Sales'[Product Category]),
        [Total Revenue],
        DESC
    )
)
```

---

###  Ranking & Segmentation

```DAX
Category Rank = 
RANKX(
    ALL('Sales'[Product Category]),
    [Total Revenue],
    ,
    DESC
)

Customer Segment = 
SWITCH(
    TRUE(),
    [Total Revenue] > 10000, "High Value",
    [Total Revenue] > 5000, "Medium Value",
    "Low Value"
)
```

---

###  Moving Average & Trend

```DAX
7 Day Moving Avg = 
AVERAGEX(
    DATESINPERIOD(
        'Sales'[Order Date],
        MAX('Sales'[Order Date]),
        -7,
        DAY
    ),
    [Total Revenue]
)
```

---

###  Discount Impact

```DAX
Revenue After Discount = 
SUMX(
    'Sales',
    'Sales'[Revenue] * (1 - 'Sales'[Discount %] / 100)
)
```

---

##  Key Insights

*  Balanced revenue across product categories
*  Equal contribution from global regions
*  Digital payments dominate transactions
*  Discounts increase total sales volume
*  Stable monthly sales trend

---

##  Learning Outcomes

* Advanced Power BI dashboard development
* Strong DAX and data modeling skills
* Business insight generation
* Data storytelling and visualization

---

##  How to Use

1. Download `.pbix` file
2. Open in Power BI Desktop
3. Refresh dataset
4. Explore dashboard

---

##  Future Enhancements

* Forecasting (AI visuals)
* Real-time data integration
* Drill-through dashboards
* Role-based access

---

##  Support

If you like this project, give it a  on GitHub!

---

```
```
