# Insider Threat Detection

Defensive security module focused on detecting insider threats in financial services environments.

## Overview
Practical detection engineering for anomalous user behavior using Windows Event Logs.

**Key Capability**: `Detect-LogonAnomalies.ps1` — identifies off-hours logons, unusual workstations, and failed logon spikes.

## Lab Testing (SANS SEC504 Windows 10)
**Setup & Simulation**:
- Created a dedicated test user (`InsiderTest`) with local admin rights for controlled testing.
- Enabled detailed logon auditing.
- Simulated insider threat activity by:
  - Temporarily adjusting system time to off-hours (03:xx AM)
  - Performing explicit credential logons (`Start-Process` with credentials)
  - Executing multiple failed logon attempts
  - Running commands under different contexts to simulate unusual workstations

**Results**:
The detection script successfully identified **anomalous logons**, flagging:
- Off-hours access (outside business hours 7 AM – 7 PM)
- Activity from non-standard workstations/processes
- Generated clear CSV reports with timestamps, user details, and reasoning for each alert.

All activities were performed safely in an isolated lab environment using synthetic data only.

![Test User Creation](../docs/create-test-user1.png)
![Simulation Commands](../docs/create-test-user2.png)
![Off-Hours Simulation](../docs/create-threat-simulation3.png)
![Detection Results](../docs/detect-threat-simulation3.png)

## Tools
- **PowerShell**: `Detect-LogonAnomalies.ps1` (v2.1)
  - Efficient event log querying
  - Structured CSV reporting
  - Execution logging

## MITRE ATT&CK Coverage
- T1078 — Valid Accounts
- T1110 — Brute Force
- T1119 — Automated Collection

## Ethical Disclaimer
**For authorized lab and educational use only.**  
Unauthorized deployment or use is prohibited.

---

*Part of the [infosec-portfolio](../..) — PowerShell + Python defensive tooling.*
