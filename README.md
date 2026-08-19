<div align="center">

# `D4RKGUNN3R // SECURITY OPERATIONS`

### Dylan Senez

`CYBERSECURITY` · `ACTIVE DIRECTORY` · `SOC` · `PENETRATION TESTING` · `SECURITY ENGINEERING`

> **Build the lab. Attack the system. Detect the activity. Document the findings.**

</div>

---

```text
╔══════════════════════════════════════════════════════════════════════╗
║  // OPERATOR PROFILE                              REF // D4RK-01     ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                      ║
║  OPERATOR ........ Dylan Senez                                       ║
║  HANDLE .......... d4rkgunn3r                                        ║
║  DISCIPLINE ...... Cybersecurity / Computer Science                  ║
║  PRIMARY FOCUS ... Security Operations • Active Directory           ║
║  SECONDARY ....... Penetration Testing • Detection Engineering      ║
║  LAB ............. Windows AD • Kali • Microsoft Sentinel           ║
║  TRAINING ........ Hack The Box • Home Lab • Security Research      ║
║  PLATFORM ........ Kali Linux • Windows • Azure • Docker            ║
║                                                                      ║
║  MISSION ......... Learn the attack. Detect the attack.              ║
║                    Understand the system. Document everything.        ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

# `// WHOAMI`

Computer Science student focused on developing practical cybersecurity skills through hands-on security operations, Active Directory environments, penetration testing, detection engineering, and adversary simulation.

My goal is to understand an intrusion from both sides:

```text
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
```

I build environments where I can generate attacks, collect the resulting telemetry, investigate what happened, engineer detections, and document the entire process.

---

# `// CURRENT OPERATIONS`

## 🛡️ SOC / ACTIVE DIRECTORY HOME LAB

Building an isolated enterprise-style cybersecurity lab designed to simulate attacks against a Windows Active Directory environment and analyze the resulting telemetry.

### Infrastructure

```text
                    ┌─────────────────────────┐
                    │   MICROSOFT SENTINEL    │
                    │    SIEM / ANALYTICS     │
                    └────────────┬────────────┘
                                 │
                          LOG / TELEMETRY
                                 │
                ┌────────────────┴────────────────┐
                │                                 │
                ▼                                 ▼
       ┌─────────────────┐              ┌─────────────────┐
       │      DC-01      │              │     WIN-01      │
       │ Windows Server  │◄────────────►│ Windows Client  │
       │ Active Directory│              │  Domain Joined  │
       └────────┬────────┘              └─────────────────┘
                │
                │ ATTACK / ENUMERATION
                ▼
       ┌─────────────────┐
       │     KALI-01     │
       │ Attacker System │
       └─────────────────┘
```

### Environment

- Windows Server Domain Controller
- Windows domain workstation
- Kali Linux attacker machine
- Microsoft Azure
- Microsoft Sentinel
- Azure Monitor Agent
- Windows Security Event Logs
- Sysmon
- VMware
- Docker

### Offensive Testing

- Active Directory enumeration
- LDAP reconnaissance
- SMB enumeration
- Password spraying
- Kerberos attacks
- Credential attacks
- BloodHound analysis
- Windows lateral movement
- Authentication testing

### Defensive Analysis

- Microsoft Sentinel
- KQL hunting
- Windows Event Logs
- Sysmon telemetry
- Authentication investigation
- Detection engineering
- Alert triage
- IOC correlation
- MITRE ATT&CK mapping

### Repository

[![SOC Lab](https://img.shields.io/badge/VIEW-SOC_LAB-0A66C2?style=for-the-badge)](https://github.com/Dylans7j/SOC-Lab)

---

# `// ATTACK → DETECT`

My lab methodology connects offensive actions directly to defensive telemetry.

```text
┌────────────────────┐
│  ATTACK TECHNIQUE  │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│     TELEMETRY      │
│ Event Logs / Sysmon│
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│      SIEM / KQL    │
│ Microsoft Sentinel │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│     DETECTION      │
│ Rule / Hunt / Alert│
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│   INVESTIGATION    │
│ Correlate Evidence │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│      REPORTING     │
│ Impact / Remediate │
└────────────────────┘
```

---

# `// OFFENSIVE SECURITY`

My offensive-security workflow follows a structured penetration-testing methodology.

```text
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

- Network enumeration
- Active Directory
- Kerberos
- LDAP
- SMB
- NTLM
- BloodHound
- PowerShell
- Windows privilege escalation
- Linux privilege escalation
- Web application security
- Credential attacks
- Lateral movement
- Access-control abuse

### Hack The Box

[![Hack The Box](https://img.shields.io/badge/VIEW-HTB_WALKTHROUGHS-9FEF00?style=for-the-badge&logo=hackthebox&logoColor=black)](https://github.com/Dylans7j/HackTheBox-Walkthroughs)

---

# `// ACTIVE DIRECTORY`

```text
ACTIVE DIRECTORY
│
├── Discovery
│   ├── DNS
│   ├── LDAP
│   ├── SMB
│   └── RPC
│
├── Enumeration
│   ├── Users
│   ├── Groups
│   ├── Computers
│   ├── Shares
│   └── Domain Trusts
│
├── Graph Analysis
│   └── BloodHound
│
├── Kerberos
│   ├── AS-REP Roasting
│   └── Kerberoasting
│
├── Authentication
│   ├── Password Spraying
│   ├── NTLM
│   └── Credential Attacks
│
├── Access Control
│   ├── ACL Analysis
│   └── DACL Abuse
│
├── Lateral Movement
│
└── Detection
    ├── Event Logs
    ├── Sysmon
    ├── Sentinel
    └── KQL
```

The objective is not simply getting access.

The objective is understanding **why the attack works, what telemetry it produces, how it can be detected, and how it should be remediated.**

---

# `// SECURITY OPERATIONS`

### Investigation Workflow

```text
ALERT
  │
  ▼
VALIDATE
  │
  ▼
COLLECT EVIDENCE
  │
  ▼
CORRELATE EVENTS
  │
  ▼
BUILD TIMELINE
  │
  ▼
IDENTIFY ATT&CK TECHNIQUE
  │
  ▼
DETERMINE IMPACT
  │
  ▼
CONTAIN / REMEDIATE
  │
  ▼
DOCUMENT
```

### Current Defensive Focus

- Microsoft Sentinel
- KQL
- Windows Security Events
- Sysmon
- Active Directory telemetry
- Authentication anomalies
- Brute-force detection
- Password-spray detection
- Privilege escalation indicators
- Lateral movement indicators
- Detection engineering
- Threat hunting
- Incident reporting

---

# `// TOOLKIT`

## 🔴 Offensive

![Kali Linux](https://img.shields.io/badge/Kali_Linux-557C94?style=for-the-badge&logo=kalilinux&logoColor=white)
![Burp Suite](https://img.shields.io/badge/Burp_Suite-FF6633?style=for-the-badge&logo=burpsuite&logoColor=white)

`Nmap`
`NetExec`
`BloodHound`
`SharpHound`
`RustHound`
`Impacket`
`Certipy`
`Kerbrute`
`Hashcat`
`Gobuster`
`FFUF`
`Evil-WinRM`
`Wireshark`

## 🔵 Defensive

![Microsoft Azure](https://img.shields.io/badge/Microsoft_Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Windows](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)

`Microsoft Sentinel`
`KQL`
`Sysmon`
`Windows Event Logs`
`Azure Monitor Agent`
`MITRE ATT&CK`

## 🟢 Engineering

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=for-the-badge&logo=powershell&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-121011?style=for-the-badge&logo=gnubash&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)

---

# `// PROJECT INDEX`

| Project | Objective | Technology |
|---|---|---|
| 🛡️ [SOC Active Directory Lab](https://github.com/Dylans7j/SOC-Lab) | Attack and defend a Windows domain environment | AD · Kali · Sentinel · Sysmon |
| 🚩 [Hack The Box Walkthroughs](https://github.com/Dylans7j/HackTheBox-Walkthroughs) | Document penetration-testing methodology | Kali · Nmap · AD · Web |
| 🎓 [CS499 ePortfolio](https://github.com/Dylans7j/CS499-ePortfolio) | Computer Science capstone portfolio | Software Engineering |
| 🐧 [D4RKGUNN3R ZSH Setup](https://github.com/Dylans7j/d4rkgunn3r-zsh-Setup) | Linux terminal configuration | Linux · Bash · Zsh |

---

# `// LAB DOCUMENTATION STANDARD`

Every major security project should answer six questions:

```text
01 // WHAT WAS BUILT?

02 // WHAT WAS TESTED?

03 // HOW WAS IT TESTED?

04 // WHAT EVIDENCE WAS GENERATED?

05 // HOW WAS IT DETECTED?

06 // HOW SHOULD IT BE REMEDIATED?
```

Example finding structure:

```text
FINDING
│
├── Description
├── Evidence
├── Attack Path
├── Technical Impact
├── MITRE ATT&CK Mapping
├── Detection
└── Remediation
```

---

# `// CERTIFICATIONS & TRAINING`

```text
┌─────────────────────────────────────────────────────┐
│ CERTIFICATION / TRAINING                 STATUS     │
├─────────────────────────────────────────────────────┤
│ HTB CJCA                                  COMPLETE   │
│ Hack The Box Academy                     ACTIVE     │
│ Active Directory Security                ACTIVE     │
│ Microsoft Sentinel                       ACTIVE     │
│ Detection Engineering                    ACTIVE     │
│ Penetration Testing                      ACTIVE     │
└─────────────────────────────────────────────────────┘
```

---

# `// CURRENT OBJECTIVES`

```text
[01] Build an enterprise-style Active Directory security lab

[02] Generate realistic attack telemetry

[03] Develop Microsoft Sentinel detections

[04] Improve KQL threat-hunting capability

[05] Deepen Active Directory attack knowledge

[06] Build repeatable penetration-testing methodology

[07] Document professional-quality security findings

[08] Develop security automation

[09] Expand the cybersecurity project portfolio

[10] Bridge offensive techniques with defensive detection
```

---

# `// OPERATING PRINCIPLES`

```text
01 // Understand the system before attacking it.

02 // Enumeration beats guessing.

03 // Every attack should create evidence.

04 // Never trust a single indicator.

05 // Correlate telemetry.

06 // Validate assumptions.

07 // Document commands and evidence.

08 // Explain impact, not just exploitation.

09 // Make the process repeatable.

10 // Hold the standard.
```

---

# `// GITHUB ACTIVITY`

<div align="center">

<img height="170" src="https://github-readme-stats.vercel.app/api?username=Dylans7j&show_icons=true&theme=transparent&hide_border=true" />

<img height="170" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Dylans7j&layout=compact&theme=transparent&hide_border=true" />

</div>

---

# `// CONNECT`

<div align="center">

[![GitHub](https://img.shields.io/badge/GitHub-Dylans7j-181717?style=for-the-badge&logo=github)](https://github.com/Dylans7j)

</div>

```text
OPERATOR ....... Dylan Senez
HANDLE ......... d4rkgunn3r
DISCIPLINE ..... Cybersecurity / Computer Science
FOCUS .......... SOC • Active Directory • Offensive Security
LOCATION ....... Michigan
```

---

<div align="center">

## `// END TRANSMISSION`

### `BUILD // ATTACK // DETECT // DOCUMENT // REPEAT`

</div>
