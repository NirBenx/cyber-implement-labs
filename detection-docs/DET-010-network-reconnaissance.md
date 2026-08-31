# DET-010 — Network Reconnaissance

## Objective
Detect Nmap network connection behavior through a dedicated Auditd key.
## Threat Scenario
An endpoint performs network service discovery.
## Data Source
Auditd `connect` syscall events for `/usr/bin/nmap`, key `network-recon`.
## Detection Logic
Rule 100150 maps the decoded audit key to a level-13 alert.
## Wazuh Rule
See [`lab02.rules`](../detections/auditd/lab02.rules) and rule `100150` in [`local_rules.xml`](../detections/local_rules.xml).
## MITRE ATT&CK
T1046 — Network Service Discovery.
## Safe Test Procedure
Run Nmap against `127.0.0.1` only. Never substitute an external or workplace target.
## Expected Result
An Auditd event with key `network-recon` selects rule 100150.
## Evidence
Status: **implemented**; successful alert evidence is not committed.
## Investigation Notes
Review target, ports, arguments, user, parent, frequency, and authorization.
## False Positives
Approved vulnerability assessment and local troubleshooting.
## Tuning Opportunities
Correlate targets, scan rate, host role, and change windows.
## Lessons Learned
Executable-plus-syscall telemetry is more behavior-focused than package presence.
