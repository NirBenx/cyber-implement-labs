# DET-001 — SSH Invalid User

## Objective
Identify SSH authentication attempts for nonexistent local users.
## Threat Scenario
An attacker enumerates accounts or attempts brute-force access.
## Data Source
Linux journald / `sshd`.
## Detection Logic
Wazuh built-in rule 5710 matches an SSH invalid-user event.
## Wazuh Rule
Built-in rule `5710`; no custom XML is required.
## MITRE ATT&CK
T1110 — Brute Force.
## Safe Test Procedure
From an explicitly authorized lab system, attempt SSH authentication once with a deliberately nonexistent test username. Avoid repeated attempts or exposed systems.
## Expected Result
Threat Hunting shows rule 5710 with the source SSH event.
## Evidence
Status: **verified by owner**. No sanitized public artifact is committed.
## Investigation Notes
Review source, target, volume, timing, related failures, and any later successful authentication.
## False Positives
Typographical errors, stale automation, and renamed accounts.
## Tuning Opportunities
Correlate repeated failures by source and target; exclude known scanners only after validation.
## Lessons Learned
Built-in rules can provide value without custom content, but raw-event review remains essential.
