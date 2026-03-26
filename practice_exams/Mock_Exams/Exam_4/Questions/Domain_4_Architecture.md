# Exam 4
## Domain 4: Secure Software Architecture and Design (18 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. During the architectural design phase of a new microservices-based application, the security team decides to implement a central Identity Provider (IdP) and an API Gateway. All external client requests must pass through the API Gateway, which validates an OAuth 2.0 JWT (JSON Web Token) before routing the request to any internal microservice. What specific security design pattern is being applied here to manage access control efficiently?**
A. The Strangler Fig Pattern
B. The Singleton Pattern
C. The API Gateway / Federated Identity Pattern (Single Point of Entry)
D. The Circuit Breaker Pattern

#### **2. A development team is designing a highly secure voting application. They identify a critical threat: a malicious database administrator (DBA) could directly alter the vote counts in the backend database. To mitigate this specific threat at the architectural level, they mandate that all votes must be digitally signed by the voter's client application before transmission, and the backend tally service will only count votes with valid signatures. Which element of the STRIDE model does this architectural control directly address?**
A. Spoofing
B. Information Disclosure
C. Denial of Service
D. Tampering

#### **3. You are conducting an architecture review of a multi-tier web application. You notice that the web server (Tier 1) connects directly to the backend database server (Tier 3) without passing through an application logic tier (Tier 2). Furthermore, the web server is placed in the DMZ. What is the fundamental security flaw in this architecture?**
A. It implements Defense in Depth too aggressively.
B. It exposes the database directly to a compromised web server in the DMZ, lacking a necessary logical boundary and separation of concerns.
C. It requires too much memory to run three tiers.
D. The web server cannot use HTTPS in the DMZ.

#### **4. A cloud architect is designing a system that processes highly sensitive credit card transactions. To isolate the processing environment, they place the payment processing virtual machines (VMs) in a dedicated Virtual Private Cloud (VPC) subnet that has NO route to the public Internet (no Internet Gateway). They communicate with the frontend web servers via a heavily firewalled internal load balancer. What architectural security concept does this highly restricted subnet represent?**
A. An Enclave (or Secure Execution Environment)
B. A Honeypot
C. A Content Delivery Network (CDN)
D. A Reverse Proxy

#### **5. When performing Threat Modeling using the STRIDE methodology, during which specific phase of the Secure Software Development Lifecycle (SSDLC) should the initial Data Flow Diagram (DFD) ideally be created and analyzed to maximize its cost-effectiveness?**
A. During the final Penetration Testing phase.
B. During the Architecture and Design phase (before coding begins).
C. Immediately after the Incident Response team detects a breach.
D. During the Decommissioning phase.

#### **6. A software architect is designing a system where users can upload profile pictures. The architect designs the application to automatically strip all EXIF metadata (e.g., GPS coordinates, camera model) from the uploaded image files before saving them to the storage bucket. What specific type of privacy design strategy is this?**
A. Data Masking
B. Data Minimization (Stripping unnecessary data)
C. Encryption Data-in-Transit
D. Database Sharding

#### **7. A monolithic application is being refactored into microservices. The architect decides that instead of every microservice maintaining its own user database and handling password hashing, a dedicated "Authentication Service" will be created. All other services will delegate login requests to this single service. Which secure design principle is being utilized?**
A. Principle of Least Privilege
B. Economy of Mechanism (and Centralized Security Controls)
C. Security by Obscurity
D. Fail-Safe Defaults

#### **8. In a Threat Modeling exercise, an architect draws a Data Flow Diagram (DFD). A dotted red line is drawn separating the "Public Internet" from the "Internal Corporate Network," representing the firewall. In threat modeling terminology, what is this dotted red line called?**
A. An External Entity
B. A Data Store
C. A Trust Boundary
D. A Process

#### **9. A system is designed to allow external researchers to query a medical database to find correlations between age and disease. However, the system is designed to automatically inject a small amount of random "noise" into the statistical results (e.g., slightly altering the average age returned). This ensures the researcher can get useful macro-trends but mathematically prevents them from identifying any specific individual patient's record. What advanced privacy-enhancing technology is being architected here?**
A. Differential Privacy
B. Homomorphic Encryption
C. Symmetric Key Exchange
D. Digital Steganography

#### **10. An architect is reviewing the design of a desktop application that requires administrative privileges to modify certain system files. Instead of requiring the user to run the entire application as an Administrator (which violates the Principle of Least Privilege), the architect redesigns the application so that the main UI runs as a standard user, and it spawns a small, separate, highly vetted background process that runs as Administrator ONLY when file modification is needed. What secure architectural pattern is this?**
A. Privilege Separation (or Compartmentalization)
B. Single Sign-On (SSO)
C. The MVC (Model-View-Controller) Pattern
D. Zero Trust Architecture

#### **11. A team is using the STRIDE threat model to analyze a proposed login system. They identify a threat: "An attacker could intercept the network traffic and capture the user's password in plaintext." To counter this, they add a requirement: "All login traffic must occur over HTTPS." Which specific aspect of STRIDE does "intercepting traffic to capture passwords" map to?**
A. Spoofing
B. Elevation of Privilege
C. Information Disclosure
D. Repudiation

#### **12. A security architect mandates the use of parameterized queries (Prepared Statements) for all database interactions in a new application's design. This architectural decision is specifically employed to act as a compensating control against which widespread class of vulnerabilities?**
A. Cross-Site Scripting (XSS)
B. Injection Attacks (e.g., SQL Injection)
C. Insecure Direct Object References (IDOR)
D. Buffer Overflows

#### **13. When designing a resilient architecture for a global SaaS application, the architect decides to distribute the database across three different geographical regions using asynchronous replication. In the event of a catastrophic failure in Region A, the system will automatically failover to Region B. This architectural decision primarily addresses which concept?**
A. Confidentiality
B. Disaster Recovery (and Availability)
C. Non-Repudiation
D. Data Sovereignty

#### **14. An architect is designing an application that will process credit card payments. To minimize the application's PCI-DSS compliance scope, the architect decides the application will NOT collect or store credit card numbers at all. Instead, the UI will embed an iframe hosted directly by a third-party payment gateway (like Stripe). The third party handles the card data and simply returns a success/fail token to the application. What risk management strategy is the architect employing?**
A. Risk Acceptance
B. Risk Avoidance (by outsourcing the high-risk function/data)
C. Risk Mitigation
D. Risk Exploitation

#### **15. During a security design review, an architect notices that an application uses a custom hashing algorithm created by a junior developer to store passwords, instead of a proven algorithm like Argon2 or bcrypt. The developer argues their algorithm is faster. Why is this a critical architectural flaw?**
A. Custom algorithms cannot be patented.
B. It violates Kerckhoffs's Principle and the rule against "rolling your own crypto," as unvetted cryptographic designs are almost certainly flawed and easily compromised.
C. Argon2 requires too much bandwidth to transmit.
D. Fast algorithms are always more secure.

#### **16. A system is designed with a "Circuit Breaker" pattern. When a backend microservice begins failing (e.g., returning 500 Server Errors due to a database outage), the API Gateway detects this and automatically stops sending traffic to that failing service for 60 seconds, returning a pre-defined cached response to the user instead of hanging. What is the primary security/reliability benefit of this architectural pattern?**
A. It prevents SQL injection attacks on the backend service.
B. It encrypts the data before it enters the database.
C. It prevents cascading failures across the entire system, protecting overall Availability during partial outages.
D. It guarantees that users have strong passwords.

#### **17. In the context of secure architecture, what is the defining characteristic of a "Zero Trust" model compared to a traditional perimeter-based (Castle-and-Moat) model?**
A. Zero Trust relies on a massive firewall at the edge of the network, assuming everything inside the firewall is safe.
B. Zero Trust assumes network location is irrelevant to security; all entities (internal or external) must be continuously authenticated, authorized, and validated before being granted access to any resource.
C. Zero Trust explicitly trusts all requests originating from IP addresses starting with `192.168.x.x`.
D. Zero Trust does not use encryption because it trusts the network cables.

#### **18. A development team is designing a mobile app that allows users to send disappearing messages (like Snapchat). A key architectural requirement is that the server that routes the messages MUST NEVER be able to read the plaintext content of the messages, even if the server is compromised or subpoenaed by law enforcement. Which architectural encryption pattern MUST be implemented to satisfy this requirement?**
A. Data at Rest Encryption (Full Disk Encryption) on the server.
B. End-to-End Encryption (E2EE), where encryption and decryption happen only on the users' devices.
C. Transport Layer Security (TLS/HTTPS) between the app and the server.
D. Symmetric Encryption using a key hardcoded in the server's source code.
