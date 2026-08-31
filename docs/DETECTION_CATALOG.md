# Detection Catalog

This is the authoritative status register. “Verified by owner” records an explicitly supplied observation; it does not imply public evidence is committed.

| ID | Rule(s) | Capability | Data source | ATT&CK | Status | Public evidence |
|---|---:|---|---|---|---|---|
| DET-001 | 5710 | SSH invalid user | journald / sshd | T1110 | Verified by owner | Pending |
| DET-002 | 100100 | Marker command | journald / logger | T1059 | Verified by owner | Pending |
| DET-003 | 100101 | Repeated marker correlation | Wazuh alerts | T1059 | Verified by owner | Pending |
| DET-004 | built-in | Command execution | Auditd `execve` | T1059 | Verified by owner | Pending |
| DET-005 | 100110–100111 | CDB-listed programs | Auditd + CDB | T1059 | Implemented | Pending |
| DET-006 | Syscheck | Protected file change | Wazuh FIM | T1565.001 | Verified by owner | Pending |
| DET-007 | 100120 | Effective root by non-root login | Auditd | T1548.003 | Verified by owner | Pending |
| DET-008 | 100130–100131 | Cron create/modify | Wazuh FIM | T1053.003 | Implemented | Pending |
| DET-009 | 100140–100141 | Account/group manipulation | Auditd | T1136.001, T1098.007 | Implemented; collision observed | Pending |
| DET-010 | 100150 | Nmap connection activity | Auditd | T1046 | Implemented | Pending |
| DET-011 | 100160–100161 | Repeated curl connections | Auditd + correlation | T1071.001 | Implemented | Pending |
| DET-012 | 100170–100180 | Multi-stage chain | Correlated alerts | Multiple | Implemented; final verification pending | Pending |

Promote a result to **repository-evidenced** only after adding and linking a sanitized artifact. DET-012 must not be described as successfully fired until evidence exists.
