# LAB 02 — Wazuh Deployment

SIEM01 hosts Wazuh 4.14.7 Manager, Indexer, and Dashboard in a single-node Docker deployment. A Wazuh 4.14.7 agent is reported active directly on Ubuntu, and the Dashboard is reported accessible through HTTPS.

The initial audit found an off-repository Compose tree whose three image declarations reference version 4.14.7. Its readable manager configuration contains baseline Syscheck monitoring. Certificate directories and credential-bearing files were not copied. Live Docker verification was unavailable without elevated access.

Supplied host state: Ubuntu 26.04.1 LTS x86_64; Docker 29.1.3; Compose 2.40.3; `vm.max_map_count=262144`.
