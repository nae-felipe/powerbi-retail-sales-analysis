# powerbi-retail-sales-analysis
Power BI dashboard analyzing 5 years of sales data for a global electronics retailer. Identifies revenue drivers, seasonal trends, and delivery performance using DAX and star schema modeling.
# Global Electronics Retail Analysis

Power BI dashboard analyzing 5 years of sales data to identify revenue drivers and seasonal trends for a global electronics retailer.

---

## Key Findings

- **Revenue Leader:** Computers generated $19.3M, with Desktops performing $201K above average
- **Seasonal Pattern:** Sales peak November-January, then dip February-April
- **Market Concentration:** US, UK, and Germany account for 76% of total orders
- **Channel Performance:** In-store AOV only 4.6% higher than online - showing strong digital potential
- **Delivery Time:** Average 5 days across all countries

---

## Business Recommendations

1. Maintain inventory levels during November-January peak season
2. Strengthen online marketing - AOV nearly matches in-store sales
3. Focus on high-performing categories (Computers, Desktops) and markets (US, UK, Germany)
4. Reevaluate underperforming categories: Games & Toys, Computer Accessories, Fans & Lamps

---

## Technical Skills Demonstrated

**Tools:** Power BI, Power Query, DAX

**Data Modeling:**
- Star schema design with 1 fact table (Sales) and 4 dimension tables
- Custom Calendar table for time-intelligence analysis

**Key DAX Measures:**
```dax
Total Revenue = SUMX(Sales, Sales[Quantity] * RELATED(Products[Unit Price USD]))

AOV = DIVIDE([Total Revenue], [Total Orders])

Average Delivery Days = AVERAGEX(
    FILTER(Sales, NOT(ISBLANK(Sales[Delivery Date])) && NOT(ISBLANK(Sales[Order Date]))),
    DATEDIFF(Sales[Order Date], Sales[Delivery Date], DAY)
)
```

**Visualizations:**
- Line charts for trend analysis
- Bar/column charts for category comparisons  
- Donut chart for channel performance
- AI visuals (Smart Narrative, Key Influencers)
- Interactive bookmarks and tooltips

---

## Dataset

**Source:** [Maven Analytics - Global Electronics Retailer](https://mavenanalytics.io/data-playground/global-electronics-retailer)

**Period:** 2016-2021

**Tables:** Sales, Products, Customers, Stores, Calendar (custom), Measure (custom)

---

## Project Files
```
├── README.md
├── reports/
│   └── Global_Electronics_Dashboard.pbix
└── images/
    └── dashboard_screenshots.png
```

---

**Note:** 86% of delivery dates are missing, likely representing pending or cancelled orders. All metrics standardized to USD.
