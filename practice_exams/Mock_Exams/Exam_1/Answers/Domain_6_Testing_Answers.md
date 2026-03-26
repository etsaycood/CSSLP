# 第一套全真模擬試題 (Exam 1) - 答案與詳解本
## 領域 6：安全的軟體測試 (Secure Software Testing) (17題)

---

#### **1. A QA engineer is preparing to conduct Security Testing on a newly compiled C++ application. The engineer possesses the final executable binary but has absolutely zero access to the original source code, internal architectural diagrams, or the developer's documentation. The engineer plans to barrage the application's input fields with randomly generated, malformed data to see if it crashes. What specific type of software security testing methodology is the engineer employing?**
**(一位品保工程師正準備對剛編譯好的 C++ 應用程式進行安全測試。工程師手上只有最終的二進位執行檔，【完全沒有】原始碼、內部架構圖，或開發者的說明文件。工程師計畫用大量隨機生成、格式錯誤的亂碼資料去轟炸應用程式的輸入欄位，看看它會不會崩潰當機。工程師正在採用哪種特定類型的軟體安全測試方法論？)**
A. White-Box Static Analysis (SAST) (白箱靜態分析 SAST)
B. Black-Box Fuzzing (Dynamic Testing) (黑箱模糊測試 (動態測試) Fuzzing)
C. Gray-Box Interactive Application Security Testing (IAST) (灰箱互動式應用程式安全測試 IAST)
D. Formal Verification and Logic Proving (形式驗證與邏輯證明)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這個情境有兩個核心關鍵字。第一是「沒有原始碼 (Zero access to source code)」，這代表這是一個純粹從外部盲目進攻的 **黑箱測試 (Black-Box Testing)**。第二個關鍵字是「用隨機亂碼轟炸看會不會當機 (Barrage with randomly generated, malformed data)」，這是在業界中尋找緩衝區溢位 (Buffer Overflows) 與解析器崩潰最經典的測試手法——**模糊測試 (Fuzzing / Fuzz Testing)**。Fuzzing 是一種動態測試 (Dynamic Testing)，因為應用程式必須真正在系統中「跑起來」，測試員才能把亂碼送進去並觀察它崩潰的反應。
    *   **為何 A 是干擾項：** SAST (靜態掃描) 的先決條件是你「必須要有 Source Code (原始碼)」或是至少要有反編譯的中介碼。因為 SAST 是一種類似查字典的『白箱 (White-Box)』原始碼文法檢查，它不會去執行那支程式。
    *   **為何 C 是干擾項：** 灰箱 (IAST) 需要在應用程式內部植入一個代理程式 (Agent) 來即時監控記憶體。情境中工程師只有外部的二進位檔案，無法安裝內部探針。
    *   **為何 D 是干擾項：** 形式驗證是使用艱澀的數學定理與密碼學演算法，去推導證明這段程式碼的安全邏輯無懈可擊（常用於航太與核電廠）。這並不是亂塞垃圾封包看它會不會死機的暴力美學測試。

#### **2. You are integrating security into the Continuous Integration (CI) pipeline of a sprawling Java project. You want to implement a tool that automatically scans the developers' raw source code every time they commit it to the repository. The goal is to detect hardcoded passwords, unsafe `exec()` calls, and missing input validation routines *before* the application is even compiled or run. Which category of testing tool is explicitly designed for this early-stage, code-level analysis?**
**(你正在將安全機制整合進龐大 Java 專案的 CI 部署流水線中。你想放一個工具，當開發人員每次發布原始碼 (Commit) 時，它就能自動掃描原始碼。目標是在應用程式『被編譯或執行之前』，就能抓出寫死的密碼、危險的系統呼叫 (exec)，或是偷懶沒寫的輸入驗證。哪個類別的測試工具是專門為這種超早期的程式碼層級分析而設計的？)**
A. Dynamic Application Security Testing (DAST) (動態應用程式安全測試 DAST)
B. Static Application Security Testing (SAST) (靜態應用程式安全測試 SAST)
C. Web Application Firewall (WAF) Fingerprinting (網頁應用防火牆 WAF 指紋辨識)
D. Penetration Testing (Pen Test) (滲透測試)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是 DevSecOps 中「向左移 (Shift-Left)」的黃金標準：**SAST (Static Application Security Testing)** 靜態測試。它就像是一個無心的文法老師，一行一行地去「閱讀」開發者剛寫好的純文字程式碼。它不需要編譯器，也不需要把網站架設起來跑。只要看到程式碼圖形長得像是 `password = "123"` 或是 `stmt = "SELECT * WHERE x=" + user_input` 這種危險的函數拼接，SAST 就會立刻發出紅色警報並阻擋那次 Commit。SAST 可以找出各種實作層面的語法與邏輯漏洞，是開發生命週期中最早介入的安全測試。
    *   **為何 A 是干擾項：** DAST 俗稱黑箱漏洞掃描器，必須等你的網站「真正架設起來且順利執行後」，它才能去對網址打封包（發送 XSS 或 SQLi）。這太晚了，與題意「編譯前」不符。
    *   **為何 C 是干擾項：** WAF 是擋在營運主機門口的盾牌，它是在生產營運階段 (Operations) 運作的，不是在開發測試階段掃描原始碼的工具。
    *   **為何 D 是干擾項：** 滲透測試通常是軟體完成度極高、快要上線營運前，花錢請白帽駭客團來發動真實攻擊，這是極度後期的動態測試。

#### **3. During a rigorous Web Application Penetration Test, the Red Team tester attempts to discover hidden administrative directories on the target server. The tester configures a proxy tool (like Burp Suite) and loads a massive dictionary text file containing thousands of common directory names (e.g., `admin/`, `backup/`, `test/`). The tool automatically sends thousands of HTTP GET requests to the server, observing the HTTP response codes (e.g., 200 OK vs. 404 Not Found) to map the hidden structure. What specific attack technique is the tester performing?**
**(在一場嚴格的網站滲透測試中，紅隊測試員試圖找出目標伺服器上隱藏的管理員資料夾。測試員設定了代理工具 (如 Burp Suite)，並載入了一個包含數千個常見資料夾名稱 (如 admin/, backup/) 的巨大字典文字檔。工具自動向伺服器發送數千次 HTTP GET 請求，並透過觀察回傳的 HTTP 狀態碼 (例如 200 找到 vs 404 找不到) 來畫出網站隱藏的地圖。測試員正在進行哪種特定的攻擊技術？)**
A. Brute-Force Directory Enumeration / Forced Browsing (暴力目錄枚舉 / 強制瀏覽)
B. Cross-Site Tracing (XST) (跨站追蹤)
C. SQL Blind Injection (SQL 盲注攻擊)
D. Man-in-the-Middle (MITM) Interception (中間人攔截)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 這個在攻擊/測試準備階段 (Reconnaissance/Enumeration) 極為常見的手法稱為 **目錄枚舉 (Directory Enumeration) 或是強迫瀏覽 (Forced Browsing)**。許多開發者錯誤地以為，「只要我的網頁上沒有放 `/backup/db.zip` 的下載連結，駭客就絕對找不到這個檔案 (隱晦式安全 Security by Obscurity)」。但駭客的字典掃描器才不管你有沒有放連結。工具會直接像機關槍一樣猜遍所有的單字。一旦伺服器笨笨地回傳了 `200 OK` 或是 `403 Forbidden`（禁止存取，這代表檔案雖然鎖住但『確實存在』），駭客就成功畫出了網站的內部地圖並找到了高價值目標。
    *   **為何 B 是干擾項：** XST 是利用古老的 HTTP `TRACE` 方法來偷取使用者的 Session Cookies。這跟猜隱藏資料夾無關。
    *   **為何 C 是干擾項：** SQL Blind Injection 是在沒有獲得錯誤回顯的情況下，盲目地向資料庫詢問「第一個人的第一個密碼字母是不是 A」，並觀察伺服器延遲的反應時間或布林結果。雖然也是盲猜，但對象是資料庫內容，而不是猜網頁的站點目錄樹。
    *   **為何 D 是干擾項：** MITM 中間人攻擊需要駭客站在通訊兩人中間去篡改或側錄封包。這裡測試員是直接和伺服器面對面單挑猜目錄，沒有介入任何第三方使用者的通訊。

#### **4. A Lead QA Tester is designing the test cases for a new "Account Lockout Mechanism." The requirements state: "The system MUST lock the account for 15 minutes after exactly 5 consecutive failed login attempts." To comprehensively verify this boundary condition, the QA tester executes three specific test scenarios: Scenario A (4 failed attempts), Scenario B (exactly 5 failed attempts), and Scenario C (6 failed attempts). What fundamental software testing technique is the tester utilizing to ensure the logic behaves correctly right at the edge of the specification?**
**(首席 QA 在為新的「帳號鎖定機制」設計測試案例。規格書寫著：「在連續 5 次登入失敗後，系統必須將帳號鎖定 15 分鐘。」為了全面驗證這個邊界條件，QA 執行了三個特定的劇本：劇本 A (4 次失敗)、劇本 B (剛好 5 次失敗)，以及劇本 C (6次失敗)。QA 工程師是利用哪一項基礎軟體測試技巧，來確保程式邏輯在『規格邊緣』正確無誤地運作？)**
A. Combinatorial Pairwise Testing (組合式正交陣列測試)
B. Fuzz Testing (模糊測試)
C. Boundary Value Analysis (BVA) (邊界值分析)
D. Statistical Code Coverage Metrics (統計程式碼覆蓋率指標)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 如果工程師的 `if` 判斷式寫錯了（例如把 `>= 5` 寫成了 `> 5`），那麼駭客就能瘋狂嘗試到第 5 次。最容易發生這種悲劇的地方就是條件判斷的臨界點，業界稱之為 **邊界值分析 (Boundary Value Analysis, BVA)**。這是一種在黑箱與白箱測試都必須執行的標準做法。如果一個數字規則界線是 N，QA 團隊的測試集就必須死盯著 `N-1`（不能鎖死）、`N`（精準鎖死）以及 `N+1`（已經鎖死了，看看系統會不會崩潰）。這是抓出商業邏輯與安全閥門瑕疵最精準有效的方法。
    *   **為何 A 是干擾項：** 組合式/成對測試是用來解決「如果系統有 20 個下拉選單，每個選單有 5 個選項，會產生幾百萬種排列組合測不完」的數學去蕪存菁技巧。與單一數字突破邊界無關。
    *   **為何 B 是干擾項：** 剛提過 Fuzzing 是向系統送入亂碼去弄當機它。此處送入的是極度正規、有意義的整數密碼失敗次數。
    *   **為何 D 是干擾項：** 覆蓋率 (Code Coverage) 測量的是「你有沒有測試到那一行程式碼」，但它無法量化「你測試那一行程式碼的數值夠不夠極端」。你可能測了 4 次的快樂路徑，覆蓋率 100%，但完全沒發現它在第 5 次會失敗。

#### **5. The development team relies heavily on an open-source JavaScript UI library (`vue.js`) and a third-party logging framework (`log4j`). The Chief Information Security Officer (CISO) is terrified that a zero-day vulnerability might be discovered in one of these dependencies, silently compromising the application. To continuously monitor and test for known vulnerabilities (CVEs) residing hidden within these third-party libraries, which specific type of automated scanning tool MUST the team integrate into their pipeline?**
**(開發團隊重度依賴開源的 JS 前端庫與第三方的日誌框架 `log4j`。CISO 極度恐懼有一天這些依賴套件裡會被爆出零日漏洞，默默攻陷應用程式。為了能「持續監控並測試」隱藏在這些第三方函式庫中已知的漏洞 (CVEs) 庫存，團隊【必須】在 CI/CD 流水線中導入哪種特定的自動化掃描工具？)**
A. Software Composition Analysis (SCA) (軟體組成成分分析 / 第三方套件分析)
B. Interactive Application Security Testing (IAST) (互動式應用安全測試)
C. Network Vulnerability Scanner (e.g., Nessus) (網路弱點掃描器，如 Nessus)
D. Static Application Security Testing (SAST) (靜態應用安全測試)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 現代的應用程式有高達 80% 到 90% 的程式碼根本不是你家公司的工程師寫的，而是從網路上 (如 npm, maven, NuGet) \`import\` 進來的外部免費套件（開源軟體 Supply Chain）。像 SAST 跟 DAST 這些工具，是專注在抓出「你家工程師自己手寫出來」的邏輯漏動。而用來清查與應對這些龐大的外來木馬成分卡的專屬雷達，叫做 **SCA (Software Composition Analysis)**。SCA 會像分析食品成分表一樣，把你的專案依賴樹 (`package.json` 或 `pom.xml`) 攤開，然後去比對全球惡意漏洞庫 (NVD/CVE)。只要發現這個被你依賴的 `log4j` 版本昨天剛被通報能被遠端拿最高權限，SCA 就會立刻阻斷編譯並通知你升級版本。
    *   **為何 B、D 是干擾項：** IAST 與 SAST 對於幾萬行的第三方依賴套件往往無能為力，因為 SAST 無法判斷這個幾千行的別人寫的加密庫究竟是安全的還是已知會被政府通緝的。要靠 CVE 資料庫比對的只有 SCA 辦得到。
    *   **為何 C 是干擾項：** Nessus 等網路弱掃是在掃「公司內網的伺服器作業系統有沒有漏洞沒打修補程式」(例如 Windows Server 沒更新版版)，它鑽不進軟體的 `package.json` 去分析 Node.js 的依賴相容套件。

#### **6. A security analyst is performing a dynamic test on a web application's search bar. She types this exact payload into the search box: `<script>alert(document.cookie)</script>`. Upon pressing enter, her browser executes the payload, and a pop-up window displays her current session cookie. The analyst successfully proved the application is highly vulnerable to which specific attack?**
**(資安分析師在一個網頁的「搜尋框」進行動態測試。她精確輸入了這個酬載：`<script>彈出視窗(印出我的餅乾憑證cookie)</script>`。按下 Enter 後，瀏覽器立刻反彈回這個腳本並執行了它，螢幕上跳出一個視窗顯露了她當前的 Session 餅乾。這位分析師成功證明了網站極度容易遭受何種特定攻擊？)**
A. Local File Inclusion (LFI) (本地端檔案包含攻擊)
B. Stored / Persistent Cross-Site Scripting (XSS) (儲存型 / 持續型跨站腳本攻擊)
C. Reflected / Non-Persistent Cross-Site Scripting (XSS) (反射型 / 非持續型跨站腳本攻擊)
D. Cross-Site Request Forgery (CSRF) (跨站請求偽造)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是 Web 測試中最經典的一幕。因為輸入的值是填在一個「搜尋框 (Search Bar)」，它的生命週期是極度短暫的：封包飛去伺服器，伺服器因為沒有做輸出編碼 (Output Encoding)，就把這句有毒的腳本連同「為您搜尋的結果是：`<script>...`」這句錯誤的網頁原封不動地「反彈 (Reflect)」回瀏覽器。瀏覽器引擎不疑有他，把它當成了神聖的官方 JavaScript 碼當場執行。這種類型的 XSS 攻擊稱為 **反射型 (Reflected XSS)**。駭客要利用這個漏洞，必須弄一張釣魚網址傳給你點擊，網址裡面就偷夾了這段毒代碼。
    *   **為何 B 是干擾項：** 儲存型 (Stored / Persistent XSS) 的殺傷力更大。它是分析師把這個毒代碼「存進了資料庫（例如留在某篇文章底下的留言板）」。以後不管誰打開這篇網頁，不用點什麼釣魚連結，伺服器都會把毒代碼從資料庫掏出來倒在他臉上。這裡情境是搜尋框，並沒有提到存入資料庫長期留存。
    *   **為何 A 是干擾項：** LFI 是試圖讓網頁去讀取伺服器內部的重要檔案（如密碼設定檔）。這題是讓前端瀏覽器自己去彈警告框彈出自己的 Cookie。
    *   **為何 D 是干擾項：** CSRF 是誘騙已登入的使用者去點一個連結（如 `bank.com/transfer?amount=1萬給駭客`），這是發出「非自願請求」，而非在受害者瀏覽器上「執行惡意惡搞碼拿走 Cookie」。

#### **7. You are managing a massive testing effort for a legacy C banking backend. To ensure the testing is thorough, the QA manager insists on measuring "Code Coverage." The manager states: "Our goal is to execute test cases until we achieve 100% Branch Coverage." In the context of White-Box testing, what does "Branch Coverage" specifically guarantee?**
**(你正在管理舊版 C 語言銀行後台的大規模測試。為確保測試徹底，QA 經理堅持要測量「程式碼覆蓋率 (Code Coverage)」。經理說：「目標是執行測試案例直到達成 100% 分支覆蓋率 (Branch Coverage)。」在白箱測試的背景下，什麼叫做「分支覆蓋率」？它保證了什麼？)**
A. Every single function in the application has been called at least once by the test suite. (保證程式裡每一個大函數都至少被測試集叫過一次，就算只有摸到表面)
B. Every line of source code in the application has been executed at least once by the test suite. (保證程式裡的每一行純文字程式碼都至少被執行過一遍 (行覆蓋率/陳述覆蓋率))
C. Every possible boolean decision outcome (both the 'True' and 'False' paths of every `if/else` statement) has been executed at least once by the test suite. (保證每一個可能的布林決策結果——包含每一個 `if/else` 裡面通往『是』和通往『否』的兩條路——全都有被測試大軍走過至少一次)
D. Every possible combination of input variables has been exhaustively tested. (每一個所有輸入變數的天文交叉組合都有被測試到極限值)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是白箱測試單元測試的心法。最普通的覆蓋率叫做「邏輯語句/行數覆蓋率 (Statement Coverage)」，只要程式每走過一行就算數。但這會有極大死角：如果你寫個測試檔只送了一個 `if(True)` 的快樂測試案例進去，雖然把裡面的程式碼都跑完了，但覆蓋率報告可能覺得你完工了。然而，資深測試者最在乎的進階標準是 **分支覆蓋率 (Branch/Decision Coverage)**。它會像樹枝一樣嚴格檢查程式裡每一個「分叉路口 (`if` 或是 `switch` 或是 `while`)」。如果你只測了密碼打對的時候 (True) 系統能登入，卻沒寫半個測試去測看看當你密碼故意打錯的時候 (False) 系統會怎麼拒絕你，那你的 Branch Coverage 就會不及格，這是逼迫開發者把防守與錯誤攔截邏輯寫好的強大測量指標。
    *   **為何 A 與 B 是干擾項：** 這兩者分別對應 Function Coverage 與 Statement Coverage。它們比分支覆蓋率弱上許多，無法保證防守邊緣與決策樹的異常路徑有被檢測到。
    *   **為何 D 是干擾項：** 這叫做 Path Coverage (全路徑覆蓋)，如果程式裡面有好幾個迴圈相疊，所有的路徑會達到天文數字的排列組合。在現實的軟體工程中是 100% 不可能完成全宇宙所有路徑覆蓋的，這不符合成本效益。

#### **8. An organization employs a "Bug Bounty Program" where external, freelance ethical hackers are paid directly for finding vulnerabilities in their public production website. During a live test, an external researcher discovers a flaw allowing them to download the entire customer database. However, instead of stopping and reporting the flaw, the researcher proceeds to download all 5 million records and then emails the CEO, demanding $50,000 to delete the data, threatening to leak it if unpaid. Which critical "Rules of Engagement (RoE)" boundary did the researcher flagrantly violate?**
**(一個組織在他們真實對外營運的網站上採用了「漏洞賞金計畫 (Bug Bounty)」，花錢懸賞外部業餘白帽駭客找漏洞。在一次實測中，一名外部研究員發現了能下載整個客戶資料庫的漏洞。然而，他非但沒有立刻停止並通報，反而順手把全部五百萬筆個資打包帶走。接著他寫信給 CEO 勒索五萬美金才肯刪檔，否則將公諸於世。請問這位研究員公然違反了「接戰規則 (RoE)」裡的哪條重大紅線？)**
A. The limitation on automated scanning tools. (對自動化掃描連發工具的限制)
B. The prohibition against Social Engineering the staff. (禁止對員工使用社交工程騙密碼)
C. The strict restriction on Data Exfiltration and the principle of doing no harm (Extortion). (嚴格禁止『資料外洩攜出 (Exfiltration)』，以及違反了「切勿造成真實傷害」的最高原則 (變成了勒索))
D. The requirement to use Black-Box testing methodologies only. (必須只能使用純黑箱測試的規範)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 任何形式的滲透測試或是 Bug Bounty 計畫，都會有極具法律效力的切結書與疆界：**接戰規則 (Rules of Engagement, RoE)**。在合約中，最重要的天條就是：「當你發現這個洞能摸到資料庫時。你只要能證明你可以 Select 出一筆測試帳號 (Proof of Concept)，你就要馬上停手，並立刻通報」。RoE 絕對嚴格禁止測試者私自進行 **資料攜出 / 竊取 (Data Exfiltration)**。這名研究員不僅把真實客戶資料盜走，還跨過最後紅線向受害者勒索，這就是典型的由白轉黑（變成網路罪犯），這是要在聯邦監獄坐牢的嚴重犯罪。
    *   **為何 A 是干擾項：** RoE 雖然有時會規定你不能用大砲掃描器把頻寬塞爆，但這不構成情境中勒索資料的事實。
    *   **為何 B 是干擾項：** 社交工程是指假扮客服騙員工密碼。這位老兄是直接打穿軟體系統，沒有騙人，他只是在事後勒索了系統維運的老闆而已。

#### **9. A highly advanced testing tool operates from *inside* the application environment (like a Java agent). While the QA team clicks around the web frontend performing normal functional tests (DAST), this internal agent continuously monitors the backend memory, database queries, and variable data flows in real-time. If it detects a SQL injection payload moving through the application's memory toward the database, it immediately flags the exact line of Java code responsible. What is the industry term for this hybrid testing technology?**
**(一種極端高科技的測試工具，它『直接附身潛伏在後端應用程式環境的內部』 (就像是個 Java Agent 探針)。當 QA 團隊在網頁前端隨意點點滑鼠（做一般的黑箱常規測試）時，這個隱藏在內部的特務會即時、全天候監測後台記憶體讀寫、資料庫查詢，以及所有的變數資料流動。一旦它在記憶體中抓到一段 SQL 注入毒藥正準備朝資料庫飛去，它就會像警報器一樣跳出來，精準標定出到底是哪行錯誤的 Java 原始碼放進這個毒藥的。這種內外包夾混血科技產業術語叫什麼？)**
A. Static Application Security Testing (SAST) (靜態測試)
B. Fuzz Testing (模糊測試)
C. Software Composition Analysis (SCA) (軟體組成分析)
D. Interactive Application Security Testing (IAST) (互動式應用安全測試)

*   **正確答案 / Correct Answer：D**
*   **[解析邏輯]**
    *   **為何 D 是最佳選擇：** 這題是在考測試光譜的最前端技術——**IAST (Interactive Application Security Testing)**。你可以把它想像成是 SAST (白箱，看得懂你的原始程式碼在哪一行) 加上 DAST (黑箱，要在測試環境中由真實人類去點擊觸發封包運作) 生下的最強混血兒，這被稱為灰箱測試 (Gray-Box Testing)。IAST 的最大劣勢是必須將探針「物理安裝」進測試儀表板 (Tomcat, IIS) 內，非常麻煩。但優勢是它不僅沒有 DAST 那些抓不到後端隱藏死角的盲區，更沒有 SAST 煩死人總是發出「假陽性 (False Positives)」誤判警報的缺點。因為如果探針親眼看到那段封包在記憶體裡面活著跑出來，那就 100% 絕對是個致命且立即生效的真漏洞，而且它能把案發現場源頭的 Java Code 行號交給你。
    *   **為何 A 是干擾項：** 靜態 SAST 是像讀死書，它是靜態掃描不用放封包去跑的。
    *   **為何 C 是干擾項：** SCA 是清查那些別家廠商寫的開源舊版過期函式庫清單。

#### **10. A penetration testing team successfully exploits a vulnerable web server, obtaining a low-level "guest" shell access. Their ultimate objective is to read a highly sensitive configuration file restricted to the "root" administrator. The testers discover an outdated local kernel process running in the background. They execute an exploit against this specific kernel process to upgrade their "guest" shell into a "root" shell. In the standard phases of Penetration Testing, what specific phase does this action represent?**
**(滲透測試隊伍成功利用了某個網頁漏洞，取得了一個超底層、能力極低的「訪客 (guest) 遠端連線終端機 shell」權限。測試組的最終極目標是要偷走一份只有『根統治權管理員 Root』才能讀取極機密設定檔。組員發覺了在背景活在那台測試機器裡的一個老舊系統核心程序。組員對此程序打入第二發專用剝削代碼，奇蹟似地把這隻窮苦訪客權限直接洗白拔高成了「上帝 Root」權限！在滲透測試的標準生命週期步驟裡中，這個超絕升華的行為隸屬於哪一個階段？)**
A. Reconnaissance and Information Gathering (偵查籌備及情報收集)
B. Elevation of Privilege (Privilege Escalation) (特權提升行動)
C. Vulnerability Scanning (弱點機具全盤無差別掃描階段)
D. Covering Tracks and Maintaining Access (消彌掩蓋犯罪足跡並保留後門維持後續遠端存取)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 當滲透測試（或真實駭客）成功越過城牆踏上城牆（取得初期的 System Access），通常拿到的只是一個在安全死角掃地的農民工權限，什麼核心機密都看不到。他們必須像這題一樣，利用系統內部的設定不當或作業系統核心 (Kernel) 老舊的二次弱點，打破階級，將自己的帳號變身成具有至高無上控制權的法老王 (Root / Domain Admin / SYSTEM)。在駭客攻擊與測試的殺傷鏈 (Kill Chain / Pen Test Methodology) 中，這種橫向或是向上跳躍的特定專業行為與階段，就被強烈且專門定名為 **特權提升 / 權限躍升 (Privilege Escalation / Elevation of Privilege)**。
    *   **為何 A 是干擾項：** 偵查是在牆外找大門，找 IP 跟看你用什麼版本，根本還沒打進去。
    *   **為何 C 是干擾項：** 只用掃描器掃一遍是漏洞掃描，這叫『實測拿到了殼並且去操縱』了，已經遠超掃描階段。
    *   **為何 D 是干擾項：** 這是打穿後、偷完東西後，準備打包走人之前把所有伺服器登入日誌全部刪掉殺光的最後工作。目前駭客正準備開保險箱而已，還太早。

#### **11. A security auditor reviews the test plan for a new cryptographic module. The programmer wrote a test that successfully encrypts a string of text. The test then asserts: `assertTrue(encryptedText.length() > 0)`. The auditor rejects this test case as completely insufficient for cryptographic testing. What is the fundamental problem with this specific test approach regarding cryptography, and what must be tested instead?**
**(資安稽核員正在審查一個剛出爐的底層密碼學模組加解密測試計畫。其中，開發人員寫的一個單元測試這樣運作：「我給了模組純文字。模組回傳給了我密碼文。最後我要測試工具『去保證！密文有大於大於零的長字數』，代表我沒吐空，結案！」。稽核人員把這這份密碼測試案丟到垃圾桶且無比鄙視。為什麼對於密碼學的工程測試而言這是一種嚴重的侮辱？到底對於這演算法這工程師本來必須該多測甚麼才是鐵則？)**
A. The test is written in Java, but cryptography should only be tested using C++. (他寫 Java，但是密碼測試只能用低階 C++)
B. The test only verifies that *some* output was generated, but it utterly fails to prove that the output mathematically matches the expected, standard ciphertext (Known Answer Test / KAT) or that the data can actually be successfully decrypted back to its original state. (這個蠢測試僅僅只是驗證了程式『有吐出一些垃圾東西而沒有因為錯誤崩壞當掉空白』而已！但這測試徹底失敗且沒人知道那個被加密的胡言亂語是否與「標準答案/已知答案模型測試 (Known Answer Test)」對齊。或是這密文是不是未來還能被完好無缺的『雙向解密』退回最原始的心血狀態)
C. The test executes too quickly, which violates the requirement for slow cryptographic operations. (這單元測試運作極快，然而演算法本來就必須非常慢。這等長度不足夠測試機器效能)
D. Cryptography cannot be unit-tested; it must only be tested via Black-Box penetration testing. (密技學本來都沒辦法在開發前期作這等模塊單元測量。那通通都必須等上架之後做駭客侵入黑黑操作)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 測試密碼模組時最大的笑話就是：「我塞了一堆蘋果進去，果汁機吐出了一堆黑黑的泥巴。這證明果汁機防禦絕佳有打碎並加密，而且沒當機 (Length > 0)，測試完美通過！」這是災難。密碼學測試 (Cryptographic Validation) 的黃金要求不僅是要它打碎，最重要的要求之一是：**你要能用那把鑰匙把它從黑漆漆的泥巴完美 100% 變回那一堆紅色原裝無損的蘋果 (Symmetric Decryption Verification)**。第二，如果演算法是業界標準 (如 SHA 或 AES)，你需要引用 **已知答案測試 (Known Answer Tests - KATs)**。NIST 政府會提供標準範本：「如果你拿密碼 "A" 去生一塊 128AES」，保證這世界上所有機器吐出來的亂碼字元都會而且也必須是 "1F8A..."。如果你的機器出來的亂碼不是這個政府標準答案，你的密碼發生器裡面就充滿了惡魔般的邏輯錯誤與實作瑕疵。
    *   **其他干擾項：** 完全與密碼學的實務無關。特別是 D 絕對錯誤，密碼學必須擁有這等大量的單元測試在代碼底層狂操。

#### **12. A dedicated "Red Team" is hired to conduct a full-scope simulated cyberattack against an enterprise. Unlike a standard Penetration Test that focuses solely on finding software bugs, the Red Team heavily utilizes "Phishing Emails" mimicking the CEO, drops infected USB drives in the company parking lot, and attempts to tailgate employees through the physical security gates. What is the primary objective of this comprehensive Red Team engagement?**
**(企業砸重金聘請傳說中的專職「紅隊 (Red Team)」發起一場地圖砲規模的模擬網攻戰。跟傳統僅僅針對某個網路系統點尋找幾隻可憐程式碼小蟲的滲透測試大不相同— 紅隊成員開始模仿 CEO 寄送帶毒重磅『釣魚信』炸彈，半夜跑去公司側門停車場亂丟佈局了帶有遠端木馬感染程序的免費漂亮 USB 隨身碟，他們甚至派人套上水電工衣服尾隨剛刷過卡要去買咖啡的員工強行混入公司物理閘門防線！企業這場全面性紅隊戰鬥大戲真正、終極的檢測目標為何？)**
A. To measure the exact number of XSS vulnerabilities in the web application using SAST tools. (要算清楚程式理有幾百隻小 XSS 的精準數量)
B. To test the holistic effectiveness of the organization's entire defensive posture, including its people (security awareness training), processes (incident response), and physical security, not just the technical software controls. (為了去試煉這家大型組織在『全方位全面』上的一體化防衛反應力架構！不僅包含它硬邦邦的電腦軟體技術，更是嚴苛檢驗了『這家公司的人性弱點 (是否能抗拒亂點隨身碟的認知資安意識教育)』，以及檢驗當紅燈大作時這公司流程上『第一時間通報事件反應 SOP 的神經協調性』以及最『實質的門薩保全站崗機制』)
C. To debug the Continuous Integration (CI) deployment scripts. (要修整 CI 持續布屬上的爛漏洞腳本機制)
D. To verify compliance with the General Data Protection Regulation (GDPR) privacy rules. (用來檢查有沒有乖乖聽歐洲資料保密跟保護法規的話)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是區分「網頁滲透測試 (Web Pen Test)」與 **紅隊演練 (Red Teaming / Full-Scope Simulation)** 最核心的考點。一般的滲透測試通常很有禮貌，目標往往限縮在一台孤單的對外網路伺服器，只找程式技術的漏洞 (Technology)。但紅隊演練是一場流氓戰爭。駭客除了網路以外，也極度針對安全架構最薄弱的環節——**「人類 (People)」與「流程 (Process) 以及物理設備 (Physical)」** 發動組合打擊。這叫做全面性的（Holistic）資安體質壓力測試（包含利用心理學社交工程的釣魚郵件騙密碼，直接走到別人辦公室桌上把未上鎖但插著密鑰卡的筆電螢幕拍照盜用）。
    *   **為何 A 與 C 是干擾項：** 殺雞焉用牛刀，SAST/DAST 工具這些程式設計師自己在實驗室跑一跑就做完了。你不用請紅隊來找單一的 XSS。
    *   **為何 D 是干擾項：** GDPR 是合規與法律隱私要求，法務跟外部四大的稽核員對照報表簽字就好。

#### **13. During a DAST scan of an online forum, the automated tool detects a concerning behavior. The scanner inputs `1' OR '1'='1` into the username field. The resulting HTTP response does not display a visible database error on the screen, nor does it log the user in. However, the automated scanner noticed that the web server took exactly 15 seconds to respond to that specific malicious payload, whereas all normal requests only take 0.1 seconds. What sophisticated vulnerability did the scanner likely discover using this time-delay technique?**
**(自動化 DAST 掃描器在掃論壇時察覺了詭異現狀：掃描儀向使用者登入格發送了一句極其邪惡的 SQL 數學咒語 `1' OR '1'='1`。隨後反饋回來的 HTTP 頁面上，『完全沒印出任何像是「資料庫出錯了！」等血淋淋錯誤外洩語』。且登入竟然也乾乾淨淨地被阻擋沒有讓他偷繞進去。但是！！這具電腦掃描儀極度靈敏地捕捉到：就在打出這行字發送封包後，那個原本連線 0.1 秒就該吐回網頁的伺服器，竟然像是中邪了一般「整整苦思停格發愣等待了死亡 15 秒！！」才慢吞吞把失敗頁面傳回。掃描儀藉由這種「刻板的時間延遲度量暗殺法」最可能精準挖出了何種惡劣漏洞？)**
A. Time-Based Blind SQL Injection (基於時間的盲注式 SQL 注入攻擊)
B. Denial of Service (DoS) Resource Exhaustion (耗盡所有防護阻斷伺服服務)
C. Reflected Cross-Site Scripting (XSS) (非駐留跨站前端腳本感染)
D. Cross-Site Request Forgery (CSRF) (請求端造假跨位劫持)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 當程式設計師已經修好了第一個洞，把討人厭且會大量洩露資料庫錯誤訊息的 Error Code 都關掉遮起來時。如果他懶惰沒順手把防禦的「字串參數化查詢」一起實做補滿，那這系統就會面臨 **盲注攻擊 (Blind SQL Injection)**。在盲注裡沒有錯誤可看，所以系統像是又瞎又聾。測試者只好強迫發射極端具有時間拖延與數學惡作劇的語句 (例如使用特製等同發送了 SLEEP 15 秒命令的條件式，如：`如果第一個提款密碼字母是A，那就請您睡 15 秒再叫我`)。當測試工具精確捕捉到這一筆超常態 15 秒延遲回應時。駭客與工具就知道：「中了中了！！這個沒聲音沉默的主機，其實已經把你的這段可怕 SQL 代碼活生生吞下肚，並在它內部腦部運轉照做了！」。這被譽為時間式盲測 SQLi。
    *   **為何 B 是干擾項：** DoS 是幾百萬的大軍要把系統幹死永遠無法呼吸。這裡這台主機只是對這個特定注入包發呆 15 秒後就健康甦醒，這是一個試水溫的特洛伊封包。
    *   **為何 C 與 D 是干擾項：** XSS / CSRF 不涉及這種精準誘騙後台資料庫去沉睡 15 秒的極端資料庫通訊回響時間測量技術。

#### **14. A tester is examining the "Password Reset" logic. She creates two identical test accounts: `victim@test.com` and `attacker@test.com`. She clicks "Forgot Password" for the victim and receives a password reset token in the victim's email inbox: `Token=XYZ123`. She then logs into the attacker's account, initiates a password reset for the attacker, but uses a proxy tool to swap the attacker's token in the HTTP request with the victim's `Token=XYZ123`. The system accepts the request and changes the *victim's* password to a new password chosen by the attacker. What critical business logic flaw did this manual test successfully demonstrate?**
**(測試員在狂拆「忘記密碼」這等底端商業邏輯的流程。她建了雙帳號 A：老好人受害者 `vic@test` 與 B：惡霸攻擊老 `atk@test`。她首先裝委屈為好人按了「我忘密碼」，於是系統開了一張重設准考證票號寄給受害者：`Token=編號X1`。接著她回到攻擊者 B 身分也狂按自己忘記密碼後啟重設流程！但在最後她竟然按下網頁攔截器工具把攻擊者的封包半路攔下改掉，把裏頭夾帶的認證票根這變數，全強制換成了『那個老好人的 Token=編號X1』並打出。系統不僅開心笑納了要求，更把受害者 A 好人的長長密碼，改換成了攻擊老 B 設定的垃圾新密碼！這個需要大量人類腦袋操作干涉手工設計所測出來的致死漏洞其正式名稱為？)**
A. Server-Side Request Forgery (SSRF) (伺服器代為打擊端要求偽造)
B. Broken Authentication / Insecure Session Management (碎裂的認證邏輯防線 / 不安全的連線階段狀態管控)
C. SQL Injection (資料封裝輸入)
D. XML External Entity (XXE) Injection (超大型外部實體擴張注入)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這個劇本描述的是現今最難掃，也最容易令新創公司面臨鉅額倒閉毀滅賠償的「業務邏輯錯誤 / 流程瑕疵」。系統在第一關雖然很聰明產了獨立一組隨機票據 Token，但在最後一階段，開發者沒有在伺服器端把『那個丟這張票進門來進行重設命令的駭客連線階段』與『那張票一開始配發主人的受害者連線階段』進行 **雙重身分核對檢查 (Validation of Session Owner Binding)**。系統傻傻只看了它拿到真票就好。任何牽涉到忘記重取密碼，並造成使用者可以直接奪走、把玩甚至摧毀替換掉別人生命帳號的管理系統這等重大故障，全都會被統一強勢歸類進 **損壞的身分認證機制 (Broken Authentication / Identity Management Failures)** 的這頂大帽子之下。這也就是所謂的帳戶奪取 (Account Takeover)。
    *   **為何 A, C, D 是干擾項：** 這是一個透過截獲網頁 HTTP 表單變數與 Session 管理瑕疵，運用兩個網址跟工具完成的大腦智力操作。這其中完全沒有任何代打內部 IP 跳板 SSRF 情節，也沒灌入任何資料庫運算用的 SQL 單引號，也完全沒有傳輸夾帶外部木馬文件的 XML實體。

#### **15. You are the security lead for a massive, multi-year software project. Management demands a comprehensive metric to determine "how well our security testing is going overall." Which of the following is the MOST meaningful metric to report to the executive board regarding the true effectiveness of the secure software testing program?**
**(你是負責幾百人常年開發史詩專案的首高資安頭號領袖。你的上頭跟高管老闆冷不防地向你要求一份最具指標性的量化測量報告 (Metric)，用來斷定：「我們團隊在這一整年的資安軟體與安全測試上到底幹得『行不行、有沒有效！』」。在下列四個報告數字中，哪一個才是最有血月價值、最有意義，能夠向滿腦子商業戰略的執行董事會展示與匯報你們團隊這些日子究竟有沒有帶來神聖幫助的「終極衡量標準 (Metric)」？)**
A. The total number of test cases written by the QA department this month. (今年測試 QA 人員爆肝硬寫產生出來的那一共好幾千筆巨量的『測試腳本數目』)
B. The percentage of developer code automatically scanned by the SAST tool within 5 minutes. (你的自動化 SAST 掃描儀表能有多麼光速神猛，在短短地 5 分鐘內用神機運算完多少百分比的總碼占比)
C. The total count of raw vulnerabilities discovered by the automated DAST scanner, including all false positives. (那個剛買來的 DAST 一次大屠殺大面積網落盲掃出來，且包含上面滿滿上百筆『誤報假警報與假陽性 (False Positives)』在內的那份超大紅色『弱點數量總覽數』)
D. The "Defect Density" and the "Remediation Rate" (the speed and percentage of critical vulnerabilities that are actually fixed/patched after being discovered in testing). (向長官展示『瑕疵密度 Defect Density (這支專案每一千行被測出幾個弱點的乾淨程度體質)』，以及最重要的神聖雙指標—『追蹤防堵癒合率 Remediation Rate (當被那些雷達掃出那些最致命的紅燈後，我們有多快，以及有多高的百分比，那些洞是真的【已經被修補且根除成功癒合結案】的！這表現了資安的真實執行成效)』)

*   **正確答案 / Correct Answer：D**
*   **[解析邏輯]**
    *   **為何 D 是最佳選擇：** 高階主管與整個 Security 團隊在乎的不是你買的雷達或是掃描儀可以掃出多少滿坑滿谷的垃圾蟲子，又或是你每天能掃多快。最關鍵的量測基準在於：**找出了洞之後，我們這個無敵拖延的團隊能不能快速且確實把那些血淋淋的大洞都補起來 (Fixing & Mitigation)**。因此 **修復率/癒合率 (Remediation Rate)** 跟 **修補的空窗生存期間 (Time to Fix)** 是最棒的管理數據。另外一個 **瑕疵密度 (Defect Density)** 測量的是我們家那些昂貴工程師寫出來的軟體每萬行程式碼所自帶的蟲孔與漏洞是不是這數目有沒有逐年降低，這也表示工程師教育訓練奏效且安全左移文化成形了。只有 D 所陳述的，才是能證明團隊防禦力量正在實質成長升級的硬核績效報告。
    *   **為何 A 是干擾項：** 腳本數量是單純衡量 QA 寫測試人員多努力工作打卡出勤 (Output)，不能反映整個系統到底有沒有變更安全 (Outcome)。這是一個毫無績效參考的虛浮數字 (Vanity Metric)。
    *   **為何 B 與 C 是干擾項：** B 是硬體 CPU 效能數字而不是安防效效數字。C 更是一場災難，只跟長官報含有大量「雜音與誤判(不實的警報)」的「總掃出來數字數」，這除了嚇死長官外無助於他理解資安管理進度。

#### **16. Before initiating a Penetration Test on a critical, live production database server, the Lead Tester and the enterprise CISO must sign a formalized document. This document strictly defines what IP addresses the testers can attack, specifies that they cannot perform Denial of Service (DoS) attacks, and dictates what hours they are permitted to test. What is the universally recognized term for this critical legal and operational document?**
**(在對企業極為關鍵的真實實機營運上線資料庫（Live Production）進行破門拿根的「這場盛大嚴肅的真刀真槍滲透戰鬥測驗」打響鳴槍信號彈之【前】！！帶槍測試的紅隊傭兵教頭跟這間企業握有最高生殺大權的保衛將軍 CISO 雙方【絕對必須】在桌上畫押且嚴格共同敲定並簽下那張合約。這薄薄幾張紙如履冰般界定：「你只能攻打這些清單上的 IP；這段過程你絕對不可拔掉氧氣筒進行死亡癱瘓式拒絕服務 (DoS)！然後你每天只准在夜深人靜晚上十一點之後開打！」 這張在全球軟銀與軍工測試圈共通被認定是法律保命與作業絕對規矩教條文件的術語全名叫什麼？)**
A. The Non-Disclosure Agreement (NDA) (守口如瓶秘密未明不披露簽定條款)
B. The Rules of Engagement (RoE) (火線交鋒/接戰規則與交戰疆域規範指引法則)
C. The End-User License Agreement (EULA) (買電腦按下一步最終用戶授權許可狀)
D. The Security Level Agreement (SLA) (安保護航服務層次保障要求合約)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 和本領域第 8 題互相呼應。在對真實商管伺服器甚至是金融銀行進行合法 hacking (駭客攻防) 時。因為滲透的本質是在刀口上跳舞操作，一個微弱的小參數指令失誤就能讓整個集團當下來並倒賠幾個億。為了畫出誰該背鍋的界線，一份詳載了「哪些大門你可以踹、幾點你可以開槍打哪裡、然後當發現金庫大開時你要做哪些不許幹哪些的聯絡手段」的手冊就是這整個滲透作業流程的心臟。業界統稱為 **接戰規則或交戰守則 (Rules of Engagement, RoE)**。
    *   **為何 A 是干擾項：** NDA 雙方都會簽而且是最基本法律要求。代表滲透黑客測試完拿了帳本出去如果講出去大嘴巴他就違法並吃官司。但保障「戰鬥行為不出亂子打死人」的戰略指揮條文那是 RoE。
    *   **為何 D 是干擾項：** SLA (Service Level Agreement) 是雲端機房租賃的停機求償率保證條款（例如保障一個月開機率維持 4 個 9，不然退訂閱費）。與主動出擊攻防測試戰略沒半個子關係。
    *   **為何 C 是干擾項：** 那是你裝微軟等軟體遊戲時你閉著眼睛按了一路無聊 Agree 到頂端的無效廢紙文。

#### **17. A team is building an e-commerce checkout flow. The security engineer writes a test script that intentionally tries to add a negative quantity of items to the cart (`quantity = -5`) to see if the total price decreases, resulting in the server owing the user money. This type of testing, which deliberately inputs invalid or unexpected data to verify the system handles errors securely and does not enter a failed state, is formally known as what?**
**(研發大軍正日以繼夜瘋狂擴編打造一條要對付雙十一檔期的全流沙結算購物車結帳大戰線。一位刁鑽狡猾的安全測評員獨自寫下了一個怪異惡毒的自動測試：這個測試專吃飽撐著，只『刻意向購買這商品選項上倒灌瘋填一個不存在的負數 (我要買 負 5 杯珍奶！！！)』。看看這個愚蠢的系統會不會被這負數數學給繞進去！從而算出這個結餘總價不只沒有增加，竟還減少讓這台伺服器銀行帳戶直接轉回頭，荒謬欠了這個天才客戶極其鉅款！這門偉大地從側面打擊偏鋒！「不送正確無事太平的乖乖資料！就專門挑送一堆『死傷錯亂、或是超常極限違歸變態怪異封包』要去看系統這死物能不能穩健、聰明完美地挺住這惡意打擊並且漂亮攔截而不會死機進入不可回復之崩潰悲慘失誤絕境」！這一派絕學學術被命名為什麼？)**
A. Positive Path Testing / "Happy Path" Testing (正向測試 / 開心美好的陽光康莊大道測試法)
B. Negative Testing / Abuse Case Testing (負面測試 / 妄想與濫用顛覆試驗法)
C. Static Application Security Testing (SAST) (靜態枯燥應用程式原始無聊分析檢驗大法)
D. Code Review Walking (白頭翁走踏過程式原始碼長征檢閱法)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 當程式設計師在測試他的軟體時，他們通常只關注 **快樂路徑 (Happy Path/Positive Testing)**，意思是「如果有一個乖客戶順著指引輸入數字 5 並拿出信用卡給錢。太棒了，他成功拿到了一張訂單了！收工完成結案！」。這是傳統 QA 做的事。但站在資訊安全與破壞領域，安全分析工程師最深愛也投入最多歲月的，是去專鑽那些「工程師忘了想像的路徑死角」，進行 **負向測試 (Negative Testing; Misuse/Abuse Test)**。也就是故意打破常規，輸入亂碼、負數、空白、超長字串，這考驗著系統（及開發者所設想的邊界條件 Boundary Check、例外異常修補處理 Error Handling 還有各種資安機制。因為真實面對網際世界的環境，只有少量的使用者是善良的，你得預想你的客戶都是駭客。
    *   **為何 A 是干擾項：** A 剛提了，是完全與之相反的光明面測試。
    *   **為何 C 與 D 是干擾項：** 代碼閱讀以及 SAST 都需要人工一頁一頁去看著這些天書，這個題目的情境是活跳跳的在對那台主機做打怪。所以他們是截然不同光譜的技術。
