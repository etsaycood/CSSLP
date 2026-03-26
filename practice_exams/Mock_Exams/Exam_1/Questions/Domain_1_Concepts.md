# Exam 1
## Domain 1: Secure Software Concepts (16 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A critical legacy web application handles real-time financial trading. The development team is tasked with implementing a new feature that temporarily elevates a user's privileges to bypass standard transaction limits during market volatility. The security team is concerned that this mechanism could fail open if the supporting authorization microservice crashes. As a secure software designer, what is the FIRST principle you should enforce to address this specific concern?**
A. Implement Complete Mediation to ensure the bypass authorization is checked on every single trade request.
B. Ensure the mechanism follows the Fail Secure principle by defaulting to standard transaction limits if the microservice is unresponsive.
C. Apply the Least Common Mechanism principle by isolating the bypass service on a dedicated server.
D. Enforce Separation of Duties by requiring two different executives to approve the temporary elevation.

#### **2. A multinational healthcare provider is designing a patient portal. The marketing department insists on collecting and indefinitely retaining detailed user browsing behavior to personalize health product recommendations. The Legal/Compliance department points out that under GDPR and HIPAA, patients must give explicit consent and have the right to request deletion of this non-essential data. The Chief Information Security Officer (CISO) is brought in to arbitrate. What is the fundamental Governance, Risk, and Compliance (GRC) concept that dictates the CISO's decision?**
A. Business alignment dictates that revenue-generating marketing initiatives take precedence over internal policies.
B. Risk Avoidance requires that the portal does not collect any browsing data whatsoever.
C. Legal and Regulatory compliance requirements supersede internal business goals and desires.
D. The psychological acceptability of the portal will be reduced if users are burdened with consent forms.

#### **3. An architect is designing a heavily encrypted storage system for a government contractor. The objective is to ensure that even if the source code of the proprietary encryption software is stolen by a nation-state attacker, the encrypted data remains entirely secure. The architect decides against writing a custom obfuscation algorithm and instead utilizes standard AES-256 in GCM mode. This architectural decision is primarily driven by which established security principle?**
A. Defense in Depth
B. Economy of Mechanism
C. Open Design
D. Leveraging Existing Components

#### **4. You are evaluating a proposal for a new Identity and Access Management (IAM) service. The vendor claims their system employs "Zero Trust architecture." To substantiate this claim, the system mandates that every single data access request—even from previously authenticated users originating from within the corporate LAN—must be explicitly verified against current authorization policies. Which core security design principle is this system actively demonstrating?**
A. Least Privilege
B. Complete Mediation
C. Separation of Duties
D. Non-repudiation

#### **5. A financial software development team is performing a quantitative risk analysis on a newly discovered vulnerability in their payment gateway. They estimate the vulnerability could be exploited once a year (ARO = 1.0). If exploited, the breach would cost the company $500,000 in fines and lost revenue (SLE = $500,000). A proposed Web Application Firewall (WAF) rule could mitigate this vulnerability completely, but the enterprise WAF license and maintenance cost $600,000 annually. Based strictly on quantitative risk management, what is the BEST recommendation?**
A. Implement the WAF rule immediately because the Single Loss Expectancy (SLE) is unacceptably high.
B. Accept the risk, as the Annualized Loss Expectancy (ALE) is lower than the cost of the control.
C. Transfer the risk by purchasing cybersecurity insurance, regardless of the premium cost.
D. Mitigate the risk using the WAF, as protecting financial data supersedes cost-benefit analyses.

#### **6. A development team lead notices that developers are routinely hardcoding database credentials directly into the application's source code to speed up local testing. When confronted, the developers state that setting up a secure local secrets manager takes too much time and breaks their workflow. The team lead decides to implement an automated script that securely injects lightweight, temporary database credentials into the developers' environments upon startup without any manual configuration. Which security design principle is the team lead primarily honoring?**
A. Fail Secure
B. Psychological Acceptability
C. Open Design
D. Least Common Mechanism

#### **7. An organization processes millions of highly sensitive biometric records. To enhance security, the architecture mandates that the front-end web tier is completely physically and logically separated from the back-end database tier. The tiers are separated by a strict firewall, an API gateway, and an Intrusion Prevention System (IPS). An attacker who manages to compromise the web tier cannot directly access the database. Which architectural concept does this best represent?**
A. Defense in Depth
B. Complete Mediation
C. Component Reuse
D. Separation of Duties

#### **8. A software development firm has recently acquired a smaller startup. The startup's flagship application is highly profitable but consists of overly complex, monolithic, "spaghetti" code that has not been securely maintained. The acquiring firm decides to isolate this legacy application on a segregated virtual network and restricts access to it, rather than attempting to review, refactor, and patch the millions of lines of complex code. This decision is predominantly an acknowledgment of which security principle?**
A. Open Design
B. Fail Safe Defaults
C. Economy of Mechanism
D. Complete Mediation

#### **9. During the design of a globally distributed ledger system, architects realize that because all nodes are equally privileged and lack a central authority, an attacker compromising a small number of nodes could inject fraudulent ledgers. To combat this, they design a consensus algorithm that relies on cryptographic hashing and requires a mathematical proof-of-work from a majority of nodes to validate any transaction. What is the fundamental security requirement this design is trying to achieve?**
A. Availability
B. Confidentiality
C. Non-repudiation
D. Integrity

#### **10. A cloud-native application uses a microservices architecture. Service A (Inventory) frequently requests data from Service B (Pricing). Originally, both services shared the same physical memory space on a monolithic server. Now, they communicate over an internal API. An architect discovers that a vulnerability in Service A is being used to conduct a Denial of Service (DoS) attack, exhausting the shared Redis cache that both Service A and Service B use to store temporary data, taking both services offline. What design principle was violated here?**
A. Defense in Depth
B. Least Common Mechanism
C. Fail Secure
D. Open Design

#### **11. An enterprise creates an Acceptable Use Policy (AUP) that forbids developers from using external, unvetted generative AI tools to write code for the company's proprietary trading algorithms. A developer inadvertently uploads a highly confidential algorithm to a public AI chatbot to debug an error. This incident represents a failure in which aspect of the CIA triad, and what is the classification of the countermeasure that failed?**
A. Confidentiality; Administrative Control
B. Integrity; Technical Control
C. Availability; Physical Control
D. Confidentiality; Technical Control

#### **12. A CISO is reviewing a risk assessment for a new legacy system migration. The assessment identifies an outdated, unpatchable protocol in use that carries a "High" risk rating due to known exploits. Because the system is critical to production line stability, the CISO decides the company cannot simply turn it off (avoidance). Furthermore, no insurance company will cover a known vulnerability (transference). Management signs a formal memo acknowledging they will absorb the financial impact if a breach occurs, while the IT team builds a 2-year plan to replace the system. Which risk treatment strategy has been adopted?**
A. Risk Mitigation
B. Risk Acceptance
C. Risk Avoidance
D. Risk Transference

#### **13. A biometric access system is engineered for a high-security military laboratory. The designers explicitly configure the system to prioritize denying access to legitimate personnel if there is even strict minor deviation in the biometric scan (e.g., a dirty finger), rather than risk allowing an unauthorized impostor inside. In biometric terminology, this design deliberately accepts a high:**
A. False Acceptance Rate (FAR)
B. Crossover Error Rate (CER)
C. False Rejection Rate (FRR)
D. Clipping Level

#### **14. User provisioning for an internal corporate web portal is automated. When an active directory user is placed into the `IT_Admins` group, they automatically receive administrative capabilities within the web portal via a nightly synchronization script. An auditor discovers that when a user is demoted and removed from the `IT_Admins` group, their administrative rights in the web portal are *not* automatically revoked because the synchronization script only handles additions, not deletions. This violates which foundational security principle?**
A. Need to Know
B. Defense in Depth
C. Separation of Duties
D. Least Privilege

#### **15. A software organization adopts a policy that states: "Whenever a data field is no longer required to support a valid business transaction or legal retention mandate, it must be permanently purged from all production databases and backups within 30 days." This policy directly addresses which aspect of information lifecycle management?**
A. Data Classification
B. Data Disposal
C. Data Archiving
D. Data Collection Minimization

#### **16. An application developer implements a "Remember Me" functionality. Instead of storing the user's secure password in a cookie, the developer generates a random, cryptographically strong token, stores its hash in the backend database, and places the plaintext token in a browser cookie. This implementation strategy specifically mitigates the risk of exposing the original credential. Which principle does this implementation represent?**
A. Tokenization
B. Encryption
C. Economy of Mechanism
D. Complete Mediation
