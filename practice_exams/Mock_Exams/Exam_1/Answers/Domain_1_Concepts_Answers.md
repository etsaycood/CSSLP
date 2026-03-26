# 第一套全真模擬試題 (Exam 1) - 答案與詳解本
## 領域 1：安全的軟體概念 (Secure Software Concepts) (16題)

---

#### **1. A critical legacy web application handles real-time financial trading. The development team is tasked with implementing a new feature that temporarily elevates a user's privileges to bypass standard transaction limits during market volatility. The security team is concerned that this mechanism could fail open if the supporting authorization microservice crashes. As a secure software designer, what is the FIRST principle you should enforce to address this specific concern?**
**(一個關鍵的傳統 Web 應用程式負責處理即時金融交易。開發團隊的任務是實作一項新功能，在市場劇烈波動期間暫時提升使用者的權限，以繞過標準交易金額上限。資安團隊擔心，如果負責支援這項授權的微服務當機崩潰，這個機制可能會預設呈現門戶洞開 (Fail Open)。身為一位安全的軟體設計師，為了解決這個特定的擔憂，您應該強制執行的「最優先 (FIRST)」原則是什麼？)**
A. Implement Complete Mediation to ensure the bypass authorization is checked on every single trade request. (實作徹底中介)
B. Ensure the mechanism follows the Fail Secure principle by defaulting to standard transaction limits if the microservice is unresponsive. (確保該機制遵循預設失效安全原則)
C. Apply the Least Common Mechanism principle by isolating the bypass service on a dedicated server. (應用最少共用機制)
D. Enforce Separation of Duties by requiring two different executives to approve the temporary elevation. (強制執行職責分離)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最優先/最佳選擇：** 這個情境明確點出了一個關於授權微服務「當機崩潰」的擔憂，以及系統可能會因此「預設呈現門戶洞開 (failing open)」的致命風險。**預設失效安全 (Fail Secure / Fail Safe)** 原則規定，當一個系統或其安全組件發生故障時，它必須全自動地退回到一個「安全的」狀態。在這個金融交易的背景下，安全狀態就是直接拒絕特權提升，並強制防守較低的標準交易上限。
    *   **為何 A 是干擾項：** 徹底中介 (Complete Mediation) 在技術上確實要求檢查所有請求。但它並未規定當「負責檢查的機制死機時」該如何反應。
    *   **為何 D 是干擾項：** 職責分離 (Separation of Duties) 是核准特權提升的最佳實踐。但情境中眼前的直接威脅是「微服務當機會發生什麼事 (系統故障行為)」，這使得「預設失效安全」成為首要原則。
    *   **為何 C 是干擾項：** 最少共用機制 (Least Common Mechanism) 主張減少共享資源防止 DoS，但不能解決授權檢查掛點時的邏輯預設路徑。

#### **2. A multinational healthcare provider is designing a patient portal. The marketing department insists on collecting and indefinitely retaining detailed user browsing behavior to personalize health product recommendations. The Legal/Compliance department points out that under GDPR and HIPAA, patients must give explicit consent and have the right to request deletion of this non-essential data. The Chief Information Security Officer (CISO) is brought in to arbitrate. What is the fundamental Governance, Risk, and Compliance (GRC) concept that dictates the CISO's decision?**
**(一家跨國醫療保健供應商正在設計一個病患入口網站。行銷部門堅持要在網站上收集並無限期保留詳細的行為數據。法務與法規遵循部門指出，根據 GDPR 與 HIPAA，病患必須給予明確同意並有權刪除此非必要數據。CISO 被請來仲裁。請問是哪一個基礎的 GRC 概念決定了 CISO 的決策？)**
A. Business alignment dictates that revenue-generating marketing initiatives take precedence over internal policies. (業務一致性)
B. Risk Avoidance requires that the portal does not collect any browsing data whatsoever. (風險規避)
C. Legal and Regulatory compliance requirements supersede internal business goals and desires. (法律和法規遵循要求凌駕於內部商業目標之上)
D. The psychological acceptability of the portal will be reduced if users are burdened with consent forms. (心理可接受度)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 在 GRC 體系中，**法律和法規遵循要求 (Regulatory and Legal compliance requirements)** 具備絕對強制力，永遠凌駕於商業渴望或行銷戰略之上。違反 GDPR 或 HIPAA 會招致毀滅性罰款，CISO 必須強制壓下行銷團隊的斂財渴望以確保合規。
    *   **為何 A 是干擾項：** 資安應當支持業務目標 (Business alignment)，但「絕不能違法」。能賺錢的專案不能當成公然違背法規的擋箭牌。
    *   **為何 B 是干擾項：** 風險規避 (Risk Avoidance) 在此太過極端。組織不需為了怕犯法就「完全不收資料」；只要導入「同意與刪除機制」來滿足法律要求 (風險緩解) 即可。
    *   **為何 D 是干擾項：** 心理可接受度 (Psychological Acceptability) 指安全應減少使用者摩擦。但面臨強制性法律規定時，不能用「使用者會覺得煩」來逃避合規責任。

#### **3. An architect is designing a heavily encrypted storage system for a government contractor. The objective is to ensure that even if the source code of the proprietary encryption software is stolen by a nation-state attacker, the encrypted data remains entirely secure. The architect decides against writing a custom obfuscation algorithm and instead utilizes standard AES-256 in GCM mode. This architectural decision is primarily driven by which established security principle?**
**(一名架構師正在為國防承包商設計高度加密儲存系統。目標是確保：即使專有加密軟體的原始碼被國家級駭客偷走，加密資料依然絕對安全。為此，他決定不客製混淆演算法，而是採用標準 AES-256。這項決策主要受哪一項原則驅使？)**
A. Defense in Depth (縱深防禦)
B. Economy of Mechanism (機制經濟)
C. Open Design (開放式設計)
D. Leveraging Existing Components (利用現有組件)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 情境聚焦於：「即使原始碼(設計演算法)被敵人偷走，系統依然安全」。這是 **開放式設計 (Open Design / 克爾克霍夫原則)** 的完美定義：安全機制的強大不應建立在設計保密上，而應只建立在金鑰的安全上。
    *   **為何 D 是干擾項：** 利用現有組件的確是個好實踐。然而，「開放式設計」才是驅動這個選擇背後的核心信仰。採用現有組件是為了「達成」開放式設計的安全目標。
    *   **為何 A 與 B 是干擾項：** 縱深防禦 (Defense in Depth) 討論多層次控制；機制經濟 (Economy of Mechanism) 強調簡單。兩者都沒有直接回答「為何失去原始碼系統卻還能安全」的命題。

#### **4. You are evaluating a proposal for a new Identity and Access Management (IAM) service. The vendor claims their system employs "Zero Trust architecture." To substantiate this claim, the system mandates that every single data access request—even from previously authenticated users originating from within the corporate LAN—must be explicitly verified against current authorization policies. Which core security design principle is this system actively demonstrating?**
**(您正在評估一份新 IAM 服務提案。供應商聲稱採用「零信任架構」。為佐證此說法，系統強制規定：每一次的資料存取請求——即使來自區域網路內部且驗證過的已知用戶——都必須被明確重新驗證。請問該系統正在展示哪一項核心安全設計原則？)**
A. Least Privilege (最小權限)
B. Complete Mediation (徹底中介)
C. Separation of Duties (職責分離)
D. Non-repudiation (不可否認性)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **徹底中介 (Complete Mediation)** 規定每一次的存取請求都必須接受驗證，禁止依賴存取的快取結果。這種「每次必查」的技術原則，正是「零信任架構 (Zero Trust)」背後最硬核的地基。
    *   **為何 A 是干擾項：** 最小權限 (Least Privilege) 規定權限的「大小」，而不是規定「驗證的頻率與強制性」。
    *   **為何 C 與 D 是干擾項：** 職責分離要求多人協作防弊；不可否認性透過日誌留存證據。這兩者皆非描述「持續攔截與驗證存取請求」的動作。

#### **5. A financial software development team is performing a quantitative risk analysis on a newly discovered vulnerability in their payment gateway. They estimate the vulnerability could be exploited once a year (ARO = 1.0). If exploited, the breach would cost the company $500,000 in fines and lost revenue (SLE = $500,000). A proposed Web Application Firewall (WAF) rule could mitigate this vulnerability completely, but the enterprise WAF license and maintenance cost $600,000 annually. Based strictly on quantitative risk management, what is the BEST recommendation?**
**(金融開發團隊正進行量化風險分析。某漏洞每年可能被利用一次(ARO=1.0)，若外洩將損失$500,000(SLE)。提議購買的 WAF 規則能完全阻擋此漏洞，但 WAF 年費為 $600,000。基於量化風險管理邏輯，最佳建議為何？)**
A. Implement the WAF rule immediately because the Single Loss Expectancy (SLE) is unacceptably high. (立即實施 WAF，因為 SLE 過高)
B. Accept the risk, as the Annualized Loss Expectancy (ALE) is lower than the cost of the control. (接受風險，因為 ALE 低於控制成本)
C. Transfer the risk by purchasing cybersecurity insurance, regardless of the premium cost. (購買保險轉移風險)
D. Mitigate the risk using the WAF, as protecting financial data supersedes cost-benefit analyses. (因為保護金融資料義務超越成本考量而使用 WAF)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 量化風險公式：ALE = ARO × SLE。此情境中，ALE = 1.0 × $500,000 = $500,000/年。風險管理金科玉律是：防護控制措施的成本絕對不能超過預期損失 (ALE)。因為 WAF 每年花 60 萬，卻只擋下 50 萬的潛在損失，導致公司每年淨虧損 10 萬。基於財務邏輯，現階段的最佳決策是 **接受風險 (Risk Acceptance)**（或尋找更便宜的方案）。
    *   **為何 A 與 D 是干擾項：** 這兩個選項充滿道德正義感，但完全違背了「量化評估」的冷血算術。盾牌不該比它要防禦的災難還要昂貴。
    *   **為何 C 是干擾項：** 雖說轉移風險 (購買保險) 是個好選項，但「不惜代價購買 (regardless of premium cost)」同樣踩了超支地雷，違背成本效益。

#### **6. A development team lead notices that developers are routinely hardcoding database credentials directly into the application's source code to speed up local testing. When confronted, the developers state that setting up a secure local secrets manager takes too much time and breaks their workflow. The team lead decides to implement an automated script that securely injects lightweight, temporary database credentials into the developers' environments upon startup without any manual configuration. Which security design principle is the team lead primarily honoring?**
**(主管注意到開發者常將資料庫密碼寫死在原始碼中以加速測試。開發者抱怨設定安全密碼管理器太花時間。於是主管寫了一支腳本，能在啟動時全自動將臨時憑證安全注入開發環境，無需手動設定。主管主要是為了擁護哪一項原則？)**
A. Fail Secure (預設失效安全)
B. Psychological Acceptability (心理可接受度)
C. Open Design (開放式設計)
D. Least Common Mechanism (最少共用機制)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **心理可接受度 (Psychological Acceptability / 易用性)** 警告我們：如果安全機制太難用、增加工作摩擦，人類天性就會主動繞過它（如寫死密碼）。主管透過自動化腳本，讓「最安全的做法」變成了「最輕鬆順暢的做法」，完美實踐了易用性精神。
    *   **為何 A、C、D 是干擾項：** 預設失效安全與系統當機行為有關；開放式設計關注演算法公開度；最少共用機制關注隔離與防禦 DoS，均與改善人類操作流程的心理阻力無直接關聯。

#### **7. An organization processes millions of highly sensitive biometric records. To enhance security, the architecture mandates that the front-end web tier is completely physically and logically separated from the back-end database tier. The tiers are separated by a strict firewall, an API gateway, and an Intrusion Prevention System (IPS). An attacker who manages to compromise the web tier cannot directly access the database. Which architectural concept does this best represent?**
**(組織處理極度敏感的生物紀錄。為強化安全，架構規定前端 Web 與後端資料庫必須物理與邏輯分離。兩層之間被防火牆、API 閘道與 IPS 隔開，攻陷 Web 層的駭客無法直接碰觸資料庫。這幅圖最代表哪一個概念？)**
A. Defense in Depth (縱深防禦)
B. Complete Mediation (徹底中介)
C. Component Reuse (組件重複使用)
D. Separation of Duties (職責分離)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **縱深防禦 (Defense in Depth / 多層次安全)** 的精髓是部署多重、重疊的安全控制。情境描述了多層次架構（分離網段、防火牆、閘道、IPS），即使第一層防線（Web 伺服器）被突破，後方的陣地依然能保護核心資產。
    *   **為何 B 是干擾項：** 儘管 API 閘道可能執行徹底中介（查驗每一次請求），但整體「多重關卡與區域隔離」的拓撲視覺描述，是在闡述縱深防禦的宏觀概念。
    *   **為何 D 是干擾項：** 職責分離是為人類主體設計的業務防弊原則，而非網路架構原則。

#### **8. A software development firm has recently acquired a smaller startup. The startup's flagship application is highly profitable but consists of overly complex, monolithic, "spaghetti" code that has not been securely maintained. The acquiring firm decides to isolate this legacy application on a segregated virtual network and restricts access to it, rather than attempting to review, refactor, and patch the millions of lines of complex code. This decision is predominantly an acknowledgment of which security principle?**
**(軟體公司收購了一家新創，其主力程式是由極度複雜、龐大且未受保護的「義大利麵條程式碼」組成。公司決定將其隔離在虛擬網路上並限制存取，而非嘗試去審查修補這幾百萬行複雜程式碼。此隔離決策主要承認了哪項原則的破滅？)**
A. Open Design (開放式設計)
B. Fail Safe Defaults (預設失效安全)
C. Economy of Mechanism (機制經濟)
D. Complete Mediation (徹底中介)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **機制經濟 (Economy of Mechanism / KISS 原則)** 規定系統設計必須盡可能簡單小巧。過度龐大複雜的系統（義大利麵條程式碼）天生就是隱藏漏洞的溫床，極難被審查與保護。資安團隊將其隔離，就是因為這套系統的複雜度違背了機制經濟原則，導致它根本「無法被治癒與修補」。
    *   **為何 A、B、D 是干擾項：** 這些原則都不是用來批判系統因「程式碼規模過於龐大複雜」而導致無法維護的禍根。

#### **9. During the design of a globally distributed ledger system, architects realize that because all nodes are equally privileged and lack a central authority, an attacker compromising a small number of nodes could inject fraudulent ledgers. To combat this, they design a consensus algorithm that relies on cryptographic hashing and requires a mathematical proof-of-work from a majority of nodes to validate any transaction. What is the fundamental security requirement this design is trying to achieve?**
**(在設計分散式帳本(區塊鏈)時，由於節點平等且無中央權威，駭客若攻陷小撮節點便可注入偽造帳本。為對抗它，團隊設計了依賴密碼學雜湊與過半數節點算力證明的共識演算法。這主要想達成哪項安全需求？)**
A. Availability (可用性)
B. Confidentiality (機密性)
C. Non-repudiation (不可否認性)
D. Integrity (完整性)

*   **正確答案 / Correct Answer：D**
*   **[解析邏輯]**
    *   **為何 D 是最佳選擇：** **完整性 (Integrity)** 保證資料未被未授權竄改。共識演算法與密碼學雜湊的核心目的，就是防止那群被駭客操控的節點將「偽造、虛假」的交易寫入龐大的分類帳中。防堵竄改與偽造正是捍衛完整性。
    *   **為何 C 是干擾項：** 不可否認性是此架構的重要副產品。但情境中首要抗擊的威脅是「注入假帳本 (fraudulent ledgers)」，防禦假資料寫入，保證全域狀態準確無誤是完整性的責任。
    *   **為何 A 與 B 是干擾項：** 機密性與此無關(帳本多為公開)；高算力的工作量證明是為了辨別資料真偽，反而某種程度上會降低交易處理的可用速度。

#### **10. A cloud-native application uses a microservices architecture. Service A (Inventory) frequently requests data from Service B (Pricing). Originally, both services shared the same physical memory space on a monolithic server. Now, they communicate over an internal API. An architect discovers that a vulnerability in Service A is being used to conduct a Denial of Service (DoS) attack, exhausting the shared Redis cache that both Service A and Service B use to store temporary data, taking both services offline. What design principle was violated here?**
**(微服務架構中，庫存服務A 頻繁向 定價服務B 請求資料。雖然拆分為微服務，但架構師發現，駭客利用服務A 的漏洞發動 DoS 攻擊，竟然榨乾了兩者「共用的」Redis 快取，導致服務A和B 雙雙斷線。這違背了哪項設計原則？)**
A. Defense in Depth (縱深防禦)
B. Least Common Mechanism (最少共用機制)
C. Fail Secure (預設失效安全)
D. Open Design (開放式設計)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **最少共用機制 (Least Common Mechanism)** 警告：多個元件若共用同一依賴機制，將容易產生交叉干擾與級聯失效。因為服務A 服務B 共用了同一座 Redis 快取（這就是共用機制），服務A 的過載立刻連累了原本毫無漏洞的服務B，完美展示了違背此隔離原則的慘痛下場。
    *   **為何 A 是一般性干擾項：** 雖說防線被攻破是縱深防禦的失敗，但導致這場「雙殺」的特定架構罪魁禍首，精準指向了「共用快取」。

#### **11. An enterprise creates an Acceptable Use Policy (AUP) that forbids developers from using external, unvetted generative AI tools to write code for the company's proprietary trading algorithms. A developer inadvertently uploads a highly confidential algorithm to a public AI chatbot to debug an error. This incident represents a failure in which aspect of the CIA triad, and what is the classification of the countermeasure that failed?**
**(企業頒布《可接受使用政策, AUP》，禁止將高機密商業演算法上傳給未審查的生成式 AI。一開發者為除錯不慎將演算法傳給了公開的人工智慧平台。此事件代表 CIA 中哪個面向崩潰？且該被違背的 AUP 屬於何種控制措施分類？)**
A. Confidentiality; Administrative Control (機密性；管理控制)
B. Integrity; Technical Control (完整性；技術控制)
C. Availability; Physical Control (可用性；實體控制)
D. Confidentiality; Technical Control (機密性；技術控制)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 將專有演算法無意間分享到公開平台是嚴重的資料外洩，即 **機密性 (Confidentiality)** 的崩潰。《可接受使用政策 AUP》是一份紙本的規定集，用來約束人類行為，它屬於最典型的 **管理層次控制措施 (Administrative Policy Control)**。
    *   **為何 D 是干擾項：** D 的機密性對了。但在分類上，AUP 是政策而非「技術」。若是防火牆或 DLP 軟體失敗讓程式碼漏出去，才叫技術控制的失敗。

#### **12. A CISO is reviewing a risk assessment for a new legacy system migration. The assessment identifies an outdated, unpatchable protocol in use that carries a "High" risk rating due to known exploits. Because the system is critical to production line stability, the CISO decides the company cannot simply turn it off (avoidance). Furthermore, no insurance company will cover a known vulnerability (transference). Management signs a formal memo acknowledging they will absorb the financial impact if a breach occurs, while the IT team builds a 2-year plan to replace the system. Which risk treatment strategy has been adopted?**
**(針對無法修補的舊系統高風險，CISO 不能關機(規避)，也買不到保險(移轉)。高層簽了一份備忘錄：長官們願意「自行吸收」萬一系統被駭時的財務損失。與此同時 IT 團隊制定了 2 年後替換系統的計畫。在簽備忘錄的當下，採取了何種風險策略？)**
A. Risk Mitigation (風險緩解)
B. Risk Acceptance (風險接受)
C. Risk Avoidance (風險規避)
D. Risk Transference (風險移轉)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 當高層簽署文件，決定在不增設技術防護的情況下繼續維持這台高危險老班底運轉，並承諾「後果自負」時，他們採取的正式姿態就是 **風險接受 (Risk Acceptance)**。
    *   **為何 A 是干擾項：** 雖然有「兩年後的替換計畫」，但在接下來的 700 多天裡，這台機器的漏洞並未被立即消除或部署防禦盾牌。因此當下他們擁抱的是接受策略，因為他們連緩解防火牆都沒架。

#### **13. A biometric access system is engineered for a high-security military laboratory. The designers explicitly configure the system to prioritize denying access to legitimate personnel if there is even strict minor deviation in the biometric scan (e.g., a dirty finger), rather than risk allowing an unauthorized impostor inside. In biometric terminology, this design deliberately accepts a high:**
**(高安全級別的軍事生物辨識門禁。設計師故意設定：即使是指紋有點髒的「合法將領」，系統也會優先拒絕讓他進門。因為他們寧可錯殺，也絕不漏放任何敵軍間諜入內。用術語來說，他們刻意且大膽地拉高了哪項數值？)**
A. False Acceptance Rate (FAR - 錯誤接受率)
B. Crossover Error Rate (CER - 交叉錯誤率)
C. False Rejection Rate (FRR - 錯誤拒絕率)
D. Clipping Level (削波位準)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **錯誤拒絕率 (FRR, Type I 錯誤)** 是把好人當壞人擋在門外的機率。設計師為了安全，調高靈敏度，故意犧牲合法使用者的便利性（導致 FRR 飆高），這一切都是為了將「讓壞人進入」的風險壓到最低。
    *   **為何 A 是干擾項：** FAR 是將壞人放進來的機率。這是高防衛模式下最需要不惜一切代價消滅的數值。

#### **14. User provisioning for an internal corporate web portal is automated. When an active directory user is placed into the `IT_Admins` group, they automatically receive administrative capabilities within the web portal via a nightly synchronization script. An auditor discovers that when a user is demoted and removed from the `IT_Admins` group, their administrative rights in the web portal are *not* automatically revoked because the synchronization script only handles additions, not deletions. This violates which foundational security principle?**
**(自動網站權限派發系統：當你加入 `IT_Admins` 群組，半夜腳本會自動開通。但稽核發現：被降級移出 `IT_Admins` 的老員工，他的入口網站管理員權限卻「不會被抽掉」，因為腳本沒寫刪除邏輯。這項「殘留特權」違背了哪項原則？)**
A. Need to Know (需知原則)
B. Defense in Depth (縱深防禦)
C. Separation of Duties (職責分離)
D. Least Privilege (最小權限)

*   **正確答案 / Correct Answer：D**
*   **[解析邏輯]**
    *   **為何 D 是最佳選擇：** **最小權限 (Least Privilege)** 要求使用者手中只應握有執行當下任務所必須的底限權限。那些被降職的人卻依舊享有不需要的最高權限（業界稱之為 Privilege Creep 權力蠕變），是對最小權限原則最直接的褻瀆。
    *   **為何 A 是干擾項：** 需知原則偏向靜態的機密資訊保護（你沒資格看這份文件）。最小權限涵蓋範圍更廣，包括可執行動作的行政權能。殘留管理員權限屬於最小權限管轄範疇。

#### **15. A software organization adopts a policy that states: "Whenever a data field is no longer required to support a valid business transaction or legal retention mandate, it must be permanently purged from all production databases and backups within 30 days." This policy directly addresses which aspect of information lifecycle management?**
**(組織頒布政策：「當資不再需要支援商業交易或已超過法律保留年限時，必須在 30 天內從所有資料庫與備份磁帶中被永久徹底抹滅。」這直接命中資訊生命週期的哪個環節？)**
A. Data Classification (資料分類標記)
B. Data Disposal (資料處置 / 銷毀)
C. Data Archiving (資料封存歸檔)
D. Data Collection Minimization (資料收集最小化)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **資料處置 (Data Disposal / Destruction)** 是資訊生命週期的最終站。政策中下達的「永久徹底抹滅 (permanently purged)」，精準符合資料在耗盡剩餘價值後，執行物理或邏輯銷毀的定義。
    *   **為何 C 是干擾項：** 封存與歸檔是將不常使用的資料移到便宜倉庫「保留下來」，而不是將其刪除。

#### **16. An application developer implements a "Remember Me" functionality. Instead of storing the user's secure password in a cookie, the developer generates a random, cryptographically strong token, stores its hash in the backend database, and places the plaintext token in a browser cookie. This implementation strategy specifically mitigates the risk of exposing the original credential. Which principle does this implementation represent?**
**(實作「記住我功能」時，開發者沒有直接把密碼塞進 Cookie，而是生成一串高強度隨機代碼(Token)，將其雜湊存於後端，並將明碼代碼放進瀏覽器 Cookie。用代碼替換真密碼的手法，體現了哪種原則？)**
A. Tokenization (代碼化)
B. Encryption (加密)
C. Economy of Mechanism (機制經濟)
D. Complete Mediation (徹底中介)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **代碼化 (Tokenization)** 是一種以假亂真的替身防禦。它使用一個毫無數學意義、無法被還原的假鈔 (隨機生成的 Token) 去前線執行認證任務，藉此完全避免真實的機敏資料 (密碼) 暴露在高風險的瀏覽器 Cookie 中。
    *   **為何 B 是干擾項：** 加密是一道擁有鑰匙就能逆轉還原的數學算式。而 Token 代碼本身就是一段無意義亂數，沒有任何數學公式能把它「解密」回真正的密碼。
