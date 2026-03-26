# Exam 1
## Domain 7: Secure Software Deployment, Operations, and Maintenance (13 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A critical e-commerce application is deployed onto a fleet of Linux servers. To ensure the principle of "Least Privilege," the system administrator creates a dedicated service account named `app_user` to run the web application process. However, the application requires the ability to bind to TCP Port 443 (HTTPS) to serve secure web traffic. In standard Linux environments, ordinary users (like `app_user`) cannot bind to privileges ports (ports below 1024). What is the MOST secure, modern operational practice to allow this application to listen on Port 443 without running the entire application as the all-powerful `root` user?**
A. Add the `app_user` to the `wheel` (Administrators) group so it has full system access.
B. Temporarily run the application as `root` so it can bind the port, and then rely on the application code to securely demote its own privileges (setuid) down to `app_user`.
C. Use a Reverse Proxy (like NGINX or HAProxy) or Linux Capabilities (`setcap cap_net_bind_service`) to handle the Port 443 binding, forwarding traffic to the application running on a high, unprivileged port (e.g., 8443) as `app_user`.
D. Disable the Linux firewall completely because port restrictions often interfere with application deployment.

#### **2. Your organization relies on a sprawling microservices architecture managed by Kubernetes. You want to enforce a strict security policy where the "Payment Container" is absolutely forbidden from opening a network connection to the "Public Web Server Container," even though they are running on the same physical cluster. Which specific Operational Security (OpSec) technology is designed to dynamically enforce these internal, east-west network traffic rules between containerized applications?**
A. Hardware Next-Generation Firewalls (NGFW) at the physical data center edge.
B. Virtual Private Network (VPN) tunnels.
C. Container Network Interface (CNI) Network Policies (e.g., Calico or Cilium) / Microsegmentation.
D. Web Application Firewall (WAF).

#### **3. A development team is preparing to deploy a new version of their cloud-native application. They use a technique where they spin up a completely identical production environment (Environment B) alongside the currently running environment (Environment A). They deploy the new code to Environment B, test it thoroughly, and then simply flip the load balancer router to seamlessly redirect all live user traffic from A to B with zero downtime. What is the industry term for this highly resilient deployment strategy?**
A. Canary Deployment
B. Blue/Green Deployment (or Red/Black Deployment)
C. Rolling Update Deployment
D. In-Place Upgrade

#### **4. You are auditing the Disaster Recovery (DR) plan of a financial institution. The core banking application has a strict business requirement: "In the event of a catastrophic data center failure, the banking system must be brought back online within a maximum of 4 hours." In the vocabulary of Business Continuity Planning (BCP), what specific metric does this "4-hour" requirement represent?**
A. Recovery Point Objective (RPO)
B. Mean Time To Repair (MTTR)
C. Recovery Time Objective (RTO)
D. Service Level Agreement (SLA)

#### **5. A critical vulnerability (CVSS Score 10.0) is publicly announced for a widely used open-source web server framework. The vendor immediately releases a patch. As the Operations Lead, you manage a cluster of 500 web servers running this framework. To minimize the window of vulnerability, you utilize a centralized management tool (like Chef, Puppet, or Ansible) to automatically push out the patch requirement to all 500 servers simultaneously without manual human intervention. What IT Operations concept are you heavily relying upon?**
A. Infrastructure as Code (IaC) / Configuration Management
B. Data Loss Prevention (DLP)
C. Continuous Integration (CI)
D. Formal Threat Modeling

#### **6. An enterprise applies a crucial security update to their flagship inventory management software. Two days after the patch is deployed, the helpdesk is flooded with thousands of calls from warehouse workers stating they can no longer print shipping labels—a feature that had worked flawlessly for years. Which critical software deployment practice was likely skipped or poorly executed by the release team before pushing the patch to production?**
A. Vulnerability Scanning (DAST)
B. Code Signing verification
C. Regression Testing
D. Threat Profiling

#### **7. A cloud operations team is configuring an Auto-Scaling Group in AWS for their web application. During normal business hours, the application runs on 5 Virtual Machines (VMs). The team configures a rule: "If average CPU utilization across the group exceeds 80% for more than 5 minutes, automatically launch 3 additional VMs." This operational design directly addresses which core pillar of the CIA Triad?**
A. Confidentiality
B. Integrity
C. Availability
D. Non-Repudiation

#### **8. A software development company sells a proprietary medical imaging application to hospitals. The application is installed directly on the servers inside the hospital's private network. When a zero-day vulnerability is discovered in the application's code, the company must quickly distribute the fix to hundreds of isolated hospital networks worldwide. To ensure the hospitals can cryptographically verify that the patch file truly originated from the software company and has not been tampered with by a man-in-the-middle attacker, what mechanism MUST the software company perform before distributing the executable patch?**
A. Compress the patch into a password-protected `.zip` file.
B. Encrypt the patch file using AES-256 Symmetric Encryption.
C. Digitally Sign the patch executable using the software company's private key (Code Signing).
D. Upload the patch exclusively via FTP (File Transfer Protocol).

#### **9. During a routine security audit of a deployed web application, you examine the HTTP security headers returned by the web server. You notice the absence of the `Strict-Transport-Security` (HSTS) header. What specific attack vector does the lack of an HSTS header expose the users' web browsers to during normal operations?**
A. Cross-Site Scripting (XSS)
B. SQL Injection
C. Secure Sockets Layer (SSL) Stripping / Downgrade Attacks
D. Directory Traversal

#### **10. An application crashes silently at 3:00 AM on a Sunday. The automated monitoring system detects the failure and automatically executes a predefined script that cleanly restarts the application service, bringing it back online by 3:02 AM without waking up any human engineers. The next morning, the engineers review the logs to investigate the root cause of the crash. This autonomous process of detecting a failure and automatically restoring functionality is an example of what operational concept?**
A. Proactive Threat Hunting
B. Incident Response Forensics
C. Self-Healing Architecture / Automated Remediation
D. Canary Release Strategy

#### **11. A massive database breach occurred because an administrator needed to urgently fix a configuration issue in the live production database. To perform the work, the admin logged in using the shared, all-powerful `sa` (System Administrator) database account, whose password was known by five different people on the team. After the breach, the forensic investigators could not determine *which* of the five people actually made the disastrous "DROP TABLE" change. Which fundamental security principle was completely destroyed by the use of this shared account?**
A. Confidentiality (Data Privacy)
B. Non-Repudiation (Individual Accountability)
C. Availability (System Uptime)
D. Cryptographic Integrity

#### **12. The DevOps team implements a "Continuous Monitoring" solution for their newly deployed application. The tool ingests thousands of application logs, server performance metrics, and network traffic flows per second. It uses machine learning baseline models to understand the "normal" behavior of the application. Yesterday, the tool fired a massive, high-priority alert because the application suddenly started establishing an outbound connection to an unknown IP address in a high-risk country, transferring 5 GB of data. The system triggered this alert because it detected what?**
A. A Code Review Failure
B. An Anomaly / Deviation from the established behavioral baseline (Indicating potential Data Exfiltration)
C. A Denial of Service (DoS) Attack
D. A Buffer Overflow compiling error

#### **13. A company has decided to completely overhaul and replace its legacy 20-year-old HR portal with a new, cloud-native SaaS solution. The old portal contains decades of highly sensitive employee social security numbers, salaries, and disciplinary records. As part of the final "Software Sunset / End-of-Life (EOL)" phase for the legacy system, what is the most critical operational security requirement to legally and safely retire the old servers?**
A. Leaving the old servers powered on indefinitely just in case someone needs an old record.
B. Performing a final DAST security scan on the legacy application.
C. Securely migrating necessary historical data to the new system, followed by the rigorous, cryptographically secure wiping (Cryptographic Erasure) or physical destruction of the old server hard drives (Secure Data Disposal) to prevent data remanence.
D. Updating the documentation for the old server's API endpoints.
