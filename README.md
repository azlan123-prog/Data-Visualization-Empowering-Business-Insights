# Retail Revenue Analysis and Data Visualization — Tata Consultancy Services Job Simulation

## Executive Summary

This project was completed as part of the Tata Consultancy Services Data Visualisation job simulation on Forage. The dataset contains transactional retail data spanning 2010-2011, comprising over 500,000 records across eight fields including invoice number, stock code, quantity, unit price, customer ID, and country. The analysis was commissioned to support executive decision-making around seasonal planning, international market prioritization, customer retention, and global expansion strategy.

---

## Core Objectives

The following four business questions were defined by the simulated CEO and CMO:

1. Identify monthly revenue trends for the year 2011 to understand seasonality and support forecasting for the following year.
2. Identify the top 10 revenue-generating countries excluding the United Kingdom, with quantity sold displayed alongside revenue figures.
3. Rank the top 10 customers by revenue in descending order to support targeted retention efforts.
4. Visualize global product demand by country on a single-view map, excluding the United Kingdom, to identify international expansion opportunities.

---

## Technical Methodology

### Data Source

- Format: CSV (Online_Retail_Data_Set.csv)
- Tool: Microsoft Power BI Desktop
- Records: 500,000+ retail transactions

### Data Cleaning and Preparation

Before any visual modeling, the raw dataset was filtered to remove two categories of invalid records:

- Negative quantity values: These represented customer returns and would have artificially deflated revenue calculations if included.
- Zero or negative unit prices: These were identified as data entry errors with no valid business interpretation.

Both filters were applied inside Power Query Editor using the Filter Rows function:
- Quantity: kept rows where value is greater than or equal to 1
- UnitPrice: kept rows where value is greater than 0

A custom DAX measure was created to calculate revenue at the row level:

```DAX
Revenue = SUMX(
    'Online Retail Data Set (1)',
    'Online Retail Data Set (1)'[Quantity] * 'Online Retail Data Set (1)'[UnitPrice]
)
```

### Visual Architecture

**Tab 1 — Revenue Trends 2011**
- Visual type: Line chart
- X-axis: InvoiceDate (Month hierarchy only, Year and Quarter removed)
- Y-axis: Revenue (DAX measure)
- Filter applied: InvoiceDate Year = 2011 using basic filter on visual level

**Tab 2 — Top 10 Markets by Revenue**
- Visual type: Clustered bar chart
- Y-axis: Country
- X-axis: Revenue and Sum of Quantity
- Filter applied: Top N filter set to 10 by Revenue, United Kingdom manually excluded via basic country filter

**Tab 3 — Top 10 Customers by Revenue**
- Visual type: Clustered bar chart
- Y-axis: CustomerID
- X-axis: Revenue
- Filter applied: Top N filter set to 10 by Revenue
- Sort applied: Descending by Revenue (Z to A)

**Tab 4 — Global Demand Map**
- Visual type: Map visual (enabled via File > Options > Security > Use Map and Filled Map visuals)
- Location: Country
- Bubble size: Sum of Quantity
- Filter applied: United Kingdom excluded via basic country filter

---

## Dashboard Screenshots

# Revenue Trends 2011
<img width="1017" height="801" alt="Screenshot 2026-05-24 230313" src="https://github.com/user-attachments/assets/9137f851-7cdf-42bd-88ef-4f160c297722" />


# Top 10 Markets by Revenue
<img width="1023" height="805" alt="Screenshot 2026-05-24 230329" src="https://github.com/user-attachments/assets/c034107c-a3a5-4448-87e3-5e2b52c3b8d7" />


# Top 10 Customers by Revenue
<img width="1015" height="790" alt="Screenshot 2026-05-24 230342" src="https://github.com/user-attachments/assets/92f09be0-f8f0-4f36-a4c6-ef4bb3518e76" />


# Global Demand Map
<img width="1029" height="815" alt="Screenshot 2026-05-24 230353" src="https://github.com/user-attachments/assets/f75a1a89-e440-4eb7-90e0-b83a4fa5907c" />

## Strategic Recommendations

**Seasonal Planning**
Revenue data for 2011 shows a consistent baseline from January through August followed by a sharp increase beginning in September and peaking in November. This pattern indicates strong Q4 holiday-driven demand. Inventory procurement, staffing, and promotional campaigns should be structured to align with this ramp-up period beginning no later than August.

**International Market Investment**
Excluding the United Kingdom, the Netherlands generates the highest revenue among all markets, followed by EIRE, Germany, France, and Australia. These five markets represent the strongest candidates for increased marketing spend and partnership development given their demonstrated revenue performance without equivalent levels of targeted investment.

**Customer Retention**
The top 10 customers by revenue show a significant drop-off between the highest-value customer and those ranked below. A disproportionate share of revenue is concentrated in a small customer segment. A structured retention program covering personalized outreach, loyalty incentives, or dedicated account management would reduce churn risk in this segment.

**Expansion Strategy**
The global demand map confirms that Western Europe carries the highest order volume concentration outside the United Kingdom. Secondary demand clusters are visible in Australia and isolated markets across Asia. Expansion efforts should prioritize Western Europe first given existing demand momentum, followed by Australia where order volume already indicates market receptiveness.

---

## Tools and Technologies

- Microsoft Power BI Desktop
- Power Query Editor
- DAX (Data Analysis Expressions)
- CSV data processing

---

## Certification

Tata Data Visualisation: Empowering Business with Effective Insights
Issued by Forage — May 2026
Credential ID: kynAj82MePuec7Jwc
