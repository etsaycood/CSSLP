# Exam 3
## Domain 2: Secure Software Lifecycle Management (14 Questions)

**This booklet contains only the questions and options. Please refer to the Answer Booklet for the key and detailed explanations.**

---

#### **1. A highly regulated financial institution is launching a new initiative to build a customer-facing wealth management portal. The Chief Information Security Officer (CISO) establishes a strict policy: Before a single line of code is written or wireframe designed, a specialized cross-functional team must formally document the exact types of sensitive data the application will handle (e.g., PII, financial portfolios), define the regulatory compliance frameworks it must adhere to (e.g., GDPR, PCI-DSS), and classify the overall risk level of the project. Which phase of the Secure Software Development Lifecycle (SSDL) is this critical foundational activity occurring in?**
A. Requirements Specification
B. Project Initiation / Planning Phase
C. Architecture and Design
D. Deployment and Operations

#### **2. A veteran software development team decides to transition from a Traditional Waterfall methodology to an Agile framework (Scrum) to improve time-to-market. The Lead Security Architect is highly concerned about integrating security into this fast-paced environment. To successfully embed security into Agile without becoming a massive bottleneck that universally blocks developers, what is the MOST effective strategic approach the Architect should mandate?**
A. Require a comprehensive, final, two-month-long penetration test at the very end of the project before the first release goes live.
B. Demand that developers write all security requirements into a massive, 500-page document before coding begins.
C. Integrate automated, lightweight security testing tools (like SAST and DAST plugins) directly into the Continuous Integration/Continuous Deployment (CI/CD) pipeline to provide immediate, iterative feedback to developers on every code commit.
D. Assign one dedicated security auditor to manually review every single line of code written during each two-week sprint.

#### **3. An organization relies heavily on offshore development teams to build proprietary software. Recently, several source code repositories were found exposed on a public GitHub server. To drastically reduce the risk of intellectual property theft and malicious code injection by internal developers, the security policy explicitly mandates that all developers are physically barred from saving source code onto their local laptops' hard drives. Instead, they must connect remotely to a centralized, heavily monitored server environment where the IDE and code reside, preventing data exfiltration. What type of security control is this centralized development environment?**
A. Endpoint Detection and Response (EDR)
B. Software Composition Analysis (SCA)
C. Virtual Desktop Infrastructure (VDI) / Secure Remote Development Environment
D. Data Loss Prevention (DLP) Network Appliance

#### **4. A project manager is calculating the budget for a major software rewrite. The security team requests a significant portion of the budget to conduct thorough Threat Modeling and Secure Architecture Reviews during the early Design phase. The project manager, trying to cut costs, suggests skipping these steps and just fixing any bugs found during the final testing phase right before release. According to the foundational principles of Secure Software Lifecycle Management, what is the most scientifically accurate argument the security team should use to definitively reject the project manager's proposal?**
A. Fixing a fundamental architectural security flaw discovered during the final testing or production phase is exponentially more expensive, time-consuming, and difficult than finding and mitigating that exact same flaw on paper during the early design phase.
B. Threat modeling guarantees that the final code will be 100% bug-free.
C. It is illegal under federal law to skip threat modeling.
D. Developers are incapable of fixing bugs found during testing.

#### **5. In defining the Governance, Risk, and Compliance (GRC) framework for a massive software engineering department, the CISO tasks a committee with writing the absolute highest-level, overarching, non-negotiable directive. This single document must formally declare the CEO's absolute commitment to secure coding practices, state the ultimate goals of protecting customer data, and mandate that all software projects must undergo a security review. This document does not contain step-by-step instructions or technology-specific rules. What specific type of governance document is this?**
A. A Standard
B. A Procedure
C. A Guideline
D. A Policy

#### **6. A development team actively maintains a large, cloud-native application. The team explicitly monitors multiple threat intelligence feeds and the National Vulnerability Database (NVD). Upon receiving an immediate alert that a critical Zero-Day Remote Code Execution vulnerability has just been discovered in the exact version of the `Log4j` logging library their application currently uses in production, the team instantly halts all new feature development. They immediately pivot their entire Sprint capacity to ripping out the vulnerable library, applying the official patch, and redeploying the application within 24 hours. This rapid, proactive response is a classic example of which critical lifecycle management process?**
A. Vulnerability Management / Patch Management Lifecycle
B. Change Advisory Board (CAB) approval process
C. Disaster Recovery Tabletop Exercise
D. Software Composition Analysis (SCA) onboarding

#### **7. A global healthcare software vendor is undergoing an arduous external audit. The auditor demands undeniable proof that the vendor possesses a formalized, reliable, and repeatable process for securely wiping all Patient Health Information (PHI) from development databases, securely archiving the final version of the source code, and permanently revoking developers' access permissions to that specific project's repositories once the software product officially reaches its End-of-Life (EOL) and is completely retired. Which final phase of the Secure Software Lifecycle Management is the auditor rigorously investigating?**
A. Incident Response
B. Disposal / Decommissioning / End-of-Life Phase
C. Deployment and Release
D. Maintenance and Operations

#### **8. The release engineering team strictly enforces version control (e.g., Git) for every single artifact associated with an application. This includes the source code, the infrastructure-as-code (Terraform) templates, the database schema migration scripts, and even the README documentation files. If a completely catastrophic deployment accidentally breaks the production database on a Friday night, this fanatical devotion to comprehensively versioning every system artifact ensures the team has the absolute capability to securely perform which critical DevOps operational action?**
A. Initiate a Bug Bounty program.
B. Perform an immediate, reliable Rollback to the exact known-good configuration and codebase from Thursday.
C. Automatically execute a Penetration Test.
D. Obfuscate the broken code from attackers.

#### **9. An organization decides to adopt the foundational concept of defining "Security Champions" embedded directly within the Agile Scrum development teams. What is the primary, strategic purpose of formally designating and training a standard developer to take on the role of a "Security Champion"?**
A. The Security Champion is legally liable if a data breach occurs.
B. To completely replace the need for an independent, centralized Information Security team.
C. To act as a decentralized, localized security advocate who helps their fellow developers write secure code daily, scale security knowledge organically within the dev teams, and serve as the primary liaison bridging the communication gap between the development team and the central security architects.
D. The Security Champion is the only person legally allowed to use automated SAST scanning tools.

#### **10. A massive technology firm mandates that every single software defect, bug, or security vulnerability currently known to exist within their proprietary codebase—from critical SQL injections down to minor cosmetic UI glitches—must be centrally logged, rigorously tracked, assigned a specific owner, categorized by risk severity, and given a definitive target date for remediation. What specific term describes this absolutely essential lifecycle management tracking mechanism?**
A. Threat Modeling Dictionary
B. Bug Tracking / Defect Management System (e.g., Jira, Bugzilla)
C. Configuration Management Database (CMDB)
D. Identity and Access Management (IAM) Registry

#### **11. A government contractor is tasked with building a weapons control system interface. The explicit military contract legally mandates that the software development team MUST adhere strictly to a formalized, highly structured methodology. This methodology demands massive amounts of upfront documentation, rigid, unbending sequential phases (Requirements -> Design -> Implementation -> Testing -> Deployment), and strictly prohibits developers from moving backwards to change a design once the next phase has officially begun. Which classic, highly rigid software development methodology does this perfectly describe?**
A. DevOps
B. Agile Scrum
C. Traditional Waterfall Methodology
D. Extreme Programming (XP)

#### **12. The AppSec team mandates that automated Static Application Security Testing (SAST) tools be configured to run instantly every single time a developer attempts to commit code into the central Git repository. If the SAST tool detects a "Critical" or "High" severity vulnerability (such as a hardcoded API key or an obvious SQL injection syntax), the automated pipeline actively blocks the code commit globally and forces the developer to fix the flaw before the code can be saved. This proactive enforcement mechanism is a textbook implementation of which modern secure development paradigm?**
A. Penetration Testing execution
B. Security "Shift Left" (integrating security controls as early as possible in the development lifecycle)
C. Security through Obscurity
D. Red Teaming

#### **13. During a routine software audit, a security analyst discovers that the production web server contains three "temporary" backdoor testing scripts (`test_db_connect.php`, `bypass_auth_v2.php`, and `dev_dump.php`). The lead developer admits they wrote these scripts two years ago to troubleshoot a frustrating login bug locally, accidentally checked them into the version control system, and completely forgot to remove them before the application was shipped to production. Which critical lifecycle management control completely failed to catch this glaring error?**
A. Fuzz Testing
B. Code Review / Peer Review process
C. Data Loss Prevention (DLP)
D. Web Application Firewall (WAF) deployment

#### **14. A highly regulated financial exchange is implementing a strict Governance, Risk, and Compliance (GRC) framework for all internal software projects. The policy states that every application must undergo a formal, documented, independent assessment by the internal audit team before it is legally allowed to connect to the live production network and process real customer stock trades. The audit team relies on a comprehensive checklist to verify that all required security controls (encryption, logging, access control) are not only designed correctly but are operating effectively in the staging environment. What formal lifecycle milestone is the application attempting to achieve?**
A. Continuous Integration (CI)
B. Threat Modeling Sign-Off
C. Authorization to Operate (ATO) / Final Security Certification and Accreditation
D. Disaster Recovery Declaration
