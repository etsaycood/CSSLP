# Exam 2
## Domain 7: Secure Software Deployment, Operations, Maintenance (13 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A deployment team is rolling out a major update to a massive, highly critical global e-commerce platform. To absolutely minimize the risk of a catastrophic outage that affects all users simultaneously, the team deploys the new version `V2` alongside the existing version `V1`. They configure the external load balancer to initially send only 5% of live customer traffic to `V2` while keeping 95% on `V1`. After observing the `V2` error logs for an hour and confirming stability, they slowly ramp up `V2` until it handles 100% of the traffic. Which modern deployment strategy does this specific rollout technique represent?**
A. Blue/Green Deployment
B. Canary Release
C. In-Place Deployment
D. Big Bang Deployment

#### **2. Following a high-profile data breach, the incident response team discovers that a hacker managed to exploit a known vulnerability in the Apache Tomcat web server that was patched by the vendor six months ago. The operations team claims they were terrified to apply the patch because the ancient, monolithic application is extremely fragile and lacks any automated regression tests. What critical IT Operations process fundamentally failed here?**
A. Threat Modeling
B. Vulnerability Scanning
C. Patch Management
D. Penetration Testing

#### **3. The DevOps team completely rebuilds the underlying Docker image for a heavily used microservice twice a week. Instead of logging into the running production containers to manually install OS updates (which leads to configuration drift), the team simply destroys the old production containers and deploys the freshly built ones containing the new OS patches. What foundational cloud-native operational concept is this team strictly enforcing?**
A. Immutable Infrastructure
B. High Availability
C. Infrastructure as a Service (IaaS)
D. Chaos Engineering

#### **4. A company hosts a highly regulated healthcare portal handling electronic health records (EHR). The Chief Information Security Officer (CISO) mandates that if any malicious code unexpectedly tries to modify the core application `.dll` or `.jar` files residing on the production server's hard drive, the security operations team (SOC) must receive an immediate, high-priority alert within 15 seconds. What specific security tool MUST be installed on the production web servers to achieve this localized file monitoring requirement?**
A. File Integrity Monitoring (FIM)
B. Data Loss Prevention (DLP)
C. Web Application Firewall (WAF)
D. Intrusion Prevention System (IPS)

#### **5. During a routine external audit, the auditor requests proof that the application development team is not secretly bypassing the change control board to directly push untested code into the live production environment. The auditor demands to see a clear, impenetrable separation between the people who "write" the code and the people who "deploy" the code to production. This requirement is a classic enforcement of which security principle?**
A. Complete Mediation
B. Need-to-Know
C. Separation of Duties (SoD)
D. Job Rotation

#### **6. A junior site reliability engineer (SRE) accidentally submits a destructive Terraform script that instantly deletes the company's entire primary production database cluster in AWS. Because the company operates a highly mature disaster recovery footprint, a secondary, fully synchronized identical environment sitting idle in another geographic region is immediately spun up and takes over the traffic within 10 minutes, resulting in minimal data loss. What type of disaster recovery site architecture did the company utilize?**
A. Cold Site
B. Warm Site
C. Hot Site
D. Mobile Site

#### **7. A highly secure financial application undergoes a complete lifecycle decommissioning because a newer, modernized platform is replacing it. Before physically throwing the old database hard drives into the corporate dumpster, the hardware disposal team uses a specialized magnetic wand to completely scramble and destroy the magnetic domains on the platters, rendering the data mathematically unrecoverable. What specific data destruction method did the team use?**
A. Cryptographic Erasure (Crypto-Shredding)
B. Degaussing
C. Software Wiping (Zeroization)
D. Physical Shredding

#### **8. The security operations center (SOC) receives 5,000 automated security alerts per day from the Web Application Firewall (WAF), the endpoint antivirus (EDR), and the network intrusion detection systems (IDS). The analysts are completely overwhelmed ("Alert Fatigue") and naturally start ignoring low-priority warnings. To solve this, the architect implements a centralized brain that ingests all 5,000 raw logs, correlates them against threat intelligence feeds, normalizes the data, and outputs only 10 consolidated, highly actionable incidents for human review. What is the acronym for this centralized security logging and correlation platform?**
A. SIEM (Security Information and Event Management)
B. SAST (Static Application Security Testing)
C. DLP (Data Loss Prevention)
D. IAM (Identity and Access Management)

#### **9. A company is retiring an old cryptographic key management server. The server contains a single, extremely sensitive "Master Key" (KEK) that was used to encrypt millions of customer records. The new architecture dictates that the old key must never be used again. What is the MOST secure, industry-accepted method for decommissioning this Master Key to ensure the old data it protected can never be decrypted by a future attacker, while leaving the encrypted database files untouched?**
A. Delete the database files.
B. Send the Master Key to a secure offshore backup facility.
C. Key Destruction / Crypto-Shredding (intentionally and permanently destroying the Master Key, rendering all data previously encrypted by it inaccessible forever).
D. Publish the Master Key to the internet.

#### **10. A seasoned incident responder (IR) is drafting the company's official Incident Response Plan. According to standard frameworks like NIST SP 800-61, immediately after the team successfully "Contains" an active ransomware infection (e.g., by unplugging the infected servers from the network), what is the very next formal phase of the incident response lifecycle?**
A. Preparation
B. Detection and Analysis
C. Eradication (Removing the malware, deleting backdoors, and closing the vulnerabilities root cause).
D. Post-Incident Activity (Lessons Learned)

#### **11. A global SaaS provider guarantees its enterprise customers a Service Level Agreement (SLA) of "Four Nines" (99.99%) uptime per year. During operations, the central database server experiences a catastrophic hardware motherboard failure. The system automatically switches over to a standby database within 30 seconds without dropping any active user connections. This rapid recovery ensures the company meets the metric defining the maximum acceptable amount of time the system can be offline after a disaster. What is the formal term for this specific time-based metric?**
A. Recovery Point Objective (RPO)
B. Mean Time to Detect (MTTD)
C. Recovery Time Objective (RTO)
D. Maximum Tolerable Downtime (MTD)

#### **12. The DevOps team implements a rigid release pipeline constraint: any developer attempting to deploy a new version of the microservices suite into the `Production` Kubernetes cluster MUST have their Pull Request digitally signed by at least one Senior Architect and one QA Lead. If these specific cryptographic signatures are missing, the deployment pipeline structurally refuses to execute. What deployment security concept is being enforced here?**
A. Blue/Green Deployment
B. Release Gating / Deployment Approvals
C. Code Obfuscation
D. Chaos Engineering

#### **13. To proactively train the operations team for inevitable, unpredictable production failures, the engineering leadership intentionally unleashes a specialized software bot called "Chaos Monkey" into the live production cloud environment. This bot randomly terminates virtual machines, severs network connections, and crashes database nodes during peak business hours to see if the auto-scaling and failover architectures actually work as designed without human intervention. What advanced operational resilience methodology is this?**
A. Penetration Testing
B. Disaster Recovery Tabletop Exercise
C. Chaos Engineering (Resilience Testing)
D. Regression Testing
