# DET-008 — Cron Persistence

## Objective
Detect new or modified persistence files under `/etc/cron.d`.
## Threat Scenario
An attacker establishes scheduled execution using system cron.
## Data Source
Wazuh FIM events for `/etc/cron.d`.
## Detection Logic
Rule 100130 derives from new-file rule 554; 100131 derives from modified-file rule 550. Both are level 12.
## Wazuh Rule
See rules `100130–100131` in [`local_rules.xml`](../detections/local_rules.xml).
## MITRE ATT&CK
T1053.003 — Cron.
## Safe Test Procedure
Create a uniquely named lab cron file whose only action is `logger`, confirm collection, then remove the file. Do not alter production jobs.
## Expected Result
Creation or modification selects the corresponding custom rule.
## Evidence
Status: **implemented**; successful alert evidence is not committed.
## Investigation Notes
Inspect file content, owner/mode, creator, command target, and related process activity.
## False Positives
Package installation, configuration management, and authorized scheduled tasks.
## Tuning Opportunities
Allowlist known package-managed filenames carefully and monitor content changes.
## Lessons Learned
Cleanup is part of a controlled persistence simulation.
