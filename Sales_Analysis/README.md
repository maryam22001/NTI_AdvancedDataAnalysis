# 📊 Sales Data Analysis Dashboard - README

## 🎯 Purpose
This Power BI project provides comprehensive sales analytics with a focus on customer segmentation, order prioritization, and profitability tracking. The dashboards enable data-driven decision making through interactive visualizations of key business metrics.

## 📂 Project Overview

### Core Dashboards
1. **Customer & Order Analysis**
   - Geographic customer distribution
   - Product-customer interactions
   - Discount impact analysis

2. **Shipping & Returns**
   - Cost by shipping mode/region
   - Return reason analysis
   - On-time delivery tracking

3. **Sales Performance**
   - Revenue vs. profit trends
   - Category performance
   - Target achievement

4. **Customer & Product Segmentation**
   - VIP customer identification
   - Product naming standardization
   - Priority order analysis

## 🔧 Implementation Details

### Key Features
- **VIP Customer Classification**
  ```DAX
  Customer Type = IF([Total Sales]>5000,"VIP","Normal")
  ```
  - Gold-highlighted cards track VIP metrics
  - Slicers for dynamic filtering

- **Product Name Standardization**
  ```powerquery
  ProductNameNoSpaces = Text.Remove([Product Name], {" "})
  ```
  - Side-by-side comparison table
  - Conditional formatting flags discrepancies

- **High-Priority Order Tracking**
  ```DAX
  High Priority Sales = CALCULATE([Total Sales], Orders[Order Priority]="High")
  ```
  - Donut chart visualization (30.6% of sales)
  - Red/gray color coding

- **Profitability Metrics**
  ```DAX
  Net Profit = SUM(Orders[Profit]) - SUM(Orders[Shipping Cost])
  Profit Ratio = DIVIDE([Net Profit], [Total Sales], 0)
  ```
  - Trend analysis by month
  - Segment breakdown (Corporate leads at $18K)

## 📊 Visual Components

| **Visual** | **Purpose** | **Key Fields** |
|------------|------------|----------------|
| Donut Chart | Priority order mix | High Priority Sales, Order Priority |
| Histogram | Customer order frequency | Customer Orders Count, Order bins |
| Line Chart | Profit trend | Profit Ratio, Month |
| Comparison Table | Product name cleanup | Product Name, ProductNameNoSpaces |

## 🛠 Technical Implementation

### Data Modeling
- Star schema with Orders as fact table
- Relationships:
  - Orders → Products (Product ID)
  - Orders → Customers (Customer ID)

### Performance Optimization
- Calculated columns in Power Query where possible
- DAX measures for dynamic calculations
- Conditional formatting for visual alerts

## 🎨 Design System

| **Element** | **Color** | **Hex Code** |
|-------------|----------|--------------|
| Primary | Deep Blue | #1F4E79 |
| Secondary | Teal Green | #2C786C |
| VIP Highlight | Gold | #FFD700 |
| High Priority | Red | #FF6B6B |
| Warning | Amber | #FFC000 |

## 🚀 Getting Started

1. Open `.pbix` in Power BI Desktop
2. Review Power Query transformations
3. Refresh data connections
4. Interact with slicers/filters
5. Drill through visual hierarchies

## 🔍 Troubleshooting

| **Issue** | **Solution** |
|-----------|-------------|
| Blank high-priority data | Verify "High" values exist in Order Priority |
| Incorrect profit ratios | Check shipping cost deduction in Net Profit |
| Name cleanup errors | Audit Power Query for special characters |

## 📅 Future Enhancements
- Predictive forecasting
- Dynamic what-if analysis
- Mobile-optimized layouts
- Automated data alerts


