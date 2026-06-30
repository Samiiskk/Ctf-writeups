# TryHackMe — Cyber Kill Chain

**Date:** June 26, 2026
**Path:** SOC Level 1
**Status:** - Room completed

---

## What is the Cyber Kill Chain?

Military concept adapted by **Lockheed Martin** in 2011 for cybersecurity. Defines the steps adversaries follow during an attack. To succeed, attacker must go through ALL phases.

**Why it matters as SOC Analyst:**
- Recognize intrusion attempts at each stage
- Understand attacker's goals/objectives
- Identify missing security controls
- Assess network security gaps

---

## The 7 Phases

### 1. Reconnaissance
Research and planning phase — gathering info about target.

**Characteristics:**
- Often passive and undetected
- Poor recon = sloppy attacks
- Good recon = highly targeted, believable attacks

**Two Types:**
| Type | Description | Examples |
|------|-------------|----------|
| **Passive** | No direct interaction with target | WHOIS lookups, social media scraping, breach data review |
| **Active** | Direct contact with target | Social engineering, port scanning, banner grabbing |

**OSINT (Open-Source Intelligence) sources:**
- Search engines
- Print/online media
- Social media accounts
- Online forums/blogs
- Public record databases
- WHOIS and technical data

**OSINT Tools:**
- **theHarvester** — gathers emails, names, subdomains, IPs, URLs
- **Hunter.io** — email hunting tied to domains
- **OSINT Framework** — collection of categorized OSINT tools

**Email Harvesting:** Obtaining email addresses for phishing attacks.

---

### 2. Weaponization
Turning raw recon info into actionable attack tools.

**Key Terms:**
- **Malware** — program designed to damage/disrupt/gain unauthorized access
- **Exploits** — code taking advantage of vulnerabilities
- **Payload** — malicious code attacker runs on system

**Attacker Options:**
- Buy pre-made payload from Dark Web
- Write custom malware (sophisticated/APT actors)
- Create infected Office docs with malicious macros/VBA
- Implant malware on USB drives for distribution
- Set up C2 (Command & Control) infrastructure
- Create backdoors
- Craft phishing templates or OAuth-consent apps

---

### 3. Delivery
Method of transmitting payload to target environment.

**Common Methods:**

| Method | Description |
|--------|-------------|
| **Phishing email** | Spear phishing (targeted) or mass phishing with malicious link/attachment |
| **USB drops** | Physical delivery in public places (coffee shops, parking lots) |
| **Watering hole attacks** | Compromise website victims regularly visit, redirect to malicious site |

---

### 4. Exploitation
Attacker's code executes on target, exploiting known vulnerability.

**Techniques:**
- **Malicious macro execution** — ransomware deployed via phishing email
- **Zero-day exploits** — unknown/unpatched flaws (no detection initially)
- **Known CVEs** — exploiting unpatched public vulnerabilities

**Signs to watch for:**
- Unexpected process spawns
- Registry changes or new services
- Suspicious command-line arguments in logs

---

### 5. Installation
Establishing persistence — backdoor access for future reconnection.

**Why persistence matters:**
- Reconnect if connection lost
- Maintain access if detected/removed
- Survive system patches

**Persistence Techniques:**

| Technique | Description |
|-----------|-------------|
| **Web shell** | Malicious script (.php, .asp, .jsp) on webserver — hard to detect |
| **Backdoor install** | E.g., Meterpreter — interactive remote shell |
| **Service modification** | MITRE T1543.003 — create/modify Windows services |
| **Registry Run Keys** | Add entry to execute payload on every login |
| **Startup Folder** | Individual or system-wide — executes at login |

**Anti-forensics technique:**
- **Timestomping** — modify file timestamps (modify, access, create, change) to avoid detection and appear legitimate

---

### 6. Command & Control (C2)
Attacker opens channel to remotely control victim machine.

**Also known as:** C&C or C2 Beaconing

**How it works:**
- Infected host consistently communicates with C2 server ("beaconing")
- Attacker gains full control after connection established

**Common C2 Channels:**

| Channel | Why used |
|---------|----------|
| **HTTP (port 80) / HTTPS (port 443)** | Blends with legitimate traffic, evades firewalls |
| **DNS** | Constant DNS requests to attacker's server (DNS Tunneling) |

**Note:** IRC was traditional C2 but now easily detected by modern security solutions.

---

### 7. Actions on Objectives
Attacker achieves original goals with hands-on-keyboard access.

**What attackers do:**
- Collect credentials from users
- Privilege escalation (workstation → domain admin)
- Internal reconnaissance (find more vulnerabilities)
- Lateral movement through environment
- Collect and exfiltrate sensitive data
- Delete backups/shadow copies (anti-recovery)
- Overwrite or corrupt data

---

## Full Attack Flow
RECONNAISSANCE → WEAPONIZATION → DELIVERY → EXPLOITATION 
→ INSTALLATION → C2 → ACTIONS ON OBJECTIVES

Each phase builds on the previous. Defenders who disrupt ANY phase can stop the attack chain.

---

## Defender Strategy

**Key insight:** The EARLIER you detect/disrupt the chain, the LESS damage occurs.

| Phase | Defender Action |
|-------|-----------------|
| Recon | Limit public info exposure, monitor for scanning |
| Weaponization | Threat intel on malware trends |
| Delivery | Email filtering, USB restrictions |
| Exploitation | Patch management, EDR |
| Installation | FIM, registry monitoring |
| C2 | Network traffic analysis, DNS monitoring |
| Actions on Objectives | DLP, backup protection |

---

## Key Takeaways
- 7 phases: Recon → Weaponization → Delivery → Exploitation → Installation → C2 → Actions on Objectives
- OSINT is critical reconnaissance tool
- Persistence techniques include web shells, backdoors, registry keys
- C2 often hides in legitimate-looking HTTP/HTTPS/DNS traffic
- Earlier detection in the chain = less damage
- Understanding kill chain helps identify security control gaps
