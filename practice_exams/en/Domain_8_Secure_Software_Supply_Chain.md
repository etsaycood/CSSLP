# Domain 8: Secure Software Supply Chain (12 Questions)

#### **1. A massive ransomware attack targets a company providing network monitoring software via an automatic update maliciously injected by hackers. Consequently, every enterprise customer who downloads this update is also compromised. This scenario represents the devastating and scalable nature of a:**
A. SQL Injection attack
B. Software Supply Chain attack
C. Denial of Service (DoS) attack
D. Privilege escalation vulnerability

*   **Answer: B**
*   **Rationale:** A **Software Supply Chain attack** targets a trusted third-party vendor or open-source component. By compromising ONE upstream supplier (like the SolarWinds incident), attackers instantly gain highly privileged access to thousands of downstream customers who trust and install that vendor's software updates.

#### **2. An engineering team relies heavily on a specialized set of third-party, open-source data visualization libraries to build their web application. To proactively identify if any of these imported libraries contain known vulnerabilities or restrictive licensing issues, the organization should implement:**
A. Dynamic Application Security Testing (DAST)
B. Manual Code Review
C. Software Composition Analysis (SCA) and maintain a Software Bill of Materials (SBOM)
D. Hardware-based Secure Boot

*   **Answer: C**
*   **Rationale:** **Software Composition Analysis (SCA)** automates the scanning of an application's dependencies to generate an **SBOM** (inventory list). It continuously monitors this list against global vulnerability bases (NVD/CVEs) to instantly flag when a third-party component becomes a risk.

#### **3. An enterprise is evaluating three different Cloud Service Providers (CSPs) to host their highly sensitive payroll architecture. The organization requires absolute proof that each CSP adheres strictly to global security standards before signing a contract. Which artifact should the organization request from the CSPs to analyze their third-party security posture?**
A. The source code of their hypervisors.
B. A fully detailed Threat Model from the CSP's internal engineering team.
C. Certifications and Assessment reports (e.g., SOC 2 Type II, ISO 27001, Cloud Security Alliance Controls Matrix - CAIQ).
D. The public SSH keys used by their administrators.

*   **Answer: C**
*   **Rationale:** When **Analyzing the security of third-party software** or providers, you cannot usually inspect their source code or internal threat models. Organizations must rely on standardized **Certifications and Assessment reports** performed by independent third-party auditors (like SOC 2 reports or the CSA's Cloud Controls Matrix) to verify the supplier's security claims.

#### **4. A developer downloads an open-source library named `react-utils` from a public repository. To verify the pedigree and provenance of this specific downloaded component—guaranteeing that it was indeed published by the official author and hasn't been backdoored in transit—the developer MUST rely on:**
A. Examining the application's runtime RASP logs.
B. Cryptographically-hashed, digitally-signed components.
C. Checking the length of the source code.
D. Executing the library in a sandbox for 5 minutes.

*   **Answer: B**
*   **Rationale:** **Verifying Pedigree and Provenance** involves ensuring origin and integrity. The only mathematically sound way to prove a downloaded file was created by the rightful owner (Provenance via Digital Signatures) and has not been altered (Integrity via Hashing) is using **cryptographically-hashed, digitally-signed components**.

#### **5. In preparation for a major procurement of commercial off-the-shelf (COTS) software, the legal and security teams draft a contract. The CISO inserts a critical, non-negotiable clause stating that the purchasing organization has the legal authority to hire an independent security firm to forcefully inspect the vendor’s internal security controls and facilities once a year to ensure compliance with the contract. This clause is known as the:**
A. End-User License Agreement (EULA)
B. Right to Audit clause
C. Code Repository Security mandate
D. Software Bill of Materials (SBOM) requirement

*   **Answer: B**
*   **Rationale:** The **Right to Audit** is a vital legal mechanism in supplier risk management. It explicitly binds the vendor to allow the customer (or a certified third party) to conduct invasive, objective security assessments to verify the vendor is actually practicing the security standards promised in the SLA.

#### **6. A company develops proprietary, closed-source financial software specifically for Wall Street trading firms. An ambitious developer decides to incorporate a highly efficient database caching library found on GitHub into the software. However, the library is licensed under the strict GNU General Public License (GPL) v3. What is the catastrophic risk of this action?**
A. The software will run 50% slower due to open-source overhead.
B. The company will be legally forced to open-source and publish their entire proprietary trading algorithm for free.
C. The software will fail SAST scans for cross-site scripting.
D. The company will have to pay the original author a 10% royalty on all sales.

*   **Answer: B**
*   **Rationale:** The GPL is a restrictive, "copyleft" or **viral license**. Incorporating GPL code into a commercial application mandates that the entire aggregate application be licensed under the GPL, forcing the company to publish its closely-guarded proprietary source code (a massive intellectual property loss). 

#### **7. An IT administrator needs to configure the package manager for the company's internal software build servers. To mitigate a specific type of supply chain attack, the administrator configures the servers to absolutely NEVER pull packages from public, untrusted repositories if an identically named package already exists in the company's private, trusted internal repository. This configuration specifically mitigates:**
A. Dependency Confusion (Namesquatting) attacks
B. SQL Injection
C. Physical theft of servers
D. Broken Access Control

*   **Answer: A**
*   **Rationale:** **Dependency Confusion** occurs when an attacker discovers a private, internal package name and publishes malicious code with the exact same name but a much higher version number out on the public internet (like NPM or PyPI). Poorly configured package managers will prioritize the higher version number and download the public malware instead of the private, safe code.

#### **8. An organization purchases critical, bespoke backend software heavily negotiated from a small, boutique software vendor consisting of only 5 employees. The organization is extremely concerned that if this small vendor goes bankrupt or closes its doors next year, the organization will lose all ability to fix bugs or update the software. What contractual requirement should the organization implement to mitigate this specific business risk?**
A. A strict Service Level Agreement (SLA) focused on API latency.
B. Source Code Escrow.
C. An End-User License Agreement (EULA).
D. Log integration into SIEM.

*   **Answer: B**
*   **Rationale:** **Source Code Escrow** involves using a trusted, neutral third-party agent to securely hold the vendor's highly proprietary source code. If a triggering event occurs (like the vendor going bankrupt or violating the support contract), the escrow agent releases the source code directly to the customer, ensuring business continuity.

#### **9. An organization is evaluating a vendor's supply chain security posture. The vendor states that their development teams operate "Hermetic Builds" on isolated servers with absolutely no internet access, and that every compile is strictly reproducible. This level of maturity aligns closely with which emerging supply chain security framework?**
A. Payment Card Industry (PCI) DSS
B. Supply-chain Levels for Software Artifacts (SLSA)
C. Health Insurance Portability and Accountability Act (HIPAA)
D. Common Vulnerability Scoring System (CVSS)

*   **Answer: B**
*   **Rationale:** The **SLSA (Supply-chain Levels for Software Artifacts)** framework is an industry effort specifically designed to secure the software build process against supply chain attacks. At its highest tiers (Level 4), it mandates extreme security measures like two-person reviews, hermetic build environments, and reproducible builds to guarantee artifact integrity.

#### **10. An incident response team discovers that a cloud-based vendor hosting the company's customer relationship management (CRM) database was utterly compromised by a nation-state actor for six months. However, the vendor hid the breach and only disclosed it to the organization after it was leaked to the press. Which critical component of the supplier acquisition contract did the vendor catastrophically violate?**
A. Requirement for maintenance and support community forums.
B. Incident notification, response, and timely reporting SLAs.
C. The shared responsibility model for infrastructure patching.
D. Log integration formatting requirements.

*   **Answer: B**
*   **Rationale:** **Ensuring supplier security requirements** demands strict, non-negotiable clauses defining exactly how rapidly a vendor must notify the customer of a suspected breach. Hiding an incident violates the **Vulnerability/incident notification and reporting** contracts, preventing the customer from protecting their data and triggering massive liability and SLA penalty clauses.

#### **11. A developer is browsing GitHub for a library that calculates complex date and time strings. They find a repository with millions of downloads but notice that the last commit was 8 years ago, there are 5,000 open unresolved issues, and the sole author's account is deleted. From a supply chain risk perspective, importing this library is highly dangerous because of the risk regarding its:**
A. Scope of testing and shared responsibility model
B. Origin and support (Maintenance structure)
C. Assessment reports (Cloud Controls Matrix)
D. Code obfuscation algorithms

*   **Answer: B**
*   **Rationale:** When analyzing third-party software, evaluating the **Maintenance and support structure (Origin and support)** is critical. Open-source libraries that are abandoned ("abandonware") will never receive security patches for newly discovered CVEs, making them a ticking time bomb if integrated into an enterprise application.

#### **12. The security architect defines a policy utilizing a "Shared Responsibility Model" for their cloud deployment. Under this model, if a hacker exploits a misconfigured S3 bucket (which was configured by the purchasing organization) to steal data, who is legally and operationally responsible for the breach?**
A. The Cloud Service Provider (e.g., AWS) because they own the physical hardware.
B. The open-source community that built the S3 underlying software.
C. The purchasing organization who misconfigured the bucket.
D. The End-User License Agreement (EULA) auditor.

*   **Answer: C**
*   **Rationale:** The **Shared Responsibility Model** makes it legally clear that while the Cloud Provider manages the security *OF* the cloud (physical data centers, hypervisors), the customer is 100% responsible for security *IN* the cloud, meaning the customer is solely accountable for network configurations, Identity and Access Management (IAM), data classification, and ensuring buckets aren't left globally readable.
