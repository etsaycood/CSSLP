# Exam 3
## Domain 7: Secure Software Deployment, Operations, Maintenance (13 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A critical zero-day vulnerability is announced for the web server software running a company's flagship e-commerce platform. The vendor releases an emergency patch. The operations team immediately applies the patch directly to all production servers to prevent exploitation. However, the patch inadvertently breaks the shopping cart functionality, causing massive revenue loss for 12 hours. Which foundational ITIL process was completely bypassed, directly causing this operational disaster?**
A. Incident Management
B. Configuration Management
C. Change Management (and Test/Staging deployment)
D. Problem Management

#### **2. An operations team is adopting Infrastructure as Code (IaC) using Terraform to deploy their AWS environment. They write a configuration file defining a new S3 bucket. A security junior reviews the code and asks why the team doesn't just log into the AWS Web Console to manually click the buttons to create the bucket, as it seems faster. What is the primary operational security advantage of using IaC scripts over manual GUI configuration?**
A. IaC automatically detects and blocks SQL injection attacks.
B. IaC guarantees consistency, completely eliminates human configuration drift ("snowflake servers"), and allows the infrastructure definitions to be version-controlled, code-reviewed, and automatically rolled back just like raw software source code.
C. Manual GUI configuration is illegal under modern PCI-DSS requirements.
D. IaC scripts do not require AWS IAM credentials to execute.

#### **3. A system administrator needs to securely access a Linux web server located in a highly isolated, segmented Demilitarized Zone (DMZ). Direct SSH access from the internal corporate network to the DMZ is strictly blocked by the firewall policy. To access the web server, the administrator must first SSH into a heavily locked-down, specialized intermediate server, and from there, SSH into the final web server. What is the standard industry term for this intermediate security control?**
A. A Web Application Firewall (WAF)
B. A Virtual Private Network (VPN) Concentrator
C. A Bastion Host (or Jump Box / Jump Server)
D. A Honeypot

#### **4. A cloud operations team manages a cluster of 50 web servers. One of the servers suddenly exhibits anomalous CPU spikes and strange network connections, indicating it may be compromised with a cryptominer. Instead of spending hours logging into the server, running forensic tools, and deleting the malware to "fix" it, the automated orchestration system simply kills the infected server instances and immediately spins up a brand-new, clean replacement server from a known-good master image. What modern operational security philosophy does this "destroy and replace" methodology embody?**
A. Immutable Infrastructure
B. Stateful Architecture
C. Continuous Integration
D. Continuous Monitoring

#### **5. While setting up logging for a new healthcare application, the developer decides to log everything to ensure the debugging team has full visibility if a bug occurs. The logging configuration captures the timestamp, the user's IP, the requested URL, and the full HTTP POST payload (which includes the user's password in plaintext and their Social Security Number). The application logs are then shipped to a centralized Splunk server accessible by 50 developers. What severe compliance and security violation has occurred?**
A. Insufficient Logging and Monitoring
B. Logging of Highly Sensitive Data (Violation of Data Minimization / Privacy Frameworks like HIPAA/GDPR)
C. Cross-Site Scripting (XSS)
D. Insecure Deserialization

#### **6. A DevOps team is building a CI/CD pipeline. They want to ensure that if a developer accidentally commits a file containing an embedded AWS Secret Key to the source code repository, the pipeline will immediately halt, sound an alarm, and absolutely refuse to deploy the code to production. At which specific stage of the CI/CD pipeline should this security check (e.g., secret scanning) IDEALLY be integrated to catch the error as early as possible?**
A. During the final Deployment (CD) script executing on the Production server.
B. Pre-commit hooks (on the developer's laptop) or as the very first step in the Continuous Integration (CI) build process (e.g., scanning the repository upon push).
C. During the User Acceptance Testing (UAT) phase.
D. During post-deployment Dynamic Application Security Testing (DAST).

#### **7. An IT department creates a detailed document outlining exactly how a system should be securely configured before it goes live. The document specifies that the default "admin" account must be disabled, Telnet must be uninstalled, and password complexity must be set to 12 characters. What is the formal term for this standardized, hardened baseline configuration document that all servers must adhere to?**
A. A Threat Model
B. A Risk Register
C. A Security Configuration Baseline (or Hardening Guide)
D. A Business Impact Analysis (BIA)

#### **8. A company utilizes an open-source Apache web server. A critical vulnerability (CVE-2024-XXXX) is published on a Tuesday morning, indicating a remote code execution flaw. The vendor releases the official patch the following Monday. However, on Thursday, attackers begin actively exploiting the flaw in the wild using exploit code posted online. From Tuesday morning until the official patch is released on Monday, what is the specific classification of this vulnerability?**
A. A Configuration Error
B. An Insider Threat
C. A Zero-Day Vulnerability
D. An Advanced Persistent Threat (APT)

#### **9. During an incident response investigation of a compromised web application, the forensic team is trying to determine exactly when the attacker bypassed the login screen. They discover that the application uses a decentralized load-balancing architecture across five different servers. The developers configured each server to use its own local, unsynchronized systemic clock. What specific operational failure will likely make creating a reliable, chronological timeline of the attacker's actions nearly impossible?**
A. The logs were not encrypted using AES-256.
B. The system failed to use Network Time Protocol (NTP) to reliably synchronize the clocks across all distributed application nodes, leading to disjointed timestamps.
C. The WAF was configured in "Monitor Only" mode.
D. The system did not use Multi-Factor Authentication (MFA).

#### **10. An organization decides to completely outsource its physical data center operations. They move all their customer-facing applications and databases into Microsoft Azure relying entirely on Azure's underlying physical security, hypervisor patching, and network edge routers. However, the organization retains full administrative control over the Windows Server Operating Systems running on the Virtual Machines, as well as the application code. According to the "Shared Responsibility Model" of cloud computing, what type of cloud service model has the organization adopted?**
A. Software as a Service (SaaS)
B. Platform as a Service (PaaS)
C. Infrastructure as a Service (IaaS)
D. Function as a Service (FaaS / Serverless)

#### **11. A legacy software application running on an obsolete operating system is vital to a manufacturing plant's assembly line. The operating system has reached End-of-Life (EoL) and no longer receives security patches from the vendor. Re-writing the software would cost millions of dollars and take three years. What is the BEST immediate operational control a security architect can deploy to minimize the risk of this unpatchable, highly vulnerable system being compromised?**
A. Install a lightweight Antivirus scanner directly on the obsolete OS.
B. Request a waiver from the CEO to accept the risk permanently.
C. Implement strict Network Segmentation (Network Isolation/VLANs) to air-gap or tightly restrict network communication to and from the obsolete machine, isolating it from the rest of the corporate network and the Internet.
D. Mandate that operators change their passwords every 15 days on the legacy system.

#### **12. The security operations center (SOC) receives an alert that a specific database administrator's account downloaded 500 gigabytes of customer data at 3:00 AM on a Sunday. This behavior represents a massive deviation from the administrator's typical weekday, 9-to-5 usage patterns. The SOC uses advanced machine learning tools to baseline normal behavior and flag these specific statistical anomalies. What category of monitoring tool is the SOC utilizing?**
A. Signature-Based Intrusion Detection System (IDS)
B. User and Entity Behavior Analytics (UEBA)
C. File Integrity Monitoring (FIM)
D. Static Application Security Testing (SAST)

#### **13. A company is shutting down an old data center. They are legally legally required to ensure that the highly classified client data stored on the solid-state drives (SSDs) in the old servers can NEVER be recovered by anyone, even a state-sponsored forensic laboratory. Software "wiping" programs are deemed insufficient for this level of security. What is the ONLY acceptable, definitive method to guarantee the data is permanently unrecoverable?**
A. Physical Destruction (e.g., Shredding or Pulverization of the hard drives)
B. Degaussing (using a giant magnet) on the SSDs.
C. Reformatting the drive using the "Quick Format" option.
D. Deleting the root directory.
