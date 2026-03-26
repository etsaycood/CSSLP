# Exam 2
## Domain 2: Secure Software Lifecycle Management (14 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A highly dynamic startup uses a two-week Agile Scrum framework. The Chief Information Security Officer (CISO) complains that the security team is constantly bypassed because traditional threat models take four weeks to complete. What is the BEST practical method to integrate security seamlessly into this fast-paced Agile environment?**
A. Force the development team to switch to the traditional Waterfall methodology for all security-critical projects.
B. Mandate a mandatory four-week security halt at the end of every six months to catch up on testing.
C. Break down security requirements into bite-sized "Security User Stories" and "Abuser Stories," integrating them directly into the standard Product Backlog to be weighted and tackled during normal sprints.
D. Ignore security during the development sprints and rely entirely on a robust Web Application Firewall (WAF) in production.

#### **2. An established healthcare enterprise realizes their software security approach is entirely reactive—they merely fix bugs after penetration testers find them just before release. Leadership wants to strategically measure their current software security maturity against industry peers and systematically build a long-term roadmap. Which framework is explicitly designed to help organizations assess and evolve their Secure Software Development Lifecycle (SSDLC) maturity?**
A. Open Web Application Security Project (OWASP) Top 10
B. Building Security In Maturity Model (BSIMM) or Software Assurance Maturity Model (OpenSAMM)
C. Advanced Encryption Standard (AES)
D. Common Vulnerability Scoring System (CVSS)

#### **3. A mid-sized software company has 200 developers but only 2 dedicated application security engineers. The security engineers are completely overwhelmed and become a massive bottleneck, delaying every release. The company does not have the budget to hire more security staff. What is the industry's MOST effective organizational strategy to scale security knowledge across the development teams?**
A. Implement a "Security Champions" program by identifying and training enthusiastic developers within the scrum teams to act as the first line of security defense and advocates.
B. Outsource all code reviews to a cheap, overseas third-party vendor.
C. Purchase the most expensive, fully automated DAST tool to replace human code reviews entirely.
D. Accept the risk and completely bypass security reviews for low-priority projects.

#### **4. A disgruntled senior software developer is abruptly terminated on a Friday afternoon. The developer had extensive access to the company's central Git source code repositories and often worked remotely using SSH keys stored on their personal unmanaged laptop. What IMMEDIATE Configuration and Version Control Management action MUST be taken to protect the integrity of the codebase?**
A. Delete all the source code repositories and restore them from yesterday's backup.
B. Instantly revoke the terminated employee's SSH public keys from the Git server and terminate their Active Directory / SSO access.
C. Ask the developer politely to delete the SSH keys from their laptop.
D. Change the master branch name from `main` to `production` to confuse the developer.

#### **5. In a fully automated DevSecOps CI/CD pipeline, the Static Application Security Testing (SAST) tool scans a developer's newly submitted Pull Request (PR) and discovers a critical SQL Injection vulnerability. According to the principle of setting strict "Quality/Security Gates," what is the BEST automated response the CI/CD pipeline should execute?**
A. Automatically email the CISO and allow the code to pass into production, ensuring it gets prioritized for the next sprint.
B. Automatically comment on the PR with the finding, but allow the developer to manually override the warning and merge it.
C. Break the build (Fail the Gate) and mathematically block the PR from being merged into the main branch until the developer fixes the critical SQL Injection.
D. Automatically attempt to rewrite the developer's SQL queries using artificial intelligence.

#### **6. A heavily regulated financial institution is preparing for an external audit. The auditor demands absolute proof that the production database cluster has not suffered any unapproved, silent configuration changes (like an administrator quietly opening port 3306 to the internet) over the last six months. What standard lifecycle management mechanism MUST the organization have in place to confidently provide this proof?**
A. Secure Software Requirements Traceability Matrix
B. Security Awareness Training Logs
C. Configuration Management Baseline paired with Continuous Integrity Monitoring (e.g., File Integrity Monitoring / Drift Detection).
D. An open-source Static Code Analyzer

#### **7. The "Shift Left" philosophy is the battle cry of modern DevSecOps. Beyond simply integrating tools earlier, what is the primary economic and business justification for relentlessly pushing security testing (like Threat Modeling and SAST) as far "left" (early) into the Requirements and Design phases of the SDLC as possible?**
A. It eliminates the need to ever perform dynamic testing (DAST) or hire penetration testers.
B. Security engineers are inherently better at writing code than developers.
C. The financial cost and engineering effort required to fix a fundamental security defect is exponentially cheaper during the Whiteboard/Design phase than waiting to fix it after it is deployed to Production.
D. It guarantees the software will be 100% bug-free.

#### **8. Your development team is officially adopting Threat Modeling (using frameworks like STRIDE). To maximize the value of Threat Modeling and avoid costly, massive architectural teardowns later, during which specific phase of the Secure Software Development Lifecycle (SSDLC) is it MOST appropriate and historically most effective to perform an intensive Threat Model?**
A. During the final Deployment phase.
B. During the Architecture and Design phase.
C. Immediately after a devastating data breach.
D. During the Operations and Maintenance phase.

#### **9. Over the past three months, junior developers have accidentally committed hardcoded Amazon Web Services (AWS) API keys and database passwords into the company's public GitHub repository on four separate occasions. Currently, the security team manually scans the repository once a week and yells at the developers when they find a leak. What preventative lifecycle control should be natively integrated into the developers' workflow to definitively stop this from happening?**
A. Implement pre-commit hooks or automated CI/CD Secret Scanning to detect and reject commits containing high-entropy strings or known token formats before they are ever pushed to the central repository.
B. Obfuscate the hardcoded passwords using Base64 encoding so hackers won't recognize them.
C. Fire any developer who commits a password.
D. Make the public GitHub repository private.

#### **10. An e-commerce application successfully repels a massive, coordinated zero-day exploit attempt. The incident response (IR) team worked 48 hours straight to patch the system, block the malicious IPs, and restore normal services. Now that the adrenaline has faded and the servers are humming quietly, what is the critical, mandatory FINAL stage of the Incident Response Lifecycle that must not be skipped?**
A. Immediately prosecuting the attackers in international court.
B. Conducting a "Lessons Learned" / Post-Mortem review to analyze what failed, what worked, and how to institutionally update defenses and incident playbooks to prevent recurrence.
C. Sending a press release bragging about the successful defense.
D. Wiping the firewall logs to save disk space for the next attack.

#### **11. A newly hired developer on the payment gateway team implements a form field that takes user input and reflects it directly back to the screen without any sanitization. This introduces a glaring Cross-Site Scripting (XSS) vulnerability. During the post-mortem, management realizes the developer simply didn't know what XSS was. To address the root cause systemically across the entire organization, what fundamental SDLC pillar must be drastically improved?**
A. Mandatory role-based Secure Coding Education and continuous Security Awareness Training for all software engineering hires.
B. Purchasing a stronger perimeter firewall.
C. Increasing the complexity rules for the developers' laptop passwords.
D. Switching the frontend framework from React to Angular.

#### **12. The Enterprise Architecture Review Board is conducting a formal "Security Gate" checkpoint at the conclusion of the Design Phase for a new remote patient monitoring app. The board reviews the data flow diagrams and discovers the architecture plans to transmit patient heartbeat and oxygen levels over unencrypted HTTP. What is the ONLY acceptable decision the review board can make at this SDLC Security Gate?**
A. Approve the design (Go) but add a note begging the developers to fix it eventually.
B. Reject the design (No-Go), formally halt the project's transition into the Coding phase, and force the team back to the drawing board to implement HTTPS / TLS.
C. Approve the design (Go) because speed-to-market is the ultimate priority for startups.
D. Terminate the entire project entirely and fire the architects.

#### **13. Modern software is rarely written from scratch; it is assembled. Your developers are about to compile a Java application that imports 45 different open-source `.jar` libraries from the internet. To formally manage the risk of importing a library that contains a known, severe vulnerability (like Log4j), what specific class of automated scanning tool SHOULD be integrated into the build lifecycle?**
A. Interactive Application Security Testing (IAST)
B. Software Composition Analysis (SCA)
C. Database Activity Monitoring (DAM)
D. Endpoint Detection and Response (EDR)

#### **14. A massive enterprise CRM application has reached its End-of-Life (EOL) after 15 years of service. All current customer data has been migrated to a new SaaS platform. As the final act in the Software Lifecycle Management process, what MUST the operations team do with the giant, dust-covered physical database servers sitting in the basement to ensure absolute data security?**
A. Unplug them and leave them in the basement indefinitely.
B. Format the hard drives using standard OS tools and donate the servers to a local school.
C. Execute cryptographic secure wiping of the drives and physically shred/destroy the storage media according to secure data disposal policies to guarantee Data Remanence is eliminated.
D. Put the servers on an internal auction site for employees to buy and take home for cheap.
