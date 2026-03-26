# Domain 5: Secure Software Implementation (17 Questions)

#### **1. A developer relies on an external framework to enforce authorization rules by simply adding a `@RolesAllowed("ADMIN")` annotation above a sensitive API method, rather than writing custom `if-else` permission checks within the method itself. This is an example of which security approach?**
A. Imperative security
B. Declarative security
C. Programmatic security
D. Concurrency management

*   **Answer: B**
*   **Rationale:** **Declarative security** relies on the underlying framework or container to enforce security policies (usually via annotations or XML configurations) outside of the business logic code. **Imperative (Programmatic) security**, conversely, involves developers writing custom control flow code (like `if (user.role == "ADMIN")`) directly within the method.

#### **2. Which of the following vulnerabilities is the DIRECT result of a failure to properly execute Output Sanitization (Encoding)?**
A. SQL Injection
B. Cross-Site Scripting (XSS)
C. Buffer Overflow
D. Insecure Direct Object Reference (IDOR)

*   **Answer: B**
*   **Rationale:** **Cross-Site Scripting (XSS)** occurs when an application includes untrusted data in a web page without proper validation or escaping (Output Sanitization or Contextual Encoding). If output is not encoded, the victim's browser will execute the injected malicious JavaScript. While SQL Injection is an input validation issue, XSS is fundamentally an output encoding failure.

#### **3. A development team is fixing a bug where two distinct users purchasing the last available ticket simultaneously results in an oversold event. The developers implement a database locking mechanism to ensure the transactions are queued and processed sequentially. This mitigation addresses the security risks associated with:**
A. Concurrency (Thread Safety / Race Conditions)
B. Output Obfuscation
C. Microarchitecture speculative execution
D. Sandboxing

*   **Answer: A**
*   **Rationale:** **Concurrency** issues (like Race Conditions or Time-of-Check to Time-of-Use [TOCTOU] flaws) occur when asynchronous threads or processes access shared resources simultaneously without proper synchronization (like database locks or thread safety mechanisms), leading to unauthorized modification or logical flaws.

#### **4. An application is designed to catch fatal database query errors. Instead of displaying the raw ODBC connection string and SQL syntax error to the end user on the web page, the application logs the detailed error internally and presents a generic "An unexpected error occurred. Please try again later" message to the user. This secure coding practice prevents which specific threat?**
A. Cross-Site Request Forgery (CSRF)
B. Elevation of Privilege
C. Information Disclosure
D. Repudiation

*   **Answer: C**
*   **Rationale:** Proper **Error and Exception Handling** prevents **Information Disclosure**. Exposing raw stack traces, database schema details, or connection strings to end users gives attackers valuable reconnaissance data they can use to map the system's architecture and craft targeted exploits.

#### **5. To protect highly sensitive PII (like Social Security Numbers) within a database, an organization mathematically replaces the sensitive data with a randomly generated, primary-key referencing surrogate value. If the database is stolen, the surrogate values hold zero mathematical relationship to the original data. This process is called:**
A. Encryption
B. Hashing
C. Tokenization
D. Obfuscation

*   **Answer: C**
*   **Rationale:** **Tokenization** replaces sensitive data with non-sensitive substitutes (tokens). Unlike encryption (which uses math and a key to transform the data, and can be decrypted), tokenization stores the real data in a secure, isolated vault and only passes the meaningless token to downstream systems, completely removing the mathematical relationship between the token and the real data.

#### **6. A security engineer evaluates an application’s session management implementation. After a user successfully authenticates by providing their username and password, what is the MOST critical action the application must perform regarding the session ID?**
A. Encrypt the existing session ID using AES-256 in transport.
B. Generate and issue a completely new, cryptographically random session ID.
C. Store the existing session ID in a secure database table.
D. Append the user's password hash to the session ID for extra security.

*   **Answer: B**
*   **Rationale:** Upon successful authentication (or privilege escalation), the application must perform **Session Fixation protection** by invalidating the pre-authentication session ID and issuing a entirely **new, highly random session ID**. This prevents an attacker from tricking a user into authenticating using a session ID the attacker already knows.

#### **7. An application development team decides to include a known cryptographic library (like OpenSSL) rather than writing custom AES encryption code. Which of the following is an associated risk they MUST actively evaluate and mitigate when reusing third-party code?**
A. The psychological acceptability of the user interface.
B. Transitive vulnerabilities and the need for continuous Software Composition Analysis (SCA).
C. Ensuring the third-party library uses programmatic rather than declarative security.
D. Validating that the library prevents SQL injection.

*   **Answer: B**
*   **Rationale:** While **secure code reuse** is highly recommended over writing custom crypto, importing third-party libraries (especially open-source) introduces the risk of inheriting previously undiscovered or future vulnerabilities. Managing this requires continuous tracking via an SBOM and **Software Composition Analysis (SCA)** tools to identify vulnerable, outdated components.

#### **8. A software product accepts an uploaded ZIP archive file from an untrusted user. To prevent a "Zip Bomb" (a tiny ZIP file that decompresses into petabytes of junk data) from crashing the server, the developers implement strict file size limits during the decompression process. This control is an example of:**
A. Sandboxing
B. Compiler switches
C. Resource management
D. Static Application Security Testing (SAST)

*   **Answer: C**
*   **Rationale:** A "Zip Slip" or "Zip Bomb" aims to execute a Denial of Service by exhausting disk space or memory. Implementing strict bounds on CPU, memory, network, and storage allocation during untrusted operations is a critical facet of secure **Resource management**.

#### **9. As a mandatory step before any code is committed to the main branch, developers run an automated tool integrated into their IDE. This tool analyzes the source code without executing it, flagging the exact line numbers where insecure API calls and potential buffer overflows exist. This tool is categorizing as:**
A. Dynamic Application Security Testing (DAST)
B. Static Application Security Testing (SAST)
C. Interactive Application Security Testing (IAST)
D. Software Composition Analysis (SCA)

*   **Answer: B**
*   **Rationale:** **SAST (Static Application Security Testing)** is a white-box testing methodology that analyzes the raw source code, bytecode, or binaries for security vulnerabilities *without* executing the program. It provides exact line numbers for vulnerabilities like XSS, SQLi, and buffer overflows early in the implementation phase.

#### **10. An attacker discovers that by inserting massive amounts of padding and chaotic inputs, they can force the application to consume excessive resources. To defend against this, the developers implement an "Accept List" (Allow-list) validation approach. How does an "Accept List" work?**
A. It blocks known bad characters (like `<script>` or `' OR 1=1`) and allows everything else.
B. It defines exactly what is allowed (e.g., only alphanumeric characters, length 1-15) and implicitly blocks everything else.
C. It tokenizes the input to ensure it cannot be executed by the microprocessor.
D. It relies on a WAF to inspect network traffic.

*   **Answer: B**
*   **Rationale:** An **Accept (Allow) list** strictly defines the expected, safe input criteria (type, length, format, range) and rejects anything that does not perfectly match. It is far superior to a Block (Deny) list, which attempts to filter out "known bad" characters—an approach attackers easily bypass using evasion techniques.

#### **11. A C/C++ development team discovers a memory management flaw in their application causing a buffer overflow. As a compensatory defense-in-depth measure while the code is being rewritten, the security engineer instructs the team to recompile the application with ASLR (Address Space Layout Randomization) and DEP (Data Execution Prevention) flags enabled. These flags are examples of:**
A. Compiler switches
B. Static code analyzer linting rules
C. Microarchitecture processor extensions
D. Sandboxing environments

*   **Answer: A**
*   **Rationale:** Modern compilers provide built-in security features mapped to OS-level protections (like ASLR, DEP/NX bit, Stack Canaries/Cookies, and SafeSEH). Activating these **Compiler switches** fortifies the binary against exploitation of memory corruption vulnerabilities without requiring code changes.

#### **12. A developer encounters a scenario where an application occasionally reads stale data from memory locations previously used by another process. This data leakage is typically prevented at the hardware level by implementing:**
A. Thread safety locking
B. Isolation boundaries (Sandboxing/Virtualization) and Processor microarchitecture security extensions
C. Mandatory Access Control (MAC) lists
D. Watchdog timers

*   **Answer: B**
*   **Rationale:** To prevent processes from snooping on each other's memory (like in the Spectre/Meltdown vulnerabilities), software must rely on OS-level **isolation** (Process spacing, Virtualization) and explicit **Processor microarchitecture security extensions** to enforce memory segmentation and prevent cache side-channel leaks.

#### **13. During a code review of a critical financial algorithm, an organization requires a senior engineer, who did not write the code, to manually read and approve the logic before merging. The primary reason to mandate manual code review OVER automated SAST scanning is that manual review:**
A. Is significantly faster and cheaper to execute at scale.
B. Automatically updates the OWASP Top 10 database.
C. Is highly effective at identifying complex business logic flaws and backdoors that automated tools cannot understand.
D. Provides comprehensive code execution coverage testing.

*   **Answer: C**
*   **Rationale:** While SAST is excellent at catching syntax flaws (like missing output encoding), automated tools cannot understand business context. **Manual Code Review (Peer Review)** is the only effective way to catch complex logic flaws, authorization bypasses, and intentionally inserted **malicious code (backdoors or logic bombs)**.

#### **14. When implementing access control within a legacy application, the developers create a discrete list attached to every single file, detailing which specific user ID is allowed to read, write, or execute that specific file. The owner of the file can change these permissions at will. What access control model is this?**
A. Role-Based Access Control (RBAC)
B. Mandatory Access Control (MAC)
C. Discretionary Access Control (DAC)
D. Attribute-Based Access Control (ABAC)

*   **Answer: C**
*   **Rationale:** **Discretionary Access Control (DAC)** operates by assigning permissions explicitly to an entity based on its identity (using Access Control Lists - ACLs), and vitally, access rights are granted at the "discretion" of the object's owner.

#### **15. To implement confidentiality for data at rest, an organization chooses to encrypt a highly sensitive database. However, the business logic requires the ability to quickly rotate algorithms if a cryptographic flaw is discovered in the future without completely rewriting the application code. This principle is known as:**
A. Cryptographic Agility
B. Salting and Key Stretching
C. Complete Mediation
D. Cryptographic Validation

*   **Answer: A**
*   **Rationale:** **Cryptographic Agility** is the design and implementation capability of a system to rapidly switch between different cryptographic primitives, algorithms, and key sizes without requiring catastrophic architectural overhauls if a current algorithm is compromised.

#### **16. An application writes detailed security audit logs. However, during a PCI compliance audit, it is discovered that the logs are capturing the plain-text credit card numbers of users inputting data into the payment screen. This represents a severe failure in:**
A. Output sanitization
B. Performance resource management
C. Secure logging & auditing (Confidentiality/Privacy)
D. Concurrency

*   **Answer: C**
*   **Rationale:** **Secure logging** mandates that while system events must be thoroughly audited for accountability, developers must ruthlessly scrub or mask sensitive configuration secrets, credentials, and PII/payment data from the logs to prevent them from becoming a massive **Privacy/Confidentiality** vulnerability.

#### **17. Code must be transferred from the development environment to the testing team. To ensure that the testing team receives the exact binary built by the authorized compiler without any tampering during transit, the build pipeline must implement which anti-tampering technique?**
A. Obfuscation
B. Code Signing (Digital Signatures/Hashes)
C. Address Space Layout Randomization (ASLR)
D. Watchdog Timers

*   **Answer: B**
*   **Rationale:** Applying a Digital Signature (**Code Signing**) to the resultant binary via a trusted private key guarantees the integrity and provenance of the artifact. Testing and production environments can use the corresponding public key to verify that the binary was not tampered with post-build.
