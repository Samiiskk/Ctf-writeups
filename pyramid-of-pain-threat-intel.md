# TryHackMe — Pyramid of Pain & Threat Intelligence

**Date:** June 25, 2026
**Path:** SOC Level 1
**Status:** ✅ Room completed

---

## Pyramid of Pain

Framework showing how difficult it is for attackers to change each type of indicator when detected. Higher = more painful for attacker.
    /\
   /  \          TTPs
  /----\         (Most painful — attacker must retrain)
 /      \
/--------\       Tools

/          \      (Attacker must rebuild/find new tool)

/------------

/              \    Network/Host Artifacts

/----------------\   (Attacker needs more time)

\                /

--------------/    Domain Names

\            /     (Need to register new domain)

----------/

\        /       IP Addresses

------/        (Easy to change — VPN, proxy)

\    /

--/          Hash Values

/           (Easiest — change one bit)

---

## Level 1: Hash Values (Trivial)

**What:** Unique numeric fingerprints identifying files.

### Common Hashing Algorithms

| Algorithm | Bits | Status |
|-----------|------|--------|
| MD5 | 128-bit | NOT cryptographically secure (collision attacks) |
| SHA-1 | 160-bit | Deprecated by NIST 2011, banned for digital signatures 2013 |
| SHA-256 | 256-bit | Current standard — recommended |

**Why trivial for attackers:**
Changing even ONE BIT of a file produces a completely different hash.

```powershell
# Before modification
Get-FileHash .\file.msi -Algorithm MD5
# Hash: D1A008E3A606F24590A02B853E955CF7

# After appending one string
echo "AppendTheHash" >> .\file.msi
Get-FileHash .\file.msi -Algorithm MD5
# Hash: 9D52B46F5DE41B73418F8E0DACEC5E9F
```

**Detection tools:** VirusTotal, MetaDefender Cloud (OPSWAT)

---

## Level 2: IP Addresses (Easy)

**What:** Numeric identifiers for devices on a network.

**Why easy for attackers:** Use VPN, proxy, Tor, or cloud services to swap IPs quickly.

**Detection:** Firewall logs, SIEM alerts, threat intel feeds.

---

## Level 3: Domain Names (Simple)

**What:** Human-readable mapping to IP addresses (e.g. evilcorp.com).

**Slightly harder** — attacker needs to:
- Purchase domain
- Register it
- Modify DNS records

**Attack technique: Punycode attacks**
- Use Unicode characters that look like legitimate domains
- Example: `adıdas.de` looks like `adidas.de` but uses different character
- Punycode: `http://xn--addas-o4a.de/`
- Modern browsers now translate these

**URL Shorteners used by attackers:**
- bit.ly, goo.gl, ow.ly, tinyurl.com, tiny.pl, x.co
- Tip: Add `+` to end of shortened URL to see redirect destination

**Detection:** Proxy logs, web server logs, DNS filtering.

---

## Level 4: Network/Host Artifacts (Annoying)

**What:** Observable evidence left behind by attacker activity.
- User-Agent strings
- C2 (Command & Control) information
- URI patterns in HTTP POST requests
- Registry keys, files dropped

**Why annoying:** Attacker needs more time to modify tactics.

**Detection with TShark:**
```bash
tshark --Y http.request -T fields -e http.host -e http.user_agent -r analysis_file.pcap
```

**Detection tools:**
- Wireshark / TShark — analyze PCAPs
- Snort — IDS alerts
- Any.run sandbox — view:
  - HTTP Requests tab
  - Connections tab
  - DNS Requests tab

---

## Level 5: Tools (Challenging)

**What:** Software attackers use:
- Malicious macro documents (maldocs) for spearphishing
- Backdoors for C2 establishment
- Custom .EXE / .DLL files
- Payloads
- Password crackers

**Why challenging:** Attacker must:
- Invest money building new tools
- Find equivalent tool
- Learn new tool proficiency

**Detection:**
- Antivirus signatures
- YARA rules
- Detection rules
- **Fuzzy hashing (SSDeep)** — similarity analysis between files

**Resources:**
- MalwareBazaar — malware samples + YARA results
- Malshare — malicious feeds
- SOC Prime Threat Detection Marketplace — community detection rules

---

## Level 6: TTPs (Most Painful)

**What:** Tactics, Techniques, and Procedures — HOW the attacker operates.

**Why most painful:** If you can detect TTPs:
- Attacker must completely retrain
- Change their entire methodology
- Near-impossible to maintain stealth
- Often means attacker gives up

**Framework:** MITRE ATT&CK maps all known TTPs.

---

## Sandbox Analysis with Any.run

When investigating suspicious files, Any.run executes samples and shows:

| Tab | What it shows |
|-----|--------------|
| **HTTP Requests** | Resources retrieved from web (droppers, callbacks) |
| **Connections** | All communications (C2 traffic, FTP, lateral movement) |
| **DNS Requests** | DNS queries (connectivity checks, call-home domains) |

⚠️ Never visit IPs or URLs from sandbox reports directly!

---

## Practical Hash Lookups

**VirusTotal:** Check file hashes against 70+ antivirus engines
- Look for filename in results
- Check detection ratio
- View behavioral analysis

**MetaDefender Cloud:** Alternative hash lookup platform

---

## Key Takeaways
- Pyramid of Pain = framework for prioritizing threat intelligence
- Hash values are trivial for attackers to bypass (change one bit)
- TTPs are hardest for attackers to change (most valuable to detect)
- Punycode attacks exploit Unicode to fake legitimate domains
- URL shorteners hide malicious destinations (add + to reveal)
- TShark can detect malicious User-Agent strings in PCAPs
- YARA rules + fuzzy hashing = powerful tool detection
- Any.run sandbox shows full network behavior of malware
- Higher on the pyramid = more pain for attacke
