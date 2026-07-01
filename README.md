# NIST RMF Authorization Package — Tactical Data Processing Workstation (TDPW-1)

**A fictional Air Force RMF portfolio project | GRC / ISSO skills demonstration**

---

## About This Project

This repository contains a complete, fictional NIST Risk Management Framework (RMF) authorization package built to demonstrate practical GRC (Governance, Risk, and Compliance) and ISSO (Information System Security Officer) documentation skills relevant to Department of Defense and Air Force cybersecurity roles.

Everything in this repository — the system, the unit, the personnel, and the findings — is **fictional**. It was created as a training and portfolio exercise to practice producing authorization artifacts the way they would be developed for a real Air Force information system under NIST SP 800-37 Rev 2, using NIST SP 800-53 Rev 5 controls and Air Force implementation guidance such as AFI 17-101, *Risk Management Framework (RMF) for Air Force Information Technology*.

No content in this repository describes a real Air Force program, system, or individual.

## The Fictional System

**Tactical Data Processing Workstation (TDPW-1)**

| Attribute | Detail |
|---|---|
| System Owner | 88th Air Base Wing (88 ABW), Wright-Patterson Air Force Base, Dayton, OH |
| Purpose | Processes and stores Sensitive But Unclassified (SBU) operational and logistics data supporting base operations |
| Environment | Standalone Windows 11 Enterprise workstation, not domain-joined, located in a controlled access facility |
| Classification | Unclassified // FOUO |
| FIPS 199 Impact Level | Moderate |
| Framework | NIST RMF (SP 800-37 Rev 2), controls from NIST SP 800-53 Rev 5 |
| Authorizing Official | Fictional 88 ABW Designated Authorizing Official (DAO) |

TDPW-1 was designed as a realistic but simplified system: a single, non-networked workstation with a narrow data-processing mission. This keeps the authorization boundary small enough to fully document in a portfolio project while still requiring genuine RMF judgment calls — control tailoring for a standalone architecture, compensating controls in place of network-based protections, and realistic findings around patch management and multi-factor authentication on an air-gapped asset.

## Deliverables

| File | Description |
|---|---|
| [`SSP.md`](./SSP.md) | **System Security Plan** — system identification, environment/architecture, FIPS 199 categorization, applicable overlays and tailoring decisions, 20 documented NIST SP 800-53 Rev 5 controls across AC, AU, CM, IA, SC, and SI families, and assigned roles/POCs. |
| [`POAM.md`](./POAM.md) | **Plan of Action and Milestones** — 7 open findings in table format, each with weakness ID, description, severity, responsible office, scheduled completion date, resources required, and current status. |
| [`SCA.md`](./SCA.md) | **Security Control Assessment Summary** — assessment scope and SP 800-53A methodology, 10 controls tested with test method/expected/actual results and Satisfied / Other Than Satisfied findings, plus an overall assessment summary and authorization recommendation. |

The three documents are cross-referenced: findings noted as "Partially Implemented" in the SSP are the same controls tested as "Other Than Satisfied" in the SCA, which in turn map to the corresponding weakness entries in the POA&M — mirroring how a real authorization package ties together across artifacts.

## Why This Project

This package was built to demonstrate the ability to produce authorization-quality RMF documentation independently: correctly applying FIPS 199 categorization, selecting and tailoring an SP 800-53 control baseline, writing control implementation statements in assessor-ready language, and translating assessment results into a tracked POA&M. These are the core work products of an ISSO or GRC analyst supporting a DoD authorization effort.

## Disclaimer

This is a training and portfolio artifact only. The system, organization, personnel, and findings described are entirely fictional and do not represent any actual Air Force system, unit, or individual.
