# Exam 4
## Domain 5: Secure Software Implementation (18 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A developer is writing a C function that copies a user-supplied string into a fixed-size local character array using the `strcpy()` function. Which of the following vulnerabilities is the developer explicitly introducing into the application?**
A. Cross-Site Scripting (XSS)
B. Buffer Overflow
C. SQL Injection
D. Integer Underflow

#### **2. You are reviewing the source code of a web application built in PHP. You encounter the following line of code used to execute a system command: `exec("ping -c 4 " . $_GET['target_ip']);`. What is the MOST effective secure coding practice to remediate this specific vulnerability?**
A. Use a regular expression to strip out all non-alphanumeric characters from the `target_ip` variable.
B. Avoid passing user input directly to the operating system shell altogether; instead, use safe, built-in language APIs (e.g., a specific DNS or ICMP library) if possible.
C. Encrypt the `target_ip` variable before passing it to the `exec()` function.
D. Append a null byte (`%00`) to the end of the `target_ip` variable.

#### **3. A Java developer needs to store a highly sensitive API key in the application's source code for a temporary proof-of-concept (PoC) demonstration. They intend to remove it before pushing the code to the central Git repository. What is the fundamental security principle being violated, even for a temporary PoC?**
A. Principle of Least Privilege
B. Separation of Duties
C. Never hardcode credentials or secrets directly into source code, as they can easily be committed to version control or extracted from compiled binaries.
D. Perfect Forward Secrecy

#### **4. In modern web development (e.g., using React, Angular, or Vue.js), which built-in framework feature serves as the primary defense mechanism against Cross-Site Scripting (XSS) by automatically treating user-provided data as text rather than executable HTML/JavaScript?**
A. Automatic Parameterization
B. Context-Aware Output Encoding (Auto-Escaping)
C. Cross-Origin Resource Sharing (CORS) enforcement
D. Content Security Policy (CSP) report generation

#### **5. A developer is implementing an "Update Profile" feature where users can change their own email address. The backend API endpoint is `PUT /api/users/{id}/email`. The developer writes the code to read the `{id}` from the URL and update the corresponding record without checking if the currently logged-in user's session token actually matches that `{id}`. Which vulnerability has been introduced?**
A. Cross-Site Request Forgery (CSRF)
B. Insecure Direct Object Reference (IDOR) / Broken Object Level Authorization (BOLA)
C. Session Fixation
D. Directory Traversal

#### **6. When generating cryptographically secure random values (such as session IDs, password reset tokens, or initialization vectors), which type of random number generator MUST a developer use to prevent attackers from predicting the next value?**
A. A Pseudorandom Number Generator (PRNG) initialized with the current system time (e.g., `java.util.Random`).
B. A hardware-based True Random Number Generator (TRNG) only.
C. A Cryptographically Secure Pseudorandom Number Generator (CSPRNG) (e.g., `/dev/urandom` or `java.security.SecureRandom`).
D. A Linear Congruential Generator (LCG).

#### **7. A developer is tasked with encrypting the network traffic between two internal microservices. They decide to use a custom XOR-based cipher they learned about in a university assignment because it is extremely fast and lightweight. This directly violates which established cryptographic implementation rule?**
A. Never reuse Initialization Vectors (IVs).
B. Use asymmetric encryption for bulk data.
C. Do not "Roll Your Own Crypto" (adhere to Kerckhoffs's Principle by using vetted algorithms like AES).
D. Passwords must be hashed, not encrypted.

#### **8. Which HTTP response header provides a robust, defense-in-depth mechanism against Cross-Site Scripting (XSS) and data injection attacks by allowing the application to explicitly declare to the browser which dynamic resources (e.g., JavaScript, CSS, Images) are permitted to load and execute?**
A. X-Frame-Options
B. HTTP Strict Transport Security (HSTS)
C. Content Security Policy (CSP)
D. Access-Control-Allow-Origin

#### **9. A senior developer is performing a code review on a junior developer's pull request. The junior developer has implemented a custom error handling routine that catches database connection exceptions and displays the detailed stack trace and SQL query syntax directly on the user's web page so that "users can report exactly what went wrong." What security issue does this represent?**
A. It fails to implement input validation.
B. It causes a Denial of Service.
C. It results in sensitive Information Disclosure (Information Leakage) which aids attackers in mapping the backend infrastructure.
D. It violates the Rule of Least Astonishment.

#### **10. When implementing session management for a web application, a developer sets the session cookie upon successful login. To ensure the cookie is protected against interception via JavaScript (XSS) and network sniffing, which two essential cookie attributes MUST the developer configure?**
A. `Secure` and `HttpOnly`
B. `Domain` and `Path`
C. `Expires` and `Max-Age`
D. `SameSite` and `HostOnly`

#### **11. A developer is writing a file upload mechanism that allows users to submit PDF receipts. To prevent malicious users from uploading executable web shells (e.g., `.php` or `.jsp` files) and compromising the server, which of the following is the MOST secure implementation strategy?**
A. Use a black-list to reject files ending in `.php`, `.exe`, or `.sh`.
B. Rely solely on checking the `Content-Type` header sent by the user's browser (e.g., `application/pdf`).
C. Implement a strict white-list of allowed extensions (e.g., ONLY `.pdf`), verify the file's "magic bytes" (file signature) matches a PDF, and store the uploaded files outside the web root directory or in an isolated object storage bucket (e.g., AWS S3).
D. Scan the uploaded file with an antivirus signature database.

#### **12. In the context of secure software implementation, what is the primary purpose of a "Static Application Security Testing" (SAST) tool integrated into the developer's Integrated Development Environment (IDE)?**
A. To automatically deploy the code to a staging server.
B. To perform automated functional UI testing simulating a user clicking buttons in a browser.
C. To analyze the source code for known security vulnerabilities (e.g., hardcoded secrets, SQL injection patterns) at the exact moment the developer is writing the code, enabling real-time feedback and "Shift-Left" security.
D. To monitor the application's memory usage in the production environment.

#### **13. A C++ developer uses the `new` operator to allocate memory dynamically on the heap for a temporary object. However, in one specific error-handling code path, the function returns early without calling the corresponding `delete` operator to free the memory. Which vulnerability is created by this implementation error?**
A. A Use-After-Free (UAF) vulnerability.
B. A Memory Leak, which can lead to resource exhaustion and a Denial of Service (DoS).
C. An Out-of-Bounds Write.
D. An Integer Overflow.

#### **14. To prevent Cross-Site Request Forgery (CSRF) attacks, a developer implements a mechanism where the server generates a unique, cryptographically strong, and unpredictable random token for each user session. This token is embedded as a hidden field in all HTML forms. Upon form submission, the server verifies that the submitted token matches the token stored in the user's session. What is this standard CSRF defense called?**
A. Double Submit Cookies
B. The Synchronizer Token Pattern (Anti-CSRF Tokens)
C. SameSite Cookie Attribute (Strict)
D. Cross-Origin Resource Sharing (CORS)

#### **15. A developer is tasked with logging user login attempts. The implementation writes the username parameter directly to a log file: `logger.info("Failed login attempt for user: " + request.getParameter("username"));`. If an attacker submits a username containing newline characters (`\n` or `\r\n`) followed by fake log entries, what class of injection vulnerability has the developer introduced?**
A. Command Injection
B. Log Forging (Log Injection / CRLF Injection)
C. LDAP Injection
D. XML External Entity (XXE) Injection

#### **16. When processing XML files uploaded by a user, a developer uses a standard XML parser without configuring any specific security settings. What high-risk vulnerability is the application likely susceptible to, allowing an attacker to read local files on the server or conduct a Server-Side Request Forgery (SSRF) attack?**
A. Malicious File Execution
B. XML External Entity (XXE) Processing
C. Insecure Deserialization
D. Broken Authentication

#### **17. A team is building a REST API in Node.js. They need to protect the API from brute-force password guessing attacks and volumetric Denial of Service (DoS) attempts against the `/login` endpoint. What is the standard implementation-level defense they should configure in the API gateway or application framework?**
A. Mutual Authentication (mTLS)
B. Output Encoding
C. Rate Limiting (Throttling) based on IP address or User ID.
D. Database Sharding

#### **18. A developer uses a third-party open-source library to parse JSON data. Three months later, a Critical CVE (CVSS 9.8) is announced for that specific version of the library, revealing a Remote Code Execution (RCE) flaw. Which secure implementation practice must the team have in place to quickly identify and remediate this risk?**
A. A Web Application Firewall (WAF) blocking all JSON payloads.
B. A robust Software Composition Analysis (SCA) tool or Dependency Checker integrated into the CI/CD pipeline to continuously continuously monitor for known vulnerabilities in third-party components.
C. A mandate to rewrite all open-source libraries in-house.
D. A weekly manual code review of the entire library's source code.
