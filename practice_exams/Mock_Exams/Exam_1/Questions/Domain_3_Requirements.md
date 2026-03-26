# Exam 1
## Domain 3: Secure Software Requirements (18 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A Business Analyst for an e-commerce platform is drafting User Stories. He writes: "As a shopper, I want to be able to place items in my shopping cart, AND the website's checkout page MUST finish loading in under 2 seconds." The Security Architect immediately demands that the analyst split this sentence apart. In the classification of software requirements, exactly what type of requirement does the statement "the checkout page MUST finish loading in under 2 seconds" represent?**
A. Functional Security Requirement
B. Business Logic Metric
C. Non-functional Requirement (Performance/Availability)
D. Privacy and Compliance Requirement

#### **2. A Requirements Engineer is interviewing the head of the finance department. The executive makes a strict demand: "Because our system handles millions of dollars in customer transfers, I demand that our authentication mechanism be extraordinarily robust. It absolutely cannot rely on just a single, easily guessable password to protect our lifelines." This is abstract business language. When the Requirements Engineer translates this into an actionable "Technical Security Requirement" for the programmers, which of the following is the MOST concrete, verifiable translation?**
A. "The system must be protected by the strongest available technology to prevent any bad actors from hacking user accounts."
B. "The system MUST enforce Multi-Factor Authentication (MFA) for all users attempting to initiate any fund transfer requests."
C. "The system should gracefully attempt to lower the overall risk rating of unauthorized logins."
D. "The system's password length ought to be extremely long and contain multiple complex phonetic characters."

#### **3. When designing a social networking application intended for customers residing in the European Union, the legal team forwards a dense 100-page summary of GDPR mandates. They highlight an incredibly difficult technical directive: "When a deeply unsatisfied user formally decides to delete their account, we must mathematically guarantee that all their posts, uploaded photos, and personal telemetry data are violently and permanently eradicated from our primary databases, third-party backup storage buckets, and all caching servers, leaving absolutely zero trace." What famous, notoriously difficult-to-implement data privacy principle is the legal team demanding?**
A. Right to be Forgotten (Right to Erasure)
B. Right to Data Portability
C. Mathematical Non-repudiation
D. Least Privilege Data Access

#### **4. The enterprise security team is conducting a rigorous security review of a newly proposed flowchart detailing "The Password Reset / Forgot Password Mechanism." On the whiteboard, they use a red marker to draw out a specific scenario known as an "Abuse Case." Which of the following dramatic scenarios MOST accurately describes an "Abuse Case" specifically targeting this password reset mechanism?**
A. A forgetful but legitimate user cannot remember the password they created yesterday and successfully resets it by answering their security questions.
B. A malicious attacker writes an automated script that sends 10,000 requests per second to the reset page, attempting to discover if the sacred account "admin@company.com" actually exists in the corporate database (Username Enumeration).
C. The backend database server suffers a catastrophic hard drive failure, causing all legitimate forgot password requests today to queue and be severely delayed.
D. A user successfully logs in and proactively navigates to their account settings to change their password to something stronger.

#### **5. The Procurement Department is preparing to sign a massive, multi-million dollar contract to lease a Cloud-based SaaS Human Resources Management System. Before the Service Level Agreement (SLA) is finalized, the formidable CISO aggressively intervenes and appends a stern clause to the bottom of the appendix: "The SaaS vendor must generate a monthly cryptographic dashboard report proving that our data maintained an availability rating of 99.99% on your cloud platform. If the availability dips below this exact threshold, the vendor must unconditionally refund our entire service fee for that month." What specific service quality benchmark is the CISO forcefully establishing?**
A. Maximum TimeToPatch (TTP) limit
B. Service-Level Objectives (SLOs)
C. Symmetric Key Length Minimums
D. Mean Time Between Failures (MTBF)

#### **6. A drone navigation software application is currently being developed by an outsourced military contractor. The application's "Security Requirement Specifications Book" contains the following unyielding sentence: "The encrypted communication module operating on the drone SHALL be validated against and strictly comply with the Federal Information Processing Standard (FIPS) 140-2 Level 2." In requirements engineering terminology, what specific category does this unforgiving, government-mandated standard fall into?**
A. Implicit Business Competitor Demands
B. Compliance / Regulatory Standards Requirement
C. Non-functional Usability Requirement
D. Open Design Principle

#### **7. Inside the chaotic world of Agile development, teams employ an adversarial technique. Instead of solely writing optimistic stories about what honest users want the system to do, they begin drafting "Evil Villain" narratives. For example: "As a malicious hacker, I want to inject an obfuscated JavaScript payload into the search bar, so that the browsers of any innocent user viewing the results will silently transfer all their digital reward points into my offshore account." What is the formal name for these specific planning documents that translate attacker goals, methods, and intentions into actionable descriptions?**
A. Firewall Access Control Lists (ACLs)
B. User Interface Mindmaps
C. Misuse / Abuser Cases
D. Threat Landscape Matrix

#### **8. During the preliminary requirements phase for a revolutionary Electronic Medical Record (EMR) system, the Chief Information Officer (CIO) issues a terrifying edict regarding the medical data, which if leaked, could cause devastating reputational ruin and loss of life. The CIO commands: "Before we even begin buying servers or designing databases, your team must first comprehensively assess exactly how devastating the explosive blast radius would be if this specific medical data fell into the hands of a foreign intelligence agency!" What is the formal term for this preliminary phase of the information lifecycle that focuses on measuring the lethal sensitivity of data?**
A. Backup Media Destruction Drill
B. Data Classification and Categorization
C. Public Key Infrastructure (PKI) Stress Test
D. Third-party Library White-box Analysis

#### **9. While actively gathering software security requirements, the Requirements Analyst discovers a violent clash between two massive departments. The aggressive Sales team demands: "To maximize sign-up conversion metrics, customers should face zero identity verification hurdles during registration!" Conversely, the terrifying Legal team roars: "If we do not enforce mandatory dual-citizenship verification and KYC checks for every single user, the federal government will fine us into immediate bankruptcy for money laundering violations!" When faced with horribly conflicting demands, what ultimate, sacred enterprise document should the Requirements Analyst prioritize as the ultimate tie-breaker to establish the final specification?**
A. The Sales department's quarterly revenue projections from last year
B. The company's highest overarching Enterprise Information Security Policies and defined risk appetite
C. The Java Secure Coding Guidelines manual
D. The after-action report from last year's crippling 3-day DDoS outage

#### **10. Once a software requirement is established, it must be written with crystal clarity. Which of the following statements represents an atrociously written, highly ambiguous, and utterly "Untestable" security requirement that would infuriate a Quality Assurance (QA) engineer?**
A. "All passwords stored within the operational data directory MUST be mathematically hashed utilizing the PBKDF2 algorithm combined with a unique cryptographic Salt."
B. "The system MUST immediately write every single failed login attempt, including the originating public IP address, directly to the `/var/log/auth` text file."
C. "The external payment webpage must be designed to be extremely secure so it does not let any bad guys in or allow connections to be broken."
D. "If the authentication module detects 5 consecutive failed login attempts originating against the same username within a 60-second window, the system MUST lock that account for exactly 15 minutes."

#### **11. A US State Supreme Court Judge issues a ruling against a booming tech platform. The ruling dictates that for the next three years, the platform must guarantee that every electronic contract generated possesses undeniable mathematical and legal proof. The judge states: "If the two signing parties end up in my courtroom a decade from now, neither party can *ever* deny saying 'I didn't sign that contract,' and the tech platform itself cannot deny saying 'We never processed that contract.'" What ultimate cybersecurity core property does this inescapable legal liability requirement correspond to?**
A. The obscuring veil of Confidentiality
B. The ultimate limits of System Availability
C. Non-repudiation (Irrefutable proof of origin and integrity)
D. The privacy-focused Right to be Forgotten

#### **12. During the very initiation phase of a massive software lifecycle, a Project Manager proudly receives a 400-page "Requirements Specification" tome from the client. It details exactly how many blue buttons the app needs and precisely when billing emails should be fired. The Lead Security Engineer spends two days reviewing it and declares nervously: "This entire document is a disaster. It does not mention 'minimum password lengths' or 'heartbeat rate-limiting for DDoS defense' a single time." What tragic but common industry phenomenon does this story highlight regarding "requirements," unless security is aggressively prioritized?**
A. Security is usually automatically and perfectly implemented deep beneath the UI color schemes.
B. Security requirements are frequently neglected, treated as uninteresting "non-functional" edge-cases, and entirely forgotten during the initial rush to define business features.
C. Security requirements are always the very first elements injected into User Interface wireframe designs.
D. Security requirements are universally so simple that even non-technical executives can effortlessly write them and force them into the spec sheet.

#### **13. An e-commerce platform receives a terrifying intelligence report from a third-party security firm: "Extremely clever hackers are manipulating your checkout system. They are manually intercepting network traffic to change the 'quantity' field to a negative integer (e.g., Quantity = -10). Because your system is mathematically naive, it multiplies the base price by -10, resulting in the server owing the hacker money, essentially refunding their credit card for an unpurchased item!" To fundamentally and permanently slam this loophole shut, what specific category of validation requirement MUST analysts force into the specification for all "Data Input" fields?**
A. Explicit Data Type Conversion (Casting) requirements
B. Regex character matching for SQL syntax
C. Strict requirements defining mandatory Boundaries, Range Checks, and Business Logic Validations for all incoming data
D. A requirement to log the hacker's IP address upon detection

#### **14. The corporate Procurement arm plans to acquire a massive fleet of IoT security cameras from various global manufacturers. Some of these obscure vendors lack even a basic company website. Horrified, the CISO aggressively injects a non-negotiable "kill order" into the Purchasing Security Requirements document: "Any IoT vendor attempting to sell to this enterprise MUST sign a legally binding contract agreeing that if a critical vulnerability is discovered in their hardware, they will provide a free, patched firmware update within 72 hours." This strict demand directly mitigates risks associated with which crucial security domain?**
A. Supply Chain Risk Management via strict Vendor SLA and Contractual Requirements
B. Complete Unit Testing Automation integration
C. Cryptographic Key Rotation and Retirement scheduling
D. Open-Source Software Component Analysis (SCA)

#### **15. You are the lead architect over an incredibly lucrative Digital Rights Management (DRM) distribution system. Regarding the absolute "Availability Requirement," your aggressive manager barks this bizarrely compromised tolerance standard at you: "I accept that if a massive earthquake destroys the power grid, this server going offline is unavoidable. BUT! No matter how long the server stays dead, when you finally power it back up, the internal DRM database is strictly forbidden from losing more than *the last 15 minutes of new transaction data*. I can tolerate losing those last 15 minutes, but if records from 16 minutes ago are missing, you will be fired and sued." What is the standardized disaster recovery term for this specific "maximum tolerable data loss" time threshold?**
A. Recovery Time Objective (RTO)
B. Recovery Point Objective (RPO)
C. Mean Time To Repair (MTTR)
D. Proof of Work (PoW) Threshold

#### **16. At an ultra-secure clearinghouse, a non-negotiable architectural rule states: "Before any highly sensitive Primary Account Number (PAN) used for credit card billing can exit our internal network gateway en route to a third-party API, the 16-digit PAN MUST be irreversibly swapped out and replaced with a meaningless, randomly generated virtual surrogate string (e.g., `TKN-1249A`). The authentic PAN with real monetary value is strictly forbidden from ever leaving the isolated database." This extreme "fake-money for real-money" data protection requirement is fundamentally designed to satisfy which massive, industry-ruling data security standard?**
A. General Data Protection Regulation (GDPR)
B. ISO 27001 Information Security Management System
C. Payment Card Industry Data Security Standard (PCI DSS) via Tokenization compliance
D. Health Insurance Portability and Accountability Act (HIPAA)

#### **17. During a lively sprint planning session, developers suggest: "We should implement a 'Multi-Language Support' feature so our international user base can comfortably navigate the website." This is a classic functional requirement catering to user comfort. Suddenly, a cynical, veteran Security Engineer interjects: "Love the feature, but regarding this seemingly harmless multi-lingual upgrade, I formally require that REGARDLESS of the user's geographical location or their chosen front-end interface language, every single 404 error, failed login attempt, and stack trace generated by the backend must be strictly written into the database using exclusively Unified English and standardized UTC timestamps." What slightly paranoid but highly critical cybersecurity goal is this engineer trying to safeguard?**
A. To guarantee that external translation agencies have specialized IT error-code work.
B. To significantly reduce database storage space by eliminating Double-Byte Unicode characters.
C. To guarantee that when a massive, global security breach inevitably occurs, global Forensic Analysts and automated SIEM tools can rapidly correlate the attack timeline across a unified, standardized log format devoid of translation ambiguity.
D. This requirement is purely to satisfy baseline testing metrics for Cross-Site Scripting (XSS).

#### **18. A hardened executive draws a massive red circle around a sentence in your draft specification document and screams: "What the hell does 'The system must effectively resist most common network attacks' mean? How am I supposed to pay a QA firm to verify that vague nonsense?!" To correct this atrocious ambiguity and convert the fluff into a highly precise, "Testable Security Requirement" that an auditor can measure with a ruler, you should change it to which of the following?**
A. "The sheer robustness of this magnificent system ought to have the capability to perfectly intercept any inbound packets intended to cause us a minor inconvenience."
B. "The software must mandate that every external input field utilize the most modern, non-lazy defense tools to check for XSS and other bad things."
C. "The system MUST forcefully utilize strictly typed 'Parameterized Queries' to capture all variables before executing any outbound database requests, thereby mathematically eliminating the possibility of SQL Injection exploitation."
D. "The security of the application needs to achieve a psychological threshold such that external hackers will feel it is extremely difficult to breach."
