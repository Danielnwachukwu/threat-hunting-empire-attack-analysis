# SPL Queries Used

## Data Ingestion Validation

```spl
index=threathunt
| stats count by Hostname
```

## Event Frequency Analysis

```spl
index=threathunt Hostname="WORKSTATION6.theshire.local"
| stats count by EventID
| sort - count
```

## Process and Network Correlation

```spl
index=threathunt Hostname="WORKSTATION6.theshire.local"
(EventID=1 OR EventID=3)
| table EventTime EventID Image CommandLine SourceIp DestinationIp DestinationPort
| sort EventTime
```

## AMSI Bypass Detection

```spl
index=threathunt Hostname="WORKSTATION6.theshire.local" EventID=4104
| table EventTime ScriptBlockText
```

## Malicious Service Installation

```spl
index=threathunt EventID=7045
| table EventTime Hostname ServiceName Message
```
