# Multi-stage Correlation Design

```mermaid
flowchart LR
  R[100170<br/>Recon / T1046] --> G[lab02_attack_chain_stage]
  P[100171<br/>Sudo / T1548.003] --> G
  A[100172<br/>Account / T1136.001] --> G
  C[100173<br/>Cron / T1053.003] --> G
  B[100174<br/>Beacon / T1071.001] --> G
  G -->|5 matches / 900 s| X[100180<br/>Level 15]
```

Rule 100180 is designed to correlate five stage-group matches within 900 seconds and suppress repeats for 600 seconds. This is an implementation design; successful final firing remains unverified.
