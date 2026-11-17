# Dataverse Storage Troubleshooting – PPAC Step-by-Step Guide

## 1. Objective

This guide explains how a support engineer or Power Platform administrator can investigate Dataverse storage consumption using the Power Platform admin center (PPAC).

The investigation covers:

- Tenant-level storage consumption.
- Database, file and log storage.
- Environment-level storage consumption.
- Table-level storage analysis.
- Capacity allocation and possible remediation.

**Important:** The figures in this portfolio are simulated. These steps describe the real administrative workflow based on Microsoft documentation. No live customer tenant was accessed.

---

## 2. Prerequisites

Before starting the investigation:

- Obtain access to the customer's Power Platform admin center.
- Confirm that the account has the required administrative permissions.
- For tenant capacity administration, use an appropriately authorized Tenant Administrator, Power Platform Administrator or Dynamics 365 Administrator account.
- Identify the affected environment name and environment type.
- Obtain the exact error message and operation that failed (create, copy, restore or another operation).

Do not attempt to modify or delete customer data without the appropriate authorization.

---

## 3. Step 1 – Open Power Platform Admin Center

1. Open a browser.
2. Navigate to: https://admin.powerplatform.microsoft.com
3. Sign in using the authorized organizational account.
4. Once the admin center opens, locate the navigation pane on the left.
5. Select **Licensing**.
6. Under the Products section, select **Dataverse**.

**Expected result:** The Dataverse capacity page opens, showing tenant-level storage information.

Note: Depending on the tenant's licensing model and admin center experience, the navigation may instead show **Licensing → Capacity add-ons → Dataverse**.

---

## 4. Step 2 – Review Overall Storage Consumption

On the Dataverse Summary page, locate the **Usage per storage type** section.

Review the three storage categories:

### A. Database storage
Represents the database capacity consumed by Dataverse records and related data.

### B. File storage
Represents file content such as attachments and files stored in Dataverse.

### C. Log storage
Represents Dataverse log capacity consumption.

Record the following information for each category:

- Allocated or entitled capacity.
- Actual consumed capacity.
- Remaining capacity, where displayed.
- Whether any usage is covered by pay-as-you-go.
- Whether the tenant is in an overage state.

For this simulated case:

| Storage type | Allocated | Consumed | Remaining |
|---|---:|---:|---:|
| Database | 20 GB | 19.2 GB | 0.8 GB |
| File | 10 GB | 7.5 GB | 2.5 GB |
| Log | 5 GB | 4.2 GB | 0.8 GB |

**Investigation finding:** Database storage has the highest utilization at 96%.

---

## 5. Step 3 – Identify Environments Consuming the Most Storage

From the Dataverse Summary page:

1. Locate the **Top environments consuming storage** section.
2. Select **See all environments**.
3. Review the list of Dataverse environments.
4. Locate the affected environment using its name.
5. Review its database, file and log consumption.
6. Check the overage status, environment type, preallocated capacity and pay-as-you-go linkage status where available.
7. Identify whether the affected environment is responsible for a significant portion of tenant consumption.

**What to record:**

- Environment name.
- Environment type (Production, Sandbox, etc.).
- Database consumption.
- File consumption.
- Log consumption.
- Overage status.
- Whether capacity is preallocated.

**Support engineer's objective:** Determine whether the issue is caused by overall tenant capacity or an individual environment's allocated capacity.

---

## 6. Step 4 – Inspect Environment Storage Details

After identifying the affected environment:

1. Open the environment's storage details by selecting its **Details** option or selecting the environment name, depending on the page layout.
2. Review the environment-level capacity information.
3. Inspect the database, file and log usage sections.
4. Review the top-consuming tables and their storage growth over time.

The detailed view helps identify which Dataverse tables contribute most to storage consumption.

### What to investigate

**Database storage**
- Identify the largest database tables.
- Check whether certain tables show unusually high growth.
- Review whether old or unnecessary records may be contributing to consumption.

**File storage**
- Identify tables consuming the most file storage.
- Review attachment and file-related storage patterns.
- Check whether large or outdated files can be managed under an approved retention policy.

**Log storage**
- Identify the tables or sources contributing to log consumption.
- Review whether audit or other log retention requirements are affecting storage.
- Confirm retention requirements before proposing cleanup.

---

## 7. Step 5 – Review Consumption Per Table

From the selected environment's details, locate the **Consumption per table** section.

1. Review the list of Dataverse tables.
2. Compare the storage consumed by each table.
3. Identify the tables with the highest consumption.
4. Check the database, file and log categories separately.
5. Where available, review the growth information over time.
6. Record the top-consuming tables for further investigation.

Examples of tables or data areas worth reviewing include:

- Annotation (Notes and attachments).
- Activity-related records.
- Audit-related data.
- Custom business tables.
- Tables containing file or image columns.
- Dataverse search indexes, where applicable.

Do not assume that a particular table is responsible before reviewing the actual report.

**Important:** System tables are included in Dataverse storage reporting. A large table is not automatically safe to clean up.

---

## 8. Step 6 – Export Storage Information

Where the Download option is available:

1. Navigate to the Dataverse environment capacity list.
2. Select **Download** above the environment list.
3. Download the CSV file.
4. Open it using Excel.
5. Review the environment-level storage information.
6. Use the report to document the affected environment and compare storage consumption.

The downloadable environment report provides high-level information. Use the environment's detailed capacity view for more detailed table-level investigation.

---

## 9. Step 7 – Investigate Environment Creation or Restore Failures

If the customer reports that environment creation or restoration is failing:

1. Ask for the exact operation that failed.
2. Obtain the error message and approximate failure time.
3. Confirm which environment is affected.
4. Review tenant-level Dataverse capacity.
5. Review the affected environment's capacity allocation and consumption.
6. Check whether sufficient capacity is available for the requested operation.
7. Review any relevant operation-specific requirements in Microsoft documentation.
8. Compare the error details with the capacity findings.

For example, Microsoft documents a minimum of 1 GB of available database capacity for creating an environment with a Dataverse database.

In this simulated scenario, only 0.8 GB of database capacity remains. This makes insufficient capacity a plausible contributor to the reported issue, but the actual cause must be validated against the operation's error details and the tenant's capacity information.

---

## 10. Step 8 – Evaluate Remediation Options

After identifying the storage category and environment responsible for the consumption, discuss the following options with the authorized administrator.

### Option A – Review and clean up unnecessary data

- Identify obsolete or duplicate business records.
- Review old attachments and files.
- Check whether eligible records can be archived or removed.
- Obtain business-owner approval before deletion.
- Consider audit, legal, retention and recovery requirements.

### Option B – Allocate available tenant capacity

If the tenant has available capacity:

1. Navigate to **Licensing → Dataverse**.
2. Select **Manage capacity** on the Summary page.
3. Select the affected environment.
4. Review its currently allocated and consumed database, file and log capacity.
5. Review the available capacity shown in the panel.
6. Enter appropriate allocation values within the available limits.
7. Configure capacity notifications if required.
8. Select **Save**.

Only an appropriately authorized administrator should perform this change.

### Option C – Evaluate additional capacity

If available tenant capacity is insufficient:

- Evaluate purchasing the appropriate Dataverse capacity add-on.
- Consider an eligible pay-as-you-go billing option.
- Discuss capacity extension options with the tenant administrator.

Additional capacity decisions should be made by the customer's licensing or billing administrator.

---

## 11. Step 9 – Validate After Remediation

After an approved remediation action:

1. Return to **Licensing → Dataverse**.
2. Review tenant-level database, file and log consumption.
3. Open the affected environment's capacity details.
4. Compare the updated consumption with the original report.
5. Confirm whether the relevant capacity constraint has been addressed.
6. Ask the customer or authorized administrator to retry the previously failing operation.
7. Record the result and any remaining errors.

Do not mark the issue resolved based only on a reduction in storage consumption. Confirm the original operation succeeds or document any remaining issue.

---

## 12. Troubleshooting Decision Summary

| Observation | Investigation direction |
|---|---|
| Database usage is high | Inspect top database-consuming tables |
| File usage is high | Review attachment and file-consuming tables |
| Log usage is high | Review log consumption and retention requirements |
| One environment has overage | Check its allocated and consumed capacity |
| Tenant capacity is insufficient | Review cleanup and additional capacity options |
| Environment restore fails | Check operation-specific capacity requirements and error details |
| Storage remains high after cleanup | Recheck reports and investigate remaining consumers |

## 13. Expected Investigation Outcome

For this simulated case:

- Database storage is the highest-utilization category at 96%.
- File storage is at 75%.
- Log storage is at 84%.
- Database storage has only 0.8 GB remaining.
- Table-level consumption needs to be examined before identifying a cleanup target.
- The environment operation failure requires validation against its exact error details.

**Investigation status:** Storage assessment completed using simulated figures. Live PPAC validation and remediation are not performed in this portfolio exercise.

---

## 14. Official Microsoft References

1. [Dataverse capacity-based storage details](https://learn.microsoft.com/en-us/power-platform/admin/capacity-storage)
2. [Add more Microsoft Dataverse capacity](https://learn.microsoft.com/en-us/power-platform/admin/add-storage)
3. [Create an environment in the Power Platform admin center](https://learn.microsoft.com/en-us/power-platform/admin/create-environment)
4. [Back up and restore environments](https://learn.microsoft.com/en-us/power-platform/admin/backup-restore-environments)
