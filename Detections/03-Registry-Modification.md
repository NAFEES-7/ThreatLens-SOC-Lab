# Detection 03 – Windows Registry Modification

## Objective
Monitor and detect registry value modifications using Sysmon and Wazuh SIEM.

## Lab Test
A controlled test registry key was created under the current Windows user's registry:

```powershell
New-Item -Path 'HKCU:\Software\ThreatLensTest' -Force

New-ItemProperty -Path 'HKCU:\Software\ThreatLensTest' -Name 'TestValue' -Value 'ThreatLens controlled registry test' -PropertyType String -Force
```

The registry value was subsequently modified to generate another test event.

## Telemetry
- Source: Microsoft Sysmon
- Event ID: 13 – Registry Value Set
- Endpoint: WINDOWS-AGENT
- Registry Path: HKCU\Software\ThreatLensTest\TestValue

## Custom Wazuh Detection Rule
- Rule ID: 100110
- Severity Level: 5
- Description: ThreatLens: Registry value modification detected in test key
- Parent Rule: 61615

## MITRE ATT&CK
This detection demonstrates registry modification monitoring. No specific MITRE ATT&CK technique is assigned because this controlled test does not establish malicious behavior or persistence.

## Investigation
Sysmon captured the registry value modification through Event ID 13. The event was forwarded to Wazuh, where a custom rule matched the test registry path and generated an alert.

## Result
Successfully tested and verified. Wazuh generated custom alert 100110 for the controlled registry modification.

## Disclaimer
This was a harmless registry modification performed in an authorized lab environment. It was not a test of Windows Run-key persistence.
