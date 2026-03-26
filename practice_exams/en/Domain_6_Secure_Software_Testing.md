# Domain 6: Secure Software Testing (18 Questions)

#### **1. A security testing team is assigned to evaluate a web application. They are given no source code, no architectural diagrams, and a single set of non-privileged user credentials. They must map the attack surface and attempt to exploit vulnerabilities entirely from the outside. What testing technique are they utilizing?**
A. Known environment testing (White-box)
B. Unknown environment testing (Black-box)
C. Static application security testing (SAST)
D. Code coverage analysis

*   **Answer: B**
*   **Rationale:** **Unknown environment testing** (Black-box / Dynamic testing) simulates an external attacker who has no internal knowledge of the system's architecture or source code. **Known environment testing** (White-box) provides the testers with full access to source code, diagrams, and administrative access.

#### **2. An automated security testing tool is integrated into the CI/CD pipeline. Once the application is deployed to a staging server, this tool proactively sends thousands of manipulated HTTP requests (like SQLi and XSS payloads) to the live, running web application and analyzes the server's HTTP responses to detect vulnerabilities. This tool is categorizing as:**
A. Static Application Security Testing (SAST)
B. Dynamic Application Security Testing (DAST)
C. Software Composition Analysis (SCA)
D. Unit Testing

*   **Answer: B**
*   **Rationale:** **DAST (Dynamic Application Security Testing)** is a black-box testing technology that finds vulnerabilities in applications *while they are running* in an environment. It crawls the app and sends malicious payloads to test how the running application reacts.

#### **3. During the test planning phase, the Quality Assurance (QA) team needs a massive database of realistic user profiles to perform stress testing. Because privacy laws strictly prohibit the use of real customer data in lower environments, the QA team utilizes an algorithm to create a highly realistic, but entirely fake, dataset that maintains statistical quality and referential integrity. What is this concept called?**
A. Data Anonymization
B. Data Obfuscation
C. Synthetic Data Generation
D. Tokenization

*   **Answer: C**
*   **Rationale:** **Generating test data (Synthetic Data)** involves building complex, relational datasets from scratch that mimic the structure and volume of production data without containing a single byte of actual, real-world personal data, completely bypassing privacy compliance risks.

#### **4. A company routinely copies its production database down to the staging environment for testing. The DBA writes a script that systematically replaces real names, addresses, and Social Security Numbers with asterisks or randomized characters in the staging database before testing begins. What practice is the DBA performing?**
A. Data Obfuscation / Sanitization
B. Synthetic Data Generation
C. Fault Injection
D. Database Normalization

*   **Answer: A**
*   **Rationale:** While synthetic data is generated from scratch, **Obfuscation / Sanitization / Masking** takes existing production data and alters or removes the sensitive identifiers before it can be legally or safely reused in non-production environments.

#### **5. In order to test the extreme boundaries of a heavily used video rendering application, security engineers deliberately introduce wildly invalid, completely random, and chaotically malformed data to the application's input processing engine, hoping to force a crash or memory leak. What testing methodology is this?**
A. Interactive Application Security Testing (IAST)
B. Fuzzing (Fuzz Testing)
C. Penetration Testing
D. Integration Testing

*   **Answer: B**
*   **Rationale:** **Fuzzing** is an automated software testing technique that involves providing invalid, unexpected, or completely random data as inputs to a computer program. The primary goal is to monitor the program for exceptions, memory leaks, or crashes that could indicate a buffer overflow vulnerability.

#### **6. An engineer needs to test how an embedded IoT medical device reacts if its network connectivity abruptly drops to zero or if its battery voltage suddenly spikes. To simulate these hardware and environmental failures in a controlled lab, the engineer should use:**
A. Stress testing
B. Fuzzing
C. Fault injection
D. Penetration testing

*   **Answer: C**
*   **Rationale:** **Fault injection** is the deliberate introduction of errors and failures (like dropping network packets, starving memory, or altering voltage) into a system to test its error-handling and verify if it defaults to a *fail secure* state.

#### **7. A developer writes a series of automated scripts that test individual, isolated methods within the authentication class (e.g., verifying that the `hashPassword()` function returns the expected string length). These highly granular tests are executed by the IDE immediately upon saving the code. What kind of testing is this?**
A. System integration testing
B. Unit testing
C. Dynamic Application Security Testing (DAST)
D. Penetration testing

*   **Answer: B**
*   **Rationale:** **Unit testing** is a white-box testing technique where individual, microscopic components of software (modules, functions, or classes) are tested in isolation from the rest of the application to ensure they perform their discrete tasks correctly.

#### **8. The QA team finishes testing Version 2.0 of a payroll application and verifies that all the new features work perfectly. However, before releasing it, they re-run the entire suite of Version 1.0 automated test scripts against the Version 2.0 build. The primary purpose of this activity is to perform:**
A. Threat Modeling
B. Fuzzing
C. Integration testing
D. Regression testing

*   **Answer: D**
*   **Rationale:** **Regression testing** is the process of re-testing a system after a modification (like a patch or a new feature) to establish that the change did not inadvertently "break" or re-introduce vulnerabilities into previously working code.

#### **9. Following a comprehensive penetration test, the red team delivers a report containing 45 identified vulnerabilities. The software engineering manager reviews the report and formally notes that 5 of these vulnerabilities cannot be exploited unless the attacker already possesses highly restricted internal super-admin credentials. Evaluating the significance and organizational risk of the test results is known as:**
A. Generating security test cases
B. Analyzing security implications of test results
C. Verifying and validating documentation
D. Interactive Application Security Testing (IAST)

*   **Answer: B**
*   **Rationale:** Not all vulnerabilities warrant an immediate panic. **Analyzing security implications of test results** involves triaging the raw output of security tools and pentests, assigning accurate risk scores (like CVSS), understanding the business impact, and prioritizing remediation efforts based on actual threat scenarios.

#### **10. A security researcher participating in a company’s Bug Bounty program submits a report proving they can bypass the multi-factor authentication mechanism. The organization accepts the report, pays the bounty, and opens a critical ticket in Jira for the developers to fix the issue. This scenario is a practical application of:**
A. Vulnerability risk scoring using CVSS
B. Identifying undocumented functionality
C. Security researcher outreach and bug tracking
D. Cryptographic entropy validation

*   **Answer: C**
*   **Rationale:** Operating a **Bug Bounty program** is engaging in **Security researcher outreach**, incentivizing external white-hat hackers to find flaws DAST/SAST missed. The resulting flaws must be systematically logged and managed through formal **Bug tracking** systems (like Jira).

#### **11. A security analyst is attempting to prioritize a massive backlog of bugs. They use a standard industry framework to assign each bug a numerical score from 0.0 to 10.0 based on criteria such as Attack Vector, Attack Complexity, Privileges Required, and Impact on Confidentiality, Integrity, and Availability. What framework is the analyst using?**
A. SLSA (Supply-chain Levels for Software Artifacts)
B. OWASP Top 10
C. CVSS (Common Vulnerability Scoring System)
D. STRIDE

*   **Answer: C**
*   **Rationale:** The **CVSS (Common Vulnerability Scoring System)** is the industry-standard methodology used to classify, prioritize, and track the severity of software vulnerabilities, outputting a base score between 0.0 (Informational) and 10.0 (Critical).

#### **12. The build manager configures the CI/CD pipeline so that if any Static Application Security Testing (SAST) or Dynamic Application Security Testing (DAST) scan returns a vulnerability with a CVSS score of 7.0 or higher, the build immediately fails and cannot proceed to the staging environment. This automated pipeline rule is an example of:**
A. Penetration testing
B. Implementing Break/Build criteria
C. Verifying documentation
D. Generating Misuse test cases

*   **Answer: B**
*   **Rationale:** Establishing **Break/Build criteria** involves setting strict, non-negotiable thresholds for security testing results. If the scan violates these thresholds (e.g., discovering high-severity flaws), the pipeline acts as a control gate and halts the release ("breaks the build").

#### **13. During a thorough security assessment of a commercial application, the reverse-engineers discover an administrative debugging interface listening on an obscure high port that was not referenced anywhere in the architecture diagrams, API specifications, or user manuals. Discovering this interface satisfies which testing goal?**
A. Validating Cryptographic pseudorandom generators
B. Fuzzing boundary values
C. Identifying undocumented functionality (Backdoors/Debug modes)
D. Regression testing the presentation layer

*   **Answer: C**
*   **Rationale:** A critical goal of security testing (especially penetration testing and code review) is **Identifying undocumented functionality**. These hidden features are often debugging portals, development shortcuts, or malicious backdoors left behind that bypass all standard authentication flows.

#### **14. A tester is assigned to verify that the application properly enforces password complexity rules. The tester writes a script that attempts to create a new user account using the password "123". The expected result is that the system rejects the creation and displays an error message. What type of test case is this?**
A. Misuse/Abuse test case
B. Functional security testing (Logic)
C. Non-functional security testing (Scalability)
D. Synthetic simulation

*   **Answer: B**
*   **Rationale:** Verifying that a specific security control (like a password complexity check, an RBAC authorization check, or an input validation filter) performs exactly as it was designed to do is **Functional security testing**. You are testing the "logic" of the security feature.

#### **15. When a new symmetric encryption feature is implemented, the security architect demands proof that the seed data feeding the initialization vectors (IVs) is truly unpredictable and mathematically random. The testing team must perform:**
A. Fuzzing
B. Fuzzing the API endpoints
C. Cryptographic validation (Entropy testing)
D. Penetration testing the firewalls

*   **Answer: C**
*   **Rationale:** Cryptography fails catastrophically if the underlying random numbers are predictable. **Cryptographic validation** involves rigorously testing pseudorandom number generators (PRNGs) to ensure they possess absolute mathematical **entropy** and unpredictability.

#### **16. Before an application is moved to the final User Acceptance Testing (UAT) phase, a specialized testing tool is attached directly to the application's runtime environment (like a Java agent). This tool analyzes code execution in real-time as QA testers interact with the application normally, pinpointing exact code vulnerabilities without requiring dedicated security scans. This tool is:**
A. Static Application Security Testing (SAST)
B. Dynamic Application Security Testing (DAST)
C. Interactive Application Security Testing (IAST)
D. Hardware-Assisted Threat Modeling

*   **Answer: C**
*   **Rationale:** **IAST (Interactive Application Security Testing)** is a "grey-box" technology. It installs an agent inside the application runtime. As the application is operated (or hit by DAST tools), the IAST agent watches the internal data flow, identifying vulnerabilities with exact line numbers and near-zero false positives.

#### **17. The deployment team is preparing the production release. According to the CSSLP curriculum, reviewing the installation manuals, user guides, setup instructions, and release notes to ensure they do not inadvertently leak sensitive infrastructure details or default administrative passwords is a critical part of:**
A. Source Code Analysis
B. Verifying and validating documentation
C. Generating misuse cases
D. Threat modeling

*   **Answer: B**
*   **Rationale:** Security testing extends beyond the code. Attackers frequently read publicly available manuals to discover default passwords or hidden URLs. **Verifying and validating documentation** ensures that user-facing materials are secure and do not facilitate social engineering or reconnaissance.

#### **18. To prove that an application can sustain a massive influx of Black Friday shopping traffic without failing to a state that compromises transaction integrity, the QA team utilizes cloud resources to simulate 100,000 concurrent user sessions. This testing falls under the category of:**
A. Functional logic testing
B. Unit testing
C. Nonfunctional security testing (Performance/Scalability/Reliability)
D. Known-environment penetration testing

*   **Answer: C**
*   **Rationale:** Validating how the application behaves under extreme load, high latency, or hardware stress without corrupting data or exposing secrets is **Nonfunctional security testing**, specifically focused on **performance, reliability, and scalability** (Availability).
