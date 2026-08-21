# `D4RKGUNN3R // SECURITY OPERATIONS`

### Dylan Senez

`CYBERSECURITY` · `ACTIVE DIRECTORY` · `SOC` · `DETECTION ENGINEERING` · `PENETRATION TESTING`

> **Build the lab. Attack the system. Detect the activity. Document the findings.**

---

```
╔══════════════════════════════════════════════════════════════════════╗
║  // OPERATOR PROFILE                              REF // D4RK-01     ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                      ║
║  OPERATOR ........ Dylan Senez                                       ║
║  HANDLE .......... d4rkgunn3r                                        ║
║  CALLSIGN ........ D4RKGUNN3R                                        ║
║  DISCIPLINE ...... Cybersecurity / Computer Science                  ║
║  PRIMARY FOCUS ... Security Operations • Detection Engineering      ║
║  SECONDARY ....... Active Directory • Penetration Testing           ║
║  LAB ............. Windows AD • Kali • Microsoft Sentinel • Splunk  ║
║  TRAINING ........ Hack The Box • Home Lab • Security Research      ║
║  PLATFORM ........ Kali Linux • Windows • Azure • Docker            ║
║  VETERAN ......... USCG (6 years, Gunner's Mate GM2)                ║
║  BUSINESS ........ Anchor Watch Security Consulting                 ║
║                                                                      ║
║  MISSION ......... Learn the attack. Detect the attack.              ║
║                    Understand the system. Secure the enterprise.      ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

---

# `// WHOAMI`

Computer Science student and USCG veteran focused on **practical cybersecurity operations** through hands-on security operations, Active Directory environments, penetration testing, and **detection engineering**. Building expertise in the complete attack-to-detection cycle.

My goal is to understand an intrusion from **both sides simultaneously:**

```
ATTACK
   │
   ▼
TELEMETRY
   │
   ▼
DETECTION
   │
   ▼
INVESTIGATION
   │
   ▼
RESPONSE
   │
   ▼
DOCUMENTATION
   │
   ▼
AUTOMATION
```

I build **isolated enterprise environments** where I can:
1. **Execute** realistic attacks against Windows Active Directory
2. **Generate** attack telemetry (Sysmon, Event Logs, Network traffic)
3. **Collect** logs in SIEM (Microsoft Sentinel, Splunk)
4. **Engineer** detection rules from first principles
5. **Hunt** for indicators of compromise
6. **Investigate** attacks like a SOC analyst
7. **Document** everything to understand **why detection works**

The objective: **Turn every attack into a detection learning opportunity.**

---

# `// CURRENT OPERATIONS`

## 🛡️ SOC / ACTIVE DIRECTORY HOME LAB

Building an isolated enterprise-style cybersecurity lab designed to simulate real-world Windows Active Directory attacks and develop Microsoft Sentinel / Splunk detection capabilities.

### Infrastructure

```
             ┌─────────────────────────┐
             │   MICROSOFT SENTINEL    │
             │    SIEM / ANALYTICS     │
             └────────────┬────────────┘
                          │
                   LOG / TELEMETRY
                          │
         ┌────────────────┼────────────────┐
         │                │                │
         ▼                ▼                ▼
    ┌─────────┐    ┌─────────┐    ┌─────────────┐
    │ SPLUNK  │    │   DC-01 │    │   WIN-01    │
    │  SIEM   │    │ Windows │    │  Windows    │
    │         │    │ Server  │    │  Client     │
    │ (Dual   │    │   AD    │    │  Domain     │
    │  SIEM)  │    │   +     │    │  Joined     │
    └─────────┘    │ Sysmon  │    │             │
                   │   +     │    │  Sysmon     │
                   │ Azure   │    │  Telemetry  │
                   │ Monitor │    └─────────────┘
                   │ Agent   │
                   └────┬────┘
                        │
                   ATTACK / ENUMERATION
                        │
                        ▼
                   ┌──────────────┐
                   │   KALI-01    │
                   │  Attacker    │
                   │  System      │
                   └──────────────┘
```

### Environment

- **Domain Controller:** Windows Server 2022 with Active Directory
- **Workstation:** Windows 10 domain-joined client
- **Attacker:** Kali Linux for reconnaissance, enumeration, attacks
- **SIEM Stack:**
  - Microsoft Sentinel (Azure-based SIEM)
  - Splunk Enterprise (alternative SIEM for detection comparison)
- **Telemetry Collection:**
  - Sysmon (process execution, network connections, DNS queries)
  - Azure Monitor Agent
  - Splunk Universal Forwarder
  - Windows Security Event Logs
- **Infrastructure:** VMware host-only network (isolated), Docker

### Offensive Testing Capability

- Active Directory enumeration (LDAP, SMB, RPC)
- User and domain reconnaissance
- Kerberos attacks (Kerberoasting, AS-REP Roasting, Golden Tickets)
- Credential attacks (password spraying, brute force, credential stuffing)
- BloodHound / SharpHound analysis
- Lateral movement techniques
- Post-exploitation
- Windows privilege escalation
- Authentication attacks (NTLM relay, Pass-the-Hash, etc.)

### Defensive Analysis Capability

- **SIEM:** Microsoft Sentinel + KQL, Splunk + SPL
- **Detection Engineering:** Rule development from attack telemetry
- **Threat Hunting:** Proactive IOC correlation and pattern detection
- **Log Analysis:**
  - Windows Security Event Logs (4624, 4625, 4769, 4768, 4672, etc.)
  - Sysmon telemetry (Process execution, DNS queries, network connections, file operations)
  - Azure Monitor events
- **Investigation Workflows:**
  - Timeline correlation
  - Evidence collection
  - MITRE ATT&CK mapping
  - Impact assessment
- **Alert Triage & Response**

### Repository

[![SOC Lab](https://img.shields.io/badge/VIEW-SOC_LAB-0A66C2?style=for-the-badge)](https://github.com/Dylans7j/SOC-Lab)

---

# `// DETECTION ENGINEERING`

My **core focus this year:** Build a library of detection rules for the entire Windows attack kill chain.

### Attack → Detection Methodology

Each attack scenario follows this pattern:

```
┌────────────────────┐
│  ATTACK TECHNIQUE  │  (e.g., Kerberoasting)
│  (MITRE ATT&CK)    │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│     EXECUTE        │  (Run Rubeus, net.exe, etc.)
│   THE ATTACK       │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│  COLLECT TELEMETRY │  (Event ID 4769, Sysmon)
│  FROM BOTH SIEMs   │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│  DEVELOP QUERIES   │  (KQL + SPL)
│  (Sentinel + Splunk)
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│   VALIDATE IN LAB  │  (Reproduce detection)
│  AGAINST LIVE ATK  │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│   GITHUB COMMIT    │  (Document everything)
│   & DOCUMENTATION  │
└────────────────────┘
```



### Detection Engineering Workflow

```
UNDERSTAND THE ATTACK
  ├── Read attack documentation
  ├── Study MITRE ATT&CK technique
  └── Review event log generation

EXECUTE IN LAB
  ├── Prepare attack tools
  ├── Clear logs / baseline telemetry
  ├── Run attack
  └── Collect all generated events

ANALYZE TELEMETRY
  ├── Review Windows Event Logs
  ├── Inspect Sysmon data
  ├── Check network traffic
  └── Correlate across sources

DEVELOP QUERIES
  ├── Write KQL (Sentinel)
  ├── Write SPL (Splunk)
  ├── Test false positives
  └── Validate detection

DOCUMENTATION
  ├── Attack explanation
  ├── Query logic
  ├── Event IDs involved
  ├── Remediation steps
  └── GitHub commit
```

---

# `// ATTACK → DETECT FLOWCHART`

How attacks are converted into detections:

```
┌────────────────────┐
│  ATTACK TECHNIQUE  │
│   (Kerberoasting)  │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│ ATTACK EXECUTION   │
│ (rubeus.exe       │
│  kerberoast)      │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│   TELEMETRY GEN    │
│  Event ID 4769:    │
│  "Kerberos service │
│   ticket request"  │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│ SIEM COLLECTION    │
│ Sentinel ingest    │
│ Splunk forward     │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│    DETECTION       │
│    LOGIC           │
│ KQL: EventID 4769  │
│  | stats by user   │
│  | > 5 per hour    │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│     ALERT          │
│ "Suspected         │
│  Kerberoasting"    │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│  INVESTIGATION     │
│ Review context     │
│ Confirm legitimate │
│ vs attack          │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│    RESPONSE        │
│ Containment        │
│ Remediation        │
│ Escalation         │
└────────────────────┘
```

---

# `// OFFENSIVE SECURITY`

My penetration-testing workflow follows structured PTES methodology:

```
RECONNAISSANCE
      │
      ▼
ENUMERATION
      │
      ▼
VULNERABILITY ANALYSIS
      │
      ▼
INITIAL ACCESS
      │
      ▼
PRIVILEGE ESCALATION
      │
      ▼
LATERAL MOVEMENT
      │
      ▼
POST-EXPLOITATION
      │
      ▼
REPORTING
```

### Current Areas of Study

- Network enumeration & reconnaissance
- Active Directory attack vectors
- Kerberos protocol attacks
- LDAP queries & enumeration
- SMB enumeration
- NTLM authentication attacks
- BloodHound / graph analysis
- PowerShell exploitation
- Windows privilege escalation
- Linux privilege escalation
- Credential attacks & dumping
- Lateral movement techniques
- Access control abuse (ACL/DACL)
- Web application security
- API security
- Cloud authentication attacks

### Hack The Box Progress

**HTB CJCA:** ✅ COMPLETE (Certified)  
**CDSA Progress:** ~75% toward completion

**HTB Boxes Completed:** 450+ (Mix of Easy/Medium/Hard)

---

# `// ACTIVE DIRECTORY`

Deep understanding of Windows AD environments and attack surface:

```
ACTIVE DIRECTORY
│
├── Discovery
│   ├── DNS enumeration
│   ├── LDAP queries
│   ├── SMB shares
│   └── RPC services
│
├── User & Group Enumeration
│   ├── Domain users
│   ├── Domain groups
│   ├── Group memberships
│   ├── Service accounts
│   └── Privileged accounts
│
├── Computer & Trust Discovery
│   ├── Computers in domain
│   ├── Domain trusts
│   ├── Cross-forest trusts
│   └── External trusts
│
├── Kerberos Analysis
│   ├── AS-REP Roasting
│   ├── Kerberoasting
│   ├── Ticket analysis
│   └── Delegation attacks
│
├── Authentication Attacks
│   ├── Password spraying
│   ├── Credential stuffing
│   ├── Brute force
│   ├── NTLM relay
│   └── Responder poisoning
│
├── Access Control Analysis
│   ├── ACL enumeration
│   ├── DACL abuse
│   ├── Resource-based constraints
│   └── Delegation analysis
│
├── Lateral Movement
│   ├── Pass-the-Hash
│   ├── Pass-the-Ticket
│   ├── Overpass-the-Hash
│   ├── Kerberos delegation abuse
│   └── Living off the land
│
├── Persistence & Privilege Escalation
│
├── Detection (The Defense Side)
│   ├── Sysmon monitoring
│   ├── Event Log analysis
│   ├── SIEM detection rules
│   ├── Threat hunting
│   └── Alert triage
│
└── Remediation & Hardening
    ├── Event log configuration
    ├── Privileged account hardening
    ├── Trust relationship review
    └── Detection rule deployment
```

**Core Principle:** Never stop at exploitation. Understand **why each attack works, what evidence it leaves, how it can be detected, and how to prevent it.**

---

# `// SECURITY OPERATIONS`

SOC analyst workflow for processing and investigating security alerts:

### Investigation Workflow

```
ALERT
  │ What triggered?
  ▼
VALIDATE
  │ Real or false positive?
  ▼
COLLECT EVIDENCE
  │ What events are related?
  ▼
BUILD TIMELINE
  │ When did what happen?
  ▼
CORRELATE EVENTS
  │ Connect the dots
  ▼
IDENTIFY TECHNIQUE
  │ MITRE ATT&CK mapping
  ▼
DETERMINE SCOPE
  │ How many systems? Which users?
  ▼
ASSESS IMPACT
  │ What data could be accessed?
  ▼
CONTAIN
  │ Stop spread/persistence
  ▼
REMEDIATE
  │ Remove attacker
  ▼
DOCUMENT
  │ Write full report
  ▼
PREVENT
  │ Improve detection/hardening
```

### Current Defensive Focus

- Microsoft Sentinel (KQL queries, hunting, analytics rules)
- Splunk (SPL queries, correlation, dashboards)
- Windows Security Events (4624, 4625, 4634, 4672, 4768, 4769, etc.)
- Sysmon monitoring (Process execution, DNS, network, file operations)
- Active Directory telemetry
- Authentication anomalies
- Brute-force detection
- Password-spray detection
- Privilege escalation indicators
- Lateral movement indicators
- **Detection engineering** (building queries from first principles)
- Threat hunting (proactive pattern detection)
- Incident reporting & documentation
- MITRE ATT&CK framework mapping
- Attack timeline reconstruction

---

# `// TOOLKIT`

## 🔴 Offensive

[![Kali Linux](https://img.shields.io/badge/Kali_Linux-557C94?style=for-the-badge&logo=kalilinux&logoColor=white)](https://img.shields.io/badge/Kali_Linux-557C94?style=for-the-badge&logo=kalilinux&logoColor=white) [![Burp Suite](https://img.shields.io/badge/Burp_Suite-FF6633?style=for-the-badge&logo=burpsuite&logoColor=white)](https://img.shields.io/badge/Burp_Suite-FF6633?style=for-the-badge&logo=burpsuite&logoColor=white)

`Nmap` `NetExec` `Impacket` `Certipy` `Rubeus` `BloodHound` `SharpHound` `RustHound` `Kerbrute` `Hashcat` `Gobuster` `FFUF` `Evil-WinRM` `Wireshark` `Responder` `LDAP query tools`

## 🔵 Defensive

[![Microsoft Azure](https://img.shields.io/badge/Microsoft_Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)](https://img.shields.io/badge/Microsoft_Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white) [![Windows](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)

`Microsoft Sentinel` `KQL (Kusto Query Language)` `Splunk Enterprise` `SPL (Splunk Search Processing Language)` `Sysmon` `Windows Event Logs` `Azure Monitor Agent` `MITRE ATT&CK Framework` `Elastic Stack` `Sigma rules`

## 🟢 Engineering & Scripting

[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white) [![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=for-the-badge&logo=powershell&logoColor=white)](https://img.shields.io/badge/PowerShell-5391FE?style=for-the-badge&logo=powershell&logoColor=white) [![Bash](https://img.shields.io/badge/Bash-121011?style=for-the-badge&logo=gnu-bash&logoColor=white)](https://img.shields.io/badge/Bash-121011?style=for-the-badge&logo=gnu-bash&logoColor=white) [![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white) [![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white) [![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github)](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github)

---

# `// PROJECT INDEX`

| Project | Objective | Technology |
|---|---|---|
| 🛡️ [SOC-Lab](https://github.com/Dylans7j/SOC-Lab) | Attack and defend a Windows AD environment + detection engineering | AD · Kali · Sentinel · Splunk · Sysmon |
| 📚 [CHEATSHEETS](https://github.com/Dylans7j/CHEATSHEETS) | Comprehensive cybersecurity command reference & enumeration guide | Offense · Defense · Tools · Techniques |
| 🚩 [HackTheBox-Walkthroughs](https://github.com/Dylans7j/HackTheBox-Walkthroughs) | Document penetration-testing methodology for each solved box | Kali · Nmap · Web · AD · Exploitation |
| 🎓 [CS499-ePortfolio](https://github.com/Dylans7j/CS499-ePortfolio) | Computer Science capstone portfolio | Software Engineering · Security · Design |
| 🐧 [d4rkgunn3r-zsh-Setup](https://github.com/Dylans7j/d4rkgunn3r-zsh-Setup) | Linux terminal configuration and productivity tools | Linux · Bash · Zsh · Vim |

---

# `// LAB DOCUMENTATION STANDARD`

Every major security finding should answer six critical questions:

```
01 // WHAT WAS BUILT?
    Describe the attack, technique, or system being tested

02 // WHAT WAS TESTED?
    Specific scenario, prerequisites, initial conditions

03 // HOW WAS IT TESTED?
    Step-by-step commands and procedures

04 // WHAT EVIDENCE WAS GENERATED?
    Event IDs, Sysmon events, logs, network traffic

05 // HOW WAS IT DETECTED?
    SIEM queries (KQL/SPL), detection logic, alert mechanism

06 // HOW SHOULD IT BE REMEDIATED?
    Defensive measures, hardening steps, monitoring improvements
```

Example structure for each lab module:

```
ATTACK SCENARIO
├── Description & Context
├── MITRE ATT&CK Mapping
├── Prerequisites & Setup
├── Attack Execution Steps
├── Generated Telemetry (Events, Logs, Sysmon)
├── Detection Queries
│   ├── Sentinel KQL
│   ├── Splunk SPL
│   └── Alert Logic
├── Investigation Evidence
└── Remediation & Hardening
```

---

# `// CERTIFICATIONS & TRAINING`

```
┌──────────────────────────────────────────────────────┐
│ CREDENTIAL / TRAINING            STATUS              │
├──────────────────────────────────────────────────────┤
│ HTB CJCA                          ✅ COMPLETE         │
│ Hack The Box SOC Analyst Path     🔴 74.9% ACTIVE    │
│ CompTIA Security+ (Planned)       📋 Q4 2026          │
│ Active Directory Attacks          ✅ MASTERED         │
│ Microsoft Sentinel & KQL          ✅ ADVANCED         │
│ Detection Engineering             ✅ DEVELOPING       │
│ Kerberos & Authentication         ✅ ADVANCED         │
│ Penetration Testing Methodology   ✅ INTERMEDIATE     │
│ SIEM Operations (Splunk)          ✅ INTERMEDIATE     │
│ Threat Hunting                    🔴 ACTIVE           │
└──────────────────────────────────────────────────────┘
```

---

# `// PROFESSIONAL EXPERIENCE`

```
┌──────────────────────────────────────────────────────┐
│ ROLE / POSITION              ORGANIZATION            │
├──────────────────────────────────────────────────────┤
│ Security Officer             Stratus (Bridge Role)   │
│ USCG Gunner's Mate GM2       U.S. Coast Guard        │
│   (Weapons, Ordnance, Sec)   (6 Years Service)       │
│                                                      
└──────────────────────────────────────────────────────┘
```

**Anchor Watch Security Consulting:** Building custom security assessments, threat modeling, and detection engineering for organizations.

---

# `// GITHUB ACTIVITY`

[![](https://github-readme-stats.vercel.app/api?username=Dylans7j&show_icons=true&theme=transparent&hide_border=true)](https://github-readme-stats.vercel.app/api?username=Dylans7j&show_icons=true&theme=transparent&hide_border=true) [![](https://github-readme-stats.vercel.app/api/top-langs/?username=Dylans7j&layout=compact&theme=transparent&hide_border=true)](https://github-readme-stats.vercel.app/api/top-langs/?username=Dylans7j&layout=compact&theme=transparent&hide_border=true)

---

# `// CONNECT`

[![GitHub](https://img.shields.io/badge/GitHub-Dylans7j-181717?style=for-the-badge&logo=github)](https://github.com/Dylans7j)

```
OPERATOR ....... Dylan Senez
HANDLE ......... d4rkgunn3r
CALLSIGN ....... D4RKGUNN3R
DISCIPLINE ..... Cybersecurity / Computer Science
FOCUS .......... Security Operations • Detection Engineering
LOCATION ....... Michigan
VETERAN ........ USCG (GM2) • 6 Years Service
BUSINESS ....... Anchor Watch Security Consulting
```

---

# `// END TRANSMISSION`

### `BUILD // ATTACK // DETECT // DOCUMENT // REPEAT`

```
Detection Engineering:
Every attack teaches something.
Every detection prevents something.
Every remediation hardens everything.

Stay curious. Stay disciplined. Stay sharp.
```
