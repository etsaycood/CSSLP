# Exam 3
## Domain 6: Secure Software Testing (17 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A security analyst is tasked with testing a proprietary legacy web server written in C. The analyst decides to map out how the server handles malformed data by continuously hammering the login API endpoint with extremely long, thousands-of-characters strings consisting of randomly generated characters (e.g., 'A', 'X', '*&%$'). The goal is to see if the random garbage data causes the server program to suddenly crash or throw memory corruption exceptions. Which specific security testing methodology is the analyst employing?**
A. Static Application Security Testing (SAST)
B. Fuzzing (Fuzz Testing)
C. Dependency/Software Composition Analysis (SCA)
D. Penetration Testing (Black Box Testing)

#### **2. A development team is integrating a new security testing tool into their CI/CD pipeline. The tool requires access to the application's uncompiled source code. It analyzes the raw syntax line-by-line, following variables and logic paths purely mathematically without actually executing the program. It successfully highlights that a developer forgot to sanitize input before writing it to a database. What type of security testing tool has the team deployed?**
A. DAST (Dynamic Application Security Testing)
B. SAST (Static Application Security Testing)
C. IAST (Interactive Application Security Testing)
D. RASP (Runtime Application Self-Protection)

#### **3. During the Verification phase of the SDLC, the QA team is conducting specific tests directly linked explicitly to the "Misuse/Abuse Cases" defined during the earlier Requirements phase. They intentionally try to bypass the password lockout mechanism by sending 100 parallel login requests simultaneously to see if the mechanism fails under a race condition. This systematic testing against specific architectural threat models is BEST described as:**
A. Unit Testing
B. Regression Testing
C. Security Functional Testing (or Security Requirements Testing)
D. User Acceptance Testing (UAT)

#### **4. A QA engineer has just received a hotfix branch from the development team patching a critical Remote Code Execution (RCE) zero-day vulnerability. Before the patch can be deployed to the production environment, the engineer reruns the entire automated security test suite, including thousands of older test cases that previously passed. The sole purpose is to definitively prove that patching the RCE vulnerability did not inadvertently break other existing, unrelated security controls elsewhere in the system. What specific type of testing is this?**
A. Fuzzing
B. Regression Testing
C. Penetration Testing
D. Smoke Testing

#### **5. A security team hires an external ethical hacking firm to test their new mobile application. The testing firm is given no prior knowledge of the internal architecture, zero access to the source code, and no test credentials. They must attack the application exactly as a real-world, uninformed external adversary would, relying entirely on scanning, reverse-engineering, and intercepting network traffic to find vulnerabilities. What is the fundamental testing paradigm being applied?**
A. White-Box Testing (Clear-Box Testing)
B. Black-Box Testing (Opaque-Box Testing)
C. Gray-Box Testing
D. Static Code Analysis

#### **6. A development team uses a fully automated CI/CD framework. They want to implement a scanning tool that acts like an automated web crawler. The tool will automatically navigate the live, running staging environment web application, clicking every button, filling out forms with cross-site scripting (XSS) payloads, and measuring the server's HTTP responses to detect reflections or database errors dynamically. Which DevSecOps testing technology is specifically designed for this?**
A. SAST (Static Application Security Testing)
B. DAST (Dynamic Application Security Testing)
C. SCA (Software Composition Analysis)
D. Threat Modeling

#### **7. A penetration tester discovers an undocumented API endpoint `/admin/debug_delete_user`. By interacting with this endpoint, the tester is able to delete the CEO's account without any authentication credentials, completely bypassing the intended access controls. Which fundamental security testing principle states that discovering this kind of hidden, unauthorized functionality is just as critical as testing documented, intended features?**
A. Testing for "Fail-Safe Defaults"
B. Testing for "Complete Mediation"
C. Testing for "Positive and Negative" requirements (Testing the Unintended)
D. Testing for "Least Common Mechanism"

#### **8. The QA team is writing localized, granular test scripts to verify the functionality of a single newly written Java method `verifyZipCodeFormat(String zip)`. The test inputs specifically check boundary conditions: a valid 5-digit string, a 4-digit string, a 6-digit string, a string with letters, and a `null` input value to ensure the tiny piece of code correctly returns true/false or throws the expected `IllegalArgumentException`. What foundational level of software testing is this?**
A. System Testing
B. Unit Testing
C. Integration Testing
D. Acceptance Testing

#### **9. An organization decides to use Synthetic Data (Mock Data) rather than a copy of the actual live Production database to populate their lower-level Staging and QA testing environments. What is the primary, overriding security justification for mandating this practice across the SDLC?**
A. Synthetic data is faster for the QA team to generate.
B. Using production data forces QA to use a slower database engine.
C. It severely limits the risk of catastrophic data breaches (Information Disclosure / Privacy Violation) if the lesser-secured testing environments are compromised by hackers or accessed by unauthorized QA personnel.
D. Synthetic data uses less disk space than real data.

#### **10. An architect is reviewing the output of a newly installed SAST tool. Over 90% of the reported "Critical SQL Injection Vulnerabilities" are found to be completely harmless because the variables flagged by the tool are internal system constants that never actually process external user input. In security testing terminology, what is the specific classification for these inaccurate, time-wasting automated alerts?**
A. True Positives
B. False Positives
C. True Negatives
D. False Negatives

#### **11. After a development team finishes writing Unit tests for all individual components, the QA team begins combining these individual microservices to verify that they securely authenticate and transmit data correctly when talking to each other across the network bus. They are testing the "mesh" where Service A passes a token to Service B. What level of software testing is being performed?**
A. Unit Testing
B. Integration Testing
C. User Acceptance Testing (UAT)
D. Fuzzing

#### **12. A security assessor is using a vulnerability scanner against a corporate network. To minimize the chances of accidentally crashing the mission-critical legacy database server or causing a highly disruptive Denial of Service (DoS) condition during business hours, which specific scanning methodology MUST the assessor choose?**
A. Fuzz Testing methodology
B. Non-Intrusive (Non-Disruptive) Vulnerability Scanning
C. Intrusive Penetration Testing
D. Social Engineering

#### **13. A Red Team is conducting an advanced engagement. Instead of just running automated scanners to find vulnerabilities in the code, their primary objective is to evaluate how the company's human Security Operations Center (SOC) team and the Blue Team's incident response procedures react to a stealthy, simulated Advanced Persistent Threat (APT) multi-stage attack over several weeks. What kind of specialized testing exercise is this?**
A. Unit Testing
B. Penetration Testing (Standard)
C. Adversarial Simulation / Red Teaming Exercise
D. Software Composition Analysis (SCA)

#### **14. A tester wants to verify the resilience of a cryptographic library. They write a script that systematically feeds every single possible combination of a 4-character password into the login prompt, starting from 'aaaa' and ending at 'zzzz', attempting to guess the correct password to bypass the authentication control. What specific attack simulation is the tester executing?**
A. Brute-Force Attack Testing
B. Fuzz Testing
C. Reverse Engineering
D. Denial of Service (DoS) Testing

#### **15. A software team uses a metric called "Statement Coverage" to evaluate the thoroughness of their automated suite of Unit tests. The report indicates 85% coverage. What exactly does this 85% metric mathematically represent regarding the software's security testing posture?**
A. 85% of all known OWASP vulnerabilities have been tested.
B. 85% of the total number of lines (statements) in the raw source code have been successfully executed at least once during the automated testing process.
C. 85% of the identified threat models have been mitigated.
D. High confidence that 85% of the application is completely secure from hacking.

#### **16. Before a major, highly anticipated release of a new ERP software product, the vendor distributes an almost-finished version of the software to a select group of external, highly trusted industry customers. These customers deploy it in their own real-world test labs to find final bugs and UX issues before the software is sold to the general public. What is the industry-standard term for this final phase of pre-release external testing?**
A. Alpha Testing
B. Beta Testing (External User Acceptance Testing)
C. Unit Testing
D. Fuzzing

#### **17. An enterprise is comparing DAST (Dynamic) and SAST (Static) testing tools. The CISO asks: "Which of these two tools will be able to tell me exactly which file name and which specific line of code (e.g., `login.java, Line 45`) contains the SQL injection vulnerability?" What is the correct technical answer based on how these tools fundamentally operate?**
A. DAST can pinpoint the exact line of code because it attacks the database directly.
B. SAST can pinpoint the exact line of code because it reads the raw static source code files directly. (DAST only sees the compiled/running web pages and HTTP responses).
C. Both tools can easily highlight the exact line of code.
D. Neither tool provides line-level detail; only manual code review can do that.
