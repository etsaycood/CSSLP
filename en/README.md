# CSSLP Comprehensive Study Guide

Welcome to the **Certified Secure Software Lifecycle Professional (CSSLP)** study guide. This material is designed to serve as a comprehensive, modern replacement for traditional study books, focusing strictly on actionable knowledge, exam focus areas, and industry-standard security practices.

> **Current Progress**: Only the localized English (EN) variant of the study guide is currently built. A Chinese variant will mirror this structure in the future.

---

## Study Approach

This guide is organized according to the official (ISC)² CSSLP Exam Outline (8 Domains).

### Recommended Workflow:
1. Begin each domain by reading its respective **`X.0_overview.md`**. This provides the weighting, key relationships to other domains, and specific study tips prioritizing what (ISC)² considers most important.
2. Read through the sub-section files sequentially.
3. Review the **Key Terms Glossary** at the bottom of each sub-section file. The exam heavily tests exact terminology definitions (e.g., *Verification* vs. *Validation*).

---

## Course Roadmap

### [Domain 1: Secure Software Concepts (10%)](domain1/1.0_overview.md)
The foundational principles of security that guide all subsequent domains.
- [1.1 Core Concepts (CIA, Non-Repudiation, Least Privilege)](domain1/1.1_core_concepts.md)
- [1.2 Security Design Principles (Defense in Depth, Fail-Secure)](domain1/1.2_security_design_principles.md)

### [Domain 2: Secure Software Lifecycle Management (14%)](domain2/2.0_overview.md)
Integrating security into the overarching management of software methodologies.
- [2.1 Security in SDLC Methodologies (Agile, DevSecOps)](domain2/2.1_security_in_sdlc_methodology.md)
- [2.2 Security Metrics & KPIs](domain2/2.2_security_metrics.md)
- [2.3 Security and Risk Management Concepts](domain2/2.3_security_and_risk_management.md)
- [2.4 Compliance and Privacy Standards](domain2/2.4_compliance_and_privacy.md)
- [2.5 Reporting Programs (Bug Bounties, Responsible Disclosure)](domain2/2.5_reporting_programs.md)
- [2.6 Maturity Models (BSIMM, SAMM)](domain2/2.6_maturity_models.md)
- [2.7 Security Awareness Training](domain2/2.7_security_awareness_training.md)
- [2.8 Third-Party Outsourcing](domain2/2.8_third_party_outsourcing.md)
- [2.9 Secure Operation Practices (SoD, Mandatory Vacations)](domain2/2.9_secure_operation_practices.md)

### [Domain 3: Secure Software Requirements (14%)](domain3/3.0_overview.md)
Capturing and prioritizing security requirements before architecture begins.
- [3.1 Software Security Requirements (Functional vs. Non-Functional)](domain3/3.1_software_security_requirements.md)
- [3.2 Compliance Requirements](domain3/3.2_compliance_requirements.md)
- [3.3 Data Classification](domain3/3.3_data_classification.md)
- [3.4 Privacy Requirements](domain3/3.4_privacy_requirements.md)
- [3.5 Data Access Provisioning](domain3/3.5_data_access_provisioning.md)
- [3.6 Misuse and Abuse Cases](domain3/3.6_misuse_and_abuse_cases.md)
- [3.7 Requirements Traceability Matrix (SRTM)](domain3/3.7_security_requirement_traceability.md)
- [3.8 Third-Party Vendor Requirements](domain3/3.8_third_party_vendor_requirements.md)

### [Domain 4: Secure Software Architecture and Design (14%)](domain4/4.0_overview.md)
Building the threat models and architectural blueprints.
- [4.1 Threat Modeling (STRIDE, DREAD, PASTA)](domain4/4.1_threat_modeling.md)
- [4.2 Security Architecture (Microservices, Zero Trust)](domain4/4.2_security_architecture.md)
- [4.3 Secure Interface Design (APIs, UI)](domain4/4.3_secure_interface_design.md)
- [4.4 Architectural Risk Assessment](domain4/4.4_architectural_risk_assessment.md)
- [4.5 Security Properties and Constraints](domain4/4.5_security_properties_constraints.md)
- [4.6 Data Modeling and Classification Design](domain4/4.6_data_modeling_classification.md)
- [4.7 Reusable Secure Design (Design Patterns)](domain4/4.7_reusable_secure_design.md)

### [Domain 5: Secure Software Implementation (14%)](domain5/5.0_overview.md)
Coding the application securely and avoiding standard flaws.
- [5.1 Secure Coding Practices (OWASP Top 10)](domain5/5.1_secure_coding_practices.md)
- [5.2 Code Analysis (Peer Review, SAST, IAST)](domain5/5.2_analyze_source_code.md)
- [5.3 Implement Security Controls (Cryptography, JWT)](domain5/5.3_security_controls.md)
- [5.4 Vulnerability Management (Triage, Remediation)](domain5/5.4_manage_vulnerabilities.md)
- [5.5 Secure Environments (CI/CD, Vaults)](domain5/5.5_secure_environments.md)
- [5.6 Protect Source Code (Code Signing, Branches)](domain5/5.6_protect_source_code.md)

### [Domain 6: Secure Software Testing (14%)](domain6/6.0_overview.md)
Validating that the implementation meets the requirements securely.
- [6.1 Security Testing Strategy (White/Black/Gray Box)](domain6/6.1_security_testing_strategy.md)
- [6.2 Security Testing Plan (Scope, SRTM)](domain6/6.2_security_testing_plan.md)
- [6.3 Security Test Cases (Positive/Negative, BVA)](domain6/6.3_security_test_cases.md)
- [6.4 Verification vs. Validation (IV&V, UAT)](domain6/6.4_verification_and_validation.md)
- [6.5 Security Testing Tools (Pentesting, DAST, Fuzzing)](domain6/6.5_security_testing_tools.md)
- [6.6 Vulnerability Assessment (Infrastructure scanning)](domain6/6.6_vulnerability_assessment.md)
- [6.7 Secure Test Data (Masking, Synthetic Data)](domain6/6.7_manage_test_data.md)
- [6.8 Analyze Test Results (Residual Risk, False Positives)](domain6/6.8_analyze_test_results.md)

### [Domain 7: Secure Deployment, Operations, and Maintenance (14%)](domain7/7.0_overview.md)
Managing the software in production through its end-of-life.
- [7.1 Secure Deployment (Blue/Green, Canary)](domain7/7.1_secure_software_deployment.md)
- [7.2 Security Data Management (ISCM, SIEM)](domain7/7.2_security_data_management.md)
- [7.3 Incident Management (PICERL)](domain7/7.3_incident_management.md)
- [7.4 Problem Management (RCA, 5 Whys)](domain7/7.4_problem_management.md)
- [7.5 Patch Management (Virtual Patching)](domain7/7.5_patch_vulnerability_management.md)
- [7.6 Security Control Testing (SOC 2, Tuning)](domain7/7.6_security_control_testing.md)
- [7.7 Threat Hunting (IoCs, Cyber Kill Chain)](domain7/7.7_threat_hunting.md)
- [7.8 Log Event Management (WORM, NTP)](domain7/7.8_log_event_management.md)
- [7.9 Backup and Recovery (RTO/RPO, Full vs. Incremental)](domain7/7.9_backup_and_recovery.md)
- [7.10 BCP and DRP (Disaster Recovery Sites)](domain7/7.10_bcp_and_drp.md)
- [7.11 Change and Release Management (CAB, SoD)](domain7/7.11_change_release_management.md)
- [7.12 EOL and Decommissioning (EOS)](domain7/7.12_eol_decommissioning.md)
- [7.13 Information Disposal (Crypto-shredding, Purging)](domain7/7.13_information_disposal.md)

### [Domain 8: Secure Software Supply Chain (10%)](domain8/8.0_overview.md)
Securing third-party dependencies and supplier risks.
- [8.1 Supply Chain Risks (Dependency Confusion, Typo-squatting)](domain8/8.1_supply_chain_risks.md)
- [8.2 Analyze 3rd-Party Software (OSS Licenses, SCA)](domain8/8.2_analyze_third_party_software.md)
- [8.3 Verify Provenance and Integrity (Code Signing, Hashing, SLSA)](domain8/8.3_verify_provenance_integrity.md)
- [8.4 Manage Supplier Risk (Right to Audit, SLAs)](domain8/8.4_manage_supplier_risk.md)
- [8.5 Supply Chain Incident Response (Log4j Mitigation, Containment)](domain8/8.5_supply_chain_incident_response.md)
