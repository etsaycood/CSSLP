# 第二套全真模擬試題 (Exam 2) - 答案與詳解本
## 領域 6：安全的軟體測試 (Secure Software Testing) (17題) - Part 1 (Q1-Q9)

---

#### **1. A QA engineer is preparing to conduct Dynamic Application Security Testing (DAST) on a newly developed web application. Before launching the automated DAST scanner against the target environment, what is the absolute FIRST and most critical administrative action the engineer MUST perform?**
**(一名品保工程師 (QA) 正摩拳擦掌，準備對一款剛出爐的熱騰騰網路應用程式，啟動那猶如狂轟濫炸般的『動態應用程式安全測試 (DAST)』掃描黑魔法。在真正按下那顆啟動自動化 DAST 掃描機大砲、朝目標陣地開火的按鈕『之前』！在這生死一線的時刻，這名工程師【絕對必須、不管天塌下來都要先做】的最核心、最致命的『行政管理動作』是什麼？)**
A. Obtain explicit, formally documented authorization and scope definition from the system owners. (必須取得來自該系統最高擁有者主權人的：『絕對白紙黑字、斬釘截鐵的【正式授權同意書 (Authorization)】與【精密畫押的轟炸範圍界線 (Scope definition)】』！)
B. Download the target application's latest source code repository. (趕緊去把目標應用程式最新鮮的全套原始碼給偷下載回家)
C. Disable the production Web Application Firewall (WAF) to ensure the scanner's payloads are not blocked. (馬上把上線營運環境的那座偉大網頁防火牆 (WAF) 給強制拔插頭關掉，以保證掃描機射出的子彈絕對能暢通無阻打中目標)
D. Notify the local law enforcement agency about the impending scan. (打電話報警，通知當地管區警察局說自己要開掃描機了)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **「取得正式授權 (Authorization) 與 範圍界定 (Scope)」** 是所有資安攻擊性測試 (包含 DAST, 滲透測試) 凌駕於一切技術之上的『最絕對鐵律』！DAST 掃描機的本質，就是模仿駭客發送成千上萬發的真實惡意攻擊封包 (SQLi, XSS, 甚至可能觸發 DoS)。如果你沒有事先取得這台主機真正主人的白紙黑字簽約同意，在法律上，你這個掃描行為跟「真實的惡意網路駭客非法入侵」是【完全無法區分且觸犯聯邦重罪的】。此外，必須嚴格界定 Scope (例如：只准打 Test 環境，絕對不准掃到 Production 資料庫)，一旦越界，就是等著坐牢或賠償天價。
    *   **為何其他錯：** DAST 是黑箱測試，不需要原始碼 (B)。絕對不應該隨便關掉 Production 的 WAF (C)，這會害死公司。

#### **2. A development team is integrating security testing into their CI/CD pipeline. They want to systematically identify known vulnerabilities (such as out-of-date HTTP servers or unpatched OS libraries) within the Docker containers they build, without actually executing the containerized application. Which specific type of testing tool should they implement in the build phase?**
**(一支無比前衛的開發大軍，正要把那些冷血的安檢關卡死命嵌入到他們那條如高速公路般的 CI/CD 發布流水線中。這群長官下了一道死命令：「我們必須用一種系統化如Ｘ光掃描的方式！嚴厲揪出我們剛打包好的 Docker 鐵皮貨櫃裡面，是否偷偷帶有那種【舉世皆知、早被通緝的古老腐敗漏洞 (例如用了過期的 HTTP 老伺服器，或忘記打疫苗修補的破爛 OS 零件庫)】」！且最玄的是：長官要求【絕對不准把這些貨櫃給實際通電開機執行！要在它們還是屍體狀態時就用機器摸出毛病】！請問在這條輸送帶上，他們必須架設哪一種名號的專門檢驗安檢門？)**
A. Static Application Security Testing (SAST) (靜態大透視源碼掃描機 SAST)
B. Interactive Application Security Testing (IAST) (互動式安檢追蹤劑 IAST)
C. Software Composition Analysis (SCA) / Vulnerability Scanning (軟體祖宗十八代血統成分大解析 (SCA) / 老弱殘兵弱點盤查儀 (Vulnerability Scanning))
D. Penetration Testing (紅隊殺手滲透測試)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是現代容器化 (Docker/Container) 開發必考題。題目明確指出兩大特徵：(1) 尋找「已知漏洞 (Known vulnerabilities)」，例如過期的函式庫 (CVEs)；(2) 「不開機執行 (Without executing)」。這正是 **軟體組成分析 (SCA, Software Composition Analysis)** 與 **容器弱點掃描 (Container Vulnerability Scanning)** (如 Clair, Trivy) 的核心專長。SCA 掃描器會像開拆盲盒一樣打開 Docker image 的那層皮，列出一張長長的 BOM (物料清單)，包含裡面裝了什麼版本的 Linux, Apache, OpenSSL，然後拿去跟全球駭客漏洞資料庫 (NVD/CVE) 的通緝令比對。看有沒有撞名。這不需要跑程式碼，而且完全專注於「第三方開源零件的腐敗程度」。
    *   **為何 SAST (A) 不是最佳解：** SAST 只管「你自己手工業手寫的那幾行程式碼有沒有寫錯邏輯」，它管不到你那台 Docker 裡面裝的隔壁棚開源 Apache 是不是過期。

#### **3. During a Black-Box penetration test, the tester is provided with absolutely no internal documentation, source code, or architecture diagrams of the target web application. The tester discovers a hidden administrative endpoint by running a tool that rapidly sends thousands of common directory names (e.g., `/admin`, `/backup`, `/test`) to the web server and observing the HTTP response codes. What testing technique is the tester employing?**
**(在一場血肉模糊的『究極黑箱 (Black-Box)』滲透測試生死戰中，這名殺手駭客被殘忍地蒙上雙眼：他手邊【連一張衛生紙大小的內部說明書、半行原始碼、甚至半張架構地圖都沒有被施捨】！但他卻奇蹟似地挖出了這網站偷偷藏起來的『皇城後台管理員小門 (Hidden administrative endpoint)』！原來，他祭出了一把盲掃機關槍大砲，這台砲會像瘋子一樣，以每秒千發的速度，朝著這網站的牆壁上瘋狂射出成千上萬個『世上最菜市場、最常見的資料夾名字 (比如說：`/admin`, `/backup`, `/test`)』。然後這殺手就趴在牆上，安靜傾聽網頁伺服器被砸到後所發出的『HTTP 痛苦回傳慘叫聲 (Response codes 像是 200 或 404)』來判斷門在哪裡。這殺手究竟是在施展哪一套暗黑探勘邪術？)**
A. Code Review (大家排排坐看程式碼大會)
B. Fuzzing (盲目亂餵垃圾大嘔吐測試法)
C. Directory Brute-Forcing (Directory Enumeration) (瞎子摸象之目錄地毯式暴力窮舉猜測法 / 目錄枚舉探索術)
D. Fault Injection (打斷狗腿之物理故障逼供注入術)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「目錄暴力破解 / 枚舉 (Directory Brute-Forcing / Enumeration)」** (常用工具如 DirBuster, Gobuster) 是黑箱測試中「偵察階段 (Reconnaissance)」的看家起手式。因為駭客沒有設計圖，他不知道網站把後門藏在什麼網址。他只能拿著一本寫滿幾百萬個單字的字典檔 (`admin.php`, `test.html`, `backup.zip`) 狂敲伺服器。如果伺服器回傳 `404 Not Found`，代表沒這門；但如果突然蹦出一個 `200 OK` 或是 `401 Unauthorized`，駭客的嘴角就會上揚，因為他知道他剛剛瞎貓碰上死耗子，撞倒了一扇隱藏的活人暗門。
    *   **為何不是 Fuzzing (B)：** Fuzzing 的本質是「塞入超級長的亂碼或亂變形的格式，試圖把系統『操到當機崩潰噴錯誤 (Crash)』」。而目錄猜測只是在「尋找現有門的位置」，並不是想把那扇門給搞壞。

#### **4. A massive, complex legacy C++ financial application occasionally crashes in production, but the root cause is exceptionally difficult to reproduce manually. The security testing team decides to implement a specialized testing methodology where an automated tool endlessly feeds massive amounts of highly mutated, completely malformed, and randomized data into the application's input fields (like file parsers and network sockets) while simultaneously monitoring the application for memory segmentation faults or crashes. What is this specific testing technique called?**
**(有一台龐大如巨龍、用上古 C++ 咒語寫成的金融結算神機，它時不時就會在營運火線上突然抽搐發瘋大當機！但這病根詭異至極，工程師用人類的雙手不管怎麼重試，就是無法重現抓出那隻當機的鬼。於是，高階的安控測試死神連隊決定祭出終極殺陣！他們搬來了一台名叫「瘋子」的自動化大砲，這台大砲會永無止境、日以繼夜地向這台神機的所有嘴巴（像是檔案讀取口、網路插座洞）！【死命瘋狂灌食、餵入那些被極度恐怖基因突變過、完全畸形殘骸爛肉、且徹底亂數大洗牌的毒藥數據垃圾】！！同時，旁邊架設著心電圖死死盯著這台神機，只要它一吐血、休克或是爆發記憶體斷層破裂 (Memory Segmentation Faults) 噴出腦漿死當！電腦就會立刻截圖記錄。這套宛如恐怖滿清十大酷刑般的究極暴力檢測邪術，江湖上尊稱它為什麼？)**
A. Fuzzing (Fuzz Testing) (萬物皆可操到壞的『盲目模糊亂打大灌食測試 (Fuzzing)』)
B. Regression Testing (怕修好的洞又跑出來的乖乖牌回歸再測一次)
C. Unit Testing (微小的單元積木顯微鏡小品測試)
D. Penetration Testing (紅隊高階駭客智慧滲透演武)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 這是對 **"Fuzzing (模糊測試 / 模糊化)"** 最標準、最暴力的定義寫照。Fuzzing 根本不在乎你的程式邏輯在幹嘛，它的唯一目標就是「把你塞到撐死、崩潰、當機 (Crash)」。對於 C/C++ 等容易發生記憶體錯誤的語言，Fuzzing 是抓出 Buffer Overflow (緩衝區溢位) 的最強神器。Fuzzer 會胡亂修改 PDF 檔頭、把字串變成一萬字長、把數字改成負無窮大，然後瘋狂餵給目標程式。如果程式沒寫好防護防線，吃到這種百年難得一見的突變異種垃圾，記憶體就會崩潰 (Segfault)。抓到 Crash 的那一瞬間，就是抓到零日漏洞 (Zero-day) 的前兆。

#### **5. A development team is adopting a "Shift Left" security culture. They want a tool that can analyze the application's Java source code as the developers are actively writing it in their IDEs, instantly flagging insecure coding patterns (like hardcoded passwords or dangerous `eval()` functions) before the code is even compiled or committed to the repository. Which tool category fits this exact requirement?**
**(一支立志要改過向善、瘋狂擁抱『防禦極限安全左移 (Shift Left)』大義的開發者聖教軍！他們現在急需一尊神像法器：這法器必須能如背後靈一般，死死盯著這群工程師。當這群人在他們的開發神器軟體 (IDEs) 裡、甚至還在敲打鍵盤熱騰騰寫著 Java 祖傳程式碼的那一秒鐘！只要他們敢打錯字、寫出像『把資料庫密碼白癡般明文寫死在裡面』，或是『呼叫了會引爆核彈的 `eval()` 死亡函數』。這法器【必須在這些程式碼連編譯 (Compile) 都還沒編譯、連傳上中央雲端金庫 (Commit) 都還沒傳的『最初始草稿卵子狀態』】，就立刻閃紅燈瘋狂打臉警告這名工程師！請問，能夠完美勝任這項『未卜先知抓內鬼』神聖任務的工具大類，尊姓大名為何？)**
A. DAST (Dynamic Application Security Testing) (要等到程式活跳跳跑起來才能打靶的動態大砲 DAST)
B. SAST (Static Application Security Testing) (趁程式碼還是塊死肉時就用 X 光透視找癌症的『靜態白箱大透視鏡 SAST』)
C. WAF (Web Application Firewall) (在網際網路大馬路上站崗的高速公路收費站警察 WAF)
D. IAST (Interactive Application Security Testing) (跑在系統肚子裡的互動式寄生蟲 IAST)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「SAST (靜態應用程式安全測試)」** (又稱白箱測試)，是「安全左移 (Shift Left)」最左端的那把看門劍。SAST 的特色就是「不看活人看死屍」：它不需要把程式編譯或架設起來跑，它純粹就是一個「超級無敵聰明的文法與字串掃描分析大師」。SAST 甚至可以直接以外掛 (Plugin) 的形式裝在工程師的開發畫板 (IDE, 如 IntelliJ, VSCode) 上。工程師每打一行字，它就像背後的指導老師一樣幫你挑錯 (例如 SonarQube)。這讓漏洞在連工程師的筆電都還沒踏出去的嬰兒時期就被掐死，成本最低、效率最高。

#### **6. A security auditor is reviewing a massive 1-million-line codebase. Knowing that manually inspecting every line for vulnerabilities is impossible, the auditor uses a SAST tool. The SAST tool generates a report containing 4,500 "Critical" vulnerabilities. After spending three days manually reviewing the first 500 alerts, the auditor realizes that 495 of them are perfectly safe, custom-built internal functions that the SAST tool incorrectly flagged as dangerous. In security testing terminology, what are these 495 alerts called?**
**(一位悲情的資安大鑑識官，正獨自面對著一坨重達『一千萬行、宛如垃圾山般龐大』的老舊祖傳程式代碼。他深知就算看到瞎掉也看不完，於是請出了名叫 SAST 的靜態白箱透視神機來幫忙。這台神機轟隆隆跑了一天後，驕傲地吐出了一份上面寫著：『恭喜！我幫你找到了高達 4,500 個驚天動地的【毀滅級 (Critical) 漏洞】！』。這鑑識官嚇到漏尿，趕緊花了三天三夜不眠不休，親眼用肉眼一行行去看前 500 個。結果差點吐血！他發現其中高達 495 個，居然都只是公司裡某個老前輩自己寫的、其實保護得滴水不漏、安全得要命的小工具，只是因為長得很像駭客套件，就被這台弱智 SAST 機器給瞎眼胡亂標上死刑牌子通報！請問，在安控測試的學術殿堂裡，這 495 個『亂指鹿為馬、害工程師白忙一場的智障瞎警報』，被安上什麼專屬惡名？)**
A. False Negatives (偽陰性 / 漏網之魚的瞎子)
B. True Positives (真陽性 / 貨真價實的死亡真理大漏洞)
C. False Positives (False Alarms) (偽陽性 / 也就是俗稱『謊報狼來了』的假警報大鳥龍)
D. True Negatives (真陰性 / 平安無事確實沒病的安全歲月)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是資安檢測工具永遠無法擺脫的魔咒天魔：**「偽陽性 (False Positives，縮寫 FP)」**。SAST 工具非常笨，它只會看「語法長相」 (Pattern matching)。它看到程式碼出現 `input` 這個字眼，就嚇得大喊「有 SQL Injection 漏洞！」。但其實那個 `input` 早就經過工程師在上一行用十二道金牌嚴格消毒過了。這種機器大喊有病、但人類進去檢查發現根本沒病的「假警報」，就是 False Positive (謊報)。如果 FP 比例太高 (大於 20%)，工程師就會得「警報疲勞 (Alert Fatigue)」，從此再也不看這台機器給的任何報告，直接全部略過。

#### **7. A company relies heavily on a third-party, commercial-off-the-shelf (COTS) proprietary software application where they do not have access to the underlying source code. The security team needs to test the application while it is actively running in a staging environment to dynamically simulate how a real external hacker would interact with the web interface. Which testing methodology is the ONLY viable option here?**
**(這間可悲的公司，其商魂命脈深深寄生仰賴在一套『花大錢從外面別家公司買回來、包裝得漂漂亮亮的商業黑盒子成套軟體套件 (COTS)』上！悲劇的是，這家公司【連半行這軟體底下是用啥鬼語言寫的原始碼 (Source code) 都摸不到、看嘸、完全沒存取權限】。現在，上頭拔刀逼迫資安團隊，必須趁這套軟體在練兵場 (Staging) 活蹦亂跳供電運作時，去對它進行『如臨大敵般、完美模擬一個真實外國駭客如何透過點擊網頁介面去進行無情打擊』的極致實戰安檢。在這種被完全蒙眼的絕境下，天下還有哪一套【唯一存活可行】的測試大陣法能夠派上用場？)**
A. DAST (Dynamic Application Security Testing) (只有那靠著盲打亂踹看反應的動態黑箱轟炸大砲 DAST 能行！)
B. SAST (Static Application Security Testing) (靜態大白箱掃描機)
C. White-Box Testing (上帝視角的白箱全知大透視)
D. Manual Code Review (人類坐下來肉眼看原始碼)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **「DAST (動態應用程式安全測試)」** 又稱黑箱測試 (Black-box)。它的特點就是：完全不需要原始碼！DAST 把目標當作一個神秘黑箱子，它只會像個真實的駭客一樣，透過網路線，在網頁的登入框、搜尋列輸入一堆奇怪的 SQLi 或 XSS 病毒字眼，然後看伺服器回傳的 HTML 結果是否崩潰或是吐出密碼。當我們面對 **COTS (商業現成軟體 / 封閉原始碼軟體)** 時，因為原廠死都不會給你原始碼，SAST (缺 Source 代碼) 和 White-box 測試全部直接陣亡武功全廢。只剩下從外頭盲打敲磚的 DAST 是唯一的出路。

#### **8. The QA team is performing functional regression testing on a web application. However, the security engineering team wants to simultaneously observe the data flowing deep inside the application's memory and execution stack during these tests to identify runtime vulnerabilities without requiring the QA team to run separate, dedicated security scans. The team deploys specialized sensor agents directly inside the application server's runtime environment (JVM/.NET CLR) to monitor the live code execution. What is this advanced testing technology called?**
**(一般的 QA 品保大軍，正坐在電腦前安分守己地點著滑鼠，進行著網頁介面的『傳統功能能否運作回歸大測試 (functional regression testing)』。但這時！背後那群心機深沉的安控死神暗部，卻想要趁這波 QA 大軍在點擊網頁產生流量時，【同時去偷窺暗中觀察大伺服器機房深處，那些資料字串如何在記憶體微血管與程式執行骨架堆疊裡流竄】的最高級動態！重點是，他們還懶得叫 QA 部門額外花時間去開那些破爛的專責資安掃描機。於是，這幫死神直接使出了『如寄生蠱毒般的高科技』：他們直接把一批微小的『特戰傳感器探員 (sensor agents)』，活生生地注射、植入深埋進那台應用程式伺服器那最底層的虛擬母體引擎肚子裡 (例如 JVM 或是 .NET CLR 環境內部)！讓這群寄生蟲探員直接從內部監聽活跳跳程式碼被執行運作時的每一寸血管波動。這等將黑箱與白箱融為一體、驚為天人的新世代高階幻獸變種測試科技，尊號為何？)**
A. SAST (靜態掃描)
B. DAST (動態外在敲打掃描)
C. IAST (Interactive Application Security Testing) (這就是被奉為融合神話的【互動式應用程式安防追蹤測試大陣 (IAST)】！)
D. Vulnerability Scanning (古老的弱點盤查器)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「IAST (Interactive Application Security Testing / 互動式安測)」** 是 SAST (懂原始碼) 與 DAST (活體運行) 結合生出的現代怪物，又被戲稱為「玻璃箱測試 (Glass-box)」。以前的 DAST 在外面打子彈，不知道裡面痛哪裡；SAST 在裡面看骨架，不知道子彈長什麼樣。IAST 的做法是：直接在應用程式啟動時掛上一個監聽套件 (Agent, 像是 Java agent)。當 QA 在網頁上輸入測試帳號時，IAST 的探員在伺服器肚子裡看著這個字串，從前端一路流進 SQL 查詢指令裡。如果它發現這是一段危險拼圖，IAST 在內部直接發報：「看啊！QA 剛剛點擊了按鈕，導致第 45 行的程式碼產生了 SQL 注入漏洞！」。它完美結合了測試流量與底層追蹤的神技。

#### **9. A highly secure government application uses a complex cryptographic module. To prove that the module cannot be bypassed even under extreme duress, the testing team artificially induces hardware failures by cutting power to specific CPU pins and manipulating the system clock speed during cryptographic operations to see if the system correctly "Fails Secure." What type of specialized testing is this?**
**(一台攸關國家命脈安危的極密政府主機，裡面掛在一套極度複雜的加密黑盒子。為了向將軍證明：『這黑盒子就算在面臨天崩地裂、被飛彈炸掉一半的極端滅絕絕境外，也絕對不會妥協開門放人』！這群瘋狂的測試敢死隊，竟然在加密運算到一半的生死瞬間，喪心病狂地人工拔掉那台機器的供電插頭、硬斬斷中央處理器 (CPU) 的特定針腳、甚至施展魔法胡搞亂調系統中樞硬體時鐘發條的超頻速度，瘋狂破壞實體層！其唯一的目的，就是要瞪大毛骨悚然的雙眼死盯著看：這套系統在其死前的最後一秒，是否真的能嚴謹地完成【『鎖死城門自刎、絕對不對外人打開的大門 (Fails Secure)』】崩潰壯舉。這等如慘烈極端拷問般的特種高難度軍事檢驗，是哪個專門門派？)**
A. Fuzzing (盲打餵垃圾法)
B. Fault Injection (Stress Testing) (這就是以折磨機體物理為樂的【斷腿物理故障注入大刑逼供術 (Fault Injection) / 極限壓力崩潰大測試 (Stress Testing)】！)
C. Penetration Testing (軟體滲透小測試)
D. Regression Testing (溫馨回歸小測試)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「故障注入測試 (Fault Injection) / 壓力測試」**。這種測試不是在找軟體邏輯寫錯，而是在測試系統的「韌性 (Resilience)」與「失效防護本能 (Fail-Safe / Fail-Secure)」。駭客有時無法破解密碼學，但他們知道如果你拔掉機器的插頭，系統重開機時可能有一秒鐘會閃過密碼檢查。因此，硬體駭客常使用「電壓毛刺 (Voltage Glitching)」或「時脈注入 (Clock Injection)」來欺騙 CPU 發生物理運算錯誤，趁機繞過權限。測試團隊為了防禦，就必須自己親自扮演上帝去拔插頭、斷網路，看這軟體在硬體死掉的慘叫中，是會把門自動解鎖 (Fail Open / 完蛋了)，還是能緊咬牙關把保險箱死死焊死封閉 (Fail Secure / 過關)。
