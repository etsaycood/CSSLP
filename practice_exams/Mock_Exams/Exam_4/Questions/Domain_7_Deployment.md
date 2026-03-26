# Exam 4
## Domain 7: Secure Software Deployment, Operations, Maintenance (13 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A DevOps engineer is configuring a CI/CD pipeline. Instead of a human administrator manually SSHing into production servers to run installation scripts (which creates configuration drift and security risks), the engineer writes configuration files (e.g., Terraform or Ansible playbooks) that define the required state of the production environment. The pipeline automatically provisions the servers exactly as defined in the files. What is this security-enhancing deployment paradigm called?**
A. Manual Patch Management
B. Infrastructure as Code (IaC)
C. Continuous Monitoring (CM)
D. Chaos Engineering

#### **2. An organization is deploying a new version of their e-commerce application. To minimize downtime and reduce the risk of a catastrophic failure affecting all users simultaneously, they deploy the new version alongside the old version. They configure the load balancer to route only 5% of real user traffic to the new version initially to monitor for errors. If it is stable, they will gradually increase the traffic to 100%. What deployment strategy is this?**
A. Blue/Green Deployment
B. Canary Release
C. In-Place Update
D. Big Bang Deployment

#### **3. During the operational phase of a software system, a massive Distributed Denial of Service (DDoS) attack hits the application's main login endpoint. The Incident Response (IR) team is activated. According to standard IR frameworks (like NIST SP 800-61), after "Detecting and Analyzing" the attack, what is the immediate NEXT critical phase the team must execute to limit the damage?**
A. Post-Incident Activity (Lessons Learned)
B. Preparation
C. Eradication and Recovery
D. Containment

#### **4. A cloud architecture uses auto-scaling groups to match server capacity with user demand. The security team insists on building virtual machine images (AMIs) that contain the OS, application code, and all security hardening configurations fully baked in. When a new server spins up, it boots from this image and *never* receives updates or configuration changes while running; if a patch is needed, a completely new image is built to replace the old running instances. What operational security concept does this represent?**
A. Immutable Infrastructure
B. Mutable Architecture
C. Legacy Server Management
D. Defense in Depth

#### **5. In the context of secure operations, what is the primary security objective of implementing "Continuous Monitoring" (Continuous Defend / Continuous Security Monitoring)?**
A. To automatically fix bugs in the source code as soon as developers type them.
B. To provide historical data exclusively for annual compliance audits.
C. To gain real-time visibility into the security posture, performance, and potential anomalies of the production system, enabling rapid detection and response to active threats or degraded states.
D. To ensure the software license has not expired.

#### **6. A security operations center (SOC) analyst is overwhelmed by the sheer volume of firewall logs, web server logs, and application error logs. To correlate these disparate log sources, identify attack patterns (like a brute-force attack spanning multiple systems), and generate actionable alerts, what type of centralized security platform MUST the organization implement?**
A. A Security Information and Event Management (SIEM) system.
B. An Intrusion Prevention System (IPS).
C. A Static Application Security Testing (SAST) tool.
D. A Relational Database Management System (RDBMS).

#### **7. A highly critical zero-day vulnerability (Out-of-Band patch) is announced for the web server software used by an organization. The security policy mandates that emergency patches must be applied within 24 hours. To ensure the patch does not break the live production application, what is the BEST initial step the operations team should take before deploying to production?**
A. Apply the patch directly to production to meet the 24-hour SLA immediately.
B. Ignore the patch until the next regularly scheduled maintenance window (next month) to avoid disruption.
C. Deploy and test the patch in a Staging/Pre-production environment that closely mirrors the production environment to verify stability and compatibility.
D. Shut down the web servers completely until a new version of the OS is released.

#### **8. During a post-mortem analysis of a recent security breach, the team discovers that the attacker gained initial access utilizing an employee's password that had been compromised in a public data breach three years ago. The system had not forced the user to change or upgrade their authentication method since the account was created. Which operational control failed?**
A. Secure Disposal (Data Sanitization)
B. Credential Lifecycle Management (and failure to enforce MFA)
C. Incident Response Containment
D. Application Whitelisting

#### **9. An operations team is decommissioning a cluster of old database servers that previously stored highly sensitive medical records (PHI). To comply with HIPAA and secure data disposal regulations, what is the ONLY acceptable method to ensure the data cannot be recovered by forensic techniques before the hard drives are sent to a recycling vendor?**
A. Formatting the hard drives using the operating system's standard "Quick Format" tool.
B. Simply deleting the files and emptying the Recycle Bin.
C. Performing Cryptographic Erasure (Crypto-Shredding) or physical destruction (e.g., degaussing, shredding, pulverizing) of the storage media.
D. Archiving the data to AWS S3 before deleting it locally.

#### **10. A software vendor discovers a serious security flaw in their application. They develop a patch and want to distribute it to their enterprise customers securely. To prevent attackers from intercepting the download and substituting the patch file with malware (a supply chain or man-in-the-middle attack), what MUST the vendor provide alongside the patch file?**
A. A detailed PDF manual explaining how the vulnerability works.
B. A cryptographic hash (e.g., SHA-256 checksum) and a Digital Signature so the customer can verify the file's integrity and authenticity before installation.
C. A symmetric encryption key sent via the same email as the download link.
D. A free license upgrade.

#### **11. In a containerized environment (like Docker or Kubernetes), which security practice is considered CRITICAL during the deployment phase to prevent a compromised container from taking over the underlying host node?**
A. Running all containers as the `root` user to ensure they have enough permissions to execute.
B. Disabling all network isolation to make debugging easier.
C. Enforcing the Principle of Least Privilege by configuring containers to run as non-root users and dropping unnecessary Linux capabilities (e.g., using a Security Context).
D. Storing SSH keys directly inside the container image.

#### **12. An application relies on several third-party APIs for processing payments and validating addresses. The operations team sets up synthetic monitoring scripts that ping these APIs every minute. If an API returns a 500 Error or takes longer than 5 seconds to respond, an alert is sent to a PagerDuty channel. What operational aspect is being monitored here?**
A. Data Confidentiality
B. Service Level Agreements (SLAs) and System Availability
C. Code Complexity
D. Vulnerability Density

#### **13. What is the fundamental goal of conducting a "Lessons Learned" (or Post-Incident Review / Post-Mortem) meeting at the conclusion of an incident response process?**
A. To assign blame to a specific developer or operations engineer so they can be fired.
B. To permanently shut down the compromised application.
C. To identify what went wrong, what defenses failed, what process bottlenecks occurred, and to implement corrective actions (improving playbooks, adding controls) to prevent the same type of incident from happening again.
D. To immediately notify the public and news media about the breach before internal analysis is complete.
