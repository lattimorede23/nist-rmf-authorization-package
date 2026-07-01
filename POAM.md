# PLAN OF ACTION AND MILESTONES (POA&M)

**Tactical Data Processing Workstation (TDPW-1)**

| | |
|---|---|
| **Document Classification** | Unclassified // FOUO |
| **System Name** | Tactical Data Processing Workstation (TDPW-1) |
| **System Owner** | 88th Air Base Wing (88 ABW), Wright-Patterson Air Force Base, Dayton, OH |
| **Reporting Period** | Q3 FY26 (as of 1 July 2026) |
| **Prepared By** | TSgt Maria E. Delgado, ISSO, 88th Communications Squadron |
| **Reviewed By** | Mr. Gerald R. Hutchins, ISSM, 88th Communications Squadron |
| **Document Version** | 1.0 |

> **Note:** This is a fictional POA&M created for cybersecurity training and portfolio demonstration purposes. It does not reflect an actual Air Force system, unit, or finding.

---

## 1. Purpose

This Plan of Action and Milestones (POA&M) documents known security weaknesses identified for TDPW-1 through Security Control Assessment (SCA) activities, STIG/SCAP compliance scanning, and ISSO self-assessment, in accordance with NIST SP 800-37 Rev 2 and AFI 17-101. Each finding below is tracked to resolution, with an assigned responsible office, resourcing estimate, and scheduled completion date (SCD). This POA&M will be updated monthly and reviewed by the ISSM and AO as part of continuous monitoring.

---

## 2. Open Findings

| Weakness ID | Weakness Description | Severity | Related Control(s) | Responsible Office | Scheduled Completion Date | Resources Required | Current Status |
|---|---|---|---|---|---|---|---|
| POAM-TDPW1-001 | No multi-factor authentication (MFA/CAC) capability exists for local logon; system relies solely on username/password authentication due to the absence of domain/PKI middleware infrastructure on the standalone workstation. | High | IA-2 | 88th Communications Squadron, Client Systems Flight (SSgt D. Marsh) | 30 Sept 2026 | Approved standalone CAC middleware/reader kit (~$450); 8 hours install/config labor; ISSO validation testing | Ongoing — procurement request submitted, awaiting funding approval |
| POAM-TDPW1-002 | Security patches and OS updates are applied manually via offline media on a monthly cadence, resulting in patch latency exceeding the 30-day remediation timeline required for High-severity vulnerabilities under DoD patching guidance. | Moderate | SI-2 | 88th Communications Squadron, Client Systems Flight (SSgt D. Marsh) | 15 Aug 2026 | Realignment of maintenance window to bi-weekly cadence; no additional funding required; 4 hours/month additional labor | Ongoing — revised maintenance schedule drafted, pending ISSM approval |
| POAM-TDPW1-003 | SCAP compliance scan (conducted 12 June 2026) identified 6 open DISA Windows 11 STIG findings related to configuration settings (e.g., PowerShell script block logging not fully enabled, legacy SMBv1 client feature not confirmed removed, Windows Remote Management service not disabled). | Moderate | CM-6 | 88th Communications Squadron, Client Systems Flight (SSgt D. Marsh) | 31 July 2026 | 6 hours remediation labor; no additional funding; re-scan validation required | Ongoing — 4 of 6 findings remediated as of 28 June 2026; remaining 2 in progress |
| POAM-TDPW1-004 | No centralized, real-time security monitoring (SIEM/HIDS alerting) capability exists for TDPW-1; monitoring is limited to weekly manual audit log review by the ISSO, delaying detection of anomalous activity between review cycles. | Moderate | SI-4 | 88th Communications Squadron, Cyber Support Flight (TSgt M. Delgado) | 31 Dec 2026 | Evaluation of standalone-compatible host intrusion detection tool; estimated $1,200 licensing; ISSE engineering support (16 hours) | Planned — requirements gathering in progress, no funding currently allocated |
| POAM-TDPW1-005 | Local administrator account password has not been rotated within the required 60-day interval; last rotation recorded 15 March 2026 (108 days as of report date), exceeding local password policy. | Low | IA-5 | 88th Communications Squadron, Client Systems Flight (SSgt D. Marsh) | 15 July 2026 | 1 hour labor; no funding required | Ongoing — rotation scheduled for next maintenance window (12 July 2026) |
| POAM-TDPW1-006 | Removable media control log has gaps for 3 of the last 12 monthly reconciliation periods; import/export activity for approved USB media was not fully documented as required by local media control SOP, creating a chain-of-custody gap for SBU data transfers. | Moderate | MP-5 (supporting AC/AU controls) | 88th Air Base Wing, Wing Cybersecurity Office (Ms. K. O'Neal) | 30 Sept 2026 | SOP refresher training for authorized users (2 hours); revised log template; no funding required | Ongoing — retraining scheduled, revised log template drafted |
| POAM-TDPW1-007 | System time is synchronized manually and was found to have drifted by approximately 6 minutes from the authoritative time source at last verification, which may affect the reliability of audit log timestamp correlation during incident investigation. | Low | AU-8 | 88th Communications Squadron, Client Systems Flight (SSgt D. Marsh) | 31 July 2026 | 1 hour labor per maintenance cycle; consider procurement of GPS-disciplined offline time appliance (~$300) as long-term fix | Ongoing — manual correction applied 28 June 2026; long-term fix under evaluation |

---

## 3. Severity Definitions

| Severity | Definition |
|---|---|
| **High** | Weakness could be exploited to cause severe degradation of confidentiality, integrity, or availability, or represents non-compliance with a mandatory DoD security requirement with no compensating control in place. |
| **Moderate** | Weakness could be exploited to cause serious but not severe impact; a partial compensating control exists but residual risk remains above acceptable threshold. |
| **Low** | Weakness represents a minor deviation from policy or best practice with limited exploitability or impact; primarily a process/documentation gap. |

---

## 4. Summary Statistics

| Metric | Count |
|---|---|
| Total open findings | 7 |
| High severity | 1 |
| Moderate severity | 4 |
| Low severity | 2 |
| Findings with remediation scheduled within 60 days | 4 |
| Findings pending funding/resourcing approval | 2 |

---

## 5. Continuous Monitoring Statement

This POA&M is reviewed monthly by the ISSO and ISSM, with quarterly reporting to the AO in accordance with AFI 17-101 continuous monitoring requirements. Closure of any finding requires ISSO verification, ISSM concurrence, and, for High-severity items, documented AO awareness prior to closure. All findings remain open as of the date of this report; none have been recommended for risk acceptance in lieu of remediation.

---

*Prepared in accordance with NIST SP 800-37 Rev 2, NIST SP 800-53 Rev 5, and AFI 17-101. This document is a fictional artifact for cybersecurity portfolio and training purposes only.*
