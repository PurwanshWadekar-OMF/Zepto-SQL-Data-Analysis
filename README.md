# Zepto SQL Data Analysis

## 📌 Project Overview

This project explores Zepto product inventory data using SQL to uncover insights into product pricing, discounts, stock availability, category-wise revenue, and inventory weight.

The project uses PostgreSQL to perform data exploration, data cleaning, and business-oriented analysis. It demonstrates practical SQL skills, including aggregation, filtering, grouping, conditional expressions, and data manipulation.

## 🎯 Project Objectives

- Explore product inventory and understand the dataset structure.
- Identify missing values and duplicate product names.
- Clean product pricing data.
- Analyze product discounts and identify the best-value products.
- Estimate revenue by product category.
- Examine out-of-stock products with high maximum retail prices (MRP).
- Calculate price per gram to compare product value.
- Analyze inventory weight across product categories.

## 🛠️ Technologies Used

- **Database:** PostgreSQL
- **Language:** SQL
- **Dataset:** Zepto product inventory data (CSV)

## 📂 Project Structure

```text
Zepto-SQL-Data-Analysis/
├── Zepto_SQL_data_analysis.sql
├── zepto_v2.csv
└── README.md
```

## 🗄️ Database Schema

The project uses a table named `zepto` with the following columns:

| Column | Data Type | Description |
|---|---|---|
| `sku_id` | SERIAL PRIMARY KEY | Unique product SKU identifier |
| `category` | VARCHAR(120) | Product category |
| `name` | VARCHAR(150) | Product name |
| `mrp` | NUMERIC(8,2) | Maximum retail price |
| `discountPercent` | NUMERIC(5,2) | Discount percentage |
| `availableQuantity` | INTEGER | Available inventory quantity |
| `discountedSellingPrice` | NUMERIC(8,2) | Selling price after discount |
| `weightInGms` | INTEGER | Product weight in grams |
| `outOfStock` | BOOLEAN | Indicates whether the product is out of stock |
| `quantity` | INTEGER | Product quantity field from the dataset |

## 🔍 Analysis Workflow

### 1. Data Exploration

The initial queries examine the dataset and help establish its quality and structure.

- Count the total number of records.
- Inspect sample product records.
- Identify missing values.
- Retrieve distinct product categories.
- Compare in-stock and out-of-stock products.
- Find product names associated with multiple SKUs.

### 2. Data Cleaning

The SQL script performs the following cleaning operations:

- Identifies products with zero MRP or selling price.
- Removes records with zero MRP.
- Converts MRP and discounted selling prices from paise to rupees.

**Note:** The script assumes the price values are stored in paise before conversion. Verify the source data's units before running the update. Also, the current deletion removes records with zero MRP but does not remove records where only the discounted selling price is zero.

### 3. Business Analysis

The project addresses eight analytical questions.

| Query | Business Question | SQL Concepts |
|---|---|---|
| Q1 | What are the top 10 best-value products based on discount percentage? | `DISTINCT`, `ORDER BY`, `LIMIT` |
| Q2 | Which high-MRP products are out of stock? | `WHERE`, Boolean filtering |
| Q3 | What is the estimated revenue for each category? | `SUM()`, `GROUP BY` |
| Q4 | Which products have an MRP above ₹500 and a discount below 10%? | Multiple conditions, filtering |
| Q5 | Which five categories offer the highest average discount? | `AVG()`, `ROUND()`, `GROUP BY` |
| Q6 | What is the price per gram for products weighing at least 100 grams? | Calculated columns, `ROUND()`, sorting |
| Q7 | How can products be classified by weight into Low, Medium, and Bulk categories? | `CASE` expressions |
| Q8 | What is the total inventory weight for each category? | `SUM()`, calculated expressions
