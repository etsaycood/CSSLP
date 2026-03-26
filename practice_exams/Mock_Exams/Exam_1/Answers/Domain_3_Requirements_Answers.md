# 第一套全真模擬試題 (Exam 1) - 答案與詳解本
## 領域 3：安全的軟體需求 (Secure Software Requirements) (18題)

---

#### **1. A Business Analyst for an e-commerce platform is drafting User Stories. He writes: "As a shopper, I want to be able to place items in my shopping cart, AND the website's checkout page MUST finish loading in under 2 seconds." The Security Architect immediately demands that the analyst split this sentence apart. In the classification of software requirements, exactly what type of requirement does the statement "the checkout page MUST finish loading in under 2 seconds" represent?**
**(電商平台的業務分析師正在草擬使用者故事：「身為購物者，我想要把商品放入購物車，『而且』結帳頁面『必須』在 2 秒內載入完畢。」資安架構師立刻要求將這句話拆開。在軟體需求分類中，「結帳頁面必須在 2 秒內載入完畢」確切屬於哪一種需求？)**
A. Functional Security Requirement (功能性安全需求)
B. Business Logic Metric (商業邏輯指標)
C. Non-functional Requirement (Performance/Availability) (非功能性需求 - 效能/可用性)
D. Privacy and Compliance Requirement (隱私與合規需求)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 軟體需求分為兩大類。第一種是「系統要做什麼 (What)」，例如「把商品放入購物車」，這叫功能性需求。第二種是「系統要表現得多好 (How well)」，這就叫 **非功能性需求 (Non-functional Requirement, NFR)**。規定系統必須在「2 秒內」給出回應，或是要求系統必須能夠同時承受十萬人點擊，這些都屬於 NFR 中的效能 (Performance) 與可用性 (Availability) 類別。資安人員非常關注這塊，因為如果無法滿足 2 秒的規定，在遭遇 DDoS 攻擊時系統就會直接崩潰（違反 CIA 中的可用性）。
    *   **為何 A 是干擾項：** 功能性安全需求是指具體的防護動作，例如「系統必須跳出視窗要求輸入密碼」或「系統必須將資料加密」。載入速度不是一種防護動作。
    *   **為何 B 是干擾項：** 商業邏輯指標通常是指「購物車轉換率要達到 5%」這類行銷數字，而非系統的硬體物理載入速度。
    *   **為何 D 是干擾項：** 載入速度跟使用者的個人隱私或政府法規（如 GDPR）毫無關係。

#### **2. A Requirements Engineer is interviewing the head of the finance department. The executive makes a strict demand: "Because our system handles millions of dollars in customer transfers, I demand that our authentication mechanism be extraordinarily robust. It absolutely cannot rely on just a single, easily guessable password to protect our lifelines." This is abstract business language. When the Requirements Engineer translates this into an actionable "Technical Security Requirement" for the programmers, which of the following is the MOST concrete, verifiable translation?**
**(需求工程師正在訪談財務部主管。主管強烈要求：「因為我們處理數百萬美元的轉帳，我要求認證機制必須超級強大，絕對不能只靠一個容易被猜到的密碼來保護我們的命脈。」這是抽象的商業語言。當工程師將其翻譯成程式設計師可執行的「技術安全需求」時，下列哪一項是最具體、可驗證的翻譯？)**
A. "The system must be protected by the strongest available technology to prevent any bad actors from hacking user accounts." (系統必須使用最強技術保護，以防壞人駭入帳號)
B. "The system MUST enforce Multi-Factor Authentication (MFA) for all users attempting to initiate any fund transfer requests." (系統【必須】對所有嘗試發起資金轉帳的使用者強制執行多因素認證 MFA)
C. "The system should gracefully attempt to lower the overall risk rating of unauthorized logins." (系統【應該】優雅地嘗試降低未授權登入的整體風險評級)
D. "The system's password length ought to be extremely long and contain multiple complex phonetic characters." (系統的密碼長度【應該】非常長，並包含多個複雜的注音字元)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 撰寫安全需求時，最大的禁忌就是「模糊不清 (Ambiguity)」。好的技術需求必須符合「可測試 (Testable)」與「具體明確」的黃金標準。當主管說「不能只靠一個密碼」時，最精確的技術對應就是 **多因素認證 (MFA)**。選項 B 使用了強制的 **MUST**，並清楚界定了觸發條件：「嘗試發起資金轉帳時」，以及具體的實作技術：「MFA」。這樣 QA 團隊才能明確寫出一條測試案例去驗證它。
    *   **為何 A 是干擾項：** 「最強技術」、「防止壞人」這都是毫無定義的形容詞公關稿，程式設計師看到這種需求會不知道該寫什麼程式。
    *   **為何 C 是干擾項：** 使用 "should" (應該) 代表這只是個建議，而非強制要求。且「降低整體風險」是一個抽象的目標，不是具體的系統行為。
    *   **為何 D 是干擾項：** "ought to be" (最好是) 一樣缺乏強制力。「非常長」到底是幾碼？這無法被精準測試。而且主管的要求是「不能只靠密碼」，選項 D 只是在把密碼弄長，完全搞錯了主管的重點。

#### **3. When designing a social networking application intended for customers residing in the European Union, the legal team forwards a dense 100-page summary of GDPR mandates. They highlight an incredibly difficult technical directive: "When a deeply unsatisfied user formally decides to delete their account, we must mathematically guarantee that all their posts, uploaded photos, and personal telemetry data are violently and permanently eradicated from our primary databases, third-party backup storage buckets, and all caching servers, leaving absolutely zero trace." What famous, notoriously difficult-to-implement data privacy principle is the legal team demanding?**
**(在設計針對歐盟客戶的社群 APP 時，法務團隊畫了一個極難的技術指令：「當使用者決定刪除帳號時，我們必須保證他們所有的貼文、照片和遙測數據，都從主資料庫、第三方備份雲以及所有快取伺服器中被永久暴力移除，絕對不留痕跡。」法務團隊要求的是哪一項惡名昭彰且極難實作的資料隱私原則？)**
A. Right to be Forgotten (Right to Erasure) (被遺忘權 / 刪除權)
B. Right to Data Portability (資料可攜權)
C. Mathematical Non-repudiation (數學級的不可否認性)
D. Least Privilege Data Access (最低權限資料存取)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 在 GDPR (歐盟一般資料保護規則) 中，讓所有資料庫管理員跟開發人員最頭痛的法規就是 **被遺忘權 (Right to be Forgotten)**，或稱刪除權。當使用者行使這項權利時，公司有法律義務在規定時間內，跨越所有複雜的微服務架構，把該使用者的每一個位元組給殺得乾乾淨淨，連冷備份磁帶上的資料都要想辦法處理。這對軟體需求與架構設計來說是巨大的挑戰。
    *   **為何 B 是干擾項：** 資料可攜權是指使用者有權要求你把他的資料打包成一份 CSV 或 JSON 給他帶走，去跳槽給你的競爭對手用。它不是關於「刪除/抹滅」資料。
    *   **為何 C 是干擾項：** 不可否認性是確保發信人沒辦法耍賴說「這封信不是我寄的」。跟使用者要你殺掉他的個資無關。
    *   **為何 D 是干擾項：** 最低權限是內部員工存取管控的原則（例如客服人員只能看客戶名字不能看信用卡號），這不是在處理客戶要求終止合約並刪除資料的議題。

#### **4. The enterprise security team is conducting a rigorous security review of a newly proposed flowchart detailing "The Password Reset / Forgot Password Mechanism." On the whiteboard, they use a red marker to draw out a specific scenario known as an "Abuse Case." Which of the following dramatic scenarios MOST accurately describes an "Abuse Case" specifically targeting this password reset mechanism?**
**(企業資安團隊正在對新的「忘記密碼/重設密碼機制」流程圖進行安檢。他們用紅筆在白板上畫出了一種稱為「濫用案例 (Abuse Case)」的特定情境。下列哪一個戲劇化的場景最精確地描述了針對此重設密碼機制的「濫用案例」？)**
A. A forgetful but legitimate user cannot remember the password they created yesterday and successfully resets it by answering their security questions. (健忘的合法用戶成功回答安全問題重設了密碼)
B. A malicious attacker writes an automated script that sends 10,000 requests per second to the reset page, attempting to discover if the sacred account "admin@company.com" actually exists in the corporate database (Username Enumeration). (惡意攻擊者寫腳本每秒發一萬次請求到重設頁面，試圖探測「admin@公司」這個帳號是否存在，即帳號枚舉攻擊)
C. The backend database server suffers a catastrophic hard drive failure, causing all legitimate forgot password requests today to queue and be severely delayed. (後端伺服器硬碟暴斃，導致今天所有合法的重設密碼請求大塞車)
D. A user successfully logs in and proactively navigates to their account settings to change their password to something stronger. (使用者登入後主動去改了更強的密碼)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 在需求分析階段，不僅要寫「好人會怎麼用系統 (Use Cases)」，更要寫出「壞人會怎麼玩壞你的系統」。這就叫做 **濫用案例 (Abuse Cases)** 或誤用案例 (Misuse Cases)。選項 B 描述了一個駭客利用你精心設計的「忘記密碼」功能，故意大量輸入不同 Email，透過觀察系統回傳的是「密碼重設信已寄出」還是「查無此帳號」，來盲測、盤點出你們公司有哪些真實存在的員工帳號 (Username Enumeration)。這是一個非常典型，利用正常功能達成惡意目的的濫用設計。
    *   **為何 A 是干擾項：** 這是一個完美的、符合設計初衷的正常「使用案例 (Use Case)」。好人正常使用了系統，沒有任何濫用發生。
    *   **為何 C 是干擾項：** 這是硬體基礎設施故障導致的「災難/營運中斷事件 (Operational Failure)」。硬碟壞掉不是因為駭客去「濫用/惡搞」重設密碼的商業邏輯所造成的。
    *   **為何 D 是干擾項：** 這是另一個正常的系統功能與良好的安全實踐，毫無濫用可言。

#### **5. The Procurement Department is preparing to sign a massive, multi-million dollar contract to lease a Cloud-based SaaS Human Resources Management System. Before the Service Level Agreement (SLA) is finalized, the formidable CISO aggressively intervenes and appends a stern clause to the bottom of the appendix: "The SaaS vendor must generate a monthly cryptographic dashboard report proving that our data maintained an availability rating of 99.99% on your cloud platform. If the availability dips below this exact threshold, the vendor must unconditionally refund our entire service fee for that month." What specific service quality benchmark is the CISO forcefully establishing?**
**(採購部準備簽署巨額雲端 HR 系統的 SaaS 租約。在服務層級協議 (SLA) 定稿前，強勢的 CISO 修改了合約：「SaaS 供應商必須每月提供儀表板證明我們的資料可用性維持在 99.99%。若低於此門檻，供應商必須無條件退還該月全部服務費。」CISO 強硬建立的是哪一種特定的服務品質基準？)**
A. Maximum TimeToPatch (TTP) limit (最大修補時間限制)
B. Service-Level Objectives (SLOs) (服務層級目標)
C. Symmetric Key Length Minimums (對稱式金鑰長度下限)
D. Mean Time Between Failures (MTBF) (平均故障間隔時間)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **服務層級目標 (Service-Level Objectives, SLOs)** 是整個大 SLA 合約裡面，那一條條非常具體、可以用數學儀表板量化的「承諾數字」。當 CISO 在合約裡寫下死板的「99.99% (四個 9)」時，這個精確的數字及違約罰則，就是一個不可妥協的 SLO。它定義了這套系統對於「可用性 (Availability)」的最低及格標準。
    *   **為何 A 是干擾項：** TimeToPatch 是指發現漏洞後要在幾天內打上更新檔。雖然這也很重要，但這不是在衡量「系統上線不中斷的百分比 (99.99%)」這個指標。
    *   **為何 C 是干擾項：** 金鑰長度是密碼學的實作規範（如 AES-256），它跟這套 SaaS 雲端系統一個月有沒有當機超過 5 分鐘的「整體營運可用性合約」無關。
    *   **為何 D 是干擾項：** MTBF 是用來計算硬體設備（如硬碟或發電機）能活多久才會壞掉的物理平均壽命。在高度分散式的雲端服務架構合約中，我們通常不看單一硬體的壽命，而是看對外的整體服務可用率 (SLO/Uptime)。

#### **6. A drone navigation software application is currently being developed by an outsourced military contractor. The application's "Security Requirement Specifications Book" contains the following unyielding sentence: "The encrypted communication module operating on the drone SHALL be validated against and strictly comply with the Federal Information Processing Standard (FIPS) 140-2 Level 2." In requirements engineering terminology, what specific category does this unforgiving, government-mandated standard fall into?**
**(一家外包軍火商正在開發無人機導航軟體。安全需求規格書中有一句鐵腕規定：「無人機上的加密通訊模組『必須』通過驗證，並嚴格遵守聯邦資訊處理標準 (FIPS) 140-2 Level 2。」在需求工程術語中，這種不容妥協的政府強制標準屬於哪一個特定類別？)**
A. Implicit Business Competitor Demands (隱含的商業競爭對手要求)
B. Compliance / Regulatory Standards Requirement (合規 / 監管標準需求)
C. Non-functional Usability Requirement (非功能性的易用性需求)
D. Open Design Principle (開放設計原則)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 當你看到 FIPS、HIPAA、GDPR、PCI DSS 這類後面常跟著法律與罰金的國家級縮寫時，這些就屬於需求收集過程中位階極高的 **合規與監管標準需求 (Compliance / Regulatory Standards Requirement)**。對美國政府（特別是軍方或聯邦機構）賣含有密碼學功能的軟體，要求必須通過 NIST 發布的 FIPS 140 認證，這不是工程師想不想做的問題，這是沒有這張法規及格證書，軟體連投標的資格都沒有的法律強制要求。
    *   **為何 A 是干擾項：** 政府的標準法規是明文規定在全球網路上的鐵律，它不是偷偷摸摸因為對手而在背後隱含的商業要求。
    *   **為何 C 是干擾項：** 易用性 (Usability) 是指軟體介面有沒有做成繁體中文、按鈕夠不夠大讓老人能按到。要求美國軍規等級的密碼驗證模組，這絕對不是為了讓它「容易使用」。
    *   **為何 D 是干擾項：** 開放設計 (Open Design) 是一個安全架構原則（不依靠隱藏程式碼來獲得安全）。它跟把軟體送去聯邦機構做 FIPS 合規認證是兩碼子事。

#### **7. Inside the chaotic world of Agile development, teams employ an adversarial technique. Instead of solely writing optimistic stories about what honest users want the system to do, they begin drafting "Evil Villain" narratives. For example: "As a malicious hacker, I want to inject an obfuscated JavaScript payload into the search bar, so that the browsers of any innocent user viewing the results will silently transfer all their digital reward points into my offshore account." What is the formal name for these specific planning documents that translate attacker goals, methods, and intentions into actionable descriptions?**
**(在 Agile 開發中，團隊採用對抗性技巧。他們不只寫好人的故事，還開始草擬「邪惡反派」的敘事。例如：「『身為一名駭客，我想要在搜尋列注入已被混淆的 JavaScript 酬載，以便讓所有觀看搜尋結果的無辜帳號，默默地將他們的點數轉入我的境外戶頭。』」這些將攻擊者目標、手法翻譯成具體描述的規劃文件，正式名稱為何？)**
A. Firewall Access Control Lists (ACLs) (防火牆存取控制串列)
B. User Interface Mindmaps (使用者介面心智圖)
C. Misuse / Abuser Cases (誤用 / 濫用案例)
D. Threat Landscape Matrix (威脅地景矩陣)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 在需求發想階段，把傳統 User Story 裡面的「身為一個好客戶，我想...」主詞，全部霸氣替換成「身為一個心懷不軌的內鬼 / 駭客，我想...」，這種刻意站在反派視角來沙盤推演系統弱點的敘事手法，就叫做 **誤用案例或濫用案例 (Misuse / Abuser Cases)**。它是挖掘深層資安防禦需求（例如：因為駭客想 XSS，所以我們必須具備嚴格的輸出編碼需求）的最強工具。
    *   **為何 A 是干擾項：** 防火牆 ACL 是一行一行寫著「允許 IP A，封鎖 IP B」的網路設備路由指令。它完全不是這種人類可閱讀的情境故事規劃草圖。
    *   **為何 B 是干擾項：** UI 心智圖是設計師在畫按鈕怎麼點、畫面怎麼跳的關聯圖。
    *   **為何 D 是干擾項：** 威脅地景矩陣是一份高階的地理與戰略報告（例如：分析今年北韓或俄羅斯駭客愛用什麼武器），它太過龐大與巨觀，不會具體寫到「在你的購物網站搜尋列打進一段 JS 偷點數」這麼微觀的單一操作功能上。

#### **8. During the preliminary requirements phase for a revolutionary Electronic Medical Record (EMR) system, the Chief Information Officer (CIO) issues a terrifying edict regarding the medical data, which if leaked, could cause devastating reputational ruin and loss of life. The CIO commands: "Before we even begin buying servers or designing databases, your team must first comprehensively assess exactly how devastating the explosive blast radius would be if this specific medical data fell into the hands of a foreign intelligence agency!" What is the formal term for this preliminary phase of the information lifecycle that focuses on measuring the lethal sensitivity of data?**
**(在電子病歷系統的初步需求階段，CIO 頒布了一道駭人的命令：「在我們買伺服器或設計資料庫之前，你們必須先全面評估，如果這些醫療數據落入外國情報機構手中，那爆炸的毀滅半徑到底會有多大！」這個專注於「丈量資料致命敏感度」的資訊生命週期初步階段，正式術語稱為什麼？)**
A. Backup Media Destruction Drill (備份媒體銷毀演習)
B. Data Classification and Categorization (資料分類與分級)
C. Public Key Infrastructure (PKI) Stress Test (公鑰基礎設施壓力測試)
D. Third-party Library White-box Analysis (第三方函式庫白箱分析)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 在軟體還沒動土開工前，你要設計一座金庫之前，你必須先知道裡面是要放衛生紙、黃金，還是會污染整座城市的核廢料。評估這批資料如果失竊、竄改或消失，會對公司（或國家命脈）造成多大等級的傷害（輕微、嚴重或毀滅性），並以此來給資料貼上「機密 (Confidential)」、「極密 (Top Secret)」等標籤的行為，這就是所有資安政策的起源：**資料分類與分級 (Data Classification and Categorization)**。因為只有先搞清楚資料的敏感度，我們才能推導出相對應強度的保護需求（例如要套用多厚的加密演算法）。
    *   **為何 A 是干擾項：** 銷毀演習是在生命週期的絕筆之作（除役階段）去砸毀過期硬碟。我們現在還在白紙階段評估資料價值。
    *   **為何 C 是干擾項：** PKI 是用來發行數位憑證的架構，這是在系統實作階段的網路建設，而不是在一開始幫資料貼「極機密」標籤的行政評估。
    *   **為何 D 是干擾項：** 分析開源軟體庫有沒有毒，這是實作/測試階段的軟體組成分析 (SCA)，與丈量醫院客戶病歷的機密等級無關。

#### **9. While actively gathering software security requirements, the Requirements Analyst discovers a violent clash between two massive departments. The aggressive Sales team demands: "To maximize sign-up conversion metrics, customers should face zero identity verification hurdles during registration!" Conversely, the terrifying Legal team roars: "If we do not enforce mandatory dual-citizenship verification and KYC checks for every single user, the federal government will fine us into immediate bankruptcy for money laundering violations!" When faced with horribly conflicting demands, what ultimate, sacred enterprise document should the Requirements Analyst prioritize as the ultimate tie-breaker to establish the final specification?**
**(需求分析師發現兩大部門爆發激烈衝突。業務部大吼：「為了衝轉換率，客戶註冊時應該『零』身分驗證障礙！」法務部則咆哮：「如果不強制每一個用戶做雙重國籍 KYC 實名認證，聯邦政府會直接用洗錢防制法把我們罰到破產！」面對這種可怕的需求衝突，分析師應該把什麼神聖的企業文件拿出來當作最終裁判，以確立最後的規格？)**
A. The Sales department's quarterly revenue projections from last year (業務部去年的季度營收預測)
B. The company's highest overarching Enterprise Information Security Policies and defined risk appetite (公司最高位階的企業資訊安全政策與既定的風險胃納量)
C. The Java Secure Coding Guidelines manual (Java 安全編程指南手冊)
D. The after-action report from last year's crippling 3-day DDoS outage (去年癱瘓三天的 DDoS 停機事後檢討報告)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 當跨部門為了解決商業利益與法規生存之間的衝突而吵得不可開交時，需求工程師不能自己擲筊決定。你必須往上呈報，拿出一把尚方寶劍：**企業資訊安全政策 (Enterprise Information Security Policies)** 與董事會畫押認可的 **風險胃納量 (Risk Appetite)**。這是公司最高經營層針對「我們願意為賺錢承擔多大被罰款或被駭客攻擊的風險」所定下的基調。如果高層政策寫明「遵循國家反洗錢法規的優先權高於一切轉換率」，那法務部就贏了。企業政策是推導所有軟體底層需求的最終依歸。
    *   **為何 A 是干擾項：** 業務部的業績夢想不能凌駕於會讓公司負責人去坐牢的國家法律風險之上，除非董事會（政策）批准這場賭博。
    *   **為何 C 是干擾項：** Coding Guidelines 是教底層工程師怎麼寫好 `if/else` 的技術說明書。它裡面絕對不會寫說「這間公司在做 KYC 實名制時要做到什麼程度」。
    *   **為何 D 是干擾項：** DDoS 防禦報告是針對網路頻寬被塞爆的技術總結。它無法用來仲裁業務跟法理針對「使用者身分認證寬嚴」的商業邏輯衝突。

#### **10. Once a software requirement is established, it must be written with crystal clarity. Which of the following statements represents an atrociously written, highly ambiguous, and utterly "Untestable" security requirement that would infuriate a Quality Assurance (QA) engineer?**
**(軟體需求必須寫得晶瑩剔透。下列哪一句話是一個寫得極度糟糕、充滿歧義，且完全「無法被測試」，會讓 QA 工程師氣到吐血的安全需求？)**
A. "All passwords stored within the operational data directory MUST be mathematically hashed utilizing the PBKDF2 algorithm combined with a unique cryptographic Salt." (所有存在目錄裡的密碼都【必須】用 PBKDF2 演算法加上獨一的鹽值進行雜湊)
B. "The system MUST immediately write every single failed login attempt, including the originating public IP address, directly to the `/var/log/auth` text file." (系統【必須】將每一次失敗的登入，含來源 IP，寫入該文字檔)
C. "The external payment webpage must be designed to be extremely secure so it does not let any bad guys in or allow connections to be broken." (外部付款頁面【必須設計得極度安全】，好讓它不會放任何壞人進來或讓連線斷掉)
D. "If the authentication module detects 5 consecutive failed login attempts originating against the same username within a 60-second window, the system MUST lock that account for exactly 15 minutes." (若 60 秒內同帳號連續 5 次登入失敗，系統【必須】死鎖該帳號整整 15 分鐘)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是標準的「垃圾需求 (Garbage Requirement)」。軟體工程界最大的噩夢就是充滿形容詞的廢話。什麼叫做「極度安全」？什麼叫做「壞人」？一個 QA 工程師要怎麼寫一段測試腳本去驗證一台伺服器夠不夠「極度安全」？因為它完全沒有定義具體的門檻、手段或可測量的數字，這種充滿模糊情緒字眼的需求，在實務上被視為是 **不可測試 (Untestable)** 的廢紙，必須被退回重寫。
    *   **為何 A 是干擾項：** 寫得極好。因為「PBKDF2」與「加鹽 (Salt)」都是極度明確、黑白分明的數學密碼學規格，工程師看一眼就知道該去 call 哪個函式庫來實作。
    *   **為何 B 與 D 是干擾項：** 寫得極好。選項 B 定義了精確的觸發條件 (failed login) 與精確的產出 (寫入 `/var/log/auth`)。選項 D 定義了完美的數字邊界 (5次、60秒、鎖15分鐘)。QA 可以非常開心地照著這些數字寫成自動化測試劇本。

#### **11. A US State Supreme Court Judge issues a ruling against a booming tech platform. The ruling dictates that for the next three years, the platform must guarantee that every electronic contract generated possesses undeniable mathematical and legal proof. The judge states: "If the two signing parties end up in my courtroom a decade from now, neither party can *ever* deny saying 'I didn't sign that contract,' and the tech platform itself cannot deny saying 'We never processed that contract.'" What ultimate cybersecurity core property does this inescapable legal liability requirement correspond to?**
**(州最高法院法官對一家暴紅科技平台做出判決。法官裁定：「如果在十年後兩個簽約的人上了我的法庭，任何一方都絕對『不能抵賴否認』說『我沒簽過那個約』，而平台也『不能抵賴』說『我們沒處理過這張合約』。」這項無法逃避的法律責任需求，精準對應了哪一項終極的網路安全核心屬性？)**
A. The obscuring veil of Confidentiality (機密性的遮蔽面紗)
B. The ultimate limits of System Availability (系統可用性的極限)
C. Non-repudiation (Irrefutable proof of origin and integrity) (不可否認性 / 來源與完整性的無法反駁證據)
D. The privacy-focused Right to be Forgotten (專注於隱私的被遺忘權)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這個情境完美地詮釋了資訊安全基石中的 **不可否認性 (Non-repudiation)**。它通常是透過非對稱式加密與數位簽章 (Digital Signatures) 來達成的高級防護。它的核心哲學是建立一條「密碼學級別的鐵證鏈」，確保做過某事的人（比如送出郵件、簽署金融合約），在未來的任何時刻，都無法在法庭上或系統紀錄前耍賴說「那個動作不是我做的」。這正是法官所要求的「無法抵賴」的法律證據能力。
    *   **為何 A 是干擾項：** 機密性 (Confidentiality) 是確保內容不被旁人偷看（例如把信封黏死）。但它無法阻止寄件人回頭死不認帳說「那封信雖然被封緊了但這信根本不是我寄的」。
    *   **為何 B 是干擾項：** 可用性 (Availability) 確保伺服器不會當機。跟法庭上的法律證據效力無關。
    *   **為何 D 是干擾項：** 被遺忘權是要你主動把資料合法註銷毀滅，這跟法官要你「死死保留住誰簽了名的無法反駁證據」完全背道而馳，它是相反的概念。

#### **12. During the very initiation phase of a massive software lifecycle, a Project Manager proudly receives a 400-page "Requirements Specification" tome from the client. It details exactly how many blue buttons the app needs and precisely when billing emails should be fired. The Lead Security Engineer spends two days reviewing it and declares nervously: "This entire document is a disaster. It does not mention 'minimum password lengths' or 'heartbeat rate-limiting for DDoS defense' a single time." What tragic but common industry phenomenon does this story highlight regarding "requirements," unless security is aggressively prioritized?**
**(在生命週期的極早期，專案經理驕傲地收到客戶 400 頁的「需求規格書」，裡面連有幾顆藍色按鈕都寫得一清二楚。但首席資安工程師花了兩天看完後緊張宣佈：「這整份文件是場災難。它高達 400 頁，卻隻字未提『密碼最少幾碼』或『抵禦 DDoS 的流量限制』。」如果不積極強求，這個故事凸顯了業界關於「需求」的哪種悲慘常態？)**
A. Security is usually automatically and perfectly implemented deep beneath the UI color schemes. (資安通常會自動且完美地實作在 UI 配色方案底層)
B. Security requirements are frequently neglected, treated as uninteresting "non-functional" edge-cases, and entirely forgotten during the initial rush to define business features. (安全需求經常被忽視，被當成無趣的「非功能性」邊緣案例，並在早期急於定義商業賺錢功能的熱潮中被徹底遺忘)
C. Security requirements are always the very first elements injected into User Interface wireframe designs. (安全需求永遠是第一個被注入到 UI 線框圖設計裡的元素)
D. Security requirements are universally so simple that even non-technical executives can effortlessly write them and force them into the spec sheet. (安全需求普遍非常簡單，連非技術主管都能毫不費力地寫好並塞進規格書)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是軟體工程史上最殘酷的現實，也是 CSSLP 考試中不斷強調的痛點：**安全需求往往是隱形的 (Security requirements are often implicit/neglected)**。客戶永遠只會興奮地描述他們在螢幕上「看得到」的功能（如購物車按鈕、花俏的報表）。而在冰山底下的那些保命心法（如防禦 SQL 注入、記憶體溢位保護、日誌監控等非功能性要求 NFR），因為它們不能直接幫客戶賺錢，所以總是在初期的需求訪談中被徹底遺忘。如果資安團隊不在需求第一天就強勢介入把安全寫進合約裡，工程師最後寫出來的系統絕對會是座沒有地基的紙房子。
    *   **為何 A 與 C 是干擾項：** 這是一個天真的幻想。資安絕對不會因為工程師把 UI 畫得很漂亮，就「自動附身」在程式碼裡。資安是需要花費重金跟時間額外刻劃出來的。
    *   **為何 D 是干擾項：** 撰寫嚴謹的密碼學規範、跨域資源共用 (CORS) 等資安需求極度艱澀且困難，非技術主管根本連聽都沒聽過這些名詞，更不可能去把他們寫進規格書裡。

#### **13. An e-commerce platform receives a terrifying intelligence report from a third-party security firm: "Extremely clever hackers are manipulating your checkout system. They are manually intercepting network traffic to change the 'quantity' field to a negative integer (e.g., Quantity = -10). Because your system is mathematically naive, it multiplies the base price by -10, resulting in the server owing the hacker money, essentially refunding their credit card for an unpurchased item!" To fundamentally and permanently slam this loophole shut, what specific category of validation requirement MUST analysts force into the specification for all "Data Input" fields?**
**(電商平台收到資安公司恐怖報告：「駭客正攔截網路封包，把結帳的『數量』欄位改成負整數 (例如數量 = -10)。因為你們的系統數學太天真，用底價乘上 -10 後，變成伺服器欠駭客錢，等於直接退款到他信用卡！」為了永遠封殺這個漏洞，分析師【必須】在規格書中強制將所有「資料輸入」欄位加上哪種特定類別的驗證需求？)**
A. Explicit Data Type Conversion (Casting) requirements (明確的資料型態轉換與強制轉型需求)
B. Regex character matching for SQL syntax (用來防堵 SQL 語法的正規表達式)
C. Strict requirements defining mandatory Boundaries, Range Checks, and Business Logic Validations for all incoming data (定義所有傳入資料【必須】通過嚴格的邊界檢查、範圍檢查，與商業邏輯驗證的需求)
D. A requirement to log the hacker's IP address upon detection (要求在偵測到攻擊時記錄下駭客 IP 的需求)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這個買東西買到變倒賺錢的奇葩案例，不是單純的技術弱點（如程式崩潰），這是一個血淋淋的 **商業邏輯漏洞 (Business Logic Flaw)** 與 **極限/範圍驗證失敗 (Boundary/Range validation failure)**。一個人在買東西時，「購買數量」在真實物理世界中，最少最少也必須是 $0$ 或是 $1$。它絕對不可能是一個負數。因此，系統需求必須從源頭下重手規定：所有來自於前端的不受信任輸入，都必須遭受最嚴格的 **邊界檢查 (Boundary Checking)** 和 **範圍檢查 (Range Check)**。只有設定出「數量必須介於 1 到 99 之間」的數學鐵籠，才能徹底粉碎這種利用負數邏輯的詐欺。
    *   **為何 A 是干擾項：** 型態轉換 (Casting) 只是把一段帶有小數點的字串轉成整數（例如把字串 "-10" 轉成系統讀得懂的數字 `-10`）。但如果你沒有做「範圍檢查」判定 -10 不合理，系統一樣會拿這個完美轉型的整數去算出退錢的結果。
    *   **為何 B 是干擾項：** 駭客輸入的 "-10" 這個負數就只是個平凡無奇的整數，它裡面沒有夾帶 `' OR 1=1 --` 這種惡意 SQL 指令。你用防 SQL 的過濾器是抓不出這種商業邏輯詐欺的。
    *   **為何 D 是干擾項：** 記錄下他的 IP 然後眼睜睜看著他一天從國外提款提走一百萬美元？這是事後調查，它並沒有在系統上「關閉/防堵」這個數學運算的漏洞。

#### **14. The corporate Procurement arm plans to acquire a massive fleet of IoT security cameras from various global manufacturers. Some of these obscure vendors lack even a basic company website. Horrified, the CISO aggressively injects a non-negotiable "kill order" into the Purchasing Security Requirements document: "Any IoT vendor attempting to sell to this enterprise MUST sign a legally binding contract agreeing that if a critical vulnerability is discovered in their hardware, they will provide a free, patched firmware update within 72 hours." This strict demand directly mitigates risks associated with which crucial security domain?**
**(企業採購部準備買一大批雜牌 IoT 監視攝影機。驚恐的 CISO 在採購安全需求上強制下了一道追殺令：「想賣設備給我們的 IoT 廠商，【必須】簽署具法律約束力的合約：一旦被發現高危漏洞，必須在 72 小時內免費提供修補韌體。」這條嚴格需求直接防禦了哪個關鍵資安領域的風險？)**
A. Supply Chain Risk Management via strict Vendor SLA and Contractual Requirements (透過嚴格的廠商 SLA 與合約要求來進行「供應鏈風險管理」)
B. Complete Unit Testing Automation integration (徹底的單元測試自動化整合)
C. Cryptographic Key Rotation and Retirement scheduling (密碼金鑰輪替與淘汰排程)
D. Open-Source Software Component Analysis (SCA) (開源軟體組成分析)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 買別人寫好的軟體或硬體設備，是把一顆不受你控制的特洛伊木馬直接搬進公司神聖的內網地帶。這種不確定性被稱為 **供應鏈風險 (Supply Chain Risk)**。特別是物聯網 (IoT) 產品以「萬年不更新的孤兒軟體」聞名。CISO 利用法務與採購的力量，直接在 **合約安全需求 (Contractual Requirements/SLA)** 中壓上修補時限的條款，這是針對供應商進行外部風險控制與施壓的最強硬、最標準的做法。我們自己改不了他們的程式碼，所以必須用合約逼他們動起來。
    *   **為何 B 是干擾項：** 單元測試是你家內部工程師在測自己寫的小程式用的。你沒辦法去幫那家位於地球另一端的雜牌攝影機廠商寫單元測試。
    *   **為何 C 是干擾項：** 金鑰輪替講述的是公司內部的 PKI 憑證多快要換發一次，跟壓榨外部廠商給予修補檔的安全政策無關。
    *   **為何 D 是干擾項：** 開源軟體分析 (SCA) 雖然也算是追蹤一部分的供應鏈風險（針對你程式碼用了什麼免費套件）。但題意非常明確是在描述用「合約 (SLA/Contract)」對「實體外部供應商/設備商」進行的法律約束，所以 A 選項涵蓋的面向更精準對接情境。

#### **15. You are the lead architect over an incredibly lucrative Digital Rights Management (DRM) distribution system. Regarding the absolute "Availability Requirement," your aggressive manager barks this bizarrely compromised tolerance standard at you: "I accept that if a massive earthquake destroys the power grid, this server going offline is unavoidable. BUT! No matter how long the server stays dead, when you finally power it back up, the internal DRM database is strictly forbidden from losing more than *the last 15 minutes of new transaction data*. I can tolerate losing those last 15 minutes, but if records from 16 minutes ago are missing, you will be fired and sued." What is the standardized disaster recovery term for this specific "maximum tolerable data loss" time threshold?**
**(你是版權派發系統的首席架構師。主管對著你大吼一項針對可用性需求的妥協標準：「大地震斷電我能接受伺服器死機。但是！不管死機多久，當你最後重啟電源時，資料庫【絕對不准遺失超過最後 15 分鐘內的新交易資料】。我可以忍受那 15 分鐘的損失，但如果 16 分鐘前的舊資料不見了，你就等著被開除。請問這個針對「最大可容忍資料遺失量」的時間回溯門檻，在災難復原術語中叫什麼？)**
A. Recovery Time Objective (RTO) (可用性復原時間目標)
B. Recovery Point Objective (RPO) (資料復原點目標)
C. Mean Time To Repair (MTTR) (平均修復時間)
D. Proof of Work (PoW) Threshold (工作量證明門檻)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 當災難 (Disaster) 發生導致系統崩潰的那個瞬間起算，我們往前回顧：你備份資料的密集程度，決定了你在爆炸時會「掉落/損失多少分鐘前的進度」。這個「你能容忍的資料遺失最大極限」，在資訊生命週期中被極度嚴格地定義為 **Recovery Point Objective (RPO - 復原『點』目標)**。如果老總說 RPO 是 15 分鐘，這意味著你的基礎建設需求，必須強制每隔 15 分鐘 (或更快) 就要把所有資料庫的進度，完整備份切片並傳送到另一個異地安全的保險箱裡面。這是一個純粹針對「Data Loss (資料丟失量)」的痛苦底線。
    *   **為何 A 是干擾項：** Recovery Time Objective (RTO) 是往災難發生「之後」算的時間。它是指「老總能容忍這台伺服器死在地上癱瘓幾個小時，才必須把它救活重新開機營業」。RTO 關注的是停機時間 (Downtime)，而本題情境中老總已經說了「不管死機多久 (放棄RTO)」，他只死死盯著以前的備份資料不能掉 (堅守 RPO)。
    *   **為何 C 是干擾項：** MTTR 是修復一台壞掉伺服器的歷史平均統計時間，這不是一個災難來臨前，公司老總所能主觀下達的聖旨目標閾值。
    *   **為何 D 是干擾項：** Proof of Work (PoW) 是區塊鏈挖礦的運作演算法，跟企業資料庫的備份目標無關。

#### **16. At an ultra-secure clearinghouse, a non-negotiable architectural rule states: "Before any highly sensitive Primary Account Number (PAN) used for credit card billing can exit our internal network gateway en route to a third-party API, the 16-digit PAN MUST be irreversibly swapped out and replaced with a meaningless, randomly generated virtual surrogate string (e.g., `TKN-1249A`). The authentic PAN with real monetary value is strictly forbidden from ever leaving the isolated database." This extreme "fake-money for real-money" data protection requirement is fundamentally designed to satisfy which massive, industry-ruling data security standard?**
**(在超安控結算中心，有一條不可妥協的架構準則：「任何信用卡 16 碼真實帳號 (PAN) 在離開我們內網傳給第三方前，『必須』被不可逆地替換成一串隨機生成的無意義虛擬代碼 (例如代幣 `TKN-1249A`)。真實卡號絕對不准踏出隔離的資料庫半步。」這種極端的「以假代換真」資料保護需求，根本上是為了滿足哪一種龐大且統治業界的資料安全標準？)**
A. General Data Protection Regulation (GDPR) (歐盟一般資料保護規則)
B. ISO 27001 Information Security Management System (ISO 27001 資訊安全管理系統)
C. Payment Card Industry Data Security Standard (PCI DSS) via Tokenization compliance (透過「權杖化 Tokenization」技術以符合支付卡產業資料安全標準 PCI DSS)
D. Health Insurance Portability and Accountability Act (HIPAA) (健康保險可攜與責任法案)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這個情境描述的是金融與支付產業最神聖的防禦絕境：**權杖化 (Tokenization)**。因為把真實的信用卡號 (Primary Account Number, PAN) 存在自己的資料庫裡風險太高了，一旦被駭客偷走就是天文數字的賠償。因此架構師用一個毫無數學關聯的虛假代幣 (Token) 來取代真實卡號在系統中流動。這種極端隔離真實持卡人資料 (Cardholder Data, CHD) 的需求，幾乎 100% 都是被全球信用卡的鐵血暴君——**PCI DSS (支付卡產業資料安全標準)** 給逼出來的。實施 Tokenization 是用來大幅縮小 PCI DSS 查核範圍的最有效手段。
    *   **為何 A 是干擾項：** GDPR 雖然也保護個資隱私，但 GDPR 大多數時候只要求你把個人的名字跟信箱做「假名化 (Pseudonymization)」。只有在看見 "PAN (16碼信用卡)" 這種關鍵字時，我們才能毫無懸念地將其直接歸類到統治金融支付的 PCI DSS 領域。
    *   **為何 B 是干擾項：** ISO 27001 是一個只顧「管理與流程」的大框架。你拿 ISO 證書並不代表你一定要用代幣替換卡號。
    *   **為何 D 是干擾項：** HIPAA 統治的是病人的醫療血液報告與病歷 (PHI)。在醫院拿代幣去置換使用者的信用卡，一樣是在解決金融支付的 PCI 痛點，而不是解決病歷洩漏的 HIPAA 痛點。

#### **17. During a lively sprint planning session, developers suggest: "We should implement a 'Multi-Language Support' feature so our international user base can comfortably navigate the website." This is a classic functional requirement catering to user comfort. Suddenly, a cynical, veteran Security Engineer interjects: "Love the feature, but regarding this seemingly harmless multi-lingual upgrade, I formally require that REGARDLESS of the user's geographical location or their chosen front-end interface language, every single 404 error, failed login attempt, and stack trace generated by the backend must be strictly written into the database using exclusively Unified English and standardized UTC timestamps." What slightly paranoid but highly critical cybersecurity goal is this engineer trying to safeguard?**
**(敏捷會議中，開發者提議：「我們應該做多國語言讓國際用戶逛網站更順心。」這是典型的功能性舒適需求。突然，資深資安工程師打岔：「我很喜歡這功能，但是！不管這個地球上的用戶選了網頁前端哪國語言，我『強制規定』伺服器後端產生的每一次密碼錯誤、每一個 404 崩潰日誌，通通只准用『統一的英文與標準 UTC 零時區時間』寫入資料庫。」這位看似妄想症的工程師，試圖捍衛哪一項極度關鍵的資安生命底線？)**
A. To guarantee that external translation agencies have specialized IT error-code work. (以保證外部的翻譯社有專門的IT錯誤碼可以賺翻譯費)
B. To significantly reduce database storage space by eliminating Double-Byte Unicode characters. (為了消除雙位元組的萬國碼，以大量節省資料庫容量)
C. To guarantee that when a massive, global security breach inevitably occurs, global Forensic Analysts and automated SIEM tools can rapidly correlate the attack timeline across a unified, standardized log format devoid of translation ambiguity. (為了確保當全球性的大型伺服器慘遭駭客屠殺時，無國界的「數位鑑識專家與自動化關聯系統 SIEM」，能免受該死的時差或語言翻譯之苦，以最快速度在一套絕對統一的日誌中『畫出時間軸以追蹤兇手』)
D. This requirement is purely to satisfy baseline testing metrics for Cross-Site Scripting (XSS). (純粹是為了滿足 XSS 弱點掃描器的測量底線)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是資安維運 (SecOps) 裡用血淚學到的教訓。在設定不可妥協的 **安全日誌與軌跡需求 (Security Logging Requirements)** 時，最大的惡夢就是日誌裡充滿了印尼文、日文的錯亂時區，導致在分析時宛如看天書。當跨國駭客攻擊爆發時，我們必須仰賴 SIEM (資安事件管理系統) 大砲或外部的救火專家來抽絲剝繭。因此，工程師下達了死命令：即使前端介面再花俏、使用再多語系，後端吐出來當證據的稽核與安全日誌 (Audit and Security Logs) 必須宛如死水般一致。強制使用 **共同的語言 (英文)** 與 **絕對統一時間系 (協調世界時 UTC)**，是保證事後電腦鑑識 (Forensics) 工具能順利畫出攻擊時間軌跡鏈、將散落全球一百台伺服器日誌完美關聯在一起的唯一方法。
    *   **為何 A 與 B 是干擾項：** 日誌存在的目的是為了給電腦或是鑑識專家找兇手用的，跟翻譯利益糾葛無關。而現代企業級軟體伺服器早就全面支援 UTF-8 以相容多國語言（日文、中文），這點字首儲存空間的消耗對現代大數據儲存池來說根本不值一提。
    *   **為何 D 是干擾項：** XSS 攻擊的起因是網頁前端沒有將使用者的惡意輸入進行中和編碼。它跟伺服器後端用哪國語言存文字檔日誌完全無關。

#### **18. A hardened executive draws a massive red circle around a sentence in your draft specification document and screams: "What the hell does 'The system must effectively resist most common network attacks' mean? How am I supposed to pay a QA firm to verify that vague nonsense?!" To correct this atrocious ambiguity and convert the fluff into a highly precise, "Testable Security Requirement" that an auditor can measure with a ruler, you should change it to which of the following?**
**(憤怒的主管在你的需求規格書圈起紅圈大吼：「『系統必須有效抵擋最常見的網路攻擊』這到底是個什麼鬼文字？你要我怎麼花錢請 QA 團隊來『驗證』這句充滿模糊廢話的空話？！」為了修正這場慘劇，將廢話轉變為稽核員可以用直尺測量的、高度精準的「可測試的安全需求 (Testable Security Requirement)」，你應該將它替換成下列哪一句話？)**
A. "The sheer robustness of this magnificent system ought to have the capability to perfectly intercept any inbound packets intended to cause us a minor inconvenience." (這套壯麗系統的純粹強健度，應該要有能力完美攔截任何意圖讓我們稍微不方便的入站封包)
B. "The software must mandate that every external input field utilize the most modern, non-lazy defense tools to check for XSS and other bad things." (軟體必須強制每一個外部輸入欄位都使用最現代化、不偷懶的防禦工具來檢查 XSS 和其他壞東西)
C. "The system MUST forcefully utilize strictly typed 'Parameterized Queries' to capture all variables before executing any outbound database requests, thereby mathematically eliminating the possibility of SQL Injection exploitation." (在執行任何對資料庫的連線前，系統【必須】強制使用嚴格定義型態的『參數化查詢 (Parameterized Queries)』來捕捉所有的變數，藉此在數學邏輯上徹底抹除 SQL 隱碼攻擊被利用的可能性)
D. "The security of the application needs to achieve a psychological threshold such that external hackers will feel it is extremely difficult to breach." (應用的安全性需要達到一個心理門檻，讓外部駭客覺得它極度難以攻破)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 和本領域第 10 題相呼應，一個及格的資安需求規格，除了要有強制力的動詞 (MUST/SHALL) 之外，最重要的是要能提供 **「防禦的具體手段 (Mechanism)」** 或 **「可測量的實體驗證標準 (Measurable Metric)」**。選項 C 是一段非常漂亮的安全程式編碼需求。它明確指定了要防禦的目標 (SQL Injection) 以及必須採用的極端具體技術手段 (強制實作所謂的 Parameters 參數化查詢或預編譯語句)。這讓 QA 團隊甚至可以用靜態原始碼自動掃描工具 (SAST)，去對照所有的資料庫連線語法，檢查是不是每一個 `Select` 指令都有乖乖使用參數化查詢。這就是所謂的「可供稽核、可受公評、精準測試 (Testable)」。
    *   **為何 A 是干擾項：** 「壯麗的系統」、「稍微不方便」？這種字眼比原本主管圈起來的廢話還要慘，它是一首毫無工程防禦意義的文學詩詞。
    *   **為何 B 是干擾項：** 「最現代化的防禦工具」這種描述在五年後就不再現代化了。「其他壞東西」更是糟糕透頂的含糊詞彙。到底 QA 用哪個掃描器掃出來才算及格？這句話充滿了無法被定義的灰色地帶。
    *   **為何 D 是干擾項：** 資安需求不能建立在「駭客的主觀內心感受」上。因為那是一個無法觀測、無法被撰寫成單位測試程式碼的幽靈指標。永遠要用具體的運算極限或防禦框架來寫規格。
