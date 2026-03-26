# Exam 1
## Domain 8: Secure Software Supply Chain (12 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A massive global cyberattack occurred when hackers successfully infiltrated the build server of a popular IT management software company (Company X). The hackers injected a malicious backdoor directly into Company X's official software update package. Thousands of Enterprise customers blindly downloaded and installed this "official update" because it was correctly digitally signed by Company X. What specific type of attack does this incredibly damaging scenario represent?**
A. Cross-Site Scripting (XSS)
B. Software Supply Chain Attack
C. Distributed Denial of Service (DDoS)
D. Social Engineering / Phishing

#### **2. You are managing the procurement of a new proprietary billing system from a third-party vendor. The CISO mandates that your organization must be protected in the event the vendor suddenly goes bankrupt, is acquired by a competitor, or simply refuses to provide support for the software in the future. To guarantee your organization will always have access to the underlying source code to maintain the system if the vendor vanishes, what specific legal mechanism MUST be established during the contract negotiations?**
A. A strict Non-Disclosure Agreement (NDA).
B. A comprehensive Service Level Agreement (SLA) mandating 99.99% uptime.
C. A Software Source Code Escrow Agreement.
D. A robust Disaster Recovery Plan (DRP).

#### **3. A development team is heavily reliant on open-source Node.js libraries downloaded directly from the public `npm` repository. A hacker creates a malicious package named `reackt` (notice the extra 'k'). The hacker is hoping that tired developers who intend to install the wildly popular legitimate library `react` will accidentally misspell the command parameter (e.g., `npm install reackt`) and pull down the virus instead. What is the industry term for this specific supply chain attack technique?**
A. Typosquatting
B. Buffer Overflow
C. Command Injection
D. Man-in-the-Middle (MITM) File Hijacking

#### **4. You are hired as a DevSecOps engineer to fortify a company's software delivery pipeline. Currently, developers compile their Java code on their personal laptops and manually upload the `.jar` files to the production server. To radically secure the software supply chain and ensure that code cannot be tampered with between the developer's keyboard and the final production environment, what architectural change MUST be implemented?**
A. Developers must start encrypting their laptops with BitLocker.
B. Implement a strictly controlled, automated Continuous Integration / Continuous Deployment (CI/CD) pipeline (e.g., using Jenkins or GitLab CI) acting as a secure, immutable "Build Factory" where no human can touch the compiled binary.
C. Require all developers to connect via VPN before uploading files to the production server.
D. Switch from programming in Java to programming in C++.

#### **5. In the aftermath of the devastating SolarWinds and Log4j supply chain breaches, the US Government issued an Executive Order mandating that all software vendors selling to the federal government must provide a comprehensive, machine-readable "ingredients list" detailing every single open-source and proprietary software component, library, and version used to build their final product. What is the formal, industry-standard acronym for this critical transparency document?**
A. Data Flow Diagram (DFD)
B. Service Level Agreement (SLA)
C. Software Bill of Materials (SBOM)
D. Acceptable Use Policy (AUP)

#### **6. A team is downloading a critical Linux kernel update. The file is massive (4 GB) and took hours to download from a public mirror site somewhat far away. To mathematically verify that the downloaded file is *exactly* the same as the original file published by the Linux creators—and that it was not corrupted during the network transmission or secretly replaced with malware by the intermediary mirror site—what simple cryptographic check MUST the team perform against the downloaded file before executing it?**
A. Encrypt the file using RSA-2048.
B. Run an automated SAST scan on the compiled binary.
C. Generate a cryptographic Hash (e.g., SHA-256) of the downloaded file and explicitly compare it against the official published Hash value found on the creator's secure website.
D. Compress the file using a ZIP utility and check the compression ratio.

#### **7. A developer is building a Docker container image for a new web service. The `Dockerfile` starts with the instruction: `FROM ubuntu:latest`. A senior security architect immediately flags this line as a severe supply chain and operational risk. Why is using the `:latest` tag considered an extremely poor practice in containerized environments?**
A. The `latest` tag requires the image to be downloaded from the internet every single time the container starts, consuming too much bandwidth.
B. The `latest` tag is completely non-deterministic. It silently points to a different, potentially incompatible, or newly vulnerable underlying operating system version every time the vendor publishes an update. Developers MUST pin dependencies to a specific, immutable version hash (e.g., `ubuntu:20.04` or `sha256:abc123...`) to guarantee the build is reproducible and predictable.
C. Images tagged with `latest` are automatically run with `root` privileges by the Docker daemon.
D. The `latest` tag automatically triggers a DAST scan which slows down the deployment pipeline.

#### **8. Your company outsources the development of its mobile application to a contractor in another country. The contract is ending, and the contractor hands over the final source code. Before compiling the code and releasing it to the Apple App Store, your security team performs a thorough audit. They discover several hardcoded API keys and a hidden function that quietly transmits all users' geolocation data directly back to a server owned by the contractor, clear outside of your company's control. What specific threat vector in the software supply chain does this represent?**
A. An unintentional Buffer Overflow vulnerability.
B. An intentional Logic Bomb or Malicious Backdoor planted by an untrusted third-party supplier.
C. Resource Exhaustion leading to Denial of Service.
D. Insecure Direct Object Reference (IDOR).

#### **9. An organization is evaluating a new open-source database to replace its expensive proprietary system. The enterprise architecture team notes that the open-source project is heavily maintained by only a single, unpaid developer who hasn't committed any new code or responded to bug reports in over 3 years. From a secure supply chain perspective, what is the primary risk of adopting this specific open-source component?**
A. Open-source software is inherently illegal to use for commercial purposes.
B. The project suffers from severe "Abandonware / Lack of Maintenance" risk. If a zero-day vulnerability is discovered tomorrow, there is no active community or vendor to patch it, leaving the enterprise permanently exposed.
C. The software lacks a graphical user interface (GUI).
D. The developer might suddenly demand millions of dollars in licensing fees.

#### **10. You are designing a secure Continuous Delivery (CD) pipeline. After the source code is successfully checked by SAST, compiled into a container image, and tested, the pipeline pushes the final image to the company's private Container Registry. To ensure that the Kubernetes production cluster *only* runs images that have legitimately passed through this specific, secure build pipeline (and to prevent an administrator from manually deploying a rogue, untested image), what security control must the CI/CD pipeline apply to the image before pushing it?**
A. The pipeline must Cryptographically Sign the container image using tools like Docker Content Trust or Cosign. The Kubernetes cluster is then configured with an admission controller to strictly reject any image lacking this specific digital signature.
B. The pipeline must encrypt the entire container image so it cannot be read by unauthorized users.
C. The pipeline must automatically delete the source code from the repository to prevent modifications.
D. The pipeline must generate a massive text file detailing every line of code inside the container.

#### **11. A massive retail company heavily relies on a third-party managed service provider (MSP) to monitor its thousands of point-of-sale (POS) systems. The MSP requires an always-on, highly privileged remote access VPN connection into the retailer's internal core network to perform maintenance. Hackers compromise the MSP's relatively weak security perimeter. They then use the MSP's legitimate, highly trusted VPN connection as a bridge to seamlessly slip into the retail company's highly fortified network, stealing millions of credit cards. Why are "Trusted Third-Party Service Providers" considered one of the weakest links in the modern supply chain?**
A. MSPs usually use outdated antivirus software.
B. Establishing an overly permissive, persistent "Trust Relationship" creates a colossal backdoor. An attack on the weaker third-party supplier allows hackers to easily bypass the primary target's strong perimeter defenses, leveraging the pre-established trust bridge.
C. Retail companies never patch their POS systems.
D. Third-party providers often steal the data themselves.

#### **12. Your team wants to incorporate a fantastic open-source charting library into your commercial, proprietary payroll software. During the architectural review, the legal department discovers that this specific open-source library is governed by the "GNU General Public License (GPL) v3". The lawyers immediately forbid the developers from using it. Why is integrating a GPL-licensed component into a closed-source, commercial product considered legally and operationally catastrophic?**
A. The GPL requires you to pay a massive royalty fee for every user who clicks on the chart.
B. The GPL is a strong "Copyleft" (Viral) license. If you link or incorporate GPL code into your proprietary software and distribute it, the license legally forces you to also open-source your entire, highly valuable proprietary codebase under the same GPL terms.
C. GPL software is notoriously unsecure and filled with known backdoors.
D. The GPL explicitly prohibits the software from being used for financial or payroll purposes.
