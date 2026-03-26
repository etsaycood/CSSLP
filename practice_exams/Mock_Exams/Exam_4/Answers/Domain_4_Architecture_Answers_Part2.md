# 第四套全真模擬試題 (Exam 4) - 答案與詳解本
## 領域 4：安全的軟體架構與設計 (Secure Software Architecture and Design) (18題) - Part 2 (Q7-Q12)

---

#### **7. A monolithic application is being refactored into microservices. The architect decides that instead of every microservice maintaining its own user database and handling password hashing, a dedicated "Authentication Service" will be created. All other services will delegate login requests to this single service. Which secure design principle is being utilized?**
**(一支準備把那座大如山岳的『巨無霸獨棟千層摩天大樓 (monolithic application)』，徹底給炸平拆夥，改建成兩百間『散落四方、各自為政獨立小茅屋 (microservices)』的工匠大拆遷隊。帶頭的總架構大仙指出了一條康莊大道：【『諸位！如果我們讓這兩百間小茅屋裡，每家都自己養一本帳冊密碼簿、各自躲在棉被裡研究怎麼加密老百姓的臉孔 (every microservice handling password hashing)。那這兩百間茅屋遲早會有一百間因為學藝不精被人破門而入！這太愚蠢了！從今天起！這座微型商城裡，【只准設立唯一一座名為『天下第一神聖驗臉查名大天壇 (dedicated Authentication Service)』的機關！】其他一百九十九家小茅屋的掌櫃，只要看到有老百姓想買東西買到要掏密碼時，一律叫他去天壇排隊蓋章 (delegate login requests to this single service)！』】。請問。大仙這套把天下驗臉大權統一集中收歸中央的神鬼陣法，是應驗了祖師爺留下的哪一句安防箴言真理大奧義？)**
A. Principle of Least Privilege (最小權限是不讓小茅屋掌櫃拿到天壇的鑰匙，但大仙這套陣法是建立一個全新的「專責驗明大總管服務器本身的存在」，這已經跨越到了機制的集中層次)
B. Economy of Mechanism (and Centralized Security Controls) (這就是名垂千古，讓兩百家小茅屋免去鑽研深奧密碼學之苦的無上大真理：【『化繁為簡之機制經濟大奧義 (Economy of Mechanism) / 與絕對極權式統一中央安防大管轄 (Centralized Security Controls)』】！這句真理的本質就是：【越複雜的齒輪陣列，就越容易卡死生鏽！把天下最難、最會出人命的密碼與雜湊大難題 (Authentication)，讓一個「全世界最懂密碼學的神仙 (Authentication Service)」專注去解就好！】。只要這唯一的神仙不出錯，全天下兩百家小店鋪就永遠不會因為密碼被破而遭難。這大幅極度降低了整個大商城被駭客攻破的攻擊面積面！)
C. Security by Obscurity (隱匿式安全是把天壇藏在地下室不讓人看見，但這種集中式的驗證大門往往是最顯眼的存在，它是用硬碰硬實力防禦的，不是靠隱身)
D. Fail-Safe Defaults (預設失效防護是萬一天壇倒了，小茅屋預設是把門關上還是打開，這與集中建構天壇的決策目的不同次元的防護)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「機制的經濟性 (Economy of Mechanism)」** (保持設計的簡潔)，以及其衍生的 **「集中式安全控制 (Centralized Security Controls)」** 的架構實務。
    *   在微服務架構 (Microservices Architecture) 演進的初期，最容易犯的錯誤就是 "分散式認證"：讓所有的 OrderService, InventoryService, PaymentService 自己去連線資料庫驗證帳號密碼。
    *   這直接違背了 "Economy of Mechanism" (設計必須保持簡單)。因為每個服務的開發團隊都要懂怎麼寫 bcrypt 或 Argon2 雜湊。只要有一個新手開發者寫成 MD5，整個系統的密碼防線就崩潰了。
    *   **架構解法：** 抽離 (Decouple) 出一個專門的、集中化的 Identity Provider / Authentication Service (身分/認證服務。如 Keycloak 或 AWS Cognito)。其他所有服務都只透過 JWT 或 OAuth Token 來**「信任 (Delegate)」**這台唯一機器的判斷。這使得安全機制的維護、升級變得極度簡單且統一。

#### **8. In a Threat Modeling exercise, an architect draws a Data Flow Diagram (DFD). A dotted red line is drawn separating the "Public Internet" from the "Internal Corporate Network," representing the firewall. In threat modeling terminology, what is this dotted red line called?**
**(在一場旨在未卜先知的『尋龍點穴大風水圖繪畫法會 (Threat Modeling exercise)』上。大仙拿著一枝硃砂筆，在那張畫滿了城池水管跟地下道的黃色宣紙 (DFD) 上。他沿著那座名為【防火牆大銅門】的邊緣，用力地畫下了一道血紅、斷斷續續的『虛線大長城 (dotted red line)』！這道紅色長城，赤裸裸、血淋淋地把圖紙外圍那名為『強盜與惡鬼肆虐之荒野 (Public Internet)』的死亡區，跟圖紙內部那名為『純潔無瑕白兔村 (Internal Corporate Network)』的淨土，硬生生地劈成了兩個世界！請問！在風水點穴的古老辭典裡，這條決定了全村人生死存亡、劃清界線的紅色虛線，專有名詞為何？)**
A. An External Entity (外部實體是在紅色虛線外面，準備要把火球丟進白兔村的強盜本人，他是方塊圖，不是這條線本身)
B. A Data Store (資料庫是白兔村裡面裝紅色蘿蔔的平行線圓筒，不是用來切開世界的線)
C. A Trust Boundary (這就是那道名震千古、只要跨越一步就是萬劫不復、隔開了天堂與地獄的：【『絕對神聖大信任邊界 (Trust Boundary)』】！這條紅色虛線是整張 DFD 圖紙上最精華的靈魂！它警告了所有的守村將軍：『聽好！虛線外面的人，我們連他們嘴巴吐出的一口氣都不准信任 (Zero Trust)！一旦有一包從虛線外傳進來的蘿蔔 (Data Flow) 想要穿透這條紅線進到圖紙裡面！那在這條紅線上，【必須、絕對、毫無懸念地，爆發一場最嚴酷的搜身、解毒、過濾大審判 (Input Validation/Authentication)！】』。在這虛線交會處，就是威脅 (Threats) 爆發的最前線戰場！)
D. A Process (處理程序是白兔村裡面煮蘿蔔湯的大圓圈鍋子，這跟分隔天下的紅線大長城是完全不同的符號)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「信任邊界 (Trust Boundary)」** 是 DFD (資料流程圖) 在威脅建模中最核心的安全符號。
    *   **DFD 的四大元素：**
        1.  **Process (處理程序)：** 用圓形表示 (如網頁伺服器、內部函數)。
        2.  **External Entity (外部實體)：** 用方形表示 (如一般使用者、外部第三方 API)。
        3.  **Data Store (資料儲存)：** 用兩條平行線表示 (如資料庫、日誌檔)。
        4.  **Data Flow (資料流向)：** 用箭頭表示資料的傳遞方向。
    *   **Trust Boundary (信任邊界)：** 在微軟 SDL 或 STRIDE 的 DFD 中，信任邊界通常用【紅色虛線 box 或曲線】來表示。
    *   **安防意義：** 當一個 Data Flow (資料流) 穿過 Trust Boundary 時 (例如從 Internet 穿過 Firewall 進入內網，或是從一般 User Mode 穿過系統 Kernel Mode)，這就是「攻擊面 (Attack Surface)」暴露的地方。威脅建模師的眼睛必須死死盯著這些交界處，針對它們想出 Mitigations (緩解措施，如身分驗證、輸入過濾)。

#### **9. A system is designed to allow external researchers to query a medical database to find correlations between age and disease. However, the system is designed to automatically inject a small amount of random "noise" into the statistical results (e.g., slightly altering the average age returned). This ensures the researcher can get useful macro-trends but mathematically prevents them from identifying any specific individual patient's record. What advanced privacy-enhancing technology is being architected here?**
**(一座藏著天下百萬黎民病歷表的大『皇城太醫院地下大藥庫 (medical database)』。太醫院院長破天荒地，批准了讓城外那些雲遊四海的老術士 (external researchers)，可以站在地下室門外大喊發問：『院長啊！全天下六十歲以上得天花的老人家到底有多少？！』。然後太醫院會給出一張統計大榜單。但是！為了防止這些心腸惡毒的老術士，藉著每天用各種怪異刁鑽的問題夾殺逼問 (query)，來反向推導出：『原來今天只死了一個六十歲的太監，那就是隔壁村的老李！』的神準個資 (identifying specific individual record)。太醫院院長在門口設下了一道名為『大霧迷蹤』的機關陣法。當術士大喊發問後，這陣法會【自動把這張榜單上的數字，偷偷揉進幾把不痛不癢的神奇隱形沙子 (inject a small amount of random "noise")！這沙子會讓『六十歲』變成『五十九歲半』或『六十歲一個月』(slightly altering the average)！】。這讓老術士依然能摸清天下的『大趨勢概況 (macro-trends)』，但他這輩子，【就算拿計算機算斷手，也絕對推算不出這張榜單裡到底藏著哪一隻具體會喘氣的老百姓 (mathematically prevents identifying individuals)】！請問，這門能精準揉合瞎子大迷霧的高端隱形術，在陣法兵書上尊號為何？)**
A. Differential Privacy (這就是名震當代、被奉為大數據隱私保護至高無上神聖王冠的：【『差分隱私大迷霧陣 (Differential Privacy)』】！這套陣法是建立在嚴謹數學界定理上的終極絕學！它證明了：只要你在每次對金庫進行大盤點的數據清單裡，撒入經過精密計算的『拉普拉斯干擾亂數沙子 (Laplace Noise)』。你就算每天問一萬個刁鑽到極點的『有沒有一個六十歲、獨眼、沒頭髮、住長安東路、昨天來看病的太監？』。這陣法也會吐出一個「大概率可能是或是零」的模糊數字！這種把具體靈魂抹殺在大數據迷霧中的技術，是世界上唯一能讓科學家拿去做大數據分析，同時又絕對不會侵犯任何一個具體鄉民隱私的極致妥協大解方！)
B. Homomorphic Encryption (同態加密是在不用把箱子拆開的前提下，隔空打牛把裡面的數字相加，這保證了箱子沒被打開，而不是為了在數字沙漏裡揉沙子去騙術士)
C. Symmetric Key Exchange (對稱密鑰交換是在傳送這張被下沙子的榜單前，跟術士對接看誰拿哪把鑰匙，而不是用來保護榜單上面『六十歲』這個敏感數字隱私本身)
D. Digital Steganography (數位隱寫術是偷偷把一張玉皇大帝的藏寶圖藏在清明上河圖的某個樹皮像素點裡，這是在掩蓋「我正在傳遞寶藏圖」這個行為本身，這跟保護幾百萬老百姓病歷統計學扯不上半點關係)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 這是對 **「差分隱私 (Differential Privacy)」** 最精準的實務應用描述。
    *   **隱私保護的難題：** 當資料庫對外開放「聚合查詢 (Aggregate Queries) / 統計分析」時。攻擊者可以透過巧妙的連續查詢 (Differential Attacks) 來反推單一個體的數據。例如：
        *   Q1: 薪水部門總人數是多少？ Ans: 100人。總薪水多少？ Ans: 10,000,000。
        *   隔天新進員工王大明加入後。
        *   Q2: 薪水部門總人數是多少？ Ans: 101人。總薪水多少？ Ans: 10,050,000。
        *   攻擊者立刻得知王大明月薪 5 萬。即使沒直接查王大明的名字。
    *   **差分隱私的解法：** 在系統的 "查詢引擎層 (Query Engine)"。當它計算出 10,050,000 後，它不會直接回傳。它會注入一個隨機但分佈受控的 **Noise (雜訊)**。最後可能回傳 10,049,123 或 10,051,800。
    *   對於想分析「全公司平均薪水趨勢」的研究員，這個微小誤差完全可以接受 (Macro-trends valid)。但對於想抓狂計算出王大明真實薪水的駭客，這個隨機變動徹底摧毀了他的推導公式。這就是 Apple, Google 等科技巨頭廣泛使用的隱私技術。

#### **10. An architect is reviewing the design of a desktop application that requires administrative privileges to modify certain system files. Instead of requiring the user to run the entire application as an Administrator (which violates the Principle of Least Privilege), the architect redesigns the application so that the main UI runs as a standard user, and it spawns a small, separate, highly vetted background process that runs as Administrator ONLY when file modification is needed. What secure architectural pattern is this?**
**(一名安防風水大師在審閱一張名為『桌面大畫板 (desktop application)』的建築圖時。大師忍不住拍桌狂罵！原來，這個畫板雖然只是拿來畫畫的。但為了偶爾能把這幅畫給釘上那面名為『皇城神聖大黑板 (modify system files)』的地方。這破畫板居然在設計圖上規定：【『只要你想打開我這個畫板，那你就得把全天下最高級的『皇帝御賜傳國玉璽大令牌 (run the entire app as Administrator)』掛在脖子上！』】。大師怒斥：『你這是極限違反《讓賤民拿最爛鑰匙之最小權限大鐵律》！萬一有刺客在這個畫板上面畫了詛咒！這刺客拿著玉璽，整座皇城就瞬間改朝換代了！』。於是，大師親手把這畫板劈成兩半！他下令：【『從今以後！這畫具跟畫布 (main UI)，只准掛著『賤民狗牌 (runs as standard user)』在路邊擺攤！只有！只有當這幅畫真的完成、必須要去皇城神聖大黑板釘釘子的那一秒鐘！這畫板才能偷偷生出一個『全身被御林軍搜身過、確認沒帶匕首的蒙面無敵小死士 (highly vetted background process)』。由這小死士拿著半分鐘體驗券的玉璽，衝去黑板釘個釘子，然後立刻自殺！』】。請問，這種把危險任務跟平庸任務直接一刀兩斷的建築學大防護陣法，名喚為何？)**
A. Privilege Separation (or Compartmentalization) (這就是名震當代、被各國朝廷奉為防範刺客終極絕殺的：【『無敵權限切割大分家 / 絕對船艙防沉水密隔離大陣法 (Privilege Separation / Compartmentalization)』】！這陣法的絕對真理就是：【絕對不要讓一個每天拋頭露面在外接客的大廳 (Main UI/Web Server)，手裡握著能把金庫大門炸開的玉璽大令牌！】。你必須像這大船的船艙一樣。把每天接客的房間跟金庫，用最厚的地窖銅門給死死切開。當你需要拿黃金，你不能親自進去。你只能派一個極度單純、代碼只有十行被檢查到完全透明的【無腦守門狗僕人 (vetted background process)】幫你拿！這讓刺客就算黑進了大廳，他也拿不到玉璽，更指使不動那個無腦守門狗！這是應用程式安全架構的極致典範！)
B. Single Sign-On (SSO) (SSO 是讓賤民只出示一次狗牌就能進兩個大樓的大門陣法。它只管進門，不管大樓內部這這畫板跟玉璽的切割)
C. The MVC (Model-View-Controller) Pattern (MVC 陣法是為了解耦畫面跟邏輯，讓畫畫的跟寫算式的不要吵架打結，這完全是為了「開發維護經濟好寫扣 (Software Engineering)」，跟把玉璽搶下來的權限大切割安防毫不相干)
D. Zero Trust Architecture (零信任大陣法是指整個大網絡體系，不管你在內網外網，每一棟樓都要拿門票去換。雖然這是神仙級別的宏觀防衛理念，但在這題對《單一桌面應用軟體內部》進行切肉割骨的手術級戰術名稱，最精確的叫法是 privilege separation)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **「權限分離 (Privilege Separation)」** 或 **「隔離區隔化 (Compartmentalization)」** 是實現 **「最小權限原則 (Principle of Least Privilege, PoLP)」** 最具體的軟體架構模式 (Architectural Pattern)。
    *   **問題的背景：** 傳統 Windows 程式最大的噩夢就是 "以系統管理員身分執行 (Run as Administrator)"。如果一個龐大且充滿 UI 繪圖套件漏洞的應用程式 (100萬行程式碼) 拿著 Admin 權限跑，一旦被攻擊 (例如在輸入框放個 Buffer Overflow)，駭客就直接取得 System 權限接管整台主機。
    *   **Privilege Separation 的解法：** 將應用程式「硬生生切成兩半」。
        1. **Main Process (UI):** 佔 99% 的程式碼。以 Standard User (標準使用者/低權限) 執行。
        2. **Helper/Daemon Process:** 佔 1% 的程式碼。這隻程式的工作極度簡單 (例如只負責把一個 Config 檔寫到 `C:\Windows\System32`)。它以特權 (Elevated Privilege/Admin) 執行。
    *   兩者之間透過防護嚴密的 IPC (行程間通訊) 溝通。因為 Helper Process 程式碼極少，可以經過極度嚴格的安全審查 (Highly Vetted)，不容易有漏洞。這種設計把高風險的「攻擊面 (Main UI)」與高價值的「防守面 (Admin 權限)」徹底剝離。

#### **11. A team is using the STRIDE threat model to analyze a proposed login system. They identify a threat: "An attacker could intercept the network traffic and capture the user's password in plaintext." To counter this, they add a requirement: "All login traffic must occur over HTTPS." Which specific aspect of STRIDE does "intercepting traffic to capture passwords" map to?**
**(一支準備佈下 STRIDE 威脅六道輪迴大陣來審判『登入大門把關系統』的特種大隊。斥候滿頭大汗地報告發現了一隻致命魔鬼的蹤跡：『大將軍！如果老百姓用大喇叭喊出他們登入的通關密語。半路上的劫匪只要躲在樹叢裡偷聽，就會把那句沒加蓋的【『阿彌陀佛密語』】原封不動地聽得一清二楚 (intercept network traffic and capture plaintext password)！』。為此，大隊長狠狠地下了一道反殺令：『去！給老子挖一條「全包覆防彈竊聽隧道大水管 (HTTPS)」，以後全都從水管傳話！』。請問！這隻躲在樹叢裡把別人沒穿衣服的密碼看光光、專門幹偷窺勾當的魔鬼，在 STRIDE 這六本兵法小冊子裡，屬於哪一本名冊的追殺名單？)**
A. Spoofing (假冒是劫匪自己帶上面具，跑去對著皇城守衛大喊「我是皇帝，給我開門」。跟這題躲在樹叢純聽別人報密碼的被動偷窺不一樣！)
B. Elevation of Privilege (權限提升是小兵在牢房裡偷拿到大將軍的鑰匙把門打開跑出來，這是攻破後端內部管理的漏洞。)
C. Information Disclosure (這就是 STRIDE 六大魔鬼中，那個專門在半夜掀人底褲、挖人墳墓的超級變態偷窺狂：【『無情扒光機密內褲毀滅者：資訊洩漏大魔王 (Information Disclosure)！』】。這隻魔鬼的專長，就是利用各種手段（例如你在客棧沒加密免費 Wi-Fi 前大喊密碼）。把原本只准天知地知你知我知的純潔機密檔案 (密碼、身分證字號)，赤裸裸地攤開在他的偷窺望遠鏡下！要殺死這隻魔鬼的唯一神仙法器，就是套上名為「機密性女神之衣」的【加密大陣法 (Encryption/TLS)】！)
D. Repudiation (否認是大將軍偷吃完燒餅後，把嘴巴抹乾淨打死不承認這餅是他吃的。這跟半路攔截抓別人對話封包的竊聽魔完全沒關聯！)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「資訊洩漏 (Information Disclosure)」** 是 STRIDE 模型中專門威脅 **「機密性 (Confidentiality)」** 的攻擊類別。
    *   **威脅場景：** 駭客透過網路監聽 (Network Sniffing / Packet Capture) 攔截明文 (Plaintext) 傳輸的 HTTP 封包，從而取得使用者的帳號和密碼。
    *   **核心目標：** 駭客的當下動作是「未經授權地看到了他不該看的資料」，這就是標準的 Information Disclosure。
    *   *(雖然這可能導致後續的 Spoofing 假冒攻擊，但「攔截封包偷看密碼」這個動作本身的歸類是資訊洩漏)*。對應的緩解措施 (Mitigation) 就是加強傳輸層加密 (Data in Transit Encryption)，例如強制使用 TLS/HTTPS。

#### **12. A security architect mandates the use of parameterized queries (Prepared Statements) for all database interactions in a new application's design. This architectural decision is specifically employed to act as a compensating control against which widespread class of vulnerabilities?**
**(一名安防風水大師在『大金庫守門人對話寶典手冊 (database interactions)』的首頁，用血紅色的硃砂筆，畫上了一道全天下最致命、違者生不如死的絕對軍令：【『聽好！從今以後，任何想跟這地下大金庫對話的老百姓或工匠。絕對！不准！像個沒唸書的蠢蛋一樣，用加號把老百姓嘴裡吐出來的話隨便黏在通關密語後面 (string concatenation)！所有要傳達給守門長老的指令，必須拿去那座被神靈附體的【『終極預編譯無敵真空大鐵籠 (parameterized queries / Prepared Statements)』】裡！把老百姓吐出來的那些危險詞彙，狠狠地關進這籠子裡的獨立鐵格子裡！然後整籠端給長老看！長老才知道哪些字是真正的神諭，哪些字是刁民的胡說八道！』】。請問，這套被資安界傳唱千古、堪稱萬靈丹的『預編譯鐵籠大陣』，其被發明出來的唯一宿命悲願，是為了徹底斬草除根去殺死哪一種肆虐人間數百年的恐怖大瘟疫 (class of vulnerabilities)？)**
A. Cross-Site Scripting (XSS) (跨站腳本攻擊是把毒藥抹在畫面按鈕上，讓下一個看這畫面的人瞎掉，不是對著地下室金庫長老下毒。治 XSS 的解藥叫「編碼 Encoding，跳脫 Escaping」)
B. Injection Attacks (e.g., SQL Injection) (這就是那道萬劫不復大陣所要鎮壓的：【『千古第一滅國大瘟疫：偷樑換柱之神鬼注入大屠殺 (Injection Attacks / SQL Injection)』】。這場瘟疫的原理，是刁民在對話框裡輸入了極度邪惡的「單引號大魔法指令 (')」。如果守門人像個白痴一樣，把這句魔法跟原本的查帳命令融合成一句，金庫就會被騙，直接打開門把所有城池的黃金噴給刁民！而要破解這瘟疫，【預先寫好框框的大鐵籠 Parameterized Queries 就是唯一能根治的千古神藥！】。它能精準地把這刁民的魔法引號，物理性地變成一坨『沒有神力、純粹只是一張白紙上的墨水塗鴉』。大金庫長老一眼就能看穿這不是指令，而是無關緊要的值 (Value)！這就是斬斷 SQLi 的究極利刃！)
C. Insecure Direct Object References (IDOR) (身分越權漏洞是：你明明只有客棧 11 號房的鑰匙，你卻偷看了 12 號房王老爺的帳本。這個跟有沒有用單引號魔法欺騙守門長老無關，這是權限沒控管好的問題)
D. Buffer Overflows (緩衝區溢位是刁民塞了一卡車大便把金庫大門塞爆，讓大門直接卡死不能動彈，這是寫 C 語言的古老死穴。現在這題討論的是用單引號跟文字去詐騙)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「參數化查詢 (Parameterized Queries) / 預編譯語句 (Prepared Statements)」** 是防禦 **注入攻擊 (Injection Attacks，特別是 SQL Injection)** 最有效、最標準的架構與程式設計層級防具。
    *   **SQL Injection 的本質：** 駭客在輸入欄位 (如 Username) 輸入 `admin' OR 1=1 --`。如果開發者用「字串相加 (String Concatenation)」組合 SQL 語句，資料庫引擎會把駭客輸入的惡意字元 (單引號與 OR) 當成「可執行的 SQL 命令結構」來解析，導致權限被繞過。
    *   **Parameterized Queries 的神威：**
        1.   資料庫驅動程式「先」把 SQL 指令的結構 (骨架) 傳給資料庫編譯 (Prepare)。
        2.   「再」把使用者輸入的值 (Value) 填入指定的參數洞孔 (Placeholder `?`) 裡。
        3.   重點來了：在這個階段，資料庫引擎會把填進來的所有內容，**強制且無一例外地當作純粹的「文字字串」或「常數 (Literal)」**。就算駭客在裡面寫了一百萬個 `DROP TABLE Users;`。資料庫也只會冷冷地回答：「喔，你想尋找一個名字叫做 `DROP TABLE Users;` 的鄉民是吧？抱歉查無此人。」這從物理上斬斷了命令與資料混淆的可能。
