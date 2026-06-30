# TryHackMe — Understanding the Dark Web, Deep Web & Surface Web

**Date:** June 26, 2026
**Path:** SOC Level 1 / Threat Intelligence
**Status:** - Room completed

---

## The Three Layers of the Internet
    SURFACE WEB (< 5%)
─────────────────────────
     DEEP WEB (~90%)
─────────────────────────
   DARK WEB (small %
   of deep web)

---

## Surface Web (Open Web)

**What it is:** The "visible" internet — accessed via Google, Yahoo, Chrome, Firefox.

**Characteristics:**
- Under 5% of total internet
- Indexed by search engines via "crawling"
- Registry operators: .com, .org, etc.
- Easily found and accessed

---

## Deep Web

**What it is:** Everything below the surface — NOT indexed by search engines.

**Size:** ~90% of all websites — impossible to know exact size

**Includes:**
- **Databases** — public/private file collections, searchable only within themselves
- **Intranets** — internal networks for organizations
- Academic journals
- Private databases

**You likely use the deep web DAILY:**
- Banking/financial accounts
- Email and messaging
- Private enterprise databases
- HIPAA medical documentation
- Legal files

**Important:** Most deep web content is LEGAL and SAFE. People often confuse "deep web" with "dark web."

---

## Dark Web

**What it is:** Hidden part of deep web, NOT accessible via normal browsers — requires Tor or similar.

**Key characteristics:**
- No indexing by surface web search engines
- "Virtual traffic tunnels" via randomized network infrastructure
- Inaccessible by traditional browsers
- Hidden by firewalls and encryption

**What's on the dark web:**

| Legal Uses | Illegal Uses |
|-----------|--------------|
| Privacy/free speech | Stolen data markets |
| Whistleblower platforms | Malware/hacking tool sales |
| Political dissidents | Leaked credentials trading |
| Abuse victim protection | Illegal goods marketplaces |
| | Scams |

---

## Key Safety Points

1. **Visiting dark web ≠ illegal** by itself
2. Many ACTIVITIES there ARE illegal and risky
3. **Your data can end up there** via data breaches — even if you never visit
4. Reduce risk with security monitoring tools
5. Only access with legitimate reason + strict safety rules
6. Deep web safety matters MORE for average users (easier to accidentally encounter)

---

## Why This Matters for SOC Analysts

- **Threat intelligence:** Monitor dark web for leaked company credentials
- **Breach detection:** Check if employee data appears in dark web markets
- **Brand protection:** Identify phishing kits targeting your organization
- **IOC gathering:** Malware samples and TTPs often shared on dark web forums

---

## Key Takeaways
- Surface web = <5% (Google-indexed)
- Deep web = ~90% (databases, intranets, private accounts)
- Dark web = small hidden portion of deep web (Tor-only)
- Most deep web activity is legal and used daily
- Dark web has both legitimate (privacy) and illegitimate (crime) uses
- Personal data exposure can happen without ever visiting dark web yourself
- SOC analysts use dark web monitoring for threat intelligence
