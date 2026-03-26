# Exam 2
## Domain 4: Secure Software Architecture and Design (18 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. To design a secure backend administrative portal, the architect ensures that a 'Customer Support Agent' profile can search for and view a user's account details, but mathematically cannot click the button to issue financial refunds. Only a 'Support Manager' profile possesses the system rights to process refunds. This deliberate architectural design strictly enforces which fundamental security principle?**
A. Open Design
B. Principle of Least Privilege (PoLP)
C. Fail Secure
D. Defense in Depth

#### **2. A robust financial payment processing system is designed so that if the central authentication database suddenly crashes or loses network connectivity, the application immediately drops all active sessions, denies all new login attempts, and displays a generic "System Offline" error message to the internet, rather than bypassing the login check to keep the business running. Which core security design principle is this system successfully demonstrating?**
A. Fail Safe / Fail Secure
B. Psychological Acceptability
C. Economy of Mechanism
D. Complete Mediation

#### **3. During an architectural code review of a monolithic application, a senior security engineer notices a flaw: the system rigorously checks a user's permissions when they first log in and download a sensitive file, but it caches that 'Authorized' token indefinitely. If the user's account is subsequently suspended by an administrator five minutes later, the user can still continue to download other sensitive files for the rest of the day using the cached session. The architect failed to implement which fundamental security principle?**
A. Obscure Design
B. Separation of Duties
C. Complete Mediation
D. Least Common Mechanism

#### **4. A startup's highly confident Chief Technology Officer (CTO) decides to develop a proprietary, custom-built cryptography algorithm for their new secure messaging app. The CTO argues to the board that because the mathematical formulas are heavily obfuscated and kept entirely secret from the public, hackers will never figure out how to crack the messages. Which time-tested cryptographic and architectural design principle is the CTO blatantly violating?**
A. Open Design (Kerckhoffs's Principle)
B. Defense in Depth
C. Tokenization
D. Steganography

#### **5. An enterprise architect designs a modernized e-commerce platform that places a highly intelligent Web Application Firewall (WAF) at the cloud edge, enforces mandatory Multi-Factor Authentication (MFA) for the application layer login, and mandates hardware AES-256 encryption for the backend database at rest. This overlapping, multi-tiered structural strategy is the textbook definition of which architectural concept?**
A. Single Point of Failure
B. Defense in Depth (Layered Security)
C. Microsegmentation
D. Data Minimization

#### **6. The IT security team mandates a new architectural rule: all employee passwords must be entirely randomly generated, exactly 32 characters long, contain absolutely no dictionary words, and must be forcibly changed every 14 days. Within a week of rollout, the physical security team discovers that 80% of employees are writing their 32-character passwords on yellow sticky notes attached directly to their monitors. The security team's draconian design failed which core principle of secure architecture?**
A. Complete Mediation
B. Compromise Recording
C. Psychological Acceptability (or Acceptability of Security Controls)
D. Fail Secure

#### **7. A sprawling legacy web application currently exposes 45 different API endpoints to the public internet. However, backend analytics show that only 12 of these endpoints are actually used by today's modern frontend clients. As part of a major Q3 redesign, the lead architect decides to permanently delete the 33 entirely unused API endpoints and aggressively remove all their underlying source code from the repository. What is the primary security benefit of this specific architectural decision?**
A. It provides automatic Database Activity Monitoring.
B. It implements strong Cryptographic Non-repudiation.
C. Attack Surface Reduction.
D. It guarantees the application is now GDPR compliant.

#### **8. A company is rapidly migrating from a legacy monolithic architecture to a modern, Zero-Trust Microservices architecture orchestrated entirely by Kubernetes. In this highly hostile internal environment, to ensure that "Payment Service A" mathematically and cryptographically proves its exact identity before communicating with "Ledger Service B" over the internal network, what specific architectural standard MUST be implemented?**
A. Mutual TLS (mTLS)
B. Base64 Encoding
C. IP Address allow-listing
D. Cross-Origin Resource Sharing (CORS)

#### **9. To structurally defend a massive user credential database against catastrophic, pre-computed dictionary attacks and devastating Rainbow Tables, what mandatory cryptographic architectural component MUST the developers implement immediately alongside a strong hashing algorithm (like Argon2 or bcrypt)?**
A. A secondary Web Application Firewall (WAF).
B. A unique, cryptographically random Salt for every individual user password.
C. A VPN connection for all users.
D. Data Masking to hide the passwords on the screen.

#### **10. An innovative medical startup wants to accept patient credit card payments directly. However, the CEO explicitly demands that the company entirely avoid the massive, million-dollar regulatory burden and overwhelming scope of passing a full PCI-DSS audit. What specific data security architectural pattern can the architects implement to replace the real, highly sensitive Credit Card Numbers (PAN) with mathematically unrelated, useless surrogate values right at the entry point, ensuring the real PAN never actually enters the startup's backend database?**
A. Full Disk Encryption (FDE)
B. Digital Signatures
C. Tokenization
D. Elliptic Curve Cryptography (ECC)

#### **11. The development team decides to implement a powerful API Gateway at the absolute external boundary of their sprawling microservices ecosystem. From a Secure Architecture perspective, what is the primary structural security advantage of forcing all inbound internet traffic to route through this singular API Gateway?**
A. It eliminates the need for any backend databases.
B. It provides a centralized, single point of enforcement (choke point) for vital controls like rate-limiting, authentication routing, and TLS termination before any traffic ever touches the fragile internal microservices.
C. It ensures the application code runs 50% faster.
D. It automatically fixes all SQL Injection vulnerabilities in the developers' code.

#### **12. A heavily trafficked, modern web application relies heavily on stateless JSON Web Tokens (JWT) for user session management. To architecturally and structurally prevent a standard Cross-Site Scripting (XSS) attack from allowing a hacker's injected malicious JavaScript payload from quietly stealing the active JWT directly out of the victim's browser, where is the ONLY technically secure place the architect should instruct the frontend developers to store the token?**
A. Inside HTML5 `localStorage`
B. Inside HTML5 `sessionStorage`
C. As a URL parameter query string
D. Inside an `HttpOnly`, `Secure` flagged cookie

#### **13. While designing a highly automated Continuous Integration / Continuous Deployment (CI/CD) pipeline for AWS cloud infrastructure, the Lead Cloud Architect mandates that all infrastructure (VPCs, Security Groups, IAM Roles, S3 Buckets) must be written exclusively as Terraform code, and strictly forbids any engineer from clicking through the AWS web console to create resources. What is the primary DevSecOps advantage of this "Infrastructure as Code" (IaC) design pattern?**
A. It provides 100% immunity against Zero-Day malware.
B. It eliminates the need to pay AWS monthly billing fees.
C. It allows the infrastructure architecture itself to be heavily version-controlled in Git, repeatedly peer-reviewed, and automatically scanned for catastrophic misconfigurations (like open S3 buckets) using static analysis tools long before it is actually deployed.
D. It automatically translates Terraform code into Java applications.

#### **14. A global organization is designing a modern Single Sign-On (SSO) architecture using SAML 2.0 to seamlessly connect their internal HR portal, enterprise email, and travel expense system. While SSO massively improves usability and completely eliminates password fatigue for the employees, what is the primary architectural security RISK inherently introduced by this design?**
A. It requires users to memorize 15 different passwords.
B. It structurally creates a massive Single Point of Compromise/Failure; if the central Identity Provider (IdP) is successfully breached by a hacker, the attacker gains immediate, frictionless access to all downstream connected applications.
C. It violates the GDPR Right to be Forgotten.
D. It prevents the use of Multi-Factor Authentication (MFA).

#### **15. A DevOps architect is containerizing a brittle, legacy Linux Java application using Docker to move it to the cloud. During an automated design review, a DevSecOps engineer immediately rejects the `Dockerfile` because the script naturally defaults to executing its main application process using the absolute highest permissions. To adhere to strict container security best practices and prevent catastrophic "container escape/breakout" attacks, what specific directive MUST be added to the Dockerfile architecture?**
A. The `USER` directive, explicitly forcing the application to run as a non-root, severely limited-privilege user account.
B. The `EXPOSE 8080` directive to open ports.
C. The `FROM ubuntu:latest` directive.
D. The `CMD ["java", "-jar", "app.jar"]` directive.

#### **16. To physically protect the highly sensitive "Master Encryption Key" used by the financial application, the enterprise architecture team decides to deploy a dedicated, military-grade Hardware Security Module (HSM) appliance deep in the data center. Furthermore, the architecture team intentionally designs a procedural access control process where unlocking the "Master Password" to this HSM structurally requires a physical smartcard inserted by the CEO, a complex PIN typed by the Chief Financial Officer (CFO), and a live biometric fingerprint scan from the Chief Information Security Officer (CISO) all submitted simultaneously. This extreme design flawlessly implements which foundational security principle?**
A. Open Design
B. Complete Mediation
C. Separation of Duties (Split Knowledge / Dual Control)
D. Economy of Mechanism

#### **17. A junior developer is designing a function that calculates the highly regulated compliance tax on a user's shopping cart. The senior architect reviews the module and observes that the developer proudly wrote 500 lines of highly complex, convoluted, and deeply nested custom mathematical logic instead of simply importing the standard, heavily vetted, 3-line built-in tax library. The architect immediately rejects the codebase, stating that unnecessary complexity represents a massive breeding ground for hidden structural security bugs. The architect's rejection aligns fundamentally with which design principle?**
A. Least Common Mechanism
B. Economy of Mechanism (Keep it Simple, Stupid - KISS)
C. Psychological Acceptability
D. Defense in Depth

#### **18. A cutting-edge application is being designed entirely on an AWS Serverless architecture using thousands of event-driven Lambda functions. Because these tiny compute functions are purely ephemeral (they spin up, execute, and die in milliseconds), traditional heavyweight endpoint antivirus (EDR) agents physically cannot be installed on them. Because the traditional server perimeter is gone, what is the MOST critical architectural defense the architect must configure to secure these Serverless functions from running amok if compromised?**
A. Installing a hardware firewall in the local office branch.
B. Enforcing microscopically scoped, highly fine-grained IAM (Identity and Access Management) execution roles, ensuring each specific Lambda function mathematically only possesses the exact permissions it needs to perform its one job, and absolutely nothing more.
C. Forcing all Lambda functions to run in a single, massive monolithic container.
D. Encrypting the AWS billing console.
