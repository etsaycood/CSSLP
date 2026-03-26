# Exam 4
## Domain 8: Secure Software Supply Chain (12 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A software development company wants to improve the transparency and security of its supply chain. They decide to generate a machine-readable inventory detailing all the open-source libraries, third-party frameworks, and proprietary components used to build their final software product. This inventory will be shared with their enterprise customers to help them manage their own risk. What is this comprehensive inventory document called?**
A. A Value Stream Map (VSM)
B. A Software Bill of Materials (SBOM)
C. A Service Level Agreement (SLA)
D. A Vendor Risk Assessment Questionnaire

#### **2. An attacker decides that hacking directly into a highly secured bank is too difficult. Instead, the attacker targets a small, less-secure company that provides a specialized charting library used by the bank's mobile app. The attacker compromises the charting library's code repository and injects a backdoor. When the bank updates the library in its next release, the backdoor is deployed to all the bank's customers. What specific class of attack does this scenario describe?**
A. Cross-Site Scripting (XSS) Attack
B. Phishing Attack
C. Software Supply Chain Attack
D. Denial of Service (DoS) Attack

#### **3. An organization relies heavily on several SaaS providers and third-party IT vendors. To ensure these external entities have adequate security controls in place (like encryption, access management, and incident response) before signing a contract, the organization's security team requires the vendors to complete a standardized set of security questions and provide evidence of independent audits (e.g., SOC 2 reports). What is this crucial supply chain risk management activity called?**
A. Penetration Testing
B. Third-Party / Vendor Risk Assessment (Due Diligence)
C. Static Application Security Testing (SAST)
D. Threat Modeling

#### **4. A developer uses an open-source library downloaded from a public package repository (like npm or Maven Central). To guarantee that the downloaded package is the exact, unaltered version published by the original author and has not been maliciously modified in transit or tampered with on the repository server itself, what specific verification mechanism should the package manager or developer use before utilizing the library?**
A. Checking the library's star rating on GitHub.
B. Running a dynamic analysis (DAST) scan on the downloaded `.jar` or `.tgz` file.
C. Verifying the library's Cryptographic Hash (checksum) and Digital Signature against the author's published public key.
D. Using a Virtual Private Network (VPN) to download the file.

#### **5. In the context of securing a CI/CD pipeline against supply chain threats (like the SolarWinds attack), a security engineer implements a policy requiring that any code merged into the `main` branch must have been reviewed and approved by *at least one other developer* who did not author the code. The build machine will physically reject the code if this condition is not met in the Git repository. What security principle is being enforced here?**
A. Separation of Duties (Two-Person Rule / Peer Review)
B. Data Minimization
C. Fuzzing
D. Obfuscation

#### **6. A software vendor utilizes a component licensed under the GNU General Public License (GPL). According to the strict "copyleft" nature of this specific open-source license, if the vendor dynamically links or incorporates this GPL component into their own proprietary, closed-source application and distributes it to the public, what is the vendor legally obligated to do?**
A. The vendor only needs to pay a small royalty fee to the original GPL author.
B. The vendor must release the entire source code of their own proprietary application under the same GPL license (or a compatible open-source license).
C. The vendor must ensure the software has no zero-day vulnerabilities.
D. The vendor can keep their source code closed, provided they mention the GPL author in the "About" menu.

#### **7. An organization discovers that a critical open-source library used throughout their microservices architecture has just been assigned a CVE for a Remote Code Execution (RCE) vulnerability. However, the original maintainer abandoned the project two years ago, and no official patch will be released. This is a classic supply chain risk. What is the MOST viable long-term remediation strategy for the organization?**
A. Implement a temporary WAF rule and continue using the vulnerable library indefinitely.
B. Fork the repository, apply a custom fix internally (if possible), and plan to migrate to a different, actively maintained library that provides similar functionality.
C. Threaten to sue the open-source author for abandoning the project.
D. Ignore the vulnerability if the organization uses a cloud-native Kubernetes architecture.

#### **8. Which of the following is considered a "malicious" supply chain attack technique where attackers discover a popular, legitimate open-source package (e.g., `requests`) and publish a malicious package with a deliberate, subtle typo in the name (e.g., `reqeusts` or `requestts`) on a public registry, hoping developers will accidentally download the poisoned version?**
A. Dependency Confusion
B. Typosquatting
C. Account Takeover (ATO)
D. Build Environment Compromise

#### **9. An organization provides an API key to a contracted third-party marketing vendor so their systems can read customer analytics data. However, the organization's security team configures the API key so that it can ONLY execute `GET` requests on specific endpoints and explicitly Denies any `POST`, `PUT`, or `DELETE` operations. What security principle is the organization applying to manage this third-party risk?**
A. Security through Obscurity
B. Principle of Least Privilege (PoLP)
C. Fail-Safe Defaults
D. Economy of Mechanism

#### **10. To mathematically prove the provenance and integrity of a software artifact (e.g., a Docker container image) moving through a CI/CD pipeline, organizations increasingly adopt frameworks like SLSA (Supply chain Levels for Software Artifacts). What critical mechanism does SLSA primarily rely on to bind an artifact to its build metadata and source code origin?**
A. Storing the artifacts in a hidden, unlisted directory.
B. Cryptographically signing the build provenance (the metadata describing how, when, and by whom the artifact was built).
C. Running a comprehensive Penetration Test before release.
D. Encrypting the entire source code repository with AES-256.

#### **11. A developer copies a 50-line algorithm from a popular coding forum (like Stack Overflow) directly into the company's proprietary trading software. The developer did not check the licensing terms of the snippet or understand exactly how the algorithm allocates memory. What are the two primary supply chain risks introduced by this action?**
A. Increased application performance and reduced infrastructure costs.
B. Potential Intellectual Property (IP) / Licensing infringement and the introduction of unvetted security vulnerabilities or malicious code.
C. The code will automatically be deleted by the compiler, causing build failures.
D. The company's servers will immediately be targeted by a DDoS attack.

#### **12. When evaluating a potential third-party software vendor, an organization requests the vendor's incident response plan and their historical track record of patching vulnerabilities (Mean Time to Repair - MTTR). What specific aspect of the vendor's security posture is the organization trying to assess?**
A. The vendor's financial stability and revenue growth.
B. The vendor's UI/UX design capabilities.
C. The vendor's operational resilience and their commitment to ongoing security maintenance and transparency.
D. The vendor's ability to conduct White-Box penetration testing.
