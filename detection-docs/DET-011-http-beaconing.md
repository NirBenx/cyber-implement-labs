# DET-011 — HTTP Beaconing / C2-like Behavior

## Objective
Detect repeated curl HTTP connection behavior rather than alerting on every curl execution.
## Threat Scenario
A process makes periodic web connections resembling application-layer command-and-control traffic.
## Data Source
Auditd `connect` events for `/usr/bin/curl`, key `lab02-web-beacon`.
## Detection Logic
Rule 100160 creates a level-5 candidate. Rule 100161 requires five candidates within 60 seconds, raises level 13, and ignores repeats for 120 seconds.
## Wazuh Rule
See [`lab02.rules`](../detections/auditd/lab02.rules) and rules `100160–100161` in [`local_rules.xml`](../detections/local_rules.xml).
## MITRE ATT&CK
T1071.001 — Web Protocols.
## Safe Test Procedure
Bind a Python HTTP server to `127.0.0.1:8088` and issue five local curl requests within 60 seconds. Stop the test server afterward. Never use an external target.
## Expected Result
Candidates appear under 100160 and the threshold produces 100161.
## Evidence
Status: **implemented**; successful alert evidence is not committed.
## Investigation Notes
Review cadence, destination, process ancestry, arguments, user, and related persistence.
## False Positives
Health checks, automation, API polling, and package scripts.
## Tuning Opportunities
Add cadence, destination reputation, parent-process, and endpoint-role context.
## Lessons Learned
Behavioral correlation reduces noise compared with treating all curl usage as malicious.
