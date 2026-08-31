# DET-003 — Repeated Suspicious Command Correlation

## Objective
Escalate repeated suspicious markers rather than treating each event independently.
## Threat Scenario
Repeated command-like activity occurs within a short interval.
## Data Source
Alerts matching rule 100100.
## Detection Logic
Rule 100101 requires five matches of 100100 in 60 seconds, raises level 12, and ignores repeats for 120 seconds.
## Wazuh Rule
See `100101` in [`local_rules.xml`](../detections/local_rules.xml).
## MITRE ATT&CK
T1059 — Command and Scripting Interpreter.
## Safe Test Procedure
Emit the DET-002 marker five times within 60 seconds on the lab host; record timestamps.
## Expected Result
One correlated rule 100101 alert follows the fifth qualifying event.
## Evidence
Status: **verified by owner**. Public evidence is pending.
## Investigation Notes
Confirm all five parents, host identity, ordering, and suppression window.
## False Positives
Automated health checks or repeated test scripts using the marker.
## Tuning Opportunities
Adjust frequency/timeframe from observed baselines and group by endpoint if required.
## Lessons Learned
Correlation thresholds and suppression must be documented to make testing repeatable.
