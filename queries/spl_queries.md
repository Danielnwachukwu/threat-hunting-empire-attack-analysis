# SPL Queries Used

## Data Ingestion Validation

```spl
index=threathunt
| stats count by Hostname
```

Purpose:
Validate that telemetry is being successfully ingested into Splunk.

---

## Event Frequency Analysis

```spl
index=threathunt Hostname="WORKSTATION6.theshire.local"
| stats count by EventID
| sort - count
```

Purpose:
Identify the most common event types and suspicious activity.

---

## Attack Timeline Reconstruction

```spl
index=threathunt Hostname="WORKSTATION6.theshire.local"
(EventID=1 OR EventID=3)
| table EventTime EventID Image CommandLine SourceIp DestinationIp DestinationPort
| sort EventTime
```

Purpose:
Reconstruct attacker activity chronologically.

---

## Process Lineage Analysis

```spl
index=threathunt Hostname="WORKSTATION6.theshire.local" EventID=1
| table EventTime Image ParentImage CommandLine User
```

Purpose:
Identify suspicious parent-child process relationships.

---

## Invoke-PsExec Detection

```spl
index=threathunt Hostname="WORKSTATION6.theshire.local"
Invoke-PsExec
```

Purpose:
Detect PowerShell Empire remote execution activity.

---

## PowerShell Script Block Logging

```spl
index=threathunt Hostname="WORKSTATION6.theshire.local" EventID=4104
| table EventTime ScriptBlockText
```

Purpose:
Review PowerShell execution contents.

---

## AMSI Bypass Detection

```spl
index=threathunt Hostname="WORKSTATION6.theshire.local"
(EventID=4104)
```

Purpose:
Identify AMSI bypass activity within script blocks.

---

## Malicious Service Installation

```spl
index=threathunt EventID=7045
| table EventTime Hostname ServiceName Message
```

Purpose:
Detect service-based persistence.

---

## Registry Persistence Detection

```spl
index=threathunt EventID=12
```

Purpose:
Identify registry modifications associated with persistence.

---

## Persistence Correlation

```spl
index=threathunt Hostname="WORKSTATION6.theshire.local"
(EventID=1 OR EventID=3 OR EventID=12 OR EventID=7045 OR EventID=4104)
| table EventTime EventID Image CommandLine DestinationIp DestinationPort ServiceName TargetObject
| sort EventTime
```

Purpose:
Correlate attacker actions across multiple telemetry sources.

---

## Network Activity Analysis

```spl
index=threathunt Hostname="WORKSTATION6.theshire.local"
(EventID=3 OR EventID=1)
| table EventTime Image DestinationIp DestinationPort CommandLine
```

Purpose:
Investigate suspicious network communication.
