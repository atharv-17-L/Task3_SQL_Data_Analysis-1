# 📊 Task 3: SQL for Data Analysis

## 🧠 Objective

This project demonstrates structured data analysis using SQL. A mock e-commerce customer dataset is used to perform operations such as filtering, aggregation, subqueries, and performance optimization using standard SQL clauses. The purpose is to simulate real-world data handling and extraction using SQL.

---

## 🧰 Tools Used

- ✅ **SQLite** – via [sqliteonline.com](https://sqliteonline.com/) (no installation needed)
- 📄 **CSV File** – `Ecommerce_DATA.csv` (fake dataset)
- ✍️ **SQL Script** – SQL queries embedded in this README
- 📸 **Mock Screenshots** – Markdown tables or images for simulated results

---

## 📁 Dataset Overview

The dataset is a mock list of customer data with the following structure:

| Column        | Description                      |
|---------------|----------------------------------|
| customer_id   | Unique identifier for customers  |
| name          | First name of the customer       |
| last_name     | Last name of the customer        |
| email         | Customer email address           |
| city          | City of residence                |
| ip_address    | Customer’s IP address            |

📄 File name: **`Ecommerce_DATA.csv`**

---

## 🧪 SQL Queries

### 🔹 1. Select all customers from the city 'Sousa'

```sql
SELECT * FROM customers WHERE city = 'Sousa';

###🔹 2. Order all customers alphabetically by last name

...sql
SELECT * FROM customers ORDER BY last_name;

###🔹 3. Count number of customers per city

...sql
SELECT city, COUNT(*) AS total_customers
FROM customers
GROUP BY city
ORDER BY total_customers DESC;

###🔹 4. Create a view for high-IP range customers
...sql
CREATE VIEW high_ip_customers AS
SELECT * FROM customers
WHERE ip_address LIKE '192.%';

###🔹 5. Use a subquery to find customers from cities with more than 1 customer

...sql
SELECT * FROM customers
WHERE city IN (
    SELECT city FROM customers
    GROUP BY city
    HAVING COUNT(*) > 1);

###🔹 6. Get distinct cities from the dataset

...sql
SELECT DISTINCT city FROM customers;

###🔹 7. Get the top 3 customers with the lowest customer_id

...sql
SELECT * FROM customers
ORDER BY customer_id ASC
LIMIT 3;

###🔹 8. Find customers who are not from 'Sousa' or 'Oromocto'

...sql
SELECT * FROM customers
WHERE city NOT IN ('Sousa', 'Oromocto');

###🔹 9. Find customers with IP addresses in a specific range

...sql
SELECT * FROM customers
WHERE ip_address BETWEEN '100.0.0.0' AND '200.255.255.255';

###🔹 10. Count how many customers have Gmail accounts

...sql
SELECT COUNT(*) AS gmail_users
FROM customers
WHERE email LIKE '%@gmail.com';

###🔹 11. Use CASE to label customers by city size
...sql

    WHEN city IN ('Sousa', 'Skórzec') THEN 'Small City'
    WHEN city IN ('Chivor', 'Oromocto') THEN 'Medium City'
    ELSE 'Unknown Size'
  END AS city_category
FROM customers;

###🔹 12. Find customers with NULL values

...sql
SELECT * FROM customers
WHERE name IS NULL OR email IS NULL OR city IS NULL;

###🔹 13. Count number of users per email domain

...sql
  SUBSTR(email, INSTR(email, '@') + 1) AS domain,
  COUNT(*) AS count
FROM customers
GROUP BY domain
ORDER BY count DESC;

###🔹 14. Create index on city column to optimize query speed

...sql
Copy code
CREATE INDEX idx_city ON customers(city);

