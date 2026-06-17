# Postgres_data_warehouse_project

Welcome to the **Data Warehouse and Analytics Project** repository! 🚀  
This project demonstrates a comprehensive data warehousing and analytics solution, from building a data warehouse to generating actionable insights. Designed as a portfolio project, it highlights industry best practices in data engineering and analytics.

**My notion link to view my speration of concern**
https://www.notion.so/Data-Warehouse-project-361c00e0955480c99a48cc472c2fe590?source=copy_link

## 🏗️ Data Architecture

The data architecture for this project follows Medallion Architecture **Bronze**, **Silver**, and **Gold** layers:



## project Requirments: 
**Objective**

Develop a modern data warehouse using SQL Server to consolidate sales data, enabling analytical reporting and informed decision Making.

**Specifications**
• Data Sources: Import data from two source systems (ERP and CRM) provided as CSV files.
• Data Quality: Cleanse and resolve data quality issues prior to analysis.
• Integration: Combine both sources into a single, user-friendly data model designed for analytical queries.
• Scope: Focus on the latest dataset only; historization of data is not required.
• Documentation: Provide clear documentation of the data model to support both business stakeholders and analytics teams.

Once the project requirements are understood, update in the Notion to complete the task & Epic 
[Epic - Requirement Analysis ] ---> [Task - Analyse and understand the requirements] 

## Design the Data Architecture: 

Data Architecture approach: 
Data Warehouse ------|  
Data Lake      ------| 
Data lakehouse ------|
Data mesh      ------| 

In this project i will be doing Data Warehouse project, In data warehouse project there four approach mentioned below: 
1) Inmon 
 Approach : Inmon
 Main Idea : Build an enterprise-wide centralized data warehouse.
 Modeling Style : first	Normalized model (3NF).
 Best For : Large enterprises needing consistency.
 Strengths : Single source of truth, strong governance, scalable for enterprise reporting.
 Weaknesses : Slow implementation, complex, expensive.

2) Kimball 
  Approach : Kimball
  Main Idea : Build business-focused data marts first.
  Modeling Style : Dimensional model (Star/Snowflake schema).
  Best For : BI dashboards, analytics, reporting. 
  Strengths : Faster delivery, easy querying, high performance.
  Weaknesses : Data silos possible, integration challenges.

3) Data Vault
  Approach : Data Vault
  Main Idea : Store historical, auditable data with flexibility.
  Modeling Style : 	Hubs, Links, Satellites
  Best For : Changing business rules, big enterprise systems. 
  Strengths : Highly scalable, audit-friendly, easy schema evolution.
  Weaknesses : Complex model, harder for business users.

5) Medallion Architecture
  Approach : Medallion Architecture
  Main Idea : Layered data refinement in lakehouse systems.
  Modeling Style: 	Bronze → Silver → Gold
  Best For : Big data, cloud analytics, streaming pipelines.
  Strengths : Easy data quality management, scalable, supports ML.
  Weaknesses : Not a traditional warehouse model, governance needed.

--------------------================================================-----------------------------------------------------

General Principles
• Naming Conventions: Use snake_case, with lowercase letters and underscores (_) to separate words.
• Language: Use English for all names.
• Avoid Reserved Words: Do not use SQL reserved words as object names.

Table Naming Conventions
Bronze Rules
• All names must start with the source system name, and table names must match their original names without renaming.
• ‹sourcesystem›_‹entity>
•‹sourcesystem>: Name of hisource system (e.g., crm, erp).
• ‹entity› : Exact table name from the source system.
• Example: crm_customer_info → Customer information from the CRM system.

Silver Rules
• All names must start with the source system name, and table names must match their original names without renaming.
• ‹sourcesystem›_‹entity>
• ‹sourcesystem› : Name of the source system (e.g., crm, erp).
• ‹entity> : Exact table name from the source system.
• Example: crm_customer_info → Customer information from the CRM system.

Gold Rules
• All names must use meaningful, business-aligned names for tables, starting with the category prefix.
• ‹category>_‹entity›
• ‹category» : Describes the role of thrtable, such as dim (dimension) or fact (fact table).
• ‹entity› : Descriptive name of the table, aligned with the business domain (e.g., customers, products, sales).
• Examples:
• dim_customers → Dimension table for customer data.
• fact_sales → Fact table containing sales transactions.


**Glossary of Category Patterns**

Dimension table:  dim_customer, dim_product
fact_          :  Fact table, fact_sales
agg_           :  Aggregated table, agg_customers, agg_salesmonthly

**Column Naming Conventions**

**Surrogate Keys**
• All primary keys in dimension tables must use the suffix _key .
• <tablename>key
• <table_name›: Refers to the name of the table or entity the key belongs to.
• _key : A suffix indicating that this column is a surrogate key.
• Example: customer_key → Surrogate key in the dim_customers table.

**Technical Columns**
• All technical columns must start with the prefix dwh_, followed by a descriptive name indicating the column's purpose.
• dwh_‹column_name›
• dwh: Prefix exclusively for system-generated metadata.
• ‹column_name› : Descriptive name indicating the column's purpose.
• Example: dwh_load_date → System-generated column used to store the date when the record was loaded.

**Stored Procedure**
• All stored procedures used for loading data must follow the naming pattern:
• load_<layer› •
• < layer›: Represents the layer being loaded, such as bronze, silver, or gold.
• Example:
• load_bronze → Stored procedure for loading data into the Bronze layer.
• load_silver Stored procedure for loading data into the Silver layer.


--------------------================================================-----------------------------------------------------

**Create Datebase and schema. **

Next Step refer Script folder to view the Code to create datae base and Schema. 


--------------------================================================-----------------------------------------------------

**Starting with Bronze Layer : **

first task: Analysing source system --> refer this 'drawio' for Analysis source model for our warehouse project. 

second task: Data ingestion -- > Refer the script file in GIT for DDL.
> Creating DDL sql scrpit for all CSV files in the and CRM and ERP systems.
> Create tables using our naming conversation patter.
> Insert bulk data into the table.

**Table names for reference:**
> bronze.crm_cust_info
> bronze.crm_prd_info
> bronze.crm_sales_details
> bronze.erp_cust_az12
> bronze.erp_loc_a101
> bronze.erp_px_cat_g1v2


 







  
