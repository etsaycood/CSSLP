# Exam 2
## Domain 8: Secure Software Supply Chain (12 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A highly publicized cyberattack occurs where nation-state hackers successfully breach a massively popular network monitoring software vendor. The hackers seamlessly inject a stealthy, cryptographically signed malicious backdoor directly into the vendor's official software update distribution servers. Consequently, 18,000 enterprise customers, blindly trusting the vendor, automatically download and install the poisoned update, resulting in a global catastrophe. What specific type of attack represents this targeted manipulation of a trusted vendor's delivery mechanism?**
A. Denial of Service (DoS) Attack
B. Phishing Attack
C. Supply Chain Attack
D. Cross-Site Scripting (XSS)

#### **2. To combat the rising threat of compromised open-source libraries, the United States Federal Government issues a strict cybersecurity executive order. It mandates that any software vendor selling digital products to federal agencies MUST provide a comprehensive, formally structured inventory document detailing every single third-party library, open-source component, and version number embedded within their application. What is the standard industry acronym for this required "ingredients list" document?**
A. SLA (Service Level Agreement)
B. NDA (Non-Disclosure Agreement)
C. SBOM (Software Bill of Materials)
D. SAST (Static Application Security Testing) Report

#### **3. A development team imports a widely used, free open-source NPM package to handle image resizing in their proprietary web application. Six months later, the original maintainer of the NPM package burns out and transfers ownership to an unknown developer on the internet. The new owner quietly publishes a minor update that includes a hidden script designed to silently steal cryptocurrency wallet keys from anyone running the package. What specific underlying supply chain risk does this scenario highlight?**
A. Zero-Day Browser Vulnerability
B. Dependency hijacking / Malicious code injection by a compromised or malicious upstream maintainer.
C. Improper output encoding.
D. Missing network firewall rule.

#### **4. A procurement officer is drafting the vendor contract for a critical new offshore software development firm. To mathematically verify that the final, compiled binary code delivered by the offshore vendor is exactly the same code that was theoretically reviewed and tested, and hasn't been secretly tampered with in transit over the internet, what specific process MUST be contractually mandated and enforced by the receiving team?**
A. The vendor must deliver the code via physical USB drives.
B. The vendor must provide the source code printed entirely on paper.
C. The receiving team must perform Code/Binary Signing verification, strictly checking the vendor's Cryptographic Hash (e.g., SHA-256) and Digital Signature upon receipt.
D. The receiving team must run an antivirus scan.

#### **5. In assessing the security maturity of a cloud service provider (CSP) acting as a massive link in an organization's supply chain, the enterprise architect requests to review the CSP's independent, third-party audit reports. Which internationally recognized compliance framework provides the most rigorous, standardized audit report specifically evaluating the operating effectiveness of a service organization's internal controls regarding security, availability, and confidentiality over a prolonged period (typically 6 to 12 months)?**
A. SOC 1 Type 1
B. SOC 2 Type 2
C. PCI-DSS
D. OWASP Top 10

#### **6. A junior developer mistakenly types `npm install react-domm` instead of the correct `npm install react-dom`. The malicious attacker who intentionally registered the dangerously similar name `react-domm` on the public registry immediately compromises the developer's workstation the moment the malicious package is downloaded. What is the specific name of this pervasive supply chain attack technique?**
A. SQL Injection
B. Typo-squatting
C. Directory Traversal
D. Clickjacking

#### **7. A large financial institution decides to heavily integrate a proprietary, commercial third-party API into their core banking mobile application to provide real-time stock quotes. To mitigate the immense risk of this third-party vendor suddenly going bankrupt, completely shutting down their servers, and bricking the bank's mobile app, what specific legal and operational safeguard should the bank fiercely negotiate to preserve business continuity?**
A. A Bug Bounty Program
B. Software Escrow Agreement (ensuring the vendor's source code is held by a trusted neutral third party and released to the bank if the vendor fails).
C. Multi-Factor Authentication (MFA)
D. A Non-Disclosure Agreement (NDA)

#### **8. The release engineering team builds a mature CI/CD pipeline. To prevent an internal attacker (or a compromised build server) from secretly swapping out the legitimate compiled application binary with a backdoored version just before sending it to the deployment repository, what cryptographic mechanism MUST the pipeline completely automate the instant the legitimate compilation finishes?**
A. Symmetrical AES encryption of the hard drive.
B. Automated Code Signing / Binary Signing of the generated artifact using a tightly guarded private key.
C. Changing the file extension from `.exe` to `.txt`.
D. Obfuscating the original source code.

#### **9. An organization is conducting a security risk assessment on a potential new Software-as-a-Service (SaaS) vendor. The vendor proudly states their data centers are physically impenetrable and their application is perfectly secure. However, the organization's CISO asks: "What happens to our extremely sensitive corporate data if we decide to cancel our subscription and terminate the contract next year?" This critical Vendor Risk Management question is probing for the presence of which crucial contract clause?**
A. Right to Audit Clause
B. Data Return and Secure Destruction / Deletion (Data Disposition) Clause
C. Service Level Agreement (SLA) penalty clause
D. Intellectual Property (IP) ownership clause

#### **10. A development team is terrified of incorporating compromised third-party open-source libraries into their codebase. To enforce strict supply chain hygiene, the security architect completely blocks all developers' laptops from directly reaching out to the public internet (like `npmjs.com` or `maven.org`) to download packages. Instead, what specific, secure architectural component MUST the architect deploy internally to fulfill the developers' need for libraries?**
A. A dedicated Web Application Firewall (WAF)
B. An Internal, privately hosted, and deeply curated Binary/Artifact Repository (e.g., Artifactory, Nexus) that acts as a secure proxy and aggressively scans all incoming public packages for known vulnerabilities before allowing internal users to download them.
C. A Virtual Private Network (VPN)
D. A public GitHub repository

#### **11. An enterprise considers migrating its highly sensitive, proprietary machine learning algorithms to a public cloud provider. The legal team expresses deep concern over "Lock-in Risk"—the danger that the enormous cost and technical complexity of moving petabytes of data out of this specific cloud provider in the future will structurally trap the enterprise and leave them entirely at the mercy of the vendor's future pricing extortion. To architecturally mitigate this specific vendor lock-in risk from day one, what modern software design strategy should the enterprise aggressively adopt?**
A. Writing everything in proprietary vendor-specific serverless languages.
B. Containerization (e.g., Docker/Kubernetes) and strictly utilizing cloud-agnostic open standards, ensuring the entire application stack can be relatively seamlessly ported to a competing cloud provider or an on-premise data center if negotiations fail.
C. Signing a 20-year exclusive contract with the vendor to lock in prices.
D. Relying exclusively on the vendor's proprietary NoSQL database engines.

#### **12. The term "Software Supply Chain" is often misunderstood as merely applying to the third-party open-source libraries a development team downloads. In reality, a mature, holistic view of the Software Supply Chain explicitly acknowledges that which of the following internal mechanisms is ALSO a massive, highly critical attack vector that must be fanatically secured?**
A. The company's physical front door locks.
B. The internal CI/CD pipelines, build servers (e.g., Jenkins), code repositories (e.g., GitHub), and the laptops of the developers themselves.
C. The marketing team's social media accounts.
D. The accounting department's payroll software.
