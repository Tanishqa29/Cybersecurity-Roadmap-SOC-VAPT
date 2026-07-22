# 🚀 Day 0 – Build Your Professional VAPT Lab

> Before performing a single penetration test, every professional security consultant prepares a standardized and repeatable lab environment. This guide walks you through setting up the exact lab that will be used throughout this 60-day VAPT Bootcamp.

---

# 🎯 Objective

By the end of this guide, you will have:

- A dedicated penetration testing environment
- Kali Linux running inside a virtual machine
- Professional VAPT tools installed
- Firefox configured with security testing extensions
- A GitHub repository for documentation
- A reusable folder structure for future assessments
- A reporting workflow used throughout this bootcamp

---

# 📋 Prerequisites

Before starting, ensure you have:

- Windows/Linux/macOS Host Machine
- Minimum 16 GB RAM (8 GB works with reduced allocation)
- At least 60 GB of free storage
- Stable internet connection
- VirtualBox or VMware installed

---

# Step 1 — Install VirtualBox

Download VirtualBox from the official website.

Install using the default settings.

After installation, restart your computer if prompted.


---

# Step 2 — Install Kali Linux

Download the Kali VirtualBox Image.

Import it into VirtualBox.

Allocate:

- RAM: 4096 MB
- CPU: 2+
- Disk: 40 GB+
- Network: NAT

Start Kali.

Login successfully.


---

# Step 3 — Update Kali

Open Terminal.

Run:

```bash
sudo apt update
sudo apt full-upgrade -y
```

Wait until the installation completes.

Verify:

```bash
cat /etc/os-release
```


---

# Step 4 — Install Burp Suite Community Edition

Open Firefox.

Download Burp Suite Community Edition.

Install it.

Launch Burp.

Verify the dashboard opens successfully.


---

# Step 5 — Install Firefox Extensions

Install the following:

- FoxyProxy Standard
- Wappalyzer
- Cookie Editor
- JSON Viewer
- User-Agent Switcher

Verify that all extensions appear in Firefox.

---

# Step 6 — Verify Core Tools

Open Terminal and run:

```bash
nmap --version
```

```bash
sqlmap --version
```

```bash
ffuf -V
```

```bash
gobuster version
```

```bash
whatweb --version
```

```bash
amass version
```



---

# Step 7 — Create Your Folder Structure

Create the following directories:

```text
VAPT-Bootcamp/
│
├── 00-Environment
├── 01-Networking
├── 02-Linux
├── 03-HTTP
├── 04-Burp
├── 05-Recon
├── 06-OWASP
├── 07-API
├── 08-Labs
├── 09-Reports
├── 10-Screenshots
├── 11-Scripts
├── 12-Interview
└── Resources
```


---

# Verification Checklist

- [x] Kali Linux Installed
- [x] VirtualBox Configured
- [x] Burp Suite Installed
- [x] Firefox Extensions Installed
- [x] Core Tools Verified
- [x] Folder Structure Created

---

# What You Learned

At this stage, you have built a professional penetration testing workstation that will be used throughout this bootcamp. Proper preparation, documentation, and organization are fundamental to every successful VAPT engagement.

---

# Next Step

Proceed to **Day 1 – How the Internet Actually Works**.
