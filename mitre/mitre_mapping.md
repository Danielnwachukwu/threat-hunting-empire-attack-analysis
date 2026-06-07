# MITRE ATT&CK Mapping

| Activity Observed | MITRE Technique | Technique ID |
|------------------|-----------------|--------------|
| PowerShell Execution | PowerShell | T1059.001 |
| Invoke-PsExec Usage | Remote Services | T1021 |
| AMSI Bypass | Impair Defenses | T1562.001 |
| Service Installation (Updater) | Create or Modify System Process | T1543.003 |
| Registry Persistence | Registry Run Keys / Startup Items | T1547 |
| Network Connections from PowerShell | Application Layer Protocol | T1071 |
| Process Discovery (whoami) | System Owner/User Discovery | T1033 |

## Attack Flow

Initial Execution
→ PowerShell Empire Launch
→ Invoke-PsExec Execution
→ AMSI Bypass
→ Service Installation
→ Registry Persistence
→ Network Communication
