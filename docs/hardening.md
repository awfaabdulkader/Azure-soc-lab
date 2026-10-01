# Linux hardening and remaining findings

[Back to overview](../README.md)

The report records a USG audit using the CIS Level 1 Server profile. Failed checks fell from **106 initially**, to **6 at an intermediate audit**, then **5 at the final reported audit**. The supplied screenshot named “AFTER CIS Level 1 → 6 FAIL” records the intermediate stage. This is improvement in failed-check counts, not proof of full CIS compliance.

| Layer | Applied control |
|---|---|
| Azure | Targeted NSG rules and source restrictions |
| Host firewall | UFW filtering |
| Administration | Key-based SSH, password/root restrictions, allowed-user control |
| Login protection | Fail2ban sshd jail and controlled ban test |
| Filesystem | Separate /tmp with nosuid, nodev, noexec options |
| Audit | Repeated USG audit and review of failed rule identifiers |

## Five residual findings reported

- `all_apparmor_profiles_in_enforce_complain_mode`
- `grub2_uefi_password`
- `nftables_ensure_default_deny_policy`
- `permissions_local_var_log`
- `file_permissions_sshd_drop_in_config`

These remain part of the project record. Further remediation should consider the Azure VM context and be validated with another audit.

[Hardening evidence](../screenshots/phase-02-hardening/README.md) · Source: final report §3.5.
