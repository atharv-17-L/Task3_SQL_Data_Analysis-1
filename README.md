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
2. Order all customers alphabetically by last name
sql
Copy code
SELECT * FROM customers ORDER BY last_name;
🔹 3. Count number of customers per city
sql
Copy code
SELECT city, COUNT(*) AS total_customers
FROM customers
GROUP BY city
ORDER BY total_customers DESC;
🔹 4. Find customers with email domain from 'github.com'
sql
Copy code
SELECT * FROM customers WHERE email LIKE '%@github.com';
🔹 5. Create a view for high-IP range customers
sql
Copy code
CREATE VIEW high_ip_customers AS
SELECT * FROM customers
WHERE ip_address LIKE '192.%';
🔹 6. Use a subquery to find customers from cities with more than 1 customer
sql
Copy code
SELECT * FROM customers
WHERE city IN (
    SELECT city FROM customers
    GROUP BY city
    HAVING COUNT(*) > 1
);
🔹 7. Get distinct cities from the dataset
sql
Copy code
SELECT DISTINCT city FROM customers;
🔹 8. Get the top 3 customers with the lowest customer_id
sql
Copy code
SELECT * FROM customers
ORDER BY customer_id ASC
LIMIT 3;
🔹 9. Find customers who are not from 'Sousa' or 'Oromocto'
sql
Copy code
SELECT * FROM customers
WHERE city NOT IN ('Sousa', 'Oromocto');
🔹 10. Find customers with IP addresses in a specific range
sql
Copy code
SELECT * FROM customers
WHERE ip_address BETWEEN '100.0.0.0' AND '200.255.255.255';
🔹 11. Count how many customers have Gmail accounts
sql
Copy code
SELECT COUNT(*) AS gmail_users
FROM customers
WHERE email LIKE '%@gmail.com';
🔹 12. Use CASE to label customers by city size (mock rule)
sql
Copy code
SELECT customer_id, name, city,
  CASE
    WHEN city IN ('Sousa', 'Skórzec') THEN 'Small City'
    WHEN city IN ('Chivor', 'Oromocto') THEN 'Medium City'
    ELSE 'Unknown Size'
  END AS city_category
FROM customers;
🔹 13. Find customers with NULL values (if any)
sql
Copy code
SELECT * FROM customers
WHERE name IS NULL OR email IS NULL OR city IS NULL;
🔹 14. Count number of users per email domain
sql
Copy code
SELECT
  SUBSTR(email, INSTR(email, '@') + 1) AS domain,
  COUNT(*) AS count
FROM customers
GROUP BY domain
ORDER BY count DESC;
🔹 15. Create an index on the city column to optimize performance
sql
Copy code
CREATE INDEX idx_city ON customers(city);
