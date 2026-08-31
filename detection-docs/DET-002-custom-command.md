# DET-002 — Custom Suspicious Command Marker

## Objective
Validate the custom Wazuh rule path with a harmless synthetic marker.
## Threat Scenario
A controlled marker represents suspicious shell execution without running a harmful command.
## Data Source
Linux logging pipeline (`logger` / journald).
## Detection Logic
Rule 100100 matches `LAB02_SUSPICIOUS_COMMAND` and raises level 10.
## Wazuh Rule
See rule `100100` in the [sanitized reconstruction](../detections/local_rules.xml).
## MITRE ATT&CK
T1059 — Command and Scripting Interpreter.
## Safe Test Procedure
Run `logger "LAB02_SUSPICIOUS_COMMAND whoami"` on the authorized lab host.
## Expected Result
Threat Hunting shows rule 100100 and the marker text.
## Evidence
Status: **verified by owner**. No sanitized public artifact is committed.
## Investigation Notes
Confirm decoder/source fields and distinguish the marker from actual command execution.
## False Positives
Documentation, scripts, or tests that emit the exact marker.
## Tuning Opportunities
Limit the match to the expected log source or add structured fields.
## Lessons Learned
A harmless marker isolates ingestion and rule evaluation from attack-tool behavior.
