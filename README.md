# Threat Hunting: PowerShell Empire Attack Analysis

## Project Overview

This project documents a threat hunting investigation conducted against Windows telemetry collected and analyzed in Splunk.

The objective was to reconstruct attacker activity from raw logs, identify malicious behaviors, correlate security events, build an attack timeline, and map findings to the MITRE ATT&CK framework.

The investigation focuses on a simulated PowerShell Empire intrusion involving:

* PowerShell execution
* Invoke-PsExec activity
* AMSI bypass attempts
* Malicious service installation
* Registry persistence
* Command and Control (C2) communication
* Incident response recommendations

This project demonstrates practical threat hunting methodologies used by SOC analysts and incident responders when investigating post-compromise activity within enterprise environments.

---

## Skills Demonstrated

* Threat Hunting
* Splunk SPL
* Windows Event Analysis
* Sysmon Analysis
* Timeline Reconstruction
* Process Lineage Investigation
* MITRE ATT&CK Mapping
* Detection Engineering
* Incident Response
* Security Event Correlation

---

## Tools Used

* Splunk
* Sysmon
* Windows Event Logs
* MITRE ATT&CK Framework
* CyberDefenders Dataset

---

## Investigation Workflow

The investigation followed a structured threat hunting process:

1. Validate data ingestion into Splunk
2. Identify abnormal event frequencies
3. Reconstruct attacker timeline
4. Investigate PowerShell process lineage
5. Detect PowerShell Empire execution
6. Identify AMSI bypass activity
7. Detect malicious service installation
8. Investigate registry persistence
9. Correlate network communication
10. Perform ATT&CK mapping
11. Develop incident response recommendations

---

## Key Findings

### Initial Access / Execution

* Encoded PowerShell execution detected.
* PowerShell Empire activity observed.
* Invoke-PsExec usage identified.

### Defense Evasion

* AMSI bypass attempts detected.
* PowerShell logging evasion techniques observed.

### Persistence

* Malicious "Updater" service installed.
* Registry modifications established persistence.

### Command and Control

* Suspicious outbound PowerShell network connections identified.

### Impact

* Attacker achieved code execution.
* Persistence mechanisms were established.
* Network communication with external infrastructure was observed.

---

## MITRE ATT&CK Techniques

| Technique ID | Technique                                        |
| ------------ | ------------------------------------------------ |
| T1059.001    | PowerShell                                       |
| T1021        | Remote Services                                  |
| T1562.001    | Impair Defenses                                  |
| T1543.003    | Create or Modify System Process: Windows Service |
| T1547        | Boot or Logon Autostart Execution                |
| T1071        | Application Layer Protocol                       |

---

# Investigation Screenshots

## 1. Splunk Data Ingestion Validation

![Data Ingestion](screenshots/01-Splunk-ThreatHunt-Data-Ingestion.png)

### Finding

Verified successful ingestion of Windows telemetry into Splunk. Data sources were validated to ensure all relevant security events were available for threat hunting and timeline reconstruction.

---

## 2. Event Frequency Analysis

![Event Frequency](screenshots/02-Event-Frequency-Analysis-Workstation6.png)

### Finding

Analyzed event frequency on the compromised workstation to identify abnormal activity patterns. High concentrations of PowerShell execution and process creation events indicated suspicious activity requiring deeper investigation.

---

## 3. Empire Attack Timeline Reconstruction

![Timeline Reconstruction](screenshots/03-Empire-Attack-Timeline-Reconstruction.png)

### Finding

Reconstructed the attack timeline using correlated Windows events. This revealed the sequence of attacker actions from execution through persistence and command-and-control communication.

---

## 4. PowerShell Process Lineage Analysis

![Process Lineage](screenshots/04-Process-Lineage-PowerShell-Execution.png)

### Finding

Investigated parent-child process relationships to trace PowerShell execution back to its originating process. This established execution context and attacker activity flow.

---

## 5. Invoke-PsExec Detection

![Invoke-PsExec Detection](screenshots/05-PowerShell-Empire-Invoke-PsExec-Detection.png)

### Finding

Detected evidence of Invoke-PsExec usage associated with PowerShell Empire. The activity suggested attempted lateral movement and remote command execution capabilities.

---

## 6. PowerShell Script Block Logging Analysis

![Script Block Analysis](screenshots/06-PowerShell-ScriptBlock-Logging-Analysis.png)

### Finding

Reviewed PowerShell Script Block Logging events to identify executed commands and attacker tooling. The logs provided direct visibility into post-exploitation behavior.

---

## 7. AMSI Bypass Detection

![AMSI Bypass](screenshots/07-AMSI-Bypass-ScriptBlock-Detection.png)

### Finding

Identified PowerShell activity associated with AMSI bypass attempts. The behavior demonstrated efforts to evade endpoint security controls and avoid malware detection.

---

## 8. Malicious Service Installation

![Service Installation](screenshots/08-Malicious-Service-Installation-Updater.png)

### Finding

Detected installation of a suspicious Windows service named "Updater." Service creation events indicated attacker efforts to establish persistence.

---

## 9. Registry Persistence Analysis

![Registry Persistence](screenshots/09-Registry-Persistence-Updater-Service.png)

### Finding

Observed registry modifications associated with persistence mechanisms. The changes ensured malicious execution would survive system reboots.

---

## 10. Persistence Correlation

![Persistence Correlation](screenshots/10-Persistence-And-PowerShell-Correlation.png)

### Finding

Correlated Sysmon Event IDs 1, 3, 12, Windows Event ID 7045, and PowerShell Event ID 4104 to establish a complete attack chain linking execution, persistence, and network activity.

---

## 11. Suspicious PowerShell Network Connections

![Network Connections](screenshots/11-Suspicious-PowerShell-Network-Connection.png)

### Finding

Correlated PowerShell execution events with outbound network connections. The activity suggested command-and-control communication between the compromised host and attacker-controlled infrastructure.

---

# Incident Response Recommendations

Following identification of malicious activity, the following response actions are recommended:

### Containment

* Isolate affected hosts from the network.
* Block identified command-and-control IP addresses.
* Disable compromised user accounts.

### Eradication

* Remove malicious services.
* Remove registry persistence mechanisms.
* Terminate malicious PowerShell processes.
* Delete attacker-created artifacts.

### Recovery

* Reset affected credentials.
* Rebuild compromised hosts if necessary.
* Validate system integrity before returning systems to production.

### Lessons Learned

* Enable PowerShell Script Block Logging enterprise-wide.
* Ensure AMSI protections remain enabled.
* Monitor for service creation events (7045).
* Deploy detections for PowerShell Empire TTPs.
* Conduct regular threat hunting exercises using Sysmon telemetry.

---

## Repository Structure

```text
screenshots/
├── 01-Splunk-ThreatHunt-Data-Ingestion.png
├── 02-Event-Frequency-Analysis-Workstation6.png
├── 03-Empire-Attack-Timeline-Reconstruction.png
├── 04-Process-Lineage-PowerShell-Execution.png
├── 05-PowerShell-Empire-Invoke-PsExec-Detection.png
├── 06-PowerShell-ScriptBlock-Logging-Analysis.png
├── 07-AMSI-Bypass-ScriptBlock-Detection.png
├── 08-Malicious-Service-Installation-Updater.png
├── 09-Registry-Persistence-Updater-Service.png
├── 10-Persistence-And-PowerShell-Correlation.png
└── 11-Suspicious-PowerShell-Network-Connection.png

queries/
├── spl_queries.md

mitre/
├── mitre_mapping.md

reports/
├── investigation_report.md

README.md
```

---

## Additional Documentation

### Investigation Report

Detailed investigation report:

```text
reports/investigation_report.md
```

### MITRE ATT&CK Mapping

Detailed ATT&CK mapping:

```text
mitre/mitre_mapping.md
```

### SPL Queries

Detection and hunting queries:

```text
queries/spl_queries.md
```

---

## Conclusion

This investigation successfully reconstructed a PowerShell Empire intrusion using Windows telemetry collected in Splunk.

Through timeline analysis, process lineage investigation, PowerShell logging review, persistence detection, registry analysis, and network correlation, attacker behavior was identified and mapped to the MITRE ATT&CK framework.

The project demonstrates practical threat hunting, log analysis, event correlation, detection engineering, and incident response techniques used in modern Security Operations Centers (SOC).

---

## Author

**Daniel Nwachukwu**

Threat Hunting • SOC Analysis • Incident Response • Detection Engineering
