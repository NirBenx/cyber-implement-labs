# Lab Overview

## LAB 01 — Enterprise infrastructure

VMware Workstation hosts FW01, DC01, and CLIENT01 across dedicated WAN, USERS, SERVERS, MGMT, and DMZ networks. FortiGate is the routing and enforcement point. DC01 provides Active Directory and DNS; CLIENT01 represents a domain workstation. WEB01 is planned.

## LAB 02 — SOC and detection engineering

SIEM01 is a Lenovo V14-IIL with an Intel Core i5-1035G1, eight logical CPUs, approximately 7.1 GiB usable RAM, 4 GiB swap, and NVMe storage. Supplied state identifies Ubuntu 26.04.1 LTS, Docker 29.1.3, Compose 2.40.3, `vm.max_map_count=262144`, and Wazuh 4.14.7.

Linux telemetry includes journald/sshd, Auditd, and Wazuh Syscheck. Custom content demonstrates CDB lookups, frequency correlation, ATT&CK mapping, and multi-stage correlation design.
