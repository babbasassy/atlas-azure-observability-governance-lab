# ATLAS Azure Observability and Governance Lab

A practical Azure Free Trial lab covering cost guardrails, control-plane log collection, ingestion validation and an evidence-based review of free identity/security capabilities. Built in North Europe on 10–11 October 2026.

## Verified outcomes

- Created a NOK 20 monthly budget, with actual-cost notification at 25% and forecast notification at 50%.
- Set and reopened a 0.100 GB daily ingestion cap to verify it persisted.
- Exported Administrative, Security and Policy activity logs to a dedicated Log Analytics workspace.
- Generated an authorized tag change and found its successful write in AzureActivity.
- Measured 7 lab-group events totaling 56,417 bytes with zero billable rows in that query scope.
- Confirmed Microsoft Entra ID Free, Security Defaults already enabled, available interactive sign-in logs and the existing Global Administrator role. No identity settings were changed.
- Recorded Defender for Cloud's actual limitation: subscription shown as Unregistered with limited visibility, 0 assessed resources and secure score N/A. This does **not** mean the environment is secure.

The companion [SOC detection engineering lab](https://github.com/babbasassy/atlas-soc-detection-engineering-lab) uses the same disposable logging infrastructure for KQL tests and incidents. This repository focuses on collection, costs and governance; the shared workspace is counted once.

## Cost controls are different mechanisms

| Mechanism | Purpose | Limitation |
|---|---|---|
| Azure Free Trial spending protection | Boundary for eligible trial-credit consumption | Excluded purchases must still be avoided |
| NOK 20 monthly budget | Early operational warning | Sends notifications; does not stop spending |
| 100 MB workspace daily cap | Reduce unexpected ingestion | May overshoot and is not a financial cap |
| Narrow data sources and no compute | Keep the actual workload small | Must be checked after configuration changes |
| Explicit cleanup | Stop ongoing collection and remove disposable resources | Must be verified, not assumed |

The lab was limited to existing trial credit and zero personal-money spend. No subscription upgrade, spending-limit removal, payment-card change or paid third-party purchase was performed.

## Files

- [Cost model and trial boundaries](docs/COSTS.md)
- [Identity and security baseline](docs/IDENTITY-POSTURE.md)
- [Collection validation](docs/VALIDATION.md)
- [Cleanup record](CLEANUP.md)
- `queries/activity-volume.kql`: executed volume and billable-row check.
- `queries/activity-summary.kql`: executed activity summary.

This is a learning portfolio, not a compliance certification or a production security assessment. Raw account details and sign-in records are retained privately.
