# TryHackMe — Pre-Security: How The Web Works

**Date:** June 9, 2026
**Path:** Pre-Security — in progress
**Modules covered:** DNS in Detail, HTTP in Detail, How Websites Work
**Status:** - Modules 2 & 3 completed

---

## DNS (Domain Name System)
Translates human-readable domain names into IP addresses.
Like a phonebook for the internet.

### Domain Hierarchy
| Part | Example | Description |
|------|---------|-------------|
| TLD | .com | Top Level Domain — rightmost part |
| Second Level Domain | tryhackme | Main domain name, max 63 chars |
| Subdomain | admin | Left of domain, e.g. admin.tryhackme.com |

**TLD Types:**
- **gTLD** — Generic: .com (commercial), .org (organisation), .edu (education)
- **ccTLD** — Country code: .co.uk (UK), .ca (Canada)

### How a DNS Request Works
1. Browser checks **local cache** first
2. If not found → asks **Recursive DNS Server** (usually your ISP)
3. Recursive server checks its cache → if not found asks **Root DNS Server**
4. Root server directs to correct **TLD Server** (.com, .org etc)
5. TLD server points to **Authoritative DNS Server** (nameserver)
6. Authoritative server returns the DNS record
7. Result cached with **TTL (Time To Live)** value in seconds

---

## HTTP & HTTPS
**HTTP** = HyperText Transfer Protocol — rules for communicating
with web servers.
**HTTPS** = Secure version — data is encrypted, verifies you're
talking to the real server.


| Part | Purpose | Example |
|------|---------|---------|
| Scheme | Protocol to use | http, https, ftp |
| Host | Domain or IP of server | tryhackme.com |
| Port | Connection port | 80 (HTTP), 443 (HTTPS) |
| Path | Location of resource | /blog |
| Query String | Extra parameters | ?id=1 |
| Fragment | Location on page | #section2 |

### HTTP Methods
| Method | Purpose |
|--------|---------|
| GET | Retrieve information from server |
| POST | Submit data, create new records |
| PUT | Update existing information |
| DELETE | Delete information/records |

### HTTP Status Codes
| Range | Meaning |
|-------|---------|
| 200 | Success |
| 301 | Redirect permanently |
| 404 | Page not found |
| 500 | Server error |

### HTTP Request Example
GET / HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0

### HTTP Response Example
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 98

---

## How Websites Work

### Two Components
- **Frontend (Client-Side)** — what browser renders for the user
- **Backend (Server-Side)** — server processes requests and returns data

### Website Building Blocks
| Language | Purpose |
|----------|---------|
| HTML | Structure and content of the page |
| CSS | Styling and appearance |
| JavaScript | Interactivity and dynamic functionality |

### HTML Key Elements
| Tag | Purpose |
|-----|---------|
| `<!DOCTYPE html>` | Defines HTML5 document |
| `<html>` | Root element |
| `<head>` | Page info (title, metadata) |
| `<body>` | Visible content |
| `<h1>` | Large heading |
| `<p>` | Paragraph |
| `<script>` | JavaScript code |

---

## Security Vulnerabilities (SOC relevance)

### Sensitive Data Exposure
- Developers sometimes leave credentials or hidden links in HTML source
- Always check page source code during web app security assessments
- Look for HTML comments with passwords, hidden links, API keys

### HTML Injection
- Occurs when unfiltered user input is displayed on the page
- Attacker injects HTML or JavaScript into vulnerable website
- **Fix:** Input sanitisation — strip all HTML tags from user input
- **Rule:** Never trust user input

### Why this matters for SOC
- Web app attacks are among the most common attack vectors
- SOC analysts investigate alerts from WAFs triggered by injection attempts
- Understanding how HTTP works helps analyze web traffic in SIEM

---

## Key Takeaways
- DNS resolves domain names to IPs through a chain of servers
- TTL controls how long DNS records are cached
- HTTPS encrypts traffic — HTTP does not
- GET retrieves, POST submits, PUT updates, DELETE removes
- HTML injection happens when user input isn't sanitised
- Always check page source during security assessments
- Frontend = what you see, Backend = server logic
