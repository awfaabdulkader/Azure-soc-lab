# Implementation walkthrough

[Back to overview](../README.md)

This is a walkthrough of the completed lab based on the final report, not a one-command installation guide. Exact server exports and application source were not supplied.

| Phase | Implementation | Validation checkpoint |
|---|---|---|
| 1 · Infrastructure | Azure resource group, VNet, VM deployment, central Wazuh services | soc01 services running and Dashboard available |
| 2 · Hardening | Restricted NSGs, UFW, SSH keys, Fail2ban, secure /tmp, USG CIS audit | Audit failures 106 → 6 → 5; controlled SSH checks |
| 3 · Suricata | Interface and HOME_NET configuration, rule loading, EVE JSON collection | Controlled SID 2100498 event in source log and Wazuh |
| 4 · SIEM | Filebeat transport, local rule testing, timeline and source dashboards | Indexer connectivity and searchable indexed alerts |
| 5 · Windows | win01 agent enrollment and Sysmon channel monitoring | Process and network events in Wazuh |
| 6 · SecureVault | Nginx/PHP-FPM/MySQL, application deployment, HTTPS and agent collection | Application events, web logs, and FIM evidence |

## Evidence sequence

1. Identify the authorized action or generated test traffic.
2. Find its source log and timestamp.
3. Verify collection by the relevant Wazuh component.
4. Inspect the decoder/rule result and key event fields.
5. Find the indexed event and confirm the same context in the Dashboard.

For historical implementation commands, see the [final report](../reports/PFA-SOC-Azure-SecureVault-2026.pdf). Adapt paths and review commands before reuse: the repository does not provide a verified deployment bundle.

[Browse evidence by phase](../screenshots/README.md).
