# finance-data-Projects

#  Finance Data Warehouse using Snowflake

##  Project Overview
This project demonstrates the design and implementation of a **finance data warehouse** using **Snowflake** and **dimensional modeling (Star Schema)** principles.  
The goal is to transform raw transactional data into an **analytics-ready structure** for BI reporting.

---

##  Business Objective
Enable business teams to analyze:
- Customer transaction behavior
- Account-level performance
- Channel-wise transaction volume
- Financial trends over time

---

##  Data Model (Star Schema)

### Dimensions
- **DIM_CUSTOMERS**
  - Stores customer descriptive attributes
  - Uses surrogate keys for performance
- **DIM_FINANCE**
  - Stores account-level attributes
  - Bridges customers and transactions

### Fact Table
- **FACT_TRANSACTIONS**
  - Stores transaction-level metrics
  - References dimensions using surrogate keys

---

##  ETL Approach :

1. **Load Dimensions First**
   - Extract distinct records from source systems
   - Generate surrogate keys using AUTOINCREMENT

2. **Load Fact Table**
   - Use TRANSACTIONS as the driving table
   - Join to account dimension using ACCOUNT_ID
   - Derive customer through account dimension
   - Use LEFT JOINs to prevent data loss
   - Assign default surrogate key (-1) for missing dimensions


##  How to Run This Project

1. Create database and schema in Snowflake
2. Execute SQL scripts in order:
   ```sql
   01_create_dim_customers.sql
   02_create_dim_finance.sql
   03_create_fact_transactions.sql
   04_load_dimensions.sql
   05_load_fact_transactions.sql
