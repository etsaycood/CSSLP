# Exam 2
## Domain 1: Secure Software Concepts (16 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A financial institution is designing a new high-value wire transfer application. The Chief Information Security Officer (CISO) is adamant that once a trader submits a wire transfer request exceeding $10 million, they must be mathematically prevented from later claiming, "I never authorized that transaction." To achieve this specific security requirement, which cryptographic implementation is the BEST choice?**
A. Implementing strong two-factor authentication (MFA) using hardware security keys for all traders.
B. Requiring the trader's client application to digitally sign the transaction payload using the trader's private key before submission.
C. Encrypting the entire network session using TLS 1.3 with Perfect Forward Secrecy (PFS).
D. Storing all transaction logs in a centralized, append-only Security Information and Event Management (SIEM) system.

#### **2. A development team is architecting a nuclear reactor monitoring system. The system polls temperature sensors every second. If the central control software loses its network connection to the sensors, the system's default behavior must be decided. According to the foundational security design principle of "Fail Safe / Fail Secure," what is the FIRST and MOST appropriate action the software should take upon losing connectivity?**
A. Suppress the error message and display the last known good temperature until the connection is restored to avoid panicking the operators.
B. Automatically reboot the central monitoring server to attempt a clean connection reset.
C. Enter a safe default state by initiating a controlled shutdown procedure for the reactor while sounding emergency alarms.
D. Switch to an alternative, untested backup network protocol to blindly attempt reconnection.

#### **3. During a code review of a monolithic web application, a security engineer notices that when a user logs in, the system checks their permissions and creates a session cookie. For all subsequent HTTP requests (e.g., viewing records, deleting users), the application only checks if the session cookie is valid, but it never re-checks the database to see if the user's role has been revoked since their initial login. Which core security design principle is this application definitively violating?**
A. Complete Mediation
B. Economy of Mechanism
C. Least Common Mechanism
D. Separation of Duties

#### **4. A junior security architect proposes building a custom, multi-layered encryption protocol that combines AES, ChaCha20, and a proprietary scrambling algorithm to protect data at rest. The architect believes this complexity will make it unbreakable. A senior reviewer immediately rejects the proposal and mandates using standard AES-256 with an established key management system instead. Which security design principle is the senior reviewer explicitly enforcing?**
A. Defense in Depth
B. Open Design
C. Economy of Mechanism
D. Least Privilege

#### **5. A company creates a DRM (Digital Rights Management) software to protect video files. To prevent piracy, the developers hardcode the master decryption key deep inside a heavily obfuscated C++ Dynamic Link Library (DLL), assuming hackers will never find it. Within two days of release, the key is extracted and published online. The developers' failure stems from relying on "Security by Obscurity," which directly violates which foundational security design principle?**
A. Psychological Acceptability
B. Separation of Privilege
C. Complete Mediation
D. Open Design

#### **6. A small DevOps team sets up their CI/CD pipeline. Currently, any software developer can write code, commit it to the main branch, and trigger an automated deployment directly to the live production server without any other person reviewing or approving the changes. To prevent a rogue developer from intentionally deploying malicious code, what operational security principle MUST be implemented FIRST?**
A. Defense in Depth
B. Least Common Mechanism
C. Separation of Duties (Dual Control)
D. Cryptographic Non-repudiation

#### **7. A hospital implements a hyper-aggressive AI-driven endpoint protection system. The system is configured to instantly isolate any medical device or server from the network if it detects even a minor anomaly. During a critical surgery, the AI flags a false positive and completely locks down the electronic health records (EHR) database. The surgical team cannot access patient blood types, putting lives at immediate risk. This scenario highlights a severe conflict between which two core security concepts?**
A. Authentication vs. Authorization
B. System Confidentiality vs. System Availability
C. Data Integrity vs. Data Non-repudiation
D. Defense in Depth vs. Complete Mediation

#### **8. The IT department issues a new password policy requiring all employees to create 24-character passwords containing uppercase, lowercase, numbers, and three special symbols. Furthermore, the password must be reset every 14 days and cannot match the last 20 passwords. Within a week, the security team finds employees writing their passwords on sticky notes attached to their monitors. Which security design principle did the IT department completely ignore?**
A. Economy of Mechanism
B. Psychological Acceptability
C. Least Privilege
D. Fail Safe Defaults

#### **9. A B2B application processes high-value wholesale orders via a REST API. The development team wants to ensure that an attacker sitting on the network cannot intercept a valid `$50,000` order packet and subtly change the payload to read `$50` before it reaches the server. Which of the following cryptographic solutions provides the strongest mathematical guarantee of Data Integrity for the message payload?**
A. Establishing a VPN tunnel between the client and server.
B. Encrypting the payload using the RSA Public Key algorithm.
C. Generating and appending a Keyed-Hash Message Authentication Code (HMAC) to the payload.
D. Encoding the payload using Base64 before transmission.

#### **10. Your risk management team is evaluating a newly discovered buffer overflow vulnerability in a legacy internal application. The application processes massive amounts of highly classified data (High Impact). However, the application is hosted on an air-gapped, physically isolated standalone machine with no network connection, no USB ports, and strict physical armed guards. In the context of the standard Risk Equation ($Risk = Threat \times Vulnerability \times Impact$), how should the overall risk level BEST be classified?**
A. High Risk, because the data is highly classified and the vulnerability is known.
B. Critical Risk, because buffer overflows always carry an immediate critical rating.
C. Low to Minimal Risk, because despite the high impact and existing vulnerability, the likelihood of a threat agent physically accessing the isolated system is practically zero.
D. Unknown Risk, until a penetration test is aggressively performed.

#### **11. A user successfully logs into an e-commerce platform by supplying their username, a complex password, and a One-Time Password (OTP) sent to their phone. Once logged in, the user manually types `https://store.com/admin/delete_user` into the URL bar. The server executes the script and deletes the requested user, even though the logged-in user is only a standard customer. What specific security concept failed in this system?**
A. Authentication
B. Accountability
C. Data Confidentiality
D. Authorization

#### **12. An application requires access to a backend database simply to perform daily `SELECT` queries to generate read-only sales reports. The system administrator configures the application's connection string to use the database's `db_owner` (Database Owner) account, reasoning that it makes deployment easier and avoids permission errors. Which fundamental security principle is being egregiously violated?**
A. Least Privilege
B. Separation of Duties
C. Open Design
D. Complete Mediation

#### **13. During a forensic investigation following a massive data breach, investigators look at the system logs. They see that an account named `Web_Admin` executed the malicious data export command. However, the company has six different system administrators who all know and regularly use the `Web_Admin` password to perform daily tasks. Because the company cannot pinpoint exactly which human being performed the action, the system has failed to provide which essential security attribute?**
A. Non-repudiation
B. Authorization
C. Individual Accountability
D. Need-to-Know

#### **14. A corporate network relies exclusively on a single next-generation perimeter firewall to protect its internal web servers. A security consultant warns that if a hacker exploits a zero-day vulnerability to bypass the firewall, the entire internal network will fall immediately. The consultant recommends deploying a Web Application Firewall (WAF), Host-based Intrusion Prevention Systems (HIPS) on the servers, and strict application-level input validation. What overarching security strategy is the consultant advocating?**
A. Fail Safe Defaults
B. Defense in Depth (Layered Defense)
C. Economy of Mechanism
D. Least Common Mechanism

#### **15. A cloud provider offers multi-tenant hosting. To save RAM, the engineers design a single, shared cryptographic key generation module in the kernel. Both "Tenant A" and "Tenant B" must call this exact same physical module in memory whenever they need a new encryption key. A security researcher discovers that by exhausting the entropy pool as Tenant A, they can predict the cryptographic keys generated for Tenant B. Which design principle was violated by forcing different security domains to share the same pathway?**
A. Open Design
B. Least Common Mechanism
C. Complete Mediation
D. Separation of Duties

#### **16. A simple mobile application designed to function as a basic calculator prompts the user to grant permissions to access their GPS location, contact list, and read SMS messages before it will launch. What core privacy and data protection principle is this application blatantly violating?**
A. Data Minimization / Purpose Limitation
B. Non-repudiation
C. Data Anonymization
D. Cryptographic Integrity
