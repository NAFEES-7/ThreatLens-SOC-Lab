# ThreatLens – Multi-Host SOC Detection & Log Analysis Lab

## Project Overview
ThreatLens is a hands-on Security Operations Center (SOC) lab built using Wazuh SIEM, Sysmon, Windows 11, Ubuntu Server, and Kali Linux.

The project focuses on collecting endpoint telemetry, detecting suspicious activities, investigating security alerts, and mapping detections to the MITRE ATT&CK framework.

## Lab Architecture
- Wazuh Manager: Ubuntu Server
- SIEM: Wazuh 4.12.0
- Endpoint Monitoring: Windows Wazuh Agent
- System Telemetry: Microsoft Sysmon
- Additional Monitoring: Kali Linux Wazuh Agent

## Implemented Security Detections

### 1. Account Discovery
- Monitored Windows account discovery commands.
- Captured process execution using Sysmon Event ID 1.
- Verified Wazuh alert generation.
- MITRE ATT&CK: T1087 – Account Discovery.

### 2. Encoded PowerShell Execution
- Executed a harmless Base64-encoded PowerShell test command.
- Captured process creation telemetry using Sysmon.
- Verified Wazuh alert generation.
- MITRE ATT&CK: T1059.001 – PowerShell.

### 3. Registry Modification
- Created and modified a controlled Windows test registry value.
- Captured registry modification using Sysmon Event ID 13.
- Developed a custom Wazuh detection rule (100110).
- Verified the resulting security alert.

## Tools & Technologies
- Wazuh SIEM
- Sysmon
- Windows PowerShell
- Ubuntu Linux
- Kali Linux
- MITRE ATT&CK
- XML

## Project Status
Three controlled security detections have been implemented and successfully verified.

## Disclaimer
This project was developed for educational and authorized lab testing purposes only. All security tests were performed in a controlled environment.
