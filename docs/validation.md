# Validation and interpretation

[Back to overview](../README.md)

| Scenario | Documented observation | What it does not establish |
|---|---|---|
| Suricata HTTP test | SID 2100498 in source events and Wazuh investigation | Successful exploitation or complete VNet traffic coverage |
| Filebeat transport | TLS connection to Wazuh Indexer | Continuous availability or retention guarantees |
| Sysmon network event | Port 5985 plus process/network context indexed | Malicious WinRM use from port number alone |
| Failed login | Application security event and matching detection evidence | Compromise from a single failure |
| Repeated login failures | Correlation evidence in supplied lab screenshots | Attacker attribution or successful account access |
| File integrity monitoring | Changes to monitored files detected | Malicious intent without file/user context |
| Nmap / SQLmap tests | Controlled testing captures supplied | Confirmed exploitable vulnerabilities |

## MITRE ATT&CK interpretation

The following conditional mappings are reproduced from the report's analysis (§3.10), rather than presented as independently confirmed incidents.

| Technique | Required supporting context |
|---|---|
| T1110 · Brute Force | Systematic repeated authentication attempts |
| T1078 · Valid Accounts | Abnormal use of a valid authenticated account |
| T1190 · Exploit Public-Facing Application | Evidence of exploitation, not just an HTTP error |
| T1046 · Network Service Scanning | Connections consistent with service discovery |
| T1098 · Account Manipulation | Unauthorized or unexpected account/role changes |
| T1005 · Data from Local System | Collection behavior supported by volume and context |

Keep **observed**, **suspected**, and **not proven** separate in investigation notes. Correlate timestamps, agent, source, event fields, and process/request identifiers before concluding.

## Evidence limits

The report and supplied captures are the source of these results. This repository update did not run a new Azure deployment or repeat the security tests. Charts are supplied illustrations of the lab: no machine-readable event dataset was provided to recalculate their figures.
