# Exam 3
## Domain 3: Secure Software Requirements (18 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A business analyst is gathering requirements for a new cloud-based payroll system. The HR director states, "The system must process payroll for 10,000 employees within a 2-hour window every Friday." The Chief Security Officer (CSO) immediately interjects, "However, the system must definitively reject any user attempt to download the master salary listing if they are not physically connected to the company's internal VPN." What specific types of requirements have the HR director and the CSO just defined, respectively?**
A. Both are Functional Requirements.
B. HR Director: Functional Requirement; CSO: Functional Security Requirement.
C. HR Director: Non-Functional Requirement; CSO: Misuse Case.
D. HR Director: Performance Requirement (Non-Functional); CSO: Security Requirement / Access Control Requirement.

#### **2. During a massive brainstorming session for a new self-driving car's software, the engineering team creates detailed diagrams mapping out how a hacker might attempt to spoof GPS signals to force the car to drive off a cliff, or how someone might inject malicious code via the Bluetooth infotainment system to disable the brakes. They then systematically document these attack vectors to ensure defensive mechanisms are built to counter them. What specific requirements engineering technique is the team actively employing?**
A. Normal Use Case Modeling
B. Misuse Case / Abuse Case Modeling
C. Policy Elicitation
D. Continuous Integration

#### **3. A development team is preparing to build a new B2B (Business-to-Business) payment API. To identify exactly what mandatory security controls must be engineered into the API, the team methodically analyzes the Data Protection Act, the industry-specific Payment Card Industry Data Security Standard (PCI-DSS), and the specific Service Level Agreements (SLAs) historically signed with their largest enterprise clients. Which critical activity within the Requirements phase is the team performing?**
A. Penetration Testing
B. Code Obfuscation Analysis
C. Security Policy and Compliance Analysis (Elicitation)
D. Source Code Review

#### **4. A project manager documents the following requirement for a new healthcare application: "The application shall ensure the Confidentiality of patient data." The Lead Security Architect immediately rejects this requirement as fundamentally broken and sends it back to the business analyst for a complete rewrite. According to the core principles of writing effective security requirements, what is the primary, fatal flaw in this stated requirement?**
A. It is too specific and restricts the developer's creativity.
B. It is overly technical and uses confusing jargon.
C. It completely lacks testability, measurable criteria, and specificity (It is vague).
D. It focuses on Availability instead of Confidentiality.

#### **5. A new digital banking application allows users to transfer funds. During the requirements definition phase, the security team mandates a specific scenario: "When the system detects a user attempting to transfer an amount exceeding their established daily risk profile, or if the transfer destination is a known high-risk international blacklist IP, the system MUST automatically freeze the transaction, trigger an alert to the fraud department, and prompt the user for biometric step-up authentication." What specific artifact is the team creating to document this critical anti-fraud logic?**
A. A Data Flow Diagram (DFD)
B. A Software Bill of Materials (SBOM)
C. A Security Misuse Case or Security Use Case
D. A Static Application Security Testing (SAST) rule

#### **6. An enterprise is migrating its physical data center to AWS. The legal department informs the engineering team that due to the specific European privacy laws governing their customers, the software application must absolutely guarantee that no database instances physically reside outside the borders of the European Union, and that any cloud provider administrators attempting to access the underlying storage servers must be flagged and blocked. Which specific category of security requirements is the legal team unilaterally imposing on the software architecture?**
A. Functional Requirements
B. Data Retention Requirements
C. Regulatory and Data Sovereignty (Data Residency) Compliance Requirements
D. Performance (Non-Functional) Requirements

#### **7. A systems engineer is categorizing various data types that a proposed human resources application will collect and process. The data dictionary includes items like: Employee Home Address, Personal Phone Number, Social Security Number, and Medical History. The engineer mathematically maps each of these specific data fields to a "High" confidentiality requirement because standard definitions mandate extreme protection for exactly this type of sensitive identifying information. What universally recognized acronym represents this specific category of highly protected data?**
A. DRM (Digital Rights Management)
B. PII (Personally Identifiable Information) / PHI (Protected Health Information)
C. SBOM (Software Bill of Materials)
D. API (Application Programming Interface)

#### **8. In the context of establishing foundational security requirements, an organization decides to implement a strict "Data Classification Policy." They define three tiers: Public, Internal, and Confidential. What is the fundamental, primary purpose of performing this categorization exercise before designing the software's access controls and encryption mechanisms?**
A. To guarantee that all data is encrypted using military-grade AES-256.
B. To ensure that expensive, heavy security controls are proportionately applied ONLY to the data that actually warrants that level of protection, rather than blindly wasting money locking down worthless public data (applying appropriate levels of protection based on risk/value).
C. To prevent the application from crashing.
D. To satisfy the requirement for a Web Application Firewall (WAF).

#### **9. A business analyst uses a technique where they physically sit next to the customer service representatives taking phone calls, observing over their shoulder exactly how they currently navigate the legacy green-screen terminal system to reset a user's password. The analyst notices many reps write passwords on sticky notes because the current system's timeout is too short, revealing a massive security flaw in the workflow. The analyst then uses these real-world observations to draft better, more secure workflow requirements for the new system. What requirement elicitation technique is the analyst using?**
A. JAD (Joint Application Design) Sessions
B. Questionnaires and Surveys
C. Observation / Ethnographic Study (Shoulder Surfing in a safe context)
D. Reverse Engineering

#### **10. An architect is reviewing the requirements for a new military communications application. The document specifies that the application must guarantee exactly three core properties: 1. No unauthorized person can read the messages. 2. Neither the sender nor receiver can falsely deny having sent or received a specific message. 3. The system must cryptographically prove that the message was absolutely not tampered with in transit. Which three specific security requirements are being mandated here?**
A. Availability, Non-repudiation, Confidentiality
B. Confidentiality, Non-repudiation, Integrity
C. Authentication, Authorization, Accounting (AAA)
D. Least Privilege, Separation of Duties, Defense in Depth

#### **11. A requirement states: "The software must incorporate an automated mechanism to continuously scan the public internet for exposed credentials belonging to our employees, and if found, automatically enforce a global password reset for those compromised accounts." This requirement is a proactive defense mechanism directly mapped to mitigating which specific, pervasive threat actor strategy?**
A. Cross-Site Scripting (XSS)
B. Distributed Denial of Service (DDoS)
C. Credential Stuffing / Password Reuse attacks based on compromised external breaches
D. SQL Injection

#### **12. A development team is tasked with writing the software for an automated ATM machine. They define a strict matrix. Row 1: "User" (can withdraw funds, can check balance). Row 2: "Bank Teller" (can restock cash, cannot withdraw funds). Row 3: "Global Admin" (can update ATM firmware, can reboot machine). By formally mapping specific roles to their exact, allowed positive actions before any code is written, what essential security requirement artifact is the team creating?**
A. A Threat Model Data Flow Diagram
B. A Key Risk Indicator (KRI) report
C. A Role-Based Access Control (RBAC) Requirements / Access Control Matrix
D. A Privacy Impact Assessment (PIA)

#### **13. During a requirements workshop, the stakeholders declare: "The application must be available 99.9% of the time, even during peak holiday shopping seasons, and must be able to recover from a complete database catastrophic failure within 4 hours without losing any committed transactions." This critical statement explicitly dictates which two specific types of non-functional operational requirements?**
A. Authentication and Authorization
B. Availability (Uptime SLA) and Disaster Recovery (specifically Recovery Time Objective [RTO] / Recovery Point Objective [RPO])
C. Confidentiality and Integrity
D. Usability and Maintainability

#### **14. A global retail company is building a mobile application that will explicitly track the real-time, physical GPS location of children under the age of 13 to help parents locate them in large shopping malls. Before technical architecture can even begin, the legal and compliance team halts the project, stating the team must first conduct a massive, formal, legally required evaluation to determine how this extremely sensitive tracking data will be collected, stored, shared with third parties, and eventually deleted, to ensure it doesn't violate laws like COPPA. What specific type of formal analysis is being demanded?**
A. Open Source Software (OSS) License Audit
B. Privacy Impact Assessment (PIA) / Data Protection Impact Assessment (DPIA)
C. Dynamic Application Security Testing (DAST)
D. Code Quality Review

#### **15. A requirement dictates: "When the application writes sensitive passwords to the backend database, it must NEVER use irreversible hashing algorithms, because the legacy mainframe billing system requires retrieving the actual, plain-text password to authenticate the user for billing cycles." A security engineer immediately flags this requirement as incredibly dangerous and fundamentally violating modern security best practices. However, because it is a hard business requirement driven by legacy systems, what specific type of requirement conflict is occurring?**
A. Financial Conflict
B. A conflict between a Business/Functional Requirement (need cleartext for legacy integration) and a Security Requirement (passwords must be hashed).
C. Regulatory Conflict
D. Usability Conflict

#### **16. To ensure a new e-commerce website cannot be successfully crippled by thousands of malicious attacker-controlled computers sending junk traffic to exhaust the server's resources, the requirements specify: "The system must utilize a specialized cloud-based traffic scrubbing service capable of automatically filtering and dropping millions of malicious junk requests per second before they reach our origin servers." This requirement is engineered precisely to mitigate which specific type of attack?**
A. Cross-Site Request Forgery (CSRF)
B. Phishing
C. Distributed Denial of Service (DDoS)
D. Advanced Persistent Threat (APT) exfiltration

#### **17. A team is using the STRIDE threat modeling framework early in the requirements phase to brainstorm potential security requirements. They are analyzing a hypothetical attack where a hacker intercepts the unencrypted network communication between the mobile app and the server, and stealthily changes a user's transfer amount from $10 to $10,000 without either party realizing until it's too late. Which specific letter in the STRIDE acronym does this exact attack represent, directly driving the requirement for TLS encryption?**
A. S - Spoofing
B. T - Tampering
C. R - Repudiation
D. E - Elevation of Privilege

#### **18. An organization is bidding on a contract to develop a web application for the US Department of Defense. The Request for Proposal (RFP) strictly states that the software MUST be evaluated and certified according to the rigorous standards of the Common Criteria for Information Technology Security Evaluation (ISO/IEC 15408). To meet this standard, the vendor must create a highly formalized, 100-page document precisely defining the unique security threats the software will face, the environment it operates in, and the specific security objectives it aims to achieve. What is the official name of this required Common Criteria document?**
A. Service Level Agreement (SLA)
B. End User License Agreement (EULA)
C. Protection Profile (PP) / Security Target (ST)
D. Software Bill of Materials (SBOM)
