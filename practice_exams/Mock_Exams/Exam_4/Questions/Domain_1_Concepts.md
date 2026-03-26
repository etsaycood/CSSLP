# Exam 4
## Domain 1: Secure Software Concepts (16 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A new developer on your team suggests implementing a complex, custom cryptographic algorithm for storing user passwords, arguing that because the algorithm is unknown to attackers, it will be impossible to break. As a senior security architect, which fundamental security principle should you immediately cite to correct this dangerous misconception?**
A. The Principle of Least Privilege
B. Kerckhoffs's Principle (Open Design)
C. The Principle of Fail-Safe Defaults
D. The Principle of Economy of Mechanism

#### **2. A healthcare application stores highly sensitive Patient Health Information (PHI). The database is encrypted using AES-256 (Data at Rest), and all network traffic uses TLS 1.3 (Data in Transit). However, a malicious insider with database administrator privileges runs a direct SQL query, exports the entire unencrypted patient table, and sells it on the dark web. Which core tenet of the CIA Triad was compromised in this scenario?**
A. Confidentiality
B. Integrity
C. Availability
D. Non-Repudiation

#### **3. When designing a new online voting system, the architecture team decides to split the final "Tally Votes" function into two distinct sub-processes. Process A is responsible for decrypting the individual ballots, and Process B is responsible for actually adding the decrypted votes to the final total. A single administrator cannot execute both processes; they require two different senior election officials to log in and authorize the respective steps. What security principle is this design pattern enforcing?**
A. Separation of Duties (SoD)
B. Defense in Depth
C. Psychological Acceptability
D. Complete Mediation

#### **4. A cloud-based HR application allows employees to update their own home address. A flaw in the application's authorization logic allows an aggressive employee to modify the API request parameters (e.g., changing `employee_id=105` to `employee_id=1`) to successfully view and modify the CEO's salary information. In security terminology, what specific type of access control violation is this?**
A. A Cross-Site Scripting (XSS) attack
B. Vertical Privilege Escalation
C. Horizontal Privilege Escalation
D. A Buffer Overflow

#### **5. To comply with strict financial regulations, a bank's trading application must ensure that once a trade is executed by a broker, the broker can never later claim, "I did not authorize that trade." To achieve this, the system generates a cryptographic digital signature using the broker's private key for every transaction block. Which specific security concept is directly satisfied by this implementation?**
A. Integrity
B. Authorization
C. Non-Repudiation
D. Availability

#### **6. A corporate firewall is configured with a rule at the very bottom of its Access Control List (ACL) that explicitly drops any incoming packet that did not match any of the "Allow" rules listed above it. This specific configuration strategy perfectly illustrates which core security design principle?**
A. Defense in Depth
B. Fail-Safe Defaults (Implicit Deny)
C. Least Common Mechanism
D. Open Design

#### **7. A software engineering team is building a microservices architecture. They decide that the "Inventory Service" and the "Billing Service" will communicate over the internal network using mutual TLS (mTLS) for encryption and authentication. Furthermore, they implement a strict network policy blocking the two services from communicating with any database other than their own dedicated instances. What foundational security mindset are they applying to their internal network architecture?**
A. Zero Trust Architecture
B. Perimeter-Based Security (Castle-and-Moat)
C. Security by Obscurity
D. Open Design

#### **8. During a security audit, it is discovered that the company's flagship web application uses a single, shared "superadmin" service account database connection string hardcoded in the application's configuration file. Every single user action out on the frontend website, from a guest viewing the catalog to a manager deleting a product, is executed against the backend database using this one omnipotent account. Which principle has been catastrophically violated?**
A. Separation of Duties
B. Principle of Least Privilege
C. Kerckhoffs's Principle
D. Psychological Acceptability

#### **9. A system architect is designing a high-availability e-commerce platform. To ensure the platform can survive an entire AWS Availability Zone going offline or a massive Distributed Denial of Service (DDoS) attack without inconveniencing customers, they deploy the application across three geographic regions and utilize a global load balancer mapped to an auto-scaling group. Which leg of the CIA triad is the architect primarily focusing on?**
A. Confidentiality
B. Integrity
C. Availability
D. Authenticity

#### **10. A user logs into a corporate VPN using their username and password (Something you know). Immediately after, they are prompted to enter a 6-digit code generated by an authenticator application on their smartphone (Something you have). Once authenticated, they attempt to access a confidential HR folder but are denied because they are in the Engineering department. What concepts have just been demonstrated in chronological sequence?**
A. Identification -> Authentication -> Authorization
B. Authentication -> Identification -> Non-Repudiation
C. Authorization -> Authentication -> Identification
D. Identification -> Authorization -> Accounting

#### **11. A legacy operating system requires users to type complex, 20-character passwords containing symbols, numbers, and mixed-case letters, and forces them to change this password every 14 days. As a result, the helpdesk is overwhelmed with password reset requests, and security auditors find sticky notes with passwords written on them physically attached to over 40% of the office monitors. Which security design principle did the creators of this password policy fail to consider?**
A. Complete Mediation
B. Psychological Acceptability (Ease of Use)
C. Fail-Safe Defaults
D. Defense in Depth

#### **12. A development team is creating a new file-sharing application. To protect the files, they implement a web application firewall (WAF) at the network perimeter, require multi-factor authentication (MFA) to access the application, strictly enforce Role-Based Access Control (RBAC) at the application layer, and finally, encrypt the files at rest using AES-256 on the hard drive. What overarching security architectural strategy is this team demonstrating?**
A. Security by Obscurity
B. Zero Trust
C. Defense in Depth (Layered Defense)
D. Separation of Duties

#### **13. What is the fundamental difference between "Authentication" and "Authorization" in secure software design?**
A. Authentication is checking *what* the user is allowed to do; Authorization is proving *who* the user is.
B. Authentication uses encryption; Authorization uses hashing.
C. Authentication verifies the identity of the user (Who are you?); Authorization determines the permissions and actions the authenticated user is allowed to perform (What can you do?).
D. There is no technical difference; the terms are used interchangeably in modern IAM systems.

#### **14. A piece of malware infects a financial system. It does not steal any data (no data exfiltration) and does not crash the system. Instead, it subtly alters the exchange rate variable in the memory by 0.001% every day for six months, leading to massive financial discrepancies in the quarterly reporting. Which aspect of the CIA triad has this specific attack targeted?**
A. Confidentiality
B. Integrity
C. Availability
D. Non-Repudiation

#### **15. When defining Access Control Models for a new military application, the requirement dictates that subjects (users) and objects (files) must be assigned formal security clearance labels (e.g., Top Secret, Secret, Confidential). A user can only access a file if their clearance level is mathematically greater than or equal to the file's classification level, and the system administrator cannot override these mathematical rules. Which historic access control model is being implemented?**
A. Discretionary Access Control (DAC)
B. Role-Based Access Control (RBAC)
C. Mandatory Access Control (MAC)
D. Attribute-Based Access Control (ABAC)

#### **16. A security consultant reviewing an application's architecture discovers that every time a user requests to view an image, the application simply checks if the user's session cookie is valid and then directly serves the image file based on the URL parameter (e.g., `image=receipt_105.jpg`). The application never verifies if the currently logged-in user actually *owns* or has the right to view `receipt_105.jpg`. Which security design principle is being blatantly violated here?**
A. Complete Mediation
B. Economy of Mechanism
C. Open Design
D. Separation of Duties
