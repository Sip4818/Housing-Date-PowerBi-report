# 🏠 House Market Analytics – Power BI Report

This Power BI report delivers deep insights into the **Danish housing market**, analyzing sales trends, pricing metrics, property types, and regional dynamics using ~100,000 rows of housing data from **Google BigQuery**.

---

## 📁 Dataset Overview

- **Source**: Google BigQuery (CSV format)
- **Volume**: ~100,000 rows × 19 columns (Columns A–S)
- **Key Features**: `date`, `region`, `purchase_price`, `offer_price`, `sqm`, `sqm_price`, `sales_type`, `house_type`, `age`

---

## 📊 Page 1 – House Market Overview

### 🔍 Visuals
- Median Sales Change by Region
- Units Sold in Latest Year & Quarter
- Sales in Last 12 Months
- Offer vs Purchase Price
- YOY Sales Growth by Sales Type

### 🧠 Insights

- 🔼 **Positive YOY Median Price Change** in regions indicates rising demand.
- 💰 **Offer vs Purchase Price gaps** highlight negotiation trends and market competitiveness.
- 🏘️ **High sales concentration** found in certain regions and quarters, useful for targeting investments.
- 📈 **YOY sales growth** signals market expansion or contraction depending on sales type.

### 📸 Screenshot – House Market Overview  
![image](https://github.com/user-attachments/assets/e3c2d488-5eb4-4fa4-8651-a07ed932d7e1)


---

## 📊 Page 2 – Sales Performance

### 🔍 Visuals
- Sales by Region
- Key Influencers (AI Visual)
- YTD Sales Table
- Offer-to-SQM Ratio by Sales Type
- Avg SQM Price by Region

### 🧠 Insights

- 🏙️ **Region-wise sales breakdown** reveals top-performing geographic areas.
- 🤖 **AI Key Influencers** identify key drivers affecting house prices (e.g., age, house type).
- 🕐 **YTD sales tracking** provides real-time performance against past benchmarks.
- 📏 **Offer-to-SQM ratio** helps assess value perception per square meter.
- 💡 **High SQM price regions** may indicate urban centers or luxury zones.

### 📸 Screenshot – Sales Performance  
`![Sales Performance](path/to/screenshot2.png)`

---

## 📊 Page 3 – House Type Insights

### 🔍 Visuals
- Avg Offer & Purchase Price by House Type
- Inflation / Interest Rate / Yield by House Type
- Avg SQM and SQM Price by House Type

### 🧠 Insights

- 🏡 **Detached houses** generally have higher average purchase prices.
- 🔄 **Yield comparisons** across house types highlight investment potential.
- 📉 **Interest rate trends** impact housing affordability and price shifts.
- 📐 **SQM-based comparison** helps buyers evaluate per-unit value by property category.

### 📸 Screenshot – House Type Insights  
`![House Type Insights](path/to/screenshot3.png)`

---

## 🛠️ Tools & Tech Stack

- **Data Source**: Google BigQuery (CSV)
- **BI Platform**: Power BI Desktop
- **Scripting**: DAX Measures
- **AI Visuals**: Key Influencers Chart (Power BI)

---

## 🚀 How to Use

1. Open `.pbix` file in Power BI Desktop.
2. Navigate through pages to explore different dimensions of the housing market.
3. Use slicers for filters:
   - **Region**
   - **Sales Type**
   - **House Type**
   - **Quarter & Year**

---

Let me know if you'd like me to export this as a `.md` file or convert it for GitHub/Notion integration.
