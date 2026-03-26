# Exam 1 - Domain 1: Secure Software Concepts (16 Questions)

**Weighting:** 13% of the exam (~16 questions)
**Style:** Highly realistic, scenario-based, BEST/FIRST decisions, with detailed distractor analysis.

---

#### **1. A critical legacy web application handles real-time financial trading. The development team is tasked with implementing a new feature that temporarily elevates a user's privileges to bypass standard transaction limits during market volatility. The security team is concerned that this mechanism could fail open if the supporting authorization microservice crashes. As a secure software designer, what is the FIRST principle you should enforce to address this specific concern?**
A. Implement Complete Mediation to ensure the bypass authorization is checked on every single trade request.
B. Ensure the mechanism follows the Fail Secure principle by defaulting to standard transaction limits if the microservice is unresponsive.
C. Apply the Least Common Mechanism principle by isolating the bypass service on a dedicated server.
D. Enforce Separation of Duties by requiring two different executives to approve the temporary elevation.

*   **Correct Answer:** B
*   **[Explanation Logic]**
    *   **Why B is the FIRST/BEST choice:** The scenario explicitly highlights a concern about the authorization microservice "crashing" (a failure state) and the system potentially "failing open" (defaulting to granting the bypass). The **Fail Secure** (or Fail Safe) principle dictates that when a system or component fails, it must revert to a secure state. In this context, the secure state is undeniably denying the privilege elevation and enforcing the standard, lower limits.
    *   **Why A is a Distractor:** Complete Mediation (A) is technically correct in that all requests must be checked. However, it does not explicitly dictate *what* happens when the checking mechanism itself goes offline. It addresses the "always check" requirement, not the "how to handle failure" requirement.
    *   **Why D is a Distractor:** Separation of Duties (D) is a strong business control for approving the bypass, and is technically a best practice for high-risk actions. However, the scenario's immediate technical concern is system failure behavior ("fail open if the microservice crashes"), making Fail Secure the primary design principle to apply.
    *   **Why C is a Distractor:** Least Common Mechanism (C) advocates for minimizing shared resources to prevent cross-contamination or denial-of-service, which doesn't directly solve the failure-state logic of this specific authorization check.

#### **2. A multinational healthcare provider is designing a patient portal. The marketing department insists on collecting and indefinitely retaining detailed user browsing behavior to personalize health product recommendations. The Legal/Compliance department points out that under GDPR and HIPAA, patients must give explicit consent and have the right to request deletion of this non-essential data. The Chief Information Security Officer (CISO) is brought in to arbitrate. What is the fundamental Governance, Risk, and Compliance (GRC) concept that dictates the CISO's decision?**
A. Business alignment dictates that revenue-generating marketing initiatives take precedence over internal policies.
B. Risk Avoidance requires that the portal does not collect any browsing data whatsoever.
C. Legal and Regulatory compliance requirements supersede internal business goals and desires.
D. The psychological acceptability of the portal will be reduced if users are burdened with consent forms.

*   **Correct Answer:** C
*   **[Explanation Logic]**
    *   **Why C is the BEST choice:** In the hierarchy of GRC (Governance, Risk, and Compliance), **Regulatory and Legal requirements** are absolute and non-negotiable. They always supersede internal business desires or marketing strategies. Failure to comply with GDPR or HIPAA results in severe legal penalties and loss of licensure. The CISO must enforce compliance over the marketing team's requests.
    *   **Why A is a Distractor:** While security should align with business goals (A is a valid concept generally), business alignment cannot violate the law. Revenue generation does not excuse regulatory non-compliance.
    *   **Why B is a Distractor:** Risk Avoidance (B) is a valid risk treatment strategy, but it's an extreme reaction here. The organization doesn't have to completely avoid collecting data; they simply must implement consent and retention mechanisms (Risk Mitigation) to comply with the law.
    *   **Why D is a Distractor:** Psychological Acceptability (D) is a true design principle (making security user-friendly), but user friction from consent forms is irrelevant when facing mandatory legal compliance.

#### **3. An architect is designing a heavily encrypted storage system for a government contractor. The objective is to ensure that even if the source code of the proprietary encryption software is stolen by a nation-state attacker, the encrypted data remains entirely secure. The architect decides against writing a custom obfuscation algorithm and instead utilizes standard AES-256 in GCM mode. This architectural decision is primarily driven by which established security principle?**
A. Defense in Depth
B. Economy of Mechanism
C. Open Design
D. Leveraging Existing Components

*   **Correct Answer:** C
*   **[Explanation Logic]**
    *   **Why C is the BEST choice:** The scenario specifically focuses on the system remaining secure *even if the source code/algorithm design is stolen*. This is the exact definition of **Open Design** (Kerckhoffs's Principle), which states that the security of a mechanism should not depend on the secrecy of its design or implementation, but solely on the secrecy of the keys.
    *   **Why D is a Distractor:** Leveraging Existing Components (D) is technically correct here—the architect is using standard AES instead of building a custom one. However, Open Design is the *primary* principle that explains *why* stealing the code doesn't compromise the data. Leveraging existing components is the *action* taken to fulfill the Open Design principle.
    *   **Why A is a Distractor:** Defense in Depth (A) involves multiple layers of security. While encryption is a layer, the scenario focuses purely on the methodology of the encryption mechanism itself, not layering it with other controls like firewalls or IDS.
    *   **Why B is a Distractor:** Economy of Mechanism (B) focuses on keeping the design simple to reduce the attack surface. While using standard AES might be simpler than writing custom crypto, it doesn't directly address the "stolen source code" premise.

#### **4. You are evaluating a proposal for a new Identity and Access Management (IAM) service. The vendor claims their system employs "Zero Trust architecture." To substantiate this claim, the system mandates that every single data access request—even from previously authenticated users originating from within the corporate LAN—must be explicitly verified against current authorization policies. Which core security design principle is this system actively demonstrating?**
A. Least Privilege
B. Complete Mediation
C. Separation of Duties
D. Non-repudiation

*   **Correct Answer:** B
*   **[Explanation Logic]**
    *   **Why B is the BEST choice:** **Complete Mediation** mandates that every access to every object must be checked for authority. It prohibits caching authorization decisions in a way that allows subsequent requests to bypass checks. This is the foundational technical principle behind Zero Trust, which assumes the network is compromised and verifies every individual transaction.
    *   **Why A is a Distractor:** Least Privilege (A) is a vital concept (giving users only the rights they need), but it defines the *extent* of the permissions, not the *action of continuously verifying* them on every request.
    *   **Why C is a Distractor:** Separation of Duties (C) requires multiple people to complete a task to prevent fraud. It is not related to continuously verifying a single user's network access requests.
    *   **Why D is a Distractor:** Non-repudiation (D) ensures a user cannot deny an action. While logging the access provides non-repudiation, the act of *blocking/verifying* the access itself is Complete Mediation.

#### **5. A financial software development team is performing a quantitative risk analysis on a newly discovered vulnerability in their payment gateway. They estimate the vulnerability could be exploited once a year (ARO = 1.0). If exploited, the breach would cost the company $500,000 in fines and lost revenue (SLE = $500,000). A proposed Web Application Firewall (WAF) rule could mitigate this vulnerability completely, but the enterprise WAF license and maintenance cost $600,000 annually. Based strictly on quantitative risk management, what is the BEST recommendation?**
A. Implement the WAF rule immediately because the Single Loss Expectancy (SLE) is unacceptably high.
B. Accept the risk, as the Annualized Loss Expectancy (ALE) is lower than the cost of the control.
C. Transfer the risk by purchasing cybersecurity insurance, regardless of the premium cost.
D. Mitigate the risk using the WAF, as protecting financial data supersedes cost-benefit analyses.

*   **Correct Answer:** B
*   **[Explanation Logic]**
    *   **Why B is the BEST choice:** In quantitative risk analysis, you calculate the Annualized Loss Expectancy (ALE = ARO * SLE). Here, ALE = 1.0 * $500,000 = $500,000. A fundamental rule of risk management is that the cost of the safeguard (control) should not exceed the ALE. Since the WAF costs $600,000/year and the ALE is only $500,000/year, deploying the WAF results in a net financial loss of $100,000 annually. Therefore, accepting the risk (or finding a cheaper mitigation) is the soundest financial decision.
    *   **Why A & D are Distractors:** Options A and D are emotionally or theoretically "correct" in a vacuum (we want to stop breaches!), but they blatantly ignore the mathematics of the quantitative risk assessment provided. A control shouldn't cost more than the risk it mitigates.
    *   **Why C is a Distractor:** Transferring the risk (C) via insurance might be a good alternative, but doing so "regardless of premium cost" is financially irresponsible and violates the same cost-benefit principles as option D.

#### **6. A development team lead notices that developers are routinely hardcoding database credentials directly into the application's source code to speed up local testing. When confronted, the developers state that setting up a secure local secrets manager takes too much time and breaks their workflow. The team lead decides to implement an automated script that securely injects lightweight, temporary database credentials into the developers' environments upon startup without any manual configuration. Which security design principle is the team lead primarily honoring?**
A. Fail Secure
B. Psychological Acceptability
C. Open Design
D. Least Common Mechanism

*   **Correct Answer:** B
*   **[Explanation Logic]**
    *   **Why B is the BEST choice:** **Psychological Acceptability** (or "Secure Defaults/Ease of Use") states that security mechanisms should not make the resource more difficult to access than if the security mechanism were not present. If a security control is too painful or complex (like the manual secrets manager), humans will naturally bypass it (by hardcoding credentials). By automating the secure process, the team lead makes the secure path the easiest path, directly fulfilling this principle.
    *   **Why A is a Distractor:** Fail Secure (A) relates to how a system behaves during a crash or error, not the usability of the developer experience.
    *   **Why C is a Distractor:** Open Design (C) advocates for not relying on the secrecy of the algorithm. It has nothing to do with workflow usability.
    *   **Why D is a Distractor:** Least Common Mechanism (D) is about minimizing shared states to prevent interference or DoS, not about reducing developer friction.

#### **7. An organization processes millions of highly sensitive biometric records. To enhance security, the architecture mandates that the front-end web tier is completely physically and logically separated from the back-end database tier. The tiers are separated by a strict firewall, an API gateway, and an Intrusion Prevention System (IPS). An attacker who manages to compromise the web tier cannot directly access the database. Which architectural concept does this best represent?**
A. Defense in Depth
B. Complete Mediation
C. Component Reuse
D. Separation of Duties

*   **Correct Answer:** A
*   **[Explanation Logic]**
    *   **Why A is the BEST choice:** **Defense in Depth** (Layered Security) involves implementing multiple, overlapping security controls in series. The scenario clearly describes a layered approach (physical separation, logical separation, firewall, API gateway, IPS). If the attacker breaches the first layer (web tier), subsequent layers still protect the core asset (database).
    *   **Why B is a Distractor:** complete Mediation (B) means every request is checked. While the API gateway likely performs mediation, the overall *topology* described (firewalls, multiple tiers, IPS) describes the broader concept of Defense in Depth.
    *   **Why D is a Distractor:** Separation of Duties (D) requires different *people* (subjects) to perform parts of a task to prevent fraud. It does not apply to network tiers or technical network segmentation.
    *   **Why C is a Distractor:** Component Reuse (C) refers to using established libraries instead of custom code, which isn't the focus of this network architecture scenario.

#### **8. A software development firm has recently acquired a smaller startup. The startup's flagship application is highly profitable but consists of overly complex, monolithic, "spaghetti" code that has not been securely maintained. The acquiring firm decides to isolate this legacy application on a segregated virtual network and restricts access to it, rather than attempting to review, refactor, and patch the millions of lines of complex code. This decision is predominantly an acknowledgment of which security principle?**
A. Open Design
B. Fail Safe Defaults
C. Economy of Mechanism
D. Complete Mediation

*   **Correct Answer:** C
*   **[Explanation Logic]**
    *   **Why C is the BEST choice:** **Economy of Mechanism** (KISS principle - Keep It Simple, Stupid) states that security mechanisms, and the system design itself, should be as simple and small as possible. Complex systems (like "spaghetti code") are inherently difficult to analyze, secure, and maintain because vulnerabilities hide easily in complexity. The firm acknowledges that the massive complexity makes it economically and practically impossible to secure properly, thus proving the negative consequences of violating the Economy of Mechanism.
    *   **Why A, B, and D are Distractors:** None of these principles directly address the inherent danger of immense, unmaintainable software complexity. Segregating the application is a risk mitigation strategy born from the realization that the system violates Economy of Mechanism.

#### **9. During the design of a globally distributed ledger system, architects realize that because all nodes are equally privileged and lack a central authority, an attacker compromising a small number of nodes could inject fraudulent ledgers. To combat this, they design a consensus algorithm that relies on cryptographic hashing and requires a mathematical proof-of-work from a majority of nodes to validate any transaction. What is the fundamental security requirement this design is trying to achieve?**
A. Availability
B. Confidentiality
C. Non-repudiation
D. Integrity

*   **Correct Answer:** D
*   **[Explanation Logic]**
    *   **Why D is the BEST choice:** **Integrity** is the assurance that data has not been altered in an unauthorized manner. Cryptographic hashing and consensus mechanisms in distributed ledgers are explicitly designed to prevent fraudulent alterations (injections) to the ledger state. While this also provides non-repudiation (C), the primary threat described—fraudulent alteration of data—is an attack on Integrity.
    *   **Why C is a Distractor:** Non-repudiation (C) is a very strong secondary goal (proving who made the transaction), but the primary goal of the consensus algorithm against fraudulent injection is to ensure the global state remains authentic and unaltered (Integrity). You can have integrity without non-repudiation, but you can't have reliable non-repudiation if the integrity of the ledger is broken.
    *   **Why A and B are Distractors:** Confidentiality (B) is not addressed (blockchains are often public). Availability (A) is inherent in a distributed system, but the cryptographic proof-of-work specifically targets the *accuracy* of the data, not its uptime.

#### **10. A cloud-native application uses a microservices architecture. Service A (Inventory) frequently requests data from Service B (Pricing). Originally, both services shared the same physical memory space on a monolithic server. Now, they communicate over an internal API. An architect discovers that a vulnerability in Service A is being used to conduct a Denial of Service (DoS) attack, exhausting the shared Redis cache that both Service A and Service B use to store temporary data, taking both services offline. What design principle was violated here?**
A. Defense in Depth
B. Least Common Mechanism
C. Fail Secure
D. Open Design

*   **Correct Answer:** B
*   **[Explanation Logic]**
    *   **Why B is the BEST choice:** **Least Common Mechanism** dictates that mechanisms shared by multiple users, processes, or systems should be minimized. By having both Service A and Service B share the *same* Redis cache (a common mechanism), a flaw or resource exhaustion in one service directly impacts the other. If they had isolated/dedicated caches, Service B would have survived Service A's DoS attack.
    *   **Why A is a Distractor:** While poor Defense in Depth (A) allows the attack to succeed, the *specific* architectural flaw allowing lateral DoS impact is the shared resource (Least Common Mechanism).
    *   **Why C is a Distractor:** Fail Secure (C) deals with the state of the system after failure. The issue here is *why* the failure propagated across service boundaries.
    *   **Why D is a Distractor:** Open Design (D) relates to algorithmic secrecy, which is irrelevant to shared infrastructure caches.

#### **11. An enterprise creates an Acceptable Use Policy (AUP) that forbids developers from using external, unvetted generative AI tools to write code for the company's proprietary trading algorithms. A developer inadvertently uploads a highly confidential algorithm to a public AI chatbot to debug an error. This incident represents a failure in which aspect of the CIA triad, and what is the classification of the countermeasure that failed?**
A. Confidentiality; Administrative Control
B. Integrity; Technical Control
C. Availability; Physical Control
D. Confidentiality; Technical Control

*   **Correct Answer:** A
*   **[Explanation Logic]**
    *   **Why A is the BEST choice:** The uploading of proprietary code to a public third party is a massive breach of **Confidentiality**. The AUP (Acceptable Use Policy) that the developer violated is a classic example of an **Administrative Control** (a policy, procedure, or guideline directed at human behavior).
    *   **Why D is a Distractor:** Confidentiality is correct, but an AUP is not a Technical Control (like a firewall or Data Loss Prevention software). The developer's brain failed to follow the rules. (If a DLP system had blocked the upload, that would have been a technical control working).
    *   **Why B and C are Distractors:** Integrity (the code wasn't altered in transit) and Availability (the code wasn't deleted from the company's servers) are not the primary victims of this data leak.

#### **12. A CISO is reviewing a risk assessment for a new legacy system migration. The assessment identifies an outdated, unpatchable protocol in use that carries a "High" risk rating due to known exploits. Because the system is critical to production line stability, the CISO decides the company cannot simply turn it off (avoidance). Furthermore, no insurance company will cover a known vulnerability (transference). Management signs a formal memo acknowledging they will absorb the financial impact if a breach occurs, while the IT team builds a 2-year plan to replace the system. Which risk treatment strategy has been adopted?**
A. Risk Mitigation
B. Risk Acceptance
C. Risk Avoidance
D. Risk Transference

*   **Correct Answer:** B
*   **[Explanation Logic]**
    *   **Why B is the BEST choice:** **Risk Acceptance** occurs when an organization formally dictates that the cost or operational impact of fixing or avoiding a risk outweighs the benefit, and they choose to live with it and absorb the potential losses. The formal memo signed by management is the textbook hallmark of Risk Acceptance. (The 2-year replacement plan is future mitigation, but the *current* technical posture for the next 2 years is acceptance).
    *   **Why A is a Distractor:** They are not currently deploying a technical fix or compensating control to reduce the *immediate* risk; they are just leaving it vulnerable for 2 years.
    *   **Why C and D are Distractors:** The scenario explicitly rules out Avoidance (cannot turn it off) and Transference (cannot get insurance).

#### **13. A biometric access system is engineered for a high-security military laboratory. The designers explicitly configure the system to prioritize denying access to legitimate personnel if there is even strict minor deviation in the biometric scan (e.g., a dirty finger), rather than risk allowing an unauthorized impostor inside. In biometric terminology, this design deliberately accepts a high:**
A. False Acceptance Rate (FAR)
B. Crossover Error Rate (CER)
C. False Rejection Rate (FRR)
D. Clipping Level

*   **Correct Answer:** C
*   **[Explanation Logic]**
    *   **Why C is the BEST choice:** The **False Rejection Rate (FRR)**, also known as Type I Error, is the rate at which authorized users are denied access. By tuning the system to be extremely strict (paranoia mode), the designers purposefully increase the FRR to ensure that the False Acceptance Rate (FAR - letting bad guys in) is driven down to nearly zero.
    *   **Why A is a Distractor:** The exact opposite. FAR (Type II Error) is what they are trying to minimize at all costs.
    *   **Why B is a Distractor:** CER is the point where FRR and FAR intersect. It is a metric of overall system accuracy, not the specific bias chosen in this scenario.
    *   **Why D is a Distractor:** Clipping Level refers to setting thresholds for auditing or account lockouts (e.g., locking an account after 3 failed login attempts), not biometric scanner sensitivity algorithms.

#### **14. User provisioning for an internal corporate web portal is automated. When an active directory user is placed into the `IT_Admins` group, they automatically receive administrative capabilities within the web portal via a nightly synchronization script. An auditor discovers that when a user is demoted and removed from the `IT_Admins` group, their administrative rights in the web portal are *not* automatically revoked because the synchronization script only handles additions, not deletions. This violates which foundational security principle?**
A. Need to Know
B. Defense in Depth
C. Separation of Duties
D. Least Privilege

*   **Correct Answer:** D
*   **[Explanation Logic]**
    *   **Why D is the BEST choice:** **Least Privilege** dictates that users should only have the exact permissions necessary to perform their *current* job functions. Because the system fails to revoke privileges upon demotion, users retain administrative rights they no longer require. This specific failure is a textbook case of "Privilege Creep," which is the direct enemy of Least Privilege.
    *   **Why A is a Distractor:** "Need to Know" is closely related but highly specific to *accessing data/information* (e.g., clearance levels). Least Privilege is broader and encompasses *capabilities and execution rights* (like administrative portal actions).
    *   **Why B and C are Distractors:** While defense in depth is missing, and separation of duties might be a good idea, the explicit failure of retaining unnecessary admin rights points directly to a Least Privilege violation.

#### **15. A software organization adopts a policy that states: "Whenever a data field is no longer required to support a valid business transaction or legal retention mandate, it must be permanently purged from all production databases and backups within 30 days." This policy directly addresses which aspect of information lifecycle management?**
A. Data Classification
B. Data Disposal
C. Data Archiving
D. Data Collection Minimization

*   **Correct Answer:** B
*   **[Explanation Logic]**
    *   **Why B is the BEST choice:** **Data Disposal** (or Data Destruction/Purging) is the final phase of the information lifecycle. The policy specifically mandates the permanent destruction ("purged from all... databases") of data when its retention period expires, which defines the disposal phase.
    *   **Why C is a Distractor:** Archiving involves moving data to long-term, cheaper storage for retention purposes, not permanently purging it from existence.
    *   **Why D is a Distractor:** Collection Minimization happens at the *start* of the lifecycle (don't collect it if you don't need it). The scenario describes dealing with data at the *end* of its usefulness.
    *   **Why A is a Distractor:** Data classification (labeling data as Public, Secret, etc.) dictates *how* it should be handled, but the act of destroying it is Disposal.

#### **16. An application developer implements a "Remember Me" functionality. Instead of storing the user's secure password in a cookie, the developer generates a random, cryptographically strong token, stores its hash in the backend database, and places the plaintext token in a browser cookie. This implementation strategy specifically mitigates the risk of exposing the original credential. Which principle does this implementation represent?**
A. Tokenization
B. Encryption
C. Economy of Mechanism
D. Complete Mediation

*   **Correct Answer:** A
*   **[Explanation Logic]**
    *   **Why A is the BEST choice:** **Tokenization** involves substituting a sensitive data element (the user's real password) with a non-sensitive equivalent (the random token) that has no extrinsic or exploitable meaning or value. While hashing is used on the backend, the architectural concept of giving the browser a surrogate value instead of the real credential is a classic tokenization strategy.
    *   **Why B is a Distractor:** Encryption is a two-way mathematical process requiring a key. The token is a randomly generated surrogate string, not an encrypted version of the password.
    *   **Why C and D are Distractors:** Economy of mechanism (simplicity) and Complete Mediation (checking every access) do not describe the data substitution technique replacing the real password with a token.
