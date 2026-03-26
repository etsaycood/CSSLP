# Exam 4
## Domain 2: Secure Software Lifecycle Management (14 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. Your organization is adopting Agile (Scrum) for a new internal web application. The development team argues that conducting full, formal Threat Modeling sessions at the beginning of the project will take too long and violate the Agile principle of "working software over comprehensive documentation." As the security champion, what is the best approach to integrate threat modeling into an Agile lifecycle?**
A. Defer all threat modeling until the final integration testing phase right before the release sprint.
B. Mandate that the team halt all coding until a comprehensive STRIDE model for the entire system architecture is formally documented and approved by the CISO.
C. Break the threat modeling process into smaller, iterative sessions focused only on the specific User Stories being planned for the upcoming sprint.
D. Replace threat modeling entirely with automated SAST and DAST scanning in the CI/CD pipeline, as agile teams require automated tools instead of manual analysis.

#### **2. Which of the following software development metrics provides the MOST accurate indication of a development team's proactive engagement with the Secure Software Development Lifecycle (SSDLC) early in the process, rather than relying on reactive testing?**
A. The number of high-severity vulnerabilities discovered by the DAST scanner in the staging environment.
B. The percentage of developers who have completed mandatory secure coding training and the number of architecture flaws identified and fixed during early design reviews.
C. The total number of incidents reported by the Security Operations Center (SOC) after the application is deployed.
D. The percentage of code coverage achieved by automated unit tests.

#### **3. A financial software company is preparing for a mandatory regulatory compliance audit (e.g., PCI-DSS). The auditors will require verifiable proof that the software changes pushed to production over the past year have undergone rigorous security reviews and testing. What is the most critical asset the organization must maintain to survive this audit?**
A. A highly detailed, 500-page Threat Model document created five years ago.
B. Comprehensive, centrally managed Artifacts and Traceability matrices linking security requirements to specific code commits, test results, and deployment approvals.
C. The deployment logs from the auto-scaling groups in AWS.
D. A daily backup schedule for all developer workstations.

#### **4. A team is using a Waterfall methodology to build a flight control system for a new commercial aircraft. Given the extreme safety-critical nature of the software, the project manager emphasizes that security and safety requirements cannot be ambiguous or missed. In which phase of the Waterfall SDLC must formal Risk Assessment and Security Objective gathering be completed to minimize the cost of fixing fundamental design flaws?**
A. Architecture and Design
B. Implementation / Coding
C. Testing and Verification
D. Requirements Elicitation (Analysis)

#### **5. In DevSecOps, a cross-functional team emphasizes the "Shift-Left" philosophy. They configure the IDE (Integrated Development Environment) to immediately warn developers via a linting plugin whenever they type a known dangerous function (e.g., `strcpy()` in C++). What is the primary business justification for implementing this specific "Shift-Left" control?**
A. It entirely eliminates the need to run SAST tools during the CI build process.
B. It drastically reduces the cost and time required to fix vulnerabilities by catching them at the exact moment the developer makes the error, rather than finding them weeks later in QA.
C. It ensures the application passes all penetration tests automatically.
D. It prevents insider threats from intentionally planting logic bombs in the source code.

#### **6. A software vendor has discovered a zero-day vulnerability in their flagship product, which is already installed on thousands of customer servers globally. They have rapidly developed a patch and are about to release it. According to the standard Vulnerability Management lifecycle, what crucial communication step must accompany the release of this patch?**
A. An internal memo to the sales team to downplay the severity of the flaw.
B. Publishing a Security Advisory (or Security Bulletin) detailing the nature of the vulnerability, its CVE identifier (if requested/assigned), and clear instructions for customers on how to apply the patch.
C. Sending a cease-and-desist letter to the security researcher who originally reported the flaw.
D. Only notifying the largest enterprise customers who pay for premium support.

#### **7. Your company uses a widely popular open-source Java library. The National Vulnerability Database (NVD) just published a Critical CVE (CVSS 9.8) for this library. The open-source maintainers have released a patched version (v2.1). However, the lead developer tells you that upgrading to v2.1 will completely break several core functions of your application, requiring at least three weeks to refactor the code. Production is currently vulnerable. What is the BEST immediate course of action for the security team?**
A. Take the application offline entirely until the code refactoring is finished in three weeks.
B. Allow the application to run as-is and hope attackers don't discover the vulnerability while the team refactors.
C. Implement a compensating control, such as a highly specific Web Application Firewall (WAF) rule to block the exploit payload, while the development team works on the 3-week refactoring effort.
D. Force the developers to upgrade to v2.1 immediately and deploy the broken application to production, as security is more important than functionality.

#### **8. Which of the following roles in a mature Secure Software Development Lifecycle (SSDLC) represents a developer who has received advanced security training and acts as the primary point of contact for security guidance within their specific Agile scrum team?**
A. Chief Information Security Officer (CISO)
B. Penetration Tester
C. Security Champion
D. Incident Commander

#### **9. A software development project is nearing completion. Before deploying to production, the organization hires an external, independent security firm to conduct a comprehensive assessment. The firm is given full access to the source code, architecture diagrams, and administrative credentials to the staging environment. They simulate a highly motivated attacker trying to compromise the system. What specific type of testing is this?**
A. Black-Box Penetration Testing
B. White-Box (Crystal-Box) Penetration Testing
C. Automated Dynamic Application Security Testing (DAST)
D. Chaos Engineering

#### **10. According to ITIL and standard IT Service Management (ITSM) frameworks, when a critical security patch needs to be deployed to the production servers to fix an actively exploited vulnerability, which formal process governs the approval, scheduling, and back-out planning for this deployment?**
A. Incident Management
B. Problem Management
C. Change Management
D. Asset Management

#### **11. An enterprise organization is maturing its SSDLC by implementing a "Security Gates" (or Quality Gates) policy. They configure their Jenkins CI/CD pipeline to automatically abort the build and block the deployment to the testing environment if the Static Code Analysis (SAST) tool reports any "High" or "Critical" severity findings. What is the primary purpose of this automated Security Gate?**
A. To guarantee the software is 100% secure against all known and unknown attacks.
B. To enforce a minimum baseline of security quality and prevent known, highly dangerous vulnerabilities from progressing further down the deployment pipeline.
C. To punish developers for writing insecure code.
D. To replace manual code reviews and penetration testing.

#### **12. A software development company frequently uses subcontractors in different countries to write code modules. To protect the company's Intellectual Property (IP) and ensure the subcontractors do not introduce malicious backdoors, the legal and security teams establish strict contractual obligations. These contracts require the subcontractors to adhere to specific secure coding standards and grant the company the right to run SAST tools on the delivered code. What phase of the supply chain/vendor management lifecycle does this describe?**
A. Software Decommissioning (End-of-Life)
B. Incident Response
C. Third-Party Risk Management and Procurement Contracting
D. Post-Release Patch Management

#### **13. During a project post-mortem (Lessons Learned) meeting for a web application that suffered a data breach, it is revealed that the security team identified the SQL Injection vulnerability during the early design phase, but the project manager ignored the finding because fixing it would have delayed the launch date by two days. Which governance mechanism failed in this scenario?**
A. The CI/CD pipeline lacked automated DAST scanning.
B. The organization lacked a formally defined and enforced Risk Acceptance and Exception Management policy, allowing a project manager to overriding critical security findings without proper executive sign-off.
C. The developers were not trained in secure coding for SQL.
D. The firewall was misconfigured.

#### **14. When an organization officially designates a software product as "End of Life" (EOL) or "End of Support", what specific security responsibility ceases, which dramatically increases the risk for any customer who continues to use the product?**
A. The vendor stops providing new feature updates and UI enhancements.
B. The vendor ceases all monitoring of new CVEs and stops issuing security patches or hotfixes for newly discovered vulnerabilities.
C. The vendor legally re-possesses the software licenses from the customers.
D. The software will automatically uninstall itself from customer servers.
