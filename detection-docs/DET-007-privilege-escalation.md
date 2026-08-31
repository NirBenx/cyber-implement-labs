# DET-007 — Privilege Escalation via sudo

## Objective
Detect commands with effective UID 0 when the login identity is non-root.
## Threat Scenario
A logged-in user elevates a process through sudo or equivalent control.
## Data Source
Auditd execution events under Wazuh parent rule 80792.
## Detection Logic
Rule 100120 matches `audit.euid=0` while excluding root/unset login `auid` values.
## Wazuh Rule
See rule `100120` in [`local_rules.xml`](../detections/local_rules.xml).
## MITRE ATT&CK
T1548.003 — Sudo and Sudo Caching.
## Safe Test Procedure
Run `sudo id` on the authorized lab host using the owner’s normal approved workflow.
## Expected Result
Rule 100120 identifies the non-root login identity and root effective identity.
## Evidence
Status: **verified by owner**. Public evidence is pending.
## Investigation Notes
Review `auid`, `uid`, `euid`, command, parent, sudo authentication, and surrounding activity.
## False Positives
Routine administration, patching, and authorized automation.
## Tuning Opportunities
Baseline approved commands/users while retaining visibility into anomalous sequences.
## Lessons Learned
Identity transition is stronger context than matching the string `sudo`.
