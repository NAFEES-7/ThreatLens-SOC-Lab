# ThreatLens – Lab Setup Guide

## 1. Lab Overview

ThreatLens uses a multi-host environment to collect endpoint security events and analyze them through Wazuh SIEM.

## 2. Lab Components

| Component | Technology |
|---|---|
| SIEM Platform | Wazuh 4.12.0 |
| Manager Server | Ubuntu Linux VM |
| Windows Endpoint | Windows with Wazuh Agent |
| Endpoint Telemetry | Microsoft Sysmon |
| Additional Endpoint | Kali Linux with Wazuh Agent |
| Custom Detection | Wazuh XML Rules |

## 3. Architecture

1. Sysmon collects Windows process and registry activity.
2. The Windows Wazuh Agent forwards collected events to the Wazuh Manager.
3. The Kali Linux agent provides additional endpoint monitoring.
4. Wazuh analyzes incoming security events using built-in and custom rules.
5. Generated alerts are investigated through the Wazuh platform.

## 4. Implemented Monitoring

- Windows process creation monitoring – Sysmon Event ID 1.
- Registry value modification monitoring – Sysmon Event ID 13.
- Wazuh alert analysis and custom rule matching.
- Multi-host endpoint monitoring.

## 5. Custom Detection

Custom rule ID: `100110`

The rule detects registry value modifications involving the controlled `ThreatLensTest` registry key.

## 6. Validation

The following detections were tested and verified:

- Account Discovery – Wazuh Rule 92039.
- Encoded PowerShell – Wazuh Rule 92057.
- Registry Modification – Custom Wazuh Rule 100110.

## 7. Security Notes

All tests were performed in an isolated, authorized lab environment using harmless test commands and a dedicated registry test key.

Private IP addresses, credentials, tokens, and personal information should not be published in this repository.