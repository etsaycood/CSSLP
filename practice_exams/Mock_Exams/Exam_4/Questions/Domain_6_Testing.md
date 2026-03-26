# Exam 4
## Domain 6: Secure Software Testing (17 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A security analyst is configuring a dynamic analysis tool to test a REST API. The tool is set to automatically send thousands of malformed JSON payloads, extremely long strings, and unexpected data types to various API endpoints while monitoring the application for unhandled exceptions or crashes. What specific type of testing technique is this?**
A. Fuzzing (Fuzz Testing)
B. Static Application Security Testing (SAST)
C. Code Coverage Analysis
D. Penetration Testing

#### **2. Which of the following vulnerabilities is Static Application Security Testing (SAST) generally LEAST effective at detecting due to its inability to understand the runtime execution environment and business logic context?**
A. Hardcoded symmetric encryption keys.
B. Use of deprecated and insecure cryptographic algorithms (e.g., MD5).
C. Insecure Direct Object Reference (IDOR) / Business Logic Flaws.
D. Buffer overflows from the use of unsafe C libraries (e.g., `strcpy`).

#### **3. During the testing phase, a QA engineer needs to verify that the application correctly handles sensitive Personally Identifiable Information (PII) without violating privacy regulations. To create a realistic test dataset that mimics production data properties without exposing actual user PII to the QA environment, which technique should the engineer employ?**
A. Live Production Data Cloning
B. Data Masking (or Data Obfuscation / Synthetic Data Generation)
C. Symmetric Encryption using the production key
D. SQL Injection

#### **4. A penetration testing team is hired to evaluate a new web application. The client provides the team with full access to the application's source code, architecture diagrams, API documentation, and database schemas before the test begins. Which testing methodology is this client employing?**
A. Black-Box Testing
B. White-Box (Clear-Box) Testing
C. Gray-Box Testing
D. Fuzz Testing

#### **5. What is the primary focus and objective of a "Regression Test" in the context of the Secure Software Development Lifecycle (SSDLC)?**
A. To measure how quickly the system can process one million concurrent requests.
B. To discover brand-new zero-day vulnerabilities in third-party libraries.
C. To verify that recent code changes (e.g., bug fixes or new features) have not inadvertently broken or re-introduced vulnerabilities into previously tested, working functionality.
D. To analyze the source code for hardcoded passwords.

#### **6. A security testing team integrates a Dynamic Application Security Testing (DAST) tool into the deployment pipeline. The tool interacts with the running web application exactly as a normal user would, clicking links and submitting HTML forms to find vulnerabilities like Reflected XSS. What is the most significant limitation of DAST tools compared to SAST tools?**
A. DAST tools cannot detect vulnerabilities in deployed, running code.
B. DAST tools are prone to a high rate of False Negatives because they cannot "see" the backend source code to identify exact line numbers, and they struggle to navigate complex authentication workflows or single-page applications (SPAs) effectively.
C. DAST tools scan too fast and consume too much CPU on the developer's laptop.
D. DAST tools only support older languages like C++ and COBOL.

#### **7. Interactive Application Security Testing (IAST) has emerged as a hybrid testing approach. How does IAST primarily differ from traditional SAST and DAST in its operational deployment?**
A. IAST requires physical hardware appliances to be installed in the data center.
B. IAST operates entirely offline without running the application.
C. IAST involves deploying an agent (or instrumentation) directly *inside* the application's runtime environment (e.g., JVM or CLR) to monitor execution, data flow, and memory usage in real-time as the application is exercised (by automated tests or manual exploration).
D. IAST relies solely on manual code review by senior developers.

#### **8. A developer wants to ensure that a newly written function specifically rejects input strings that exceed 50 characters, throwing a specific `ValidationException`. The developer writes an automated script that passes a 51-character string to the function and asserts that the `ValidationException` is indeed thrown. What type of test is this?**
A. A Unit Test (Negative Testing)
B. A Penetration Test
C. A User Acceptance Test (UAT)
D. A Load Test

#### **9. During a security assessment, the testing team decides to perform "Penetration Testing" rather than just a "Vulnerability Scan." What is the fundamental, defining difference that elevates an assessment to a true Penetration Test?**
A. Penetration testing only uses automated tools, while vulnerability scanning is purely manual.
B. Vulnerability scanning is only performed on source code (SAST).
C. Penetration testing actively involves the *exploitation* (or attempted exploitation) of identified vulnerabilities to prove the risk, determine the depth of access achievable, and demonstrate the actual business impact, whereas a scan merely reports potential flaws.
D. Penetration testing only looks at the network perimeter firewalls.

#### **10. An organization is planning a "Bug Bounty" program. What is the primary strategic benefit of implementing a public bug bounty program as part of the overall security testing strategy?**
A. It completely replaces the need for internal QA testing teams.
B. It guarantees that the software will be 100% bug-free.
C. It leverages the crowdsourced expertise of independent security researchers to continuously discover complex edge-case vulnerabilities that internal automated tools and time-boxed penetration tests likely missed.
D. It automatically fixes the bugs found in the source code.

#### **11. A developer is configuring a Continuous Integration (CI) pipeline. They want to ensure that if a developer commits code that introduces a known critical vulnerability (e.g., SQL Injection), the build process will immediately stop and notify the team. Which specific metric or mechanism is used to enforce this automatic stoppage?**
A. Setting a "Quality Gate" (or Security Gate) failure threshold based on SAST/DAST scan results.
B. Enforcing Code Coverage metrics to reach 100%.
C. Utilizing a Web Application Firewall (WAF) blocking rule.
D. Running a stress test for 24 hours.

#### **12. When evaluating the effectiveness of a security testing tool, the security team notes that the tool frequently flags legitimate, safe code as a "Critical SQL Injection vulnerability," forcing developers to waste hours investigating non-issues. In security testing terminology, what is this undesirable outcome called?**
A. A True Positive
B. A False Negative
C. A False Positive
D. A True Negative

#### **13. A test engineer is designing cases to verify the boundary conditions of an age input field, which should only accept values between 18 and 65 inclusive. Using Boundary Value Analysis (BVA), which set of test data points is the MOST critical to include in the test suite?**
A. 25, 30, 40, 50, 60
B. 17, 18, 19, 64, 65, 66
C. -1, 0, 100, 1000
D. 'eighteen', 'sixty-five', null

#### **14. During which phase of penetration testing does the ethical hacker attempt to maintain access to a compromised system, often by installing backdoors or creating hidden user accounts, to demonstrate what an Advanced Persistent Threat (APT) might do?**
A. Reconnaissance / Footprinting
B. Vulnerability Scanning
C. Maintaining Access (Persistence)
D. Reporting / Remediation

#### **15. A development team employs a robust Unit Testing framework (e.g., JUnit or NUnit). To measure how much of the application's actual source code (lines, branches, or paths) is executed by their automated unit tests, what metric do they track?**
A. Vulnerability Density
B. Code Coverage
C. Mean Time to Repair (MTTR)
D. Common Vulnerability Scoring System (CVSS)

#### **16. Before a major new release of an ERP system is deployed to production, it is deployed to a staging environment. The business stakeholders and end-users are asked to perform their daily tasks on this staging system to confirm that the software meets their operational needs and the original functional requirements. What type of testing phase is this?**
A. Unit Testing
B. Integration Testing
C. User Acceptance Testing (UAT)
D. Static Analysis

#### **17. A team is developing a cryptographic library. To ensure their implementation of the AES-256 algorithm securely and correctly transforms plaintext into ciphertext according to the mathematical standard, they use a large set of standardized inputs with mathematically known, pre-calculated expected outputs to verify the results. What is this rigorous verification process called?**
A. Fuzzing
B. Known-Answer Tests (KATs) / Cryptographic Validation
C. Stress Testing
D. Penetration Testing
