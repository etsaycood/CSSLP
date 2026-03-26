# 領域 3：安全的軟體需求 (Secure Software Requirements) (16題)

#### **1. 一名商業分析師正在記錄一個新電子商務應用程式的需求。其中一項需求寫道：「系統必須使用 TLS 1.3 對所有信用卡交易進行加密。」這種需求最適合被歸類為：**
A. 功能性需求 (A functional requirement)
B. 非功能性安全需求 (A non-functional security requirement)
C. 法規遵循需求 (A compliance requirement)
D. 功能性使用案例 (A functional use case)

*   **答案：B**
*   **解析：** 「使用 TLS 1.3 對所有交易進行加密」規定的是系統應「如何 (how)」保護資料 (傳輸中的機密性)，而不是系統執行的具體商業動作 (what)。這屬於**非功能性安全需求**。功能性需求定義了系統能「做什麼」(例如：「系統必須能處理這筆付款」)。

#### **2. 一家跨國企業正在建置一個針對歐盟 (EU) 與加州客戶的雲端應用程式。下列哪一項法規遵循需求，強制規定必須明確定義「資料蒐集範圍 (Data Collection Scope)」並賦予用戶「被遺忘權 (Right to be Forgotten) / 刪除權」？**
A. 支付卡產業資料安全標準 (PCI DSS)
B. 聯邦資訊安全管理法案 (FISMA)
C. 一般資料保護規則 (GDPR)
D. 健康保險便利和責任法案 (HIPAA)

*   **答案：C**
*   **解析：** 歐盟的 **一般資料保護規則 (GDPR)** 具有極其嚴格的隱私控制強制力，包含了強制最小化資料蒐集範圍，並直接賦予歐盟公民行使「被遺忘權」(要求企業執行資料徹底銷毀) 的權利。

#### **3. 在收集醫療資料入口網站需求的階段，資料擁有者 (Data Owner) 決定將患者的過往病歷歸類為「高敏感度 (High Sensitivity)」，且一旦外洩將面臨「高衝擊 (High Impact)」。這種根據敏感度指派標籤的過程被稱為：**
A. 資料匿名化 (Data Anonymization)
B. 資料處理 (Data Handling)
C. 資料標記 / 標籤化 (Data Labeling)
D. 風險接受 (Risk Acceptance)

*   **答案：C**
*   **解析：** **資料標記 (Data Labeling)** 是一種行為，根據資料在未經授權的披露、修改或銷毀時將會對組織構成的衝擊程度，為資料貼上或標記特定的分類等級 (例如：「高敏感」、「機密 (Confidential)」)。

#### **4. 一個組織正在彙整龐大的消費者行為數據集，用來訓練新的 AI 模型。為了保護個別消費者的隱私，資料團隊從數學層面上對資料集進行了修改，確保即使將該資料集與外部其他公開數據交叉比對，也永遠無法反向追蹤回或辨識出任何一位原始的消費者。這種極致的隱私保護手段稱為：**
A. 完全匿名化 (Data Anonymization - Fully Anonymous)
B. 個資處理程序 (Data Handling - PII)
C. 假名化 / 虛擬匿名化 (Pseudo-anonymization)
D. 代碼化 (Tokenization)

*   **答案：A**
*   **解析：** **完全匿名化的資料 (Fully Anonymous data)** 已經永久且不可逆地移除了所有個人可識別資訊 (PII)，從數學上保證了「重新識別 (re-identification)」是絕對不可能發生的。**假名化 (Pseudo-anonymization)** 則是用虛擬標籤替換直接識別碼，但通常會偷偷保留一張「交叉對照表」，意味著它*仍有可能*被反向識別還原。

#### **5. 一家金融機構設定了一項需求：一個全自動的後端服務必須每晚存取內部資料庫，以產出隔夜交易報表。為了在不需人工介入的情況下安全地滿足此需求，系統架構師應該規定使用：**
A. 專屬使用者配置 (Dedicated User Provisioning)
B. 共用的使用者帳號 (Shared user accounts)
C. 服務帳號 (Service accounts)
D. 單一登入 (Single Sign-On, SSO)

*   **答案：C**
*   **解析：** **服務帳號 (Service accounts)** 是專門設計給應用程式、背景服務或自動化批次處理流程使用的「非人類帳號」。它讓這些死板的程式碼能安全地通過身分驗證並與其他系統或資料庫互動，而不需要活人來敲鍵盤登入或輸入 MFA。

#### **6. 一個資安團隊正在為系統建立模型，以找出駭客可能會如何嘗試操縱輸入欄位，以對後端資料庫發動 SQL 注入 (SQL Injection) 攻擊。探索這些充滿敵意、居心叵測的情境，是為了建立：**
A. 一個功能性需求 (A functional requirement)
B. 誤用/濫用案例 (A misuse/abuse case)
C. 資料分類綱要 (A data classification schema)
D. 法規遵循矩陣 (A compliance matrix)

*   **答案：B**
*   **解析：** **誤用和濫用案例 (Misuse and abuse cases)** 會把標準的使用案例「反轉過來思考」，它詳細描述了一個駭客或充滿惡意的內部員工，會如何以不尋常的手段與系統互動，藉此找出漏洞或繞過防護。它能直接指明我們需要去寫哪些「緩解控制措施」(例如：強制加上嚴格的輸入驗證功能)。

#### **7. 一位專案經理想要確保：早在 SDLC 最一開始所制定的「每一項資安需求」，在軟體正式上線到生產環境前，都已經被準確地設計、完整地寫進程式碼裡，並且被毫不遺漏地測試過。下列哪一項產出物 (Artifact) 正是為了這個精準的目的而設計的？**
A. 軟體物料清單 (Software Bill of Materials, SBOM)
B. 風險登記冊 (Risk Register)
C. 資安需求追溯矩陣 (Security Requirement Traceability Matrix, SRTM)
D. 使用者授權合約 (End-User License Agreement, EULA)

*   **答案：C**
*   **解析：** **資安需求追溯矩陣 (SRTM)** 會建立一條筆直、具備文件證明的「血統追溯線」。它將最源頭的每一條資安需求，一直連線對應到它具體的設計圖、實作程式碼、與最終的測試腳本與證據上。它能掛保證：在漫長的開發過程中，絕對沒有任何一項資安防護被遺忘或被開發者偷懶扔掉。

#### **8. 一個組織正在進行談判，準備採購一套第三方的商用現成軟體 (COTS)。資安架構師在談判桌上堅持：合約裡面必須用法律明文規定供應商的最低服務運作時間 (Uptime)、發生資安事件時的通報時限，以及該軟體在開發時必須遵守的安全框架。這些硬性規定被稱為：**
A. 第三方供應商資安需求 (Third-party vendor security requirements)
B. 開源授權限制 (Open-source licensing constraints)
C. 跨境資料落地需求 (Cross-border data residency requirements)
D. 功能性商業使用案例 (Functional business use cases)

*   **答案：A**
*   **解析：** **第三方供應商資安需求** (通常被白紙黑字寫進服務級別協定 SLA 或合約附件中) 極度重要。它透過法律手段強制規定了賣家 (供應商) 必須如何「安全地」開發、營運和維護他們賣給客戶的軟體或服務。

#### **9. 一條明確的需求寫道：「應用程式必須安全地儲存使用者密碼，並確保即使資料庫整包被偷走也不會洩漏。」在設計階段，架構師選擇使用 Argon2 演算法來滿足這項需求。關於這個情境，下列哪一個敘述是正確的？**
A. 該需求是功能性的；Argon2 是誤用案例。
B. Argon2 是非功能性需求。
C. 該需求是非功能性的；Argon2 是緩解控制措施 (mitigating control)。
D. 該需求是誤用案例；Argon2 是功能性使用案例。

*   **答案：C**
*   **解析：** 「安全地儲存密碼」這個目標本身是一項 **非功能性安全需求**。而為了達成這個目標，架構師在技術層面所挑選並實作的 Argon2 演算法，則是被用來對抗資料庫失竊風險的 **緩解控制措施 (mitigating control)**。

#### **10. 一款目標用戶為軍事人員的應用程式，按規定必須有能力處理美國國防部 (DoD)「非機密但敏感」等級的資料。因此，該應用程式在設計上被強迫必須嚴格遵守國防資訊系統局 (DISA) 的安全技術實作指南 (STIGs)。這是在識別哪一種需求類型？**
A. 隱私需求 (Privacy requirement)
B. 針對特定產業的法規遵循需求 (Industry-specific compliance requirement)
C. 功能性商業使用案例 (Functional business use case)
D. 退場除役政策 (End of Life policy)

*   **答案：B**
*   **解析：** 遵守國防部的內部準則 (像是 DISA STIGs)，屬於一種 **特定產業 (軍防/國防) 的法規遵循需求**。不同的垂直領域 (例如：醫療、金融、軍事國防) 都包含非常特殊、只適用於其獨特風險輪廓的嚴苛監管框架。

#### **11. 一項需求明確規定：員工對於某個核心財務應用程式的「存取權限/特權」，必須每隔 90 天由其直屬主管親自覆核一次；如果發現該員工因輪調職務等原因不再需要該權限，則必須立刻撤銷。這項需求描述的是：**
A. 重新核准流程 (Reapproval process)
B. 資料匿名化流程 (Data anonymization process)
C. 資料標籤配置 (Data labeling scheme)
D. 服務帳號發放迴圈 (Service account provisioning loop)

*   **答案：A**
*   **解析：** **重新核准流程 (Reapproval process / Periodic Access Review 定期存取權限審查)** 保證了使用者的存取特權不會隨著時間推移而產生致命的「權限蠕變 (privilege creep / 權限無腦無限膨脹)」，確保系統隨時都能嚴格死守「最小權限原則 (Least Privilege)」。

#### **12. 資料架構委員會下令：某應用程式必須確保其「所有稽核日誌 (Audit Logs)」都能被妥善保存並且隨時可供調閱，期限為「整整七年」；一旦滿七年，這些日誌就必須被永久且徹底地抹除。這項需求正在處理資料生命週期中的哪一個階段？**
A. 資料生成 (Generation)
B. 資料保留與處置/銷毀 (Retention and Disposal)
C. 資料標記 (Labeling)
D. 資料匿名化 (Anonymization)

*   **答案：B**
*   **解析：** 決定資料在法律上或業務上必須「被保存多久」，以及期限到了之後該如何「從物理與邏輯上讓它毀滅」，正是資料生命週期中對於 **資料保留 (Retention)** 與 **資料處置 (Disposal)** 階段的嚴肅定義。

#### **13. 為了遵守德國嚴苛的資料主權法律，一個組織被迫規定：所有來自德國使用者的個資，其物理上的儲存地點與運算處理過程，都必須「完全被鎖在德國的國境線內」之伺服器。這引入了哪一種極度複雜的隱私需求？**
A. 使用者行銷偏好 (User marketing preferences)
B. 資料匿名化 (Data anonymization)
C. 跨境需求——資料落地 / 司法管轄區 (Cross-border requirements - Data Residency/Jurisdiction)
D. 服務級別協定 (Service level agreements, SLA)

*   **答案：C**
*   **解析：** **跨境需求 (Cross-border requirements)**，特別是 **資料落地 (data residency)** 或是 **資料主權 (data sovereignty)**，強制規定資料在物理上絕對不能離開特定的地緣政治邊界。這是為了確保這些資料受到且「僅受到」當地的司法管轄與法律保護，防止其被敵對國家或外國強權攔截與強制調閱。

#### **14. 在設計一套全新的人資 (HR) 應用程式時，開發團隊草擬了一個劇本，內容描述：「一名擁有合法權限的人資部員工，竟然濫用職權企圖進入資料庫竄改自己的薪水欄位。」請問團隊是在記錄什麼類型的案例，以便未來能實作出對應的控制措施 (例如：職責分離) 來阻止這種事發生？**
A. 勾勒出內部威脅的「誤用案例」 (A misuse case outlining an insider threat)
B. 功能性的業務需求 (A functional business requirement)
C. 監管法規遵循需求 (A compliance regulatory requirement)
D. 資料標記標準 (A data labeling standard)

*   **答案：A**
*   **解析：** 探討一個擁有合法存取權的Authorized User (授權使用者)，如何「濫用他所擁有的信任與權限」來扒開系統防線進行惡意的、未經授權的破壞行為，這正是在記錄專注於 **內部威脅 (insider threat)** 的 **誤用/濫用案例 (misuse/abuse case)**。

#### **15. 一項需求強烈要求：如果發生了一場摧毀了主要資料中心的大地震，這個雲端儲存平台必須能提供極高等級的資料韌性 (Resilience) 與備援能力 (Redundancy)。就 CIA 三角模型的觀點而言，這項需求極度專注在保護下列哪一項？**
A. 機密性 (Confidentiality)
B. 完整性 (Integrity)
C. 可用性 (Availability)
D. 不可否認性 (Non-repudiation)

*   **答案：C**
*   **解析：** 韌性 (Resilience)、備援 (Redundancy) 以及災難復原 (Disaster Recovery) 的相關需求，都是被明確設計用來確保即使在發生毀滅性天災人禍的逆境中，系統與資料仍能保持百分之百的 **可用性 (Availability)**。

#### **16. 在開始寫程式前，一個治理委員會拍板定案：全公司只有「最高人力資源長 (CHRO)」擁有終極的權力，能決定員工績效資料該被歸類在哪種機密等級，以及誰有資格去調閱它。在這個情境中，人力資源長被賦予了什麼神聖的大位？**
A. 資料保管者 (Data Custodian)
B. 資料擁有者 (Data Owner)
C. 系統管理員 (System Administrator)
D. 服務帳號 (Service Account)

*   **答案：B**
*   **解析：** **資料擁有者 (Data Owner)** 是一名擁有實權的高階管理高層 (通常是 C-Level 級別主管)，他們肩負為資料定義「機密分類等級」、「剩餘價值」並決定「誰可以得到授權存取該資料」的終極政治責任。而 **資料保管者 (Data Custodian)** (通常是倒楣的 IT 部門) 則是負責「技術實踐」(像是幫資料做加密、搞異地備份) 這些被 Owner 下令必須做到的控制措施。
