# Solution Evidence Register

## Purpose

This file links the Business Analysis case study to the completed Power BI implementation and distinguishes what can be **observed or documented** from what would require live user testing or internal City validation.

## Companion Analytics Project

**GitHub repository:**  
https://github.com/ChaseBrangham/san-diego-service-operations

The companion project documents the source-data scope, Power Query transformations, data-quality correction, date model, DAX measures, dashboard pages, analytical findings, and business recommendations.

## Dashboard Evidence

### Executive Overview

![Executive Overview](https://raw.githubusercontent.com/ChaseBrangham/san-diego-service-operations/main/images/executive-overview.png)

Direct image:  
https://raw.githubusercontent.com/ChaseBrangham/san-diego-service-operations/main/images/executive-overview.png

Evidence supported by this page includes the presence of executive KPIs, workload/backlog views, service-category analysis, council-district analysis, and requests-versus-dispositions trending.

### Backlog & Process Analysis

![Backlog & Process Analysis](https://raw.githubusercontent.com/ChaseBrangham/san-diego-service-operations/main/images/backlog-process-analysis.png)

Direct image:  
https://raw.githubusercontent.com/ChaseBrangham/san-diego-service-operations/main/images/backlog-process-analysis.png

Evidence supported by this page includes monthly net request flow, backlog by district and request type, aging-bucket analysis, and supporting operational-pattern analysis.

## Documented Implementation Evidence

The companion project documents the following implementation choices:

- folder-based ingestion of closed 2025, closed 2026, and current open CSV files;
- data-type standardization and preservation of identifiers as text;
- Open vs. Inactive request classification;
- duplicate-request flags and backlog-aging buckets;
- explicit `Unknown` handling for missing council-district values;
- a dedicated Date dimension;
- an active Date-to-Request Date relationship;
- an inactive Date-to-Date Closed relationship activated for disposition calculations;
- DAX measures for workload, backlog, aging, throughput, duplicates, and referrals;
- repair of a CSV parsing problem in which quoted multiline text shifted values across fields and created apparent date errors.

## Analytical Findings Used in the BA Case Study

The completed analysis documents approximately:

- **800K** modeled service requests;
- **86K** open backlog;
- **75.1%** of open backlog aged 90+ days;
- **367 days** median open-request age;
- **14.8K** open Sidewalk Repair Issues;
- **14.8K** open Street Light Maintenance requests;
- **10.6K** open ROW Maintenance requests;
- **19.2K** open requests in Council District 3;
- **13.1%** duplicate rate;
- **6.0%** referral rate;
- **41.3%** duplicate rate for Street Light Maintenance among the referenced high-volume categories;
- **28.6%** duplicate rate for Encampment among the referenced high-volume categories.

These values are treated as **observed analytical results from a specific project snapshot**, not timeless City performance measures.

## Evidence Classification

| Evidence type | What can be claimed | What cannot be claimed |
|---|---|---|
| Public dashboard screenshot | The visible KPI/visual exists in the completed solution | Every interactive filter or edge case has been tested |
| Companion README / documented DAX-model approach | The project documented a specific transformation/modeling approach | The implementation has been independently code-audited |
| Analytical result | The project produced the reported descriptive result | The result proves a root cause or operational failure |
| Analyst verification | The portfolio author checked the documented solution against defined expectations | Authorized business users accepted the solution |
| Planned UAT | A testable acceptance scenario has been designed | UAT was executed or formally approved |

## Formal UAT Boundary

Formal UAT remains **Not Executed** in this portfolio case study. No authorized City stakeholder group participated in acceptance testing. The separate `17_Solution_Verification.xlsx` workbook records analyst-level verification while preserving this distinction.
