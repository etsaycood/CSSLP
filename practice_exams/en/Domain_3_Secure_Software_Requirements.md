# Domain 3: Secure Software Requirements (16 Questions)

#### **1. A business analyst is documenting the requirements for a new e-commerce application. One of the requirements states: "The system shall encrypt all credit card transactions using TLS 1.3." This type of requirement is BEST classified as:**
A. A functional requirement
B. A non-functional security requirement
C. A compliance requirement
D. A functional use case

*   **Answer: B**
*   **Rationale:** "Encrypt all transactions using TLS 1.3" dictates *how* the system should protect data (confidentiality in transit), not the business action the system performs. This is a **non-functional security requirement**. Functional requirements define *what* the system does (e.g., "The system shall process a payment").

#### **2. A multinational corporation is building a cloud-based application that targets customers in the European Union (EU) and California. Which of the following compliance requirements mandates the explicit definition of "Data Collection Scope" and "User Rights (Right to be Forgotten)"?**
A. Payment Card Industry Data Security Standard (PCI DSS)
B. Federal Information Security Management Act (FISMA)
C. General Data Protection Regulation (GDPR)
D. Health Insurance Portability and Accountability Act (HIPAA)

*   **Answer: C**
*   **Rationale:** The **General Data Protection Regulation (GDPR)** directly mandates strict privacy controls, including minimizing the data collection scope and providing EU citizens with the "Right to be Forgotten" (data disposal user rights).

#### **3. During the requirements gathering phase for a healthcare data portal, the data owner decides that patient medical histories are classified as "High Sensitivity" and face a "High Impact" if breached. This process of assigning labels based on sensitivity is known as:**
A. Data Anonymization
B. Data Handling
C. Data Labeling
D. Risk Acceptance

*   **Answer: C**
*   **Rationale:** **Data Labeling** is the act of tagging or marking data with a specific classification level (e.g., "High Sensitivity," "Confidential") based on the impact that unauthorized disclosure, modification, or destruction of the data would have on the organization.

#### **4. An organization is aggregating large datasets of consumer behavior to train a new AI model. To ensure the privacy of individual consumers, the data team mathematically modifies the dataset so that no single record can ever be traced back to the original individual, even if combined with other public datasets. This level of privacy protection is called:**
A. Data Anonymization (Fully Anonymous)
B. Data Handling (Personally Identifiable Information)
C. Pseudo-anonymization
D. Tokenization

*   **Answer: A**
*   **Rationale:** **Fully Anonymous data** has all personally identifiable information permanently and irreversibly removed, making re-identification mathematically impossible. **Pseudo-anonymization** replaces direct identifiers with artificial identifiers (pseudonyms) but retains a cross-reference table that *could* allow re-identification.

#### **5. A financial institution sets a requirement that an automated backend service must access an internal database to generate overnight transaction reports. To fulfill this requirement securely without human intervention, the system architect should specify the use of:**
A. Dedicated User Provisioning
B. Shared user accounts
C. Service accounts
D. Single Sign-On (SSO)

*   **Answer: C**
*   **Rationale:** **Service accounts** are non-human accounts designed specifically for applications, services, or automated backend processes to authenticate and interact with other systems or databases securely without requiring an interactive user login or MFA.

#### **6. A security team is modeling a system to identify how an attacker might attempt to manipulate an input field to execute a SQL injection attack against the backend database. Exploring these adversarial scenarios is establishing:**
A. A functional requirement
B. A misuse/abuse case
C. A data classification schema
D. A compliance matrix

*   **Answer: B**
*   **Rationale:** **Misuse and abuse cases** turn standard use cases upside down to describe how an attacker or malicious insider might interact with a system to exploit vulnerabilities or bypass controls, directly informing the need for mitigating security controls (like input validation).

#### **7. A project manager wants to ensure that every security requirement established at the beginning of the SDLC is accurately designed, fully implemented, and properly tested before the software is released to production. Which artifact is designed EXACTLY for this purpose?**
A. Software Bill of Materials (SBOM)
B. Risk Register
C. Security Requirement Traceability Matrix (SRTM)
D. End-User License Agreement (EULA)

*   **Answer: C**
*   **Rationale:** A **Security Requirement Traceability Matrix (SRTM)** creates a direct, documented linkage tracing every initial security requirement forward through its specific design, implementation code, and final test cases to guarantee that no security controls were dropped or ignored during development.

#### **8. An organization is negotiating to procure a third-party commercial-off-the-shelf (COTS) software package. The security architect insists that the contract must legally dictate the vendor's required uptime, incident response communication timeline, and adherence to secure development frameworks. These stipulations are known as:**
A. Third-party vendor security requirements
B. Open-source licensing constraints
C. Cross-border data residency requirements
D. Functional business use cases

*   **Answer: A**
*   **Rationale:** **Third-party vendor security requirements** (often codified in Service Level Agreements or contract addendums) are essential to mandate how a supplier must securely develop, operate, and maintain the software or service they are selling to the organization.

#### **9. An explicit requirement states: "The application must store user passwords securely and prevent disclosure even if the database is stolen." During the design phase, the architect selects the Argon2 algorithm to satisfy this requirement. Which of the following statements is true regarding this scenario?**
A. The requirement is functional; Argon2 is a misuse case.
B. Argon2 is the non-functional requirement.
C. The requirement is non-functional; Argon2 is the mitigating control.
D. The requirement is a misuse case; Argon2 is a functional use case.

*   **Answer: C**
*   **Rationale:** The objective to store passwords securely is a **non-functional security requirement**. The selection of Argon2 is the technical **mitigating control** chosen by the architects to fulfill that requirement.

#### **10. An application targets military personnel and is required to handle Department of Defense (DoD) unclassified but sensitive data. Consequently, the application design must adhere strictly to Defense Information Systems Agency (DISA) Security Technical Implementation Guides (STIGs). This is an example of identifying which type of requirement?**
A. Privacy requirement
B. Industry-specific compliance requirement
C. Functional business use case
D. End of Life (EOL) policy

*   **Answer: B**
*   **Rationale:** Adhering to DoD guidelines (like DISA STIGs) is an **industry-specific (defense) compliance requirement**. Different verticals (healthcare, finance, military) contain very specific frameworks mapping to their unique risk profiles.

#### **11. A requirement specifies that an employee’s access permissions to a critical financial application must be reviewed by their direct manager every 90 days, and access revoked if no longer needed. This requirement describes the:**
A. Reapproval process
B. Data anonymization process
C. Data labeling scheme
D. Service account provisioning loop

*   **Answer: A**
*   **Rationale:** The **Reapproval process** (or Periodic Access Review / Recertification) guarantees that access privileges do not suffer from "privilege creep" over time, ensuring continued adherence to the principle of least privilege.

#### **12. The data architecture board dictates an application must ensure that audit logs remain available for exactly seven years, after which they must be permanently erased. This requirement is addressing which portion of the data lifecycle?**
A. Data Generation
B. Data Retention and Disposal
C. Data Labeling
D. Data Anonymization

*   **Answer: B**
*   **Rationale:** Deciding how long data is stored before it must be legally or functionally destroyed is defining the **Data Retention and Disposal** phases of the data lifecycle. 

#### **13. To comply with German data sovereignty laws, an organization must specify that the personal data of its German users is physically stored and processed on servers located entirely within the borders of Germany. This introduces which complex privacy requirement?**
A. User marketing preferences
B. Data anonymization
C. Cross-border requirements (Data Residency/Jurisdiction)
D. Service level agreements (SLA)

*   **Answer: C**
*   **Rationale:** **Cross-border requirements**, specifically **data residency** or **data sovereignty**, mandate that data stays within specific geopolitical boundaries to fall solely under local jurisdiction and legal protections, preventing it from being intercepted or requested by foreign powers.

#### **14. When designing a new HR application, the development team documents a scenario outlining an authorized HR employee attempting to alter their own salary field in the database. What kind of case is being documented to ensure a control (Segregation of Duties) is implemented to stop it?**
A. A misuse case outlining an insider threat
B. A functional business requirement
C. A compliance regulatory requirement
D. A data labeling standard

*   **Answer: A**
*   **Rationale:** A scenario exploring an authorized user abusing their rightful access to perform an unauthorized, malicious action is documenting a **misuse/abuse case** focused on an **insider threat**.

#### **15. A requirement demands that a cloud storage platform provide high levels of data resilience and redundancy in the event of an earthquake destroying the primary data center. In terms of the CIA Triad, this requirement is heavily focused on:**
A. Confidentiality
B. Integrity
C. Availability
D. Non-repudiation

*   **Answer: C**
*   **Rationale:** Resilience, redundancy, and disaster recovery requirements are explicitly designed to ensure the continuous **Availability** of the system and its data during adverse events.

#### **16. Before beginning development, a governance committee determines that only the Chief Human Resources Officer possesses the ultimate authority to dictate how employee performance data is classified and who is permitted to access it. In this scenario, the Chief Human Resources Officer has been assigned the role of:**
A. Data Custodian
B. Data Owner
C. System Administrator
D. Service Account

*   **Answer: B**
*   **Rationale:** The **Data Owner** is a senior executive responsible for determining the classification, value, and access rights of the data. The **Data Custodian** (usually IT) is tasked with implementing the technical controls (like encryption or backups) mandated by the Owner.
