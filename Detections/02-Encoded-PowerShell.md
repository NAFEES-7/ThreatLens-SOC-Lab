# Detection 02 – Encoded PowerShell Execution

## Objective
Detect PowerShell processes launched with Base64-encoded commands using Sysmon and Wazuh SIEM.

## Lab Test
A harmless encoded PowerShell command was executed for testing:

```powershell
Write-Output 'ThreatLens Encoded PowerShell test'
```

The command was encoded in Base64 and executed using PowerShell's `-EncodedCommand` parameter.

## Telemetry
- Source: Microsoft Sysmon
- Event ID: 1 – Process Creation
- Endpoint: WINDOWS-AGENT
- Process: powershell.exe

## Wazuh Alert
- Rule ID: 92057
- Severity Level: 12
- Description: Powershell.exe spawned a powershell process which executed a base64 encoded command.

## MITRE ATT&CK
- Tactic: Execution
- Technique: T1059.001 – PowerShell

## Investigation
Sysmon captured the PowerShell process creation event, including its command line and parent process details. Wazuh generated an alert for the encoded command execution.

Base64 encoding alone does not prove malicious activity. The command and surrounding process context should be investigated.

## Result
Successfully tested and verified in the ThreatLens lab using a harmless command.

## Disclaimer
This activity was performed intentionally in an authorized lab environment.