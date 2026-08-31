# DET-006 — File Integrity Monitoring

## Objective
Detect and attribute changes to a protected configuration path.
## Threat Scenario
An attacker or administrator changes security-relevant configuration.
## Data Source
Wazuh Syscheck for `/etc/wazuh-lab/` with `check_all`, `whodata`, and `report_changes` enabled.
## Detection Logic
Syscheck reports creation/modification and file differences for `/etc/wazuh-lab/app.conf`.
## Wazuh Rule
Built-in FIM rules; endpoint configuration supplies the monitored path.
## MITRE ATT&CK
T1565.001 — Stored Data Manipulation (portfolio mapping).
## Safe Test Procedure
On the lab test file only, change `logging=normal` to `logging=verbose` and add `debug=true`; preserve or restore the desired final state.
## Expected Result
Threat Hunting shows events filterable by `syscheck.path`, including the controlled changes.
## Evidence
Status: **verified by owner**. No sanitized screenshot or event is committed.
## Investigation Notes
Review actor, timestamp, before/after content, hashes, permissions, and adjacent events.
## False Positives
Authorized deployments, package updates, and configuration management.
## Tuning Opportunities
Restrict paths, exclude volatile files, and baseline approved change windows.
## Lessons Learned
Whodata and report-changes materially improve investigation value over change-only alerts.
