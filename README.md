# 🔷 End-to-End Azure Data Engineering Project – Retail Analytics

This project demonstrates a complete, **production-grade Azure Data Engineering solution** using the **Medallion Architecture (Bronze → Silver → Gold)**. It simulates a real-world retail client scenario where data is ingested from multiple sources, transformed using PySpark, and visualized using Power BI.

---

## 📊 Business Requirement

A retail client needs a unified analytics pipeline to consolidate data from:
- **Azure SQL Database**: `transactions`, `products`, `stores`
- **REST API**: Customer data in JSON format

---

## 🏗️ Architecture Overview

         +------------------+
         | Azure SQL & API  |
         +--------+---------+
                  |
                  ▼
    +-----------------------------+
    | Azure Data Factory (ADF)    |
    | - Ingest SQL & API data     |
    | - Load into ADLS as Parquet |
    +--------------+--------------+
                   |
                   ▼
    +-------------------------------+
    | Azure Data Lake Gen2 (ADLS)   |
    | ├── /bronze                   |
    | ├── /silver                   |
    | └── /gold                     |
    +-------------------------------+
                   |
                   ▼
    +-----------------------------+
    | Azure Databricks (PySpark) |
    | - Clean, Join, Transform    |
    | - Medallion Architecture    |
    +-------------+---------------+
                  |
                  ▼
           +--------------+
           | Power BI     |
           | Dashboards   |
           +--------------+

---

## 🧰 Tech Stack

| Tool               | Usage                                 |
|--------------------|----------------------------------------|
| **Azure Data Factory** | Data ingestion from SQL & API       |
| **Azure SQL DB**       | Source for transactions, products, stores |
| **Azure Data Lake (Gen2)** | Storage for Bronze/Silver/Gold layers |
| **Azure Databricks**   | PySpark transformations (Delta Lake) |
| **Power BI**           | Data visualization from Gold layer   |

---

## 🧱 Medallion Architecture

| Layer   | Description                                      |
|---------|--------------------------------------------------|
| Bronze  | Raw data ingestion from SQL and API              |
| Silver  | Cleaned and joined data (type casting, deduping) |
| Gold    | Aggregated business metrics for analytics        |

---

## 📁 Folder Structure

/bronze/
├── customers/
├── products/
├── stores/
└── transactions/

/silver/
└── cleaned_transactions/ ← joined & cleaned dataset

/gold/
└── sales_summary/ ← business KPIs


---

## 📈 Power BI Dashboard

- Total Sales Amount
- Quantity Sold
- Number of Transactions
- Avg. Transaction Value
- Sales by Product, Store, Category, Date


## 📊 Power BI Dashboard


![Power BI Dashboard](https://raw.githubusercontent.com/alicorduk/DataEngineer/main/PowerBI-%20Dashboard.jpg)


---

## 🧠 Skills Practiced

✅ Azure Cloud Architecture  
✅ Data Ingestion via ADF  
✅ API + SQL integration  
✅ PySpark DataFrame transformations  
✅ Delta Lake table creation  
✅ Visualization in Power BI  
✅ Medallion Architecture  

---

## 🚀 How to Run

> Note: Requires Azure subscription and Databricks workspace

1. Deploy Azure SQL DB and load source data  
2. Set up Azure Data Lake Gen2 with `bronze`, `silver`, `gold` containers  
3. Use ADF to ingest SQL & API data into ADLS  
4. Run Databricks notebooks to process Bronze → Silver → Gold  
5. Connect Power BI to the Gold layer and build visuals

---

