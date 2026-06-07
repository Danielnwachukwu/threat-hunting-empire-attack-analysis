## Investigation Screenshots

### 1. Splunk Data Ingestion Validation

![Data Ingestion](screenshots/01-Splunk-ThreatHunt-Data-Ingestion.png)

**Finding:**
Verified successful ingestion of Windows telemetry into Splunk. Data sources were validated to ensure all relevant security events were available for threat hunting and timeline reconstruction.

---

### 2. Event Frequency Analysis

![Event Frequency](screenshots/02-Event-Frequency-Analysis-Workstation6.png)

**Finding:**
Analyzed event frequency on the compromised workstation to identify abnormal activity patterns. High concentrations of process creation, PowerShell execution, and system modification events indicated suspicious behavior requiring deeper investigation.

---

### 3. Empire Attack Timeline Reconstruction

![Timeline Reconstruction](screenshots/03-Empire-Attack-Timeline-Reconstruction.png)

**Finding:**
Reconstructed the attacker timeline using correlated Windows events. This established the sequence of execution, persistence creation, network communication, and subsequent attacker actions across the host.

---

### 4. PowerShell Process Lineage Analysis

![Process Lineage](screenshots/04-Process-Lineage-PowerShell-Execution.png)

**Finding:**
Investigated parent-child process relationships to trace PowerShell execution back to its originating process. This revealed attacker-controlled PowerShell activity and provided context for subsequent malicious actions.

---

### 5. Invoke-PsExec Detection

![Invoke-PsExec Detection](screenshots/05-PowerShell-Empire-Invoke-PsExec-Detection.png)

**Finding:**
Detected evidence of PowerShell Empire's Invoke-PsExec functionality. The activity indicated lateral movement capabilities and demonstrated the attacker's attempt to execute commands remotely across systems.

---

### 6. PowerShell Script Block Logging Analysis

![Script Block Analysis](screenshots/06-PowerShell-ScriptBlock-Logging-Analysis.png)

**Finding:**
Reviewed PowerShell Script Block Logging events to identify executed commands and attacker tooling. Script contents provided visibility into malicious execution techniques and post-exploitation activity.

---

### 7. AMSI Bypass Detection

![AMSI Bypass](screenshots/07-AMSI-Bypass-ScriptBlock-Detection.png)

**Finding:**
Identified PowerShell commands associated with attempts to bypass the Anti-Malware Scan Interface (AMSI). This behavior demonstrated deliberate efforts to evade endpoint security controls and conceal malicious scripts.

---

### 8. Malicious Service Installation

![Service Installation](screenshots/08-Malicious-Service-Installation-Updater.png)

**Finding:**
Detected creation of a suspicious Windows service used to maintain attacker access. Service installation events indicated persistence mechanisms commonly leveraged by post-exploitation frameworks.

---

### 9. Registry Persistence Analysis

![Registry Persistence](screenshots/09-Registry-Persistence-Updater-Service.png)

**Finding:**
Investigated registry modifications linked to persistence. Analysis revealed configuration changes consistent with maintaining execution after system reboot and ensuring continued attacker access.

---

### 10. Persistence Correlation

![Persistence Correlation](screenshots/10-Persistence-And-PowerShell-Correlation.png)

**Finding:**
Correlated Sysmon Event IDs 1, 3, 12, 7045, and 4104 to link PowerShell execution, service installation, registry persistence, and network activity into a single attack timeline.

---

### 11. Suspicious PowerShell Network Connections

![Network Connections](screenshots/11-Suspicious-PowerShell-Network-Connection.png)

**Finding:**
Correlated PowerShell execution events with outbound network connections. The activity suggested command-and-control communication between the compromised host and attacker infrastructure.

---

## Incident Response Recommendations

Based on the investigation findings, the following actions are recommended:

1. Isolate affected hosts from the network to prevent further attacker activity.
2. Terminate malicious PowerShell sessions and associated processes.
3. Remove unauthorized services and registry persistence mechanisms.
4. Block identified command-and-control IP addresses and domains.
5. Reset credentials associated with compromised accounts.
6. Conduct enterprise-wide hunting for similar PowerShell Empire indicators.
7. Enable PowerShell Script Block Logging and AMSI protections across all systems.
8. Deploy detections for AMSI bypass attempts, malicious service creation, and suspicious PowerShell execution.
9. Review lateral movement activity and investigate potentially impacted hosts.
10. Update security monitoring rules based on discovered attacker techniques.

---

## Conclusion

This investigation successfully reconstructed a PowerShell Empire intrusion using Windows telemetry collected in Splunk. Through timeline analysis, process lineage investigation, PowerShell logging review, persistence detection, registry analysis, and network correlation, attacker behavior was identified and mapped to the MITRE ATT&CK framework. The findings demonstrate practical threat hunting methodology, event correlation techniques, and incident response decision-making using real-world telemetry.
