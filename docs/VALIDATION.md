# Collection validation

The subscription diagnostic setting selected Administrative, Security and Policy categories and the dedicated workspace as the sole destination. A harmless tag `LabPurpose=ATLAS-SOC-Detection` was applied to the lab group.

Log Analytics returned a successful `MICROSOFT.RESOURCES/TAGS/WRITE` at 01:37:23.109 UTC on 11 October 2026 and its Start event at 01:37:22.312 UTC. The same result set contained the lab's Sentinel rule write and workspace configuration operations. This establishes delivery to AzureActivity; merely saving a diagnostic setting would not have established it.

The first query used a six-hour window after the work resumed later in the day and returned no rows. Expanding to 24 hours exposed the earlier lab events. This illustrates why event time and observation time must be distinguished. Ingestion latency was not measured precisely, because the session paused between the operation and verification.

The subsequent scoped volume query returned:

| Rows | Bytes | BillableRows | DataMB |
|---:|---:|---:|---:|
| 7 | 56417 | 0 | 0.056417 |

Numbers are a snapshot for the lab resource group and a 24-hour window. Subscription-scoped diagnostic-setting events have a blank ResourceGroup and are not included in that scoped count.

Sensitive caller information is deliberately omitted from the public summary. The unchanged original screenshot and raw result observations are retained in the private evidence folder.
