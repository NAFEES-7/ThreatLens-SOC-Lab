# ThreatLens – SOC Lab Architecture

## Architecture Diagram

```mermaid
flowchart TD
    A[Windows 11 Endpoint]
    B[Sysmon]
    C[Windows Wazuh Agent]
    D[Ubuntu Linux VM]
    E[Wazuh Manager]
    F[Wazuh Dashboard]
    G[Kali Linux]
    H[Kali Wazuh Agent]

    A --> B
    B --> C
    C -->|Security Events| E
    G --> H
    H -->|Endpoint Events| E
    D --> E
    E --> F
```

## Data Flow

1. Sysmon collects process creation and registry activity on Windows.
2. The Windows Wazuh Agent forwards collected events.
3. The Kali Linux agent provides additional endpoint telemetry.
4. Wazuh Manager analyzes events using built-in and custom rules.
5. The Wazuh Dashboard displays alerts for investigation.