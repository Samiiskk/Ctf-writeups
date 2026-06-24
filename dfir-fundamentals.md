# TryHackMe — DFIR Fundamentals

**Date:** June 24, 2026
**Path:** DFIR Track
**Status:** ✅ Room completed

---

## What is DFIR?

**DFIR = Digital Forensics + Incident Response**

Collects forensic artifacts from digital devices (computers, phones, media) to investigate incidents. Helps identify attacker footprints, determine breach extent, and restore environment.

---

## Why DFIR Matters

1. **Find evidence** of attacker activity (signal from noise)
2. **Remove attackers** completely (no persistent access)
3. **Identify extent + timeframe** (breach scope communication)
4. **Find vulnerabilities** that led to breach (prevention)
5. **Understand attacker behavior** (proactive blocking)
6. **Share threat intel** with community

---

## Who Does DFIR?

### Skill Requirements
| Role | Expertise |
|------|-----------|
| **Digital Forensics** | Identify forensic artifacts + evidence of human activity |
| **Incident Response** | Cybersecurity focus using forensic info to identify threats |

DFIR professionals combine both domains.

---

## Core DFIR Concepts

### Artifacts
- Pieces of evidence pointing to activities on a system
- Collected to support hypotheses about attacker activity
- Example: Registry keys maintaining persistence
- Collected from: filesystem, memory, network activity

### Evidence Preservation

**Chain of Custody:** Evidence kept in secure custody throughout investigation.
- No unauthorized handling
- Maintains integrity
- Any mishandling contaminates chain
- Weakens legal case with unknown variables

**Integrity Process:**
1. Collect original evidence
2. Write-protect it
3. Make copy for analysis
4. Original stays safe for future copies if needed

### Order of Volatility
Capture evidence by volatility priority (most volatile first):

1. **RAM** (most volatile) — lost when powered off
2. **Swap/Temp files**
3. **Network connections**
4. **Running processes**
5. **Filesystem**
6. **Hard drive** (persistent storage)

### Timeline Creation
- Chronological ordering of all activities
- Provides investigation perspective
- Collates info from multiple sources
- Reconstructs "story" of what happened
- Critical for understanding attack chain

---

## DFIR Tools

| Tool | Purpose | Category |
|------|---------|----------|
| **KAPE** (Eric Zimmerman) | Automates collection + parsing of forensic artifacts, timeline creation | Automation |
| **Autopsy** | Open-source forensics platform for mobile/hard drives/removable media | Analysis |
| **Volatility** | Memory analysis for Windows + Linux | Memory Analysis |
| **Redline** | Incident response tool by FireEye, gathers forensic data | Data Gathering |
| **Velociraptor** | Advanced endpoint monitoring, forensics, response | Endpoint |

---

## Incident Response Process (PICERL)

### 1. Preparation
- Before incident happens
- Have people, processes, technology ready
- Prevention + response infrastructure

### 2. Identification
- Incident identified through indicators
- Analyze for false positives
- Document findings
- Communicate to stakeholders

### 3. Containment
- Limit incident effects
- Short-term + long-term fixes based on forensic analysis
- Isolate affected systems

### 4. Eradication
- Remove threat from network
- Ensure entry point is plugged
- Requires forensic analysis to be complete
- Cannot eradicate without knowing how attacker got in

### 5. Recovery
- Restore disrupted services
- Return to pre-incident state
- Verify systems functioning normally

### 6. Lessons Learned
- Review incident
- Document everything
- Identify improvements
- Train team for next incident
- Update procedures + playbooks

---

## DFIR Workflow
Incident Detected

↓

[IDENTIFICATION] Analyze indicators for FP

↓

[CONTAINMENT] Isolate + limit damage

↓

[ERADICATION] Remove threat (after forensics confirm)

↓

[RECOVERY] Restore services

↓

[LESSONS LEARNED] Review + improve

↓

[PREPARATION] Updated defense strategy
---

## Evidence Categories

### Host-Centric Evidence
- File access logs
- Authentication attempts
- Process execution
- Registry modifications
- PowerShell execution
- Startup programs
- Installed software

### Network-Centric Evidence
- SSH connections
- FTP transfers
- Web traffic
- VPN access
- Network file sharing
- DNS queries
- Firewall logs

---

## Key Principles

1. **Preserve evidence integrity** — maintain chain of custody
2. **Respect order of volatility** — capture volatile first
3. **Document everything** — timeline reconstruction
4. **Communicate findings** — relevant stakeholders
5. **Follow legal standards** — evidence admissibility
6. **Continuous improvement** — lessons learned application

---

## Takeaways
- DFIR combines forensics + incident response
- Artifacts are evidence of activity
- Order of volatility = RAM before hard drive
- Chain of custody = legal validity
- Timeline creation = understanding attack sequence
- Six PICERL phases guide all IR efforts
- Tools automate collection + analysis
- Human expertise essential for interpretation
