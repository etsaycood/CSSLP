# Domain 4: Secure Software Architecture and Design (19 Questions)

#### **1. A security architect decides to segment a large monolithic application into several small, independently deployable services that communicate via HTTP APIs. Each service contains its own database. What architectural pattern has the architect adopted?**
A. Client-Server
B. Peer-to-Peer (P2P)
C. Microservices (Service-Oriented Architecture / SOA)
D. N-tier

*   **Answer: C**
*   **Rationale:** Segmenting an application into small, independent services bounded by business domains and communicating via APIs defines a **Microservices** architecture (a modern implementation of SOA). This pattern provides agility but introduces a massive attack surface spanning hundreds of API endpoints that must be authenticated and authorized.

#### **2. An engineering team is developing a mobile application that temporarily caches sensitive user data securely on the device's specialized, physically isolated silicon chip to prevent extraction by malware or a compromised OS. The team is leveraging which hardware platform mitigation?**
A. Secure Element / Trusted Platform Module (TPM)
B. Side-channel mitigation
C. Firmware driver virtual memory
D. Speculative execution mitigation

*   **Answer: A**
*   **Rationale:** A **Secure Element** (like Apple's Secure Enclave) or a **Trusted Platform Module (TPM)** is a dedicated, physically isolated cryptographic coprocessor designed to securely generate, store, and process cryptographic keys and sensitive data, defending against OS-level compromise.

#### **3. An architect is using the STRIDE threat modeling methodology to evaluate an application's architecture. The architect identifies a flaw where a user can intercept and alter an HTTP request in transit to increase the price of an item in a shopping cart. This flaw corresponds to which category in STRIDE?**
A. Spoofing
B. Tampering
C. Repudiation
D. Information Disclosure

*   **Answer: B**
*   **Rationale:** **Tampering** involves the malicious modification, manipulation, or alteration of data, either in transit (as in this scenario) or at rest.

#### **4. A cloud-native application is designed to be completely elastic, with the backend scaling up to 100 web servers during traffic spikes and scaling down to 2 during quiet periods. To implement this architecture securely, the architect mandates that servers are never manually configured but are spun up dynamically from validated scripts. This is leveraging which technology?**
A. Pervasive computing
B. Infrastructure as Code (IaC)
C. Cognitive computing
D. Content Delivery Networks (CDN)

*   **Answer: B**
*   **Rationale:** **Infrastructure as Code (IaC)** allows for the automated, repeatable, and secure provisioning of infrastructure components (VMs, containers, networks) using configuration scripts instead of manual portal configurations, which is essential for secure, elastic cloud architectures.

#### **5. In a distributed peer-to-peer (P2P) network architecture without a centralized server, a key architectural security concern is ensuring that the data provided by one node to another has not been maliciously altered. Which cryptographic mechanism is MOST critical to establish this?**
A. Symmetric encryption via AES-256
B. Hashing and digital signatures (Non-repudiation)
C. Database triggers and views
D. Screen layouts and UI masking

*   **Answer: B**
*   **Rationale:** In a trustless, decentralized P2P network, ensuring data integrity and verifying the origin of the data requires robust **hashing and digital signatures**. Symmetric encryption provides confidentiality but does not natively guarantee the author's identity or prevent repudiation across distributed nodes.

#### **6. A team of security engineers conducts an exercise simulating an advanced persistent threat (APT) attacking their new architecture to identify potential vulnerabilities. The methodology they use focuses intensely on the motivations, tools, and objectives of the adversary rather than just the software components. They are likely using which threat modeling methodology?**
A. Common Vulnerability Scoring System (CVSS)
B. STRIDE
C. Process for Attack Simulation and Threat Analysis (PASTA)
D. Infrastructure as Code (IaC)

*   **Answer: C**
*   **Rationale:** **PASTA** is an attacker-centric, risk-based threat modeling methodology. It takes seven steps to align business objectives with technical requirements and deeply simulates the attacker's perspective (Attack Simulation) to identify threats.

#### **7. A developer is designing a system where an application must temporarily grant a third-party service limited access to a user's account without sharing the user's password. Which protocol is the BEST design choice for this interface?**
A. Security Assertion Markup Language (SAML)
B. OAuth 2.0
C. Lightweight Directory Access Protocol (LDAP)
D. Kerberos

*   **Answer: B**
*   **Rationale:** **OAuth 2.0** is an authorization framework explicitly designed to allow a third-party application to obtain limited access (via tokens) to an HTTP service on behalf of a resource owner, crucially without exposing the resource owner's credentials.

#### **8. The architecture board requires the implementation of an architectural pattern where external B2B partners can authenticate against their own identity systems, but seamlessly log into your organization's web applications. This design requires the adoption of:**
A. Discretionary Access Control (DAC)
B. Mandatory Access Control (MAC)
C. Federated Identity
D. Speculative Execution

*   **Answer: C**
*   **Rationale:** **Federated Identity** (or Federation) creates a trust agreement between multiple organizations, allowing users from one domain to securely access resources in another domain using their home organization's credentials (commonly using SAML or OIDC).

#### **9. An architect is reviewing the Attack Surface of a new web application. The application exposes 15 unauthenticated public REST API endpoints, utilizes 4 external unvetted open-source libraries, and accepts file uploads in 2 different forms. What is the primary goal of Attack Surface Evaluation?**
A. To increase the number of API endpoints to confuse attackers.
B. To identify all potential entry and exit points an attacker could exploit and attempt to minimize them.
C. To generate the exact CVSS score for the web application.
D. To mandate the use of Cognitive Computing (AI) in threat detection.

*   **Answer: B**
*   **Rationale:** **Attack Surface Evaluation** documents every possible way an attacker could interact with the system (APIs, ports, UI inputs, external libraries) with the ultimate architectural goal of reducing or minimizing that surface to lower the overall risk.

#### **10. An IoT architecture relies on hundreds of remotely deployed wireless sensors. To prevent physical tampering and ensure only authorized code executes on these sensors, the architect mandates that the hardware must verify a digital signature before loading the operating system kernel. This hardware-level protection is known as:**
A. Side-channel mitigation
B. Secure Boot
C. Out-of-band management
D. Continuous Integration

*   **Answer: B**
*   **Rationale:** **Secure Boot** ensures that a device only executes trusted, signed software firmware and operating system layers upon power-up, preventing rootkits or maliciously altered firmware from persisting on embedded IoT devices.

#### **11. A legacy monolithic architecture is refactored into an N-tier architecture consisting of a presentation layer, a business logic layer, and a data access layer. Where should the architectural design enforce the MOST stringent input validation?**
A. Only in the presentation layer (client-side)
B. Only in the data access layer
C. In the presentation layer, but heavily enforced and trusted only at the business logic layer (server-side)
D. Input validation is unnecessary in an N-tier architecture.

*   **Answer: C**
*   **Rationale:** In an N-tier design, client-side validation (presentation layer) improves usability, but it can be easily bypassed by attackers directly querying the API. Therefore, **server-side validation** (at the business logic boundary) is critical and must not trust any input from upstream tiers.

#### **12. A security architect mandates that a database housing PII implements explicit "Views" rather than allowing applications to query base tables directly. This database security control primarily enforces which security principle?**
A. Need-to-know / Least Privilege
B. Non-repudiation
C. Open Design
D. Fail Secure

*   **Answer: A**
*   **Rationale:** Database **Views** act as virtual tables that limit the columns and rows visible to the querying application, masking sensitive data not relevant to the caller's task. This strictly enforces the principle of **Need-to-Know** and **Least Privilege**.

#### **13. During an architectural design review, an engineer proposes passing sensitive user session tokens completely in the URL query parameters to speed up routing. The security architect rejects this proposal because URLs are routinely logged by external proxies and browser histories. This scenario underscores the importance of:**
A. Selecting reusable technologies
B. Secure interface design and upstream/downstream dependencies
C. Cognitive computing
D. Trusted Computing Base (TCB)

*   **Answer: B**
*   **Rationale:** **Secure Interface Design** involves scrutinizing how components interact. Passing sensitive secrets (like tokens or API keys) via URL query parameters is a critical design flaw because upstream/downstream systems (proxies, load balancers, browser histories) systematically log URLs, resulting in massive credential exposure.

#### **14. When considering threat intelligence as part of the architecture phase, an organization relies on feeds from an industry Information Sharing and Analysis Center (ISAC) to predict which attack vectors are currently targeting the financial sector. The primary purpose of this activity is to:**
A. Calculate the CVSS score of the organization's existing vulnerabilities.
B. Retroactively identify zero-day vulnerabilities in source code.
C. Identify credible, relevant threats to inform and prioritize protective architectural design choices.
D. Satisfy the right to audit clause in vendor contracts.

*   **Answer: C**
*   **Rationale:** Applying **Threat Intelligence** during the architecture phase allows architects to understand the Tactics, Techniques, and Procedures (TTPs) of real-world adversaries targeting their industry, allowing them to **prioritize controls** against the most credible threats during the system's design.

#### **15. An organization is migrating an on-premises web server directly to an Amazon Web Services (AWS) EC2 Virtual Machine without rewriting any code. In this specific Cloud Architecture model, the organization remains entirely responsible for managing the operating system, patching, and the application runtime. This model is:**
A. Software as a Service (SaaS)
B. Platform as a Service (PaaS)
C. Infrastructure as a Service (IaaS)
D. Serverless Architecture

*   **Answer: C**
*   **Rationale:** Buying raw compute power (like a VM) where the cloud provider manages the physical hardware, but the customer manages the OS, patching, and application code is defining an **Infrastructure as a Service (IaaS)** shared responsibility model.

#### **16. An application handles classified government intelligence. The security architect limits network connectivity, implements mandatory access control (MAC), and ensures any object access is strictly verified by reference monitors. The sum of all these protection mechanisms (hardware, software, and firmware) enforcing the security policy is widely referred to as the:**
A. Common Vulnerability Scoring System (CVSS)
B. Trusted Computing Base (TCB)
C. Speculative Execution
D. Software Bill of Materials (SBOM)

*   **Answer: B**
*   **Rationale:** The **Trusted Computing Base (TCB)** is the totality of all protection mechanisms within a computer system (hardware, firmware, and software) that act together to enforce a security policy.

#### **17. Under the STRIDE threat model, an attacker successfully exhausts the memory of a target application server by sending thousands of incomplete TCP connection requests, effectively preventing legitimate customers from accessing the service. This attack correlates to which STRIDE element?**
A. Spoofing
B. Information Disclosure
C. Denial of Service (DoS)
D. Elevation of Privilege

*   **Answer: C**
*   **Rationale:** **Denial of Service (DoS)** attacks aim to compromise the Availability of a system by exhausting compute, memory, or network resources, preventing legitimate users from accessing the service.

#### **18. A security team evaluates the architecture of an application and requires that every single administrative command sent to the server must be logged to a remote, read-only Syslog server. According to STRIDE, this architectural control specifically mitigates which threat?**
A. Elevation of Privilege
B. Repudiation
C. Spoofing
D. Information Disclosure

*   **Answer: B**
*   **Rationale:** Logging transactions to an immutable, external server ensures that an administrator cannot deny executing a harmful command when the audit log review occurs later. This directly mitigates **Repudiation** threats.

#### **19. An architect dictates that a new mobile application must rely exclusively on existing Identity Providers (like Google, Apple, or Azure AD) for authentication, eliminating the need for the application to store its own hashed passwords. This architectural decision leverages which concept to reduce the attack surface?**
A. Evaluating and selecting reusable technologies (Credential Management)
B. Industrial Internet of Things (IoT) robotics
C. Rich internet applications (Client-side exploits)
D. Cognitive computing

*   **Answer: A**
*   **Rationale:** Outsourcing authentication to massive, hardened IdPs (Identity Providers) via standards like SAML or OIDC is a classic example of **evaluating and selecting reusable technologies for credential management**, drastically lowering the risk associated with developing and securing a custom, bespoke password storage database.
