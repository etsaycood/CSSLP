# 第四套全真模擬試題 (Exam 4) - 答案與詳解本
## 領域 3：安全的軟體需求 (Secure Software Requirements) (18題) - Part 1 (Q1-Q6)

---

#### **1. A business analyst is writing user stories for a new payroll application. They write: "As an HR manager, I want to be able to export employee salary data to CSV so I can generate reports." From a security perspective, what critical element is missing from this requirement that represents an "Abuse Case" or "Evil User Story"?**
**(一名專門負責幫金庫寫許願池清單的衙門書記官 (business analyst)，他在新的發薪水系統願望單上寫下：『身為人資大掌櫃，我希望能把全城人的薪水單，全部打包成幾百箱的公文卷宗出庫 (export to CSV)，這樣我才好回家用算盤慢慢算帳 (generate reports)』。但站在安防大將軍的眼中！這張只有「純潔善意」的許願單，它致命地遺漏了那名為【『惡意劇本 (Abuse Case) / 魔王反向許願單 (Evil User Story)』】的恐怖暗黑元素！請問，這份願望單到底少了哪一句能防微杜漸的保命符？)**
A. The specific SQL query needed to extract the data. (這是工匠自己要去想的技術細節，這不叫惡意許願單)
B. A corresponding story defining what *cannot* or *should not* happen (e.g., "As a malicious insider, I want to export data for employees outside my department, which the system must prevent"). (這就是那句能把魔鬼擋在門外的終極神聖保命符：【『一張相對應的、明確定義出「絕對不准發生之恐怖災難」的反向詛咒單』】！例如：『身為一個潛伏在內部的死內鬼 (malicious insider)，我希望能偷偷把【那些根本不歸我管、別的部門所有無辜老百姓的薪水單】全部偷印出來帶回家！而這個系統，【必須不計一切代價給我死死攔住這個動作 (system must prevent)】！』。這就是把安全需求 (Security Requirement) 寫成惡意劇本的經典範例！)
C. The exact mathematical encryption algorithm (e.g., AES-256-GCM) to be used for the CSV file. (這是後期的設計與實作決定，在寫 User Story 的業務需求階段，不需要標明到 AES-256 這麼細的技術名詞)
D. The precise UI button design for the "Export" function. (按鈕長方形還是圓形，這跟安防的防範內外鬼毫不相干)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 探討在需求擷取階段，如何編寫 **「惡意使用案例 (Abuse Cases / Misuse Cases)」** 或 **「邪惡使用者故事 (Evil User Stories)」**。
    *   **正向需求 (Functional/User Story) 的盲點：** 業務分析師 (BA) 通常只會寫出「好人想做什麼事 (Happy Path)」。但系統被駭客攻破，往往是因為沒人去設想「壞人會利用這個正常功能來幹嘛」。
    *   **Abuse Case 的價值：** 它是從攻擊者的視角出發。如果系統有一個「匯出 CSV」的強大功能，那它也是一個完美的「資料外洩 (Data Exfiltration)」管道。所以安防團隊必須在需求階段，強迫加上反向的 Security Requirement (例如：必須防止越權匯出、必須加上匯出數量上限的 Rate Limiting 監控)，這才是完整的安全需求分析。

#### **2. A development team is tasked with building a healthcare application that must comply with the Health Insurance Portability and Accountability Act (HIPAA). The product owner asks the security architect how to translate the massive HIPAA legal textbook into actionable software tasks. Which statement best describes the relationship between Compliance, Security Policies, and Software Requirements?**
**(一支準備打造『國家最高太醫院電子病歷庫 (healthcare application)』的工匠大軍，接到了朝廷頒布、厚達八千頁、違法就直接砍頭的【『HIPAA 醫療隱私終極大法典 (Compliance)』】。帶頭的工頭抱著這本像山一樣重的法典，崩潰地跑去問安防大將軍：『將軍啊！這法典上面全都是之乎者也的律師火星文！我們這群只會敲釘子寫程式的苦力，到底要怎麼把它變成可以天天照表操課的造車藍圖 (actionable software tasks)？』。請問大將軍該如何精準地點出：那遠在天邊的『朝廷法規 (Compliance)』、公司內部的『家規 (Security Policies)』、以及最後落在工匠手上的『施工清單 (Software Requirements)』，這三者到底存在什麼樣的鐵血血脈傳承關係？)**
A. Compliance regulations directly generate ready-to-code functional software requirements. (這就像是說「憲法」會自動變成「警察怎麼開罰單的操作手冊」一樣荒謬。法條是死板龐大的，它不會告訴你「這個網頁要寫幾行程式碼」)
B. Compliance regulations inform organizational Security Policies, which are then translated into specific, verifiable Security Requirements for the software. (這就是這三者之間無縫接軌的黃金大漏斗法則：【『由朝廷大法 (Compliance) 來指導公司要頒布什麼樣的家規 (Security Policies)。然後再把這套家規，像翻譯機一樣，精確翻譯成可以讓工匠直接看懂、並且可以用機器去驗證對錯的：終極施工藍圖指令 (verifiable Security Requirements)！』】。例如：法規說「要保護病人隱私」 => 政策翻成「病歷庫必須加密」 => 需求落實為「開發者，你這台資料庫給我套上 AES-256，不然就算你出廠不合格！」)
C. Software Requirements dictate the organizational Security Policies, which lawmakers then use to write Compliance regulations. (這完全反了！這是造車工人去指揮皇帝怎麼立法，大逆不道)
D. Development teams should ignore high-level Compliance regulations and only focus on technical OWASP guidelines. (雖然 OWASP 很有用，但如果你造出來的車不符合朝廷合規 (Compliance)，整間公司還是會被抄家倒閉，絕不能無視合規)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 釐清了 **合規 (Compliance) -> 政策 (Policy) -> 需求 (Requirements)** 的階層與轉譯過程。
    *   **Compliance (合規的外部性)：** 如 HIPAA, GDPR, PCI-DSS。它們是政府或產業聯盟寫的法律文件。它們只告訴你「What to achieve (必須達到什麼境界)」，例如「保護傳輸中的敏感資料」。
    *   **Security Policy (組織的內部政策)：** 公司的資安長 (CISO) 閱讀了這些法規，制定出適合本公司的《高階資訊安全政策》。例如「本公司規定：所有對外傳輸皆須使用 TLS 1.2 以上」。
    *   **Software Security Requirements (軟體安全需求)：** 這是最底層、給開發者看的「How to do (怎麼做)」。系統分析師會把公司政策翻譯成 JIRA Ticket：「User Story: API Server 必須關閉對 SSLv3, TLS 1.0/1.1 的支援，且只允許特定的強 Cipher Suites 進行連線，否則 Build Failed」。這才具有可測試性 (Testability)。

#### **3. During the requirements gathering phase for a new e-commerce platform, the team decides that user sessions must automatically expire after 15 minutes of inactivity to prevent session hijacking if a user walks away from a public computer. How should this constraint be formally classified?**
**(在為新開張的名牌大商城 (e-commerce platform) 籌備『大門放行許可證 (requirements gathering)』的會議上。大將軍拍板定案了一條龜毛的死規矩：【『只要在商城裡瞎逛的客人，連續十五分鐘像石頭一樣站在原地發呆不講話 (15 minutes of inactivity)！那他脖子上的那張金牌通行證，就必須在第十五分鐘的最後一秒鐘，直接炸裂失效 (automatically expire)！以防他去上廁所時，被旁邊的乞丐拿走金牌冒用身分 (prevent session hijacking)！』】請問，在將軍那本防衛大兵法名冊上，這條用來約束時間與行為的強硬鐵鍊，被正式歸類為什麼標籤？)**
A. As a Functional Requirement. (功能性需求是指「這台車能發射飛彈」、「這家店能結帳算錢」。也就是業務功能 (What it does)。而十五分鐘閒置踢除，是約束與規範條件)
B. As a Non-Functional Requirement (NFR). (這就是那藏在背後保平安、規範系統『該用什麼姿勢、符合什麼體質來運轉』的：【『非功能性大需求 (Non-Functional Requirement, NFR)』】！安全需求 (Security Requirements) 在絕大部分的兵法書中，都被歸類在這裡！它就像是這台車的「防撞係數」、「剎車距離」一樣，不是車子能不能跑的問題，而是它跑起來安不安全的約束條件 (How well it operates)！)
C. As an Abuse Case. (惡意劇本是描寫壞人會做什麼事，而這道十五分鐘的死命令是抵禦手段，不是攻擊劇本本身)
D. As a Service Level Agreement (SLA). (SLA 是保證商城每年只有幾分鐘不會開門做生意的停機賠償合約，跟客人閒置多久要被踢出門完全無關)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 在需求工程中，**「安全需求」通常被歸類為「非功能性需求 (NFRs, Non-Functional Requirements)」** 的一個子集。(其他 NFR 還包含效能 Performance、可用性 Availability、擴充性 Scalability 等)。
    *   **功能 (Functional) vs 非功能 (Non-Functional)：**
        *   **Functional (功能)：** 系統「必須做什麼 (What)」。例如：系統必須能讓使用者放進購物車並刷卡結帳。
        *   **Non-Functional (非功能/品質屬性)：** 系統「必須具備什麼樣的整體品質或限制 (How)」。例如：結帳過程【必須在 2 秒內完成 (效能)】，且【必須使用 AES 加密信用卡 (安全)】。閒置 Timeout 機制也是限制系統運作行為的安控要求，屬於 NFR。

#### **4. A project team is defining the Data Retention Policy for a new customer service portal. The business wants to keep chat logs "forever" to train future AI models. The privacy officer states that under GDPR, chat logs containing personal data can only be kept as long as necessary for the original purpose of customer support (e.g., 90 days). How should the lead architect resolve this conflict during the requirements phase?**
**(一支準備打造『天下第一客棧迎賓問卷台 (customer service portal)』的大隊，正在為了要不要燒毀客人的對話紀錄 (Data Retention Policy) 而爆發激烈的內戰！客棧的算盤大掌櫃貪婪地叫囂著：【『把這些客人說的每一句話都給老子留下來！留他個一萬年 (keep chat logs "forever")！因為老子未來要拿這些客人的隱私去煉丹，餵給我們下個世紀的無敵智障機器人吃 (train AI models)！』】但此時，掌管朝廷生死刑罰的護法面色鐵青地拔出尚方寶劍：【『你這畜生！根據朝廷最新頒布的《歐洲保護老百姓八代祖宗大隱私法典 (GDPR)》。這些包含隱私的卷宗，只要客人結完帳滾蛋了，頂多只能留三個月 (e.g., 90 days)！剩下的敢多留一天，我就把你家客棧封了！』】請問，身為主持這場會議的總工頭，面對這種要錢還是要命的大衝突，他在寫需求時該如何一槌定音定生死？)**
A. Implement the business requirement ("keep forever") because AI training is critical to the company's future revenue. (為了賺錢而公然違抗朝廷的《GDPR》。客棧等著面臨全球營收 4% 的毀滅級天價罰款，這是在帶領全隊走向滅頂深淵)
B. Implement the privacy requirement ("delete after 90 days") because legal and regulatory compliance mandates supersede conflicting business desires to hoard data. (這就是能保住全家人項上人頭、不被朝廷滿門抄斬的唯一活命大鐵律：【『在任何大衝突面前！朝廷頒布的《絕對法律底限與強制合規天條 (legal and regulatory compliance mandates)》，絕對、且毫無懸念地凌駕並輾壓那些只為了貪圖蠅頭小利的商業白日夢 (supersede conflicting business desires)！』】。如果合規說要在 90 天後燒毀，那系統的需求就必須寫下【自動定時毀滅炸彈】的程式碼。隱私凌駕商業，這是現代資訊戰場的唯一生存法則！)
C. Ask the developers to decide during the sprint planning phase. (這簡直是總工頭推卸責任、把大將軍的決定權扔給底層工匠去猜拳的笑話。工匠怎麼會懂深奧的歐盟法典？)
D. Keep the data forever, but encrypt it, as encrypted data is completely exempt from GDPR retention rules. (這是一個巨大的法盲誤區！加密只是防賊拿去用，但 GDPR 規定的是「超過保留期限，連你這家客棧老闆自己都不准擁有這個資料的存在」，加密過期的資料沒刪除，依然違反了 GDPR 的資料最小化與期限原則！)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是軟體需求工程中處理 **合規衝突 (Compliance Conflicts)** 的最高指導原則。
    *   **GDPR 的核心精神：**
        1.  **目的限制 (Purpose Limitation)：** 你因為 "客服" 收集資料，就只能做 "客服"。不能偷偷挪用去 "訓練 AI 賺大錢" (除非使用者額外給了明確同意 Consent)。
        2.  **資料最小化與儲存限制 (Data Minimization & Storage Limitation)：** 資料一旦完成了它原本收集的目的 (客服結案)，就必須刪除或匿名化，絕對不能無止盡的囤積 (hoarding)。
    *   **Legal > Business：**在所有的需求優先級 (Prioritization) 排序中，**法律法規與合規要求 (Regulatory / Legal Requirements) 永遠是最高優先級 (Must-Have)**。違法帶來的罰款與營運停擺風險，遠超過資料練兵帶來的潛在商業價值。

#### **5. When defining Access Control requirements for a military intelligence application, the requirement states: "A subject may only read an object if the subject's clearance level is strictly greater than or equal to the object's classification level." Which formal Access Control Model does this requirement describe?**
**(在為兵部打造一個可以管理幾百萬刺客名單與將軍密報的『終極大內國防密報系統 (military intelligence app)』時。需求規格書上用紅字寫下一道死命令：【『聽好！在這個系統裡，不管是會走路喘氣的兵將 (subject)，還是被鎖在櫃子裡的文件 (object)！都必須被強迫烙印上階級標籤！【只要這個小兵腦袋上的階層級別分數，沒有大於或是等於你想借的那份公文的危險分數層級 (clearance level >= classification level)】！那大門就絕對一秒鎖死封殺！』】請問，這套猶如軍規般絕對階層森嚴的古老存取陣法模型，尊號為何？)**
A. Discretionary Access Control (DAC) (這是小老百姓誰寫檔案誰就作主的自由分發權，無階層概念)
B. Role-Based Access Control (RBAC) (這是看你名片角色分群組的陣法，不是用這種嚴格等級數字比大的階梯式防護)
C. Mandatory Access Control (MAC) / Bell-LaPadula (這就是以鐵血無情、由國家強制打下絕對階層標籤之：【『最高強制存取大防線 (Mandatory Access Control, MAC) / 以及著名的只能往下看不能往上看的「貝爾-拉帕杜拉大保密模型 (Bell-LaPadula)」』】！)
D. Attribute-Based Access Control (ABAC) (這更進階且看情境，不是純粹的層次比對)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「強制存取控制 (Mandatory Access Control, MAC)」** 以及其具體的機密性模型 **Bell-LaPadula**。
    *   **MAC 的特徵：** 它是基於「標籤 (Labels)」。Subject 擁有 Clearance (如 Top Secret)。Object 擁有 Classification (如 Secret)。系統會強制檢查這兩個標籤。
    *   **Bell-LaPadula (BLP) 的 "Simple Security Rule (No Read Up)"：** 題幹描述的正是這條規則。一個 Secret 級別的人，不能去讀取 (Read) Top Secret 的文件 (因為他不夠格)，這保護了機密性 (Confidentiality)。

#### **6. A team is developing a B2B API service. The requirement states: "The API must authenticate the client application, not the individual human user." Furthermore, the client must be able to periodically request a new, short-lived access token without requiring human interaction. Which standard protocol is the absolute best fit for fulfilling this specific security requirement?**
**(一支精稅大軍正在建造一座『大財團專屬的機器人自動交易通關口 (B2B API service)』。門禁需求書上是這麼寫的：【『聽好！這個通關口，它要查驗的身分，【是來跑腿的那個沒血沒淚的送貨機器人小弟 (client application)】！而不是站在它背後納涼的那個活生生的人類大老闆 (not human user)！』】。而且這道死命令還加上了一個極度苛刻的條件：【『這隻機器人小弟，它必須學會自己每隔半天，就自動跑到簽證官那邊換一張全新的短期通關令牌 (request a new short-lived access token)！這整個換發過程，【絕對不准有任何活人跑去幫它填表單或是按印章 (without human interaction)！】它得自己全自動搞定！』】請問，在江湖上，哪一本通訊與通行證大典，是為了這種沒血沒淚的『機器接腳本純自動通訊』而量身打造的極致神器？)**
A. SAML 2.0 (SAML 雖然龐大，但它主要是設計給「活生生的人類 (Browser Profile)」在網頁之間跳來跳去作單一登入使用的。它如果要給純機器人自動通訊會非常的笨重且難以實作)
B. OAuth 2.0 (specifically the Client Credentials Grant flow) (這就是名震當代、專門為了斬斷人類枷鎖，讓機器與機器之間能自動互相信任、並換取無窮盡通關令牌的：【『OAuth 2.0 之純『機器小弟自主認證通道』 (Client Credentials Grant flow)』】！這套機關的奧義就是：直接給這隻伺服器小弟一組背在背上的『機器憑證與密碼 (Client ID & Secret)』。當通行證過期時，小弟只要自己秀出這組密碼對接，就能無限期、不用透過任何人手與瀏覽器，瞬間拿到全新的出入令牌！完美契合純 B2B 自動化通訊的需求！)
C. OpenID Connect (OIDC) (OIDC 是蓋在 OAuth 裡面的延伸套件，但 OIDC 的唯一目的是為了證實那個【背後活生生的人是誰 (Identity of the end-user)】。現在我們這題明確講了『不查人類，只查這隻送貨的機器程序』，所以不需要用到專查人臉的 OIDC)
D. HTTP Basic Authentication (把帳號密碼寫死在每次送貨的馬車外殼上，不僅落後且危險，完全無法滿足『短期生命週期令牌換發 (short-lived access token)』的高端要求)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **OAuth 2.0 的 "Client Credentials Grant" (客戶端憑證授權流程)**。
    *   **Machine-to-Machine (M2M) 需求：** 這是現代微服務架構 (Microservices) 或 B2B API 最常見的安全需求。沒有瀏覽器 (Browser-less)，沒有使用者輸入帳號密碼的地方。
    *   **Client Credentials Flow 的運作：** 授權伺服器 (Authorization Server) 直接把 Client (例如一個背景 Cron Job 腳本) 視為資源的擁有者。腳本直接拿自己的 `client_id` 和 `client_secret` 去換取 `access_token`，完全不需要使用者的參與。
    *   SAML (選項A) 通常用於企業級的 SSO (Web Browser SSO Profile)。OIDC (選項C) 用於身分驗證 (Authentication)，重點是核實使用者的身分 (產生 ID Token)。Basic Auth (選項D) 因為每次都要傳輸長期靜態密碼，安全性極低，不符合現代短期 Token 的精神。
