# SQL Injection Labs — PortSwigger Web Security Academy

**Topic:** SQL Injection
**Platform:** PortSwigger Web Security Academy
**Goal:** Practice and understand SQL Injection vulnerabilities hands-on

---

## Lab 1 — WHERE Clause (Hidden Data)

- **Lab Link:** https://portswigger.net/web-security/sql-injection/lab-retrieve-hidden-data
- **Difficulty:** Apprentice
- **Vuln Type:** SQL Injection (In-band)
- **Location:** category parameter (GET request)
- **Original URL:** https://0adb0040039cc0f080843f3900af00f0.web-security-academy.net/filter?category=Clothing%2c+shoes+and+accessories
- **Payload Used:** ' OR 1=1--
- **Payload URL:** https://0adb0040039cc0f080843f3900af00f0.web-security-academy.net/filter?category=%27+or+1=1--
- **What happened:** All rows returned including unreleased/hidden products
- **Why it worked:** OR 1=1 made condition always TRUE, -- commented out AND released=1
- **Mitigation:** Use parameterized queries / prepared statements

---

## Lab 2 — Login Bypass

- **Lab Link:** https://portswigger.net/web-security/sql-injection/lab-login-bypass
- **Difficulty:** Apprentice
- **Vuln Type:** SQL Injection (Authentication Bypass)
- **Location:** Username field in login form
- **Payload Used:** admin'--
- **What happened:** Logged in as administrator without knowing the password
- **Why it worked:** -- commented out the password check in SQL query completely
- **Mitigation:** Use parameterized queries, never concatenate user input into SQL query directly
