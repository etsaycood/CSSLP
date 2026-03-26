# Exam 3
## Domain 4: Secure Software Architecture and Design (18 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A senior security architect is designing a high-security microservices-based application for processing classified military data. The architect mandates a Zero Trust capability where every single API call between the internal microservices (e.g., the User Service calling the Billing Service) must be explicitly authenticated and cryptographically secured using mutual TLS (mTLS). They state developers should NOT have to write this complex mTLS logic and certificate rotation code into every single application container. What architectural pattern is BEST suited to automatically inject and enforce this requirement infrastructure-wide?**
A. Deploy a centralized Web Application Firewall (WAF) in front of the Kubernetes cluster.
B. Implement a Service Mesh (e.g., Istio, Linkerd) with sidecar proxies attached to every microservice container.
C. Utilize an API Gateway at the perimeter of the cloud architecture.
D. Mandate that all developers write a standardized internal authentication library using AES-256 for all traffic.

#### **2. A software engineering team is building a decentralized peer-to-peer cryptocurrency exchange. To completely eliminate the risk of a single central authority unilaterally altering the transaction history, the architectural design explicitly mandates that the entire decentralized network must reach a mathematical consensus before any new block of transactions can be appended to the immutable, chronologically chained, distributed ledger. What fundamental cryptographic data structure defines this underlying architecture?**
A. A relational SQL database utilizing strict ACID (Atomicity, Consistency, Isolation, Durability) properties.
B. A NoSQL Key-Value Store optimized for eventual consistency.
C. A Blockchain architecture (utilizing cryptographic hashing linking).
D. A centralized Git repository.

#### **3. An e-commerce platform's monolithic architecture has become too large to maintain, causing slow deployments. The architect decides to physically break the application apart so that the "Inventory Module," the "Shopping Cart Module," and the "Payment Processing Module" are entirely independent programs running in their own isolated Docker containers. They will now communicate exclusively through well-defined, lightweight RESTful web APIs over the network. What fundamental software architectural pattern has the team just adopted?**
A. Service-Oriented Architecture (SOA)
B. Microservices Architecture
C. Client-Server Architecture
D. Peer-to-Peer (P2P) Architecture

#### **4. A company adopts an architectural design strategy conceptually built entirely on the premise of absolute paranoia: "Never trust, always verify." Regardless of whether an employee is sitting physically inside the heavily guarded corporate headquarters on the internal LAN, or working from a coffee shop in another country, every single attempt to access any corporate resource must dynamically evaluate the user's identity, the health and patch level of their device, and the context of the request before granting limited access. What is the name of this prevailing security architectural paradigm?**
A. Defense in Depth (Layered Defense)
B. Single Sign-On (SSO) Federation
C. Zero Trust Architecture (ZTA)
D. Endpoint Detection and Response (EDR)

#### **5. An architect is applying the foundational security design principle of "Economy of Mechanism." During the design review of a new financial application's authentication module, they notice the developers have implemented three different custom authentication protocols, connected to four different identity providers, and added complex fallback logic if any step fails. The architect orders the team to rip out the complex logic and replace it with a single, universally standardized SAML 2.0 integration. What is the primary theoretical justification, based on the principle of "Economy of Mechanism," for doing this?**
A. SAML 2.0 is fundamentally unbreakable by modern quantum computers.
B. Complex, convoluted security designs inherently create more opportunities for critical bugs, configuration errors, and hidden vulnerabilities than simple, elegant, and standardized designs (KISS principle).
C. Keeping the mechanism simple makes it easier to pass the blame to the SAML provider if a breach occurs.
D. The economy of mechanism principle dictates that software should always use the cheapest open-source libraries available to save money.

#### **6. A banking application's architectural design document explicitly dictates: "The code that dictates how the colorful user interface buttons are rendered on the screen MUST be physically and logically separated from the backend code that queries the secure SQL database for account balances." The developers are instructed to build this using a strict Model-View-Controller (MVC) software pattern. Which fundamental secure design principle is this software architecture primarily attempting to enforce?**
A. Fail-Safe Defaults
B. Open Design
C. Separation of Duties
D. Separation of Domains / Separation of Concerns (Modularity)

#### **7. A cloud architect is designing a highly sensitive data processing pipeline. They require a specialized, physically isolated hardware appliance dedicated entirely to securely generating, storing, and managing the absolute highest-tier encryption root keys used by the enterprise. This device must be mathematically proven to be tamper-resistant, automatically zeroizing its memory if a physical intrusion is detected. What highly specialized hardware component MUST the architect include in the infrastructure design?**
A. A Trusted Platform Module (TPM) chip on every developer's laptop.
B. A Hardware Security Module (HSM).
C. A dedicated Virtual Private Network (VPN) concentrator.
D. A Web Application Firewall (WAF).

#### **8. A design team is outlining the authorization logic for a new medical records system. The lead security architect enforces the following rule: "By absolute default, when a new doctor's account is created, they are implicitly denied access to ALL patient records. If they attempt to open a file, the system must definitively block them unless a specific, explicit rule has been mapped to their profile explicitly granting them 'Read' access to that specific ward." This design fundamentally embodies which core security principle?**
A. Principle of Least Privilege
B. Fail-Safe Defaults (Implicit Deny)
C. Complete Mediation
D. Psychological Acceptability

#### **9. A software development team builds an enterprise password vault application. To convince the Chief Information Security Officer (CISO) that their encryption methodology is unbreakable, the lead developer proudly claims, "Our application is completely unhackable because we invented a highly complex, secret, proprietary mathematics encryption algorithm entirely from scratch, and we refuse to publish how it works, so no hacker can ever figure it out." The CISO immediately rejects the software. Which fundamental secure design principle did the developer blatantly violate?**
A. Separation of Privilege
B. Psychological Acceptability
C. Open Design (Kerckhoffs's Principle) / Avoid Security through Obscurity
D. Least Common Mechanism

#### **10. An architect is designing a heavily fortified system for processing nuclear launch sequences. The design mandates that an attacker cannot compromise the system by finding a single vulnerability in the perimeter firewall. Therefore, the architect designs a system requiring the attacker to bypass the edge firewall, then compromise the internal Intrusion Prevention System (IPS), then evade the host-based Endpoint Detection and Response (EDR) agent, and finally break the AES-256 database encryption. Which classical security architectural strategy relies on deploying multiple, independent layers of security controls?**
A. Zero Trust Architecture (ZTA)
B. Defense in Depth (Layered Defense)
C. Threat Modeling Analysis
D. Compartmentalization

#### **11. A developer is designing a function to process user uploaded profile pictures. The logic is designed as follows: "The system will accept the file, and then explicitly check the file extension against a predefined list of known bad extensions (e.g., .exe, .sh, .bat). If the extension is on this list, the file is blocked; otherwise, it is accepted and executed by the image processor." A security tester immediately flags this as a critical architectural flaw. What is the fundamental problem with this specific design approach?**
A. The list of bad extensions is too short and should include .txt files.
B. It relies on a "Blacklist" (Default Allow) approach, which is inherently flawed because hackers will easily bypass it by using unknown malicious extensions (e.g., .php5) that aren't on the list. It should use a "Whitelist" (Default Deny/Fail-Safe) approach instead.
C. Profile pictures should never be uploaded; users should only provide URLs to external images.
D. Checking file extensions is illegal under modern data privacy frameworks.

#### **12. A system architecture is designed such that every single time a user requests to download a highly sensitive financial report—even if they successfully downloaded that exact same report five minutes ago—the system physically intercepts the request dynamically. It then completely re-evaluates the user's current session token, their IP address, and their current RBAC permissions against the central directory to verify they still have authorized access at this exact microsecond, before releasing the file payload. Which fundamental security design principle guarantees that authorization checks cannot be permanently bypassed or cached?**
A. Complete Mediation
B. Least Privilege
C. Separation of Duties
D. Economy of Mechanism

#### **13. A large financial institution is designing a distributed ledger application to facilitate cross-border currency exchanges. The primary architectural requirement is that the system must inherently prevent a malicious bank from denying that they initiated a specific trillion-dollar transfer request, providing indisputable mathematical evidence to a third-party auditor in the event of a dispute. Which specific security service must the architecture definitively provide to satisfy this requirement?**
A. Availability
B. Confidentiality
C. Non-Repudiation (via Digital Signatures)
D. Forward Secrecy

#### **14. During the design phase of a new operating system's kernel, the architects decide that the highly sensitive code responsible for managing raw memory allocation and talking directly to the actual hardware (CPU, Disk) will run in an isolated memory space called "Ring 0." Conversely, normal, untrusted user applications like web browsers will be forced to operate in "Ring 3," meaning they cannot touch hardware directly and must ask the kernel for permission via strict system calls. What foundational operating system security concept does this design implement?**
A. Virtualization (Hypervisor)
B. Protection Domains / Execution Rings (Privilege Separation)
C. Cryptographic Sandboxing
D. Trusted Execution Environment (TEE)

#### **15. A developer is tasked with designing the session management architecture for a high-traffic web application. They decide to store the user's authenticated session state, permissions list, and shopping cart directly inside a large JSON Web Token (JWT) sent back to the user's browser, rather than storing this information in a backend database tables (stateful). This allows the backend servers to scale effortlessly because any server can mathematically verify the token without looking up a database. What is a primary, potentially critical security drawback of choosing this specific "Stateless/Client-Side Token" architectural design over traditional server-side sessions?**
A. JWTs are fundamentally impossible to encrypt, making them highly vulnerable to interception over HTTPS.
B. Because the state is stored on the client side, forcibly invalidating or immediately revoking an active, unexpired JWT (e.g., if the user clicks "Logout" or is fired) is architectural exceedingly difficult without maintaining a complex, centralized "blacklist" on the server.
C. Browsers automatically delete JWTs every time the user closes a single tab.
D. JWTs mandate the use of symmetric encryption, which is illegal for web applications.

#### **16. A security architect mandates that a new financial trading application must utilize public-key cryptography (PKI) for all secure communications. Specifically, they require that if a hacker somehow manages to perfectly compromise and steal the server's long-term private RSA key today, that hacker must still be mathematically incapable of decrypting the terabytes of historical, intercepted encrypted traffic they recorded from the server over the past five years. What specific cryptographic property must the architect require the TLS configuration to support?**
A. Perfect Forward Secrecy (PFS) (e.g., using Ephemeral Diffie-Hellman [DHE/ECDHE])
B. Non-repudiation (using Digital Signatures)
C. Hashing (e.g., SHA-256)
D. Symmetric Key Wrapping (e.g., AES Key Wrap)

#### **17. A team is designing a serverless architecture using AWS Lambda functions. To adhere to the principle of "Least Privilege," the architect enforces a strict policy: The Lambda function named `ReadUserProfile` is assigned an IAM role that explicitly allows `Update` access to the `Users` DynamoDB table but implicitly denies access to the `Passwords` table. Which crucial aspect of the "Least Privilege" principle did the architect misconfigure in this design?**
A. Giving raw database access to any serverless function is a violation; they must only go through an API Gateway.
B. The function should be granted `AdministratorAccess` temporarily during execution for maximum flexibility.
C. The privileges define the WRONG action: The function is named `ReadUserProfile` but was granted `Update` access, rather than strictly `Read/GetItem` access, granting unnecessary modification capabilities.
D. Serverless functions inherently run as root, so IAM policies are irrelevant.

#### **18. An enterprise architect is designing a massive customer portal. They decide that instead of forcing users to create a brand-new username and password for this specific portal, the architecture will allow users to click a button and authenticate using their existing Google, Facebook, or Enterprise Active Directory accounts. The underlying protocol will pass an asserted "token" from the Identity Provider to the portal. What architectural pattern is the enterprise adopting to vastly improve user experience and centralize identity management?**
A. Discretionary Access Control (DAC)
B. Federated Identity Management (FIM) / Single Sign-On (SSO) (e.g., OAuth 2.0, SAML, OIDC)
C. Multi-Factor Authentication (MFA)
D. Role-Based Access Control (RBAC)
