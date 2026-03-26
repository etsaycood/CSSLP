# Domain 2: Secure Software Lifecycle Management (14 Questions)

#### **1. A software development team is tasked with adopting a new Secure Software Development Lifecycle (SSDLC). Rather than creating a custom framework, the security director mandates the use of the Software Assurance Maturity Model (SAMM). What is the PRIMARY benefit of using an established model like SAMM?**
A. It provides automated tools for static code analysis.
B. It offers a measurable, structured approach to assessing and improving software security practices.
C. It eliminates the need for manual code review.
D. It guarantees compliance with the Payment Card Industry (PCI) standard.

*   **Answer: B**
*   **Rationale:** Frameworks like OWASP SAMM or BSIMM provide a **measurable, structured approach** defining maturity levels for different security activities. It does not provide automated tools yourself, nor guarantee specific PCI compliance or eliminate manual review.

#### **2. An organization is integrating security into its Agile development methodology. Which of the following approaches is MOST effective for ensuring security is addressed without significantly disrupting the sprint velocity?**
A. Conducting a comprehensive penetration test at the end of every 2-week sprint.
B. Embedding a security champion within the development team and integrating security user stories.
C. Delaying all security testing until the final release candidate is prepared.
D. Requiring the CISO to manually approve every code commit.

*   **Answer: B**
*   **Rationale:** In Agile, security must keep pace with rapid development. **Embedding security champions** (developers with security training) and using **security user stories** (evil user stories) natively integrates security into the ongoing workflow, avoiding the bottleneck of heavy end-of-stage gates.

#### **3. During the release pipeline, a software build is automatically halted because a static analysis tool detected hardcoded administrative credentials in the source code. This automated halting is an example of which roadmap strategy?**
A. Key Performance Indicator (KPI)
B. Feedback Loop
C. Control Gate (Break/Build Criteria)
D. Incident Response Plan

*   **Answer: C**
*   **Rationale:** A **Control Gate** (or Break/Build Criteria) establishes a security milestone. If the software does not meet the predefined criteria (e.g., no hardcoded credentials), the pipeline "breaks," preventing the insecure code from progressing to the next stage.

#### **4. A project manager is defining security metrics for an upcoming application. Which of the following is an example of a good Key Performance Indicator (KPI) for the secure software lifecycle?**
A. The total number of firewalls deployed in the staging environment.
B. The average remediation time for critical vulnerabilities discovered during testing.
C. The number of developers who have read the company security manual.
D. The exact monetary value of the data stored in the database.

*   **Answer: B**
*   **Rationale:** A KPI must be a measurable value demonstrating how effectively an objective is achieved. **Average remediation time** directly measures the efficiency of the vulnerability management process.

#### **5. A company is shutting down an old HR application and migrating to a new cloud-based SaaS platform. As part of the End of Life (EOL) policy, what is the MOST critical security activity regarding the old application's data?**
A. Re-encrypting the data with a newer algorithm before leaving it on the old server.
B. Maintaining the old server's active network connection indefinitely for reference.
C. Executing secure data disposition, including retention of necessary records and verifiable destruction of the rest.
D. Revoking all user interface licenses for the old application.

*   **Answer: C**
*   **Rationale:** Proper **Data Disposition** during decommissioning outlines exactly what data must be retained (archived for legal/compliance reasons) and ensures the irretrievable **destruction** (sanitization/crypto-shredding) of data that is no longer needed, preventing data leaks from orphaned systems.

#### **6. A development team wants to push a major update to production. Before this can happen, the Information System Owner (ISO) and the Security Officer must formally review the residual risks and sign an official document accepting those risks. This describes which process?**
A. Agile Sprint Retrospective
B. Incident Response Triage
C. Assessment and Authorization (A&A)
D. Common Vulnerability Scoring System (CVSS)

*   **Answer: C**
*   **Rationale:** The **Assessment and Authorization (A&A)** process (often seen in NIST RMF) is the formal management process where a system is assessed for risk, and an authorizing official formally grants the Approval to Operate (ATO) by accepting the residual risk.

#### **7. When deciding whether to implement a highly complex, expensive security control to mitigate a newly discovered vulnerability, executive management conducts a cost-benefit analysis. They weigh the cost of the control against the potential financial loss if the vulnerability is exploited. This activity balances:**
A. Technical risk vs. Business risk
B. Qualitative vs. Quantitative metrics
C. Least Privilege vs. Complete Mediation
D. End of Life (EOL) vs. Data Disposition

*   **Answer: A**
*   **Rationale:** This scenario represents balancing **Technical risk** (the vulnerability itself) against **Business risk** (the financial cost of the control vs. the cost of a breach). Business risk ultimately determines whether a technical risk is mitigated or accepted.

#### **8. A developer accidentally commits a valid AWS access key to a public GitHub repository. Within minutes, attackers find the key and spawn thousands of unauthorized cryptocurrency mining servers. Which established practice should dictate the organization's immediate steps to contain, eradicate, and recover from this event?**
A. Risk Assessment Methodology
B. Change Management Process
C. Incident Response Plan
D. Software Assurance Maturity Model

*   **Answer: C**
*   **Rationale:** An **Incident Response (IR) Plan** provides the structured procedures for identifying, containing, eradicating, and recovering from a security breach.

#### **9. An organization performs an annual review of its software development processes. They find that developers are frequently bypassing security checks to meet tight deadlines. To address this sustainably and align with an SDLC, what is the BEST course of action?**
A. Fire the developers who bypassed the checks.
B. Implement security awareness training and create automated, frictionless security reporting mechanisms.
C. Remove the security checks from the SDLC entirely.
D. Shift all security testing to the Quality Assurance (QA) team at the end of the lifecycle.

*   **Answer: B**
*   **Rationale:** Bypassing security usually indicates the controls are too intrusive (lack of psychological acceptability) or developers lack awareness. **Promoting security awareness** and building frictionless, automated **feedback loops** (reporting mechanisms) integrates security sustainably.

#### **10. An architect is reviewing the integrated risk management methods. A component of the application processes credit card payments. The architect must ensure the system adheres to the Payment Card Industry Data Security Standard (PCI DSS). In the context of risk management, PCI DSS is classified as a:**
A. Legal regulation
B. Threat Intelligence feed
C. Software vulnerability framework
D. Industry standard

*   **Answer: D**
*   **Rationale:** PCI DSS is an **Industry standard** mandated by major credit card brands, not a governmental law or legal regulation (though failing to comply carries severe financial penalties and loss of processing privileges).

#### **11. During the decommissioning of a legacy application, the security team discovers several service accounts used by the app still possess read/write access to the core enterprise database. What End of Life (EOL) policy was improperly executed?**
A. Data Retention
B. License Cancellation
C. Credential Removal
D. Archiving

*   **Answer: C**
*   **Rationale:** **Credential Removal** (or revoking service accounts and access rights) is a critical step in decommissioning. "Orphaned" service accounts from dead applications are a prime target for attackers seeking to escalate privileges.

#### **12. A security analyst is analyzing the impact of a vulnerability and determining its likelihood of exploitation based on current threat actors. This specific activity is best described as:**
A. Risk Assessment
B. Continuous Integration
C. Change Management
D. Assessment and Authorization

*   **Answer: A**
*   **Rationale:** **Risk Assessment** (and Risk Analysis) is the process of identifying vulnerabilities, evaluating the threat landscape, and determining the likelihood and impact (the risk) to the organization.

#### **13. To ensure that developers understand the current security posture of their applications, a security team sets up a portal displaying real-time metrics on open vulnerabilities, time-to-fix ratios, and static analysis scan results. This portal serves as a:**
A. Change Management Board
B. Security Dashboard / Reporting Mechanism
C. Break/Build control gate
D. SLA contract

*   **Answer: B**
*   **Rationale:** **Security Dashboards and Reporting mechanisms** provide visibility and feedback loops, allowing teams to monitor KPIs and track their security maturity over time.

#### **14. When implementing secure operation practices, a developer requests to deploy an urgent patch to a production server on a Friday night without submitting a ticket, claiming it fixes a critical bug. Why must the organization enforce the Change Management Process instead?**
A. To ensure the developer gets paid for overtime.
B. To prevent unauthorized, undocumented changes that could cause an outage or introduce new vulnerabilities.
C. Because Agile methodology prohibits Friday deployments.
D. To trigger the Incident Response plan automatically.

*   **Answer: B**
*   **Rationale:** The **Change Management Process** ensures that all modifications to production environments are reviewed, authorized, documented, and tested, preventing uncontrolled changes that can compromise availability and security.
