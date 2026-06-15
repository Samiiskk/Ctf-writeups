# TryHackMe — Pre-Security Path Completed! 🎉

**Date:** June 15, 2026
**Path:** Pre-Security
**Status:** - Path Complete

---

## Final Rooms Completed

### Computer Hardware & OS Security
- Hardware = physical components (CPU, RAM, HDD, keyboard)
- OS sits between hardware and applications
- CIA Triad applies to personal devices too

**Three main attack targets:**
| Attack | What it targets |
|--------|----------------|
| Weak passwords | Confidentiality |
| Weak file permissions | Confidentiality + Integrity |
| Malicious programs | Confidentiality, Integrity, Availability |

**Top weak passwords to never use:**
123456, password, qwerty, iloveyou, monkey — all in top 20 most used

---

### Cryptography Concepts

**Key terms:**
| Term | Meaning |
|------|---------|
| Plaintext | Readable message |
| Ciphertext | Scrambled unreadable version |
| Key | Secret that controls encryption/decryption |
| Algorithm | Public recipe — how encryption works |

**Caesar Cipher — learning example only:**
- Shifts each letter by a fixed number
- Key = 3: HELLO → KHOOR
- Not used in real systems — too easy to crack

### Symmetric vs Asymmetric Encryption

| | Symmetric | Asymmetric |
|-|-----------|-----------|
| Keys | One key for both | Public + private key pair |
| Speed | Very fast | Slower |
| Problem | Key distribution | Solved with public keys |
| Use case | Bulk data encryption | Sharing keys, certificates |

**How HTTPS works:**
1. Browser gets website's public key in certificate
2. Asymmetric encryption used to share a symmetric key
3. Symmetric encryption takes over for the session
4. Certificate Authority (CA) verifies the certificate is legitimate

**Key distribution problem:**
Symmetric encryption alone can't safely share the key →
Asymmetric encryption solves this → then symmetric takes over for speed.

---

### Offensive Security Basics

**Key terms:**
| Term | Meaning |
|------|---------|
| Scope | Boundaries of what's allowed to be tested |
| Vulnerability | Weakness that could be exploited |
| Exploit | Technique to take advantage of vulnerability |
| Enumeration | Collecting info about systems to find weaknesses |
| Dictionary attack | Using wordlist to guess passwords |
| Authentication | Verifying identity before granting access |

**Tools used:**
- **Gobuster** — discovers hidden web directories and pages
- **Hydra** — automates login attempts using wordlists

**Gobuster command:**
gobuster dir --url http://target.com/ -w /usr/share/wordlists/dirbuster/directory-list.txt

**Hydra command:**
hydra -l admin -P passlist.txt target.com http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect" -V

**Chain of weaknesses example:**
Hidden login page + weak password → admin access → full compromise

**Think like a hacker:**
- Ask "What if this doesn't work as intended?"
- Test unexpected inputs
- Chain small weaknesses together
- Think like an adversary

---

### Defensive Security Basics

**City analogy:**
| Security Concept | City Analogy |
|-----------------|-------------|
| Employee devices | Homes |
| Web server | Shop/public buildings |
| Mail server | Post office |
| Firewall | City gate |
| Internet | Everything outside the city |

**Defender mindset:**
- **Prevention** — stop attacks before they happen
- **Detection** — monitor for suspicious activity
- **Mitigation** — limit damage during incident
- **Analysis** — investigate what happened
- **Response** — recover and improve

**Defensive career paths:**
- **SOC Analyst** — monitors alerts, investigates incidents
- **Threat Intelligence** — researches threats and attackers
- **DFIR** — Digital Forensics & Incident Response

---

## Key Takeaways from Pre-Security Path
- CIA Triad is the foundation of everything in security
- Weak passwords are still the #1 attack vector
- Symmetric = fast, Asymmetric = secure key sharing
- HTTPS uses both — asymmetric first, then symmetric
- Ethical hacking requires explicit permission and defined scope
- Gobuster finds hidden pages, Hydra cracks weak passwords
- Defense is layered — no single tool stops everything
- SOC is the entry point — exactly your target role ✅

---

## 🎉 Pre-Security Path Complete!
Ready to continue with SOC Level 1 path.
