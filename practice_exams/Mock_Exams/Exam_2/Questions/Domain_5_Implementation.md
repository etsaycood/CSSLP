# Exam 2
## Domain 5: Secure Software Implementation (18 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A junior developer asks the security engineering team how to permanently and mathematically eliminate the threat of SQL Injection vulnerabilities when building dynamic database search queries. What is the absolute MOST effective secure coding mechanism the team should mandate?**
A. Manually filtering out characters like `'` and `OR 1=1` using a custom Regex function.
B. Using Parameterized Queries (Prepared Statements) provided by the database driver.
C. Encrypting the entire database column with AES-256.
D. Using Client-Side JavaScript validation before sending the query.

#### **2. During a source code review of a modern frontend React application, the security engineer finds that user comments pulled from the database are being rendered to the DOM using the function `dangerouslySetInnerHTML`. What critical secure coding practice must the frontend developers implement to prevent catastrophic Cross-Site Scripting (XSS) here?**
A. Rate Limiting
B. Input Sanitization on the backend only.
C. Context-aware Output Encoding (escaping the data before it is rendered into the HTML).
D. Enabling Cross-Origin Resource Sharing (CORS).

#### **3. A legacy C/C++ application has a long history of unexpectedly crashing when malicious users input excessively long strings into the username field. A penetration tester recently proved they could carefully craft an incredibly long string to overflow the memory boundaries and overwrite the system's instruction pointer, achieving a remote shell. What is the fundamental root cause of this vulnerability, and how MUST the developer fix it at the code level?**
A. SQL Injection. Fix: Use Prepared Statements.
B. Buffer Overflow. Fix: Replace historically unsafe, unbounded memory functions (like `strcpy()` or `gets()`) with bounds-checking functions (like `strncpy()` or `fgets()`).
C. Missing Encryption. Fix: Hash the input string using SHA-256.
D. TOCTOU. Fix: Implement file locking.

#### **4. A multi-threaded, high-frequency banking application occasionally allows a user with an exact balance of `$100` to successfully submit and execute two separate `$100` withdrawal requests, resulting in the bank incorrectly handing out `$200`. The logs show both requests hit the server's checking logic at the exact same millisecond before the database could subtract the first `$100`. What specific concurrency implementation flaw is this, and how can it be fixed?**
A. Integer Overflow; Fix by using 64-bit integers.
B. Race Condition (Time-of-Check to Time-of-Use); Fix by implementing atomic database transactions or strict thread/row locking mechanisms.
C. Buffer Overflow; Fix by using a memory-safe language like Java.
D. Cross-Site Request Forgery; Fix by adding an Anti-CSRF token.

#### **5. A developer wants to ensure that whenever the application fails to connect to the backend database, the debugging process is as fast as possible. They configure the production server's global error handler to print out the raw, unhandled Java Exceptions and full, verbose stack traces directly onto the user's web browser screen. Why is this considered a severe implementation failure?**
A. Stack traces run extremely slowly and will cause a Denial of Service.
B. It violates Information Hiding principles by exposing highly sensitive internal infrastructure details (like database versions, file paths, and SQL query structures) to potential attackers.
C. It will cause the browser's JavaScript engine to crash.
D. Stack traces take up too much bandwidth on mobile networks.

#### **6. A hacker creates a malicious, entirely separate website containing a hidden JavaScript form. When a victim visits the hacker's site, the hidden script automatically submits a "Transfer $1,000 to Hacker" request in the background toward the victim's banking website. Because the victim is already logged into the bank in another tab, the victim's browser automatically attaches their valid Session Cookie, and the bank executes the transfer. What specific implementation defense is missing from the bank's HTTP forms?**
A. Anti-CSRF (Cross-Site Request Forgery) Synchronizer Tokens.
B. HTTPS (TLS 1.3) encryption.
C. Parameterized Queries.
D. Output Encoding.

#### **7. A developer needs the application backend to automatically authenticate to an external cloud database upon startup. To ensure the code builds seamlessly on all developer laptops without complex configuration, they copy and paste the production database password directly inside the `config.java` source code file and commit it to the Git repository. What fundamental secure coding practice is violated, and what is the proper solution?**
A. Violates Principle of Least Privilege. Solution: Make the database public.
B. Violates Open Design. Solution: Encrypt the Java file.
C. Violates Hardcoding Secrets. Solution: Remove the password from the source code entirely and dynamically retrieve it at runtime via Environment Variables or a centralized Secrets Manager (Vault).
D. Violates Data Minimization. Solution: Delete the database.

#### **8. A popular multiplayer game application stores the player's total cumulative gold as a signed 16-bit integer (which has a maximum positive value of 32,767). A clever hacker discovers that if they aggressively grind exactly 32,768 gold pieces, the computer's memory wraps around, the balance suddenly reads `-32,768`, and the game economy instantly breaks. What specific mathematical vulnerability was implemented, and what is the fix?**
A. Buffer Overflow; Fix by adding memory randomization (ASLR).
B. Floating Point Error; Fix by rounding to two decimal places.
C. Integer Overflow/Underflow; Fix by implementing strict mathematical bounds checking before performing arithmetic operations, or replacing the variable with a larger data type capable of holding the value.
D. Cross-Site Scripting; Fix by HTML encoding the gold value.

#### **9. A Java web application receives a Base64 encoded, serialized payload from the client's HTTP cookie, decodes it, and passes it directly into the `ObjectInputStream.readObject()` function to seamlessly reconstruct the user's profile object in memory. During a routine pentest, the server is suddenly taken over via a devastating Remote Code Execution (RCE) attack originating from that cookie. What vulnerable implementation pattern was explicitly used?**
A. Server-Side Request Forgery (SSRF)
B. Insecure Deserialization of entirely untrusted data without prior strict schema validation.
C. SQL Injection
D. Man-in-the-Middle (MitM)

#### **10. An implementation developer needs to generate a highly unpredictable 128-bit session token string to assign to a user upon a successful login. They quickly write code to generate the token using the standard `Math.random()` function library provided out-of-the-box by the programming language. Why will the security architecture team immediately reject this code during review?**
A. It generates tokens that are too long to fit in a cookie.
B. Standard random math functions are statistically predictable (Pseudo-Random) and mathematically vulnerable to sequencing attacks. The developer MUST explicitly use a Cryptographically Secure Pseudo-Random Number Generator (CSPRNG) like `/dev/urandom` or `java.security.SecureRandom`.
C. It relies on Open Design, which hackers can view.
D. `Math.random()` only generates letters, not numbers.

#### **11. An application allows users to download their monthly PDF invoices by clicking a link that passes the filename in the URL exactly like this: `https://bank.com/download.php?file=invoice_jan.pdf`. A hacker manually changes the URL to `?file=../../../../etc/passwd` and successfully downloads the underlying Linux server's highly sensitive password configuration file. What is the missing secure implementation control?**
A. Missing Authentication. Mitigation: Add a login page.
B. Failure to validate and constrain path input (Directory Traversal / Path Traversal). Mitigation: Aggressively strip path manipulation characters (like `../`) and forcibly map the input string to an internal static Allowlist, refusing to ever pass raw user input directly to the operating system's filesystem APIs.
C. SQL Injection. Mitigation: Use Prepared Statements.
D. Broken Cryptography. Mitigation: Encrypt the PDF files.

#### **12. A mobile application makes the following API call to fetch the current user's profile data: `GET /API/v1/user/account_details?id=505`. User `505` legally logs in, observes the API call in their proxy, manually changes the ID in the URL parameter from `505` to `506`, and successfully views the extremely private medical data of user `506`. What specific API authorization implementation entirely failed?**
A. Insecure Direct Object Reference (IDOR) / Broken Object Level Authorization (BOLA). The API merely checked if the user was logged in, but failed to assert if the logged-in user actually possessed ownership rights to the specific object (ID=506) being requested.
B. Lack of TLS encryption on the API endpoint.
C. Cross-Site Scripting (XSS).
D. Buffer Overflow.

#### **13. A modern Node.js web application is built entirely upon an ecosystem of 400 different open-source NPM packages imported from the internet. The internal developers meticulously write perfect, flawless secure code for their own proprietary logic. Yet, the application is still catastrophically compromised because one of the imported NPM packages contained a hidden, community-injected malicious backdoor. What SDLC implementation process failed?**
A. Penetration Testing was not performed aggressively enough.
B. Software Composition Analysis (SCA) / Dependency Management. The team failed to rigorously scan, audit, and mathematically pin the versions of their third-party supply chain libraries to detect known compromises.
C. The developers should not have used Node.js.
D. Threat Modeling was skipped.

#### **14. To make creating shareable bookmarks easier for users, a frontend developer implements a login flow that intentionally submits the user's username and password via an HTTP GET request, resulting in a visible URL parameter string like `https://portal.com/login?user=admin&pass=secret123`. Why is this considered a catastrophic and amateur implementation error?**
A. GET requests are strictly limited to 10 characters.
B. Passwords sent in the URL string of a GET request are permanently recorded in plaintext across browser histories, upstream corporate proxy logs, and the receiving web server's access logs, massively exposing the credentials. Credentials must ALWAYS be sent hidden within the POST body.
C. GET requests cannot be encrypted by HTTPS.
D. It violates the SQL Injection parameters.

#### **15. A backend database engineer is explicitly tasked with securely storing new user passwords. Because the system is highly latency-sensitive, they decide to run all incoming passwords through the extremely fast, highly optimized `SHA-256` hashing algorithm before writing them to disk. Why is this implementation choice considered radically insecure by modern cryptographic standards?**
A. Hash functions can be reversed instantly using Base64 decoding.
B. Fast, single-iteration hashing algorithms (like pure SHA-256 or MD5) are massively vulnerable to modern brute-force, GPU-accelerated offline cracking. The engineer MUST implement an intentionally slow, CPU/Memory-hard "Key-Stretching" or "Work Factor" algorithm like Argon2, bcrypt, or PBKDF2 alongside a unique salt.
C. SHA-256 is owned by the NSA and contains a backdoor.
D. Passwords should be stored in plaintext to prevent data corruption.

#### **16. A B2B inventory application frequently processes vendor manifests uploaded as standard XML files. A clever attacker uploads a highly crafted XML file containing a malicious `<!ENTITY>` payload instruction that explicitly commands the receiving server to quietly read its local `/etc/shadow` file and echo the contents back out in the XML response. To definitively stop this XML External Entity (XXE) attack, what single secure configuration must the developer apply to the XML Parser?**
A. Delete all XML files after processing them.
B. Force the XML parser to run via HTTPS only.
C. Completely and totally disable the resolution of Document Type Definitions (DTDs) and External Entities within the XML parsing engine's configuration.
D. Encode the XML as JSON before reading it.

#### **17. A malicious scam website quietly loads a legitimate, fully functional banking portal inside a completely invisible, transparent `<iframe>`. The malicious site places a fake HTML button titled "Click Here to Win an iPhone!" exactly hovering over where the invisible bank's real "Confirm Wire Transfer of $10,000" button sits. When the greedy user vigorously clicks to win the phone, their mouse physically clicks the hidden bank's button instead, executing the transfer. What HTTP Response Header MUST the banking application implement to prevent its site from being hijacked in this manner?**
A. `Strict-Transport-Security: max-age=31536000`
B. `Cache-Control: no-cache`
C. `X-Frame-Options: DENY` (or the modern Content Security Policy `frame-ancestors` directive).
D. `Access-Control-Allow-Origin: *`

#### **18. A modern web application features a dynamic tool where a user can provide a URL, and the server backend will proactively reach out, fetch the image from that URL, and securely crop it to display as their profile picture. An attacker realizes this, and instead of an image URL, they provide the string `http://169.254.169.254/latest/meta-data/`. The backend server blindly reaches out to this internal IP address and successfully fetches and returns the AWS cloud server's highly privileged, secret IAM temporary execution keys back to the attacker's screen. What specific implementation vulnerability was exploited here?**
A. Server-Side Request Forgery (SSRF)
B. Client-Side Request Forgery (CSRF)
C. Cross-Site Scripting (XSS)
D. XML External Entity (XXE)
