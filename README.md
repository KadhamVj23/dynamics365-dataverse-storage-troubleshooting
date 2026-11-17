# Dynamics 365 Dataverse Storage Troubleshooting

A technical support case study demonstrating a structured approach to investigating Microsoft Dynamics 365 Customer Engagement (CE) and Microsoft Dataverse storage capacity issues.

## Project Overview

This project demonstrates how a Technical Support Engineer can investigate Dataverse storage capacity concerns, identify potential storage constraints, assess environment lifecycle operation failures, and recommend appropriate remediation.

The case study is based on a simulated customer scenario and follows Microsoft's published documentation.

## Objectives

- Understand Dataverse database, file and log storage.
- Navigate the Power Platform Admin Center (PPAC) to review capacity.
- Identify environments with high storage consumption.
- Investigate table-level storage usage.
- Assess possible capacity-related environment operation failures.
- Prepare a Root Cause Analysis (RCA).
- Recommend remediation and validation steps.

## Simulated Customer Scenario

A customer reports that their Dataverse environment is approaching its storage capacity limit and that environment creation or restoration operations are experiencing failures.

The investigation focuses on identifying the storage category with the highest consumption and determining whether insufficient capacity could explain the reported issue.

### Simulated Storage Report

| Storage category | Allocated | Consumed | Remaining | Utilization |
|---|---:|---:|---:|---:|
| Database | 20 GB | 19.2 GB | 0.8 GB | 96% |
| File | 10 GB | 7.5 GB | 2.5 GB | 75% |
| Log | 5 GB | 4.2 GB | 0.8 GB | 84% |

**Initial observation:** Database storage has the highest utilization at 96%.

## Troubleshooting Approach

The investigation follows these steps:

1. Collect the customer's environment details and exact error message.
2. Access Power Platform Admin Center.
3. Navigate to Licensing → Dataverse.
4. Review database, file and log storage consumption.
5. Identify environments with high storage usage.
6. Inspect table-level storage consumption.
7. Verify tenant capacity and environment allocation.
8. Assess the failed environment operation against its error details and capacity requirements.
9. Recommend appropriate remediation.
10. Validate storage and retry the affected operation.

## Project Documentation

| Document | Description |
|---|---|
| [Customer Scenario](customer-scenario.md) | Simulated customer issue and environment details |
| [Storage Investigation Report](storage-investigation-report.md) | Capacity analysis and preliminary findings |
| [PPAC Troubleshooting Steps](ppac-troubleshooting-steps.md) | Detailed navigation and investigation instructions |
| [Root Cause Analysis](root-cause-analysis.md) | Preliminary RCA, potential impact and corrective action plan |
| [Troubleshooting Flowchart](troubleshooting-flowchart.md) | Visual investigation workflow |

## Tools and Knowledge Areas

- Microsoft Dynamics 365 Customer Engagement (CE)
- Microsoft Power Platform
- Power Platform Admin Center (PPAC)
- Microsoft Dataverse
- Database, file and log capacity analysis
- Environment administration and lifecycle operations
- Root Cause Analysis (RCA)
- Technical troubleshooting documentation
- Customer support and incident investigation

## Expected Investigation Outcome

The simulated assessment identifies database capacity as the primary area requiring further investigation.

The remaining database capacity is 0.8 GB, below Microsoft's documented 1 GB minimum for creating an environment with a Dataverse database.

This is a plausible explanation for the reported creation issue, but the exact cause requires validation using the tenant's capacity reports and operation-specific error details.

## Official Microsoft References

1. [Dataverse capacity-based storage details](https://learn.microsoft.com/en-us/power-platform/admin/capacity-storage)
2. [Add more Microsoft Dataverse capacity](https://learn.microsoft.com/en-us/power-platform/admin/add-storage)
3. [Create an environment in Power Platform](https://learn.microsoft.com/en-us/power-platform/admin/create-environment)
4. [Back up and restore environments](https://learn.microsoft.com/en-us/power-platform/admin/backup-restore-environments)
5. [Power Apps Developer Plan](https://learn.microsoft.com/en-us/power-platform/developer/plan)

## Scope and Disclaimer

This is a documentation-based portfolio project using fictional customer information and simulated storage figures.

No live customer tenant was accessed, and no production data was modified. The PPAC instructions describe the administrative workflow based on Microsoft documentation.

The investigation findings are preliminary and do not represent a confirmed production incident or resolution.
