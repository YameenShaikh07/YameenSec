# XSS Labs — PortSwigger Web Security Academy

**Topic:** Cross Site Scripting (XSS)
**Platform:** PortSwigger Web Security Academy
**Goal:** Practice and understand XSS vulnerabilities hands-on

---

## Lab 1 — Reflected XSS (Basic)

- **Lab Link:** https://portswigger.net/web-security/cross-site-scripting/reflected/lab-html-context-nothing-encoded
- **Difficulty:** Apprentice
- **Vuln Type:** Reflected XSS
- **Location:** Search parameter (GET request)
- **Tool Used:** Browser

### Steps
1. Opened the lab and went to the search box
2. Identified search parameter as injection point
3. Injected XSS payload directly into search field
4. Browser executed the JavaScript and alert popup appeared
5. Lab solved successfully

- **Payload Used:** <script>alert("BAKI");</script>
- **What happened:** JavaScript executed in browser — alert box popped up
- **Why it worked:** Search input was reflected directly in response without any sanitization
- **Mitigation:** Sanitize and encode user input, use Content Security Policy (CSP)


<img width="1824" height="986" alt="xss lab1 1" src="https://github.com/user-attachments/assets/7ae00a01-5255-47f0-94db-a343fe13ad9d" />

