# NIST RMF Authorization Package: TDPW-1

A fictional Air Force authorization package written the way an ISSO or GRC analyst would prepare one. It includes a System Security Plan, a Security Control Assessment, and a Plan of Action and Milestones for a Moderate-impact standalone Windows 11 workstation, under NIST SP 800-37 Rev 2 and SP 800-53 Rev 5.

**Everything here is fictional:** the system, the unit's use of it, the personnel, and the findings. Real organization names (88th Air Base Wing, Wright-Patterson AFB) provide realistic context only. No content describes a real Air Force program, system, or person.

---

## The fictional system

| Attribute | Detail |
| :-- | :-- |
| System | Tactical Data Processing Workstation (TDPW-1) |
| System owner | 88th Air Base Wing (88 ABW), Wright-Patterson AFB, Dayton, OH |
| Purpose | Processes and stores Controlled Unclassified Information (CUI): operational and logistics data supporting base operations |
| Environment | Standalone Windows 11 Enterprise workstation, not networked or domain-joined, in a controlled-access facility |
| FIPS 199 categorization | Moderate (C: Moderate, I: Moderate, A: raised from Low to Moderate) |
| Framework | NIST RMF (SP 800-37 Rev 2), SP 800-53 Rev 5 Moderate baseline, SP 800-53A assessment procedures, DAFI 17-101 |

A single, non-networked workstation keeps the authorization boundary small enough to document fully. It still forces real RMF judgment calls:

- Tailoring controls out (AC-17, AC-4, CA-3) for a standalone architecture.
- Compensating controls in place of network boundary protection.
- Realistic findings around offline patching and multi-factor authentication on an air-gapped asset.

---

## Deliverables

| Document | Contents |
| :-- | :-- |
| [`SSP.md`](SSP.md) | System Security Plan: identification, boundary, architecture, FIPS 199 categorization, overlays and tailoring decisions, roles, and **21 control implementation statements** across AC, AU, CM, IA, SC, and SI |
| [`SCA.md`](SCA.md) | Security Control Assessment: scope, SP 800-53A methods (examine, interview, test), **10 controls tested** with expected and actual results, findings (6 Satisfied, 4 Other Than Satisfied), and an authorization recommendation |
| [`POAM.md`](POAM.md) | Plan of Action and Milestones: **7 open weaknesses** (1 High, 4 Moderate, 2 Low), each with control, owner, scheduled completion, and resources |

---

## Traceability across the package

Every **Other Than Satisfied** finding in the SCA has a POA&M entry. The POA&M also tracks weaknesses found outside the SCA sample: the SI-4 monitoring gap, local admin password rotation, and removable-media log gaps.

| Control | SSP status | SCA result | POA&M item | Severity |
| :-- | :-- | :-- | :-- | :-- |
| IA-2 | Partially Implemented | Other Than Satisfied | POAM-TDPW1-001: no MFA/CAC for local logon | High |
| SI-2 | Partially Implemented | Other Than Satisfied | POAM-TDPW1-002: offline patch latency | Moderate |
| CM-6 | Partially Implemented | Other Than Satisfied | POAM-TDPW1-003: 6 open STIG findings | Moderate |
| SI-4 | Partially Implemented | Not in SCA sample | POAM-TDPW1-004: no centralized monitoring | Moderate |
| IA-5 | Implemented | Not in SCA sample | POAM-TDPW1-005: admin password not rotated in 60 days | Low |
| MP-5 | Not documented in SSP | Not in SCA sample | POAM-TDPW1-006: media control log gaps | Moderate |
| AU-8 | Implemented | Other Than Satisfied (6-minute clock drift) | POAM-TDPW1-007 | Low |

AU-8 shows the normal gap between documented and observed state. The SSP describes the synchronization procedure as implemented, but the assessment found it hadn't been performed on schedule. An SSP update after the assessment would normally record that result.

---

## Why this project

The package demonstrates the core work products of an ISSO or GRC analyst supporting a DoD authorization:

- Applying FIPS 199 categorization.
- Selecting and tailoring an SP 800-53 baseline.
- Writing control implementation statements in assessor-ready language.
- Turning assessment results into a tracked POA&M.

It pairs with [windows11-stig-hardening-lab](https://github.com/lattimorede23/windows11-stig-hardening-lab), a hands-on STIG assessment of a Windows 11 VM. That lab is real work on a different system; TDPW-1 is a fictional system described on paper.

---

## Revision history

**v1.1 (2026-10-14).** Corrections only. No findings, controls, or assessment results were added or removed.

1. **Replaced retired markings.** DoDI 5200.48 (2020) replaced the "For Official Use Only" (FOUO) and "Sensitive But Unclassified" (SBU) markings with Controlled Unclassified Information (CUI). Document markings now read as a simulated CUI marking, and the data descriptions say CUI.
2. **Updated the instruction reference.** AFI 17-101 references now read DAFI 17-101, the current Department of the Air Force issuance.
3. **Corrected the SSP status for IA-2** from Implemented to Partially Implemented. The control's own narrative documents the MFA deviation as an open POA&M item, and the SCA rates it Other Than Satisfied.
4. **Corrected the SSP control count** from 20 to 21. The summary table lists 21 controls.
5. **Replaced an inaccurate traceability claim.** The README said the SSP's "Partially Implemented" controls are exactly the SCA's Other Than Satisfied controls, which was not accurate. It is replaced with the traceability table above.

**v1.0 (2026-07-01).** Original package. Available in the git history at commit `59f5d08`.

---

## Disclaimer

This is a training and portfolio artifact only. The system, organization, personnel, and findings are fictional and do not represent any actual Air Force system, unit, or person.

**Author:** Derrick Lattimore Jr. · B.S. Information Security, Shawnee State University · CompTIA Security+
