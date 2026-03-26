# Exam 1
## Domain 6: Secure Software Testing (17 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A QA engineer is preparing to conduct Security Testing on a newly compiled C++ application. The engineer possesses the final executable binary but has absolutely zero access to the original source code, internal architectural diagrams, or the developer's documentation. The engineer plans to barrage the application's input fields with randomly generated, malformed data to see if it crashes. What specific type of software security testing methodology is the engineer employing?**
A. White-Box Static Analysis (SAST)
B. Black-Box Fuzzing (Dynamic Testing)
C. Gray-Box Interactive Application Security Testing (IAST)
D. Formal Verification and Logic Proving

#### **2. You are integrating security into the Continuous Integration (CI) pipeline of a sprawling Java project. You want to implement a tool that automatically scans the developers' raw source code every time they commit it to the repository. The goal is to detect hardcoded passwords, unsafe `exec()` calls, and missing input validation routines *before* the application is even compiled or run. Which category of testing tool is explicitly designed for this early-stage, code-level analysis?**
A. Dynamic Application Security Testing (DAST)
B. Static Application Security Testing (SAST)
C. Web Application Firewall (WAF) Fingerprinting
D. Penetration Testing (Pen Test)

#### **3. During a rigorous Web Application Penetration Test, the Red Team tester attempts to discover hidden administrative directories on the target server. The tester configures a proxy tool (like Burp Suite) and loads a massive dictionary text file containing thousands of common directory names (e.g., `admin/`, `backup/`, `test/`). The tool automatically sends thousands of HTTP GET requests to the server, observing the HTTP response codes (e.g., 200 OK vs. 404 Not Found) to map the hidden structure. What specific attack technique is the tester performing?**
A. Brute-Force Directory Enumeration / Forced Browsing
B. Cross-Site Tracing (XST)
C. SQL Blind Injection
D. Man-in-the-Middle (MITM) Interception

#### **4. A Lead QA Tester is designing the test cases for a new "Account Lockout Mechanism." The requirements state: "The system MUST lock the account for 15 minutes after exactly 5 consecutive failed login attempts." To comprehensively verify this boundary condition, the QA tester executes three specific test scenarios: Scenario A (4 failed attempts), Scenario B (exactly 5 failed attempts), and Scenario C (6 failed attempts). What fundamental software testing technique is the tester utilizing to ensure the logic behaves correctly right at the edge of the specification?**
A. Combinatorial Pairwise Testing
B. Fuzz Testing
C. Boundary Value Analysis (BVA)
D. Statistical Code Coverage Metrics

#### **5. The development team relies heavily on an open-source JavaScript UI library (`vue.js`) and a third-party logging framework (`log4j`). The Chief Information Security Officer (CISO) is terrified that a zero-day vulnerability might be discovered in one of these dependencies, silently compromising the application. To continuously monitor and test for known vulnerabilities (CVEs) residing hidden within these third-party libraries, which specific type of automated scanning tool MUST the team integrate into their pipeline?**
A. Software Composition Analysis (SCA)
B. Interactive Application Security Testing (IAST)
C. Network Vulnerability Scanner (e.g., Nessus)
D. Static Application Security Testing (SAST)

#### **6. A security analyst is performing a dynamic test on a web application's search bar. She types this exact payload into the search box: `<script>alert(document.cookie)</script>`. Upon pressing enter, her browser executes the payload, and a pop-up window displays her current session cookie. The analyst successfully proved the application is highly vulnerable to which specific attack?**
A. Local File Inclusion (LFI)
B. Stored / Persistent Cross-Site Scripting (XSS)
C. Reflected / Non-Persistent Cross-Site Scripting (XSS)
D. Cross-Site Request Forgery (CSRF)

#### **7. You are managing a massive testing effort for a legacy C banking backend. To ensure the testing is thorough, the QA manager insists on measuring "Code Coverage." The manager states: "Our goal is to execute test cases until we achieve 100% Branch Coverage." In the context of White-Box testing, what does "Branch Coverage" specifically guarantee?**
A. Every single function in the application has been called at least once by the test suite.
B. Every line of source code in the application has been executed at least once by the test suite.
C. Every possible boolean decision outcome (both the 'True' and 'False' paths of every `if/else` statement) has been executed at least once by the test suite.
D. Every possible combination of input variables has been exhaustively tested.

#### **8. An organization employs a "Bug Bounty Program" where external, freelance ethical hackers are paid directly for finding vulnerabilities in their public production website. During a live test, an external researcher discovers a flaw allowing them to download the entire customer database. However, instead of stopping and reporting the flaw, the researcher proceeds to download all 5 million records and then emails the CEO, demanding $50,000 to delete the data, threatening to leak it if unpaid. Which critical "Rules of Engagement (RoE)" boundary did the researcher flagrantly violate?**
A. The limitation on automated scanning tools.
B. The prohibition against Social Engineering the staff.
C. The strict restriction on Data Exfiltration and the principle of doing no harm (Extortion).
D. The requirement to use Black-Box testing methodologies only.

#### **9. A highly advanced testing tool operates from *inside* the application environment (like a Java agent). While the QA team clicks around the web frontend performing normal functional tests (DAST), this internal agent continuously monitors the backend memory, database queries, and variable data flows in real-time. If it detects a SQL injection payload moving through the application's memory toward the database, it immediately flags the exact line of Java code responsible. What is the industry term for this hybrid testing technology?**
A. Static Application Security Testing (SAST)
B. Fuzz Testing
C. Software Composition Analysis (SCA)
D. Interactive Application Security Testing (IAST)

#### **10. A penetration testing team successfully exploits a vulnerable web server, obtaining a low-level "guest" shell access. Their ultimate objective is to read a highly sensitive configuration file restricted to the "root" administrator. The testers discover an outdated local kernel process running in the background. They execute an exploit against this specific kernel process to upgrade their "guest" shell into a "root" shell. In the standard phases of Penetration Testing, what specific phase does this action represent?**
A. Reconnaissance and Information Gathering
B. Elevation of Privilege (Privilege Escalation)
C. Vulnerability Scanning
D. Covering Tracks and Maintaining Access

#### **11. A security auditor reviews the test plan for a new cryptographic module. The programmer wrote a test that successfully encrypts a string of text. The test then asserts: `assertTrue(encryptedText.length() > 0)`. The auditor rejects this test case as completely insufficient for cryptographic testing. What is the fundamental problem with this specific test approach regarding cryptography, and what must be tested instead?**
A. The test is written in Java, but cryptography should only be tested using C++.
B. The test only verifies that *some* output was generated, but it utterly fails to prove that the output mathematically matches the expected, standard ciphertext (Known Answer Test / KAT) or that the data can actually be successfully decrypted back to its original state.
C. The test executes too quickly, which violates the requirement for slow cryptographic operations.
D. Cryptography cannot be unit-tested; it must only be tested via Black-Box penetration testing.

#### **12. A dedicated "Red Team" is hired to conduct a full-scope simulated cyberattack against an enterprise. Unlike a standard Penetration Test that focuses solely on finding software bugs, the Red Team heavily utilizes "Phishing Emails" mimicking the CEO, drops infected USB drives in the company parking lot, and attempts to tailgate employees through the physical security gates. What is the primary objective of this comprehensive Red Team engagement?**
A. To measure the exact number of XSS vulnerabilities in the web application using SAST tools.
B. To test the holistic effectiveness of the organization's entire defensive posture, including its people (security awareness training), processes (incident response), and physical security, not just the technical software controls.
C. To debug the Continuous Integration (CI) deployment scripts.
D. To verify compliance with the General Data Protection Regulation (GDPR) privacy rules.

#### **13. During a DAST scan of an online forum, the automated tool detects a concerning behavior. The scanner inputs `1' OR '1'='1` into the username field. The resulting HTTP response does not display a visible database error on the screen, nor does it log the user in. However, the automated scanner noticed that the web server took exactly 15 seconds to respond to that specific malicious payload, whereas all normal requests only take 0.1 seconds. What sophisticated vulnerability did the scanner likely discover using this time-delay technique?**
A. Time-Based Blind SQL Injection
B. Denial of Service (DoS) Resource Exhaustion
C. Reflected Cross-Site Scripting (XSS)
D. Cross-Site Request Forgery (CSRF)

#### **14. A tester is examining the "Password Reset" logic. She creates two identical test accounts: `victim@test.com` and `attacker@test.com`. She clicks "Forgot Password" for the victim and receives a password reset token in the victim's email inbox: `Token=XYZ123`. She then logs into the attacker's account, initiates a password reset for the attacker, but uses a proxy tool to swap the attacker's token in the HTTP request with the victim's `Token=XYZ123`. The system accepts the request and changes the *victim's* password to a new password chosen by the attacker. What critical business logic flaw did this manual test successfully demonstrate?**
A. Server-Side Request Forgery (SSRF)
B. Broken Authentication / Insecure Session Management
C. SQL Injection
D. XML External Entity (XXE) Injection

#### **15. You are the security lead for a massive, multi-year software project. Management demands a comprehensive metric to determine "how well our security testing is going overall." Which of the following is the MOST meaningful metric to report to the executive board regarding the true effectiveness of the secure software testing program?**
A. The total number of test cases written by the QA department this month.
B. The percentage of developer code automatically scanned by the SAST tool within 5 minutes.
C. The total count of raw vulnerabilities discovered by the automated DAST scanner, including all false positives.
D. The "Defect Density" and the "Remediation Rate" (the speed and percentage of critical vulnerabilities that are actually fixed/patched after being discovered in testing).

#### **16. Before initiating a Penetration Test on a critical, live production database server, the Lead Tester and the enterprise CISO must sign a formalized document. This document strictly defines what IP addresses the testers can attack, specifies that they cannot perform Denial of Service (DoS) attacks, and dictates what hours they are permitted to test. What is the universally recognized term for this critical legal and operational document?**
A. The Non-Disclosure Agreement (NDA)
B. The Rules of Engagement (RoE)
C. The End-User License Agreement (EULA)
D. The Security Level Agreement (SLA)

#### **17. A team is building an e-commerce checkout flow. The security engineer writes a test script that intentionally tries to add a negative quantity of items to the cart (`quantity = -5`) to see if the total price decreases, resulting in the server owing the user money. This type of testing, which deliberately inputs invalid or unexpected data to verify the system handles errors securely and does not enter a failed state, is formally known as what?**
A. Positive Path Testing / "Happy Path" Testing
B. Negative Testing / Abuse Case Testing
C. Static Application Security Testing (SAST)
D. Code Review Walking
