# LAB 01 — Enterprise Infrastructure

| Segment | VMware network | Subnet | Key systems |
|---|---|---|---|
| WAN | VMnet8 | VMware NAT | FW01 WAN |
| USERS | VMnet10 | `10.10.10.0/24` | gateway `.1`, CLIENT01 `.100` |
| SERVERS | VMnet20 | `10.10.20.0/24` | DC01 `.10` |
| MGMT | VMnet30 | `10.10.30.0/24` | management systems |
| DMZ | VMnet40 | `10.10.40.0/24` | WEB01 `.10` planned |

CLIENT01 uses FW01 as gateway and DC01 for DNS. Policy intent permits required AD/DNS traffic, restricts USERS-to-MGMT and USERS-to-DMZ, restricts DMZ-to-DC01, and controls Internet access through FortiGate NAT. This records design intent, not an exported policy audit.
