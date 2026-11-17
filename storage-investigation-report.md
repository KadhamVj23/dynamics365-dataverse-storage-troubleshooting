# Dataverse Storage Capacity – Investigation Report

## 1. Investigation Objective

Analyze the simulated Dataverse storage consumption, identify the highest-utilization storage category, and assess the possible impact on environment creation and restoration.

**Note:** All figures and findings in this report are fictional and intended for portfolio demonstration.

## 2. Storage Utilization Analysis

| Storage category | Allocated | Consumed | Remaining | Utilization |
|---|---:|---:|---:|---:|
| Database | 20 GB | 19.2 GB | 0.8 GB | 96% |
| File | 10 GB | 7.5 GB | 2.5 GB | 75% |
| Log | 5 GB | 4.2 GB | 0.8 GB | 84% |

### Key observations

- **Database:** Highest utilization at 96%, with only 0.8 GB remaining.
- **File:** 75% utilized, with 2.5 GB remaining.
- **Log:** 84% utilized, with 0.8 GB remaining.
- Database is the primary area requiring investigation.

## 3. Potential Impact on Environment Operations

Microsoft documentation states that creating an environment with a Dataverse database requires at least 1 GB of available database capacity. Certain environment lifecycle operations, including restore, also require minimum available capacity.

In this simulated scenario, database capacity remaining is only 0.8 GB.

This makes insufficient database capacity a plausible explanation for the reported environment creation or restoration issue. However, the actual cause must be confirmed against the tenant's capacity report and the specific operation that failed.

## 4. Recommended Investigation Areas

The following checks should be performed by an authorized Power Platform administrator in a real customer environment.

### A. Database storage

- Review database consumption by table.
- Identify tables with the highest storage usage.
- Review growth trends to identify rapidly increasing tables.
- Investigate whether unnecessary or obsolete records are contributing to consumption.

### B. File storage

- Review file storage consumption by table.
- Identify large attachments and unnecessary files.
- Review whether eligible file data can be retained or managed through an approved data lifecycle process.

### C. Log storage

- Review log storage consumption.
- Identify the sources contributing to log growth.
- Review applicable retention and audit requirements before recommending any cleanup.

### D. Tenant and environment capacity

- Confirm tenant-level entitlement and actual consumption.
- Check whether the issue is tenant-level or environment-level.
- Review available capacity and any eligible capacity borrowing.
- Confirm the capacity required for the requested environment operation.

## 5. Preliminary Findings

| Finding | Assessment |
|---|---|
| Highest storage utilization | Database |
| Database capacity remaining | 0.8 GB |
| Minimum database capacity for environment creation with Dataverse | 1 GB |
| Likely investigation priority | Database capacity |
| Root cause confirmed? | No – further validation required |

## 6. Initial Recommendation

1. Review database consumption at the table level.
2. Identify unnecessary data only after business-owner approval.
3. Check retention, audit, legal and recovery requirements before deleting records.
4. Verify available tenant capacity and environment-level allocation.
5. If cleanup is insufficient, evaluate additional database capacity or an eligible billing option with the customer's administrator.
6. Retry the environment operation only after confirming sufficient capacity.

## 7. Conclusion

The simulated environment has high Dataverse storage utilization, particularly in database storage.

The available database capacity is below the 1 GB minimum documented for creating an environment with Dataverse. This is a plausible explanation for the reported issue, but the exact cause requires validation using the Power Platform admin center capacity reports and operation-specific error details.

**Investigation status:** Preliminary assessment completed. Further administrator validation required.

## 8. Official Microsoft References

1. [Dataverse capacity-based storage details](https://learn.microsoft.com/en-us/power-platform/admin/capacity-storage)
2. [Create and manage environments in the Power Platform admin center](https://learn.microsoft.com/en-us/power-platform/admin/create-environment)
3. [Back up and restore environments](https://learn.microsoft.com/en-us/power-platform/admin/backup-restore-environments)
