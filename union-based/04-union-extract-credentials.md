# 🧪 Lab: SQL Injection UNION Attack - Extract Credentials

## 🎯 Goal
Extract usernames and passwords from the database

## 🔍 Vulnerability Type
UNION-based SQL Injection

## ⚙️ Payload Used
' UNION SELECT username, password FROM users--

## 🧠 Explanation
After identifying column count and visible columns, we inject a UNION SELECT statement to retrieve data from the users table.

The injected query appends attacker-controlled data to the original query result.

## 💥 Exploitation Steps
1. Determine column count
2. Identify visible column
3. Inject:
   ' UNION SELECT username, password FROM users--
4. Observe credentials in response

## 🔁 Variations
- ' UNION SELECT username, password, NULL--
- ' UNION SELECT NULL, username, password--

## 🌍 Real-World Impact
- Account takeover
- Data breach
- Privilege escalation

## 🛡️ Prevention
- Parameterized queries
- Least privilege database access
- Input validation
