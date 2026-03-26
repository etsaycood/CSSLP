# Exam 4
## Domain 3: Secure Software Requirements (18 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A business analyst is writing user stories for a new payroll application. They write: "As an HR manager, I want to be able to export employee salary data to CSV so I can generate reports." From a security perspective, what critical element is missing from this requirement that represents an "Abuse Case" or "Evil User Story"?**
A. The specific SQL query needed to extract the data.
B. A corresponding story defining what *cannot* or *should not* happen (e.g., "As a malicious insider, I want to export data for employees outside my department, which the system must prevent").
C. The exact mathematical encryption algorithm (e.g., AES-256-GCM) to be used for the CSV file.
D. The precise UI button design for the "Export" function.

#### **2. A development team is tasked with building a healthcare application that must comply with the Health Insurance Portability and Accountability Act (HIPAA). The product owner asks the security architect how to translate the massive HIPAA legal textbook into actionable software tasks. Which statement best describes the relationship between Compliance, Security Policies, and Software Requirements?**
A. Compliance regulations directly generate ready-to-code functional software requirements.
B. Compliance regulations inform organizational Security Policies, which are then translated into specific, verifiable Security Requirements for the software.
C. Software Requirements dictate the organizational Security Policies, which lawmakers then use to write Compliance regulations.
D. Development teams should ignore high-level Compliance regulations and only focus on technical OWASP guidelines.

#### **3. During the requirements gathering phase for a new e-commerce platform, the team decides that user sessions must automatically expire after 15 minutes of inactivity to prevent session hijacking if a user walks away from a public computer. How should this constraint be formally classified?**
A. As a Functional Requirement.
B. As a Non-Functional Requirement (NFR).
C. As an Abuse Case.
D. As a Service Level Agreement (SLA).

#### **4. A project team is defining the Data Retention Policy for a new customer service portal. The business wants to keep chat logs "forever" to train future AI models. The privacy officer states that under GDPR, chat logs containing personal data can only be kept as long as necessary for the original purpose of customer support (e.g., 90 days). How should the lead architect resolve this conflict during the requirements phase?**
A. Implement the business requirement ("keep forever") because AI training is critical to the company's future revenue.
B. Implement the privacy requirement ("delete after 90 days") because legal and regulatory compliance mandates supersede conflicting business desires to hoard data.
C. Ask the developers to decide during the sprint planning phase.
D. Keep the data forever, but encrypt it, as encrypted data is completely exempt from GDPR retention rules.

#### **5. When defining Access Control requirements for a military intelligence application, the requirement states: "A subject may only read an object if the subject's clearance level is strictly greater than or equal to the object's classification level." Which formal Access Control Model does this requirement describe?**
A. Discretionary Access Control (DAC)
B. Role-Based Access Control (RBAC)
C. Mandatory Access Control (MAC) / Bell-LaPadula
D. Attribute-Based Access Control (ABAC)

#### **6. A team is developing a B2B API service. The requirement states: "The API must authenticate the client application, not the individual human user." Furthermore, the client must be able to periodically request a new, short-lived access token without requiring human interaction. Which standard protocol is the absolute best fit for fulfilling this specific security requirement?**
A. SAML 2.0
B. OAuth 2.0 (specifically the Client Credentials Grant flow)
C. OpenID Connect (OIDC)
D. HTTP Basic Authentication

#### **7. To fulfill a "Non-Repudiation" security requirement for high-value financial transactions, which of the following mechanisms MUST be explicitly defined in the requirements documentation?**
A. The use of Symmetric Encryption (e.g., AES) for all database fields.
B. The use of Digital Signatures (Asymmetric Cryptography) where the sender signs the transaction with their Private Key.
C. The enforcement of two-factor authentication (2FA) during login.
D. The implementation of a Web Application Firewall (WAF) to log all incoming HTTP headers.

#### **8. A software architect is analyzing the security requirements for an IoT (Internet of Things) temperature sensor intended for agricultural use. The sensor has 16KB of RAM and an extremely low-power 8-bit microcontroller. The product manager demands that the sensor use TLS 1.3 with an RSA 4096-bit certificate to transmit data to the cloud. What is the fatal flaw in the product manager's requirement?**
A. RSA 4096-bit is no longer considered secure by NIST.
B. It violates the constraint of the operational environment; the IoT device lacks the computational power and memory to perform heavy asymmetric cryptographic handshakes like RSA 4096.
C. TLS 1.3 only supports UDP traffic, but IoT devices require TCP.
D. The requirement does not specify the color of the IoT device's casing.

#### **9. During a threat modeling session in the requirements phase, the team identifies that an attacker might try to exhaust the server's CPU by repeatedly submitting incredibly complex, deeply nested JSON payloads to the search API. Which countermeasure should be documented as a functional security requirement to mitigate this Denial of Service (DoS) threat?**
A. The application shall encrypt all incoming JSON payloads using AES-256 before processing.
B. The application shall implement input validation to enforce a strict maximum depth limit and maximum size limit for all incoming JSON payloads.
C. The application shall require users to change their passwords every 30 days.
D. The application shall store all database backups in an off-site location.

#### **10. A multinational company is building a cloud storage solution. The EU legal team dictates a strict requirement: "Data belonging to citizens of the European Union must be physically stored on servers located within the geopolitical boundaries of the EU." What specific type of compliance and legal requirement is this?**
A. Data Portability
B. Data Residency (Data Sovereignty)
C. Data Masking
D. Safe Harbor

#### **11. According to OWASP, which of the following is an example of an effectively written, testable Security Requirement?**
A. "The application must be completely secure against all hacker attacks."
B. "The application shall use industry-standard encryption."
C. "The application shall lock the user account for 15 minutes after 5 consecutive failed login attempts within a 5-minute window."
D. "The application should have a strong password policy."

#### **12. A company requires a Single Sign-On (SSO) solution for its internal web applications. The requirement states: "When an employee logs into the central portal, they must be seamlessly logged into WebApp_A and WebApp_B without entering their credentials again. The applications rely on XML-based assertions to exchange this identity information." Which technology is the requirement describing?**
A. OAuth 2.0
B. SAML (Security Assertion Markup Language)
C. LDAP (Lightweight Directory Access Protocol)
D. JWT (JSON Web Tokens)

#### **13. When defining requirements for "Data Masking," a business stakeholder requests that customer credit card numbers be stored in the database but completely obscured when viewed by customer service representatives, showing only the last 4 digits (e.g., `****-****-****-1234`). Which of the following is true regarding this requirement?**
A. Data Masking is a form of strong, irreversible cryptographic hashing.
B. Data Masking is a presentation-layer control designed to protect confidentiality from unauthorized viewing; the underlying data in the database remains intact and usable by authorized backend processes.
C. Data Masking perfectly fulfills the requirement for "Data at Rest Encryption."
D. Masked data can be easily unmasked by the frontend browser using JavaScript.

#### **14. A risk assessment identifies that highly privileged administrators might abuse their power to modify audit logs and cover their tracks. To mitigate this, a requirement is drafted: "The application's audit logs must be immediately transmitted to a centralized, isolated, write-once-read-many (WORM) logging server." Which security concept does this requirement directly support?**
A. Availability
B. Non-Repudiation and Accountability
C. Authentication
D. Least Privilege

#### **15. A development team is tasked with building a web application that handles sensitive payment card data. They must adhere to the Payment Card Industry Data Security Standard (PCI-DSS). Which of the following statements about incorporating PCI-DSS into software requirements is correct?**
A. PCI-DSS is a guideline; developers can choose to ignore requirements if they slow down the Agile sprint.
B. PCI-DSS requirements (like encrypting cardholder data and not storing CVV codes) must be explicitly translated into verifiable software requirements to achieve compliance and pass the mandatory audit.
C. As long as the production servers have a firewall, the application code itself does not need to worry about PCI-DSS requirements.
D. PCI-DSS only applies to the hardware infrastructure, not to the software development lifecycle.

#### **16. When gathering privacy requirements for a new mobile application that targets children under 13 in the United States, which specific federal regulation MUST be analyzed to dictate restrictions on data collection, parental consent, and data sharing?**
A. GDPR (General Data Protection Regulation)
B. HIPAA (Health Insurance Portability and Accountability Act)
C. COPPA (Children's Online Privacy Protection Act)
D. SOX (Sarbanes-Oxley Act)

#### **17. A security architect is defining requirements for protecting "Data in Transit" for a new public-facing API. Which of the following is the MOST appropriate technical requirement to specify?**
A. "All API endpoints shall require mutual TLS (mTLS) authentication for all external mobile app users."
B. "The API shall encrypt all responses using a proprietary substitution cipher before transmitting."
C. "The API must only be accessible over HTTPS using TLS v1.2 or higher, with strong cipher suites enabling Forward Secrecy, and enforce HTTP Strict Transport Security (HSTS)."
D. "The API shall hash all traffic using MD5 before sending it over the network."

#### **18. In the context of secure software requirements, what is the primary purpose of defining a "Subject" and an "Object"?**
A. To define the relationship between the database tables (Objects) and the foreign keys (Subjects).
B. To establish the foundational vocabulary for Access Control Requirements, where the Subject (e.g., a user, a process) is the active entity requesting access, and the Object (e.g., a file, a database record) is the passive entity being accessed.
C. To specify the frontend UI components (Subjects) and the backend API endpoints (Objects).
D. To differentiate between the person buying the software (Subject) and the developer writing it (Object).
