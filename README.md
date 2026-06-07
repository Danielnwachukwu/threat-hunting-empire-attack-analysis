# Threat Hunting: PowerShell Empire Attack Analysis

## Project Overview

This project documents a threat hunting investigation conducted against Windows telemetry collected in Splunk.

The objective was to reconstruct attacker activity from raw logs, identify malicious behaviors, correlate security events, and map findings to the MITRE ATT&CK framework.

The investigation focuses on a PowerShell Empire intrusion involving:

- PowerShell execution
- Invoke-PsExec activity
- AMSI bypass attempts
- Malicious service installation
- Registry persistence
- Network communication
- Incident response recommendations

---

## Skills Demonstrated

- Threat Hunting
- Splunk SPL
- Log Analysis
- Windows Event Analysis
- Sysmon Investigation
- Timeline Reconstruction
- Incident Response
- MITRE ATT&CK Mapping
- Detection Engineering

---

## Tools Used

- Splunk
- Sysmon
- Windows Event Logs
- MITRE ATT&CK
- CyberDefenders Dataset

---

## Investigation Workflow

1. Data Ingestion Validation
2. Event Frequency Analysis
3. Timeline Reconstruction
4. Process Lineage Investigation
5. PowerShell Empire Detection
6. AMSI Bypass Detection
7. Persistence Analysis
8. Registry Investigation
9. Network Activity Correlation
10. Incident Response Recommendations

---

## Key Findings

### Initial Access / Execution

- Encoded PowerShell execution observed.
- Invoke-PsExec activity detected.

### Defense Evasion

- AMSI bypass identified.
- PowerShell logging bypass attempts observed.

### Persistence

- Malicious "Updater" service installed.
- Registry modifications created persistence mechanisms.

### Command and Control

- Suspicious PowerShell-generated network connections identified.

---

## MITRE ATT&CK Techniques

| Technique | Description |
|------------|------------|
| T1059.001 | PowerShell |
| T1021 | Remote Services |
| T1562.001 | Impair Defenses |
| T1543.003 | Windows Service |
| T1547 | Registry Persistence |
| T1071 | Application Layer Protocol |

---

## Screenshots

### Investigation Walkthrough

## Screenshots

### 1. Data Ingestion Validation

![Data Ingestion](screenshots/01-Splunk-ThreatHunt-Data-Ingestion.png)

---

### 2. Event Frequency Analysis

![Event Frequency](screenshots/02-Event-Frequency-Analysis-Workstation6.png)

---

### 3. Attack Timeline Reconstruction

![Timeline](screenshots/03-Empire-Attack-Timeline-Reconstruction.png)

---

### 4. Process Lineage Analysis

![Process Lineage](screenshots/04-Process-Lineage-PowerShell-Execution.png)

---

### 5. Invoke-PsExec Detection

![Invoke-PsExec](screenshots/05-PowerShell-Empire-Invoke-PsExec-Detection.png)

---

### 6. PowerShell Script Block Logging Analysis

![Script Block Logging](screenshots/06-PowerShell-ScriptBlock-Logging-Analysis.png)

---

### 7. AMSI Bypass Detection

![AMSI Bypass](screenshots/07-AMSI-Bypass-ScriptBlock-Detection.png)

---

### 8. Malicious Service Installation

![Service Installation](screenshots/08-Malicious-Service-Installation-Updater.png)

---

### 9. Registry Persistence

![Registry Persistence](screenshots/09-Registry-Persistence-Updater-Service.png)

---

### 10. Persistence Correlation

![Correlation](screenshots/10-Persistence-And-PowerShell-Correlation.png)

---

### 11. Suspicious PowerShell Network Activity

![Network Activity](screenshots/11-Suspicious-PowerShell-Network-Connection.png)

## Repository Structure

```text
screenshots/
queries/
mitre/
reports/
README.md
```

---

## Investigation Report

Detailed report available here:

```text
reports/investigation_report.md
```

---

## MITRE ATT&CK Mapping

Detailed ATT&CK mapping available here:

```text
mitre/mitre_mapping.md
```

---

## Author

Daniel Nwachukwu

Threat Hunting • SOC Analysis • Incident Response • Detection Engineering
