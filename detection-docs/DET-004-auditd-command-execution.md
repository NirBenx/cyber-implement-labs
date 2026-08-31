# DET-004 — Linux Command Execution with Auditd

## Objective
Capture process execution with attribution fields suitable for hunting and downstream rules.
## Threat Scenario
An analyst investigates commands executed by a user or elevated process.
## Data Source
Auditd `execve` events from `/var/log/audit/audit.log`, key `audit-wazuh-c`.
## Detection Logic
Wazuh decodes Auditd events and exposes command, executable, login/effective identities, working directory, and key.
## Wazuh Rule
Built-in Auditd processing; a reconstructed collection rule is in [`lab02.rules`](../detections/auditd/lab02.rules).
## MITRE ATT&CK
T1059 — Command and Scripting Interpreter.
## Safe Test Procedure
Run benign `whoami` and `id` commands on the authorized lab host.
## Expected Result
Threat Hunting exposes `data.audit.command`, `exe`, `auid`, `uid`, `cwd`, and `key` as applicable.
## Evidence
Status: **verified by owner**. No public event export is committed.
## Investigation Notes
Correlate login identity, effective identity, parent context, working directory, and command line.
## False Positives
Normal administration, package tasks, monitoring, and automation.
## Tuning Opportunities
Use focused keys and executable rules; avoid alerting on every execution at high severity.
## Lessons Learned
Rich identity fields make Auditd more useful than command-name matching alone.
