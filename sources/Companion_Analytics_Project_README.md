# San Diego Service Operations Analysis

A Power BI business analysis project using real City of San Diego Get It Done service-request data to evaluate operational backlog, aging, throughput, geographic concentration, and duplicate-reporting patterns.

## Project Overview

This project was built to answer a practical operational question:

**Where are service-request bottlenecks occurring, what is driving the backlog, and where should management focus attention?**

Rather than beginning with visualizations, I approached the project as a Business Analyst by defining business questions, profiling and validating the source data, creating management-level KPIs, modeling multiple business dates, and developing an interactive Power BI reporting solution.

The analysis combines approximately **800,000 service-request records** from the City of San Diego Get It Done system.

## Business Questions

The dashboard was designed to answer:

- How large is the current open-service backlog?
- How much of the backlog is significantly aged?
- Which service categories account for the greatest backlog?
- Which high-volume services have the highest 90+ day aging rates?
- Are incoming requests outpacing requests leaving the workflow?
- Which council districts contain the largest active backlogs?
- Which high-volume service categories experience the highest duplicate-reporting rates?
- Where should operational leadership prioritize further investigation?

## Data Source

**City of San Diego Open Data Portal — Get It Done Reports**

https://data.sandiego.gov/datasets/get-it-done-reports/

Source files used:

- Closed service requests from 2025
- Closed service requests from 2026
- Current open service requests

The raw source files are not included in this repository because of their size. They can be downloaded directly from the City of San Diego Open Data Portal.

## Project Architecture

```text
City of San Diego CSV Files
            ↓
     Folder-Based Ingestion
            ↓
        Power Query
            ↓
 Cleaning & Data Validation
            ↓
  fact_ServiceRequests Table
            ↓
 Date Model + DAX Measures
            ↓
      Power BI Dashboard
            ↓
 Business Findings & Recommendations
```

## Data Preparation and ETL

The three CSV files were loaded through a folder-based Power Query pipeline and combined into a single analytical table.

Key transformation steps included:

- Standardizing column data types
- Preserving IDs, ZIP codes, and other identifiers as text
- Creating an Open vs. Inactive request classification
- Creating duplicate-request flags
- Creating backlog aging buckets
- Creating monthly reporting fields
- Standardizing missing council-district values as `Unknown`
- Creating an ordered aging-bucket field for reporting
- Validating source-file ingestion and status distributions

### Data Quality Issue Identified

During data profiling, approximately 800 records initially generated date-conversion errors.

Investigation showed that the dates themselves were not the root problem. Free-text fields containing quoted multiline content were causing some CSV records to be parsed incorrectly, shifting values across columns.

Rather than removing the affected records downstream, I corrected the CSV ingestion logic so quoted fields were parsed properly.

This eliminated the date-conversion errors and restored record integrity before the data entered the reporting model.

## Data Model

A dedicated Date table was created to support monthly operational reporting.

Two relationships were modeled between the Date table and the service-request fact table:

```text
Date[Date] ───────────────► Request Date
             Active

Date[Date] - - - - - - - ► Date Closed
             Inactive
```

The active relationship supports analysis of incoming request volume.

The inactive relationship is activated with DAX `USERELATIONSHIP()` when calculating requests that left the workflow by closing date.

This allows incoming workload and outgoing workload to be compared correctly on the same monthly timeline.

## Key DAX Measures

Core measures include:

```text
Total Requests
Open Backlog
30+ Day Backlog
90+ Day Backlog
90+ Day Backlog Rate
Median Open Case Age
Requests Received
Requests Dispositioned
Net Request Flow
Duplicate Requests
Duplicate Rate
Referred Requests
Referral Rate
```

## Dashboard

### Executive Overview

The Executive Overview provides leadership-level visibility into workload, backlog severity, high-volume service categories, and monthly operational throughput.

![Executive Overview](https://raw.githubusercontent.com/ChaseBrangham/san-diego-service-operations/main/images/executive-overview.png)

### Backlog & Process Analysis

The second page provides deeper analysis of backlog aging, geographic concentration, monthly net request flow, referral activity, and duplicate-reporting patterns.

![Backlog & Process Analysis](https://raw.githubusercontent.com/ChaseBrangham/san-diego-service-operations/main/images/backlog-process-analysis.png)

## Key Findings

The analysis identified several notable operational patterns.

**Current backlog:** Approximately **86,000 requests** remain open.

**Severely aged backlog:** Approximately **75.1% of the open backlog is more than 90 days old**.

**Typical open-request age:** The median open case age is approximately **367 days**.

**Largest service backlogs:** Sidewalk Repair Issues and Street Light Maintenance each account for approximately **14,800 open requests**, followed by ROW Maintenance at approximately **10,600**.

**Backlog severity:** Approximately **95.3% of the Pavement Maintenance backlog** and **94.1% of the Sidewalk Repair backlog** are more than 90 days old.

**Geographic concentration:** Council District **3** has the largest open backlog at approximately **19,200 requests**.

**Duplicate reporting:** Approximately **13.1% of all service requests are identified as duplicates**.

**Referral activity:** Approximately **6.0% of requests are referred**.

**High duplicate concentration:** Among the highest-volume service categories, Street Light Maintenance has an approximately **41.3% duplicate rate**, followed by Encampment at approximately **28.6%**.

**Operational throughput:** Monthly request intake frequently exceeds monthly dispositions, indicating recurring periods of positive net request flow and additional backlog pressure.

## Business Recommendations

Operational leadership should prioritize service categories where **high request volume and severe aging occur simultaneously**, particularly Sidewalk Repair, Street Light Maintenance, ROW Maintenance, and Pavement Maintenance.

The high duplicate-reporting rate within Street Light Maintenance warrants additional investigation. Potential contributing factors could include long processing times, highly visible unresolved conditions, or limited status visibility for residents. The dashboard identifies the pattern but does not assume causation.

Council District 3 should receive additional operational review because it contains the largest active backlog. Before making resource-allocation decisions, backlog volume should also be evaluated against population, service mix, and infrastructure characteristics.

Monthly Requests Received versus Requests Dispositioned should be monitored over time. Sustained positive net request flow indicates that new demand is entering faster than workload is leaving the system and may require capacity or process intervention.

## Tools and Technologies

**Power BI** — dashboard development and data modeling  
**Power Query** — ingestion, transformation, cleaning, and validation  
**DAX** — KPI development and time-based analysis  
**CSV / Flat Files** — operational source data  
**Dimensional Modeling** — fact table and Date dimension design

## Skills Demonstrated

This project demonstrates practical experience with:

- Business requirements analysis
- KPI definition
- Operational reporting
- Data profiling
- Data-quality troubleshooting
- ETL and data transformation
- Dimensional modeling
- DAX development
- Multiple date relationships
- Root-cause prioritization
- Executive dashboard design
- Translating analytical findings into business recommendations

## Repository Structure

```text
san-diego-service-operations/
│
├── images/
│   ├── executive-overview.png
│   └── backlog-process-analysis.png
│
├── powerbi/
│   └── San_Diego_Service_Operations.pbix
│
├── sql/
│
├── data/
│   └── raw/
│
└── README.md
```

## Project Note

The Get It Done dataset records service-request workflow activity. A request being closed or referred should not automatically be interpreted as confirmation that the underlying physical issue was resolved.

For this reason, the dashboard uses terminology such as **Requests Dispositioned** rather than claiming all closed records represent completed physical work.
