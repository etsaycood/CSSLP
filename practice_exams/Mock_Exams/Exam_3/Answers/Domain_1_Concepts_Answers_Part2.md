# 第三套全真模擬試題 (Exam 3) - 答案與詳解本
## 領域 1：安全的軟體概念 (Secure Software Concepts) (16題) - Part 2 (Q9-Q16)

---

#### **9. During an annual compliance audit, the auditor discovers that the application's core "User Password Reset" functionality requires a customer service representative to verbally ask the caller for their social security number, click an "override" button on their web dashboard, and then manually type a new, temporary password to give to the caller over the phone. The auditor heavily criticizes this manual, human-centric process as being highly susceptible to social engineering and operational errors. The auditor strongly recommends replacing it with a fully automated self-service email link system that completely removes the human representative from the loop. Which security design principle is the auditor advocating for?**
**(在一年一度如雷射光般苛刻的合規性大體檢中，那位冷若冰霜的外部查帳稽核官揪出了一條尾巴：他發現這家公司那最要命的『用戶忘記密碼重新大重置金鑰系統 (User Password Reset)』！居然還停留在史前時代！因為它【必須】由一位坐在客服中心戴著耳機的客服阿姨，像審問犯人一樣，透過電話『親口』去問客人的身分證字號。接著還要阿姨手動去點擊她那個網頁後台畫面上那顆危險的『上帝特權解鎖按鈕 (override button)』，再由阿姨親自用鍵盤『手工敲打出一串新的臨時大門密碼，最後透過電話唸給那個外頭不知道是不是詐騙集團的陌生人登入』！這名稽核官聽到這兒，當場氣得七竅生煙、大聲抨擊這種『度度仰賴活生生人類去手動決策』的爛流程，簡直是給騙子跟阿姨手殘犯錯送上門的大肥肉大開後門大放送 (highly susceptible to social engineering and operational errors)！稽核官下達死命令：『立刻把這些危險的客服人員從這條火線上全面撤除拔掉！全部給我換成一台沒有感情的自動化機器大水管！只要客人在網頁上輸入信箱，電腦程式就會毫無人情味地、全自動發射一封帶有魔法無人重置連結的信給對方去自救。人類絕對不准再插手這件事 (completely removes human representative from the loop)！』。請問這位稽核官是在狂熱佈道哪一條斬斷人類手殘風險的軟體保安聖經大教條？)**
A. Complete Mediation (每進出一次都要搜身安檢的完全仲裁)
B. Automatic Administration / Economy of Mechanism (simplifying and automating security processes to reduce human error) (這就是以消滅肉體怠惰風險為唯一真身、將防衛網全面化零為整、強硬推行拔除人類肉體手動決策的【防禦大自動化管理 (Automatic Administration) / 或是化繁為簡的極簡防禦機制大陣法 (Economy of Mechanism)】！)
C. Open Design (把系統攤在陽光下的開放設計)
D. Security through Obscurity (躲避在黑暗中不公開的隱藏神功)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是資安維運管理中常被忽略的全自動化核心精神：**「管理自動化 (Automatic Administration) / 化繁為簡 (Economy of Mechanism)」**。
    *   在資安防禦鏈條上，**「人類」永遠是最脆弱的環節！** 人類會被社交工程騙、會鍵盤打錯字輸入到別人帳號、會疲勞、會貪污。所以資安架構有一項鐵律是：凡是涉及到發放高特權 (如密碼重置、防火牆規則開通) 的工作，【只要能用腳本、機器與代碼全自動且標準化無感情地執行，就絕對不准讓人用手去點擊干涉】。機器的自動化重置信件系統，會發送獨一無二帶有過期時間的 Token 給註冊信箱，這消滅了客服阿姨被駭客花言巧語騙走密碼的巨大破洞，讓機制回歸最簡單不犯錯的狀態 (Economy of Mechanism 化繁為簡防止大頭症)。

#### **10. An organization implements a stringent physical and logical security framework to combat internal fraud. The policy explicitly mandates that the senior software engineer who writes and compiles the trading algorithm source code is structurally and irrevocably banned from possessing the administrative deployment credentials required to actually push that compiled code into the live production trading environment. This critical control requires two completely separate individuals from different departments to successfully deploy a system update. What is this foundational security principle called?**
**(一家吃過內賊大虧的大企業集團，為了斬斷那隻會從內部伸向金庫的髒手 (combat internal fraud)，他們不惜傾盡國力，布下了一套從實體門鎖到邏輯程式碼都極度變態嚴密的大陣法。這套教條式法典上，用鮮血刻著一條死規定：『那位腦袋絕頂聰明、負責坐在房間裡【親自敲打撰寫出那顆會自動賺錢殺人的神經末梢代碼大腦 (trading algorithm source code)、並且親手將其熬煮編譯出來的那位資深工程死神】！從他敲下第一行程式碼的那一天起！他就【從物理結構上，被永遠且絕對無法挽回地徹底剝奪、斬斷褫奪去了】他能夠真正握住、掌管那把將程式碼推進核彈發射井營運火線最高司令部鑰匙 (administrative deployment credentials) 的一切皇權！』。這個絕殺般的防衛控制鎖，生硬地逼迫：要完成一套系統大上線，就必須硬生生地拆夥！【絕對需要、強制綑綁兩名活生生、而且還隸屬於不同派系部門、平時老死不相往來的傢伙】！分別掏出身上的半塊兵符，兩人同時點頭，大門才會打開。這等防獨裁神功，尊號為何？)**
A. Need-to-Know (這只不過是蒙上眼睛只准看一條縫的須知防護)
B. Separation of Duties (Two-Man Rule) (這就是以制衡獨裁君王為終極目的！將大權劈成兩半的【職責分離大結界 (Separation of Duties, SoD) / 雙人核彈綁縛大陣 (Two-Man Rule)】！)
C. Job Rotation (這只是把大家換座位防無聊大輪調)
D. Least Privilege (給盡量少點鑰匙的剝削權力法)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「職責分離 (Separation of Duties, SoD) / 雙人控制 (Two-Man Rule)」**。這題情境描述了在 DevOps 或傳統 IT 中預防內鬼破壞的最經典案例。
    *   一個會寫程式又能自己發布上線程式的工程師，就像是一個既掌管金庫開關、又能自己批准自己撥款領錢的國防部長，他只要一念成魔，公司就毀了。
    *   SoD 的防護邏輯是：【將一個涉及重大利益或極度危險完整流程，像切蛋糕一樣，強制切割交由兩個沒有利益瓜葛的人 (最好是不同部門) 分別執行】。一個人寫扣 (Developer)，另一個人負責審核布署上線 (Release Engineer/Ops)。兩個人必須同時發瘋串通 (Collusion) 才有可能摧毀系統，這機率比一人發瘋小了幾萬倍。

#### **11. A developer is designing a custom session management module for a web application. To generate the unique "Session ID" cookie given to a user upon successful login, the developer decides to simply hash the user's username concatenated with the current timestamp (e.g., `MD5(username + time)`). A security architect immediately flags this design as fundamentally flawed because an attacker could trivially predict or bruteforce the sequence of future Session IDs if they know a victim's login time. To fix this, the architect mandates the use of a Cryptographically Secure Pseudo-Random Number Generator (CSPRNG). What specific characteristic is the architect demanding the Session IDs possess to prevent predictive attacks?**
**(一名工程師在打造自家網頁的『使用者憑證俱樂部出入通行證大派發系統 (session management module)』時，耍了個自私的小聰明。他在客人成功通關登入後，要發給那客人一張天下無數兩張的『VIP 大門房卡通行證 (Session ID)』。這名工程師為了省事，居然只是隨便拿了一把叫做 MD5 的大鐵槌，把這名客人的【名字】與他按下大門的【當下時間碼表 (timestamp)】，兩者像是揉麵糰一樣隨便混在一起敲一敲：`MD5(username + time)`，就當作這張通行證的神秘亂碼發出去了！沒想到！路過的資安大魔神架構師一看，立刻拔劍震怒，大吼這是一個會毀滅全站千秋大業的豆腐渣工程破洞！大魔神怒斥：『你這白癡！因為外面排隊的那些駭客殺手，只要稍微躲在暗處偷喵到受害者是幾點幾分進門的，再加上本來就知道他的名字！駭客就能像個會算命的先知一樣，【輕易算出、暴力破解並完美預判複製預測出】你未來幾張、甚至上一張發出去的所有大門房卡密碼數字組合 (bruteforce the sequence of future Session IDs)！從而完全不用密碼就能直接附身潛入客人的帳號裡把他的錢搬空！』。為了修補這個能被算命先生算出來的大黑洞，大魔神降下神諭：『你未來發的每張通行證！給我去用那【被雷電劈過、絕對無神可解的密碼學亂數大造幣神明機 (CSPRNG)】去生成！』請問大魔神這番死命令，唯一且極端追求的是這張房卡必須具備哪項讓算命算不出來的防禦神性？)**
A. High Entropy (Unpredictability / Randomness) (這就是在混亂世界中追求那永無止盡、無法捉摸的終極亂象：【絕對高熵大魔數 (High Entropy) / 無法預測之全視亂碼大陣 (Unpredictability / Randomness)】！)
B. Non-repudiation (不讓你耍賴的大印章)
C. Confidentiality (怕你偷看的大盲眼術)
D. Data Integrity (不怕資料被塗改大防偽印鑑)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **「高熵 (High Entropy) / 隨機不可預測性 (Randomness)」** 是密碼學與憑證發放 (Session ID generation) 中最致命也最容易被誤解的一環。
    *   **何謂低熵 (危險)：** 將 `使用者名稱` 跟 `現在的秒數時間` 加在一次拿去 Hash。因為時間是世界上最規律、最容易預先猜測的東西！如果駭客知道你昨天晚上八點登入過，他只要寫一個迴圈，從 8:00:00 一路算到 8:01:00 (這才 60 個組合)，他立刻就能算出你的 Session ID 是哪一個，然後直接把 ID 貼到自己的瀏覽器接管你的登入狀態 (Session Hijacking / Fixation 攻擊)。這種密碼就像是寫在臉上一樣好猜。
    *   **何謂高熵 (安全)：** 必須使用作業系統層面、最深不可測底層物理雜訊 (如滑鼠亂動軌跡微秒) 的 **密碼學安全偽隨機亂數產生器 (CSPRNG, 例如 `/dev/urandom`)** 來生出高達 128 bit 的一團「連神仙算力都完全猜不到下一張是什麼數字」的亂數符號字串。只有無法被預測的亂數 (高熵值)，才配當登入憑證通行證。

#### **12. A massive, global cloud provider guarantees a Service Level Agreement (SLA) of 99.999% ("Five Nines") uptime for their core object storage service. To achieve this extreme level of operational resilience against natural disasters or localized data center fires, the architecture is designed so that every single file uploaded by a customer is automatically and instantly replicated across three geographically distinct data centers spread across different tectonic plates. Which of the three core pillars of the CIA Triad is this extreme replication strategy primarily engineered to safeguard?**
**(一家掌控地球命脈的全球巨無霸雲端霸主大帝國，他們驕傲地向全世界的信徒降下了神聖誓言：『我們家最偉大的那座【無限存放空間大寶庫 (core object storage service，如 AWS S3)】！我們敢用命來跟你擔保！它具備了那連神都敬畏的「五個九」純金防震不滅大保證 (SLA 99.999% uptime，一年只會斷網不到 5 分鐘)！』。為了完成這個如同狂妄天威的誓言、去迎擊那連大自然地震與地獄業火肆虐狂燒整座機房都無法撼動的【極限營運大死神韌性 (extreme level of operational resilience)】。這座雲端大帝國的總神經架構，居然病態到了這種地步：當小明在外頭隨便上傳了一張只要 1MB 大小的無聊搞笑照片進這寶庫裡。這張照片居然在千分之一秒內！【被這座大陣如影分身般，全自動、無死角地同時瘋狂備份血影分身大複製，射向並深深鎖死在遠在地球端三個橫跨不同大陸板塊、地理上完全八竿子打不著的巨無霸核防空洞超級機房深處堡壘裡面！！】。請問，這等因為懼怕斷氣當機而發狂做出的『異地大陸板塊極限分身血影大備份戰略大陣法』。它是整本資安創世金字塔 (CIA Triad 三兄弟) 之中，哪一位大聖人教條的終極、純粹肉身顯現大法？)**
A. Confidentiality (機密大盾)
B. Integrity (防改數字資料的雷神之鎚大印)
C. Availability (這就是對抗天地俱滅、確保大門敞開永不死機永不關燈之【無尚可用性大陣 (Availability)】的終極降臨法陣！)
D. Non-repudiation (讓你簽了名就賴不掉的不可否認大印章)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「可用性 (Availability)」** 的終極定義：不僅是「系統現在能服務不當機」，更涵蓋了「當面對各種災難衝擊 (硬體故障、地震、DDoS 攻擊) 時，系統依然能夠屹立不搖，讓合法用戶在需要時，永遠能順暢無阻地存取他們要的資料與服務」。
    *   在雲端運算架構中，達成「高可用性 (HA) 與災難復原 (DR)」最強大且最暴力的神教解法，就是 **「跨地理分區的冗餘備份設計 (Geographically Distinct Replication)」**。一旦某個大洲的機房真的被飛彈炸火燒了，系統架構不用人類介入、連半點思考猶豫都不用。它會直接把全球客人的水管，瞬間切到另外一個位於不同大陸板塊的完整複製資料城繼續喝水分發。這完全不涉及掩飾資料 (機密性) 或是 防止被竄改 (完整性)。這純粹是在瘋狂維持系統的「不會死斷氣 (可用性 99.999%)」。這就是 CIA 三位一體中 Availability 最經典的火力展示。

#### **13. An application uses a central configuration file (`config.xml`) that dictates critical database connection strings and API keys. The operations team configures the file system permissions so that the application service account has "Read-Only" access to this file, while only the "Administrators" group has "Write" access. However, the application logic does absolutely nothing to verify if the file has been maliciously modified (e.g., by checking a digital signature or cryptographic hash) before loading it into memory at startup. If an internal attacker with admin rights modifies the file, which core security concept has the application failed to independently verify?**
**(有一隻肥大的應用程式，它的肚子裡深埋著一張名為 `config.xml` 的『絕殺中樞神經聖旨圖 (central configuration file)』。這張圖表上寫滿了這隻怪獸要去哪裡喝水、要去哪裡開大金庫後門的『資料庫連線天眼通密碼與尚方寶劍金鑰 (API keys)』！那些顧機房的老頭子們，自以為聰明地在這張聖旨外層套上了幾道物理大鐵籠：『這隻應用大怪獸這輩子只能用眼睛隔著鐵籠看 (Read-Only) 這張圖，只有那些掛著最高將軍牌子的長老內閣 (Administrators)，才有拿筆去圈改塗抹這張圖的權力 (Write)！』。但這群人卻蠢到了極點：這隻大怪獸每天早上起床開機通電時，它就只是大爺般地張開嘴，看都不看一眼地把這張極地聖旨給直接生吞活剝進神經肚子裡！這怪獸的程式【徹徹底底地、完完全全地從來沒想過要啟動任何一滴點大腦！去核對檢查這張圖紙上『是不是已經被人偷蓋了假印章、內容有沒有被半夜竄改大亂塗過 (例如：打上數位簽章查驗算命法或是用雜湊 Hash 值去校對防偽)』！】。完蛋了，如果今天晚上這家公司出了一個大內鬼、一個拿著將軍牌子的高階長老叛變！他溜進去機房，拿紅筆偷偷把聖旨上的連線指引改成了自己的邪惡大帳戶！隔天一早怪獸起床開機生吞下去！這隻怪獸的瞎眼愚蠢，是因為它徹底瞎死了整座大城牆上哪一道【核心防禦驗證大陣的大意失荊州？】)**
A. Confidentiality (防偷看的機密遮眼法)
B. Authentication (查驗你是誰的通關口令)
C. Data Integrity (這就是盲人瞎馬瞎吃毒藥下肚！徹底棄守了那去『無情核對內容真假有沒有被動手腳』的【至高數據完整防偽大陣 (Data Integrity)】防線！)
D. Non-repudiation (防耍賴不可否認大陣)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「資料完整性 (Data Integrity)」** 關注的是：『資訊在儲存或傳輸的過程中，是否能保證未經授權或非預期的「竄改、破壞、變造」』？
    *   這家公司靠著作業系統層面的權限控制 (Authorization / ACL, 管理員才能寫入) 加上了一層實體防線。但是！這是一個典型的軟體設計缺失：**「應用程式沒有自己去驗證輸入來源的完整性」**。在國防級的軟體架構中，光靠系統資料夾權限是不夠的。這隻怪獸軟體在每次喚醒讀取 Config 檔 `xml` 之前，應該要啟動密碼學引擎算一次這張聖旨的 Hash (雜湊值)，然後跟自己大腦出廠時死背下來的真理 Hash 核對。只要這兩組亂碼有半個字母對不上 (代表這張紙昨天晚上被人動了手腳竄改過內容！)，怪獸就應該立刻大叫崩潰死當拒絕啟動，寧死不屈。這個「核對資料有沒有變造」的步驟，就是 Data Integrity 最傳神的驗明正身動作。

#### **14. A Chief Information Officer (CIO) is giving a presentation to the board of directors arguing against spending $5 million on a newly proposed, ultra-advanced AI threat detection system. The CIO presents a risk analysis report proving that even if the company suffered a total, worst-case scenario data breach of their specific customer database, the absolute maximum financial impact (fines, lawsuits, and lost business) would only amount to $2 million. Therefore, spending $5 million to protect a $2 million asset is financially irrational. Which fundamental risk management concept is the CIO employing to justify rejecting the security investment?**
**(一位大公司的『皇城大總管 (資訊長 CIO)』，如今正滿臉肅殺之氣地板著臉，站在那供奉著皇帝大長老們的董事會最高大殿上！他在一場大提案中，拍著桌子、不惜以下犯上，死死阻擋回絕了下面那群將軍吵著要『花掉高達五百萬黃金國庫 (5 million)，去買一套瞎扯淡的頂天級無敵 AI 大怪物防禦偵測巨砲系統』的敗家子計畫！這名大總管從袖口掏出了一份蓋著血紅大印的絕殺『算命大軍推演風險報告』，用力砸在文武百官面前。報告上血淋淋的算式寫著：『睜大眼睛看清楚！根據最毀滅的情境，就算明天我們家大門被隕石砸碎、就算我們家那個破爛客戶資料金庫被天底下所有駭客扒光屠殺殆盡大洩漏！我們家因為被客戶提告、被政府罰款跟虧錢不幹所面臨的【最極端崩潰悲慘大結局的總死亡賠償金】，算破天最高也就是這區區的【兩百萬黃金 (2 million) 鉅款】罷了！你們這群大傻Ｂ將軍想提議花足足五百萬去替這個只值兩百萬的破帳篷買保險，這他媽的根本就是白癡與腦袋進水 (financially irrational)！！』這名大總管能夠在大殿上振振有詞地揮下終結大刀，擋下這筆軍購。是因為他爐火純青地發動了哪一套商場算命兵法風控之術？)**
A. Risk Avoidance (這不過是看到洞就縮頭繞道不敢做的逃避兵法)
B. Cost-Benefit Analysis (ROI of Security Controls) (這就是一分錢一分貨、用極限商業算盤敲得震天響！無情將刀刃用在風險最大刀口上的【終極成本效益經濟大算盤推演大法 (Cost-Benefit Analysis) / 防禦控制設施那死神般的投資報酬率 (ROI of Security Controls)】之道！)
C. Threat Modeling (這只是在那紙上談兵劃箭頭兵推畫怪物的威脅兵棋)
D. Vulnerability Scanning (那只是派一隻掃地機器人去掃漏水的掃瞄法)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「成本效益分析 (Cost-Benefit Analysis)」** 是大企業投資資安預算最血淋淋的鐵律，也是所有 CISSP/CSSLP 總監主管第一天要學的核心思想。
    *   在資安領域，我們有一條死標準公式定理：【**你花在資安防禦保全機制上的建置費用總成本 (Cost of the safeguard)，絕對、不准、不可以 > 大於！> 該資產本身暴露在危險中被炸毀時你能容忍的極限損失 (Value of the Asset / ALE - Annualized Loss Expectancy)**】。
    *   如果那台保護客戶資料庫的主機裡面，所有的資料就算全被賣到黑市或者公司倒閉破產總共才損失 200 萬美金。那你卻去花 500 萬美金去買各種最強的防火牆、AI 系統跟養五十個保鑣來保護它，這在資源管理上是絕對的失敗。在資安世界裡，沒有 100% 的安全體系，永遠都是在用「合理的 CP 值防線」去防堵威脅，不能把錢砸到大於資產本身價值。這叫 Cost-Benefit Analysis 防禦經濟學。

#### **15. An organization's HR system contains thousands of highly sensitive employee salary records. The security policy dictates that the "Apprenticeship Program Director" may log into the system to view the names of all current apprentices, but the system must absolutely blind them to the 'Salary' column, displaying only asterisks `***` or denying access to that specific field entirely. However, the system must allow the Director to successfully view the 'Department' and 'Start Date' columns for those exact same records. This highly granular, column-level restriction of visibility is an enforcement of which principle?**
**(一家皇朝巨型企業的人力資源 (HR) 大金庫系統裡，深藏著這家公司上萬名太監宮女官員最赤裸裸、最要命機密的『底褲薪資發財數字 (employee salary records)』！皇朝法典上有一條絕殺禁令明文規定針對那位『菜鳥學徒大教頭 (Apprenticeship Program Director)』：這名教頭拿著他身上的令牌登入點開花名冊系統時。系統只准！給他看所有那些菜鳥弟子的『名字、入宮日期跟單位部門』！但是！！這名教頭的權力在面對那神聖的『【那欄薪資俸祿到底領多少錢 (Salary) 的欄位】』深淵面前，這系統必須猶如黑魔法迷霧般，【當場極度冷血暴虐地戳瞎這教頭那對貪婪的雙眼 (blind them)】！！系統要嘛直接把薪水欄位這行字直接抹去不見、要嘛就是必須強硬打上一排猶如亂碼死光般的馬賽克星號『***』死死遮蔽封印住！但是這名瞎眼教頭居然還能正常看那一筆同一列菜鳥紀錄旁邊的其他所有部門文字。這等能精準到把一整張大桌布上的一格小『欄位 (column-level) 的視野給精準閹割挖瞎掉』的刀法佈局。這是為了神聖捍衛並實踐哪一條極端潔癖的大護法？)**
A. Separation of Duties (分一半工作給別人的職責分離)
B. Complete Mediation (每過一扇門都要檢查的完全仲裁)
C. Need-to-Know (Granular Data Masking/Access Control) (這就是讓你如同瞎瞎子摸象、剝奪多餘好奇心！被推上神壇的【極限知其所需/只讓你看到你該看的大法則 (Need-to-Know)】！也同時是在資料庫維度上，刀法精準且病態地執行那令神魔屏息的【極致顆粒度精細欄位挖眼級大法 (Granular / Column-level Access Control) 與機密資料就地遮罩大霧 (Data Masking)】之終極神技！)
D. Cryptographic Hashing (拿去攪拌機攪爛不可逆的雜湊演算法)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「須知原則 / 必須知道法則 (Need-to-Know)」** 是「最小特權 (Least Privilege)」在 **『資料與資訊視野 (Information Flow & Visibility)』** 維度上的延伸發展。
        *   Least Privilege 是：「我不給你『修改』這張表的權限」。
        *   Need-to-Know 則是：「我知道你工作需要讀這份名單。但我就是【只讓你看到你那幾格所需的資料】。就算這張表上還有其他你同事的薪水，我也要拿奇異筆把那些薪水塗黑 (給你看星星符號)，因為這不關你的事，這不是你能勝任工作所『必須知道』的事」。
    *   而要實現這個最高原則，在應用程式架構中，必須仰賴極為高深的**「極細微 / 顆粒度極端細緻存取控制 (Granular / Column-level Access Control)」** 和 **「資料遮罩 (Data Masking / Redaction)」**。系統在呈現畫面給該角色看之前，會像拿過濾網一樣啟動黑魔法：把 SQL 資料庫撈出來的那份超大資料結構中，精準動手腳把不關這角色事的 Salary 這個物件屬性，給硬生生挖瞎掉、或是把字元變換成星號遮住，這等絕活完美捍衛了 Need-to-Know。

#### **16. A company develops a proprietary industrial control system (ICS) protocol to communicate with physical machinery on a factory floor. In a misguided attempt to prevent attackers from sending malicious commands, the development team decides not to use industry-standard encryption like TLS. Instead, they invent a secret, undocumented mathematical algorithm to scramble the commands. They argue that because the algorithm is a closely guarded corporate secret and not published on the internet, hackers will never figure out how to crack it. Which notoriously flawed and universally condemned security anti-pattern is this engineering team relying upon?**
**(一家製造大工廠養了一幫自以為能隻手遮天的小工程師！他們自己發明了一套像天書一樣『公司私有內部專屬的工廠遙控機器怪手打架大暗語 (proprietary ICS protocol)』，用來躲避外邊駭客的控制。在一個極度白癡且誤入歧途的大走鐘計畫裡，這群工程師為了自以為能讓外邊來的網軍大駭客聽不懂他們在亂叫什麼。他們這群狂妄小子居然拍桌決定：【去他的！老子我們才不屑去用那個全地球全宇宙幾十億人都在用、經過一萬種數學大砲炸過都還天下第一強那套標準大將軍 TLS 傳輸核爆加密防衛網！】。相反地，他們幾個人躲在廁所裡，閉門造車自己拿紙筆畫符發明了一套宣稱天下第一、且【打死也不在網路上公開、絕不給任何人看說明書的神祕怪獸亂數數學密碼大洗牌公式 (secret, undocumented mathematical algorithm) 去攪爛語音指令】！他們幾個還不要臉地洋洋得意跟老闆吹牛鼻：『老闆安啦！因為我們這個瞎編的神功大公式，現在被我們鎖進公司最深的抽屜保險箱裡成為全台最高獨家小機密！這輩子都沒被發佈上網路上。外頭的駭客瞎子找都找不到，怎麼可能算得出破綻解鎖攻破我們這套死結？不信來戰！』！。請問這群愚蠢如豬的工程師大陣，正瘋狂且不知死活地騎乘並信仰那條在整個地球資安大歷史上，【最惡名昭彰、最被萬人唾棄遺臭萬年且必然被反噬滅局的送死反安全異端死路大教派 (security anti-pattern)】？)**
A. Defense in Depth (一重保護包一重的縱深大防禦)
B. Security through Obscurity (這就是那遺臭萬年！猶如把頭埋進沙堆裡以為別人都看不見、靠著『沒人知道所以很安全』那極度自我感覺良好且必死無疑的荒謬騙局大邪端：【靠躲貓貓、沒人知道這小秘密來當護身符自嗨的安全掩耳盜鈴大陣 (Security through Obscurity / 以隱匿蔽目騙來的心安防安控法)】！)
C. Kerckhoffs's Principle (演算法應該全部脫光給世人檢驗看找死路的柯克霍夫大道)
D. Least Privilege (給盡量少點鑰匙的剝削權力法)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是資安考題中出現頻率極高、也最容易被無知工程師在現實中犯的大死穴：**「以隱匿為安全 (Security through Obscurity)」**。
    *   這條大謬論的核心思想是：「只要我把大門的金鑰插孔偷偷藏在地毯下面 (隱藏機制/藏拙)、或是只要我自己發明一種奇怪的怪異長相打不開鎖，因為沒人知道怎麼開，所以就沒有人進得去！小偷找不到自然就是絕對安全」。
    *   **為何這會帶來毀滅：** 任何依賴「程式碼、協定架構或演算法是個秘密不被人看見」來充當防衛主力的爛設計，在現代強悍的駭客逆向工程 (Reverse Engineering) 跟拆解大砲面前，根本撐不過一個禮拜。一旦駭客在系統找到那個小小的開關密道、或者某個離職員工在論壇上把你家那個自製破公式洩漏出去貼出來了。你那自以為堅不可摧的無敵城牆，就會在瞬間分崩離析如同沒穿底褲一樣，這是一種病態的防禦大破網！真正的安全，應該是遵守它完全相反的反面道理：也就是選項 C 大名鼎鼎的「柯克霍夫大原則」！
