# TryHackMe — SOC Level 1: Human & System Attack Vectors

**Date:** June 16, 2026
**Path:** SOC Level 1 — in progress
**Status:** ✅ Rooms completed

---

## Why Humans Are Targeted

Humans provide access — to websites, mailboxes, databases.
The easiest way into a network is through a person, not a firewall.

| Attack | What attacker gains |
|--------|-------------------|
| Breach HR manager's Google account | Steal entire employee database |
| Trick wealthy person into running malware | Hijack web banking session |
| Breach IT admin's VPN account | Access heart of corporate network |
| Trick government worker into sharing secrets | Simplify future attacks |

---

## Social Engineering
Manipulating victims into helping the attacker — knowingly or not.

**Two key ingredients:**
- **Trustworthy** — attacker appears legitimate
- **Emotional** — triggers urgency, fear, or curiosity

### Types of Human Attack Vectors

| Attack | How it works |
|--------|-------------|
| Phishing | Fake emails with malicious links — 3.4 billion sent daily |
| Malware downloads | Fake apps, fake CAPTCHAs, malicious QR codes, SEO poisoning |
| Deepfakes | AI-generated video/audio impersonating bosses or colleagues |
| Impersonation | Pretending to be IT support via phone call |
| USB drop | Leaving malicious USB drives in public places |
| Fake job offers | Luring targets into installing malware |

**Real example:** Finance worker received deepfake video call from
"boss" and wired $25 million for a fake urgent business deal.

---

## Defending Humans — SOC Analyst Role

### Mitigation Measures
| Measure | What it does |
|---------|-------------|
| Anti-phishing solution | Blocks phishing emails before users see them |
| Antivirus/EDR | Prevents malware execution on endpoints |
| Trust but verify | Train employees to verify suspicious requests |
| Security awareness training | Teach phishing detection + run simulations |

**Key point:** No mitigation is perfect — threats will get through.
That's why SOC detection skills matter.

---

## System Attack Vectors

Systems are high-value targets — breaching one server affects
thousands of users vs one person.

| Breached System | Attack Value |
|----------------|-------------|
| Student laptop | Steal gaming accounts, add to botnet |
| Bank IT admin laptop | Access internal banking systems |
| Law firm mail server | Dump all mailboxes, blackmail victims |
| Industrial network server | Encrypt entire network with ransomware |
| Government website panel | Website defacement |

---

## Three Ways Systems Are Attacked

### 1. Human-Led Attacks
- Malicious USB drives found in public
- Downloading malware from pirated resources
- Reusing weak passwords across accounts
- **81% of breaches involve stolen or weak passwords**

### 2. Software Vulnerabilities
- Every piece of software can have security flaws
- **2024:** Over 40,000 vulnerabilities published, 300+ actively exploited
- **Shellshock** — Linux vulnerability existed since 1992, found in 2014
- **Zero-day** — vulnerability found by attackers before defenders
- Once public → assigned a **CVE number**
- Race begins: attackers build exploits, defenders rush to patch

**Responding to vulnerabilities:**
- Apply vendor patch as soon as available
- Restrict access to trusted IPs temporarily
- Block known attack patterns on IPS or WAF
- Apply vendor's temporary workarounds

### 3. Supply Chain Attacks
- Attackers breach a trusted app or library used by thousands
- Malicious update pushed to all users → all compromised
- **Famous examples:** SolarWinds, 3CX breaches
- Hard to defend — you can't control all software dependencies
- SOC must be ready to detect and respond

---

## Misconfigurations
Not a software bug — a mistake in how the system was set up.

**Real examples:**
- "123456" password exposed 64 million McDonald's job applications
- Misconfigured AWS cloud breached 106 million bank customers
- Improperly configured smart fridges used in botnet attacks

**Responding to misconfigurations:**
- Penetration testing — hire ethical hackers to find flaws
- Vulnerability scans — detect default passwords and outdated software
- Configuration audits — review systems against CIS benchmarks

---

## CVE (Common Vulnerabilities and Exposures)
- Public database of known vulnerabilities
- Each vulnerability gets a unique CVE number
- Defenders use CVEs to prioritize patching
- Attackers use CVEs to build exploits

---

## Key Takeaways
- Humans are the weakest link — social engineering is most common attack
- Phishing = 3.4 billion malicious emails sent daily
- Deepfakes and impersonation are growing threats
- 81% of breaches involve stolen or weak passwords
- Zero-days are the most dangerous — no patch exists yet
- Supply chain attacks are hard to prevent — detection is key
- Misconfigurations are as dangerous as vulnerabilities
- SOC role = detect what mitigation missed
- CVE number = public acknowledgment of a vulnerability
