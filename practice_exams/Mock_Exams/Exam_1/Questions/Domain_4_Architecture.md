# Exam 1
## Domain 4: Secure Software Architecture and Design (18 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A financial technology (FinTech) startup is building a brand new microservices architecture for their mobile banking app. The Chief Architect mandates a strict zero-trust approach between all internal backend services. One critical developer explicitly asks: "If the 'Payment Gateway Service' needs to talk to the 'User Ledger Service,' how exactly should they mathematically prove their identities to each other without passing passwords back and forth in plaintext over the internal network?" Which of the following architectural implementations is the MOST robust and standard solution to fulfill this zero-trust inter-service authentication requirement?**
A. Establishing a hardware-based IPsec VPN tunnel between the two Docker containers.
B. Implementing Mutual Transport Layer Security (mTLS) utilizing ephemeral cryptographic certificates issued by an internal Certificate Authority (CA).
C. Hardcoding a 256-bit symmetric AES key inside the configuration files of both services to act as a shared secret.
D. Utilizing the OAuth 2.0 "Authorization Code Flow with PKCE" specifically designed for machine-to-machine backend communication.

#### **2. You are leading a Threat Modeling workshop for a new IoT smart home platform using the STRIDE methodology. A senior engineer points at a specific data flow arrow on the Data Flow Diagram (DFD) representing the connection between the user's mobile app and the cloud backend. She states: "If an attacker on the same local Wi-Fi intercepts this traffic, they could secretly read the user's home security camera logs." According to the STRIDE model, which specific threat category is the engineer identifying, and what is the standard architectural mitigation?**
A. Threat: Tampering. Mitigation: Implement Digital Signatures.
B. Threat: Elevation of Privilege. Mitigation: Enforce strict Role-Based Access Control (RBAC).
C. Threat: Information Disclosure. Mitigation: Encrypt the data in transit using TLS 1.3.
D. Threat: Repudiation. Mitigation: Implement comprehensive, immutable logging.

#### **3. The enterprise security architecture board is reviewing a monolithic legacy application that consists of 2 million lines of code running on a single massive application server. A critical vulnerability in the "Avatar Upload Component" allows an attacker to execute arbitrary OS commands. Because the application runs as a single process with administrative privileges, the attacker immediately gains total control over the entire database and the underlying operating system. To fundamentally prevent this total system compromise in the future, which core architectural security principle MUST be applied to restructure this monolithic beast?**
A. The Principle of Open Design
B. The Principle of Separation of Privilege (Compartmentalization)
C. The Principle of Psychological Acceptability
D. The Principle of Failsafe Defaults

#### **4. A cloud architect is designing the identity management strategy for a massive B2B SaaS platform that serves hundreds of different corporate clients. The sales team's primary requirement is: "Our corporate clients refuse to create new passwords for our SaaS. They demand that their employees use their existing corporate Windows Active Directory logins to access our cloud platform seamlessly." To satisfy this architectural demand for Identity Federation, which of the following standard protocols should the architect implement?**
A. Simple Directory Access Protocol (LDAP) combined with NTLMv2
B. Security Assertion Markup Language (SAML) 2.0 or OpenID Connect (OIDC)
C. Extensible Authentication Protocol (EAP) over TLS
D. Fast Identity Online (FIDO2) WebAuthn

#### **5. During the initial design phase of a highly classified military communications application, the lead cryptographer mandates: "If an adversary compromises our server today and steals the RSA private key we are currently using for TLS connections, they MUST NOT be able to use that stolen key to decrypt the mountains of intercepted, encrypted network traffic they recorded from us over the past five years." What advanced cryptographic design feature is the cryptographer demanding to ensure the historical confidentiality of the data?**
A. Perfect Forward Secrecy (PFS) utilizing Ephemeral Diffie-Hellman (DHE or ECDHE) key exchange algorithms.
B. Utilizing AES-256 in Galois/Counter Mode (GCM) for extremely fast symmetric encryption.
C. Implementing Quantum Key Distribution (QKD) across the entire fiber-optic network.
D. Forcing strict Certificate Pinning within the mobile client application.

#### **6. A junior developer is tasked with designing the "Password Storage Module" for a new web forum. He proudly presents his design to the Security Review Board: "To ensure blazing-fast login performance, I have decided to store all user passwords in the database after hashing them once using the incredibly fast MD5 algorithm." The Security Architect immediately rejects the design, shouting: "MD5 is dead for a reason! An attacker with a cheap GPU rig can brute-force crack millions of those hashes per second using a rainbow table!" To mathematically slow down the attacker and make off-line dictionary attacks economically unfeasible, what specific cryptographic technique MUST the developer implement?**
A. Encrypt the database hard drives using Microsoft BitLocker or Linux LUKS.
B. Switch to the SHA-256 algorithm completely unmodified, as it is NSA-approved.
C. Implement a slow, computationally expensive Key Derivation Function (KDF) such as PBKDF2, bcrypt, or Argon2, combined with a unique cryptographic Salt for each user.
D. Utilize an asymmetric RSA-4096 public key to encrypt the passwords before storing them.

#### **7. An architect is designing a highly scalable, stateless RESTful API destined for the public internet. The frontend SPA (Single Page Application) needs to prove its identity to the backend API without maintaining traditional server-side session cookies. The architect decides to use JSON Web Tokens (JWT) passed in the `Authorization: Bearer` header. However, a major security flaw in the standard JWT specification severely dictates how the architect must handle token invalidation. What is the fundamental, architectural weakness of stateless JWTs when a user clicks the "Logout" button or a token is stolen?**
A. They require massive database lookup overhead for every single API request, killing performance.
B. They are inherently unencrypted and transmit user data in plaintext base64, easily sniffed by attackers.
C. A stateless JWT cannot be individually revoked or invalidated before its built-in expiration time (`exp`) is reached unless complex, stateful token revocation lists (blacklists) are awkwardly introduced to the architecture.
D. They are completely incompatible with modern OAuth 2.0 flows and Active Directory.

#### **8. The infrastructure team proposes a new architecture for the corporate DMZ. They plan to place the Web Server, the Application Business Logic Server, and the massive Backend Database Server all on the exact same physical machine placed directly behind the perimeter firewall. The CISO vehemently vetoes this design, citing a massive violation of a classic network security principle. The CISO demands that the architecture be split into a "Three-Tier Architecture" with strict firewalls placed *between* the Web, App, and Database layers. What foundational security principle is the CISO attempting to enforce by slicing the network into distinct, firewalled zones?**
A. Defense in Depth (Layered Defense)
B. The Principle of Complete Mediation
C. The Principle of Least Common Mechanism
D. The Security through Obscurity paradigm

#### **9. When designing a secure logging and auditing capability for a centralized log server (e.g., Splunk or ELK stack), the architect must ensure that attackers who successfully breach a web server cannot simply delete their tracks by altering the logs they just sent to the central server. Which of the following architectural designs provides the STRONGEST guarantee of log integrity and prevents post-compromise tampering by the attacker?**
A. Storing the logs in a traditional SQL database table indexed by timestamp.
B. Pumping the logs into a "Write-Once, Read-Many (WORM)" immutable storage bucket and cryptographically signing the log chains.
C. Zipping and password-protecting the daily log files using a 4-digit PIN.
D. Storing the logs in volatile RAM on the central server for faster search querying.

#### **10. A cloud-native application is being built using AWS cloud services. The architecture requires a backend Lambda function (compute) to read sensitive customer photos stored in an S3 bucket (storage). The junior developer suggests creating a permanent IAM user named "lambda-user," generating long-lived Access Keys, and hardcoding those keys directly into the Lambda function's source code so it can access the bucket. In modern secure cloud architecture, this is considered a catastrophic anti-pattern. What is the standard, secure architectural method for granting the Lambda function the necessary permissions?**
A. Passing the Root account credentials to the Lambda function via environment variables.
B. Making the S3 bucket entirely public and utilizing obscure, unguessable file names (Security by Obscurity).
C. Assigning a temporary IAM Role directly to the Lambda function's execution environment, allowing the cloud infrastructure to automatically rotate and inject short-lived, ephemeral credentials.
D. Requiring the Lambda function to perform a CAPTCHA challenge before downloading

#### **11. You are applying the STRIDE threat modeling framework to a proposed architecture for managing electronic medical records. You identify a potential flaw where a malicious nurse could alter a patient's dosage record, and the system would have absolutely no way to prove *who* actually changed the data. Which specific STRIDE threat category does this inability to trace an action back to an individual represent, and what is the required architectural control?**
A. Threat: Information Disclosure. Control: Data Masking.
B. Threat: Denial of Service. Control: Rate Limiting.
C. Threat: Repudiation. Control: Non-repudiation via comprehensive Audit Trails and Digital Signatures.
D. Threat: Spoofing. Control: Strong Password Policies.

#### **12. A software architect is reviewing an application that utilizes an older XML parser. The application accepts XML files uploaded by users to generate PDF invoices. The security team demonstrates a terrifying attack: they upload a specially crafted XML file containing a `<!ENTITY>` directive that instructs the XML parser to silently read the contents of the server's `/etc/passwd` file and embed it into the final PDF output. What specific architectural vulnerability is the application suffering from, and how must it be mitigated at the design level?**
A. Vulnerability: Cross-Site Request Forgery (CSRF). Mitigation: Use Anti-CSRF tokens.
B. Vulnerability: Buffer Overflow. Mitigation: Switch from C++ to a memory-safe language like Rust.
C. Vulnerability: XML External Entity (XXE) Injection. Mitigation: The architect must explicitly configure the XML parser library to aggressively disable DTDs (Document Type Definitions) and forbid the resolution of external entities.
D. Vulnerability: SQL Injection. Mitigation: Implement an Object-Relational Mapper (ORM).

#### **13. During the architecture design phase of an API gateway that will be exposed to the public internet, the lead engineer is terrified of "Resource Exhaustion" attacks (Layer 7 DDoS), where an attacker writes a simple script to call the `/api/v1/heavy-calculate` endpoint 10,000 times per second, instantly melting the backend databases. To protect the backend services, which classic architectural defense pattern MUST be implemented directly at the API gateway layer?**
A. Implementing rigorous Input Validation to check for SQL injection characters.
B. Enforcing strict Rate Limiting and Throttling controls per API key or IP address.
C. Utilizing a Global Server Load Balancing (GSLB) algorithm based on geographic latency.
D. Encrypting all backend database communication with TLS 1.3.

#### **14. When designing the administrative backend interface for a sprawling content management system (CMS), the architect creates three distinct roles: "Content Writer," "Editor," and "Super Administrator." The architect strictly enforces a rule: A Content Writer can draft an article, but they are physically locked out of the "Publish" button. Only an Editor, using a separate account, can review the draft and click "Publish." What foundational security design principle is the architect implementing to prevent a single rogue writer from bringing down the website with terrible content?**
A. The Principle of Complete Mediation
B. The Principle of Defense in Depth
C. Separation of Duties (Two-Man Rule)
D. The Principle of Failsafe Defaults

#### **15. A software team is building an open-source password manager application. The community raises a massive concern: "If the government subpoenas your servers, or if a rogue database admin goes rogue, they could steal all our encrypted password vaults!" To fundamentally architect the system so that *even the application creators and database administrators* mathematically cannot decrypt the user's data, which specific cryptographic architecture MUST be enforced?**
A. Transparent Data Encryption (TDE) managed by the cloud provider.
B. End-to-End Encryption (E2EE) / Client-Side Encryption, where the decryption keys are generated and held exclusively on the user's local device and are NEVER transmitted to the server.
C. Wrapping the entire database in an AES-256 encrypted volume using a key managed by a Hardware Security Module (HSM) in the data center.
D. Enforcing strict Multi-Factor Authentication (MFA) for the database administrators.

#### **16. An experienced architect is designing an authentication microservice. Currently, the system responds to a failed login for a non-existent username with: `"Error: Username does not exist."` And it responds to a failed login for a valid username but wrong password with: `"Error: Incorrect password."` The security review board rejects this design, stating it violates a core concept of preventing Information Disclosure. What is the standard architectural fix to mitigate this specific vulnerability?**
A. The system must deliberately pause for 30 seconds before returning the error message to slow down the attacker.
B. The system must return a generic, unified error message such as `"Invalid username or password"` regardless of which part of the credential was wrong, preventing "Username Enumeration."
C. The system must immediately lock the public IP address after the first failed attempt to prevent brute forcing.
D. The system must demand the user solve a complex CAPTCHA before displaying the exact error message.

#### **17. A banking application needs a secure way to allow a third-party accounting application (like Mint or Xero) to "read-only" a user's transaction history without the user ever sharing their actual banking password with the accounting app. Which standardized delegation protocol is specifically designed at the architectural level to allow a user to grant limited access to their resources to a third-party application via a scoped token?**
A. SAML 2.0 Identity Federation
B. Kerberos Key Distribution Center (KDC)
C. OAuth 2.0 (Authorization Framework)
D. Lightweight Directory Access Protocol (LDAP)

#### **18. In the context of secure architectural design patterns, the concept of a "Choke Point" or "Single Point of Access Control" is highly recommended for filtering incoming traffic. If a web application forces every single incoming HTTP request to pass through a singular, heavily fortified logic module that validates authentication, authorization, and input sanitization BEFORE routing the request to the internal business logic, this monolithic gatekeeper is an application of which fundamental security principle?**
A. The Principle of Weakest Link Optimization
B. The Principle of Economy of Mechanism
C. The Principle of Complete Mediation
D. The Principle of Open Design
