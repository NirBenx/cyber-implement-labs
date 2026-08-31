# FortiGate Integration

Status: **planned**.

Configure FW01 to send selected Syslog categories to the existing SIEM01 after it has a predictable home address and policy permits the flow. Keep credentials and full FortiGate backups outside Git.

Validation must confirm transport, timestamp/time zone, device identity, parsing, and representative events. Later detections should correlate FortiGate context with CLIENT01 endpoint and DC01 identity telemetry.
