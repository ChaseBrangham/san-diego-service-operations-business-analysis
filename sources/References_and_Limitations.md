# References & Evidence Boundaries

## Purpose

This file documents the sources used to ground the San Diego Service Operations Business Analysis Case Study and separates **publicly supported facts**, **original analytics-project findings**, and **portfolio assumptions / proposed BA design**.

**Evidence review date:** October 27, 2026

## Public Sources

### City of San Diego - Get It Done
https://www.sandiego.gov/get-it-done

Used for the public context of Get It Done as a City service-request platform and for the ability of requesters to check report status.

### Get It Done Community FAQ / status guidance
https://getitdone.sandiego.gov/TSWCommunityFAQ

Used to ground the simplified public lifecycle represented in the As-Is process map. Public guidance describes statuses such as **New**, **In Process**, **Closed**, and the routing / work-order context available to requesters.

### City of San Diego Open Data - Get It Done Reports
https://data.sandiego.gov/datasets/get-it-done-reports/

Used to ground the public-data scope, dataset fields, and availability of Get It Done records. The portal explicitly limits the dataset to report information rather than detailed evidence of how each underlying issue was addressed.

The public field dictionary is also used to support fields such as request identifiers, parent-request relationships, request/closed dates, status, service type, location, council district, and referral indicators.

### Get It Done Guidelines
https://www.sandiego.gov/sites/default/files/get-it-done-guidelines.pdf

Used to support the high-level submission/routing concept: selecting the issue type helps route a report to the appropriate City function.

### How to Get It Done on the New Mobile App
https://www.sandiego.gov/get-it-done/how-to-get-it-done-on-the-new-mobile-app

Used to support the public interpretation of **Referred**: a report may be routed to an outside agency or a City department not connected to Get It Done, after which normal Get It Done visibility may be limited.

## Companion Analytics Project

### San Diego Service Operations Analysis
https://github.com/ChaseBrangham/san-diego-service-operations

Used as the implementation/evidence source for the original Power BI project: data scope, ETL approach, date modeling, DAX measures, dashboard screenshots, findings, and recommendations.

A snapshot of the companion project's README is retained in this repository at:

`Companion_Analytics_Project_README.md`

## Evidence Classes Used in the Case Study

### 1. Publicly supported

Facts explicitly grounded in City sources, such as public service context, public status descriptions, public field definitions, and dataset limitations.

### 2. Original analytics-project findings

Results produced by the completed Power BI project. Examples include the approximate open backlog, 90+ day backlog share, District 3 concentration, service-category backlog, duplicate/referral rates, and throughput patterns.

These are treated as **snapshot-specific descriptive results**, not permanent City performance figures.

### 3. Reconstructed requirements

Requirements derived retrospectively from the business questions, implemented dashboard capabilities, metric logic, and documented analytical needs. They demonstrate BA methodology but are not represented as requirements elicited from or approved by City stakeholders.

### 4. Portfolio assumptions / proposed design

Items created to demonstrate how the engagement could proceed with stakeholder access: stakeholder groups, engagement plans, To-Be analytics monitoring, governance ownership, implementation sequencing, training, and planned UAT roles.

These are explicitly labeled **proposed**, **reconstructed**, **simulated**, or **portfolio-only**.

## Important Interpretation Rules

The case study deliberately does **not** make unsupported statements such as:

- "The City is understaffed."
- "District 3 is performing poorly."
- "A 90-day request violates the City's SLA."
- "Street Light Maintenance backlog is caused by a specific process failure."
- "Closed means the underlying physical issue was necessarily resolved."
- "Referred means the underlying physical issue was resolved."

The data can identify patterns that **warrant investigation**. Establishing causes or service-performance judgments would require additional operational context and stakeholder validation.

## Key Portfolio Limitations

- No City stakeholder interviews, workshops, observations, or approvals were performed.
- No access was available to internal work-order systems, staffing/capacity data, budgets, costs, service targets/SLAs, or department-specific operating procedures.
- The 90-day threshold is a portfolio monitoring indicator, not an asserted official City SLA.
- UAT scenarios are planned but not executed by authorized City users.
- Static public screenshots can support visual-evidence checks but cannot independently prove every interactive behavior or edge case.
- The formal BA artifacts were created after the Power BI solution; this retrospective nature is disclosed throughout the package.
