---

# Step 4 — TCP Three-Way Handshake

After obtaining the destination IP address, the browser knows **where** to send the request.

However, before sending any data, it must establish a reliable connection with the server.

This is achieved using the **Transmission Control Protocol (TCP)**.

TCP ensures:

- Reliable communication
- Ordered packet delivery
- Error detection
- Packet retransmission
- Connection management

Before exchanging data, TCP performs a process known as the **Three-Way Handshake**.

---

## TCP Three-Way Handshake

```text
Client                              Server

  | -------- SYN ------------------> |
  |                                  |
  | <------ SYN + ACK -------------- |
  |                                  |
  | -------- ACK ------------------> |
  |                                  |
        Connection Established
```

---

## Step 1 — SYN

The client sends a **Synchronize (SYN)** packet.

Meaning:

> "Hello Server, I'd like to establish a connection."

---

## Step 2 — SYN-ACK

The server responds with:

**SYN + ACK**

Meaning:

> "I received your request and I'm ready."

---

## Step 3 — ACK

The client sends an acknowledgement.

Meaning:

> "Connection confirmed."

The TCP connection is now established.

---

# Why Does TCP Need a Handshake?

Without the handshake:

- The server wouldn't know whether the client is available.
- Packets could be lost.
- Communication might begin before both devices are ready.
- Reliable communication wouldn't be possible.

TCP solves these problems before any application data is exchanged.

---

# VAPT Perspective — TCP

A penetration tester should understand TCP because many reconnaissance tools rely on it.

Examples include:

- Nmap TCP SYN Scan
- Banner Grabbing
- Port Enumeration
- Firewall Detection
- Service Fingerprinting

Understanding TCP also helps analyse packet captures in Wireshark.

---

# Screenshot Required

Capture a TCP handshake using Wireshark later in the bootcamp.

```
Images/tcp-handshake.png
```

---

# Step 5 — TLS Handshake (HTTPS)

If the website uses:

```
https://
```

another handshake occurs after TCP.

This is called the **TLS Handshake**.

TLS stands for:

> **Transport Layer Security**

TLS provides three major security properties:

- Encryption
- Integrity
- Authentication

---

## TLS Handshake Simplified

```text
Client
      │
      ▼
Hello Server

      │
      ▼
Server sends Certificate

      │
      ▼
Client verifies Certificate

      │
      ▼
Encryption Keys Generated

      │
      ▼
Encrypted Communication Begins
```

---

# What HTTPS Protects

HTTPS protects:

- Login credentials
- Cookies
- API requests
- Payment details
- Personal information
- Data exchanged between client and server

---

# What HTTPS Does NOT Protect

HTTPS **does not** prevent:

- SQL Injection
- Cross-Site Scripting (XSS)
- IDOR
- Broken Access Control
- File Upload Vulnerabilities
- Business Logic Flaws
- Authentication Weaknesses

HTTPS only protects **data in transit**.

It does **not** guarantee the application itself is secure.

---

# Interview Question

### Question

The application uses HTTPS.

Is it secure?

### Answer

No.

HTTPS only protects communication between the client and server by encrypting data in transit.

The application may still contain vulnerabilities such as SQL Injection, Cross-Site Scripting (XSS), Insecure Direct Object References (IDOR), Authentication Bypass, or Broken Access Control.

---

# Step 6 — HTTP Request

Once the secure connection is established, the browser sends an HTTP request.

Example:

```http
GET / HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0
Accept: text/html
Cookie: session=abc123
```

Every part of this request has security implications.

---

# Understanding the Request

## Request Method

Example:

```
GET
POST
PUT
DELETE
PATCH
OPTIONS
```

Determines what action should be performed.

---

## Host Header

Specifies the destination website.

Example

```
Host: example.com
```

---

## User-Agent

Identifies the browser.

Example

```
Mozilla/5.0
```

---

## Cookies

Cookies contain session identifiers and user preferences.

Example

```
Cookie:
session=abc123
```

---

## Headers

Headers provide additional information about the request.

Examples:

- Accept
- Content-Type
- Authorization
- Origin
- Referer
- Cache-Control

---

# VAPT Perspective — HTTP Request

A penetration tester asks:

- Can headers be manipulated?
- Can cookies be modified?
- Can request methods be changed?
- Can hidden parameters be discovered?
- Can Content-Type validation be bypassed?
- Can authentication tokens be replayed?

Every request is a potential attack vector.

---

# Burp Suite Perspective

Burp Suite intercepts HTTP and HTTPS traffic between the browser and the server.

It allows testers to:

- Intercept requests
- Modify parameters
- Replay requests
- Analyse responses
- Discover vulnerabilities

Example workflow:

```text
Browser

↓

Burp Suite

↓

Target Server

↓

Burp Suite

↓

Browser
```

---

# Wireshark vs Burp Suite

| Wireshark | Burp Suite |
|-----------|------------|
| Captures network packets | Captures HTTP/HTTPS requests |
| Works at lower network layers | Works at the application layer |
| Shows TCP packets | Shows HTTP messages |
| Useful for network analysis | Useful for web security testing |

---

# Step 7 — Server Side Journey

After receiving the request, the server processes it through multiple components.

```text
Internet

↓

Firewall

↓

Load Balancer

↓

Web Server

↓

Application Server

↓

Authentication

↓

Business Logic

↓

Database

↓

Response Generated

↓

Browser
```

Each component has its own responsibilities and potential security weaknesses.

---

# Potential Attack Surface

| Layer | Example Security Questions |
|--------|----------------------------|
| Browser | Can JavaScript validation be bypassed? |
| HTTP | Can headers be manipulated? |
| Cookies | Are Secure and HttpOnly flags missing? |
| Session | Can session IDs be predicted or hijacked? |
| Authentication | Can login be bypassed? |
| Business Logic | Can workflows be abused? |
| Database | Is user input safely handled? |
| File System | Can arbitrary files be uploaded? |
| APIs | Is authorisation enforced? |

---

# Practical Exercises

## Exercise 1 — Identify Your IP Configuration

Run:

```cmd
ipconfig
```

Record:

- IPv4 Address
- Default Gateway
- DNS Server


---

## Exercise 2 — Ping Google

Run:

```cmd
ping google.com
```

Observe:

- IP Address
- Latency
- Number of Replies


---

## Exercise 3 — Trace the Route

Run:

```cmd
tracert google.com
```

Observe:

- Number of hops
- Routers involved
- Time taken

---

## Exercise 4 — DNS Lookup

Run:

```cmd
nslookup google.com
```

Compare the returned IP address with the Ping result.

---

## Exercise 5 — Browser Developer Tools

1. Open a website.
2. Press **F12**.
3. Open the **Network** tab.
4. Refresh the page.
5. Click the first request.

Answer the following:

- Which HTTP Method was used?
- What Status Code was returned?
- Which Headers are present?
- Were Cookies sent?
- What is the Response Size?

---

# Scenario-Based Questions

## Scenario 1

The website is down.

However:

- DNS resolves successfully.
- Ping works.
- TCP Handshake succeeds.

What could be wrong?

Possible answers include:

- Web Server Failure
- Application Crash
- Reverse Proxy Misconfiguration
- Database Connectivity Issues
- Maintenance Mode

---

## Scenario 2

Every request returns **403 Forbidden**.

Possible causes:

- Firewall Rules
- Web Application Firewall (WAF)
- IP Restrictions
- Authentication Issues
- Missing Required Headers

---

## Scenario 3

Two users visit the same URL.

One sees an Admin Dashboard.

The other sees a Login Page.

Possible explanations:

- Role-Based Access Control (RBAC)
- Session Cookies
- Authentication State
- Access Control Rules
- Different User Permissions

---

# Key Takeaways

- Every website request passes through multiple networking layers.
- DNS translates domain names into IP addresses.
- TCP establishes reliable communication.
- TLS secures data in transit.
- HTTP carries requests and responses.
- Burp Suite analyses application-layer traffic.
- Wireshark analyses network traffic.
- Every stage of the request lifecycle presents opportunities for security assessment.

---

# Homework

- Draw the complete request flow from memory.
- Explain each step in your own words.
- Complete all five practical exercises.
- Create a one-page cheat sheet titled **"Life of an HTTP Request"**.
- Commit today's work to GitHub.

---

# References

- Practical Networking
- PortSwigger Web Security Academy
- Wireshark Documentation
- Mozilla Developer Network (MDN)
- RFC 791 (IP)
- RFC 793 (TCP)
- RFC 8446 (TLS 1.3)

---



# Next Lesson

➡️ **Day 2 – Networking Fundamentals for Pentesters**



Understanding these concepts will help you think like a penetration tester rather than simply using security tools.
