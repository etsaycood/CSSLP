# Exam 3
## Domain 1: Secure Software Concepts (16 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A military defense contractor is designing a highly secure, multi-tier intelligence database. To ensure that a compromised front-end web server cannot directly access or query the backend top-secret database servers containing classified blueprints, the network architect places the web servers in a Demilitarized Zone (DMZ) and the database servers in an isolated, internal network segment. All communication between the two zones is strictly controlled by stateful firewalls enforcing specific, narrow ports and protocols. Which foundational security concept is the architect primarily establishing to limit the "blast radius" of a potential breach?**
A. Obfuscation
B. Non-repudiation
C. Segmentation (Network Segmentation / Zoning)
D. Least Privilege

#### **2. An e-commerce heavily relies on a commercial cryptographic library to encrypt millions of credit card transactions daily. One evening, a massive zero-day vulnerability is publicly disclosed, indicating that a specific padding oracle attack can completely decrypt the library's ciphertexts. The company immediately realizes they have absolutely no alternative secondary cryptographic library integrated into their application to switch to. Consequently, to protect customer data, they are forced to completely shut down the entire payment processing system for three agonizing days while their developers frantically attempt to rip out and replace the compromised library. Which core security design principle did the application architectures catastrophically fail to implement?**
A. Complete Mediation
B. Open Design
C. Defense in Depth (specifically regarding Diversity / Redundancy of critical security controls)
D. Separation of Duties

#### **3. A healthcare application processes electronic health records (EHR). When a user successfully authenticates and clicks on a specific patient's profile link, the web application generates the following URL: `https://ehr.hospital.com/view_record?patient_id=88492`. A curious user (Patient A) manually changes the `patient_id` parameter directly in their browser's address bar to `88493` and hits enter. To Patient A's surprise, the application successfully displays the highly sensitive medical history of Patient B. Which fundamental access control principle did the application explicitly fail to enforce on the backend server before retrieving and displaying the data?**
A. Confidentiality (Encryption at Rest)
B. Authorization (specifically preventing Insecure Direct Object Reference / IDOR)
C. Authentication
D. Availability

#### **4. A Chief Information Security Officer (CISO) mandates that all remote employees must use a Virtual Private Network (VPN) equipped with mutual TLS (mTLS) authentication. Furthermore, the CISO decrees that the underlying cryptographic algorithms used by the VPN software (such as AES-256 and ECC) must be publicly published, extensively peer-reviewed mathematical standards governed by NIST, rather than secret, proprietary algorithms developed in-house by the VPN vendor. Which classic security principle is the CISO strictly enforcing to ensure the strength of the cryptography?**
A. Security through Obscurity
B. Kerckhoffs's Principle (Open Design)
C. Fail-Safe Defaults
D. Separation of Duties

#### **5. A financial trading platform must guarantee absolute, undeniable proof that a specific high-value stock execution order was definitively initiated by 'Trader X' and absolutely no one else. The system architecture achieves this by requiring Trader X to digitally sign the transaction payload using an asymmetric private key securely stored in a hardware token that physically requires Traders X's biometric fingerprint to activate. Which core security objective is this architectural design primarily fulfilling?**
A. Availability
B. Non-repudiation
C. Confidentiality
D. Least Privilege

#### **6. A junior developer is tasked with handling error exceptions thrown by the backend SQL database when a user searches for an invalid product ID. To proactively aid the internal helpdesk in fast-tracking debugging efforts, the developer configures the global error handler to intercept the SQL exception and display the exact, raw database error message (e.g., `Syntax error in SQL statement near 'SELECT * FROM products WHERE id =...'`) directly on the public-facing customer webpage. Which security principle has the developer grossly violated, thereby providing reconnaissance gold to potential attackers?**
A. Psychological Acceptability
B. Separation of Duties
C. Fail-Safe (specifically, improperly handling errors and leaking sensitive internal state information)
D. Least Common Mechanism

#### **7. A highly secure government data center mandates a strict physical access control policy: To enter the server room, an employee must first swipe an authorized smart badge (something they have), simultaneously enter a memorized 6-digit PIN on a keypad (something they know), and finally, submit to a biometric retina scan (something they are). What fundamental access control concept does this rigorous, multi-layered entry process represent?**
A. Two-Factor Authentication (2FA)
B. Single Sign-On (SSO)
C. Multi-Factor Authentication (MFA)
D. Federation

#### **8. A monolithic legacy application historically ran entirely under the context of the highly privileged `root` (or `NT AUTHORITY\SYSTEM`) operating system account, meaning a single web vulnerability could allow an attacker total control over the server. The architecture team decides to refactor the application, breaking it down into smaller, individual microservices. They configure the operating system so each specific microservice runs under a dedicated, stripped-down service account that literally only has file-system read access to its specific configuration folder and nothing else. Which foundational security design principle is the team applying?**
A. Economy of Mechanism
B. Principle of Least Privilege
C. Open Design
D. Separation of Duties

#### **9. During an annual compliance audit, the auditor discovers that the application's core "User Password Reset" functionality requires a customer service representative to verbally ask the caller for their social security number, click an "override" button on their web dashboard, and then manually type a new, temporary password to give to the caller over the phone. The auditor heavily criticizes this manual, human-centric process as being highly susceptible to social engineering and operational errors. The auditor strongly recommends replacing it with a fully automated self-service email link system that completely removes the human representative from the loop. Which security design principle is the auditor advocating for?**
A. Complete Mediation
B. Automatic Administration / Economy of Mechanism (simplifying and automating security processes to reduce human error)
C. Open Design
D. Security through Obscurity

#### **10. An organization implements a stringent physical and logical security framework to combat internal fraud. The policy explicitly mandates that the senior software engineer who writes and compiles the trading algorithm source code is structurally and irrevocably banned from possessing the administrative deployment credentials required to actually push that compiled code into the live production trading environment. This critical control requires two completely separate individuals from different departments to successfully deploy a system update. What is this foundational security principle called?**
A. Need-to-Know
B. Separation of Duties (Two-Man Rule)
C. Job Rotation
D. Least Privilege

#### **11. A developer is designing a custom session management module for a web application. To generate the unique "Session ID" cookie given to a user upon successful login, the developer decides to simply hash the user's username concatenated with the current timestamp (e.g., `MD5(username + time)`). A security architect immediately flags this design as fundamentally flawed because an attacker could trivially predict or bruteforce the sequence of future Session IDs if they know a victim's login time. To fix this, the architect mandates the use of a Cryptographically Secure Pseudo-Random Number Generator (CSPRNG). What specific characteristic is the architect demanding the Session IDs possess to prevent predictive attacks?**
A. High Entropy (Unpredictability / Randomness)
B. Non-repudiation
C. Confidentiality
D. Data Integrity

#### **12. A massive, global cloud provider guarantees a Service Level Agreement (SLA) of 99.999% ("Five Nines") uptime for their core object storage service. To achieve this extreme level of operational resilience against natural disasters or localized data center fires, the architecture is designed so that every single file uploaded by a customer is automatically and instantly replicated across three geographically distinct data centers spread across different tectonic plates. Which of the three core pillars of the CIA Triad is this extreme replication strategy primarily engineered to safeguard?**
A. Confidentiality
B. Integrity
C. Availability
D. Non-repudiation

#### **13. An application uses a central configuration file (`config.xml`) that dictates critical database connection strings and API keys. The operations team configures the file system permissions so that the application service account has "Read-Only" access to this file, while only the "Administrators" group has "Write" access. However, the application logic does absolutely nothing to verify if the file has been maliciously modified (e.g., by checking a digital signature or cryptographic hash) before loading it into memory at startup. If an internal attacker with admin rights modifies the file, which core security concept has the application failed to independently verify?**
A. Confidentiality
B. Authentication
C. Data Integrity
D. Non-repudiation

#### **14. A Chief Information Officer (CIO) is giving a presentation to the board of directors arguing against spending $5 million on a newly proposed, ultra-advanced AI threat detection system. The CIO presents a risk analysis report proving that even if the company suffered a total, worst-case scenario data breach of their specific customer database, the absolute maximum financial impact (fines, lawsuits, and lost business) would only amount to $2 million. Therefore, spending $5 million to protect a $2 million asset is financially irrational. Which fundamental risk management concept is the CIO employing to justify rejecting the security investment?**
A. Risk Avoidance
B. Cost-Benefit Analysis (ROI of Security Controls)
C. Threat Modeling
D. Vulnerability Scanning

#### **15. An organization's HR system contains thousands of highly sensitive employee salary records. The security policy dictates that the "Apprenticeship Program Director" may log into the system to view the names of all current apprentices, but the system must absolutely blind them to the 'Salary' column, displaying only asterisks `***` or denying access to that specific field entirely. However, the system must allow the Director to successfully view the 'Department' and 'Start Date' columns for those exact same records. This highly granular, column-level restriction of visibility is an enforcement of which principle?**
A. Separation of Duties
B. Complete Mediation
C. Need-to-Know (Granular Data Masking/Access Control)
D. Cryptographic Hashing

#### **16. A company develops a proprietary industrial control system (ICS) protocol to communicate with physical machinery on a factory floor. In a misguided attempt to prevent attackers from sending malicious commands, the development team decides not to use industry-standard encryption like TLS. Instead, they invent a secret, undocumented mathematical algorithm to scramble the commands. They argue that because the algorithm is a closely guarded corporate secret and not published on the internet, hackers will never figure out how to crack it. Which notoriously flawed and universally condemned security anti-pattern is this engineering team relying upon?**
A. Defense in Depth
B. Security through Obscurity
C. Kerckhoffs's Principle
D. Least Privilege
