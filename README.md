# Bike Share Data Analysis Project

![Dashboard](garbage\Dashboard.png)

## Project Overview

The **Bike Share Data Analysis Project** focuses on analyzing bike-sharing data to understand trends in revenue, seasonal performance, and rider demographics. The goal is to create a database from Excel files, connect it to Power BI, and build a dashboard that shows important metrics. We aim to provide recommendations on whether to raise prices for the next year based on our analysis.

> **Prepared for Dashboard Development**  
> **Objective:** Help leadership understand performance metrics and make informed decisions.

---

## `Insights`
## 🕐 1. Hourly Revenue Analysis

### 🔍 Key Findings:
- **Peak Hours** for revenue: **8–10 AM** and **5–7 PM**
- These hours match **commute times**, indicating high usage by **office workers**.
- **Low Revenue Hours**: Late night (10 PM–5 AM) — fewer rides, possibly due to safety or lack of demand.

### 📌 Recommendation:
- Consider promotional offers during **off-peak hours** to improve usage.
- Add more bikes during peak hours to avoid stock-outs.

---

## 📈 2. Profit and Revenue Trends

### 🔍 Key Findings:
- **Overall Monthly Revenue** shows growth but dips in **Winter months**.
- **Highest Revenue Months**: May to September (Summer season).
- **Profit** follows a similar pattern — high in summer, drops in winter due to lower ridership and fixed maintenance costs.

### 📌 Recommendation:
- Introduce **seasonal pricing**: Lower prices in winter to maintain ridership.
- Raise prices moderately in summer — demand is strong.

---

## 🌦️ 3. Seasonal Revenue Patterns

### 🔍 Key Findings:
- **Summer** (June–August) = 📈 highest revenue (~40% of annual total).
- **Winter** (December–February) = 📉 lowest revenue (~15–20%).

### 📌 Recommendation:
- **Plan marketing campaigns** around spring and summer.
- Offer **winter subscription discounts** to retain loyal customers.

---

## 👥 4. Rider Demographics

### 🔍 Key Findings:
- **Gender Distribution**:
  - **60% Male**, **38% Female**, 2% Other/Unspecified.
- **Age Groups**:
  - Most riders: **25–34 years** (~40%)
  - Followed by **35–44 years** (~25%)
- **Customer Types**:
  - **Subscribers (70%)** bring in more consistent revenue than **Casual Riders (30%)**.

### 📌 Recommendation:
- Target marketing to **young professionals (25–44 age group)**.
- Provide **loyalty benefits** to retain subscribers.
- Create offers to convert casual riders into subscribers.

---

## Data Analysis Workflow

The project follows these main steps:

1. **Create a Database**: Set up a SQL database to store bike share data.
2. **Import Data**: Load data from Excel files into the database.
3. **Develop SQL Queries**: Write SQL queries to analyze the data.
4. **Connect to Power BI**: Link the SQL database to Power BI for visualization.
5. **Build a Dashboard**: Create a dashboard in Power BI to display key metrics.
6. **Analyze and Recommend**: Analyze the data to provide recommendations on pricing.

## Database Creation

We start by creating a SQL database called **Bike Data**. This database will hold all the information related to bike sharing, including:

- **Rider Information**: Details about the riders, such as their demographics and usage patterns.
- **Revenue Data**: Information on how much money is made from bike rentals.
- **Cost Data**: Data about the costs of running the bike-sharing service.

## Data Import and SQL Query Development

After creating the database, we import data from Excel files. This is done using SQL Server Management Studio (SSMS). The data is organized into tables for easy access.

### SQL Query Development

We write SQL queries to extract and analyze the data. Key tasks include:

- **Selecting Data**: Using `SELECT` statements to get specific information from the database.
- **Joining Tables**: Combining data from different tables to get a complete view.
- **Aggregating Data**: Calculating totals and averages to summarize the data.
- **Using Common Table Expressions (CTEs)**: Making complex queries easier to read.

```sql
WITH CTE AS (
    SELECT * FROM bike_share_yr_0
    UNION ALL
    SELECT * FROM bike_share_yr_1
)
SELECT
    dteday,
    season,
    a.yr,
    weekday,
    hr,
    rider_type,
    riders,
    price,
    COGS,
    riders * price AS revenue,
    riders * price - COGS * riders  AS profit
FROM CTE a
LEFT JOIN cost_table b ON a.yr = b.yr;
```
## Power BI Dashboard Creation

Next, we create a dashboard in Power BI to visualize the data. This dashboard helps users understand key metrics at a glance.

### Dashboard Features

The dashboard includes:

- **Key Metrics**: Displays important numbers like total revenue and average profit.
- **Revenue Analysis**: Shows how revenue changes by hour and season.
- **Demographic Insights**: Visualizes rider demographics to understand the audience better.
- **Interactive Filters**: Allows users to filter data by year or other criteria.

---
