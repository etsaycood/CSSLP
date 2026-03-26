# 第三套全真模擬試題 (Exam 3) - 答案與詳解本
## 領域 3：安全的軟體需求 (Secure Software Requirements) (18題) - Part 2 (Q10-Q18)

---

#### **10. An architect is reviewing the requirements for a new military communications application. The document specifies that the application must guarantee exactly three core properties: 1. No unauthorized person can read the messages. 2. Neither the sender nor receiver can falsely deny having sent or received a specific message. 3. The system must cryptographically prove that the message was absolutely not tampered with in transit. Which three specific security requirements are being mandated here?**
**(一名頂尖架構大祭司，正緊盯著那份攸關國家生死存亡的『全新三軍通訊神盾應用程式 (military communications application)』的最高絕密需求聖旨。這張羊皮紙上，以雷射般精準的死令，強硬宣判這套系統【打死都必須、不計代價地保證達成】下列三項絕對不容侵犯的核心神聖特質結界：1. 【天王老子來了，只要他身上沒有長官發的令牌大印 (unauthorized person)，他就連一個字都別想看懂這封信裡寫了什麼偷天換日的機密 (read the messages)！】 2. 【傳令兵跟收信將軍，這輩子誰都別想在法庭上裝死耍賴！發送者絕對無法狡辯說 "這封退兵令不是我下的"，而接收者也絕對無法裝死抵賴說 "我根本沒收到這封進攻信" (falsely deny having sent or received)！】 3. 【這套系統必須搬出神明級的密碼學證據，當庭鐵血保證這封信在兩座山頭之間飛鴿傳書的半路上，【絕對、完全沒有、連一個標點符號都沒有】被敵軍的間諜給悄悄攔截下來偷改成 "今晚投降" (not tampered with in transit)！】。請問這三道如同雷霆般劈下的神聖護法指令，正精準呼喚並強制對應了哪三尊名震江湖的『特種安全防禦需求大神』？)**
A. Availability, Non-repudiation, Confidentiality (可用性、不可否認性、機密性)
B. Confidentiality, Non-repudiation, Integrity (這就是完美無瑕、威震天下的特種安控三神柱大集合：【機密性大神 (Confidentiality)、不可否認大印章神 (Non-repudiation)、以及完整防偽真理神 (Integrity)】！)
C. Authentication, Authorization, Accounting (AAA) (這只是門神在查你身分證、看你有幾把鑰匙、跟結帳算你花多少錢的 AAA 帳房三兄弟配置)
D. Least Privilege, Separation of Duties, Defense in Depth (這是最小極限特權、把工作切開兩人做的職責分離、還有一層包一層的縱深大陣)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是一題非常經典的需求術語 (Terminology) 映射題。
        1.  "No unauthorized person can read (未授權者無法讀取)" = 防偷看 = **機密性 (Confidentiality)**。通常透過加密 (Encryption) 實現。
        2.  "Neither sender nor receiver can falsely deny (任何一方都不能說謊耍賴)" = 防抵賴 = **不可否認性 (Non-repudiation)**。通常透過數位簽章 (Digital Signatures) 實現。
        3.  "Not tampered with in transit (半路沒有被竄改過)" = 防偷改 = **完整性 (Integrity)**。通常透過雜湊 (Hashing/MACs) 實現。

#### **11. A requirement states: "The software must incorporate an automated mechanism to continuously scan the public internet for exposed credentials belonging to our employees, and if found, automatically enforce a global password reset for those compromised accounts." This requirement is a proactive defense mechanism directly mapped to mitigating which specific, pervasive threat actor strategy?**
**(這道帶著濃厚血腥味的戰略命令上如此宣告：「這套軟體必須在肚子裡，活生生縫進一套『猶如鷹眼般，在半夜裡永不睡眠、全自動且瘋狂地去那骯髒混亂的全世界公開大網際網路與暗網黑市上 (public internet)』，四處掃視尋找、嗅探有沒有任何屬於我們公司員工那已經被人扒光衣服、賤價販賣或洩漏張貼在路邊牆上的『帳號密碼狗牌 (exposed credentials)』！聽好！只要這套鷹眼雷達一嗶嗶叫，發現了我們自家人的名字在黑名單上亮起紅燈 (if found)！系統這頭【必須直接、當場、毫不猶豫地】發動猶如核彈級的大反制：『瞬間將這個已經被感染奪舍的大兵帳號給物理性摧毀重製！強制發動全球大清洗令 (automatically enforce a global password reset)，逼迫他立刻繳回舊鑰匙換新鎖 (compromised accounts)』！」。請問這道帶有濃厚『主動出擊、殺氣騰騰的防禦制裁大需求』。它所直接鎖定瞄準、並試圖在源頭就掐死的，是現今哪一套如蝗蟲過境般氾濫的『駭客偷吃步恐怖戰略 (pervasive threat actor strategy)』？)**
A. Cross-Site Scripting (XSS) (這只是在網頁留言板上偷偷塞滿噁心反光小強的跨站腳本術)
B. Distributed Denial of Service (DDoS) (叫一千萬台被附身的殭屍來塞爆你家大門的水管崩潰戰)
C. Credential Stuffing / Password Reuse attacks based on compromised external breaches (這就是最惡毒、專門靠『撿路上死人骨頭、拿別人外洩的鑰匙來開我們家大門』的無本生意：【『帳密填充大滿貫猛攻 (Credential Stuffing)』 與 『靠著員工把所有密碼都設一樣的惰性發動的連鎖偷家密碼重用大攻擊 (Password Reuse attacks)』】！)
D. SQL Injection (用單引號狂戳資料庫眼睛的注射拔金庫法)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是現代資安防禦 (如 Azure AD / Entra ID 的 Identity Protection) 非常前衛的 "**洩漏憑證偵測 (Leaked Credentials Detection)**" 需求。
    *   **駭客策略：** 為什麼我們要一直上網掃描員工的密碼有沒有被偷？因為現在最主流的攻擊不是硬破解你的系統，而是 "**Credential Stuffing (憑證填充)**"。駭客去暗網買了一批「Yahoo! 或 LinkedIn 外洩的五千萬組帳密」。因為人類極度懶惰，高達 60% 的人會把他在 Yahoo 用的密碼，一字不改地繼續用在「公司的登入系統」上 (Password Reuse)。駭客只要寫個腳本，拿外面買來的這把舊鑰匙，直接插進你們公司的伺服器大門轉一轉，大門就直接開了。
    *   防禦這個威脅的最佳反制需求：主動去暗網買這些名單，只要發現自家員工的密碼流落在外，立刻強迫他改現在公司的密碼。C 精準描述了這個攻防對戰。

#### **12. A development team is tasked with writing the software for an automated ATM machine. They define a strict matrix. Row 1: "User" (can withdraw funds, can check balance). Row 2: "Bank Teller" (can restock cash, cannot withdraw funds). Row 3: "Global Admin" (can update ATM firmware, can reboot machine). By formally mapping specific roles to their exact, allowed positive actions before any code is written, what essential security requirement artifact is the team creating?**
**(一支被委以重任、正在打造那一台台會吐鈔票的『全自動無人銀行提款大怪獸 (ATM machine)』的菁英火槍隊！為了不讓這怪獸最後亂吐錢發瘋，他們在寫下第一行咒語之前。非常嚴肅地、拿著一把滴血的羽毛筆，在一張羊皮紙上畫出了一個界線分明、猶如種姓分離審判大陣般的『極其死硬冷血之權力分配大矩陣棋盤 (strict matrix)』！這棋盤上這樣規定：第一條血脈：『路人小兵角色 (User)』：他被允許可以從怪獸嘴裡拔出鈔票 (withdraw funds)、也可以偷看肚子裡還剩多少錢。第二條血脈：『老家派來的銀行搬運工 (Bank Teller)』：他有特權可以打開怪獸後門的保險箱塞滿補給品 (restock cash)，但是他【大逆不道絕對不准】碰怪獸嘴裡的客人鈔票半根寒毛！第三條血脈：『帶著皇冠的全球神級管理員 (Global Admin)』：他有能把怪獸大腦挖出來重灌系統 (update firmware)、甚至能拔電源掐死怪獸重新復活 (reboot) 的通天特權！請問，這群火槍兵【在開工動土以前】，就透過這張猶如階級大判官一般的『神仙與奴隸對照表格 (formally mapping specific roles to their exact, allowed positive actions)』，他們正是在親手勾勒出哪一份【資安聖典中最不可或缺之安控權力大門票名冊產物 (security requirement artifact)】？)**
A. A Threat Model Data Flow Diagram (這只是一張畫著水溝怎麼流進城裡的兵推大圖)
B. A Key Risk Indicator (KRI) report (那只是老闆用來看今天會不會賠錢的紅綠燈溫度報告)
C. A Role-Based Access Control (RBAC) Requirements / Access Control Matrix (這就是震懾八方、將眾生萬物死死禁錮在自己那一畝三分地裡的【死神大判官名冊：基於角色的存取控制大定讞 (Role-Based Access Control, RBAC) 需求 / 與那無情的大門鎖頭檢驗對照表大矩陣 (Access Control Matrix)】！)
D. A Privacy Impact Assessment (PIA) (那是專用來評估病歷有沒有被路人看見的隱私大風暴衝擊報告 PIA)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「存取權制矩陣 (Access Control Matrix)」** 和 **「基於角色的存取控制 (RBAC)」**。
    *   在資安需求定義中，要落實「授權 (Authorization)」，最標準且最常被要求產出的文件就是 **Access Control Matrix**。這是一張表格 (通常是 Excel 或是設計文件裡的表格)，橫向 (Rows) 列出軟體中所有的**「角色 (Roles/Subjects，例如 User, Teller, Admin)」**，縱向 (Columns) 列出系統中所有的**「動作或資源 (Objects/Permissions，例如領錢、補鈔、重啟機器)」**。然後在交會點打勾或打叉。這份矩陣文件清楚定調了誰能做什麼、誰不能做什麼。如果開發者沒有這份 Matrix，他們就會在 Code 裡面亂寫權限邏輯 (例如忘記擋下 Teller 領錢的按鈕)，這會引發難以收拾的越權漏洞 (Privilege Escalation)。

#### **13. During a requirements workshop, the stakeholders declare: "The application must be available 99.9% of the time, even during peak holiday shopping seasons, and must be able to recover from a complete database catastrophic failure within 4 hours without losing any committed transactions." This critical statement explicitly dictates which two specific types of non-functional operational requirements?**
**(在一場猶如血肉橫飛的『建國需求搶奪圓桌大會戰 (requirements workshop)』上，那群出了錢的財閥老闆們 (stakeholders) 拍桌怒吼，對著台下那群嚇得發抖的工程師們下達了死命令：「聽著！這台印鈔機應用程式，【必須、極限保證】它一整年要有高達 99.9% 的時間都在敞開大門接客賺錢 (available 99.9%)！！就算是在那猶如喪屍圍城、幾百萬人瘋狂湧入的『超級黑色星期五聖誕購物大狂歡旺季』，這破機器也絕對不准給我閃黃燈斷氣當機！不但如此，萬一哪一天真的碰上小行星撞地球，把後面那座超級大金庫資料庫給徹底炸成了一片焦土廢墟 (complete catastrophic failure)！這破系統也【必須】要在短短『猶如跟死神搶命的 4 個小時大限內 (within 4 hours)』給我滿血原地復活！並且！那裡面每一個客人已經刷卡的血汗錢紀錄，【連一個銅板、一筆已咬死的交易都不准給我搞丟蒸發 (without losing any committed transactions)！】」。請問！老闆這段如同天雷劈下、強加在將軍脖子上的發飆宣言。它裡面極端精準且血淋淋地，死咬著哪【兩條】猶如軍令狀般的『系統死活維運非功能大需求 (non-functional operational requirements)』？)**
A. Authentication and Authorization (這只是在門口查驗身分證跟配給鑰匙的通關需求)
B. Availability (Uptime SLA) and Disaster Recovery (specifically Recovery Time Objective [RTO] / Recovery Point Objective [RPO]) (這就是猶如『神之不滅金身』與『地獄重生大法』的極限霸王條款大合體：【雷打不動之大門永開大可用性承諾 (Availability / Uptime SLA 99.9%)】，以及那與閻王搶時間的【終極災難復原防護大限 (Disaster Recovery) / 特別是那要在四小時內重開機的『起死回生大限時鐘 (RTO)』、以及連一塊錢記憶都不准丟的『時空回溯救回大界線 (RPO)』】！)
C. Confidentiality and Integrity (這兩位大神只保證文件不要被偷看也不要被偷改數字，但不保證機器不會斷電當機)
D. Usability and Maintainability (這只是要求畫面有沒有比較好按、還有機器破了洞好不好補土的維護性需求)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：**
        1.  "Available 99.9% of the time (維持 99.9% 的正常開機時間)" 非常直白，這是 **可用性 (Availability)** 需求，在商業合約上稱為 **SLA (Service Level Agreement)**。
        2.  "Recover within 4 hours (在 4 小時內起死回生)"，這定義了系統死掉後可以搶修多久，這術語叫 **RTO (Recovery Time Objective / 復原時間目標)**。
        3.  "without losing any committed transactions (不能搞丟任何已經存檔的交易資料/連最新的一秒鐘都不能弄丟)"，這定義了你從備份磁帶倒資料回去時可以容忍流失多少過去的資料，這術語叫 **RPO (Recovery Point Objective / 復原點目標)**。這裡的要求是 RPO = 0 (零資料遺失)。
        RTO 與 RPO 兩者共同構成了 **災難復原 (Disaster Recovery, DR)** 的最核心需求指標。

#### **14. A global retail company is building a mobile application that will explicitly track the real-time, physical GPS location of children under the age of 13 to help parents locate them in large shopping malls. Before technical architecture can even begin, the legal and compliance team halts the project, stating the team must first conduct a massive, formal, legally required evaluation to determine how this extremely sensitive tracking data will be collected, stored, shared with third parties, and eventually deleted, to ensure it doesn't violate laws like COPPA. What specific type of formal analysis is being demanded?**
**(一家掌控全球市場的零售大巨頭，正異想天開地打算鑄造一款『超神準雷達追蹤手機 App』。他們的目標非常令人毛骨悚然：這款 App 要【極端赤裸、二十四小時猶如背後靈一般，死死釘住並即刻追蹤並廣播那些『全地球未滿 13 歲稚嫩小屁孩 (children under the age of 13)』的身上那代表著活體肉身座標的真實物理 GPS 訊號 (real-time, physical GPS location)】！他們美其名說是為了讓爸媽在跟山一樣大的破購物中心裡不怕把小孩搞丟。這駭俗的計畫才剛端上兵棋桌、就連一塊磚頭都還沒開始蓋 (Before architecture begin)。那群被嚇到心臟病快發作的帝國法務長老總裁辦公室，立刻發出瘋狂的奪命連環死命令，直接拔掉全場電源強迫專案完全停工剎車 (halts the project)！長老怒吼著說：『你們這群找死的瘋狂工程師！你們難道不知道追蹤小屁孩是會引爆全宇宙核爆級的官司末日死罪嗎？在這計畫敢繼續往前推動半寸之前！你們全隊給我立刻去【啟動並上繳一份史無前例、如天書般厚重且被國家法律拿刀架在脖子上死逼著要交出來的『極機密數據生殺大權全面大普查報告 (massive, formal, legally required evaluation)』】！這份報告必須給我清清楚楚地把腸子剖開交代：我們到底打算怎麼像吸血鬼一樣去吸取這些小屁孩極端致命的行蹤數據 (collected)、如何把這批炸藥藏進我們的山洞金庫 (stored)、會不會轉手把這批鮮血偷偷賣給外頭那些無良的小販第三方 (shared)、以及最後到底什麼時候會放火把這堆犯罪證據給徹底燒爛挫骨揚灰 (eventually deleted)！我們必須用命擔保這一切絕對這輩子都他媽的不會踩到像美國《兒童線上隱私大保護法大魔王 (COPPA)》這種一旦違規就直接抄家滅族的紅線！』請問，法務大長老這番雷霆震怒要求交出來的這份「專門衡量隱私爆炸威力」的史詩級生死大報告，尊號為何？)**
A. Open Source Software (OSS) License Audit (這只是拿放大鏡去挑那些不用錢軟體上面有沒有寫版權聲明大字報的智財大抽查)
B. Privacy Impact Assessment (PIA) / Data Protection Impact Assessment (DPIA) (這就是那一紙能決定專案生死、讓全歐洲法官都為之瘋狂的終極護身符大檢定：【絕對隱私權風暴爆炸衝擊超級大評估 (Privacy Impact Assessment, PIA) / 又或是那個歐盟 GDPR 祖宗親自頒發的『神聖資料保護大劫難死神評估大典 (Data Protection Impact Assessment, DPIA)』】！！)
C. Dynamic Application Security Testing (DAST) (這只是裝作駭客狂點網站滑鼠，看系統會不會噴出錯誤畫面的動態大盲測)
D. Code Quality Review (那是幾個工程師拿著茶杯，互相嫌棄對方寫的迴圈不夠漂亮的程式喝茶大會)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「隱私衝擊評估 (Privacy Impact Assessment, PIA 或 DPIA)」**。
    *   在處理 PII (包含更嚴格的 13 歲以下兒童隱私 COPPA、或歐盟 GDPR) 時，法規強制要求企業在設計系統**「之前」**，必須進行 PIA。
    *   PIA 的核心就在審查系統對資料生命週期 (Data Lifecycle) 的處置：你 **收集 (Collect)** 了什麼？保存在哪 (Store)？會保留多久 (Retention)？會不會分享給外部廠商 (Share)？最後何時銷毀 (Delete)？
    *   題目描述的情境 (追蹤小孩 GPS) 是最高度的隱私風險。如果不做 PIA 釐清法規紅線就直接寫程式，一旦 App 上線，公司將面臨毀滅性的鉅額罰款。

#### **15. A requirement dictates: "When the application writes sensitive passwords to the backend database, it must NEVER use irreversible hashing algorithms, because the legacy mainframe billing system requires retrieving the actual, plain-text password to authenticate the user for billing cycles." A security engineer immediately flags this requirement as incredibly dangerous and fundamentally violating modern security best practices. However, because it is a hard business requirement driven by legacy systems, what specific type of requirement conflict is occurring?**
**(這張沾滿了歷史塵埃與固執的專案需求老羊皮卷上，大逆不道地寫了一條讓所有資安專家看了都想挖掉自己眼珠子的變態死需求：「當我們這群小工程師，把全天下最最最神聖不可侵犯的『客戶登入心臟密碼 (sensitive passwords)』灌進後台大地窖資料庫時。聽好了！【絕對不准！永遠不准！死也不准】給我開動那台近代最引以為傲的『絕對不可逆、絞肉機大雜湊加鹽防禦演算法 (irreversible hashing algorithms)』去把它攪爛！為什麼呢？因為我們公司地下室那台從恐龍時代活到現在、負責每個月收錢開發票的『祖宗級算盤老主機大怪獸 (legacy mainframe billing system)』！它那生鏽的腦袋根本看不懂雜湊亂碼。它它它...它竟然可恥地【必須每個禮拜硬生生伸進大地窖裡，親手抓出那赤裸裸、連一塊遮羞布都沒穿的完全原始活體明文密碼 (actual, plain-text password)！】，然後親自把這串字塞進它嘴裡嚼一嚼，才能認得這個客人是誰、並順利進行扣款！」一名正義的資安巡捕一看，當場差點沒休克死過去！他揮舞著大刀狂罵：「這簡直是把城門鑰匙送給路人！徹底強暴且踐踏了我們這個時代所有被證明的神聖資安防線最高指導原則！！」然而，就算這巡捕再怎麼發瘋怒吼，這條需求卻是那台負責幫整間公司賺錢收帳的老怪物系統所發出的不可違抗的『賺錢大死命 (hard business requirement)』，不照做公司就沒錢發薪水。請問，這等猶如冰與火之歌般，雙方都拿著刀互砍、卻又僵持不下的極端需求大車禍，上演的是哪一齣專有名詞的『大衝突 (conflict)』戲碼？)**
A. Financial Conflict (沒錢買伺服器，或者是大家為了預算分贓不均在搶錢的財務大打架)
B. A conflict between a Business/Functional Requirement (need cleartext for legacy integration) and a Security Requirement (passwords must be hashed). (這就是那場最經典、每天都在血汗工廠上演的『賺錢部門與警察部門的終極生死大對決』：【在『要賺錢發大財的商業老主機功能性大需求 (Business/Functional Requirement - 要求脫光光看明文去接那該死的老系統)』 與 『那條打死不退、保護身價性命的安全大防線需求 (Security Requirement - 密碼必須被狠狠攪爛雜湊！決不妥協)』 之間所爆發的世紀大車禍衝撞矛盾 (conflict)】！)
C. Regulatory Conflict (那是政府新法規跟舊法規在打架的官僚大矛盾)
D. Usability Conflict (這是在吵那個小按鈕應該放在左邊還是右邊比較好按的膚淺順手大吵架)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「業務需求 (Business/Functional Requirement)」與「安全需求 (Security Requirement)」之間的衝突 (Conflict)**。
    *   這是 CSSLP 在 Requirements 階段極為強調的管理難題。
    *   **Security (資安) 的真理：** 密碼絕對不能存明文，必須使用 PBKDF2 或 Bcrypt 進行加鹽雜湊 (Hashing)。資安工程師的反彈是完全正確的。
    *   **Business (業務) 的現實：** 那台老主機不懂 Hash，如果沒有明文密碼它就不做事，公司就收不到錢。
    *   這兩條需求直接對撞，無法同時被滿足。在真實世界中，團隊必須開始做 "Trade-off (妥協分析) / Risk Acceptance (風險接受)"，例如：妥協這台資料庫用可逆加密 (AES 雙向加密) 而不是 Hash，然後把加密金鑰鎖進硬體安全模組 (HSM)，來勉強平衡這場商業與安全的世紀大車禍衝突。

#### **16. To ensure a new e-commerce website cannot be successfully crippled by thousands of malicious attacker-controlled computers sending junk traffic to exhaust the server's resources, the requirements specify: "The system must utilize a specialized cloud-based traffic scrubbing service capable of automatically filtering and dropping millions of malicious junk requests per second before they reach our origin servers." This requirement is engineered precisely to mitigate which specific type of attack?**
**(為了死死確保這座剛落成的金碧輝煌之『全新網路吸金大商城 (e-commerce website)』，絕對不會被外面那個變態大魔王所操控的一千萬台【身上發著惡臭、如喪屍般發瘋被下蠱的遠端死靈機器人大軍 (malicious attacker-controlled computers)】給徹底輾壓淹沒！這群駭客喪屍，平時最擅長的就是像土石流一般，朝著城門瘋狂吐出幾十億噸沒有意義的『垃圾封包口水大洪流 (setting junk traffic)』，企圖把商城大門水管給活生生塞爆、把守門伺服器老爺爺的體力給徹底榨乾致死 (exhaust the server's resources)！為此，防禦大典裡寫下了這條宛如搬出如來神掌般的鎮妖大需求：「聽好了！我們這座金庫的防護罩，【必須花重金去租用且掛載那片飄在雲端上的『超神聖終極封包大清洗過濾吸塵大陣 (cloud-based traffic scrubbing service)】！這座大陣必須要有能吞吐天地之氣的能力，它要在戰場的最外圍，也就是這群喪屍那幾百萬發毒砲彈還沒摸到我們家大門磚頭的半空中 (before they reach our origin servers)！就能全自動把每一秒鐘飛過來的那幾百萬顆垃圾毒球 (millions of malicious junk requests per second)，給精準過濾辨識出來，然後像拍蒼蠅一樣把它們全部拍碎丟棄 (filtering and dropping)！」這條武裝到牙齒的防洪巨型引水需求，它是如同精準導引飛彈般，專門被派去阻擋殺死哪一頭威懾天下的特定末日大怪獸攻擊法？)**
A. Cross-Site Request Forgery (CSRF) (騙你在不知情下按了刪除帳號按鈕的跨站請求偽造)
B. Phishing (發電子郵件騙阿公阿嬤點假網址的釣魚信騙術)
C. Distributed Denial of Service (DDoS) (這就是用百萬萬殭屍大軍塞爆你全家水管，讓你直接斷氣崩潰死亡的終極人海戰術：【大名鼎鼎、毀城滅國的『分散式阻斷服務大癱瘓屠殺陣 (Distributed Denial of Service, DDoS)』】！)
D. Advanced Persistent Threat (APT) exfiltration (那是一群國家級特務潛伏兩年在你家慢慢偷搬金塊的細膩 APT 偷竊術)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **阻斷服務攻擊 (DDoS, 分散式阻斷服務)**。
    *   DDoS 的本質就是「耗盡資源 (Resource Exhaustion)」，駭客控制殭屍網路 (Botnets) 同時對你的伺服器發送假流量。
    *   對抗 DDoS 最有效的「需求架構」之一，就是不讓流量直接打進你家的小機房 (Origin server)，而是先把流量導向 Cloudflare 或 AWS Shield 等在雲端邊緣 (Edge) 提供清洗服務 (Traffic scrubbing service) 的超級大廠。這些清洗中心有海洋般的頻寬吸收垃圾，過濾出正常的客人流量再導回你家。這正是需求中明確描述的防禦手段。

#### **17. A team is using the STRIDE threat modeling framework early in the requirements phase to brainstorm potential security requirements. They are analyzing a hypothetical attack where a hacker intercepts the unencrypted network communication between the mobile app and the server, and stealthily changes a user's transfer amount from $10 to $10,000 without either party realizing until it's too late. Which specific letter in the STRIDE acronym does this exact attack represent, directly driving the requirement for TLS encryption?**
**(一支精銳部隊正在『防禦需求大地圖開拓階段』，圍著火爐，搬出那本流傳自古老微軟大帝國的防禦九陰真經：【STRIDE 兵棋推演大框架 (STRIDE threat modeling framework)】！他們正如火如荼地敲著腦袋，在大爆發激盪各種可能出現的惡魔威脅與對應的神聖防禦結界！此時，桌面上擺出了一個令人毛骨悚然的假想戰局推演模型：『想像一下！如果今天有一名精通隱形術的黑魔法刺客，他躲在暗巷裡，死死攔截卡住了那條【可憐的手機 App 與遠方總部伺服器之間，完全沒穿大不入加密隱形外衣、大咧咧裸奔的空中通訊電波訊號線 (unencrypted network communication)】！當這名小老百姓只是想匯個微不足道的『10 塊錢美金買便當 ($10)』。這名刺客這傢伙，居然在中途以光速一般的手法，悄悄地、一聲不響地！把那張從空中飄過去的匯款單表格上的數字，拿奇異筆偷偷多畫了三個零！硬生生改成了【一萬美金的大豪賭 ($10,000)】！(stealthily changes amount)！而且還施下了障眼法，讓匯款的跟收錢的雙方，都被蒙在鼓裡，直到存款見底才崩潰發現！』請問！在這本神聖的 STRIDE 框架之六字真言縮寫裡面，這招猶如在半途換掉包裹內容物、神不知鬼不覺的【竄改大調包邪典之術】，正好是不偏不倚、死死對應了哪一個字母大魔王？而正是為了斬殺這頭魔王，才逼出了我們必須全線強制點亮【啟動 TLS 全域傳輸終極防改密碼結界 (TLS encryption)】的這個救世主需求？)**
A. S - Spoofing (假冒成你阿罵來借錢的欺騙偽裝大法 Spoofing)
B. T - Tampering (這就是那神不知鬼不覺、在半路上把你的牛奶偷換成毒藥的【中途掉包竄改大毒手 (Tampering)】！代表著完整性 (Integrity) 的徹底淪喪崩潰！)
C. R - Repudiation (做了壞事卻能在法庭上耍賴說不是我幹的死不認帳功夫 Repudiation)
D. E - Elevation of Privilege (本來只是個洗碗工，卻自己偷掛上國王名牌跑去開保險箱的權力大耀越境界 Elevation of Privilege)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **STRIDE 威脅模型 (由微軟發明)** 中的 **"T" 代表 Tampering (竄改)**。
    *   STRIDE 分別代表：Spoofing (偽造身分), **Tampering (竄改資料)**, Repudiation (否認), Information Disclosure (資訊洩漏), Denial of Service (阻斷服務), Elevation of Privilege (權限提升)。
    *   「在未加密的網路上中間人攔截，把十塊錢改成一萬塊」這是攻擊了資料的 **完整性 (Integrity)**。而在 STRIDE 框架中，對應破壞完整性的威脅就是 **Tampering (竄改)**。為了反制 Tampering，開發團隊必須生出對應的安控需求：「使用 TLS 傳輸加密與 MAC 雜湊校驗」。

#### **18. An organization is bidding on a contract to develop a web application for the US Department of Defense. The Request for Proposal (RFP) strictly states that the software MUST be evaluated and certified according to the rigorous standards of the Common Criteria for Information Technology Security Evaluation (ISO/IEC 15408). To meet this standard, the vendor must create a highly formalized, 100-page document precisely defining the unique security threats the software will face, the environment it operates in, and the specific security objectives it aims to achieve. What is the official name of this required Common Criteria document?**
**(一家野心勃勃的兵工廠組織，正摩拳擦掌、準備殺入那水最深、錢最多的『美國國防大五角大廈部 (US Department of Defense)』，去搶奪開發一套超級兵器大網頁系統的天價大標案合約 (bidding on a contract)。然而，那張燙著金色圖騰國徽的『死神的邀標書大戰令 (RFP)』上，用鮮血般紅字粗暴無比地寫著一條絕對不通融的霸王死命令：『聽好！你們這群猴子打造出來的這些破程式碼，【絕對必須！打死也必須！】被牽去我們軍方廣場上，按照那威懾全球、極限嚴格神聖且毫無破綻的【國際資訊技術安全大審判共同準則大典 (Common Criteria, ISO/IEC 15408)】的最高標準，去接受那猶如扒皮抽筋般的終極大洗禮拷問與純金認證大評估 (certified according to the rigorous standards)！』。為了有資格跨過這道地獄大關檢定，這個想發財的包商，必須在那群將軍面前，恭恭敬敬地先上一份【厚達猶如電話簿般、刻板嚴謹到極點、極度官僚又法言法語的百頁生死狀大文書】！這份無比沉重的手冊裡面，必須以神之眼的角度，精準且病態地圈出這套軟體這輩子到底會招惹到哪些長相奇特的『獨特致命妖怪大威脅 (unique security threats)』、它會降生在多麼險惡的『沼澤環境生態系中 (environment specifies)』、以及它這輩子注定要扛起哪些『斬妖除魔的具體神聖保安大宿命目標 (specific security objectives)』！請問在美國軍方這套《Common Criteria》的黑魔法名詞字典裡，這份能決定生死的『自家軟體防禦宿命自我介紹白皮書』那響噹噹的官方尊號為何？)**
A. Service Level Agreement (SLA) (那只是承諾客人一年當機不超過五分鐘要是當了賠死你的老土商業合約)
B. End User License Agreement (EULA) (這是印在安裝光碟背面，密密麻麻叫你同意才能按下一步的最終霸王破條款)
C. Protection Profile (PP) / Security Target (ST) (這就是在那神聖共同準則祭壇上，唯一能證明你身分的祭品大卷軸：【《保護這產品的輪廓大畫像 (Protection Profile, 簡稱老大哥 PP)》 / 又或是那份針對你自己這台特製機器的專屬《安全狙擊死神大目標宣告書 (Security Target, ST)》】！)
D. Software Bill of Materials (SBOM) (那只不過是廚師在交代今天用了哪頭豬跟什麼鹽巴的開源材料清單)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **ISO/IEC 15408 共同準則 (Common Criteria, CC)** 是全球政府與軍方 (如美國 DoD) 採購軟硬體的最高安全檢驗標準。
    *   在 CC 認證的官僚與標準流程中，有兩個最核心的需求定義文件：
        1.  **Protection Profile (PP, 保護剖繪)：** 這是政府/採購方定義的「通用需求藍圖」。(例如：政府發表一份針對 "所有軍用防火牆" 應該要多強的 PP 規格書)。
        2.  **Security Target (ST, 安全目標)：** 這是廠商要拿去考試時，自己寫的應考自我宣告書。廠商會在這份百頁文件裡描述：「我這台 "超級無敵防火牆 3000 型"，它的環境如何、它面臨什麼威脅、並且它如何能百分之百完美滿足長官您那份 PP 規格書的要求」。
    *   這題考的正是這兩個 CC 認證專屬的術語。當廠商要將自家軟體送去評鑑時，就必須準備 ST 來宣告系統的 security objectives 和 threats。
