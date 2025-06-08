# 📊 Task 3: SQL for Data Analysis

## 🧠 Objective

This project demonstrates how to perform SQL-based data analysis using a mock e-commerce dataset. The goal is to simulate real-world data extraction, filtering, and aggregation using SQL commands. This includes basic querying, grouping, filtering, subqueries, views, and indexing concepts.

---

## 🧰 Tools Used

- 🗃️ SQLite (via [sqliteonline.com](https://sqliteonline.com/))
- 📄 CSV Dataset ('Ecommerce_DATA.csv`)
- ✍️ SQL Query File (`task3_data_analysis.sql`)
- 📸 Screenshot Placeholders (for simulated outputs)

---

## 📁 Dataset Description

The dataset is a mock e-commerce customer list with the following columns:

| Column Name   | Description                    |
|---------------|--------------------------------|
| customer_id   | Unique ID of each customer     |
| name          | First name of the customer     |
| last_name     | Last name of the customer      |
| email         | Email address                  |
| city          | City of residence              |
| ip_address    | Customer’s IP address          |

---

## 🧪 SQL Queries Performed

### 🔹 1. Select all customers from the city 'Sousa'

```sql
SELECT * FROM customers WHERE city = 'Sousa';
