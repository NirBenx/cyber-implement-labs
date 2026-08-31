# Network Architecture

```mermaid
flowchart TB
  NAT[VMware NAT / VMnet8] --- WAN[FW01 WAN]
  WAN --- FW[FortiGate routing and policy]
  FW --- U[VMnet10 USERS<br/>10.10.10.0/24]
  FW --- S[VMnet20 SERVERS<br/>10.10.20.0/24]
  FW --- M[VMnet30 MGMT<br/>10.10.30.0/24]
  FW --- D[VMnet40 DMZ<br/>10.10.40.0/24]
  U --- C[CLIENT01<br/>10.10.10.100]
  S --- DC[DC01 / DNS<br/>10.10.20.10]
  D --- W[WEB01<br/>10.10.40.10 planned]
```

CLIENT01 uses `10.10.10.1` as gateway and DC01 as DNS. Required AD/DNS flows are allowed; USERS-to-MGMT, USERS-to-DMZ, and DMZ-to-DC01 are restricted by intent. Internet access is controlled through FW01/NAT, with no unnecessary inbound exposure.
