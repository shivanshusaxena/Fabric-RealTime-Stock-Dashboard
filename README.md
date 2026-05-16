# Fabric Real-Time Stock Dashboard

Real-time stock price monitoring pipeline built on Microsoft Fabric using Eventstream, KQL Database and Real-Time Dashboard.

---

## Architecture

Sample Stock Data (Fabric built-in)
↓
Eventstream (real-time ingestion)
↓
KQL Database / Eventhouse (time-series storage)
↓
KQL Queries (data transformation)
↓
Real-Time Dashboard (live visualization)
↓
Activator (alerts and triggers)


---

## What It Does

- Ingests real-time stock price data using Fabric Eventstream
- Stores streaming data in KQL Database (Eventhouse)
- Queries data using KQL — Kusto Query Language
- Visualizes live stock prices on Real-Time Dashboard with auto-refresh
- Configured Activator for price alerts and triggers

---

## Tech Stack

- Microsoft Fabric
- Eventstream
- KQL Database (Eventhouse)
- Kusto Query Language (KQL)
- Real-Time Dashboard
- Activator

---

## KQL Queries Used

```kql
-- Price over time
Stock
| where lastUpdated > ago(1h)
| summarize avgPrice = avg(lastSalePrice) by bin(lastUpdated, 1m), symbol
| order by lastUpdated asc

-- Average price by symbol
Stock
| summarize avgPrice = avg(lastSalePrice) by symbol
```

---

## Dashboard

Real-time line chart showing price movement for BMZM, HOOJ and NSFT stocks over last 1 hour with auto-refresh.

---

## Author

**Shivanshu Saxena**
Data Engineer | Microsoft Fabric • PySpark • Power BI | PL-300 Certified
[GitHub](https://github.com/shivanshusaxena)