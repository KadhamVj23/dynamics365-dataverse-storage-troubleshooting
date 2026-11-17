# Customer Support Case Study: Dataverse Storage Capacity Issue

## 1. Project Overview

This case study demonstrates a structured troubleshooting approach for a simulated Microsoft Dynamics 365 Customer Engagement (CE) and Microsoft Dataverse storage capacity issue.

**Project type:** Simulated technical support case study  
**Platform:** Dynamics 365 CE / Microsoft Power Platform  
**Focus area:** Dataverse storage investigation and environment lifecycle operations

## 2. Customer Problem Statement

A customer reports that their Microsoft Dataverse environment is approaching its storage capacity limit.

They are experiencing difficulties creating and restoring environments and want to understand:

- Which storage category is consuming the most capacity.
- Which tables or data are contributing to the storage usage.
- Why environment lifecycle operations may be affected.
- What corrective actions can be taken to address the issue.

## 3. Simulated Customer Environment

The following figures are fictional and created for this portfolio exercise. They do not represent a real customer tenant.

| Storage category | Allocated capacity | Used capacity |
|---|---:|---:|
| Database | 20 GB | 19.2 GB |
| File | 10 GB | 7.5 GB |
| Log | 5 GB | 4.2 GB |

**Reported symptom:** The customer reports that environment creation and restoration operations are failing due to insufficient storage capacity.

## 4. Initial Support Assessment

The support investigation will focus on:

1. Reviewing database, file and log capacity separately.
2. Identifying the storage category with the highest utilization.
3. Reviewing table-level storage consumption.
4. Checking whether the tenant has sufficient available capacity for the requested operation.
5. Recommending appropriate remediation steps.

## 5. Scope and Limitations

This is a documentation-based simulation, not a live customer investigation. No production tenant was accessed or modified. Storage figures, customer details and reported symptoms are fictional.

The recommendations will be based on official Microsoft documentation and a structured technical support approach.
