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
