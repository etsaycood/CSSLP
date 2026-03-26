# Exam 1
## Domain 2: Secure Software Lifecycle Management (14 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. An Agile development squad is conducting a sprint planning meeting for the upcoming two-week sprint. The Product Owner introduces a brand-new, highly anticipated feature that integrates credit card payments via an external API. The security team reviews the initial design sketches on the whiteboard and is immediately concerned about the associated risks. During this very early "Planning/Requirements" phase of Agile, what is the MOST critical activity the security personnel must mandate to be included in the sprint backlog to prevent this feature from becoming a liability?**
A. Pre-writing the code signing certificates for the external credit card vendor.
B. Executing a comprehensive Static Application Security Testing (SAST) scan.
C. Completing a formal Threat Modeling exercise specific to the payment feature.
D. Performing Fuzzing to ensure the mathematical robustness of the new API.

#### **2. The Chief Information Security Officer (CISO) of a large financial institution is reviewing a terrifying audit report: over the past year, 40% of critical vulnerabilities were discovered and hastily patched by the operations team *after* the software was already deployed into the live production environment. Outraged, the CISO mandates a complete paradigm shift, declaring that starting next month, all security testing and vulnerability scanning must be systematically forced to occur much earlier, specifically while developers are still actively writing code. In the software industry, what is this strategic philosophy called?**
A. Shift Left Security
B. Continuous Delivery
C. Zero Trust Architecture
D. Blue-Green Deployment

#### **3. In a multi-million dollar defense contract for a missile control software, the agreement contains a highly stringent clause: "The government will only accept delivery and remit payment if the software code, prior to every single release candidate build, mathematically proves it has passed 100% of automated unit tests and contains zero vulnerabilities with a CVSS score greater than 7.0. If the scanner flags a single violation, the entire deployment pipeline must immediately and automatically halt." What specific, critical security checkpoint in the software development lifecycle does this strict clause describe?**
A. Incident Response Plan (IR Plan)
B. Release Management
C. Break/Build Criteria (Quality/Security Gates)
D. Architecture Risk Analysis

#### **4. A senior software architect is drafting the enterprise-wide "Secure Coding Guidelines." In the section dedicated to C++ development, the architect places a massive red "X" and explicitly writes: "The use of legacy C standard functions such as `strcpy()`, `strlen()`, or `strcat()` for string manipulation is STRICTLY PROHIBITED! Any code utilizing these will be automatically rejected during code review." What specific, catastrophic software vulnerability is the architect attempting to eliminate by blacklisting these ancient functions?**
A. SQL Injection
B. Cross-Site Scripting (XSS)
C. Buffer Overflow
D. Insecure Direct Object Reference (IDOR)

#### **5. A multinational bank decides to outsource the development of its core "Global Cross-Account Transfer Engine" to a highly cost-effective software studio located in Southeast Asia. The Chief Audit Executive is deeply panicked by this decision due to extreme supply chain risks. Even though massive Non-Disclosure Agreements (NDAs) have been signed, what is the MOST "MUST-HAVE," non-negotiable contractual requirement the bank must demand during the acceptance phase to ensure the offshore vendor hasn't secretly embedded a backdoor that could drain the bank's vaults?**
A. A notarized document proving the offshore vendor's office building employs armed security guards.
B. The bank must obtain the application's Software Bill of Materials (SBOM) and mandate an independent, third-party source code security review report.
C. The bank must dispatch a manager to Southeast Asia to physically monitor the offshore developers clocking in and out.
D. A mandatory technical requirement that the software must solely rely upon symmetric encryption algorithms.

#### **6. You have recently been hired as the company's Software Security Coach. You immediately notice a glaring cultural problem: the development team treats security as an afterthought, assuming it's solely the firewall team's responsibility. To shatter this misconception, you organize an internal "Capture the Flag (CTF) Hackathon." You deliberately provide the developers with several broken applications riddled with SQL Injection and XSS vulnerabilities, offering substantial cash prizes to those who can successfully hack and exploit them. What is the ULTIMATE, core training objective of this seemingly destructive internal competition?**
A. To formally assess and aggressively terminate developers who lack innate cybersecurity skills.
B. To significantly elevate the developers' Security Awareness in a realistic, engaging scenario by forcing them to witness firsthand how easily their own poor coding practices can be weaponized.
C. To fulfill an arbitrary KPI mandated by external auditors requiring quarterly "team-building physical activities."
D. To identify developers with destructive tendencies so they can be forcibly transferred to the Red Team.

#### **7. A rapid-growth startup has fully embraced radical DevOps principles, deploying code to their production environment up to 50 times per day. The CISO faces a massive dilemma: the traditional "waterfall" security approach—where code is frozen, handed off to the security team for a week-long manual vulnerability scan, and then handed back for remediation—will absolutely destroy the startup's competitive speed advantage. To successfully integrate "security" into this hyper-fast Agile pipeline without slamming on the brakes, what is the CISO's ONLY viable, modern strategy?**
A. Outsource all security validation to a massive, 24/7 offshore hacking syndicate in India.
B. Fully integrate and automate Static and Dynamic Application Security Testing (SAST/DAST) tools directly inside the CI/CD pipeline, requiring zero human intervention.
C. Cancel all internal security testing and instead purchase excessive cyber liability insurance policies to transfer the risk.
D. Mandate that only developers with 10+ years of seniority are permitted to commit code, thereby eliminating the need for code review time.

#### **8. At the very end of its software lifecycle, an antiquated Customer Relationship Management (CRM) system is scheduled to be formally "Decommissioned." This legacy database contains millions of highly confidential customer records, including credit card numbers and social security numbers, accumulated over the past twenty years. However, the Legal Department intervenes, stating: "According to federal tax laws, these specific historical transaction records must be retained on ice for a mandatory minimum of seven years, ready for potential IRS audits." When executing the decommissioning plan for this old CRM server, what is the MOST legally compliant and standard disposal strategy for this highly sensitive, yet legally bound data?**
A. Physically rip out the database hard drives and violently destroy them using an industrial-grade physical shredder.
B. Install three new layers of firewalls around the old legacy server and leave it permanently powered on in the corner of the data center.
C. Securely transfer and Archive the legally mandated data into a highly protected, inexpensive, offline storage vault, and subsequently execute physical destruction on the old server hardware.
D. Export all the data in plaintext to a public cloud drive so the IRS can easily download it whenever they wish.

#### **9. During the deployment and operations phase of the software lifecycle, a highly bureaucratic yet life-saving process known as "Change Management" is enforced. Your company has an ironclad rule: "Absolutely no one, regardless of executive rank, is permitted to alter a single comma inside a configuration file in the formal Production environment without prior, documented CAB (Change Advisory Board) approval." In the realm of cybersecurity, this draconian rule is primarily designed to defend against and prevent which terrifying, catastrophic operational phenomenon?**
A. Distributed Denial of Service (DDoS) botnet attacks originating from foreign nations.
B. Configuration Drift and undocumented, Unauthorized Changes (backdoors) introduced by internal staff.
C. Advanced SQL Injection payloads bypassing the Web Application Firewall.
D. Brute-force password guessing attacks against the administrative SSH port.

#### **10. Comprehensive frameworks like the Software Assurance Maturity Model (SAMM) or the Building Security In Maturity Model (BSIMM) exist. What is the ultimate, primary purpose of utilizing one of these massive frameworks within an organization?**
A. To automatically scan your source code and magically fix all identified buffer overflows.
B. To provide a standardized translation matrix to localize your software into multiple languages.
C. To provide a quantified, standardized questionnaire and matrix that helps an organization objectively measure, evaluate, and ultimately elevate the overall "maturity and robustness" of its entire secure software development lifecycle.
D. To permanently replace the need for endpoint anti-virus software on developer workstations.

#### **11. During a massive software development project, the Project Manager enthusiastically reports to the executive board: "We have successfully completed 100% of our 'Functional Testing'! When you click the shopping cart button, it accurately places the correct item into the basket." The Security Director immediately pours cold water on the celebration, stating coldly: "But you haven't performed any 'Non-functional Security Testing' yet." Which of the following grueling, server-crushing experiments is the Security Director referring to when demanding "non-functional" tests?**
A. Testing to verify if a user can successfully log in utilizing their correct username and password combination.
B. Executing a "Stress Test" by simultaneously flooding the application with 100,000 synthetic bot requests to verify if it can maintain availability and resilience under extreme, unreasonable loads.
C. Inspecting the font color on the UI registration page to ensure it meets ADA compliance for colorblind users.
D. Reading through the raw source code line-by-line to check for expired copyright header dates.

#### **12. The development team has just performed a heroic, all-night effort to patch a critical zero-day vulnerability. Before this piping-hot patch is pushed to the live production server to save the world, the Quality Assurance (QA) team stands firmly blocking the door. The QA lead insists on re-executing a massive suite containing thousands of ancient, previously passed test cases against this newly patched version of the software. Why is the QA team so pedantically re-running old tests? They are performing which crucial, sacred testing phase?**
A. Incident Response Plan Testing (IR Plan Testing)
B. Micro-level Unit Testing
C. Regression Testing
D. Proactive Threat Modeling

#### **13. As the Director of Security Culture, you are designing a comprehensive "Security Education and Awareness Training" program for the entire enterprise. You understand that generically feeding the same cybersecurity PowerPoint to everyone is a massive waste of time. Which of the following training pairings properly targets specific pain points and is considered a perfect example of effective "Role-based" training?**
A. Teaching the corporate front-desk receptionist how to utilize reverse-engineering tools to disassemble polymorphic malware.
B. Training the executive C-suite (CEO, CFO) on how to write C++ string manipulation functions that are immune to heap overflows.
C. Providing a specialized, hands-on workshop focused entirely on defending against "OWASP Top 10 Web Vulnerabilities" exclusively for the front-line web application development engineers.
D. Mandating that all late-night janitorial staff achieve the rigorous CISSP certification before they are allowed to mop the data center floor.

#### **14. Source Code Version Control Systems (VCS), such as Git, represent the foundational fortress of the development lifecycle. Today, a rogue engineer actively committed a massive block of malicious code designed to silently drop the entire corporate database. Fortunately, your company enforces a strict Git policy: "Every single commit must be cryptographically verified using a Digital Signature generated by the engineer's personal private key." When the security team investigates this disaster to legally prosecute the insider, what two undeniable cryptographic guarantees does this Digital Signature provide?**
A. Complete Confidentiality and perfect Data Integrity.
B. Undeniable Authentication (Non-repudiation of identity) and guarantee of Code Integrity (proof not a single byte was altered).
C. High System Availability and optimal network performance.
D. Complete Mediation and administrative Separation of Duties.
