# 🏠 House Market Analytics – Power BI Report

This Power BI report provides a comprehensive analysis of the **Danish housing market**, built using **historical housing data (~100,000 rows)** from **Google BigQuery**. The project leverages advanced DAX measures, interactive visuals, and page-wise insights to understand market trends, sales performance, and property type behaviors.

---

## 📁 Dataset Overview

- **Source**: Google BigQuery (CSV format)
- **Volume**: ~100,000 rows × 19 columns (Columns A–S)
- **Important Columns**: `date`, `house_id`, `region`, `purchase_price`, `Offer Price`, `sqm`, `sqm_price`, `sales_type`, `house_type`, `age`

---

## 📊 Page 1 – House Market Overview

### 🔍 Visuals
- Median Sales Change by Region
- Units Sold in Latest Year & Quarter
- Sales in Last 12 Months
- Offer vs Purchase Price (scatter plot)
- YOY Sales Growth by Sales Type

### 🧮 DAX Measures

```dax
// Median Sales Change by Region
Mediun Sales Change = 
VAR CurrMedianPrice = 
    MEDIANX(
        FILTER(Housing, YEAR(Housing[date]) = YEAR(MAX(Housing[date]))),
        Housing[purchase_price]
    )
VAR PrevMedianPrice = 
    MEDIANX(
        FILTER(Housing, YEAR(Housing[date]) = YEAR(MAX(Housing[date])) - 1),
        Housing[purchase_price]
    )
RETURN IF(PrevMedianPrice <> 0, (CurrMedianPrice - PrevMedianPrice) / PrevMedianPrice, BLANK())
```

```dax
// Units Sold in Latest Year & Quarter
Houses Sold on latest year and quarter = 
    CALCULATE(
        DISTINCTCOUNT(Housing[house_id]),
        YEAR(Housing[date]) = YEAR(MAX(Housing[date])) &&
        QUARTER(Housing[date]) = QUARTER(MAX(Housing[date]))
    )
```

```dax
// Sales in Last 12 Months
Last 12 months Sales = 
    CALCULATE(
        SUM(Housing[purchase_price]),
        DATESINPERIOD(Housing[date], MAX(Housing[date]), -12, MONTH)
    )
```

```dax
// YOY Sales Growth
YOY_SALES_GROWTH = 
VAR CurrYearSales = 
    CALCULATE(SUM(Housing[purchase_price]), YEAR(Housing[date]) = YEAR(MAX(Housing[date])))
VAR PrevYearSales = 
    CALCULATE(SUM(Housing[purchase_price]), YEAR(Housing[date]) = YEAR(MAX(Housing[date])) - 1)
RETURN IF(PrevYearSales <> 0, (CurrYearSales - PrevYearSales) / PrevYearSales, BLANK())
```

### 📸 Screenshot – House Market Overview

> *(Insert screenshot here)*  
`![House Market Overview](![{C6F82730-FC2F-4AC3-8C16-E251DC4F5D7A}](https://github.com/user-attachments/assets/6f74ab8e-fae1-4a61-9f4a-6e9e87d4e4d3)
)`

---

## 📊 Page 2 – Sales Performance

### 🔍 Visuals
- Sales by Region (bar chart)
- Key Influencers (AI visual)
- Year-to-Date (YTD) Sales Table
- Offer-to-SQM Ratio by Sales Type
- Avg SQM Price by Region (donut chart)

### 🧮 DAX Measures

```dax
// Sales by Region
Sales by region = 
    CALCULATE(
        SUM(Housing[purchase_price]),
        ALLEXCEPT(Housing, Housing[region])
    )
```

```dax
// Offer to SQM Ratio
Offer to SQM Ratio = 
    DIVIDE(SUM(Housing[Offer Price]), SUM(Housing[sqm]))
```

```dax
// YTD Sales
Total YTD Sales = 
    TOTALYTD(SUM(Housing[purchase_price]), Housing[date].[Date])
```

### 📸 Screenshot – Sales Performance

> *(Insert screenshot here)*  
`![Sales Performance](path/to/screenshot2.png)`

---

## 📊 Page 3 – House Type Insights

### 🔍 Visuals
- Avg Offer & Purchase Price by House Type
- Avg Inflation / Interest Rate / Yield by House Type
- Avg SQM and SQM Price by House Type

### 🧮 DAX Measure

```dax
// Average SQM Price
Average SQM Price = 
    AVERAGE(Housing[sqm_price])
```

### 📸 Screenshot – House Type Insights

> *(Insert screenshot here)*  
`![House Type Insights](path/to/screenshot3.png)`

---

## 🛠️ Tools & Tech Stack

- **Data Source**: Google BigQuery (manually uploaded CSV)
- **Visualization Tool**: Power BI Desktop
- **Scripting Language**: DAX

---

## ✅ Key Insights

- YOY growth trends and median pricing help assess market health.
- Filters by region, quarter, and sales type support dynamic analysis.
- Key influencers highlight pricing drivers (e.g., age group, house type).
- Type-wise metrics enable detailed comparison across housing categories.

---

## 🚀 How to Use

1. Open the `.pbix` file in Power BI Desktop.
2. (Optional) Replace dataset with updated BigQuery CSV.
3. Use slicers to explore trends by:
   - **Region**
   - **Sales Type**
   - **House Type**
   - **Quarter & Year**
