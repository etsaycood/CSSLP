# 第一套全真模擬試題 (Exam 1) - 答案與詳解本
## 領域 8：安全的軟體供應鏈 (Secure Software Supply Chain) (12題)

---

#### **1. A massive global cyberattack occurred when hackers successfully infiltrated the build server of a popular IT management software company (Company X). The hackers injected a malicious backdoor directly into Company X's official software update package. Thousands of Enterprise customers blindly downloaded and installed this "official update" because it was correctly digitally signed by Company X. What specific type of attack does this incredibly damaging scenario represent?**
**(一場震驚全球的網路毀滅戰爆發！原因在於駭客軍團成功打穿了某家極知名的 IT 網管軟體龍頭原廠 (X 公司) 內部神聖的『編譯伺服器 (Build Server)』。駭客沒有去偷 X 公司的薪水，而是直接把一個邪惡的後門木馬，悄悄『注射』進了 X 公司即將要發布的下一個【官方正版軟體更新升級包】裡面。接著，全世界幾千家大台骨幹電信跟五角大廈客戶，就這樣閉著眼睛下載並安裝了這包「官方升級檔」，因為它的確完美帶有 X 公司的官方保證數位憑證簽章！這個具備幾千億美金毀滅力道的情境，是哪種特定攻擊手法的經典展現？)**
A. Cross-Site Scripting (XSS) (跨站腳本攻擊)
B. Software Supply Chain Attack (軟體供應鏈攻擊)
C. Distributed Denial of Service (DDoS) (分散式阻斷服務)
D. Social Engineering / Phishing (社交工程 / 騙密碼釣魚)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是 2020 年震驚世界的 **SolarWinds (太陽風) 攻擊事件** 的完美重現，也是現代資安界最恐懼的終極夢魘：**軟體供應鏈攻擊 (Supply Chain Attack)**。以往駭客是直接拿石頭去砸五角大廈的鐵門 (很難打進去)。現在駭客變聰明了，他們知道五角大廈會向外面的 A 公司買軟體。於是駭客潛入防護較弱的 A 公司，跑到 A 公司的「軟體製造工廠 (CI/CD Build Pipeline)」，在源頭的水井裡下毒。當 A 公司不知情地把裝滿毒水的正版軟體送到五角大廈時，五角大廈的超級防火牆不僅不會擋，還會熱烈歡迎這包「帶有原廠正版簽章」的更新檔。這種借刀殺人的溯源攻擊就是供應鏈安全的探討核心。
    *   **其餘干擾項：** XSS, DDoS 都是單點網站的戰術層級技術攻擊，不具備這種戰略層級「感染全球物流網路」的擴展性。社交工程則是騙人，供應鏈則是騙取系統對官方數位簽章的無條件信任。

#### **2. You are managing the procurement of a new proprietary billing system from a third-party vendor. The CISO mandates that your organization must be protected in the event the vendor suddenly goes bankrupt, is acquired by a competitor, or simply refuses to provide support for the software in the future. To guarantee your organization will always have access to the underlying source code to maintain the system if the vendor vanishes, what specific legal mechanism MUST be established during the contract negotiations?**
**(你正在替公司對外採購一隻超貴的私有產權金流結帳系統軟體。你們的安全長 (CISO) 下了死命令：「萬一這家賣軟體的廠商明天突然破產倒閉了、或是被我們死對頭公司惡意併購了、或是他老闆捲款潛逃再也不提供我們維修更版服務了，我們公司絕對不能跟著陪葬！」為了在法律層面上保證，一旦原廠人間蒸發，貴公司依然能夠合法且實體地【取得這隻軟體最底層的原始碼 (Source Code)】好讓你們自己接手維護它。在當初簽約買軟體時，雙方【必須】設立什麼機制？)**
A. A strict Non-Disclosure Agreement (NDA). (極度嚴苛的保密防諜條款)
B. A comprehensive Service Level Agreement (SLA) mandating 99.99% uptime. (要求 99.99% 不當機的服務水準保證 SLA)
C. A Software Source Code Escrow Agreement. (軟體原始碼託管協議 / Escrow 第三方存證保管)
D. A robust Disaster Recovery Plan (DRP). (強韌的災難復原兵推計畫)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是購買商業現成軟體 (COTS) 供應鏈中最經典的法律防線：**原始碼託管 (Source Code Escrow)**。當你買軟體時，原廠絕對不會把他的商業機密 (原始碼) 交給你，他只會給你打包鎖死的二進位執行檔。但如果原廠倒閉了，這套軟體就變成了沒人能修補漏洞的孤兒。為了解決這死局，雙方會找一個有公信力的第三方律師或金庫機構 (Escrow Agent)。原廠定期把最新的原始碼鎖進這個金庫。萬一有一天發生了合約上寫的「觸發事件 (Release Conditions)」(例如原廠宣告破產或連續三十天聯絡不到人)，金庫就會把原始碼合法解鎖交給客戶，讓客戶的生意能活下去。
    *   **為何 A, B, D 皆為干擾項：** NDA 只是叫你們不要亂講話洩密。SLA 是原廠還活著的時候答應你他網頁不會當機的罰錢條款（他都破產跑路了，你哪裡罰得到錢）。DRP 則是你們自家機房停電時的應變計畫，與原廠的智慧財產歸屬權轉移毫不相干。

#### **3. A development team is heavily reliant on open-source Node.js libraries downloaded directly from the public `npm` repository. A hacker creates a malicious package named `reackt` (notice the extra 'k'). The hacker is hoping that tired developers who intend to install the wildly popular legitimate library `react` will accidentally misspell the command parameter (e.g., `npm install reackt`) and pull down the virus instead. What is the industry term for this specific supply chain attack technique?**
**(一個開發大隊重度依賴每天從公網開源集散地 `npm` 下載 Node.js 的積木套件來拼湊網站。有個惡毒駭客，他在 npm 上註冊了一個帶著病毒的全新外掛包，並且把它心機極重地命名為『`reackt`』 (請注意他故意多塞了一個極其隱密的 小寫字母 'k')！駭客坐在家裡守株待兔，祈禱那些爆肝熬夜、眼睛已經睜不開的工程師，在終端機本來想打下載全世界最紅的套件 `react` 時，肥手指不小心多敲了一個字打成了 `npm install reackt`，然後就把他的木馬給迎接入核。這種下三濫但極度有效的供應鏈下毒術語叫甚麼？)**
A. Typosquatting (錯字域劫持 / 誤拼搶註攻擊)
B. Buffer Overflow (陣列滿載溢位衝鋒)
C. Command Injection (系統終端惡意命令注入)
D. Man-in-the-Middle (MITM) File Hijacking (路中惡人半途狹持檔案調包)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 這是現代開源軟體供應鏈中最令人防不勝防的低科技高產出戰術：**Typosquatting (誤植搶註 / 錯字下毒)**。駭客利用人類的疲勞與打字慣性。如果正版軟體叫 `request`，駭客就會去註冊 `requst`、`rqeuest` 甚至是 `request-api`。只要有工程師打錯字又沒看清楚畫面，一按下 Enter，病毒就以開發者這個超級管理員的權限，堂而皇之地住進了開發主機裡，並隨著 CI 編譯被帶入整個公司的產品線。解決方案通常是建立公司內部的私有套件倉庫 (Private Nexus/Artifactory)，審查過後才能存取。
    *   **為何 B, C 是干擾項：** 溢位與命令注入是拿又長又怪的惡意字串去把應用程式的記憶體弄崩潰，或是騙終端機幫你下指令。這裡完全沒騙電腦，駭客是直接在騙人類工程師的大腦。
    *   **為何 D 是干擾項：** MITM 是你在下載正確名字的 `react` 時，駭客在半路的基地台把封包切開塞病毒進去。Typosquatting 則是駭客根本沒截封包，他只是開了一間假店等你走錯門。

#### **4. You are hired as a DevSecOps engineer to fortify a company's software delivery pipeline. Currently, developers compile their Java code on their personal laptops and manually upload the `.jar` files to the production server. To radically secure the software supply chain and ensure that code cannot be tampered with between the developer's keyboard and the final production environment, what architectural change MUST be implemented?**
**(你被高薪聘為 DevSecOps 神兵去整頓一間公司的散漫軟體發布產線。目前的陋習是：全公司的工程師各自在自己的咖啡廳筆電上，把寫好的 Java 編譯成 `.jar` 執行檔。然後他們用 FTP 手工把這些檔案傳上高機密營運伺服器。為了對這條千瘡百孔的軟體供應鏈實施神經外科式的大手術，『確保程式碼從離開工程師鍵盤，到最終抵達戰場伺服器這段漫長路途中，絕對不遭受任何活人干預與竄改感染』。你【必定會】強勢推行什麼樣的架構大變革？)**
A. Developers must start encrypting their laptops with BitLocker. (強逼大家把筆電用微軟 BitLocker 上鎖)
B. Implement a strictly controlled, automated Continuous Integration / Continuous Deployment (CI/CD) pipeline (e.g., using Jenkins or GitLab CI) acting as a secure, immutable "Build Factory" where no human can touch the compiled binary. (建立一條手段極端嚴酷、全自動化的 CI/CD 連續整合與發布流水線 (如 GitLab CI)。這條管線將化身為一座防彈的「不可摧毀的無塵建立工廠 (Build Factory)」，一旦進入這條輸送帶，【絕對禁止任何一個活人(包含寫扣工程師本人)】有權力去觸碰或更動那剛做好的二進位產出結果)
C. Require all developers to connect via VPN before uploading files to the production server. (只要求他們改連 VPN)
D. Switch from programming in Java to programming in C++. (把 Java 燒了改用 C++)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 手工在本地端編譯並上傳 (Local Builds) 是軟體工程與供應鏈安全的地獄。你永遠不知道工程師 A 的筆電是不是已經中了來自中國或俄羅斯的木馬，更不知道他上傳的那個 `.jar` 裡面，是不是夾帶了連他自己都不知道的殭屍網路病毒。要切斷這個感染鏈，企業必須實作 **CI/CD 流水線 (Continuous Integration/Continuous Deployment)**，並貫徹 **「不可變的構建 (Immutable Builds / Centralized Build Server)」** 原則。工程師只能把純文字的原始碼推上版本控制系統 (Git)。接下來，由公司那台被層層防火牆鎖死、絕對乾淨無毒的 CI 機器，全自動把文字抓下來、掃毒 (SAST)、測驗、然後打包編譯。嚴禁任何人類手動干預打包過程，這保障了軟體出廠的原生純潔。
    *   **為何 A, C, D 皆為干擾項：** BitLocker 只是防筆電在公車上被偷走硬碟裡的資料。VPN 只是保護傳輸路徑不被側錄密碼。改寫 C++ 更是荒謬，C++ 反而更容易寫出記憶體漏洞。這些都無法改變「由充滿變數且可能中毒的個人筆電，來執行神聖軟體生產打包任務」這個核心架構性災難。

#### **5. In the aftermath of the devastating SolarWinds and Log4j supply chain breaches, the US Government issued an Executive Order mandating that all software vendors selling to the federal government must provide a comprehensive, machine-readable "ingredients list" detailing every single open-source and proprietary software component, library, and version used to build their final product. What is the formal, industry-standard acronym for this critical transparency document?**
**(在毀滅性的太陽風暴 (SolarWinds) 還有 Log4j 兩次供應鏈大屠殺血案落幕後，痛定思痛的美國政府白宮直接下達了一道極度嚴厲的總統行政命令：即日起，所有想把軟體賣進聯邦政府吃公家飯的供應商，【必須】隨機附上一張『能被機器自動判讀的全方位食品成分表清單』。這清單必須死板地詳列：這個產品裡面到底摻了哪些幾千個開源的別人的函式庫、你自己寫的模組、跟它們準確到小數點的版本號碼。這份被視為軟體界大透明時代來臨的關鍵報表，其正式業界縮寫為？)**
A. Data Flow Diagram (DFD) (資料流動圖)
B. Service Level Agreement (SLA) (服務等級賠償契約)
C. Software Bill of Materials (SBOM) (軟體物料清單 SBOM)
D. Acceptable Use Policy (AUP) (乖乖上網不可看色情守則 AUP)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **SBOM (Software Bill of Materials，軟體物料清單)** 是近年 CSSLP 考試中「供應鏈領域」絕對必考的最核心時事重點。你可以把它看成是買洋芋片包裝背後的「成分表」。以前公司買一套防毒軟體，根本不知道這防毒軟體裡面是不是包了一個兩年前有漏洞的 `Log4j` 壓縮檔。當漏洞爆發時，全球上百萬家企業完全瞎了，不知道自己家到底有沒有買到這等毒藥。現在有了 SBOM (通常由 SPDX 或 CycloneDX 標準格式撰寫)，資安主管只要按個鍵，系統就會自動去比對這個「成分表清單」跟最新的 CVE 漏洞庫，十秒鐘就能精準抓出「我們向 A 廠商買的這套軟體裡面，含有會致命的一行過期開源代碼，趕快斷網隔離」。
    *   **為何 A 是干擾項：** DFD （資料流圖）是在做威脅建模 (Threat Modeling) 畫流程圓圈圈圖用的。
    *   **為何 B 與 D 是干擾項：** SLA 是合約。AUP 是規定員工在辦公室不得上網看 YouTube 的政策。與軟體拆解成分無關。

#### **6. A team is downloading a critical Linux kernel update. The file is massive (4 GB) and took hours to download from a public mirror site somewhat far away. To mathematically verify that the downloaded file is *exactly* the same as the original file published by the Linux creators—and that it was not corrupted during the network transmission or secretly replaced with malware by the intermediary mirror site—what simple cryptographic check MUST the team perform against the downloaded file before executing it?**
**(技術連隊正在從一個不知道架在全球哪個鬼角落的開放站點上，花了幾個小時下載一尊高達 4 GB 龐大的核心升級檔。為了要『在數學與物理上鐵證如山地保證』：我們載下來這陀 4GB 的位元汪洋，跟原廠教父當初按出來發佈的那個原初檔案【長得一模一樣連一個標點符號 0 或 1 都沒掉】，而且也絕對沒有在漫長的網路海底電纜傳送裡壞掉，或是被那家中繼分發假好心站點偷偷掉包塞了木馬進去。在動手點擊把它安裝之前，大隊【務必及必須】對這個檔案施展哪項簡潔暴力的密碼學檢驗手段？)**
A. Encrypt the file using RSA-2048. (拿最難的 RSA 把它通通鎖起來)
B. Run an automated SAST scan on the compiled binary. (用 SAST 掃描那尊二進補丁)
C. Generate a cryptographic Hash (e.g., SHA-256) of the downloaded file and explicitly compare it against the official published Hash value found on the creator's secure website. (從我們自己這端，對這包 4GB 大嬰兒動用『密碼學雜湊函數 (Hash，例如 SHA-256 指紋演算法)』榨出一串文字指紋；並把這道指紋拿去跟官方帶鎖 https 網站上公告的「官方黃金指紋」字串硬核比對！完全符合才能放行)
D. Compress the file using a ZIP utility and check the compression ratio. (把它壓縮後算比例看看有沒有發福)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 在檔案傳輸與供應鏈中，確保 **資料完整性 (Integrity)** 是一種信仰。而這信仰的最高神聖工具就是 **雜湊碼 / 指紋 (Hash / Checksum)**，常使用如 SHA-256 這等演算法。雜湊有一條神奇的不可逆物理定律：雪崩效應 (Avalanche Effect)。就算一個 4GB 的電影檔，只要裡面有哪怕只是 1 個 bit 被駭客用木馬取代了，它算出來的 SHA-256 64 個字母指紋，會跟原本官方公布的模樣呈現天崩地裂、完全不認識的巨大改變。所以下載大型 ISO 檔或升級包的第一鐵律，就是自己算一遍，然後拿著指紋字串（就像身分證）去官方佈告欄比對。
    *   **為何 A 是干擾項：** 你把它鎖起來加密 (Confidentiality 機密性作為)，對「保證它本來是不是無毒正版 (Integrity)」沒有任何幫助，只是多此一舉把它鎖死不能用而已。
    *   **為何 B 與 D 皆為干擾項：** SAST 根本讀不懂 Binary 執行檔。檔案壓縮比例這完全是搞笑跟防毒毫無關聯。

#### **7. A developer is building a Docker container image for a new web service. The `Dockerfile` starts with the instruction: `FROM ubuntu:latest`. A senior security architect immediately flags this line as a severe supply chain and operational risk. Why is using the `:latest` tag considered an extremely poor practice in containerized environments?**
**(菜鳥工程師在寫新的 Docker 容器配方表。他在大標題第一段豪氣寫下：『我的基礎房型來自於 `ubuntu:latest (最新版打我啊)`』。老練的架構師看到這個 `latest` 後直接翻桌，並嚴正標記這是一場巨大的系統與供應鏈營運災難漏洞。為什麼在嚴謹的微服務裝箱世界裡，信手拈來使用 `:latest (抓最新版就對了)` 這種無腦語法，是極度糟糕、被千夫所指的下三濫實作方式？)**
A. The `latest` tag requires the image to be downloaded from the internet every single time the container starts, consuming too much bandwidth. (這會強迫系統每次起飛都要去重抓拖垮內網)
B. The `latest` tag is completely non-deterministic. It silently points to a different, potentially incompatible, or newly vulnerable underlying operating system version every time the vendor publishes an update. Developers MUST pin dependencies to a specific, immutable version hash (e.g., `ubuntu:20.04` or `sha256:abc123...`) to guarantee the build is reproducible and predictable. (因為這個字眼是極度『測不準、無確定性 (Non-deterministic)』！它會在沒有通知你的某個黑夜裡，當原廠又做了一版新的時候，默默漂移更換！導致你昨天還活得好好的系統，今天因為底層作業系統架構徹底斷層、或是原廠新版剛好有嚴重零日漏洞而直接全域死當。開發大軍【絕對必須】學會將依賴牢牢綁死「釘死」在特定的、永痕不變的版本雜湊或精確版號上 (例如 `sha256:..` 或是 `v2.4.1`)，來保證每一次做出來的東西都是「一模一樣的還原 (Reproducibility)」)
C. Images tagged with `latest` are automatically run with `root` privileges by the Docker daemon. (帶有這標籤的軟體會自帶高權限屬性霸王執行)
D. The `latest` tag automatically triggers a DAST scan which slows down the deployment pipeline. (這標籤會觸發過於無敵緩慢的安全掃描)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 在容器技術 (Docker) 與依賴管理解套上，最危險的關鍵字叫做**不確定性 (Non-determinism)**。當你寫下 `:latest`，你這就像是買樂透。你今天按下編譯，拿到的是 18.04，你的程式跟它相處融洽。但明天你同事接手你的程式再次編譯，這時 Ubuntu 剛好發布了 22.04，這個 `:latest` 就會自動漂移去抓新版。如果新版不支援你舊版的函數，你的服務在上線那一刻就會原地全軍覆沒。更可怕的是供應鏈威脅：如果原廠最新版昨晚剛被駭客植入後門，你的系統也會在第一時間「熱情擁抱」那個有毒的最新版。所以業界死命令是：**依賴釘選 (Dependency Pinning)**。我們寧可寫死成難看的雜湊碼 `sha256:6b82...`，也要保證我在日本編譯、在美國佈署，拉下來的基礎這塊磚塊是永恆、鐵壁不可改變的同一塊。
    *   **其餘為干擾項：** A 不對，Docker 有緩存 (cache)，有 latest 也不會每次硬抓。C 更是胡扯，權限取決於你在裡面怎麼定義 User，跟外表名稱無關。D 更無稽之談，Docker 本身不包含任何掃描機制。

#### **8. Your company outsources the development of its mobile application to a contractor in another country. The contract is ending, and the contractor hands over the final source code. Before compiling the code and releasing it to the Apple App Store, your security team performs a thorough audit. They discover several hardcoded API keys and a hidden function that quietly transmits all users' geolocation data directly back to a server owned by the contractor, clear outside of your company's control. What specific threat vector in the software supply chain does this represent?**
**(你們公司將手機 App 開發外包給國外傭兵公司。合約截止了，對方交出了最後的程式碼大作。在把這個 App 裝機送進蘋果商店供凡人下載前，這家公司的資安小組拿了掃描器去做了個徹底底朝天。小組居然驚恐地發現了一整疊『被直接硬寫死在原始碼裡的金庫通行金鑰』，以及一隻極度無恥、能夠偷偷把所有使用者當下的精準 GPS 經緯度座標，悄悄側漏傳送直達『那家外包公司遠在國外自己家架設的秘密伺服器』裡面的隱形功能！請問這在軟體安防供應戰裡，是代表著怎麼樣惡毒的威脅面向向量？)**
A. An unintentional Buffer Overflow vulnerability. (菜鳥不小心搞砸的記憶體溢位瑕疵)
B. An intentional Logic Bomb or Malicious Backdoor planted by an untrusted third-party supplier. (這是來自缺乏信任基礎『第三方外部防線製造商』所極為『刻意』蓄意深埋的邏輯炸彈地雷或是惡毒盜取竊聽後門 (Malicious Backdoor))
C. Resource Exhaustion leading to Denial of Service. (這是吸血鬼耗盡機器死當的癱瘓招式)
D. Insecure Direct Object Reference (IDOR). (沒有好好保護物件被翻閱)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 當購買或外包開發軟體時 (Third-Party Supplier Risk)，最大的威脅不再是單純的「寫爛的漏洞」，而是 **內鬼或未受信任廠商蓄意植入的後門 (Intentional Malicious Backdoors) 或邏輯炸彈 (Logic Bombs)**。這支 App 不是因為寫爛了而被外面的駭客攻破，而是造橋的建築師本人親自在橋墩裡藏了炸藥。外包廠商未經授權硬生生拉一條線去吸走自己客戶的機密資料（位置信息），這已構成犯罪規格的供應鏈詐欺後門。
    *   **為何 A, C, D 是干擾項：** Buffer overflow 與 IDOR 都是程式碼「沒寫好」產生的意外瑕疵漏洞，它們並不帶有這種被隱密埋藏、專程用來盜撥客戶財產外洩的「濃烈主動惡意建構意圖 (Intentional Malice)」。

#### **9. An organization is evaluating a new open-source database to replace its expensive proprietary system. The enterprise architecture team notes that the open-source project is heavily maintained by only a single, unpaid developer who hasn't committed any new code or responded to bug reports in over 3 years. From a secure supply chain perspective, what is the primary risk of adopting this specific open-source component?**
**(企業架構師正在秤重一款開源免費資料庫，因為公司想踢掉那尊極端昂貴的微軟大系統。但架構師在翻這款免費軟體的 GitHub 族譜時背脊一涼：這整個龐大系統雖然很神，但在過去幾年間，居然完全只靠『唯一一位』根本不支薪的神仙老爺爺在獨力支撐。而且重點是，這位老爺爺已經超過三年沒有在網路上講過一句話，這三年來無數個論壇跟臭蟲警報單堆積如山他都沒修復或回應。單純從『軟體供應鏈安全防衛』戰略角度，強行牽這頭免費開源軟體牛進公司，我們面臨撲面而來的超級死亡風險是什麼？)**
A. Open-source software is inherently illegal to use for commercial purposes. (企業拿免錢開源去賺錢本身就觸犯版權法絕對違法)
B. The project suffers from severe "Abandonware / Lack of Maintenance" risk. If a zero-day vulnerability is discovered tomorrow, there is no active community or vendor to patch it, leaving the enterprise permanently exposed. (這產品已經成為了駭人的『被遺棄孤兒軟體 (Abandonware) / 維護動能枯竭斷層』。這意味著：哪怕明天早上這套系統被爆出一個被偷光家的宇宙級死亡零日洞，公司也絕對找不到這個神仙，更沒有任何活著的活人社群可以幫忙研發打上那張補救的創可貼。企業將如裸身暴露在廢土之中永遠等死)
C. The software lacks a graphical user interface (GUI). (沒華麗圖形介面打字太痛苦)
D. The developer might suddenly demand millions of dollars in licensing fees. (這個三年死掉的神仙搞不好明天爬起來要大家吐保護費)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 開源軟體 (Open Source Software, OSS) 的強大在於「千萬雙眼睛能讓臭蟲無所遁形 (Linus 定律)」。但是！這一切建立在有一個活躍的維護者社群 (Active Community)。在開源供應鏈安全風險評估中，一個只有一個作者且已經幾年沒更新的專案，被稱為 **廢棄軟體 (Abandonware)**。這是絕對的致命紅十字。因為沒有人會幫你修補未來的漏洞，如果駭客發動新時代的心臟出血攻擊，像微軟這種大公司半天就能發給你修正檔修復，但這套荒島系統，你們公司只能等死（或者要逼迫自家不熟這系統的員工下去修改這底層開源碼），這在企業營運上是無法接受的毀滅級風險。這也是許多公司要求廠商提供 SBOM 的原因（去抓出誰在用這些死了三年的爛木頭蓋房子）。
    *   **為何 A, C, D 皆為干擾項：** A 錯了，99% 的開源軟體只要合乎授權聲明 (MIT, Apache) 都可以正當用於商業行為。C 沒漂亮介面只是一場設計悲劇而不是安防漏洞。D 是授權法務議題（他當初宣告開源就不能反悔亂要錢），這裡的威脅在於「孤兒沒人修補漏洞」。

#### **10. You are designing a secure Continuous Delivery (CD) pipeline. After the source code is successfully checked by SAST, compiled into a container image, and tested, the pipeline pushes the final image to the company's private Container Registry. To ensure that the Kubernetes production cluster *only* runs images that have legitimately passed through this specific, secure build pipeline (and to prevent an administrator from manually deploying a rogue, untested image), what security control must the CI/CD pipeline apply to the image before pushing it?**
**(你正在精心雕琢一道滴水不漏的『連續遞交部屬火車管線 (CD)』。當脆弱的純文字程式碼在經過層層 SAST 光機透掃、被完美打包裝箱成一塊微服務容器，並且被測試軍團虐待通過後，管線最後一哩路會將這尊『聖物』推進到公司最核心的私有聖殿存放區 (Registry)。為了強勢並物理保證：前方營運大機房 (K8S叢集) 絕對不吃任何來路不明的東西，『【只准執行】這些曾經在洗禮下真真切切通過這道火車管線的這塊聖物映像檔』！並且還要死硬防堵那些有高權限的管理員哪天偷吃步，自己從旁邊隨便手工編譯一包破爛木馬強塞給 Kubernetes 吃下。這個打狗棒出廠前的 CI/CD 管線在推出去前，必須打上什麼魔法禁制防護印記控制鎖？)**
A. The pipeline must Cryptographically Sign the container image using tools like Docker Content Trust or Cosign. The Kubernetes cluster is then configured with an admission controller to strictly reject any image lacking this specific digital signature. (管線在出廠時必須用最高機密工具 (如 Cosign 或是 Docker Content Trust) 對這個軟體大箱子結結實實烙下【密碼學數位簽章】。前線的 K8S 哨兵 (准入控制器) 將被教導並配備：只要膽敢端進來的這箱東西上面，缺少或印模不對這家公司的唯一數位真血指紋，管你是超級總理還是路邊駭客，系統將全面暴力無情剔除退回決不能開機)
B. The pipeline must encrypt the entire container image so it cannot be read by unauthorized users. (管道必須把這個檔案全部加密得黑壓壓誰也看不到)
C. The pipeline must automatically delete the source code from the repository to prevent modifications. (管線必須發出命令把原始版本控制系統 Github 裡的心血文字全部斬草除根殺光)
D. The pipeline must generate a massive text file detailing every line of code inside the container. (管線要印出一張長如萬里長城的每行點點細項)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 這是現代 DevSecOps 中 **零信任供應鏈 (Zero Trust Supply Chain)** 的頂級藝術。你怎麼證明這個放在倉庫的東西，是真的走過所有安全掃描流程，而不是某個工程師跳過安檢系統、自己在家裡做了一個長得很像的仿冒品偷偷丟進倉庫的？機制就是 **軟體映像檔簽章 (Image Signing)**。在標準流程中，只有 CI/CD 最後檢查合格的那個關卡機器人，才擁有簽名的私鑰 (Private Key)。它會在容器肚子上蓋上 `Cosign` 戳記。接著，生產線防衛營地 Kubernetes (`Admission Controller`) 就像是一台有公鑰驗鈔機的機器，它只會放行驗鈔放得出綠光的簽名檔。這種「端到端的密碼學證明信任鏈 (Chain of Trust)」，徹底瓦解了內部破壞與未授權竄改。
    *   **其餘干擾項：** B 加密不代表有「合格通過測驗」的背書。C 刪除原始碼是極端愚蠢且毀滅公司智慧財產的自殺行為。D 印出天書這無法建立物理驗票機制，哨兵一樣會吃進有病毒的假軟體。

#### **11. A massive retail company heavily relies on a third-party managed service provider (MSP) to monitor its thousands of point-of-sale (POS) systems. The MSP requires an always-on, highly privileged remote access VPN connection into the retailer's internal core network to perform maintenance. Hackers compromise the MSP's relatively weak security perimeter. They then use the MSP's legitimate, highly trusted VPN connection as a bridge to seamlessly slip into the retail company's highly fortified network, stealing millions of credit cards. Why are "Trusted Third-Party Service Providers" considered one of the weakest links in the modern supply chain?**
**(一家巨獸零售大集團仰賴他們外包聘請的第三方「機房保鑣保母大廠 (MSP)」來盯梢看管全美幾千台收銀機。這個保母這行當有特許要求：「我必須跟你們總司令部拉一條二十四小時完全不閉合、且享有直奔司令台插卡的【常駐高極端暢通 VPN 大特權連線生命通道】去遠端維修！」。隨後，駭客軍團這輩子根本攻不破那隻恐怖巨大的零售城牆。這群駭客於是改攻勢，他們直接拿那家保母外包公司弱爆的安全軟肋開刀並斬下頭顱！駭客接著直接帶上這保母的面具，搭乘這條早就開好的這條特權無敵寬敞紅地毯『VPN 信任大橋』，如入無人之境般直接走進巨型零售集團深處那防衛森嚴的堡壘核心，把幾百萬名客戶的信用卡提空！為什麼『受高度信用信任授權認證的這些協力外部第三方合作包商』，永遠在現代軟體戰略被當作供應鏈最薄且最痛的那塊致命弱側腰腹？)**
A. MSPs usually use outdated antivirus software. (這群人通常都買不起貴的現代防毒軟體)
B. Establishing an overly permissive, persistent "Trust Relationship" creates a colossal backdoor. An attack on the weaker third-party supplier allows hackers to easily bypass the primary target's strong perimeter defenses, leveraging the pre-established trust bridge. (因為一但你點頭同意並架構這種極度寬鬆無比、甚至永不打烊中斷的「兩國信任關係 (Trust Relationship)」，你等於是在金庫後方牆上開了一座巨大通風管大後門。這是一場借刀殺人的骨牌效應：當這些外包的『第三方軟柿子』供應小弟被剝皮後，駭客不用浪費子彈打主城強大的外防衛城牆火力，駭客甚至只要穿上這小弟制服跟借用本來就有的紅地毯橋樑過橋，靠著繼承而來的信任信物繞過所有安檢直搗黃龍)
C. Retail companies never patch their POS systems. (因為小商店從來不修自己的機器漏洞)
D. Third-party providers often steal the data themselves. (因為協力包商通常就是內賊會把財物直接搬光)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是資安史上最有名的 Target（塔吉特百貨）信用卡一億筆外洩事件的完美復刻。這帶出了 **第三方/供應商風險管理 (Third-Party Risk Management, TPRM)** 最可怕的核心概念：你的防禦力不取決於你自己的城牆有多厚，而是取決於 **「擁有你金庫大門鑰匙的最弱那個朋友」** 的城牆有多厚。這叫作供應鏈傳染病攻擊 (Island Hopping)。企業為了外包省錢，經常會給外部廠商（修空調的、幫忙盯防火牆的）拉一條「永遠信任且白名單 (Allowlisted Network Trust)」的特長 VPN 暗道。只要駭客把這家防護極弱的小公司帳號攻陷，駭客就能「合法地」沿著這條沒人設防的高速公路開卡車撞進巨型企業。解決方法就是落實「零信任架構」，就算你是包商來敲門，在機房通道還是處處設管制門。
    *   **為何其他是干擾項：** A, C, D 都有可能發生，但這無法從高架構戰略的維度來解釋整場「跨島國跳板登陸、信任橋樑變死亡大道」這種借道伐首駭人等級的神髓與連鎖攻擊精妙之處。

#### **12. Your team wants to incorporate a fantastic open-source charting library into your commercial, proprietary payroll software. During the architectural review, the legal department discovers that this specific open-source library is governed by the "GNU General Public License (GPL) v3". The lawyers immediately forbid the developers from using it. Why is integrating a GPL-licensed component into a closed-source, commercial product considered legally and operationally catastrophic?**
**(技術團隊發現了一個美極了的開源不用錢免費表格繪圖小模組，然後興高采烈地要把它「內核融合」深埋塞進我們自家血汗打造、且一套要賣幾百萬這套極端無價機密的商業發大財計薪私有軟體中！就在這千鈞一髮上線建築會議的剎那，法務老怪物衝進來尖叫！因為他看見這個小元件它的名字合約上居然附帶了這條條款：『GNU 普遍公共授權條款 (GPL) 第 3 版授權』！法務律師立刻毫不留情當頭棒喝嚴厲阻止並且甚至要工程師馬上去洗手不准再碰。將這等 GPL 加持過的光明開源物件融進黑暗閉門鎖著收費的極端獨有商業機密心血產品，為什麼對於公司來說在營運面是一場粉身碎骨的法律毀滅毒藥劫難？)**
A. The GPL requires you to pay a massive royalty fee for every user who clicks on the chart. (這合約的這條規則會要你在每個客戶按這表時，按抽成趴數給他超級保護智財費)
B. The GPL is a strong "Copyleft" (Viral) license. If you link or incorporate GPL code into your proprietary software and distribute it, the license legally forces you to also open-source your entire, highly valuable proprietary codebase under the same GPL terms. (GPL 是一個具有極端猛烈劇毒感染性與同化能力的『強大 Copyleft (公共著作權傳染)』證書！這代表一種狂教規矩：一旦你家這些幾百萬美金的商業極度機密獨家原始源碼區塊，哪怕只是去觸碰、引用或揉合了這個開源玩意！而你把它拿去市場發放了。在法庭上被稱為強迫連坐效應，這會用法律硬逼迫你這整套極端寶貴商業程式，【通通必須被迫全面扒光公開成為免錢免費可隨意修改發佈的另一套開源軟體】，也全都被這個 GPL 原教旨條約生吞活剝給吸收並同化)
C. GPL software is notoriously unsecure and filled with known backdoors. (因為這證書體系軟體早就一堆大洞背後黑道在運作)
D. The GPL explicitly prohibits the software from being used for financial or payroll purposes. (他這張證書上寫著這工具就只有不能這兩種產業用)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 開源軟體供應鏈風險不僅僅在「程式碼有沒有漏動」，它的另一個斷頭台是 **「智慧財產權授權法規與合規性 (Licensing & Compliance)」**。開源授權分為兩大派：一種是寬鬆的老好人 (Permissive，如 MIT 或 Apache)，它說「我沒收你錢，你拿我的去賺了幾億也是你厲害，只要註明一下作者是我即可」。但另一派是極端狂熱的 **GPL (強屬性 Copyleft)**。GPL 的精神是「知識必須共享」，它帶有強烈的 **「病毒性/傳染性 (Viral effect)」**。一旦你這個小偷公司把他的開源軟體做為骨幹連結進了你的產品又拿去散佈，你就會被 GPL 的咒語糾纏：你連帶必須要將你外星等級的心血結晶「強迫 100% 原始碼曝光給全世界，且禁止閉源收授權費用」。這是商業公司最恐懼的供應鏈智慧財產權污染核爆彈。
    *   **為何 A, C, D 大家都是干擾項：** GPL 精神剛講過是共用不用錢的，並沒有什麼抽版稅收成這種貪財想法。它是理念狂熱而非惡意集團，且無硬性拒絕特定商業場域。其致命的強迫性只對同化別人的源碼有毀天滅地的強制作怪效力。
