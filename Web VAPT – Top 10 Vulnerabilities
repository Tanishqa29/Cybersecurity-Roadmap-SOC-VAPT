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

# 🔹 PART 2: RAPID FIRE Q&A

🔐 **1. Authentication Bypass**
Q: What is authentication bypass?
👉 It is a vulnerability where an attacker gains access without valid credentials due to broken login logic.

Q: How does it happen?
👉 Due to missing server-side validation, weak OTP checks, or trusting client-side logic.

Q: Impact?
👉 Unauthorized login to user or admin accounts.

---

🧾 **2. Broken Access Control**
Q: What is broken access control?
👉 When users can perform actions or access data beyond their privilege level.

Q: Example?
👉 Normal user accessing /admin/dashboard.

Q: Impact?
👉 Data leakage and privilege escalation.

---

🔓 **3. IDOR**
Q: What is IDOR?
👉 A vulnerability where object references (like IDs) are exposed without authorization checks.

Q: How to identify?
👉 Change ID in request and check if other user’s data is accessible.

Q: Impact?
👉 Unauthorized access to sensitive user data.

---

🧑‍💻 **4. SQL Injection**
Q: What is SQL Injection?
👉 Injection of malicious SQL queries into input fields.

Q: Example payload?
👉 ' OR 1=1 --

Q: Impact?
👉 Database dump, login bypass, data manipulation.

---

🌐 **5. XSS**
Q: What is XSS?
👉 Injection of malicious JavaScript into web pages viewed by users.

Q: Types?
👉 Stored, Reflected, DOM-based.

Q: Impact?
👉 Cookie theft, session hijacking.

---

🔁 **6. CSRF**
Q: What is CSRF?
👉 Trick a logged-in user into performing unwanted actions.

Q: How it works?
👉 Exploits missing CSRF token validation.

Q: Impact?
👉 Unauthorized actions like password/email change.

---

📂** 7. File Upload Vulnerability**
Q: What is file upload vulnerability?
👉 When system allows unsafe files to be uploaded without proper validation.

Q: Risk?
👉 Upload of malicious scripts (web shells).

Q: Impact?
👉 Remote code execution or server compromise.

---

🌍 **8. SSRF**
Q: What is SSRF?
👉 Server is tricked into making requests to internal or external systems.

Q: Example?
👉 Changing URL input to http://localhost.

Q: Impact?
👉 Internal network exposure, cloud metadata access.

---

🔎 **9. Information Disclosure**
Q: What is information disclosure?
👉 Sensitive data is exposed unintentionally.

Q: Examples?
👉 .env files, debug logs, API keys in frontend.

Q: Impact?
👉 Helps attackers plan further attacks.

---

⚙️ **10. Security Misconfiguration**
Q: What is security misconfiguration?
👉 Improperly configured security settings in application or server.

Q: Example?
👉 Default credentials, debug mode ON.

Q: Impact?
👉 Easy entry point for attackers.


---

# 🔹 PART 3: REAL-WORLD SCENARIOS

## 🔐 Authentication Bypass

Startup OTP system validated only frontend → attacker skipped OTP → account takeover.

## 🧾 Broken Access Control

Student accessed `/admin/dashboard` → no backend check → admin access.

## 🔓 IDOR

Invoice ID modified → accessed other users' financial data.

## 🧑‍💻 SQL Injection

Login query manipulated → bypass authentication → DB compromise.

## 🌐 XSS

Malicious script in comments → cookie theft.

## 🔁 CSRF

Malicious link triggered fund transfer.

## 📂 File Upload

Uploaded `shell.php` → remote server control.

## 🌍 SSRF

Accessed cloud metadata → leaked credentials.

## 🔎 Information Disclosure

Exposed `.env` → leaked API keys.

## ⚙️ Security Misconfiguration

Default admin credentials → full system control.

---

# 🔥 FINAL NOTE

Always test using:

* Burp Suite (Intercept + Repeater)
* Parameter manipulation
* Backend validation checks

---
