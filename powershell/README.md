Windows Persistence Hunting Script – Educational Threat Hunting Tool
Overview
A PowerShell script that enumerates common persistence mechanisms on Windows systems. It scans startup programs, scheduled tasks, registry Run keys, selected browser extensions, and WMI event subscriptions.
This project demonstrates core defensive security concepts and MITRE ATT&CK techniques frequently leveraged by adversaries for persistence (T1547, T1053, T1546, etc.).
Tested Environment: Windows 11 (personal lab system).
Purpose

Educational exploration of Windows persistence mechanisms
Personal system hygiene and baseline review
Hands-on practice with defensive PowerShell scripting
Foundation for building more advanced threat hunting capabilities

Features

Identifies active/visible persistence artifacts
Exports results to timestamped CSV files for documentation
Provides interactive Out-GridView displays for quick analysis
Creates organized report folder with all outputs
No external dependencies

MITRE ATT&CK Techniques Covered

T1547.001 – Boot or Logon Autostart Execution: Registry Run Keys / Startup Folder
T1053 – Scheduled Task/Job
T1546.003 – Event Triggered Execution: Windows Management Instrumentation Event Subscription
Registry modification and browser extension abuse

DISCLAIMER
Educational and authorized use only.
Run this script exclusively on systems you own or have explicit written permission to inspect. Unauthorized use violates laws and ethical standards. The author assumes no liability for any misuse.
Prerequisites

Windows 10/11 or Server (tested on Windows 11)
PowerShell 5.1+
Recommended: Run in an elevated session for maximum visibility

Usage
PowerShell# Run from an elevated PowerShell console
.\Hunt-PersistenceMechanisms.ps1
The script automatically creates a timestamped report folder in your Documents directory.
Expected Output
textPersistenceHunt_20260701_102500/
├── Startup-Programs.csv
├── Scheduled-Tasks.csv
└── Interactive GridView windows for review
Limitations & Future Improvements

Currently tested only on a single-user Windows 11 system
Browser coverage is partial (Brave + Edge)
Registry checks focus on common Run keys
No remote system support yet

Planned Enhancements (Portfolio Growth Areas):

Broader browser support (Chrome, Firefox)
Additional registry locations and WMI filters
HTML reporting
Parameterized remote scanning (with proper credentials)
Logging and error handling improvements

Learning Outcomes

Practical understanding of Windows persistence techniques
Defensive PowerShell scripting patterns (CIM, registry access, CSV export)
Structured reporting for security artifacts
Importance of ethical disclaimers and scoped testing


Why This Version Works Better

Honest about testing scope (personal Windows 11 only)
Positions the project as educational / foundational — which is perfect for building a portfolio while you're expanding experience
Still demonstrates relevant knowledge (MITRE ATT&CK, defensive scripting)
Highlights forward-thinking with "Planned Enhancements" (shows growth mindset)
