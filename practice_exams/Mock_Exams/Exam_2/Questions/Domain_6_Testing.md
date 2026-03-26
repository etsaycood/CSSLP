# Exam 2
## Domain 6: Secure Software Testing (17 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A QA engineer is preparing to conduct Dynamic Application Security Testing (DAST) on a newly developed web application. Before launching the automated DAST scanner against the target environment, what is the absolute FIRST and most critical administrative action the engineer MUST perform?**
A. Obtain explicit, formally documented authorization and scope definition from the system owners.
B. Download the target application's latest source code repository.
C. Disable the production Web Application Firewall (WAF) to ensure the scanner's payloads are not blocked.
D. Notify the local law enforcement agency about the impending scan.

#### **2. A development team is integrating security testing into their CI/CD pipeline. They want to systematically identify known vulnerabilities (such as out-of-date HTTP servers or unpatched OS libraries) within the Docker containers they build, without actually executing the containerized application. Which specific type of testing tool should they implement in the build phase?**
A. Static Application Security Testing (SAST)
B. Interactive Application Security Testing (IAST)
C. Software Composition Analysis (SCA) / Vulnerability Scanning
D. Penetration Testing

#### **3. During a Black-Box penetration test, the tester is provided with absolutely no internal documentation, source code, or architecture diagrams of the target web application. The tester discovers a hidden administrative endpoint by running a tool that rapidly sends thousands of common directory names (e.g., `/admin`, `/backup`, `/test`) to the web server and observing the HTTP response codes. What testing technique is the tester employing?**
A. Code Review
B. Fuzzing
C. Directory Brute-Forcing (Directory Enumeration)
D. Fault Injection

#### **4. A massive, complex legacy C++ financial application occasionally crashes in production, but the root cause is exceptionally difficult to reproduce manually. The security testing team decides to implement a specialized testing methodology where an automated tool endlessly feeds massive amounts of highly mutated, completely malformed, and randomized data into the application's input fields (like file parsers and network sockets) while simultaneously monitoring the application for memory segmentation faults or crashes. What is this specific testing technique called?**
A. Fuzzing (Fuzz Testing)
B. Regression Testing
C. Unit Testing
D. Penetration Testing

#### **5. A development team is adopting a "Shift Left" security culture. They want a tool that can analyze the application's Java source code as the developers are actively writing it in their IDEs, instantly flagging insecure coding patterns (like hardcoded passwords or dangerous `eval()` functions) before the code is even compiled or committed to the repository. Which tool category fits this exact requirement?**
A. DAST (Dynamic Application Security Testing)
B. SAST (Static Application Security Testing)
C. WAF (Web Application Firewall)
D. IAST (Interactive Application Security Testing)

#### **6. A security auditor is reviewing a massive 1-million-line codebase. Knowing that manually inspecting every line for vulnerabilities is impossible, the auditor uses a SAST tool. The SAST tool generates a report containing 4,500 "Critical" vulnerabilities. After spending three days manually reviewing the first 500 alerts, the auditor realizes that 495 of them are perfectly safe, custom-built internal functions that the SAST tool incorrectly flagged as dangerous. In security testing terminology, what are these 495 alerts called?**
A. False Negatives
B. True Positives
C. False Positives
D. True Negatives

#### **7. A company relies heavily on a third-party, commercial-off-the-shelf (COTS) proprietary software application where they do not have access to the underlying source code. The security team needs to test the application while it is actively running in a staging environment to dynamically simulate how a real external hacker would interact with the web interface. Which testing methodology is the ONLY viable option here?**
A. DAST (Dynamic Application Security Testing)
B. SAST (Static Application Security Testing)
C. White-Box Testing
D. Manual Code Review

#### **8. The QA team is performing functional regression testing on a web application. However, the security engineering team wants to simultaneously observe the data flowing deep inside the application's memory and execution stack during these tests to identify runtime vulnerabilities without requiring the QA team to run separate, dedicated security scans. The team deploys specialized sensor agents directly inside the application server's runtime environment (JVM/.NET CLR) to monitor the live code execution. What is this advanced testing technology called?**
A. SAST
B. DAST
C. IAST (Interactive Application Security Testing)
D. Vulnerability Scanning

#### **9. A highly secure government application uses a complex cryptographic module. To prove that the module cannot be bypassed even under extreme duress, the testing team artificially induces hardware failures by cutting power to specific CPU pins and manipulating the system clock speed during cryptographic operations to see if the system correctly "Fails Secure." What type of specialized testing is this?**
A. Fuzzing
B. Fault Injection (Stress Testing)
C. Penetration Testing
D. Regression Testing

#### **10. An organization decides to hire an external cybersecurity firm to conduct a comprehensive Penetration Test. The organization provides the hired hackers with full administrative credentials, complete access to the Git source code repositories, detailed network architecture diagrams, and the API swagger documentation before the test even begins. What specific type of penetration testing engagement is this?**
A. Black-Box Testing
B. Grey-Box Testing
C. White-Box (Crystal-Box) Testing
D. Blind Testing

#### **11. After a severe security breach where hackers exploited a missing validation check in the password reset logic, the development team patches the vulnerability. However, the exact same vulnerability accidentally reappears in the production system three months later because a different developer overwrote the patch with an older branch. What specific type of automated security testing MUST be heavily implemented in the CI/CD pipeline to prevent previously fixed bugs from ever returning?**
A. Fuzzing
B. Regression Security Testing
C. Red Teaming
D. Threat Modeling

#### **12. A company maintains a strict benchmark policy that code coverage for unit tests must exceed 85% before an application can be deployed. A developer writes unit tests that execute 90% of the lines of code in a specific class. However, during a production incident, the class fails catastrophically when a specific combination of input parameters causes an untested execution path (a complex nested `if/else` statement) to trigger an exception. What does this reveal about code coverage metrics in the context of security testing?**
A. 100% line coverage guarantees that an application is free of security vulnerabilities.
B. High line coverage percentage does not inherently guarantee high security or that all logical execution paths and edge cases have been adequately tested.
C. Code coverage metrics are completely irrelevant to software engineering.
D. The developer should have aimed for 75% coverage instead of 85%.

#### **13. During a vulnerability assessment, a security analyst uses an automated network scanner to discover that a specific server is running an older version of OpenSSL. The scanner flags this as a "High Request" vulnerability because this version of OpenSSL is known to be vulnerable to the 'Heartbleed' bug. The analyst manually drafts a report and hands it to the operations team to patch. The analyst did not attempt to actually steal data from the server using the Heartbleed exploit. This activity is precisely defined as:**
A. Penetration Testing
B. Vulnerability Scanning (Vulnerability Assessment)
C. Fuzzing
D. Red Teaming

#### **14. A security team is planning a massive "Red Team" exercise. Unlike a standard penetration test that focuses purely on finding software vulnerabilities within a specific application scope, what is the primary, overarching objective of a comprehensive Red Team engagement?**
A. To train the developers on how to write secure Java code using secure libraries.
B. To evaluate the organization's holistic security posture, including the physical security guards, employee susceptibility to social engineering, and the active detection and response capabilities of the internal "Blue Team" (SOC).
C. To achieve 100% SAST code coverage.
D. To patch and update all Windows servers in the data center.

#### **15. A software engineering team implements a "Bug Bounty" program, inviting independent security researchers from around the world to attack their production application and report vulnerabilities in exchange for monetary rewards. What is the most significant inherent risk or challenge of relying heavily on a public bug bounty program as a primary testing strategy?**
A. Researchers will find zero bugs because the application is already heavily tested.
B. Bug bounty programs provide consistent, predictable, and fully comprehensive test coverage of every single feature in the application.
C. It generates a massive volume of duplicate submissions, out-of-scope reports, and "beg bounty" spam, requiring significant internal triage resources to verify the legitimacy of the findings.
D. It replaces the need to run SAST and DAST in the CI/CD pipeline.

#### **16. A developer is writing Unit Tests for a newly created 'User Authentication' module. Which of the following test cases represents the BEST example of "Negative Testing" (Abuse Case Testing) for this module?**
A. Submitting a correct username and a correct password to verify the user is successfully logged in.
B. Submitting a username that does not exist in the database with a random password to verify the system explicitly rejects the login attempt and returns a generic error message.
C. Verifying that the login screen renders correctly on a mobile device browser.
D. Confirming that the login process completes within 500 milliseconds.

#### **17. Following a major architectural refactoring of a monolithic application into microservices, the QA team wants to verify that the newly independent 'Order Service' can successfully communicate, authenticate, and exchange data with the 'Payment Service' across the internal network. What specific level of testing must be performed to validate this interaction?**
A. Unit Testing
B. Integration Testing
C. SAST
D. User Acceptance Testing (UAT)
