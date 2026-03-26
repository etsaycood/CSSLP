# Exam 1
## Domain 5: Secure Software Implementation (18 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A junior developer is writing a C function to parse incoming network packets. The function allocates a fixed 128-byte array on the stack to hold the packet's payload data. However, he copies the incoming data into this array directly using the `strcpy()` function without first checking the actual length of the incoming data stream. An attacker sends a crafted packet with 500 bytes of payload. At runtime, what catastrophic memory corruption vulnerability will immediately occur when the extra 372 bytes overwrite the frame pointer and the return address?**
A. Race Condition (Time-of-Check to Time-of-Use)
B. Stack-based Buffer Overflow
C. Integer Underflow Memory Allocation
D. Use-After-Free Dereference

#### **2. You are auditing a Java web application that takes an unsanitized "AccountID" string straight from the HTTP GET request URL (e.g., `?id=105`) and blindly concatenates it into a backend database query: `String query = "SELECT * FROM Users WHERE AccountID = " + request.getParameter("id");`. A malicious user changes the URL to `?id=105 OR 1=1; DROP TABLE Users; --`. To mathematically immunize the application against all forms of this devastating injection attack, what specific coding technique MUST the developer implement instead of string concatenation?**
A. Symmetrically encrypt the "AccountID" parameter before appending it to the SQL string.
B. Implement rigorous HTML Entity Encoding on the input to neutralize the angle brackets (`<`, `>`).
C. Replace the raw string concatenation with Strictly Typed Parameterized Queries (PreparedStatement).
D. Enforce a strict Web Application Firewall (WAF) rule to block all IP addresses that type the word "DROP".

#### **3. A development team is rushing to release a PHP e-commerce site. When validating user input on the registration form, the lead developer writes a 200-line regular expression to create a "Blacklist" of bad characters that the system must block (e.g., `<script>`, `'`, `OR`, `SELECT`). A senior security engineer angrily rejects this code during the peer review. Why is relying heavily on Blacklisting (Deny Listing) fundamentally flawed as a secure coding practice, and what should be used instead?**
A. Blacklists are too computationally intensive. They should rely entirely on client-side JavaScript validation instead for better performance.
B. External hackers will always invent a new encoding permutation or payload variation that is not on your static blacklist. Developers should exclusively use a "Whitelist" (Allow List) approach, defining exactly the few characters that are explicitly safe and rejecting everything else.
C. Blacklisting breaks the Open Design principle because it reveals the inner workings to the attacker via error messages.
D. Blacklists are completely incompatible with UTF-8 character encoding standards.

#### **4. A Ruby on Rails application allows users to upload profile pictures. The code securely verifies that the uploaded file has a `.jpg` extension and is less than 5 MB. However, it saves the file directly to the `/var/www/uploads/` directory using the user-provided filename without sanitizing it. A hacker uploads a malicious PHP script and names it `../../../var/www/html/backdoor.php` with a manipulated header. When the application writes the file to the disk, it escapes the intended uploads directory and overwrites the site's main index page. What specific category of vulnerability has the application fallen victim to?**
A. Cross-Site Scripting (XSS)
B. Path Traversal (Directory Traversal)
C. Insecure Direct Object Reference (IDOR)
D. Server-Side Request Forgery (SSRF)

#### **5. In a massive enterprise, two asynchronous, multi-threaded C++ processes (Process A and Process B) share a single boolean variable called `is_payment_verified`. Because both threads failed to lock a critical mutex, they simultaneously read the variable as `false`. Both threads then simultaneously process a $5,000 withdrawal for the exact same transaction, believing they are the first to do so, resulting in a duplicate $5,000 loss for the bank. What is the standard computer science term for this specific concurrency flaw?**
A. Buffer Overflow
B. Time-of-Check to Time-of-Use (TOCTOU) / Race Condition
C. Memory Leak leading to Denial of Service
D. Cryptographic Key Collision

#### **6. A junior programmer writes a login script for an internal dashboard. Because he wants to save time diagnosing issues during development, he creates an error-handling block: `try { connect_to_db(); } catch (Exception e) { print_to_browser("DB Connection failed. Root password 'SuperSecr3t!' was rejected by host 192.168.1.100. Stack Trace: " + e.toString()); }`. When this sloppy error-handling code is accidentally pushed to the live production server, what OWASP Top 10 vulnerability is the programmer explicitly committing?**
A. Security Misconfiguration and Improper Error Handling (Information Leakage).
B. Broken Authentication and Session Management.
C. XML External Entity (XXE) Injection.
D. Cross-Site Request Forgery (CSRF).

#### **7. An outsourced development firm delivers a compiled binary for an Android application to your QA team. Your security analyst runs a static reverse-engineering tool on the `.apk` file and discovers a horrifying function named `def BypassAuth_ForDevsOnly() { return True; }`. The developers claim they used this "hidden feature" to skip endless login screens during local testing, but forgot to remove it before the final compiling phase. What is the industry term for this unforgivable secure coding violation?**
A. Implementing an undocumented Backdoor (often masked as a maintenance hook).
B. A severe Memory Leak condition.
C. Storing plaintext passwords in the SQLite database.
D. Utilizing a weak Random Number Generator (RNG).

#### **8. You are reviewing the session management code of a Node.js web application. Upon a successful login, the server generates a session ID for the user using this specific line of code: `const sessionID = Date.now() + Math.random();`. The security reviewer immediately flags this line as a catastrophic failure. Why is `Math.random()` unacceptable for generating session identifiers, and what should be used instead?**
A. It generates strings that are too long to fit in standard HTTP cookie headers.
B. It is a Pseudo-Random Number Generator (PRNG) that lacks sufficient entropy, meaning its outputs are highly predictable. Instead, the developer MUST strictly substitute it with a Cryptographically Secure Pseudo-Random Number Generator (CSPRNG).
C. `Math.random()` is notoriously slow, causing unacceptable application latency during login spikes.
D. `Math.random()` only generates positive numbers, which violates the OAuth 2.0 specification for token format.

#### **9. An application calculates the total price of items in a shopping cart using a standard 32-bit signed integer. A hacker with malicious intent purposefully adds 2.5 billion dollars' worth of luxury items to their cart. Because the total value far exceeds the maximum positive limit of a 32-bit signed integer (`2,147,483,647`), the binary math wraps around to a massive negative number (e.g., `-1.7 billion`). The system views the negative total and credits the hacker's account instead of charging them. What kind of devastating mathematical implementation flaw is this?**
A. Integer Overflow (Integer Wrap-around)
B. Buffer Overflow Memory Corruption
C. Time-of-Check to Time-of-Use (TOCTOU) vulnerability
D. Unvalidated Redirect and Forward flaw

#### **10. An architect is reviewing code that establishes a TLS connection to an external payment processor. The developers wrote a custom certificate validation routine because they thought the built-in library was too slow. Their code looks like this: `if (cert.getExpirationDate() > Date.now()) { return true; }`. This extremely lazy custom routine completely ignores checking whether the certificate was actually signed by a trusted internal CA or checking the Certificate Revocation List (CRL). What kind of implementation vulnerability is introduced when developers improperly write custom security controls instead of relying on heavily vetted, standard libraries?**
A. Cryptographic Agility failure leading to lock-in.
B. "Rolling your own Crypto/Security Mechanism" leading to severe implementation flaws, such as the total bypass of trust chains in this scenario.
C. Cross-Site Scripting (XSS) due to unescaped certificate fields.
D. Elevation of Privilege due to poor access controls.

#### **11. A developer is designing a feature that allows users to download their monthly billing statements. The URL generated looks like this: `https://bank.com/download_pdf?statement_id=1055`. The backend code takes the `statement_id`, queries the database for that file, and returns it to the user. A mischievous customer changes the URL parameter in their browser to `statement_id=1056`. The system blindly returns another customer's highly confidential financial statement because it never explicitly checked if the currently logged-in user actually *owned* document 1056. What classic OWASP API vulnerability is the system fundamentally suffering from?**
A. Unrestricted File Uploads (UFU).
B. Broken Object Level Authorization (BOLA), historically known as Insecure Direct Object Reference (IDOR).
C. Server-Side Request Forgery (SSRF).
D. Security Misconfiguration.

#### **12. The QA team runs a dynamic Application Security Testing (DAST) scanner against a newly written Java component. The scanner's final report screams: "Catastrophic Memory Issue Detected! The application allocates memory dynamically using `new()` for every incoming HTTP request, but completely lacks any corresponding `delete()` or garbage collection mechanisms when the objects fall out of scope. After 4 hours of heavy load traffic, the server crashed due to 100% RAM exhaustion." What is the technical term for this implementation error that leads to a Denial of Service?**
A. Memory Leak (Resource Exhaustion)
B. Use-After-Free Dereference
C. SQL Injection
D. Buffer Overflow

#### **13. When implementing a sensitive web application that handles healthcare data, the development team is forced to sanitize vast amounts of user-generated content (names, addresses, medical conditions) before displaying it back onto the web page to prevent Cross-Site Scripting (XSS). To mathematically ensure that the browser never accidentally executes user input as script code, what is the absolute MUST-HAVE, final defense implementation step before the data hits the HTML DOM?**
A. Encrypting the data with AES-256 before printing it to the screen.
B. Strict Context-Aware Output Encoding (HTML Entity Encoding) to safely neutralize special characters like `<` into `&lt;`.
C. Removing all vowels from the text to break any hidden JavaScript.
D. Using Client-Side JavaScript RegEx to delete the word `<script>` from the browser memory.

#### **14. A team is refactoring a legacy C application. The original code is littered with dangerous functions like `gets()`, `strcpy()`, and `sprintf()`, which do not inherently check the length of strings and memory boundaries, notoriously causing Buffer Overflows. As a secure coding fundamental, the team's first overarching mandate is to execute a massive "Search and Replace" across the codebase to swap these dangerous functions with their "safer, bounds-checking equivalents." Which of the following functions represents a safer alternative?**
A. Replace `gets()` with `scanf()`.
B. Replace `strcpy()` with `memcpy()`.
C. Replace `strcpy()` and `sprintf()` with `strncpy()` and `snprintf()`, which explicitly force the programmer to declare maximum buffer size limits.
D. Replace `strcpy()` with `strcat()`.

#### **15. You are inspecting the configuration files (`appsettings.json`) of an enterprise .NET application stored in a public GitHub repository. You are horrified to find the following line written in plain text: `"DatabaseConnectionString": "Server=tcp:prod.database.windows.net;Database=HR_Records;User ID=sa;Password=SuperSecretAdminPassword123;"`. This is a massive violation of secure implementation principles. What is the standard, enterprise-grade architecture pattern to eliminate the presence of hardcoded secrets in source code?**
A. Hash the connection string using SHA-256 so humans cannot read it.
B. Replace the connection string with an API key generated by the developers.
C. Utterly remove all credentials from the codebase and configure the application to dynamically fetch the required credentials at runtime from a secure, centralized Secrets Management Vault (e.g., Azure Key Vault, HashiCorp Vault, AWS Secrets Manager).
D. Store the connection string in a slightly obscured text file called `config.txt` and place it three directory levels deep.

#### **16. A developer writes a web scraper in Python to pull images from a user-supplied URL. The code looks like this: `response = requests.get(user_supplied_input_url_parameter)`. A malicious user realizes the server is blindly trusting their input. Instead of giving it a picture URL like `http://example.com/pic.jpg`, they input the internal, non-routable IP address of the company's private accounting server: `http://192.168.1.50/admin-panel`. The web scraper server obeys the command, reaches into the private internal network, fetches the highly confidential internal dashboard, and serves it back to the hacker on the public internet. What specific vulnerability did the Python code introduce?**
A. Cross-Site Scripting (XSS)
B. Server-Side Request Forgery (SSRF)
C. Command Injection (OS Injection)
D. XML External Entity (XXE) Injection

#### **17. When writing secure C/C++ code, a developer allocates a chunk of memory using a pointer. Later in the code, the developer correctly calls `free(pointer)` to release the memory back to the operating system. However, due to sloppy logic, much further down in the 2,000-line function, the developer's code attempts to write new data into that *exact same memory location* via the old, dangling pointer. This causes arbitrary code execution or a massive crash. What is the formal name for this horrifying memory corruption vulnerability?**
A. Memory Leak
B. Use-After-Free (UAF) Dereferencing
C. Stack Integer Underflow
D. Race Condition (TOCTOU)

#### **18. A developer is tasked with encrypting highly sensitive credit card numbers in the database. They find a tutorial online from 2005 and decide to implement the Electronic Codebook (ECB) mode of operation: `cipher = AES.new(key, AES.MODE_ECB)`. A senior cryptographer catches this during a code review and demands an immediate rewrite. Why is AES-ECB considered a critically flawed implementation for encrypting data larger than one block, and what should be used instead?**
A. AES-ECB is far too slow and consumes too much CPU power. They should use 3DES instead.
B. ECB mode deterministic. It encrypts identical plaintext blocks (like repeating image pixels or repeating strings of zeros) into identical ciphertext blocks, leaving obvious visual and mathematical patterns in the encrypted data that attackers can decipher. The developer MUST switch to a secure, randomized mode like Cipher Block Chaining (CBC) or Galois/Counter Mode (GCM).
C. ECB mode requires sending the decryption key in plaintext alongside the ciphertext over the network.
D. ECB does not use symmetric keys; it relies entirely on public-key infrastructure which is fundamentally inappropriate for database storage.
