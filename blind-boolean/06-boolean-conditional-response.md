# 🧪 Lab: Blind SQL Injection - Conditional Response

## 🎯 Goal
Extract sensitive data (e.g., password) using boolean-based blind SQL injection.

## 🔍 Vulnerability Type
Blind SQL Injection (Boolean-based)

---

## 🧠 Concept Overview

In this lab, the application does not return:
- SQL errors ❌  
- Query results ❌  

Instead, it shows **different responses based on TRUE or FALSE conditions**.

👉 This allows us to extract data by asking the database **yes/no questions**.

---

## ⚙️ Step 1 — Confirm Injection

### Payloads:
' AND 1=1--  
' AND 1=2--  

### Observation:
- `1=1` → Normal page (TRUE)  
- `1=2` → Different response (FALSE)  

👉 This confirms:
We can control backend logic.

---

## ⚙️ Step 2 — Identify Target (Example: Password)

We assume a query like:

SELECT * FROM users WHERE username='administrator'

Now we inject conditions to test properties of the password.

---

## ⚙️ Step 3 — Determine Password Length

### Payload:
' AND LENGTH(password)>5--  

### Logic:
We test different values:

- LENGTH(password)>1 → TRUE  
- LENGTH(password)>5 → TRUE  
- LENGTH(password)>10 → FALSE  

👉 From this, we narrow down the exact length.

---

## ⚙️ Step 4 — Extract Characters (Brute Force)

### Payload:
' AND SUBSTRING(password,1,1)='a'--  

### Breakdown:
- `SUBSTRING(password,1,1)` → first character  
- Compare with 'a', 'b', 'c'...  

### Process:
Try all characters until response = TRUE

👉 That reveals:
First character of password

---

## ⚙️ Step 5 — Full Extraction Logic

Repeat for each position:

- Position 1 → find char  
- Position 2 → find char  
- Position 3 → find char  

Example:

' AND SUBSTRING(password,1,1)='a'--  
' AND SUBSTRING(password,2,1)='d'--  

👉 Eventually reconstruct full password.

---

## 🔁 Payload Variations

- ' AND LENGTH(password)=8--  
- ' AND SUBSTRING(password,2,1)='x'--  
- ' AND ASCII(SUBSTRING(password,1,1))>100--  

---

## 🌍 Real-World Impact

- Extract credentials silently  
- Bypass logging (no errors triggered)  
- Works even when output is hidden  

---

## 🛡️ Prevention

- Use parameterized queries  
- Avoid dynamic SQL queries  
- Implement proper input validation  
- Use ORM frameworks  

---

## ⚠️ Key Insight

Blind SQLi is:
- Slow ❌  
- Requires multiple requests ❌  

But:
👉 Extremely powerful when no output is available
