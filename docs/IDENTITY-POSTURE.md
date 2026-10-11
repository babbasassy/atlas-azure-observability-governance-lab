# Identity and posture assessment

Read-only observations on 11 October 2026. Existing tenant objects were preserved.

| Area | Observation | Interpretation |
|---|---|---|
| License | Microsoft Entra ID Free | Paid P1/P2 controls were not assumed available |
| Security Defaults | Portal stated the organization is protected by Security Defaults | Existing baseline enabled; no change was needed |
| Identity inventory | 5 users, 3 groups, 0 applications, 0 devices in the overview | Point-in-time inventory, not a complete entitlement review |
| Current administrator | Global Administrator shown | Broad standing privilege; assess role separation before production use |
| Sign-in logs | Interactive events accessible, including successful portal/security-center sign-ins | Portal investigation available on this tenant |
| Selected sign-in | Basic info: single-factor requirement, with MFA requirement satisfied by claim in token; authentication detail: previously satisfied first factor | Existing token claims were reused; this record is not evidence of a new MFA challenge |
| Conditional Access | Selected rows showed Not applied | Do not interpret this as Security Defaults being off |
| Entra diagnostics | No diagnostic settings defined | No Entra-to-workspace export is claimed; AzureActivity collection is a separate source |
| Defender for Cloud | Unregistered subscription, limited visibility, 0 assessed resources, secure score N/A | Insufficient evidence for a posture assessment or a compliance score |

No roles, authentication methods, security policies, identities or licenses were modified. No secrets or credentials were created. The account's broad administrator role was used for the authorized lab only; this is not a least-privilege deployment demonstration.

## Follow-up design

For a future production environment, separate daily administration from emergency administration, review role assignments and authentication-method migration status, and validate log retention/export licensing before enabling continuous export. The portal displayed an authentication-method migration notice, but this lab did not investigate whether it reflects an outstanding configuration issue.

Defender for Cloud's free foundational posture features exist, but the observed registration/visibility state prevented validating recommendations. No paid Defender CSPM upgrade was enabled to get around this limitation.

## Sources

- [Security Defaults](https://learn.microsoft.com/en-us/entra/fundamentals/security-defaults)
- [Foundational and paid CSPM capabilities](https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-cloud-security-posture-management)
- [Sign-in log activity details](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-in-log-activity-details)
