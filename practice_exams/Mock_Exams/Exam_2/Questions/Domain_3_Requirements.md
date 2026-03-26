# Exam 2
## Domain 3: Secure Software Requirements (18 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. During a requirements gathering workshop for a new banking portal, a product owner states: "When a user enters an incorrect password three consecutive times, the system must immediately lock the account for 30 minutes to prevent brute-force attacks." How should a security requirements engineer formally classify this specific statement?**
A. It is a Non-functional Security Requirement because it describes an architectural trait rather than a specific system action.
B. It is a Functional Security Requirement because it mandates a very specific, testable behavior and action the software must execute.
C. It is an Abuse Case.
D. It is a Service Level Agreement (SLA).

#### **2. A global e-commerce firm must comply with the GDPR. A former customer submits a formal legal request demanding the complete and total deletion of all their past purchasing history, home addresses, and personal identifiable information (PII) from the firm's databases. Which specific GDPR privacy principle must the software's functional requirements have anticipated to handle this demand?**
A. The Right to Erasure (Right to be Forgotten)
B. Data Portability
C. Pseudo-anonymization
D. Privacy Shield

#### **3. A startup is building a payment gateway application that will process, store, and transmit full Credit Card Primary Account Numbers (PAN) and CVV codes. To legally operate and process payments, the software's database architecture and security requirements must strictly adhere to which global industry security mandate?**
A. Health Insurance Portability and Accountability Act (HIPAA)
B. Payment Card Industry Data Security Standard (PCI-DSS)
C. Sarbanes-Oxley Act (SOX)
D. Federal Information Security Management Act (FISMA)

#### **4. A security architect is leading a Threat Modeling session using the STRIDE methodology. The team identifies a scenario where a hacker intercepts an unencrypted data packet containing a user's salary and modifies the number from `$50,000` to `$90,000` before it reaches the backend database. Which specific STRIDE threat category does this scenario represent?**
A. Spoofing
B. Repudiation
C. Tampering
D. Elevation of Privilege

#### **5. An enterprise wants to adopt a threat modeling framework that is heavily aligned with business impact, organizational risk, and attacker motives, rather than just focusing purely on technical software flaws. They choose a robust, seven-step, risk-centric methodology. Which specific threat modeling framework did they select?**
A. DREAD
B. OCTAVE
C. PASTA (Process for Attack Simulation and Threat Analysis)
D. CVSS

#### **6. The development team uses the DREAD model to prioritize a newly discovered vulnerability in a legacy app. The team gives it a high score for "Damage Potential" and "Reproducibility." However, they determine that to actually exploit the flaw, the attacker would need physical access to the server room and an extremely rare, specialized supercomputer. Therefore, which DREAD category will receive a very LOW score, significantly driving down the overall risk rating?**
A. Discoverability
B. Affected Users
C. Exploitability
D. Damage

#### **7. While capturing requirements for a shopping cart module, an AppSec engineer writes a detailed persona scenario explaining exactly how a malicious user might attempt to completely bypass the checkout logic by manipulating hidden HTML form fields to change an item's price to `$0.00`. What is the formal industry term for this type of negative requirement documentation?**
A. Positive Use Case
B. Security Traceability Matrix
C. Abuse Case (or Misuse Case)
D. Software Bill of Materials (SBOM)

#### **8. Before selecting encryption protocols for a new heavily integrated database, the enterprise compliance team mandates a formal "Data Classification" exercise for all incoming fields. From a requirements engineering perspective, why is performing Data Classification considered a mandatory FIRST step before writing specific security controls?**
A. It allows the database to run faster.
B. Because assigning a classification level (e.g., Public vs. Top Secret / PII) directly dictates the strictness, legal necessity, and cost of the security controls (like encryption strength) that must be applied to that specific data element.
C. It ensures that the software is written in a modern language like Python.
D. It prevents Denial of Service (DoS) attacks.

#### **9. A medical software company is designing a new remote patient portal. The requirements specify that patient medical records, session notes, and prescription history must be encrypted both at rest (AES-256) and in transit (TLS 1.3). If the tool is sold in the United States, which federal regulation legally drives these severe privacy and security requirements?**
A. GDPR
B. HIPAA (Health Insurance Portability and Accountability Act)
C. PCI-DSS
D. COPPA (Children’s Online Privacy Protection Act)

#### **10. The business owner insists on launching a newly developed feature by Friday, even though the security team warns that the feature lacks rate-limiting and is highly vulnerable to automated credential stuffing attacks. The CEO signs a formal document deciding to launch the feature anyway and explicitly accepts the potential financial loss of an attack. What risk management concept describes this executive decision?**
A. Risk Mitigation
B. Risk Transference
C. Risk Acceptance (based on organizational Risk Appetite)
D. Risk Avoidance

#### **11. To ensure that a critical cloud hosting provider mathematically guarantees the enterprise database cluster will remain online and accessible 99.99% of the year (supporting Availability requirements), what specific legal/contractual requirement document must be established during the procurement phase?**
A. Non-Disclosure Agreement (NDA)
B. Service Level Agreement (SLA)
C. EULA (End User License Agreement)
D. Data Processing Agreement (DPA)

#### **12. A massive government software requirements document lists over 500 different highly specific security controls. How can the project manager mathematically and procedurally ensure that every single one of those 500 security requirements is actually built by the developers and successfully verified by the QA testers before launch?**
A. By trusting the developers to remember them.
B. By running a single DAST scan at the end.
C. By creating and strictly maintaining a Security Requirements Traceability Matrix (SRTM).
D. By reviewing the code manually over a weekend.

#### **13. During a STRIDE threat modeling analysis of an API, the team realizes that an attacker could easily guess another user's sequential session ID token (e.g., moving from `Session=101` to `Session=102`) and literally "take over" their active session, pretending to be them. Which STRIDE threat is this, and what is the standard architectural requirement to mitigate it?**
A. Information Disclosure; Mitigate by encrypting the database.
B. Spoofing; Mitigate by enforcing strong authentication and issuing massive, cryptographically randomized Session IDs.
C. Repudiation; Mitigate by adding digital signatures.
D. Denial of Service; Mitigate by adding a Web Application Firewall.

#### **14. A development team is required to adhere to SOX (Sarbanes-Oxley Act) because they are building an internal accounting application for a publicly traded company. Which of the following software requirements would be MOST directly driven by strict SOX compliance?**
A. Requirements establishing immutable audit trails, strict segregation of duties, and irrefutable internal controls over who can modify financial reporting data.
B. Requirements ensuring that credit card numbers are masked on the screen.
C. Requirements guaranteeing that medical records are anonymized.
D. Requirements forcing passwords to have special characters.

#### **15. In modern privacy engineering, a new mobile game application prompts users to grant access to their exact GPS location 24/7, even though the game is a simple offline Solitaire app that never uses location data for its core functionality. This requirement blatantly violates which core privacy principle?**
A. Data Portability
B. Data Minimization (Collection Limitation)
C. Right to Rectification
D. Cryptographic Hashing

#### **16. A company is exporting its software services to the European Union (EU). The legal team mandates a strict architectural requirement: "Under no circumstances may database records concerning an EU citizen be physically replicated, backed up, or stored on server hardware located outside the geographic borders of the EU." What data protection and compliance concept does this requirement directly enforce?**
A. Data Sovereignty / Data Localization
B. Data Masking
C. Transborder Threat Modeling
D. Network Microsegmentation

#### **17. A tier-1 financial system is designed so that if the primary trading database experiences a catastrophic hardware failure, all trading traffic is instantly and seamlessly redirected to a geographically distant "hot standby" database without any users noticing a drop in service. This functional architectural requirement primarily supports which pillar of the CIA triad?**
A. Confidentiality
B. Integrity
C. Availability
D. Non-repudiation

#### **18. During the early requirements gathering phase, the development team realizes they lack the mathematical expertise to build their own custom cryptography module. Instead, they write a requirement to formally purchase and integrate a vetted, third-party FIPS-140-2 compliant Hardware Security Module (HSM). By shifting the burden and liability of cryptographic correctness to a specialized vendor, what formal Risk Treatment strategy is the team employing?**
A. Risk Avoidance
B. Risk Acceptance
C. Risk Mitigation
D. Risk Transference
