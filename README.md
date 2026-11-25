# Brightwave security sql investigations

# Insider Risk, Data Access & Phishing Response Investigation

## Project overview

This project uses fictional Brightwave Logistics data to explore employee access activity, email security events, and incident response in MySQL. The dataset covers **August 3–30, 2026** and contains five CSV tables with **423 records** in total.

The project files specify the investigation scope and dataset, but include no SQL scripts or saved query results. The aggregate figures below are calculated directly from the supplied CSVs; they are descriptive summaries, not evidence of wrongdoing or completed SQL analysis.

## Objectives

- Summarize access activity across systems, actions, outcomes, and locations.
- Review the mix of email security categories and recorded user actions.
- Describe incidents by type, severity, and status.
- Prepare related CSV tables for analysis in MySQL.
- Identify data-quality issues for review while preserving the raw data.

## Key business questions

- What kinds of access actions and outcomes appear in the logs?
- How is access distributed across office, VPN, and remote locations?
- What email security categories and user actions are recorded?
- Which incident types, severities, and statuses appear in the dataset?
- Are there missing values or inconsistent entries that could affect analysis?

## Dataset and aggregate summary

| Dataset | Records | Simple summary |
|---|---:|---|
| Employees | 20 | 18 active; 2 terminated |
| Systems | 10 | 4 restricted, 3 confidential, 2 internal, 1 public |
| Access logs | 254 | 236 granted; 18 denied |
| Email security events | 119 | 57 phishing, 45 legitimate, 11 spam, 6 malware |
| Incidents | 20 | 13 closed, 4 in progress, 3 open |
| **Total** | **423** | Five related datasets |

## Key aggregates

### Access logs

| Measure | Count |
|---|---:|
| View | 153 |
| Edit | 59 |
| Download | 29 |
| Export | 13 |
| **Total access records** | **254** |

| Access result | Count |
|---|---:|
| Granted | 236 |
| Denied | 18 |
| **Total** | **254** |

| Location | Count |
|---|---:|
| Office | 180 |
| VPN | 64 |
| Remote | 10 |
| **Total** | **254** |

### Email security events

| Email category | Count |
|---|---:|
| Phishing | 57 |
| Legitimate | 45 |
| Spam | 11 |
| Malware | 6 |
| **Total email events** | **119** |

| Recorded user action | Count |
|---|---:|
| Opened | 28 |
| Clicked Link | 22 |
| Reported | 18 |
| Deleted | 17 |
| Replied | 17 |
| Ignored | 14 |
| Opened Attachment | 3 |
| **Total email events** | **119** |

### Incidents

| Incident severity | Count |
|---|---:|
| High | 6 |
| Medium | 6 |
| Low | 5 |
| Critical | 3 |
| **Total incidents** | **20** |

| Incident status | Count |
|---|---:|
| Closed | 13 |
| In Progress | 4 |
| Open | 3 |
| **Total incidents** | **20** |

| Incident type | Count |
|---|---:|
| Phishing Link Clicked | 7 |
| Access Beyond Clearance | 3 |
| Lost Device | 2 |
| Malware Attachment Opened | 2 |
| Policy Violation | 2 |
| Unauthorized Access Attempt | 2 |
| Bulk Data Export | 1 |
| Terminated Account Activity | 1 |
| **Total incidents** | **20** |

## Findings and insights

- **Access activity is mostly recorded as views.** The dataset contains 153 view actions out of 254 access records; edits, downloads, and exports make up the remainder.
- **Most access attempts were granted.** There are 236 granted and 18 denied records. These counts alone do not establish whether any access was appropriate.
- **Office is the most frequently recorded access location.** There are 180 office records, compared with 64 VPN and 10 remote records.
- **Phishing is the largest email category in the supplied data.** It appears in 57 of 119 events; legitimate email appears in 45.
- **Phishing Link Clicked is the most common incident type.** It accounts for 7 of the 20 incident records.
- **Most incidents are marked closed.** 13 incidents are closed, while 7 are open or in progress.

These are dataset-level summaries. Employee-level risk conclusions would require validated analysis and appropriate context. The dataset notes explicitly caution that risk indicators are prompts for further review, not proof of wrongdoing.

## SQL techniques and concepts

The files describe a MySQL dataset with linked employee and system identifiers, suitable for demonstrating:

- CSV import and appropriate date/time data types.
- Table relationships using primary and foreign keys.
- Joins across employee, system, access, email, and incident records.
- Filtering, grouping, and aggregate functions such as `COUNT`.
- `NULL` handling and data-quality checks.
- Creating cleaned tables or views while retaining raw source data.

These are techniques supported by the project structure and import notes; the provided files do not include SQL queries proving that these analyses were implemented in SQL.

## Data quality and interpretation notes

The project notes say blank cells should be loaded as `NULL`, highlight several columns for checking, and state that intentional data-quality issues are present. For example, the employee data contains department values `Legal` and `Legal `, which differ by trailing whitespace and may split a grouped count unless standardized. The raw data should be preserved while any cleaned version or view is prepared.

## Scope and tools

- **Organization:** Brightwave Logistics (fictional)
- **Database:** MySQL
- **Period:** August 3–30, 2026
- **Tables:** `employees`, `systems`, `access_logs`, `email_security_events`, `incidents`
