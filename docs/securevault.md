# SecureVault application and SOC integration

[Back to overview](../README.md)

SecureVault is the monitored business application in the final project. Angular provides the interface; Laravel provides the API, authorization, and audit behavior; MySQL stores structured data. Nginx serves the frontend and routes API requests to PHP-FPM on web01.

## Functional scope

| Feature | Security context |
|---|---|
| Authentication | Successful/failed login, blocking, logout |
| Documents | Upload, download, deletion, restoration, ownership |
| Sharing | Creation, expiry, revocation, usage, download quota |
| Administration | Account status and role changes |
| Audit | Actor, source, affected object, outcome, and chronology |

## Event collection

The report identifies application `security.log`, Laravel logs, and Nginx access/error logs as sources. The dedicated JSON security log includes event name, timestamp, severity, user identity where known, source IP, route/object context, and request ID. Passwords, session tokens, and document contents should not be logged.

The web01 Wazuh agent collects the configured sources and forwards them to soc01. File integrity monitoring adds visibility into changes to monitored application paths.

## Detection design

The report includes illustrative local rules `100500` (a failed login) and `100501` (same-source failure correlation, configured with frequency 5 and a 120-second window). These are report examples, not exported rules from the deployed host; confirm actual decoded fields, rule IDs, and correlation behavior with `wazuh-logtest` before reuse. Screenshots may show a different iteration of the rule set.

An authentication failure is an observation. Repeated failures warrant investigation; a brute-force label requires context. A FIM alert establishes that a monitored object changed, not that the change was unauthorized.

## Included material

[Application demo](../screenshots/securevault-demo/README.md) · [Deployment and monitoring](../screenshots/phase-06-securevault/README.md) · [UML](visuals.md)

The application was deployed in the documented lab, but its Laravel/Angular source, dependency manifests, migrations, and exact configuration exports are not in this upload package. No application version is inferred solely from the technology names.
