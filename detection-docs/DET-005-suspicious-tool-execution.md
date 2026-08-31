# DET-005 — Suspicious Tool Execution

## Objective
Classify executable names through a maintainable CDB lookup.
## Threat Scenario
High-risk (`nc`, `ncat`, `socat`) or dual-use (`nmap`, `tcpdump`) tools execute on a monitored endpoint.
## Data Source
Auditd command events decoded under parent rule 80792 and CDB list `suspicious-programs`.
## Detection Logic
Rule 100110 raises level 12 for `red`; 100111 raises level 8 for `orange`.
## Wazuh Rule
See [`local_rules.xml`](../detections/local_rules.xml) and the [CDB list](../detections/lists/suspicious-programs).
## MITRE ATT&CK
T1059 — Command and Scripting Interpreter (supplied mapping).
## Safe Test Procedure
On the lab host, invoke an installed listed tool only with a harmless help/version option. Do not scan a target.
## Expected Result
The matching color classification selects the corresponding custom rule.
## Evidence
Status: **implemented**; successful alert evidence is not available in this repository.
## Investigation Notes
Review full arguments, parent, user, destination context, and whether usage was authorized.
## False Positives
Network troubleshooting, packet capture, administration, and security testing.
## Tuning Opportunities
Use path, user, host role, arguments, and approved maintenance windows.
## Lessons Learned
CDB classification separates frequently changing tool lists from rule logic.
