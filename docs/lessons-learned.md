# Lessons Learned

## Rule collisions are detection behavior

DET-009 exposed a significant lesson: `sudo useradd` matched both generic privilege-escalation rule 100120 and account-creation rule 100140. The event arrived, but 100120 won the evaluation path, so the intended final alert did not appear. Rule 100140 was made more specific and raised to level 13.

Rules must be tested as a system. Parent selection, specificity, level, grouping, and evaluation behavior can change which alert is visible even when the raw event exists.

## Configuration is not evidence

XML, Auditd rules, and CDB entries prove implementation intent—not successful alerting. Raw-event and alert evidence must be preserved separately.

## Portable addressing

Because SIEM01 moves between networks, a home-router DHCP reservation is preferable to a globally static host configuration.
