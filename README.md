# Shadow-Trace

## Objective
Conduct a forensic investigation on a Windows system to trace the activities of an attacker who moved laterally within a network. The goal was to identify the initial access vector, lateral movement techniques, and persistence mechanisms deployed.

### Skills Learned
- Windows event log analysis (Security, System, Application)
- Lateral movement detection (Pass-the-Hash, RDP abuse)
- Persistence mechanism identification
- MITRE ATT&CK framework mapping
- Forensic artifact correlation

### Tools Used
- Windows Event Viewer and PowerShell log analysis
- Sysmon (Event IDs 1, 3, 7, 11, 13)
- MITRE ATT&CK Navigator
- Timeline Explorer

## Steps
Initial investigation focused on Windows Security Event logs, specifically Event IDs 4624 (logon) and 4648 (explicit credential use) to identify lateral movement. Sysmon logs were analyzed to detect suspicious process creation and network connections. Persistence mechanisms were identified through scheduled task and registry run key inspection. Each technique was mapped to its corresponding MITRE ATT&CK tactic and technique ID to produce a structured threat report.

*Ref 1: Event ID 4624 log entries showing lateral movement via RDP*
*Ref 2: MITRE ATT&CK mapping of identified techniques*
