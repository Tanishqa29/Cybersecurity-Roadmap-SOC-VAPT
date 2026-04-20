# OWASP Top 10: 2025 

## 🥇 A01: Broken Access Control (MOST IMPORTANT)

👉 “User la je access nahi pahije te milto”

### 💣 Real Example:
- User1 cha data URL change karun User2 cha data baghne
- `/api/user/123` → `/api/user/124`

### 🧠 Attacks:
- IDOR (VERY IMPORTANT)
- Privilege escalation (user → admin)
- Forced browsing

### 🛡️ Fix:
- Server-side authorization checks
- Role-based access control (RBAC)

---

## 🥈 A02: Security Misconfiguration

👉 “System wrong settings mule vulnerable hota”

### 💣 Example:
- Default password: admin/admin
- Debug mode ON in production

### 🧠 Attack:
- Exposed admin panels
- Missing security headers

### 🛡️ Fix:
- Disable unused features
- Secure headers (CSP, HSTS)

---

## 🥉 A03: Software Supply Chain Failures (NEW TREND)

👉 “Third-party libraries mule hack”

### 💣 Example:
- NPM package madhe malicious code
- Compromised CI/CD pipeline

### 🧠 Attack:
- Dependency poisoning
- Backdoor injection

### 🛡️ Fix:
- Use trusted libraries
- Regular updates + vulnerability scanning

---

## 🔐 A04: Cryptographic Failures

👉 “Encryption wrong asel tar data leak”

### 💣 Example:
- Password plain text madhe store
- HTTP instead of HTTPS

### 🧠 Attack:
- Data theft
- Session hijacking

### 🛡️ Fix:
- Strong encryption (AES, bcrypt)
- Always use HTTPS

## 💉 A05: Injection (🔥 Classic Hacker Attack) 
👉 “Input sanitize nahi → code execute hoto” 

### 💣 Example:
SELECT * FROM users WHERE username = 'admin' OR '1'='1'

### 🧠 Types: 
* SQL Injection
* XSS
* Command Injection 

### 🛡️ Fix: 
* Input validation
* Prepared statements

---

## 🧠 A06: Insecure Design 
👉 “System design madhech flaw aahe” 

### 💣 Example: 
* No rate limiting → brute force possible
* No validation logic

### 🛡️ Fix: 
* Threat modeling
* Secure architecture

--- 

## 🔑 A07: Authentication Failures 
👉 “Login system weak aahe” 

### 💣 Example: 
* Weak passwords allowed
* No MFA

### 🧠 Attack: 
* Brute force
* Credential stuffing

### 🛡️ Fix: 
* Strong password policy
* Multi-factor authentication

---
## 🔄 A08: Software / Data Integrity Failures 
👉 “Code/data tampered hota” 

### 💣 Example: 
* Unsigned updates
* Insecure deserialization

### 🧠 Attack: 
* Malware injection
* Remote code execution

### 🛡️ Fix: 
* Integrity checks
* Signed updates

--- 

## 📊 A09: Logging & Alerting Failures 
👉 “Attack jhala pan detect nahi jhala” 

### 💣 Example: 
* No logs
* No alerts

### 🧠 Impact: 
* Hacker months stay unnoticed

### 🛡️ Fix: 
* SIEM tools
* Real-time alerts

--- 

## ⚠️ A10: Mishandling of Exceptional Conditions (🔥 NEW) 
👉 “Error handling wrong → system break” 

### 💣 Example: 
* Server crash on bad input
* Sensitive error messages show

### 🧠 Attack: 
* DoS
* Info leakage

### 🛡️ Fix: 
* Proper error handling
* Fail securely

---
