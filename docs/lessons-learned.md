# Troubleshooting and lessons learned

[Back to overview](../README.md)

| Problem recorded in report | Diagnosis and resolution |
|---|---|
| Root partition full | Temporary vd_updater cache near 16 GB; targeted cleanup and before/after checks |
| SSH private key rejected on Windows | Local PEM ACLs too permissive; restrict file access and retest |
| Suricata has no rules | Missing rules file; update rules and validate the configuration |
| Filebeat authentication fails after rotation | Indexer secret and Filebeat keystore no longer match; synchronize and retest |
| Event difficult to locate | Narrow searches by time, agent, group, and relevant fields |
| web01 agent not communicating | Check service logs, Azure IP flow/NSGs, and host firewall |
| Sysmon event ambiguous | Read address, port, process, GUID, and chronology together |

The recurring method is to isolate each dependency and verify its output before changing the next component. A running service is not sufficient evidence that events are collected, decoded, indexed, and searchable.

## Suggested future work

Infrastructure as code; sanitized configuration exports; automated validation fixtures; backup and restore exercises; retention and capacity planning; stronger separation of central SOC services; managed secret storage. These are proposed improvements, not completed deliverables.
