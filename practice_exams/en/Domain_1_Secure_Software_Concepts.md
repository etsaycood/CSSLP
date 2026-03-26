# Domain 1: Secure Software Concepts (15 Questions)

#### **1. A software architect is reviewing a system where an administrative user denies performing a specific configuration change that resulted in a data breach. Which of the following implementations would have been MOST effective in preventing this denial of action?**
A. Implementing strong Multi-Factor Authentication (MFA) for all administrative logins.
B. Encrypting all system configuration files using AES-256.
C. Combining unique identification with comprehensive auditing of privileged transactions.
D. Using a shared administrative account with a rotating high-complexity password.

*   **Answer: C**
*   **Rationale:** **Non-repudiation** addresses the deniability of actions and is accomplished by **auditing** used in conjunction with **identification**. While MFA (A) strengthens authentication, it does not inherently provide the audit trail needed to prove a specific action was taken after login.

#### **2. During a security review, a developer argues that hard-coding a secret cryptographic algorithm is an effective way to protect data because an attacker would not know how the encryption works. This approach MOST directly violates which design principle?**
A. Economy of Mechanism
B. Open Design
C. Least Common Mechanism
D. Fail Secure

*   **Answer: B**
*   **Rationale:** The **Open Design** principle states that security should not depend on the secrecy of the design or its implementation (Security through Obscurity). Instead, security should rest on the secrecy of the **key**.

#### **3. A financial application is being designed to handle high-value wire transfers. The organization decides that the person who initiates a transfer cannot be the same person who approves the transfer. This is an application of which security principle?**
A. Least Privilege
B. Defense in Depth
C. Separation of Duties
D. Complete Mediation

*   **Answer: C**
*   **Rationale:** **Separation of Duties** (or Compartmentalization) ensures that the successful completion of a single sensitive task is dependent on more than one person, preventing any single individual from abusing the system.

#### **4. Users of a new enterprise portal complain that they must re-enter their credentials every time they move between different modules of the application. While the developers want to fix this to improve the user experience, they are concerned about security. Which principle are the developers currently enforcing?**
A. Psychological Acceptability
B. Complete Mediation
C. Leveraging Existing Components
D. Economy of Mechanism

*   **Answer: B**
*   **Rationale:** **Complete Mediation** requires that every access request to an object be checked for authority every time, without circumventing checks in subsequent requests. While this ensures high security, it often conflicts with **Psychological Acceptability** (usability).

#### **5. A company suffers a breach because a legacy application failed and defaulted to a state that allowed all traffic to bypass its authentication layer to ensure "business continuity." This failure represents a lack of which design principle?**
A. Resiliency
B. Fail Secure
C. Least Privilege
D. Accountability

*   **Answer: B**
*   **Rationale:** **Fail Secure** (often used interchangeably with Fail Safe) ensures that if a system or design fails, it defaults to a **secure state** that maintains confidentiality, integrity, and availability rather than failing open.

#### **6. When determining the risk for a new cloud-based payroll system, the management decides to buy a specialized insurance policy to cover potential losses from a data breach. This is an example of which risk handling strategy?**
A. Risk Mitigation
B. Risk Avoidance
C. Risk Transference
D. Risk Acceptance

*   **Answer: C**
*   **Rationale:** **Risk Transference** involves shifting the financial liability of a risk to a third party, such as an insurance company.

#### **7. An application is designed to run with "System" or "Root" privileges to ensure it has all the permissions it might ever need for any future updates. This design choice primarily ignores which security concept?**
A. Defense in Depth
B. Least Privilege
C. Economy of Mechanism
D. Component Reuse

*   **Answer: B**
*   **Rationale:** **Least Privilege** dictates that a subject (user or process) should be given only the **minimum level of access** necessary to perform its current task. Running as "Root" by default provides excessive privilege that increases the impact of a potential compromise.

#### **8. A security professional is evaluating a biometric authentication system. They find that the point where legitimate users are wrongly rejected is exactly equal to the point where imposters are wrongly accepted. What is this specific metric called?**
A. False Rejection Rate (FRR)
B. False Acceptance Rate (FAR)
C. Crossover Error Rate (CER)
D. Clipping Level

*   **Answer: C**
*   **Rationale:** The **Crossover Error Rate (CER)** is the point at which the False Rejection Rate equals the False Acceptance Rate. A lower CER indicates a more accurate biometric system.

#### **9. A software development team is under pressure to deliver a product quickly. They decide to skip the removal of unneeded "bells-and-whistles" features that were not part of the original requirements. Which principle does this MOST likely violate?**
A. Open Design
B. Economy of Mechanism
C. Psychological Acceptability
D. Separation of Duties

*   **Answer: B**
*   **Rationale:** **Economy of Mechanism** (KISS principle) states that the likelihood of vulnerabilities increases with complexity. Unnecessary "bells-and-whistles" increase the **attack surface** and make the software harder to secure and understand.

#### **10. An organization processes highly sensitive data and implements a firewall, followed by an Intrusion Detection System (IDS), and then requires encrypted storage and strict access control lists. This "layered" approach is BEST described as:**
A. Complete Mediation
B. Least Common Mechanism
C. Defense in Depth
D. Fail Secure

*   **Answer: C**
*   **Rationale:** **Defense in Depth** (or Layered Defense) involves the use of multiple overlapping security safeguards so that the failure of a single control does not result in a total compromise.

#### **11. A developer is designing a web application and wants to implement cryptographic hashing for storing user passwords. Instead of creating a custom hashing algorithm to keep attackers guessing, the developer opts to use the established Argon2 algorithm from a well-known cryptographic library. This decision aligns BEST with which security design principle?**
A. Economy of Mechanism
B. Component Reuse
C. Complete Mediation
D. Separation of Duties

*   **Answer: B**
*   **Rationale:** **Component Reuse** emphasizes using existing, proven, and reviewed security controls and libraries (like established crypto libraries) instead of attempting to "reinvent the wheel," which often introduces new, unforeseen vulnerabilities.

#### **12. An organization is designing a high-availability customer portal. They are deciding between sharing a single overarching database connection pool for all users versus implementing isolated connections tailored to specific user trust levels. A security architect recommends the isolated approach to prevent a single compromised connection from impacting all users. This recommendation enforces which principle?**
A. Open Design
B. Psychological Acceptability
C. Least Common Mechanism
D. Nonrepudiation

*   **Answer: C**
*   **Rationale:** **Least Common Mechanism** dictates that mechanisms common to more than one user or process (like shared variables or single connection pools) should be minimized, as these shared pathways can be exploited to facilitate unauthorized information flow or widespread denial of service.

#### **13. A global healthcare provider is updating its patient portal. The software development team receives conflicting requirements regarding patient data retention: the marketing team wants to keep the data indefinitely, but a new regional law requires data to be deleted upon patient request. Under Governance, Risk, and Compliance (GRC) standards, which requirement takes highest priority?**
A. Internal corporate policy
B. The marketing team's business use case
C. Regulatory authority and legal requirements
D. Industry best practices for data warehousing

*   **Answer: C**
*   **Rationale:** In the hierarchy of organizational governance, **Regulatory authority and legal requirements** supersede internal business desires or policies. Failing to comply with privacy laws introduces severe legal, financial, and reputational risk.

#### **14. During the design of an identity and access management (IAM) system, the engineering team insists that using complex, 20-character passwords that must change every 30 days is the most secure approach. However, the security team argues this will lead to users writing passwords on sticky notes, effectively weakening security. The security team is advocating for which principle?**
A. Psychological Acceptability
B. Complete Mediation
C. Defense in Depth
D. Fail Secure

*   **Answer: A**
*   **Rationale:** **Psychological Acceptability** means that security mechanisms should not make the resource more difficult to access than if the security mechanisms were absent. If controls are too burdensome, users will actively find ways to bypass them (like writing down complex passwords), destroying the intended security. 

#### **15. An enterprise architect is designing a distributed cloud application and ensures that even if a primary database instance fails, a secondary replica in another geographic region automatically takes over without any loss of service or data corruption. This specific design choice primarily ensures which tenet of the CIA triad?**
A. Confidentiality
B. Integrity
C. Availability
D. Accountability

*   **Answer: C**
*   **Rationale:** **Availability** ensures that systems, networks, and applications are functioning and accessible when needed. Techniques such as redundancy, replication, clustering, and failover are key components of maintaining high availability.
