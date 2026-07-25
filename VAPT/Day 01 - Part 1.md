# 🌐 Day 1 – How the Internet Actually Works (VAPT Perspective)

> **Phase 1 – Cybersecurity Foundations**
>
> **Duration:** 5–6 Hours
>
> **Difficulty:** Beginner → Intermediate
>
> **Goal:** Understand every step between typing a URL into your browser and receiving a response from a web application, while identifying the potential attack surface from a penetration tester's perspective.

---

# 📖 Introduction

Many beginners believe penetration testing starts by opening Burp Suite or running Nmap.

Professional penetration testers think differently.

Before testing a target, they understand how data travels across the Internet.

Every request passes through multiple systems before reaching the application.

Each one of these systems can introduce vulnerabilities, misconfigurations, or security weaknesses.

Understanding this journey is one of the most important foundations in Web Application Penetration Testing (VAPT).

---

# 🎯 Learning Objectives

By the end of today's lesson, you should be able to:

- Explain how the Internet works.
- Describe what happens after typing a URL into a browser.
- Understand DNS resolution.
- Explain IP addressing.
- Understand the TCP Three-Way Handshake.
- Explain the purpose of HTTPS.
- Understand where attackers can intercept or manipulate requests.
- Differentiate between what Burp Suite and Wireshark can observe.
- Identify potential attack surfaces in the request lifecycle.

---

# 🧠 Why This Lesson Matters

Imagine you're testing the following application:

```
https://bank.example.com/login
```

If someone asks,

> **"Where can an attacker interact with this request?"**

A beginner might answer:

```
Burp Suite
```

A professional penetration tester thinks like this:

```text
Browser
        │
        ▼
Browser Cache
        │
        ▼
DNS Resolution
        │
        ▼
Router
        │
        ▼
ISP
        │
        ▼
Firewall
        │
        ▼
Load Balancer
        │
        ▼
Web Server
        │
        ▼
Application Server
        │
        ▼
Authentication Service
        │
        ▼
Database
        │
        ▼
Response
```

Every single layer above can become an attack surface.

Understanding these layers helps penetration testers determine where to perform security testing.

---

# 🌍 What is the Internet?

Most people describe the Internet as:

> "A network of computers."

Although technically correct, this definition is incomplete.

A better definition is:

> The Internet is a global collection of interconnected networks that communicate using standardized communication protocols such as TCP/IP to exchange information.

Every device connected to the Internet requires four essential components:

- A unique address (IP Address)
- A communication protocol
- A method to send data
- A method to receive data

Without these components, communication cannot occur.

---

# 📦 How Does a Browser Open a Website?

Let's assume a user types:

```
https://google.com
```

and presses Enter.

The browser does **not** immediately contact Google's server.

Instead, it performs several checks before sending any request.

---

# Step 1 — Browser Cache

The browser first checks its local cache.

It asks:

> "Have I visited this website recently?"

If the answer is yes, cached information may already contain:

- DNS records
- Images
- CSS files
- JavaScript
- Previously downloaded resources

Using cached resources improves loading speed because the browser avoids downloading the same content repeatedly.

---

## Browser Cache Flow

```text
User Types URL
        │
        ▼
Browser Cache
        │
 ┌──────┴────────┐
 │               │
 ▼               ▼
Cache Found   Cache Missing
 │               │
 ▼               ▼
Use Cache     Perform DNS Lookup
```

---

# 🔍 VAPT Perspective — Browser Cache

A penetration tester should ask:

- Does the browser cache sensitive pages?
- Are authentication tokens stored locally?
- Is Local Storage storing JWT tokens?
- Does Session Storage contain secrets?
- Can cached responses leak confidential information?
- Can an attacker recover sensitive files from browser storage?

During authentication testing, browser storage becomes extremely important.

---

# Step 2 — DNS Resolution

Suppose the browser cannot find the requested website in its cache.

It now needs to determine the server's IP address.

Instead of remembering numerical IP addresses, humans remember domain names.

For example:

```
google.com
```

The browser must convert this domain into an IP address.

This process is called:

# DNS Resolution

DNS stands for:

> **Domain Name System**

DNS is commonly referred to as the Internet's phonebook.

---

## DNS Resolution Process

```text
Browser
      │
      ▼
Operating System Cache
      │
      ▼
Router Cache
      │
      ▼
ISP DNS Resolver
      │
      ▼
Root DNS Server
      │
      ▼
Top Level Domain (.com)
      │
      ▼
Authoritative DNS Server
      │
      ▼
IP Address Returned
```

---

# Example

The browser asks:

```
Where is google.com?
```

DNS replies:

```
142.250.xxx.xxx
```

Now the browser knows where Google's server is located.

---

# 📌 Why DNS Exists

Imagine trying to remember the IP address of every website you visit.

Instead of typing:

```
142.250.196.46
```

you simply type:

```
google.com
```

DNS performs the translation automatically.

---

# 🔍 VAPT Perspective — DNS

DNS is much more than name resolution.

For penetration testers, DNS provides valuable reconnaissance opportunities.

Common questions include:

- Can subdomains be enumerated?
- Is Zone Transfer enabled?
- Are development environments exposed?
- Are staging servers publicly accessible?
- Which technologies can DNS records reveal?
- Can forgotten subdomains be discovered?

DNS reconnaissance often reveals systems that developers forgot to secure.

---

# 📸 Screenshot Required

Capture the following later during the practical exercises.

```
Images/nslookup-google.png
```

---

# Step 3 — IP Address

After DNS resolution, the browser finally receives the destination IP address.

Example:

```
google.com

↓

142.xxx.xxx.xxx
```

An IP address uniquely identifies a device on a network.

Think of an IP address like a home address.

Without it, data would never reach the intended destination.

---

# IPv4 Example

```
192.168.1.100
```

IPv4 consists of four numbers separated by periods.

Each number ranges from **0 to 255**.

---

# Public vs Private IP Addresses

## Private IP Addresses

Private IP addresses are used inside local networks.

Examples:

```
10.0.0.0 – 10.255.255.255

172.16.0.0 – 172.31.255.255

192.168.0.0 – 192.168.255.255
```

These addresses are **not directly accessible from the Internet.**

---

## Public IP Addresses

Public IP addresses are globally routable.

They allow communication across the Internet.

Example:

```
8.8.8.8
```

Google Public DNS

---

# 🔍 VAPT Perspective — IP Address

While assessing a target, penetration testers investigate:

- Is the application behind NAT?
- Is IPv6 enabled?
- Does the organisation expose multiple public IP addresses?
- Are unnecessary services publicly accessible?
- Are additional hosts located in the same IP range?

Understanding IP addressing helps define the attack surface before active testing begins.

---

# 📝 Day 1 Summary (Part 1)

Today you learned:

- What the Internet actually is.
- How browsers process URLs.
- Browser Cache.
- DNS Resolution.
- IP Addresses.
- Public vs Private Networks.
- Why these concepts matter during a VAPT engagement.

In **Part 2**, we will cover:

- TCP Three-Way Handshake
- TLS Handshake
- HTTPS
- HTTP Requests
- Burp Suite Perspective
- Server-side Request Journey
- Practical Exercises
- Interview Questions
