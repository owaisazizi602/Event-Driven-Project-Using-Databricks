# Event-Driven-Project-Using-Databricks



Tech Stack:

PySpark / Spark SQL – distributed ETL processing

Delta Lake – incremental, ACID-compliant data storage

Databricks Utilities (dbutils) – pipeline orchestration and task logging

Python – ETL scripting and safe data handling

JSON – structured processing logs




This project implements a fully event-driven ETL and analytics pipeline for e-commerce operations, capable of processing multiple source files as soon as they arrive. It leverages PySpark, Delta Lake, and Databricks utilities to ensure reliable, incremental, and fault-tolerant data processing.

The pipeline is triggered automatically when a new file arrives (using a touch file trigger) and executes the following steps:

Source File Ingestion:

Automatically detects new files for orders, customers, products, inventory, and shipping.

Initiates the pipeline immediately when a new file is available.

Data Validation:

Performs schema validation, type checks, and quality checks.

Filters invalid or malformed records to ensure clean, reliable data for downstream processing.

Data Enrichment:

Combines multiple source datasets to derive additional insights.

Calculates metrics such as estimated CLV, order profit margin, and aggregates customer, product, and seasonal metrics.

SC2 Merge (Final Merge Operation):

Applies the SC2 merge strategy to update existing Delta tables incrementally.

Ensures transactional consistency while merging new or updated records into the analytics tables.

Analytics Summary & Reporting:

Computes KPIs such as total orders, total revenue, average order value, profit margin, revenue per customer, and orders per customer.

Generates segment-level, seasonal, and product-category analyses.

Writes results to Delta tables for BI consumption.

Event-Driven Logging:

Maintains a processing log recording task status, timestamps, total records, valid records, and metadata of processed files.

Integrates with Databricks dbutils.jobs.taskValues for orchestrating downstream tasks and monitoring pipeline status.

Error Handling & Data Safety:

Uses try_divide() and coalesce() in Spark to safely handle division by zero and NULL values.

Implements safe Python conversions to avoid runtime errors when printing or writing metrics.
