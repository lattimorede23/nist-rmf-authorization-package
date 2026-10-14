# SECURITY CONTROL ASSESSMENT (SCA) SUMMARY REPORT

**Tactical Data Processing Workstation (TDPW-1)**

| | |
|---|---|
| **Document Marking** | CUI (simulated marking: this public portfolio document is fictional and contains no actual CUI) |
| **System Name** | Tactical Data Processing Workstation (TDPW-1) |
| **System Owner** | 88th Air Base Wing (88 ABW), Wright-Patterson Air Force Base, Dayton, OH |
| **Assessment Type** | Full Security Control Assessment in support of Initial ATO |
| **Assessment Date(s)** | 8 June 2026 – 12 June 2026 |
| **Security Control Assessor (SCA)** | Ms. Renee K. Ashworth, AFMC Detachment 1, Assessment and Authorization Division |
| **ISSO Point of Contact** | TSgt Maria E. Delgado, 88th Communications Squadron |
| **Document Version** | 1.0 |
| **Date of Report** | 19 June 2026 |

> **Note:** This is a fictional Security Control Assessment report created for cybersecurity training and portfolio demonstration purposes. It does not reflect an actual Air Force assessment.

---

## 1. Assessment Scope

This Security Control Assessment (SCA) evaluated a representative subset of the NIST SP 800-53 Rev 5 Moderate baseline controls implemented on TDPW-1, a standalone Windows 11 Enterprise workstation operated by the 88th Air Base Wing at Wright-Patterson AFB. The assessment was conducted in support of the system's initial Authorization to Operate (ATO) decision under NIST SP 800-37 Rev 2, Step 4 (Assess), and in accordance with DAFI 17-101.

The scope of this assessment includes 10 controls selected from the TDPW-1 System Security Plan (SSP), spanning the Access Control (AC), Audit and Accountability (AU), Configuration Management (CM), Identification and Authentication (IA), System and Communications Protection (SC), and System and Information Integrity (SI) families. Controls were selected to provide representative coverage across all six families and to prioritize controls with elevated risk given the system's standalone, non-networked architecture.

This assessment does not constitute a full baseline assessment of all applicable controls; the remaining Moderate baseline controls documented in the SSP will be assessed in accordance with the system's continuous monitoring schedule.

---

## 2. Assessment Methodology

The assessment was conducted using the assessment methods defined in NIST SP 800-53A: **Examine**, **Interview**, and **Test**.

- **Examine**: Review of system configuration settings, policy documents, audit logs, account rosters, and SCAP scan output.
- **Interview**: Discussions with the ISSO, System Administrator, and select system users to confirm operational practices align with documented procedures.
- **Test**: Direct technical verification on the workstation, including SCAP/STIG compliance scanning (using the DISA Windows 11 STIG SCAP benchmark), manual configuration checks, and functional testing of security mechanisms (e.g., forced lockout testing, session timeout observation).

Assessment results are reported using the SP 800-53A finding categories of **Satisfied (S)** — the control is implemented correctly, operating as intended, and meeting the control objective — or **Other Than Satisfied (O)** — the control exhibits a weakness requiring remediation, tracked in the associated POA&M.

---

## 3. Controls Assessed

| # | Control ID | Control Name | Test Method | Expected Result | Actual Result | Finding Status |
|---|---|---|---|---|---|---|
| 1 | AC-2 | Account Management | Examine, Interview | Only authorized, currently-needed local accounts exist; account roster is current and reviewed monthly. | Local account roster reviewed and confirmed current; two active accounts (one standard, one administrator) matched approved access list; no dormant or unauthorized accounts found. | **Satisfied** |
| 2 | AC-3 | Access Enforcement | Examine, Test | Standard user account is restricted from administrative functions and cannot modify protected system files or settings. | Verified standard user account could not install software, modify NTFS permissions on protected directories, or access Local Security Policy console; enforcement consistent with STIG baseline. | **Satisfied** |
| 3 | AC-7 | Unsuccessful Logon Attempts | Test | Account locks after 3 failed logon attempts within 15 minutes; lockout duration of 15 minutes enforced. | Test lockout triggered successfully after 3 failed attempts; account remained locked for the configured 15-minute duration before automatic reset. | **Satisfied** |
| 4 | AC-11 | Session Lock | Test | Workstation session locks automatically after 15 minutes of inactivity, requiring re-authentication. | Session lock activated at 15-minute mark during observed test; re-authentication was required to resume session. | **Satisfied** |
| 5 | AU-2 | Event Logging | Examine | Security-relevant events (logon/logoff, account management, object access failures, privilege use) are logged per STIG audit policy. | Windows Event Log configuration confirmed to match required audit policy settings; sample log review showed logon/logoff and account management events being captured as expected. | **Satisfied** |
| 6 | AU-8 | Time Stamps | Examine, Test | System clock accurately reflects an authoritative time source, supporting reliable audit log correlation. | System clock found to have drifted approximately 6 minutes from the authoritative reference time at time of testing; manual synchronization process is in place but had not been performed within the expected interval. | **Other Than Satisfied** |
| 7 | CM-6 | Configuration Settings | Test | System configuration settings comply with the DISA Windows 11 STIG baseline with no open findings. | SCAP compliance scan identified 6 open STIG findings (e.g., PowerShell script block logging not fully enabled, WinRM service not disabled, SMBv1 client removal unconfirmed); baseline substantially but not fully compliant. | **Other Than Satisfied** |
| 8 | IA-2 | Identification and Authentication (Organizational Users) | Examine, Interview | Users are uniquely identified and authenticated, ideally leveraging DoD-standard multi-factor authentication (CAC/PKI). | Unique username/password authentication confirmed for all users; however, no CAC/PKI-based multi-factor authentication capability exists due to the system's standalone architecture, representing a deviation from DoD MFA requirements. | **Other Than Satisfied** |
| 9 | SC-28 | Protection of Information at Rest | Examine, Test | Fixed disk and approved removable media are encrypted to protect CUI data at rest. | BitLocker confirmed enabled and TPM-backed on the system drive; sampled removable media confirmed to be hardware-encrypted per media control SOP. | **Satisfied** |
| 10 | SI-2 | Flaw Remediation | Examine, Interview | Security patches are applied within DoD-required timelines for the severity of identified vulnerabilities. | Patch application confirmed via offline media on a monthly cadence; review of patch records showed High-severity vulnerability patches were applied outside the 30-day DoD remediation requirement due to the offline update process. | **Other Than Satisfied** |

---

## 4. Overall Assessment Findings Summary

Of the 10 controls assessed, **6 were found Satisfied** and **4 were found Other Than Satisfied**. The four unsatisfied findings (AU-8, CM-6, IA-2, SI-2) have been documented in the system's Plan of Action and Milestones (POA&M) with assigned responsible offices, resourcing estimates, and scheduled completion dates.

None of the identified weaknesses were assessed as High-severity system-level failures that would preclude an authorization decision; however, the absence of multi-factor authentication (IA-2) is flagged as the highest-priority finding given its direct relevance to DoD identity assurance requirements, and is recommended for expedited remediation. The remaining findings (CM-6, SI-2, AU-8) reflect operational limitations inherent to the system's standalone, non-networked design and are considered manageable through the compensating controls and remediation timelines documented in the POA&M.

**Assessment Conclusion:** The SCA team assesses that TDPW-1's implemented controls, taken together with the tracked POA&M remediation plan, provide an acceptable basis for the AO to render a risk-based authorization decision. The SCA recommends the AO consider an **Authorization to Operate (ATO) with conditions**, contingent on remediation of the IA-2 finding within the timeline documented in the POA&M and continued monthly POA&M reporting for the remaining open items.

---

## 5. Assessor Statement

This assessment was conducted independently by the designated Security Control Assessor, who has no responsibility for the operation or day-to-day management of TDPW-1, in accordance with the independence requirements of NIST SP 800-37 Rev 2 and DAFI 17-101. Results were briefed to the ISSM and ISSO on 19 June 2026 and will be forwarded to the AO as part of the authorization package.

---

*Prepared in accordance with NIST SP 800-53A, NIST SP 800-37 Rev 2, and DAFI 17-101. This document is a fictional artifact for cybersecurity portfolio and training purposes only.*
