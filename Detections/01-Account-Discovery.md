# Detection 01 – Windows Account Discovery

## Objective
Detect Windows account discovery activity using Sysmon and Wazuh SIEM.

## Lab Test
The following commands were executed in Windows PowerShell:

```powershell
net.exe user
net.exe user guest
```

## Telemetry
- Source: Microsoft Sysmon
- Event ID: 1 – Process Creation
- Endpoint: WINDOWS-AGENT

## Wazuh Alert
- Rule ID: 92039
- Severity Level: 3
- Description: A net.exe account discovery command was initiated.

## MITRE ATT&CK
- Tactic: Discovery
- Technique: T1087 – Account Discovery

## Investigation
Sysmon captured the execution of net.exe and its command-line arguments. Wazuh generated an alert that can be investigated using endpoint and process details.

## Result
Successfully tested and verified in the ThreatLens lab.

## Disclaimer
This activity was performed intentionally in an authorized lab environment.