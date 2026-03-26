# Exam 3
## Domain 8: Secure Software Supply Chain (12 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. Following a devastating supply chain attack where a compromised third-party library was injected into their flagship product, the CISO mandates that the engineering team must automatically generate and publish a cryptographic inventory of every single open-source and proprietary component used to build the software. What specific artifact serves as this transparent "ingredients list" for the software supply chain?**
A. A Code Signing Certificate
B. A Service Level Agreement (SLA)
C. A Software Bill of Materials (SBOM)
D. A Static Application Security Testing (SAST) Report

#### **2. An attacker wants to compromise a popular Node.js application. Instead of attacking the application's servers directly, the attacker notices that the application relies on an open-source npm package named `data-parser-utils`. The attacker creates a malicious package with an almost identical name, `data-parsr-utils` (missing the 'e'), hoping developers will accidentally make a typo when installing the dependency. What specific type of supply chain attack is this?**
A. Dependency Confusion
B. Typosquatting
C. Cross-Site Request Forgery (CSRF)
D. Man-in-the-Middle (MitM)

#### **3. A large financial institution is evaluating a small, independent software vendor to provide a critical new payment processing module. Before signing the contract, the institution demands to review the vendor's internal security policies, their latest penetration testing results, and their employee background check procedures to ensure the vendor won't introduce unacceptable risk into the institution's ecosystem. What is the formal name for this rigorous evaluation process?**
A. Software Composition Analysis (SCA)
B. Third-Party Risk Assessment (or Vendor Risk Management)
C. Dynamic Application Security Testing (DAST)
D. Incident Response Planning

#### **4. To prevent unauthorized modifications to the source code after it has been reviewed and approved, a development team enforces a strict policy: Every single commit to the main production branch in Git must be cryptographically signed by the developer using their private GPG key. This ensures the organization can definitively prove which specific developer authored the altered code. Which fundamental security principle does this code-signing mandate enforce?**
A. Non-Repudiation (and Authenticity)
B. Availability
C. Obfuscation
D. Least Privilege

#### **5. An enterprise development team uses a private, internal artifact repository (like JFrog Artifactory or Sonatype Nexus) to cache approved versions of open-source libraries (e.g., Maven, npm). The build servers are strictly configured to pull libraries ONLY from this internal repository, completely blocking them from downloading packages directly from the public internet. What is the primary supply chain risk this architecture mitigates?**
A. It prevents SQL Injection attacks on the build server.
B. It drastically reduces the risk of developers accidentally downloading malicious, unvetted, or tampered packages directly from public repositories, enforcing a single source of truth for approved dependencies.
C. It ensures the build runs faster because internal networks have more bandwidth.
D. It automatically encrypts all source code before compiling.

#### **6. A company develops firmware for medical devices. To assure hospitals that the firmware update files downloaded from the company's website have not been tampered with or replaced by malware while in transit across the internet, the company provides a SHA-256 hash value next to the download link. Providing this cryptographic hash ensures which core tenet of the CIA triad for the supply chain artifact?**
A. Confidentiality
B. Integrity
C. Availability
D. Authorization

#### **7. A cloud-native startup utilizes hundreds of open-source container images from Docker Hub. The security team implements an automated policy that immediately blocks any container image from running in the production Kubernetes cluster if the image has not been scanned for CVEs within the last 24 hours and if its digital signature cannot be verified against the trusted corporate registry. What process is the security team enforcing?**
A. Penetration Testing
B. Container Image Provenance and Attestation Verification
C. Static Application Security Testing (SAST)
D. Distributed Denial of Service (DDoS) Mitigation

#### **8. The "SolarWinds" attack is often cited as the textbook example of an Advanced Persistent Threat (APT) supply chain compromise. How did the attackers primarily distribute their malicious code to thousands of highly secure government and corporate customer networks?**
A. By sending massive phishing email campaigns to the target companies' employees.
B. By compromising the SolarWinds build environment and injecting a digitally signed, malicious backdoor into a legitimate software update, which the customers then downloaded and installed automatically.
C. By exploiting a zero-day vulnerability in the customers' Cisco firewalls.
D. By physically breaking into data centers and plugging in infected USB drives.

#### **9. A development organization specifies in its vendor contracts that any third-party software library integrated into their product must have a "Time-to-Remediate" Service Level Agreement (SLA) of less than 72 hours for critical CVEs. If the open-source project or vendor cannot patch critical vulnerabilities within this timeframe, the organization will refuse to use the library. What specific aspect of supply chain security management does this address?**
A. Intellectual Property (IP) Protection
B. License Compliance (e.g., GPL, MIT)
C. Vulnerability Management and Response Capabilities of the Supplier
D. Code Obfuscation Requirements

#### **10. An attacker discovers that a corporate application relies on private internal packages (e.g., `com.mycompany.utils`). The attacker publishes a malicious package with the exact same name (`com.mycompany.utils`) to the public internet repository (like public npm) but gives it a much higher version number (v99.0.0). Because the corporate build tool is misconfigured, it automatically pulls the highest version number from the public internet instead of using the local v1.0.0 internal package, inadvertently executing the attacker's code. What is this specific supply chain attack called?**
A. Dependency Confusion (or Dependency Hijacking)
B. Typosquatting
C. Cross-Site Scripting (XSS)
D. Buffer Overflow

#### **11. A developer copies a large block of code from a popular open-source project on GitHub that is licensed under the strict GNU General Public License (GPL) and pastes it directly into their company's proprietary, closed-source commercial software product. According to standard open-source licensing compliance, what is the most likely severe consequence for the company?**
A. The company's database will automatically encrypt itself.
B. The company faces significant legal risk, as the "viral" nature of the GPL may legally force the company to open-source and publish their entire proprietary codebase for free.
C. The code will fail to compile.
D. The company will be fined by the FBI for hacking.

#### **12. During the build process, a Continuous Integration (CI) server compiles the source code into a binary executable. The CI pipeline is configured to calculate the hash of the source code repository states, the specific compiler version used, and the final output binary, packaging these cryptographically signed metadata records together. This verifiable record that proves *how* and *from what* the software was built is known fundamentally as:**
A. A Non-Disclosure Agreement (NDA)
B. Software Provenance (or Build Attestation)
C. A Threat Model
D. An End-User License Agreement (EULA)
