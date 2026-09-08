#SQL Data Warehouse Project

Overview

This project is an end-to-end data warehouse built in MySQL using CRM and ERP source data. I developed it to practise data engineering: loading raw files, cleaning inconsistent records, integrating related datasets, building an analytical model, and validating the results.

The warehouse follows a layered architecture:

Bronze layer: Stores the raw CRM and ERP data imported from CSV files.

Silver layer: Cleans, standardizes, and prepares the source data.

Gold layer: Organizes the transformed data into customer and product dimensions with a sales fact view for analysis.

Data Transformation

The silver-layer process handles duplicate customers, missing values, unwanted spaces, hidden CSV characters, inconsistent codes, and invalid dates. Gender, marital status, product lines, countries, and identifiers are standardized across the source systems.

Product keys are separated into category and standalone identifiers, while product history is managed using window functions. Invalid sales and price values are recalculated from quantity, price, and sales information when possible.

Gold Layer

The gold layer combines CRM and ERP data into:

dim_customers — customer identity, demographics, marital status, location, and creation date.

dim_products — product details, categories, maintenance information, cost, and product history.

facts_sales — sales transactions connected to customer and product surrogate keys.

Data Quality

Separate validation scripts check:

Missing and duplicate identifiers

Invalid product and sales dates

Incorrect sales calculations

Null surrogate keys

Missing customer, product, and category relationships

Unexpected row increases caused by joins

Row-count differences between warehouse layers

These tests helped identify genuine source-data issues, including products without matching ERP categories and historical product records that affected gold-layer joins.

Tools and Techniques

MySQL, MySQL Workbench, Git, GitHub, CTEs, window functions, joins, subqueries, regular expressions, CASE expressions, and string/date functions.

Running the Project

Run the scripts in this order:

Create and load the bronze layer.

Create and load the silver layer.

Run the silver validation tests.

Create the gold-layer views.

Run the gold validation tests.

Author

Aderinwale John O.
