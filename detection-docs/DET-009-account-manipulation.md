# DET-009 — Account Manipulation

## Objective
Detect local account creation and local account/group changes.
## Threat Scenario
An attacker creates an account or changes group membership after elevation.
## Data Source
Auditd execution events under parent rule 80792.
## Detection Logic
Rule 100140 matches `useradd`/`adduser`; rule 100141 matches `usermod`. Both are level 13.
## Wazuh Rule
See `100140–100141` in [`local_rules.xml`](../detections/local_rules.xml).
## MITRE ATT&CK
T1136.001 — Local Account; T1098.007 — Additional Local or Domain Groups.
## Safe Test Procedure
Use a disposable lab-only account with explicit approval, record identifiers, and remove it after validation. Avoid system or real user accounts.
## Expected Result
The specific account rule, not only generic elevation rule 100120, becomes the final alert.
## Evidence
Status: **implemented**. The owner confirmed event ingestion and reported the rule-collision behavior; final public alert evidence is pending.
## Investigation Notes
Review command arguments, sudo/Auditd identity, `/etc/passwd` and group changes, login activity, and persistence.
## False Positives
Authorized provisioning, support work, package-created service accounts, and automation.
## Tuning Opportunities
Differentiate interactive users from system accounts and approved provisioning parents.
## Lessons Learned
Initially, generic rule 100120 won for `sudo useradd`. Increasing 100140 specificity and severity to level 13 addressed the evaluation collision. Test the complete ruleset, not rules in isolation.
