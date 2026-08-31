# DET-012 — Multi-stage Attack Correlation

## Objective
Correlate diverse behaviors into one high-confidence endpoint attack-chain alert.
## Threat Scenario
Reconnaissance is followed by elevation, account creation, cron persistence, and repeated web connections.
## Data Source
Stage rules derived from DET-010, DET-007, DET-009, DET-008, and DET-011.
## Detection Logic
Rules 100170–100174 add `lab02_attack_chain_stage`. Rule 100180 requires five group matches within 900 seconds, raises level 15, and suppresses repeats for 600 seconds.
## Wazuh Rule
See `100170–100180` in [`local_rules.xml`](../detections/local_rules.xml).
## MITRE ATT&CK
T1046, T1548.003, T1136.001, T1053.003, and T1071.001.
## Safe Test Procedure
Do not run as a single script until every stage is separately validated. On the authorized lab host only: scan `127.0.0.1`, run an approved sudo test, use a disposable account, create a harmless logger-only cron file, and send curl requests only to `127.0.0.1:8088`. Record timing and clean up temporary state.
## Expected Result
Each stage rule appears, followed by rule 100180 after five qualifying stage-group matches within 900 seconds.
## Evidence
Status: **implemented; final verification pending**. There is no local evidence proving rule 100180 fired.
## Investigation Notes
Verify all five parent alerts, ordering, endpoint identity, raw events, suppression state, and whether actions share a coherent actor/timeline.
## False Positives
Compressed lab exercises, administrative build activity, or automation could generate multiple stages.
## Tuning Opportunities
Consider ordered correlation, same-agent constraints, field matching, longer baselines, and environment-specific stage weighting.
## Lessons Learned
Stage normalization makes heterogeneous correlation legible, but frequency across a common group does not by itself prove ordered causality.
