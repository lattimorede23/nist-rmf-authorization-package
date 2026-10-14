# SYSTEM SECURITY PLAN (SSP)

**Tactical Data Processing Workstation (TDPW-1)**

| | |
|---|---|
| **Document Marking** | CUI (simulated marking: this public portfolio document is fictional and contains no actual CUI) |
| **System Name** | Tactical Data Processing Workstation (TDPW-1) |
| **System Owner** | 88th Air Base Wing (88 ABW), Wright-Patterson Air Force Base, Dayton, OH |
| **RMF Step** | Step 2 — Select; Step 3 — Implement (SP 800-37 Rev 2) |
| **FIPS 199 Categorization** | Moderate |
| **Document Version** | 1.0 |
| **Date** | 1 July 2026 |
| **Prepared By** | 88th Communications Squadron, Cyber Support Flight |

> **Note:** This document describes a fictional system and organization created for cybersecurity training and portfolio demonstration purposes. It does not represent an actual Air Force program, and no content herein should be treated as reflecting real DoD systems, personnel, or operations.

---

## 1. System Identification

| Field | Value |
|---|---|
| System Name | Tactical Data Processing Workstation |
| System Acronym | TDPW-1 |
| Unique Identifier | AF-88ABW-TDPW-001 |
| System Owner | 88th Air Base Wing (88 ABW) |
| Hosting Location | Building 262, Area B, Wright-Patterson AFB, OH 45433 |
| System Type | Standalone (non-networked, non-domain-joined) workstation |
| Operational Status | Operational |
| Security Categorization | Moderate (FIPS 199) |
| Classification Level | Unclassified; data handled as Controlled Unclassified Information (CUI) |
| Authorization Type | Authorization to Operate (ATO) |
| Authorizing Official (AO) | Fictional 88 ABW Designated Authorizing Official (DAO) |

### 1.1 Purpose

TDPW-1 processes and stores Controlled Unclassified Information (CUI) operational and logistics data in direct support of base-level operations at Wright-Patterson AFB. The system supports 88 ABW mission partners by providing a dedicated, isolated environment for handling operational planning data, logistics tracking records, and installation support documentation that require protection beyond general unclassified handling but do not require classified processing.

### 1.2 System Boundary

The authorization boundary for TDPW-1 consists of a single Windows 11 Enterprise workstation, its peripheral devices (keyboard, mouse, monitor, and locally attached printer), and removable storage media approved for use with the system under a documented media control process. The boundary does not extend to any network infrastructure, as the system is not connected to the Non-classified Internet Protocol Router Network (NIPRNet), the base Local Area Network (LAN), or any other external network. No wireless interfaces are enabled.

---

## 2. System Environment and Architecture

### 2.1 Physical Environment

TDPW-1 is located within a controlled access facility (Building 262, Area B) that requires Common Access Card (CAC) badge access and a supplemental cipher lock (PIN) for entry. The room is monitored by the 88th Security Forces Squadron via installed CCTV, and access is restricted to personnel on the facility access roster maintained by the System Owner's designated representative. The workstation is secured to a workstation cart with a cable lock during non-duty hours, and the facility is included in the wing's physical security inspection cycle under AFI 31-101.

### 2.2 Technical Architecture

TDPW-1 is a standalone Dell OptiPlex workstation running Windows 11 Enterprise (64-bit), configured per the applicable DISA Security Technical Implementation Guide (STIG) baseline for Windows 11. The system is **not domain-joined**; all account management is performed locally using local user accounts and Windows local security policy. The system has no network interface cards enabled at the OS level (Ethernet and Wi-Fi adapters are disabled in device manager and, where supported, disabled in UEFI/BIOS), eliminating network-based attack surface as an operational design decision consistent with its CUI processing mission.

Data enters and exits the system boundary only via:

1. Locally attached, agency-approved encrypted removable media (USB), subject to media control and two-person handling procedures for import/export, or
2. Local printing to an approved, physically co-located printer.

No email, web browsing, or removable-network capability is present on the system.

### 2.3 System Interconnections

TDPW-1 has **no external system interconnections**. There are no Interconnection Security Agreements (ISAs) or Memoranda of Understanding/Agreement (MOU/MOA) required, as the system does not exchange data electronically with any other information system. This is documented as a permanent architectural control rather than a temporary configuration.

### 2.4 Data Types and Information

| Data Type | Description | Sensitivity |
|---|---|---|
| Operational planning data | Base-level exercise and operations planning artifacts | CUI |
| Logistics tracking records | Supply and logistics status data supporting base operations | CUI |
| Installation support documentation | Facility and installation support records | CUI |

No classified information, Personally Identifiable Information (PII) beyond that minimally necessary for logistics point-of-contact tracking, or Protected Health Information (PHI) is authorized for processing on TDPW-1.

---

## 3. System Categorization (FIPS 199)

In accordance with FIPS Publication 199 and NIST SP 800-60, the following provisional and final impact values were determined for TDPW-1:

| Security Objective | Provisional Impact | Final Impact | Rationale |
|---|---|---|---|
| Confidentiality | Moderate | **Moderate** | Unauthorized disclosure of CUI operational/logistics data could adversely affect base operations and mission partner activities. |
| Integrity | Moderate | **Moderate** | Unauthorized modification of logistics or planning data could degrade base support operations and decision-making. |
| Availability | Low | **Moderate** | While the system is not mission-critical in real time, sustained unavailability would degrade the wing's logistics and planning support function; categorization was raised to Moderate at System Owner discretion to align the baseline uniformly. |

**Overall System Categorization: Moderate**

This categorization drives selection of the NIST SP 800-53 Rev 5 Moderate control baseline as the starting control set for TDPW-1, tailored as described in Section 4.

---

## 4. Applicable Overlays and Tailoring

### 4.1 Baseline

TDPW-1 is assessed against the **NIST SP 800-53 Rev 5 Moderate baseline**, as required for a Moderate-categorized system under NIST SP 800-37 Rev 2 and consistent with Air Force implementation guidance in DAFI 17-101 (formerly AFI 17-101), *Risk Management Framework (RMF) for Department of the Air Force Information Technology (IT)*.

### 4.2 Overlays Applied

No specialized overlay (e.g., Classified, Privacy, Space Platform) applies to TDPW-1, as the system processes unclassified CUI only and does not meet the criteria for the Privacy Overlay (no significant PII processing). A **Standalone/Non-Networked System tailoring profile** has been applied locally by the ISSM to reflect the system's isolated architecture.

### 4.3 Tailoring Decisions

The following control tailoring decisions were made and documented in accordance with DAFI 17-101 and SP 800-53B guidance:

| Control | Tailoring Action | Justification |
|---|---|---|
| AC-17 (Remote Access) | **Not Applicable (NA)** | System has no network connectivity or remote access capability by design; control is inherited/negated by architecture. |
| AC-4 (Information Flow Enforcement) | **Not Applicable (NA)** | No network interfaces are enabled; information flow across the boundary occurs only via physically controlled removable media, addressed under media protection (MP) controls instead. |
| SC-7 (Boundary Protection) | **Tailored — Compensating Control** | Traditional network boundary protection (firewalls, IDS) is not applicable since there is no network connection. Compensating controls consist of physical isolation, disabled network adapters, and BIOS-level port control. |
| CA-3 (Information Exchange) | **Not Applicable (NA)** | No system interconnections exist. |
| CP-7 (Alternate Processing Site) | **Downgraded to CP-7(1) Not Selected** | Given the system's non-mission-critical, standalone nature, an alternate processing site was determined unnecessary; addressed instead through backup media and spare-hardware sparing at the System Owner level. |

All tailoring decisions were reviewed and approved by the ISSM and documented for AO acceptance as part of the authorization package.

---

## 5. Roles and Responsibilities

| Role | Name (Fictional) | Title / Organization |
|---|---|---|
| Authorizing Official (AO) | Fictional 88 ABW DAO | 88th Air Base Wing Designated Authorizing Official |
| Information System Owner (ISO) | Col Aaron J. Whitfield | Director, 88th Mission Support Group, Wright-Patterson AFB |
| Information System Security Manager (ISSM) | Mr. Gerald R. Hutchins | 88th Communications Squadron, Wing ISSM |
| Information System Security Officer (ISSO) | TSgt Maria E. Delgado | 88th Communications Squadron, Cyber Support Flight |
| Information System Security Engineer (ISSE) | Mr. Aaron P. Lindqvist | 88th Communications Squadron, Cybersecurity Engineering |
| Security Control Assessor (SCA) | Ms. Renee K. Ashworth | AFMC Detachment 1, Assessment and Authorization Division |
| System Administrator | SSgt Devon T. Marsh | 88th Communications Squadron, Client Systems Flight |
| Information Assurance Manager (IAM), Base-level | Ms. Karen J. O'Neal | 88th Air Base Wing, Wing Cybersecurity Office |

Roles and responsibilities are assigned in accordance with DAFI 17-101 and AFMAN 17-1301, *Computer Security (COMPUSEC)*. The ISSO is the primary day-to-day point of contact for TDPW-1 and is responsible for maintaining this SSP, coordinating assessments, and tracking the POA&M.

---

## 6. Security Control Implementation

The following controls are drawn from the NIST SP 800-53 Rev 5 Moderate baseline across the Access Control (AC), Audit and Accountability (AU), Configuration Management (CM), Identification and Authentication (IA), System and Communications Protection (SC), and System and Information Integrity (SI) families. Implementation status follows standard RMF terminology: **Implemented**, **Partially Implemented**, **Planned**, or **Not Applicable**.

### 6.1 Access Control (AC)

**AC-2 — Account Management**
*Status: Implemented*
TDPW-1 uses local Windows account management since the system is not domain-joined. The ISSO maintains a local account roster reviewed monthly. Only two account types exist: a standard user account for mission operators and a local administrator account restricted to the System Administrator (SSgt Marsh). Accounts are provisioned upon documented, ISSM-approved access request and are disabled within 24 hours of a user's loss of need-to-know or departure, per local account management SOP.

**AC-3 — Access Enforcement**
*Status: Implemented*
Access to system resources is enforced through Windows 11 Discretionary Access Control (DAC) via NTFS file permissions and local security policy. Standard users are restricted from installing software, modifying system configuration, or accessing administrative functions. Access enforcement settings are configured per the DISA Windows 11 STIG baseline.

**AC-7 — Unsuccessful Logon Attempts**
*Status: Implemented*
Local security policy is configured to lock the account after three consecutive failed logon attempts within a 15-minute window, with a 15-minute lockout duration, consistent with the Moderate baseline and DISA STIG guidance. Lockout events are logged locally.

**AC-8 — System Use Notification**
*Status: Implemented*
The system displays the DoD-standard consent-to-monitoring banner at logon, requiring explicit user acknowledgment before session initiation, in accordance with DoD and Air Force policy.

**AC-11 — Session Lock**
*Status: Implemented*
The workstation is configured to automatically lock the session after 15 minutes of inactivity, requiring re-authentication to resume. Users are also required by local policy to manually lock the session (Windows+L) whenever leaving the workstation unattended.

**AC-17 — Remote Access**
*Status: Not Applicable*
TDPW-1 has no network connectivity and does not support remote access by design (see Section 4.3). Network adapters are disabled at the OS and firmware level.

### 6.2 Audit and Accountability (AU)

**AU-2 — Event Logging**
*Status: Implemented*
The system is configured to log security-relevant events including logon/logoff, account management actions, object access failures, and privilege use, per the Windows 11 STIG audit policy baseline. Logs are retained locally in the Windows Event Log.

**AU-6 — Audit Record Review, Analysis, and Reporting**
*Status: Implemented*
The ISSO manually reviews local audit logs on a weekly basis using Windows Event Viewer, given the absence of a centralized SIEM (a consequence of the system's standalone architecture). Findings of note are documented in an audit review log maintained by the ISSO and escalated to the ISSM as needed.

**AU-8 — Time Stamps**
*Status: Implemented*
The system clock is manually synchronized against an authoritative time source during scheduled maintenance windows, since the workstation cannot reach a network time server. Time synchronization is logged as part of routine maintenance records.

**AU-9 — Protection of Audit Information**
*Status: Implemented*
Audit log access is restricted to the local Administrators group (System Administrator only); standard user accounts have no read or write access to the Event Log files or audit configuration.

### 6.3 Configuration Management (CM)

**CM-2 — Baseline Configuration**
*Status: Implemented*
TDPW-1 is built and maintained against a documented baseline configuration derived from the DISA Windows 11 STIG. The baseline is recorded in the system's configuration management record and reviewed at each SCA cycle.

**CM-6 — Configuration Settings**
*Status: Partially Implemented*
The majority of DISA STIG settings have been applied and validated via SCAP compliance scan. A subset of findings remain open and are tracked in the POA&M (see Deliverable 2), pending remediation by the System Administrator.

**CM-7 — Least Functionality**
*Status: Implemented*
Unnecessary services, ports, and applications have been disabled or removed per the STIG baseline. Only software required for the system's operational data-processing mission is installed; USB mass storage is restricted to an approved allow-list of encrypted devices.

**CM-8 — System Component Inventory**
*Status: Implemented*
The ISSO maintains a hardware and software inventory for TDPW-1, including make/model/serial number of the workstation, installed software versions, and firmware revisions, updated at each configuration change and reviewed quarterly.

### 6.4 Identification and Authentication (IA)

**IA-2 — Identification and Authentication (Organizational Users)**
*Status: Partially Implemented*
All users authenticate with a unique local username and password prior to gaining access; shared accounts are prohibited by local policy. Multi-factor authentication via CAC is not technically feasible in the current standalone configuration (no domain controller or PKI middleware infrastructure); this is documented as a Moderate-baseline deviation and tracked as an open POA&M item (see Deliverable 2).

**IA-5 — Authenticator Management**
*Status: Implemented*
Local password policy enforces a 15-character minimum, complexity requirements, 60-day maximum password age, and password history of 24, consistent with DISA STIG and Air Force password policy requirements. Initial passwords are distributed via a sealed, hand-delivered credential per local SOP.

### 6.5 System and Communications Protection (SC)

**SC-7 — Boundary Protection**
*Status: Not Applicable / Compensating Control*
As TDPW-1 has no network interface, traditional boundary protection mechanisms (firewalls, network IDS) do not apply. Physical isolation, disabled network adapters, and firmware-level port disablement serve as compensating controls, documented under the tailoring decision in Section 4.3.

**SC-28 — Protection of Information at Rest**
*Status: Implemented*
The system's fixed disk is encrypted using BitLocker with a TPM-backed key, protecting CUI data at rest in the event of workstation theft or unauthorized removal. Removable media approved for use with the system are also required to be hardware-encrypted per local media control SOP.

### 6.6 System and Information Integrity (SI)

**SI-2 — Flaw Remediation**
*Status: Partially Implemented*
Because the system has no network connectivity, security patches are applied manually using offline update packages transferred via approved, scanned removable media during scheduled maintenance windows (currently monthly). This offline cadence results in a patch latency greater than that of networked systems, tracked as an open POA&M item.

**SI-3 — Malicious Code Protection**
*Status: Implemented*
Endpoint antivirus (Microsoft Defender for Endpoint, offline signature update mode) is installed and configured for scheduled full-system scans weekly and real-time protection continuously. Signature updates are applied manually via approved removable media during each maintenance window.

**SI-4 — System Monitoring**
*Status: Partially Implemented*
Given the absence of network connectivity, host-based monitoring is limited to local antivirus alerting and manual audit log review (see AU-6). No centralized, real-time SIEM monitoring capability exists for this standalone asset; this limitation is documented as a residual risk accepted at the ISSM level pending future capability review.

---

## 7. Control Implementation Summary

| Control ID | Control Name | Family | Status |
|---|---|---|---|
| AC-2 | Account Management | AC | Implemented |
| AC-3 | Access Enforcement | AC | Implemented |
| AC-7 | Unsuccessful Logon Attempts | AC | Implemented |
| AC-8 | System Use Notification | AC | Implemented |
| AC-11 | Session Lock | AC | Implemented |
| AC-17 | Remote Access | AC | Not Applicable |
| AU-2 | Event Logging | AU | Implemented |
| AU-6 | Audit Record Review, Analysis, and Reporting | AU | Implemented |
| AU-8 | Time Stamps | AU | Implemented |
| AU-9 | Protection of Audit Information | AU | Implemented |
| CM-2 | Baseline Configuration | CM | Implemented |
| CM-6 | Configuration Settings | CM | Partially Implemented |
| CM-7 | Least Functionality | CM | Implemented |
| CM-8 | System Component Inventory | CM | Implemented |
| IA-2 | Identification and Authentication (Org. Users) | IA | Partially Implemented |
| IA-5 | Authenticator Management | IA | Implemented |
| SC-7 | Boundary Protection | SC | Not Applicable / Compensating Control |
| SC-28 | Protection of Information at Rest | SC | Implemented |
| SI-2 | Flaw Remediation | SI | Partially Implemented |
| SI-3 | Malicious Code Protection | SI | Implemented |
| SI-4 | System Monitoring | SI | Partially Implemented |

**Total controls documented: 21** across six families (AC, AU, CM, IA, SC, SI).

---

## 8. Authorization Recommendation

Based on the implementation status summarized above and the open items tracked in the accompanying POA&M, the ISSM recommends TDPW-1 for an **Authorization to Operate (ATO)** with conditions, contingent on remediation of open POA&M findings within their scheduled completion dates. This recommendation will be forwarded to the AO for risk acceptance determination in accordance with NIST SP 800-37 Rev 2 Step 5 (Authorize) and DAFI 17-101.

---

*This SSP is a living document and will be updated upon any significant change to TDPW-1's architecture, control implementation, or operating environment, and reviewed at minimum annually per DAFI 17-101.*
