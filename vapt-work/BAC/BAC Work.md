# Broken Access Control Labs — PortSwigger Web Security Academy

**Topic:** Broken Access Control (BAC)
**Platform:** PortSwigger Web Security Academy
**Goal:** Practice and understand Access Control vulnerabilities hands-on

---

## Lab 1 — Unprotected Admin Functionality


- **Lab Link:** https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality
- **Difficulty:** Apprentice
- **Vuln Type:** Broken Access Control (Unprotected Admin Panel)
- **Location:** /administrator-panel
- **Tool Used:** Browser

### Steps
1. Opened the lab website
2. Navigated to /robots.txt to check for hidden directories
3. Found /administrator-panel listed under Disallow
4. Directly navigated to /administrator-panel in browser
5. Admin panel loaded without any authentication required
6. Deleted user carlos — lab solved

- **What happened:** Admin panel accessible to anyone without login
- **Why it worked:** No authentication or access control applied to admin panel URL
- **Mitigation:** Implement proper authentication on all admin endpoints, never rely on obscurity

<img width="1194" height="587" alt="BAC1 1" src="https://github.com/user-attachments/assets/85ab0c2b-593a-4347-abe3-9ac8ca00ec86" />
<img width="1777" height="953" alt="BAC1" src="https://github.com/user-attachments/assets/1acf0606-eba9-482d-80c7-113d5208f275" />


---

## Lab 2 — Unprotected Admin Functionality With Unpredictable URL

- **Lab Link:** https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality-with-unpredictable-url
- **Difficulty:** Apprentice
- **Vuln Type:** Broken Access Control (Hidden Admin Panel)
- **Location:** /admin-gk77r3
- **Tool Used:** Browser (View Page Source)

### Steps
1. Opened the lab website
2. robots.txt did not reveal the admin panel this time
3. Viewed page source code (Ctrl+U)
4. Found admin panel URL /admin-gk77r3 hardcoded in JavaScript
5. Directly navigated to /admin-gk77r3 in browser
6. Admin panel loaded without any authentication required
7. Deleted user carlos — lab solved

- **What happened:** Admin panel URL exposed in client side JavaScript source code
- **Why it worked:** Developer assumed unpredictable URL = security — but source code is visible to anyone
- **Mitigation:** Never expose sensitive URLs in client side code, implement proper server side authentication


<img width="1827" height="1020" alt="bac3" src="https://github.com/user-attachments/assets/73607a5f-8e74-4b3c-938d-7370fad84446" />
<img width="1794" height="896" alt="BAC3 1" src="https://github.com/user-attachments/assets/45bdc52f-3dad-4451-88e8-dbb881a90c91" />
