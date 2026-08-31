# INC-001 — Multi-stage Attack Scenario

## Status

**Test pending / no confirmed incident alert.** This is an investigation template for DET-012, not a claim that rule 100180 fired.

## Scenario

The planned controlled sequence combines localhost reconnaissance, approved sudo activity, a disposable local account, a logger-only cron file, and curl requests to a localhost HTTP server.

## Expected timeline

| Stage | Rule | ATT&CK | Evidence state |
|---|---:|---|---|
| Reconnaissance | 100170 | T1046 | Pending |
| Privilege escalation | 100171 | T1548.003 | Pending |
| Account creation | 100172 | T1136.001 | Pending |
| Cron persistence | 100173 | T1053.003 | Pending |
| Web beaconing | 100174 | T1071.001 | Pending |
| Final correlation | 100180 | Multiple | Pending |

## Analyst workflow

Validate raw events and each stage alert, establish endpoint/user identity, reconstruct timestamps, assess rule collisions, and confirm the five matches fall inside 900 seconds. Record cleanup of the account, cron entry, and local HTTP server.

## Conclusion

No conclusion is available until sanitized alert evidence is captured. Do not label this a detected incident or successful correlation test.
