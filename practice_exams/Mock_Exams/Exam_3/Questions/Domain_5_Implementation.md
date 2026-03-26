# Exam 3
## Domain 5: Secure Software Implementation (18 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A developer is writing code to authenticate users against a backend database. The developer constructs the query dynamically by concatenating the user's input directly into the SQL string like this: `query = "SELECT * FROM users WHERE username = '" + user_input + "' AND password = '" + pass_input + "'"`. To definitively eliminate the risk of a hacker injecting maliciousSQL commands (SQL Injection) via `user_input`, which specific coding technique MUST the developer implement instead of string concatenation?**
A. Encode the user input using Base64 before concatenation.
B. Implement client-side JavaScript validation to block single quotes.
C. Utilize Parameterized Queries (Prepared Statements) provided by the database driver.
D. Hash the SQL query before sending it to the database.

#### **2. While reviewing the source code of a C++ application, a security auditor notices that the programmer is using the `strcpy()` function to copy user-supplied input into a fixed-size character array (buffer) of 128 bytes, without checking if the input actually exceeds 128 bytes. This classic coding error directly exposes the application to which critical vulnerability that could lead to remote code execution?**
A. Cross-Site Scripting (XSS)
B. Buffer Overflow (Stack/Heap Overflow)
C. Cross-Site Request Forgery (CSRF)
D. XML External Entity (XXE) Injection

#### **3. A web application displays a personalized greeting using the user's profile name, which they previously entered into a text field. The backend PHP code simply reads the name from the database and directly echoes it into the HTML page: `<h1>Welcome, <?php echo $profile_name; ?></h1>`. If a malicious user entered `<script>alert('Stealing cookies!')</script>` as their profile name, this code would execute in every other user's browser who views their profile. What is the fundamental, mandatory defensive implementation required to neutralize this vulnerability?**
A. Encrypt the profile name in the database using AES-256.
B. Implement an IPSec VPN for all users.
C. Apply strict Context-Aware Output Encoding (e.g., HTML Entity Encoding) before rendering the data in the browser.
D. Change the database to a NoSQL database system.

#### **4. A massive data breach investigation reveals that hackers compromised a company's AWS cloud infrastructure. The root cause was traced back to a junior developer who accidentally committed a file named `config.json` into the public, open-source GitHub repository. This file contained the live, production AWS Access Key ID and Secret Access Key. Which secure implementation practice completely prevents this catastrophic scenario?**
A. Using a Software Composition Analysis (SCA) tool on the Git repository.
B. Externalizing secrets and managing them via a secure Secrets Management Vault (e.g., HashiCorp Vault, AWS Secrets Manager, Azure Key Vault) injecting them as environment variables at runtime, keeping them entirely out of the source code.
C. Hashing the AWS keys using SHA-256 before putting them in the `config.json` file.
D. Relying on "Security through Obscurity" by naming the file something else.

#### **5. A development team is adding a new "Forgot Password" feature. The initial code generates a random 4-digit PIN using the standard language library: `Random.Next(1000, 9999)` and emails it to the user as a temporary reset token. A security reviewer immediately rejects this code. Why is using standard `.Next()` or `rand()` functions a critical security vulnerability when generating security tokens or cryptographic keys?**
A. Standard random number generators are Pseudorandom Number Generators (PRNGs) and are mathematically predictable. The developer MUST use a Cryptographically Secure Pseudorandom Number Generator (CSPRNG) instead.
B. A 4-digit PIN is too long; it should be 2 digits for better usability.
C. The function takes too much CPU processing time, leading to Denial of Service (DoS).
D. Random numbers cannot be emailed securely over SMTP.

#### **6. A prominent financial application allows users to download monthly PDF statements. The URL looks like this: `https://bank.com/download?statement_id=8845`. An attacker, logged in as "User A", manually changes the URL to `statement_id=8846` (which belongs to "User B") and the application successfully delivers User B's highly confidential statement to the attacker. Which pervasive Access Control vulnerability, categorized in the OWASP Top 10, does this implementation suffer from?**
A. Security Misconfiguration
B. Insecure Direct Object Reference (IDOR) / Broken Access Control
C. Server-Side Request Forgery (SSRF)
D. Insecure Deserialization

#### **7. A developer is writing the core logic for a user registration portal. They need to securely store the user's password in the database. They decide to use the extremely fast MD5 hashing algorithm to hash the password before saving it. What are the two massive, critical flaws with this specific implementation?**
A. MD5 is a symmetric encryption algorithm, and it requires a public key.
B. MD5 is an outdated, cryptographically broken algorithm susceptible to collision and rapid brute-forcing. Furthermore, the developer failed to use a unique "Salt" (Salting) to prevent Rainbow Table attacks.
C. MD5 is too slow, and it will cause the database to crash.
D. MD5 cannot store passwords longer than 8 characters, and it is illegal under GDPR.

#### **8. A Java web application accepts serialized Java objects from an external, untrusted API endpoint to process complex data structures natively. The application immediately calls the `readObject()` function to deserialize the stream back into operational memory without performing any structural validation or type checking on the incoming bytecode. If an attacker crafts a malicious serialized payload containing arbitrary execution commands, what devastating vulnerability is triggered?**
A. Cross-Site Scripting (XSS)
B. Insecure Deserialization (leading to Remote Code Execution - RCE)
C. SQL Injection
D. Man-in-the-Middle (MitM) Attack

#### **9. During a code review, an architect notices that an API endpoint designed to update a user's `email_address` also blindly accepts and processes ANY other JSON key-value pairs submitted in the HTTP POST request. By simply adding `"is_admin": true` to the JSON payload, an ordinary user can trick the backend object-relational mapper (ORM) into instantly elevating their privileges in the database. What specific security implementation flaw is this?**
A. Mass Assignment (aka Overposting / Auto-Binding vulnerability)
B. Buffer Overflow
C. Cross-Site Request Forgery (CSRF)
D. XML External Entity (XXE)

#### **10. An application relies heavily on third-party, open-source libraries (e.g., npm packages, Python PIP modules) to accelerate development. The security team realizes they have absolutely no visibility into the thousands of transitive dependencies these libraries drag into their final build, and whether any of those hidden libraries contain known, documented CVE vulnerabilities (like the Log4j disaster). What specific category of automated DevSecOps tooling must be implemented in the CI/CD pipeline to analyze the `package.json` and flag vulnerable third-party components?**
A. Static Application Security Testing (SAST)
B. Dynamic Application Security Testing (DAST)
C. Software Composition Analysis (SCA)
D. Interactive Application Security Testing (IAST)

#### **11. A developer implements a global exception handling block (a `try-catch` statement) around the main database execution module. When a database error occurs, the code logs the error and displays the following raw message directly to the end-user's web browser: `Error 500: Database connection failed. ODBC Driver 17 for SQL Server on Server 10.0.1.55. Table 'Customers' column 'credit_card' not found in statement 'SELECT credit_card FROM Customers'.` Why is this specific error handling implementation extremely dangerous?**
A. Error 500 automatically encrypts the database.
B. It implements "Fail Open," which shuts down the server.
C. It constitutes severe Information Disclosure. Displaying verbose, detailed technical stack traces and internal architecture details to the end-user provides a perfect blueprint for an attacker to launch targeted exploits.
D. `try-catch` blocks are deprecated in modern programming languages.

#### **12. A web application features a "Contact Us" form where users can submit feedback. To prevent automated botnets from spamming the database with millions of fake submissions, the developer implements a completely hidden HTML field `<input type="hidden" name="is_bot" value="false">`. The backend server only processes the form if `is_bot` remains "false". Why is this anti-automation implementation completely ineffective against an actual attacker?**
A. Hidden fields cannot hold boolean values like "false".
B. It relies on Client-Side Controls. An attacker using a proxy (like Burp Suite) or a simple script can effortlessly view, bypass, and manipulate anything sent from the client-side browser, rendering the hidden field useless.
C. The database will reject the "hidden" attribute.
D. The developer should have used `<input type="password">` instead.

#### **13. A C development team is rewriting a legacy application. The security architect strictly bans the use of "dangerous" legacy functions such as `gets()`, `sprintf()`, and `strcat()`. What is the primary, overarching reason for permanently banning these specific standard C library functions in modern secure coding?**
A. They natively lack any capability to define or enforce internal buffer boundary limits, making them inherently and historically the primary cause of catastrophic Buffer Overflow vulnerabilities.
B. They are too slow and cause performance bottlenecks.
C. They require an active internet connection to compile.
D. They automatically execute SQL queries in the background.

#### **14. A highly secure B2B financial portal allows specific enterprise partners to upload XML files containing bulk payment instructions. A security researcher discovers that if they upload a specially crafted XML file containing a `<!ENTITY>` payload pointing to `file:///etc/passwd`, the server's backend XML parser actually reads the local password file from its own hard drive and embeds the contents directly into the API response sent back to the researcher. What specific vulnerability did the researcher exploit?**
A. XML External Entity (XXE) Injection
B. Cross-Site Scripting (XSS)
C. SQL Injection
D. Denial of Service (DoS)

#### **15. When writing code to handle multi-threaded processing in a real-time trading application, two separate execution threads simultaneously attempt to access and modify the exact same shared memory variable representing an account balance, without using any synchronization locks or mutexes. Depending on the exact millisecond timing of which thread finishes last, the final account balance can be incorrectly corrupted. What is the fundamental security engineering term for this specific type of concurrency flaw?**
A. A Logic Bomb
B. A Race Condition (specifically, a Time-of-Check to Time-of-Use [TOCTOU] or concurrency flaw)
C. An Integer Underflow
D. A Buffer Over-read

#### **16. A developer is building a banking website. They want to ensure that if a user logs into their bank account on `Tab A`, and then opens a malicious hacker's website on `Tab B`, the hacker's website cannot secretly trigger a background HTTP POST request to the bank (e.g., `POST /transfer?amount=1000`) that effectively leverages the user's active login cookie to steal money without the user's knowledge. What specific defensive mechanism MUST the developer implement to bind the specific action explicitly to an intentional user click on the legitimate bank page?**
A. Implement an Anti-CSRF (Cross-Site Request Forgery) Token (a unique, unpredictable, synchronizer token) that must be submitted with every state-changing request.
B. Utilize a Web Application Firewall (WAF) to block IP addresses from `Tab B`.
C. Encrypt the user's password using AES-GCM.
D. Require the user to use an Incognito/Private Browsing window.

#### **17. A programmer is calculating the exact exact memory required to store an array of user inputs. They use the following C logic: `short int total_size = user_count * fixed_item_size;`. However, if a malicious user provides an astronomically large number for `user_count`, the multiplication result exceeds the maximum positive value a 16-bit `short int` (32,767) can hold. The value unexpectedly wraps around to a small negative number, causing the system to allocate far too little memory, subsequently leading to a massive buffer overflow when it tries to write the data. What specific type of software vulnerability is this?**
A. Format String Vulnerability
B. Integer Overflow (or Arithmetic Wrap-around)
C. Null Pointer Dereference
D. Cross-Site Scripting (XSS)

#### **18. To adhere to the principle of "Defense in Depth" at the code level, a development team implements severe restrictions on what their application can do if it gets compromised. They configure their Java application server to run under a restricted service account that cannot read any files outside of its specific `/var/www/webapp/` directory, cannot execute shell commands, and cannot open network ports below 1024. Which foundational secure coding concept does this operating environment directly enforce?**
A. Obfuscation
B. Least Privilege (and Sandboxing/Jailing at the execution level)
C. Open Design
D. Economy of Mechanism
