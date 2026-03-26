# Domain 7: Secure Software Deployment, Operations, Maintenance (14 Questions)

#### **1. A deployment team is preparing to migrate an application from the Staging environment to Production. Which of the following is the MOST critical operational risk analysis task the team must perform specifically regarding the environment differences?**
A. Fuzzing the API endpoints in Production
B. Verifying that the application behaves identically under the stricter, highly restricted access controls of Production compared to the relaxed Staging environment
C. Validating the entropy of the Random Number Generator
D. Compiling the source code using the SAST engine

*   **Answer: B**
*   **Rationale:** **Operational Risk Analysis regarding Deployment Environments** necessitates acknowledging that environments differ. Staging often has relaxed permissions (like open firewall ports or shared credentials) for testing. Migrating to Production (where Least Privilege is strictly enforced) often causes applications to break if they hard-code permissions or rely on staging-specific lax topologies.

#### **2. An e-commerce platform stores payment gateway keys and database connection strings in plain-text inside the `application.properties` configuration file deployed alongside the code. A security architect mandates that these secrets be removed and managed centrally. What is the BEST architectural solution to securely store and manage these credentials at runtime?**
A. Encrypting them and storing the key in the source code repository.
B. Utilizing a dedicated secrets management vault (like HashiCorp Vault or AWS Secrets Manager) and injecting them into the application at runtime.
C. Storing them in the database and passing them via HTTP headers.
D. Using Cryptographic hashes (SHA-256) instead of the actual passwords.

*   **Answer: B**
*   **Rationale:** **Storing and Managing Security Data** mandates that highly sensitive infrastructure secrets (Keys, Certificates, API tokens, Credentials) must never be hardcoded into configuration files or version control. A dedicated, highly-available **secrets manager** provisions them dynamically to the application in memory at runtime.

#### **3. The development team has fully automated their pipeline using DevSecOps principles. Once a developer commits code, it passes a SAST scan, is compiled, containerized, and immediately deployed to the production cluster without manual human intervention. This pipeline describes a:**
A. Security reporting mechanism
B. Manual code review cycle
C. Secure Continuous Integration and Continuous Delivery (CI/CD) pipeline
D. Disaster Recovery Plan (DRP)

*   **Answer: C**
*   **Rationale:** A **Secure CI/CD Pipeline (DevSecOps)** integrates security testing tools automatically into the software development and deployment lifecycle. It allows for rapid, repeatable, and highly consistent **Secure Release** of software directly to production while maintaining security control gates.

#### **4. An organization purchases a complex commercial accounting software package. Before the IT team can install the software on the corporate network, a security engineer requires that the host server’s operating system be stripped of all unnecessary services, default passwords changed, and explicit firewall rules applied. This process is known as:**
A. Environment hardening
B. Runtime Application Self Protection (RASP)
C. Secure Boot
D. Version Control

*   **Answer: A**
*   **Rationale:** **Environment Hardening (Secure Installation)** is the systematic process of reducing the attack surface of the underlying infrastructure (OS, network, containers) that hosts the application by strictly applying secure baseline configurations and disabling all unneeded ports and services prior to software deployment.

#### **5. A critical application suffers a severe outage after a junior administrator accidentally applies a flawed configuration update directly to the production firewall. The incident response team restores service by quickly rolling back the firewall to its previous state. The team’s ability to perform this rapid rollback relies heavily on the organization maintaining:**
A. An application security toolchain
B. Rigorous secure configuration and version control of the baseline hardware/software configurations
C. A Security Information and Event Management (SIEM) dashboard
D. A business continuity plan for natural disasters

*   **Answer: B**
*   **Rationale:** Applying strict **Version Control** to **baseline configurations** (Infrastructure as Code) ensures that every change to production infrastructure is tracked and reversible. Without centralized version control, identifying the flawed change and rapidly rolling it back to a known-good state is nearly impossible.

#### **6. A newly deployed application exhibits strange behavior and frequently crashes under load. The operations team struggles to diagnose the root cause because the application produces only generic "System Error" messages and writes nothing to the `/var/log` directory. The application has fundamentally failed to provide the necessary data for:**
A. Integration analysis and continuous monitoring
B. Cryptographic validation
C. User provisioning and reapproval
D. Obfuscation of production data

*   **Answer: A**
*   **Rationale:** **Continuous Monitoring** and Incident Response are entirely dependent on **Observable data** (logs, events, telemetry, metrics, trace data). If an application does not natively emit detailed, structured audit logs, it creates an operational black hole, preventing operations teams or SIEM platforms from monitoring its health or detecting intrusions.

#### **7. During a high-stress production outage, the Incident Response team completes the Triage and Containment phases. They determine that a malicious web shell was uploaded to the server by exploiting a known vulnerability in an outdated image processing library. The final step of the Incident Response plan, designed to prevent this exact scenario from ever happening again, is:**
A. Remediating the vulnerability
B. Performing a formal Root Cause Analysis (Lessons Learned)
C. Forensic data collection
D. Deploying a Web Application Firewall (WAF)

*   **Answer: B**
*   **Rationale:** The ultimate goal of the Incident Response lifecycle is the **Root Cause Analysis (Lessons Learned)** phase. Identifying the systemic failure (e.g., a broken patch management process or a missing SCA scanner) allows the organization to update its SDLC policies and prevent recurrence, rather than just treating the symptom.

#### **8. The security operations center (SOC) detects an active, sophisticated SQL injection attack targeting an old legacy PHP application that the company cannot afford to rewrite or patch. To mitigate this immediate threat, the security engineer deploys an external appliance in front of the web server that analyzes incoming HTTP traffic and blocks the malicious SQL payloads before they reach the PHP code. This appliance is a:**
A. Runtime Application Self Protection (RASP) module
B. Web Application Firewall (WAF)
C. Static Application Security Testing (SAST) tool
D. Dynamic Execution Prevention switch

*   **Answer: B**
*   **Rationale:** A **Web Application Firewall (WAF)** is an external, network-based **Runtime Protection** mechanism that intercepts HTTP/S traffic, inspecting payloads for known web attacks (like SQLi or XSS) and blocking them, serving as a critical "virtual patch" for vulnerable legacy applications.

#### **9. Unlike a WAF, which sits externally on the network and guesses if traffic is malicious, a specific runtime protection technology is integrated directly into the application's runtime environment (like the JVM or CLR). This technology possesses deep introspection into the application's execution state, allowing it to accurately block a SQL injection only if it detects the application is actually attempting to execute a modified query. This technology is:**
A. Address Space Layout Randomization (ASLR)
B. Runtime Application Self Protection (RASP)
C. Dynamic Application Security Testing (DAST)
D. Secure boot

*   **Answer: B**
*   **Rationale:** **RASP (Runtime Application Self Protection)** resides *inside* the application runtime. Because it understands the application's internal state and execution flow, it can block attacks with extremely high accuracy and near-zero false positives compared to a network-based WAF, completely neutralizing zero-day exploits.

#### **10. A cloud-native application is designed so that if the primary database cluster in Availability Zone A physically burns down in a fire, an exact replica in Availability Zone B instantly takes over processing queries with zero downtime or data loss. The architects achieved this Continuity of Operations specifically by implementing:**
A. Backup and archiving
B. Resiliency (Operational Redundancy / Failover)
C. Change management
D. Personnel training

*   **Answer: B**
*   **Rationale:** **Resiliency and Operational Redundancy (Failover)** focuses on building highly robust architectures where secondary systems seamlessly take over for primary systems in the event of a catastrophic hardware failure, ensuring absolute maximum Availability (the 'A' in the CIA triad).

#### **11. An organization outsources the hosting and maintenance of its core CRM application to a third-party managed service provider. The security manager insists that the contract must legally dictate that the provider applies critical OS security patches within 48 hours of their release, or face severe financial penalties. This requirement is integrating security into:**
A. The Business Continuity Plan (BCP)
B. Service Level Agreements (SLA)
C. Interactive Application Security Testing (IAST)
D. The Assessment and Authorization (A&A) process

*   **Answer: B**
*   **Rationale:** **Service Level Agreements (SLAs)** are legally binding contracts that establish explicit, measurable performance expectations (like maintenance windows, minimum uptime percentages, or strict patching timelines), allowing organizations to hold third-party vendors financially accountable for security failures.

#### **12. A project sponsor declares that the newly built trading platform is ready for launch. Before it can go live, the Chief Information Security Officer (CISO) reviews the residual risk report, notes a few unmitigated medium-severity vulnerabilities, but formally signs a document accepting those risks because the business value of launching immediately outweighs the potential operational threat. The platform has officially received:**
A. A vulnerability scan report
B. A compiled binary
C. Security Approval to Operate (ATO)
D. An automated CI/CD pipeline integration

*   **Answer: C**
*   **Rationale:** **Obtaining Security Approval to Operate (ATO)** is the final, formal management sign-off milestone. A designated executive (like the CISO or Information System Owner) reviews the security posture and explicitly accepts the residual risks, authorizing the system to transition into the live production environment.

#### **13. Following the discovery of a major zero-day vulnerability (e.g., Log4Shell), a company spends three weeks manually scanning its servers with bespoke scripts to determine which systems are vulnerable, significantly delaying their remediation efforts. To solve this systemic failure, the organization must implement a robust:**
A. Cryptographic hashing protocol
B. Fuzz testing strategy
C. Vulnerability Management program (tracking, triaging, and CVE correlation)
D. Source code obfuscator

*   **Answer: C**
*   **Rationale:** An effective **Vulnerability Management** program continuously tracks the software and infrastructure inventory. When a new **CVE** is published, the program automatically cross-references the intelligence with the inventory, enabling rapid triage, impact analysis, and immediate, targeted remediation routing.

#### **14. During the implementation of a new DevSecOps pipeline, the security architect mandates that before any deployment script pushes a Docker container image to the production registry, it must mathematically verify that the image exactly matches the one generated by the approved build server. Which specific Build Artifact Verification technique accomplishes this?**
A. Checking the application's runtime telemetry
B. Performing a dynamic penetration test on the container
C. Using cryptographic hashes and digital signatures (Code Signing)
D. Verifying the application's SLA document

*   **Answer: C**
*   **Rationale:** **Build Artifact Verification** relies heavily on **hashes and code signing**. The authorized compile server calculates a hash of the container image and digitally signs it with a private key. The deployment server uses the public key to verify that the signature is valid and the hash matches, guaranteeing the artifact's integrity and provenance before running it in production.
