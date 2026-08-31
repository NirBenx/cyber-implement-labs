# Project Context

## Purpose and evidence vocabulary

This is a cybersecurity implementation and detection-engineering portfolio, not an operational backup.

- **Verified by owner:** the owner explicitly reports observing expected telemetry; public evidence may be absent.
- **Repository-evidenced:** a sanitized artifact committed here supports the result.
- **Implemented:** logic is reported as deployed, but the final result is not demonstrated here.
- **Planned:** future work not yet deployed or validated.

Rule presence never proves alert generation. Keep the catalog and detection documents aligned with these definitions.

## Fixed architecture

FW01 routes VMnet8 WAN/NAT, VMnet10 USERS, VMnet20 SERVERS, VMnet30 MGMT, and VMnet40 DMZ. CLIENT01 is on USERS and DC01 is on SERVERS. Do not redesign addressing, routes, or policy intent without explicit approval.

SIEM01 is the physical Lenovo Ubuntu system running Wazuh 4.14.7 Manager, Indexer, and Dashboard as a Docker single-node deployment plus a host agent. Do not create a second SIEM.

## Safety boundaries

- Do not modify, restart, or reconfigure active services without approval.
- Do not scan external, corporate, or unauthorized networks; existing recon and beacon tests use localhost only.
- Never publish credentials, certificate material, keys, `.env` files, public/transient IPs, workplace data, or personal data.
- Before a commit: validate configuration, inspect the diff, scan staged files for secrets, and obtain owner approval.

## Initial audit limitations

On 2026-08-31 this repository contained only a one-line README. A separate readable LAB02 deployment tree confirmed Wazuh `4.14.7` image references and baseline manager FIM configuration. Standard `/var/ossec` and `/etc/audit` paths were unavailable, and Docker status required privileges that were not requested. Custom rule, CDB, Auditd, and DET-012 alert artifacts could not be independently extracted.
