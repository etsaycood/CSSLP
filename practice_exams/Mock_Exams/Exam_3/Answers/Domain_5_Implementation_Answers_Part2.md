# 第三套全真模擬試題 (Exam 3) - 答案與詳解本
## 領域 5：安全的軟體實作 (Secure Software Implementation) (18題) - Part 2 (Q10-Q18)

---

#### **10. An application relies heavily on third-party, open-source libraries (e.g., npm packages, Python PIP modules) to accelerate development. The security team realizes they have absolutely no visibility into the thousands of transitive dependencies these libraries drag into their final build, and whether any of those hidden libraries contain known, documented CVE vulnerabilities (like the Log4j disaster). What specific category of automated DevSecOps tooling must be implemented in the CI/CD pipeline to analyze the `package.json` and flag vulnerable third-party components?**
**(一家急功近利的工坊，為了貪圖神速造車 (accelerate development)，他們打造出來的馬車，幾乎全車上下所有零件，都是從路邊那種不用錢的開源跳蚤市場裡撿來的 (third-party, open-source libraries)。負責把關車輛安全的老師傅，在檢查車廂時突然脊背發涼！他發現他們雖然只買了三個大零件回去組裝，但那三個大零件裡面，卻猶如俄羅斯娃娃般，還暗藏著幾萬個連原設計者都不認識的【來路不明之阿米巴原蟲般極度微小、會自動寄生的『幽靈傳染性重重疊加依賴小木塊 (thousands of transitive dependencies)』】！最可怕的是，沒人知道這些隨便抓來的小木塊裡面，會不會藏了一隻早在通緝榜上大名鼎鼎、能讓整台馬車瞬間爆炸解體 (like the Log4j disaster) 的【天下大劇毒 CVE 蠕蟲 (known vulnerabilities)】！請問，為了拯救這場看不到底的災難，防禦大隊必須在汽車出廠的最後一道掃描站 (CI/CD pipeline) 上，強制裝備哪一種【專門能拿著顯微鏡去拆解『包裹成分配方表 (package.json)』、甚至專門抓出那躲在最深處發霉零件】的自動化驗屍神器？)**
A. Static Application Security Testing (SAST) (SAST 只是用來檢查【你自己家工程師寫的】那堆字串原始碼有沒有白痴錯誤，它不擅長去解剖包起來的外部別人家包裹 CVE)
B. Dynamic Application Security Testing (DAST) (DAST 只是模擬一個亂踹門的駭客，去打活著的網站，拿來抓外部開源零件弱點是大砲打小鳥且非常不準)
C. Software Composition Analysis (SCA) (這就是以火眼金睛名震古今、專治供應鏈與開源垃圾包裹之最偉大顯微鏡大殺器：【『軟體成分大起底 / 原物料死神透視分析神器 (Software Composition Analysis, SCA)』】！)
D. Interactive Application Security Testing (IAST) (這只是在軟體裡面裝個竊聽器的進階測試儀器)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「軟體成分分析 (Software Composition Analysis, SCA)」** 是專門為了解決這題描述的痛點而生的 DevSecOps 核心工具。
    *   **痛點描述 (開源相依性與漏洞)：** 現代軟體有 80% 的程式碼是從 npm, maven, pip 這些公開庫拉進來的。你只 `npm install react`，但 React 背後可能又相依了別人寫的 50 個小模組 (Transitive Dependencies)。如果這 50 個小模組裡只要有一個爆發了像 "Log4j" 那樣名留青史的百年一次 CVE 漏洞，你的軟體在不知情的情況下就已經在全裸狂奔了。
    *   **SCA 的專武能力：** SCA 工具 (如 Snyk, Black Duck, 或是 GitHub Dependabot) 會掃描你的 `package.json` 或 `pom.xml` (BOM 表/配方表)，把它們跟全球 CVE 漏洞大資料庫比對。不只是第一層包裹，SCA 能深入掃描第五層、第六層的「相依性的相依性」。並告訴開發者："你撿來的那個輪胎裡面的螺絲釘生鏽了，請升級到 v2.1 版"。這是防禦供應鏈攻擊的最強防盾。

#### **11. A developer implements a global exception handling block (a `try-catch` statement) around the main database execution module. When a database error occurs, the code logs the error and displays the following raw message directly to the end-user's web browser: `Error 500: Database connection failed. ODBC Driver 17 for SQL Server on Server 10.0.1.55. Table 'Customers' column 'credit_card' not found in statement 'SELECT credit_card FROM Customers'.` Why is this specific error handling implementation extremely dangerous?**
**(一名老實巴交的防禦工程師，在幫公司打造最核心的【皇家後宮大金庫連通結界 (database execution module)】時，雖然他在外面套了一層名為『全面捕捉失誤崩潰大氣墊 (global exception handling block / try-catch)』的安全防護網。可是，當裡面真的發生了火燒車爆炸的嚴重意外時 (database error)！這個老實人，居然！把當時金庫管家被炸得滿臉血、臨死前口裡吐出來的那句鉅細靡遺、包含著無數國家最高機密的【底層靈魂赤裸原始吶喊 (raw message)】，像報紙一樣毫不遮掩地，直接投影在城外每個路人甲的巨大電視牆上 (displays directly to the end-user's web browser)。這路人看著電視牆上活生生寫著：『`第 500 號大死當：我們連不上金庫啦！因為我們是用 ODBC 驅動 17 版、那台裝載了微軟大金磚 SQL Server、且就座落在我們內網絕秘 IP 地址【10.0.1.55】的資料庫伺服器！而且你剛呼叫的【顧客的信用卡卡號 (Table Customers column credit_card)】居然從那條【SELECT credit_card FROM Customers】的神聖搜刮指令裡面人間蒸發找不到了！`』請問這位老實人的這種寫法，為什麼是一種足以讓他被抓去槍斃一百次的極度危險致命架構？)**
A. Error 500 automatically encrypts the database. (這瞎扯說當機代碼可以幫忙鎖門防禦的笑話)
B. It implements "Fail Open," which shuts down the server. (出錯關閉是安全的失效安全，這不是把密碼攤在陽光下的問題)
C. It constitutes severe Information Disclosure. Displaying verbose, detailed technical stack traces and internal architecture details to the end-user provides a perfect blueprint for an attacker to launch targeted exploits. (這就是讓他被槍斃的重罪起訴書：【公然且無知地導致一場毀城級別的『國家大機密全面洩漏慘案』 (Information Disclosure)！】。你這白痴工程師，居然把這座金庫底層到底是用什麼外星廠牌牌子的保險箱 (stack traces)、保險箱精確擺放在地球上的絕對內網 GPS 經緯度座標 (internal IP architecture details)、甚至連裡面裝黃金的那格抽屜具體叫什麼狗屁名字！全部一清二楚地全裸公布給全世界看。這簡直是雙手奉上一張畫好紅心標靶的完美藏寶圖 (perfect blueprint)，邀請駭客拿著狙擊槍來精準屠城 (targeted exploits)！)
D. `try-catch` blocks are deprecated in modern programming languages. (`try-catch` 是所有語言防禦的主心骨，哪來的被淘汰說法)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是資安實作中最常見低級錯誤之：**「不當的錯誤處理 (Improper Error Handling) / 導致資訊洩漏 (Information Disclosure/Leakage)」**。
    *   **駭客最愛的禮物：** 在漏洞挖掘 (Reconnaissance) 階段，駭客如果隨便送些怪字元，就能讓網頁吐出 `Stack Trace` 或資料庫錯誤訊息。這對駭客來說是極品的情報。
    *   題目描述的錯誤訊息，等於大放送了：
        1.  後端資料庫種類 (SQL Server)。
        2.  驅動程式版本 (ODBC Driver 17 - 駭客可以查有沒有已知 CVE 弱點)。
        3.  內部網路真實 IP (10.0.1.55 - 有利 Server-Side Request Forgery 攻擊)。
        4.  資料表名稱 (Customers) 和欄位名稱 (credit_card) (直接給了盲注 SQL Injection 所需的字典)。
    *   **正確實作方式：** Catch 到 Exception 後。把這些詳細報錯 `Logger.error(...)` 寫進系統內部的日誌檔供工程師除錯，然後對瀏覽器顯示一個**簡單、籠統的、絕不包含技術細節**的友好訊息 (例如："抱歉，系統遭遇意外錯誤，請聯絡開發團隊，錯誤追蹤碼：1A8F" )。

#### **12. A web application features a "Contact Us" form where users can submit feedback. To prevent automated botnets from spamming the database with millions of fake submissions, the developer implements a completely hidden HTML field `<input type="hidden" name="is_bot" value="false">`. The backend server only processes the form if `is_bot` remains "false". Why is this anti-automation implementation completely ineffective against an actual attacker?**
**(一家小商店的網頁裡，做了一個名為『百姓抱怨信箱 (Contact Us form)』的樹洞。為了防止外面那些由幾百萬隻無腦殭屍老鼠組成的網軍 (botnets)，一股腦兒把幾萬公斤的垃圾塞爆這個樹洞 (spamming the database with fake submissions)。這家店的天才掃地僧，發明了一招他覺得連玉皇大帝都看不穿的『終極防禦結界 (anti-automation implementation)』：除了給客人寫字的紙條外，他在那張網頁的最深處，藏了一張對客人這輩子【永遠隱形看不見的符咒 (hidden HTML field)】，上面寫著：『`<input type="hidden" name="我不是老鼠(is_bot)" value="我發誓我不是(false)">`』。然後系統只要看到這隻飛鴿傳書回到大本營時，如果這張紙條上面還乖乖寫著 'false'，掃地僧就深信這一定是活生生的良民寫的，然後笑嘻嘻地把抱怨信收進皇宮 (processes the form)。請問天真的掃地僧，這套【隱身防禦法】，在真正的惡魔駭客大軍面前，為何連這張紙的厚度都不如，只是一場徹頭徹尾的滑稽笑話？)**
A. Hidden fields cannot hold boolean values like "false". (胡說連個字串 false 都不行裝那是因為程式寫爛不是機制的問題)
B. It relies on Client-Side Controls. An attacker using a proxy (like Burp Suite) or a simple script can effortlessly view, bypass, and manipulate anything sent from the client-side browser, rendering the hidden field useless. (這就是這場鬧劇最可恥的笑柄底層邏輯：【這白癡掃地僧居然把判斷生死的大權，下放並寄託在這個名為『客戶端瀏覽器信任大防線 (Client-Side Controls) 的超級紙糊盾牌上】！這老天爺般的常識他居然不懂：駭客可是擁有『攔截器與神明手術刀大 Proxy (例如傳說中的 Burp Suite)』的超能力啊！駭客要派出萬千鼠輩時，這張隱形紙條在駭客的顯微鏡下根本無所遁形 (effortlessly view)，駭客只要用腳趾頭在半空中寫個腳本小程式，把幾百萬封垃圾信件裡全都無腦強行硬掛上『我不是老鼠(false)』這幾個字 (manipulate anything)，掃地僧這招就直接被破得連灰都不剩 (rendering it useless)！』)
C. The database will reject the "hidden" attribute. (這種資料庫不認識網頁 HTML 標籤的法盲論點)
D. The developer should have used `<input type="password">` instead. (用看不到小黑點的密碼欄位當防禦根本就是更白癡的做法，對防禦老鼠大軍毫無幫助)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「不可信任客戶端輸入 (Never trust client-side controls/validation)」**。
    *   這是 Web 安全實作的核心教條。HTML 表單裡的 `hidden` 欄位、或是前端 JavaScript 寫的驗證邏輯，其設計目的是為了 "方便與優化使用者體驗"，【絕對不是】為了安全防禦。
    *   **駭客視角：** 駭客根本不會用普通的滑鼠跟 Chrome 瀏覽器操作你的網頁，所以這欄位隱不隱藏對駭客毫無意義。駭客使用腳本 (Python requests) 或是本機 Proxy (Burp Suite)。他在攔截封包時，所有要送往伺服器的欄位 (包含 hidden) 都會直接變成普通的文字檔 `name=John&is_bot=false`。駭客寫個迴圈打一萬次 API，每次都夾帶著 `is_bot=false`，伺服器就會把它當好人全部收進去。
    *   **防堵自動化的正確解法：** 必須使用伺服器端驗證機制，例如加入 CAPTCHA (如 reCAPTCHA)、Rate Limiting (限流)、或行為分析 (WAF) 功能。

#### **13. A C development team is rewriting a legacy application. The security architect strictly bans the use of "dangerous" legacy functions such as `gets()`, `sprintf()`, and `strcat()`. What is the primary, overarching reason for permanently banning these specific standard C library functions in modern secure coding?**
**(一支渾身長滿青苔的古老 C 語言修繕大隊，正準備翻修一座百年前用古文字寫下的龐大城牆 (legacy application)。只見大都督拿著沾著鮮血的硃砂筆，冷血地劃掉了一整排在老工人眼裡最親切好用的祖傳修磚工具名單：他當場下達這輩子誰敢用都會被抄家滅族的禁令！【全面封殺並銷毀那名為 `霸道吸收大法(gets())`、`蠻幹印墨連環指(sprintf())`、以及 `無腦黏土神功(strcat())` 等三大上古邪術大招 (strictly bans dangerous legacy functions)】！請問，在現代那講求滴水不漏的『現代終極防禦大陣 (modern secure coding)』中。大都督之所以對這幾套歷史悠久、阿公年代就傳下來的 C 語言老傢伙們趕盡殺絕，那是因為這幾招老古董的靈魂深處，染上了哪一種毀天滅地的終極原罪 (overarching reason)？)**
A. They natively lack any capability to define or enforce internal buffer boundary limits, making them inherently and historically the primary cause of catastrophic Buffer Overflow vulnerabilities. (他們的原罪，就是這些老傢伙在盤古開天被創造出來時，【根本就他媽的沒有加上『去拿尺量一下記憶體盒子到底有多大、裝不裝得下 (lack capability to enforce internal buffer boundary limits)』的煞車功能】啊！他們只要一被發動，就像頭眼瞎的狂奔野牛，閉著眼睛死命把你拿到的幾千萬字串往一個可能只有十塊錢大小的杯子裡硬塞，直到把記憶體給活生生撐爆炸出一地屍骨！這就是近代歷史上所有那些能讓帝國瞬間崩潰的【『緩衝區終極溢位大爆炸浩劫 (catastrophic Buffer Overflow vulnerabilities)』的最主要元兇跟千古罪人】！)
B. They are too slow and cause performance bottlenecks. (他們跑得太快了，才不是因為他們跑的慢被淘汰)
C. They require an active internet connection to compile. (這年代連這個都不用的 C 語言當然不用連線編譯的胡言亂語)
D. They automatically execute SQL queries in the background. (這幾招都在記憶體裡面打轉拿陣列接字串，扯不到後山撈資料的黑魔法)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 這些古老的 C 標準函式庫函數 (如 `gets`, `strcpy`, `strcat`, `sprintf`) 惡名昭彰，被公認為**「危險函數 (Dangerous Functions)」**，幾乎在所有的 Secure Coding Guidelines (如 CERT C, MISRA C) 裡都被列為絕對禁用。
    *   **致命缺陷 (Unbounded String Operations)：** 這些函數在運作時，只認結尾的空字元 `\0` (Null-Terminator)。它們完全不理會目標記憶體區塊 (Buffer) 的長度限制 (Bound checking/Size Check)。只要攻擊者餵給這些函數足夠長的字串，這些失控的野馬就會衝出原本的記憶體邊界，覆寫掉旁邊的執行指令記憶體，造成名存千古的**核心殺手級漏洞：緩衝區溢位 (Buffer Overflow)** 並且被引導至遠端程式碼執行 (RCE)。
    *   **正確解法：** 在現代 C 語言開發中，必須強制改用它們的「安全版本」，也就是具有 "Boundary-Checked (邊界檢查)" 能力的函數，例如 `fgets()`, `strncpy()`, `strncat()`, `snprintf()` 等 (字尾有 `n`，代表傳入最大 Size 限制)。

#### **14. A highly secure B2B financial portal allows specific enterprise partners to upload XML files containing bulk payment instructions. A security researcher discovers that if they upload a specially crafted XML file containing a `<!ENTITY>` payload pointing to `file:///etc/passwd`, the server's backend XML parser actually reads the local password file from its own hard drive and embeds the contents directly into the API response sent back to the researcher. What specific vulnerability did the researcher exploit?**
**(一家號稱滴水不漏、專門服務大總裁跨國洗錢的帝國匯款門戶網站 (highly secure B2B financial portal)。為了讓各大財閥能夠一次倒出幾萬筆的轉帳清單，這座大門開放了一個能讓財閥上傳【長得像古老樹枝狀符號文字的巨大檔案 (XML files)】的大洞口。結果，某天傍晚，一名笑著在門外溜達的白帽刺客，發現了能讓這座皇城一秒倒閉的世紀大天坑！他偷偷塞了一份外面包裝得跟匯款單一模一樣、但裡面卻用劇毒墨水畫上了一道名為『實體召喚惡毒邪門大咒語 (<!ENTITY> payload)』的恐怖 XML 巫毒草人！這咒語上面寫著：`把這台大伺服器心臟最深處那個名叫【/etc/passwd 國家級絕密高官帳號名冊 (password file)】的檔案給我念出來！`！結果！這座帝國那群自以為是的『後端 XML 解讀審查官 (XML parser)』，居然像中邪般瞎了狗眼，對這個外部的巫毒咒語百依百順，當場衝進自己的保險庫深處，活生生拔出那份名冊！而且還把它完完整整地複印了一份，夾在那原本要送回給刺客的收據回聲大聲公裡面，大喇喇地交給了刺客 (embeds contents directly into API response)！請問，這名刺客所利用的這手，被那部名震天下的 XML 巫毒之書記載為哪一招足以摧城拔寨的死穴大漏洞？)**
A. XML External Entity (XXE) Injection (這就是這場中邪事件的禍首主嫌、以操控實體符咒來召喚並榨乾系統內臟底細的：【『XML 外部實體極限木馬大注射法術 (XML External Entity (XXE) Injection)』】！)
B. Cross-Site Scripting (XSS) (這只是小混混在別人網頁牆上亂寫 javascript 騙普通路客，不是這種深海惡魔的攻擊維度)
C. SQL Injection (這是去別人的關聯式資料庫裡偷偷撈錢跟改密碼的大把戲，跟那幾份標籤字串 (XML) 無關)
D. Denial of Service (DoS) (這是把大門給炸垮不要給人家進去的玉石俱焚，這是去偷密碼名冊不是用來搞破壞關機)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **「XML 外部實體注入 (XXE, XML External Entity)」** 是專挑那些用來解析 XML 檔案的後端程式下手的毀滅性攻擊。
    *   **漏洞原理：** 很多 Web 應用程式 (如 SOAP API, SAML) 會接收外部使用者傳來的 XML 文件。XML 規範裡有一個古老又危險的奇妙功能叫 `Entity (實體)`，它允許工程師在 XML 檔案最開頭 (DTD 宣告區) 定義一個代數 (例如 `<!ENTITY my_var SYSTEM "file:///etc/passwd">`)。這句話的意思是："這台伺服器的 XML 解析器老兄，當你在下面看到 `&my_var;` 這個代號時，請你親自跑到你這台伺服器本機的磁碟機裡，打開 `/etc/passwd` 這個檔案，然後把裡面的字【一字不漏地塞進這個變數裡面】替代掉它"。
    *   如果程式設計師在實作 XML Parser 時，沒有強制把它設定為「關閉解析外部實體 (Disable resolving external entities)」，伺服器真的就會乖乖聽駭客的話，把系統內部檔案 (或是透過 SSRF 攻擊攻擊內部網路 `http://192.168.1.1`) 的內容全部印出來送還給駭客，造成嚴重的資料外洩。

#### **15. When writing code to handle multi-threaded processing in a real-time trading application, two separate execution threads simultaneously attempt to access and modify the exact same shared memory variable representing an account balance, without using any synchronization locks or mutexes. Depending on the exact millisecond timing of which thread finishes last, the final account balance can be incorrectly corrupted. What is the fundamental security engineering term for this specific type of concurrency flaw?**
**(在寫程式打造那猶如每秒鐘會有千刀萬剮在半空中飛舞交錯的『華爾街即時生死決戰股票大印鈔機 (real-time trading application)』時，一群猴子工程師寫出了一段極其恐怖的『多重影分身平行動力大結界 (multi-threaded processing)』！在某次運作的瞬間，這段破結界居然！同時噴出了兩隻分身小黑鬼 (two separate execution threads)。這兩隻小黑鬼像瘋狗一樣，他們【同時、且不商量地、猶如餓虎撲羊般，撲向了同一格裝著客人生死存亡餘額數字的神聖保險箱共同記憶體神龕 (simultaneously attempt to access and modify exact same memory variable)】裡面去亂搬錢！而且最要命的是，那群猴子居然忘記在這格抽屜上，鎖上能逼這兩隻分身排隊不准打架的『大排長龍同步大鎖或是紅綠燈 (without using any synchronization locks or mutexes)』！結果這兩隻分身互相踩來踩去，這格抽屜裡的錢，會因為哪隻分身在【千分之一秒的毫髮之差 (exact millisecond timing) 間，誰的手腳慢半拍最後才把抽屜推進去，導致前面那隻分身的計算結果直接被無情覆寫輾壓而變成靈異算術爛帳 (final account balance corrupted)！】。請問，在程式語言防禦工程的生死薄上，這等猶如在獨木橋上同時發動瘋狂踩踏事件的並行時間差大黑洞，稱之為何？)**
A. A Logic Bomb (這是工程師心生歹念埋下等到九月九號引爆的倒數死神計時器，這不是因為並行的問題出包的)
B. A Race Condition (specifically, a Time-of-Check to Time-of-Use [TOCTOU] or concurrency flaw) (這就是以極度難抓出蟲子而惡名昭彰天下的世紀懸案：【極限競速大失控 / 或時間差競態大崩潰 (Race Condition)！這更是平行世界併發症漏洞群組裡那最致命的『查完馬上被搶的空窗期大盜竊 (Time-of-Check to Time-of-Use, TOCTOU)』！】！)
C. An Integer Underflow (那是計算機瘋狂倒退扣錢到破表變成數字環繞的無限加錢魔法)
D. A Buffer Over-read (那是你在照妖鏡前面超過鏡子範圍看到隔壁房間女孩子在洗澡的超界記憶體窺視)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「競爭條件 (Race Condition)」** 或是更普遍的 **「並行漏洞 (Concurrency Flaw)」**。
    *   在多執行緒 (Multi-threading) 程式碼中 (特別是 C++, Java, Go 等)，如果多個 Thread (執行緒) 同時存取一個位於 Heap 記憶體中的「共享變數 (Shared Resource/Variable)」，而且開發者沒有使用 Mutex (互斥鎖)、Semaphore、或是 Monitor/Synchronized 區塊來保護這個變更動作。
    *   **銀行餘額慘案：** 變數原來是 100 塊。
        *   Thread A 讀取 100，準備加 50。
        *   同時，Thread B 也讀取 100，準備加 20。
        *   Thread A 算好 150，寫回。
        *   Thread B (慢了 1 毫秒) 算好 120，寫回。
        *   **結果：** 最後帳戶變成 120 塊，A 加進去的 50 塊就憑空消失被覆寫了 (這就是競爭條件導致的狀態混亂)。
    *   其中一種惡劣的利用此並發漏洞的手法，就被稱為 **TOCTOU (檢查與使用之間的時間差)**，常被駭客用來在防毒軟體檢查完檔案，剛要執行前的那百萬分之一秒，把好檔案直接抽換成病毒檔。

#### **16. A developer is building a banking website. They want to ensure that if a user logs into their bank account on `Tab A`, and then opens a malicious hacker's website on `Tab B`, the hacker's website cannot secretly trigger a background HTTP POST request to the bank (e.g., `POST /transfer?amount=1000`) that effectively leverages the user's active login cookie to steal money without the user's knowledge. What specific defensive mechanism MUST the developer implement to bind the specific action explicitly to an intentional user click on the legitimate bank page?**
**(一名老僧正在防衛一座有著金銅大門的【銀行跨網匯款大網站 (banking website)】。大總管下達了死命令要防止這種被俗稱『大黑吃黑連體嬰偷錢法』的現象：萬一哪天我們有一個渾蛋大商人，他好死不死在電腦瀏覽器的『第一區視窗 (Tab A)』裡面，才剛驗明正身、通過瞳孔掃描登入了我們家的超級大金庫！這傢伙居然手癢，又在隔壁的『第二區視窗 (Tab B)』裡面，去點到一個由無雙大魔王架設的萬惡之源釣魚網站。這時那家魔王網站居然不講武德！它居然躲在地下暗處，【背地裡默默發出一張偽造成第一區大商人的轉帳大命令 (trigger a background POST request \/transfer?amount=1000)！且它居然還像寄生蟲一樣，卑鄙無恥地直接掛靠並且盜用了那張此時此刻依然閃耀著金光、插在第一區視窗上的無敵登入身分通關憑證大金牌 (leverages user's active login cookie) 取代大商人本人把幾萬塊瞬間偷走】！請問這名防衛老僧，要祭出哪一套法寶，才能死死鎖住這道手續，保證【只要這筆轉帳號令不是那傢伙這隻手、有意識並且真的在這座金庫門口按下去的 (bind action exactly to intentional user click on legitimate page)】，我就絕對不買帳！？)**
A. Implement an Anti-CSRF (Cross-Site Request Forgery) Token (a unique, unpredictable, synchronizer token) that must be submitted with every state-changing request. (這就是用來鎮壓這種跨界大偷襲神威外掛的唯一法器：【在每張轉帳申請表裡，都必須發放並打上一種『防禦跨站請求之超級偽造防禦印（Anti-CSRF Token/同步大金丹）』！這顆金丹必須擁有每一次都不一樣、連佛祖都算不出來的隨機亂舞數字，如果送來的提款申請書裡連這個金丹都掏不出來，一律轟出去當狗打】！)
B. Utilize a Web Application Firewall (WAF) to block IP addresses from `Tab B`. (胡扯瞎掰 WAF 無法去防阻使用者的視窗 IP 那是瀏覽器端的東西，這個不是靠封鎖外部 IP 就可以搞定的)
C. Encrypt the user's password using AES-GCM. (這時候密碼早就輸入成功幾萬年了，這跟後續的防偽造按鈕保護毫無關聯)
D. Require the user to use an Incognito/Private Browsing window. (那是防老婆用的不是這樣防大駭客黑水鬼攻擊的好防護)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 這題精準描述了 **跨站請求偽造 (Cross-Site Request Forgery, CSRF/XSRF)** 的經典攻擊情境。
    *   **CSRF 攻擊原理：** 它的恐怖之處在於，駭客**根本不用偷你的密碼或 Cookie**。駭客只是利用了瀏覽器一個預設的很蠢的特性：「當瀏覽器對 `bank.com` 發出任何網頁請求時 (即使這個請求是從隔壁另一個惡意分頁 `evil.com` 的腳本偷偷射出來的)，瀏覽器都會很雞婆地把 `bank.com` 存在這台電腦裡有效的登入 Cookie，自動貼掛在這個請求封包上送過去」。所以銀行的伺服器看到這包請求，會以為是你本人親自按下的。
    *   **CSRF Token 的防禦魔法：** 工程師在銀行這個原廠網頁裡面的 "轉帳表單" 裡面，埋入一組**隱藏、隨機、不可預測、且跟這個人綁定的字串 (Anti-CSRF Token)**。當你按下轉帳，除了 Cookie，這串 Token 也必須一起送到伺服器驗證。
    *   **為什麼可以防住駭客：** 當駭客在隔壁頁面 (Tab B) 偷偷送出轉帳請求時，他可以騙瀏覽器掛上你的 Cookie，但他**絕對拿不到 (或猜不到) 存在 Tab A 網頁裡面那組隨機產生的 CSRF Token** (因為瀏覽器的同源政策 Same-Origin Policy 會擋住跨站讀取)。所以這個暗殺包裹送到銀行，銀行發現 "有 Cookie 但沒有對應的 Token"，就會直接當作偽造品退件，完美保護了存款。

#### **17. A programmer is calculating the exact exact memory required to store an array of user inputs. They use the following C logic: `short int total_size = user_count * fixed_item_size;`. However, if a malicious user provides an astronomically large number for `user_count`, the multiplication result exceeds the maximum positive value a 16-bit `short int` (32,767) can hold. The value unexpectedly wraps around to a small negative number, causing the system to allocate far too little memory, subsequently leading to a massive buffer overflow when it tries to write the data. What specific type of software vulnerability is this?**
**(一名精算師正拿著算盤，計算要買多大的一個記憶體玻璃大倉庫，才裝得下外面那群排隊幾千人的『客人行李陣列包裹 (array of user inputs)』。這個精算師在他的 C 古代編譯寶典上，寫下了這樣的一句話：『`倉庫需要的大位元組 (這只是一個能塞得下 3 萬多數字的小算盤 short int) = 客人數目 * 每個人行李箱的大小`』。但是，就在這時候，一個笑得很邪惡的駭客惡魔突然跑了進來！他居然在『客人的數目』上，直接填上了一個像天文數字般長度、大到能夠把天際線給捅出一個窟窿的超大無解巨無霸數字 (astronomically large number)！這時，可悲的數學發生了毀滅性的核子突變：因為那把破爛的 16-bits 小算盤，它原本這輩子最高只能承受跑到正整數 32,767 這微弱的巔峰 (maximum positive value)。這兩團猛烈的數字像核彈般相撞乘起來後，居然直接把小算盤的鐵皮給撐破了！原本該是一個巨大正值的倉庫容量，居然【在記憶體輪盤物理法則的反轉下，莫名其妙地在時空中旋轉了半圈，變成了一個極端微小且致命的負數狗洞大小 (wraps around to a small negative number)】！系統看了這個微小的負數，只給駭客分配了一個像老鼠洞這麼丁點大的記憶體皮箱 (allocate far too little memory)。接下來，當那滿天星斗的幾萬公斤行李全部狂砸下來想塞進鼠洞時，當場引爆了毀滅天地的浩劫 (massive buffer overflow)！請問！這種猶如數學輪盤倒轉破洞大失控的妖孽軟體實作神級漏洞！道號名稱為何？)**
A. Format String Vulnerability (那是 `printf` 把格式符號印錯印進心臟去撈記憶體深處秘密的透視邪術)
B. Integer Overflow (or Arithmetic Wrap-around) (這就是被世人奉上神台的絕對數學反轉之怒：【『整數溢位算術環繞大爆炸大破滅 (Integer Overflow / Arithmetic Wrap-around)』！】)
C. Null Pointer Dereference (那是指著一塊空氣還要用一輩子想要叫出錢包的絕望當機指引空標破滅)
D. Cross-Site Scripting (XSS) (這只是騙你按下去以後出現幾行網頁 JavaScript 不痛不癢的小木馬彈跳)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是一道非常經典的 C/C++ 等底層語言的 **「整數溢位 (Integer Overflow)」** 漏洞情境。
    *   **漏洞原理 (Arithmetic Wrap-around 環繞)：** 在電腦底層的二進位世界裡，一個 16位元帶號整數 (Signed Short Int)，能代表的分數區間是 `-32,768 到 +32,767`。
    *   當運算 `20,000 * 2` 時，答案 `40,000` 超過了 `32,767` 的極限。在二進位加法器裡，最前面的正負號 Bit 被進位改變了 (從 0 變 1)，於是這個數字會像汽車里程表破表一樣直接 "環繞 (Wrap Around)"，變成一個負數 (例如變成 `-25536`)。
    *   **災難鏈條 (Integer Overflow 導致 Buffer Overflow)：**
        1.  系統拿到這個不可思議的負數 (或一個極小的正數)，去向作業系統要記憶體 (例如 `malloc(-25536)`，在某些實作中會轉成一個極小的記憶體空間)。
        2.  但要被複製進去的行李 (User Inputs) 卻是真真實實的天文數字長度。
        3.  把巨大的資料塞進這個因為算數錯誤而縮水成老鼠洞的記憶體，最終就會觸發這題後半部所描述的致命 **「緩衝區溢位 (Buffer Overflow)」** 漏洞。這是許多系統被大破防的連環殺招。

#### **18. To adhere to the principle of "Defense in Depth" at the code level, a development team implements severe restrictions on what their application can do if it gets compromised. They configure their Java application server to run under a restricted service account that cannot read any files outside of its specific `/var/www/webapp/` directory, cannot execute shell commands, and cannot open network ports below 1024. Which foundational secure coding concept does this operating environment directly enforce?**
**(為了要向這世間的『如千層糕大蛋糕般一層層防護加碼之縱深防禦大道 (Defense in Depth)』致敬膜拜！在這座皇城地底的最深處，一群造物工程師對他們打造的超級『巨大神像 Java 法師程式塔 (Java application server)』，下了最嚴苛且最變態的血咒封印結界大規定 (severe restrictions)：這些造物主防著萬一某天這座法師塔不幸中邪被外星駭客木馬大將軍附身控制時的最後保命底牌 (if it gets compromised)！於是他們像對奴隸一樣，只剝削發放給這座龐大的法師塔一個最卑賤的乞丐版身分大護照 (run under a restricted service account)！條款裡死死規定：這尊看起來巨大的法師只要敢踏出它被圈養的那個狗窩小房間一步，企圖去伸手偷摸旁邊國王那名為 `/etc/` 之類的黃金保險庫文件檔案！天上的雷電就會立刻劈死它把它手腳斬斷 (cannot read files outside directory)！它嘴巴被戴上消音大狗嘴套，絕對無法發號施令叫下方的軍隊執行什麼砲彈打出去的大指令 (cannot execute shell commands)！最後，大魔王把城池下方那一整排裝潢豪華、編號從 1 號排到 1024 號的光鮮亮麗出城大門通道，全給焊死！只丟給這個法師一條走旁門左道的下九流破爛小窗戶讓它跟外界送信任務 (cannot open ports below 1024)。請問這群殘忍的造物主，這樣像對待恐怖份子般虐奪其生殺大權的作業環境架構大限制，正是無情且純粹地執行了哪一項如萬丈高樓平地起的深淵防禦法則真理？)**
A. Obfuscation (這是用來把自己的程式碼塗墨水假裝成火星文字然後騙那些看程式碼的老外，不過這沒法阻擋程式的實權能力)
B. Least Privilege (and Sandboxing/Jailing at the execution level) (這就是能夠保命延壽的那【最原始底層殘酷絕學：嚴格苛扣的『最小、最瘦的剝削極限小特權大天條 (Least Privilege)』啊！並同時將這支法師塔像被流放般關進死囚籠裡面的沙盒與監獄禁閉大牢房 (Sandboxing / Jailing)】的最完美展示防線！)
C. Open Design (這是把自己的機密機關大圖紙全部大公開宣揚也不怕別人攻打的最高浪漫情懷)
D. Economy of Mechanism (這是指防禦城牆少一點花俏的機關才不會卡頓故障越簡單越好越能防出洞口)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「最小特權 (Least Privilege)」** 在實作層面的極致體現。
    *   **縱深防禦與損害控制 (Damage Control)：** 我們必須假設程式碼「總有一天會有漏洞」。如果這個 Java 程式是用 `root` (最高管理員) 身分在執行，一旦被駭客透過前面提過的 RCE (Remote Code Execution) 漏洞打穿，駭客瞬間就能掌握整台 Linux 伺服器的全部生殺大權，這就是「遊戲結束」。
    *   **Sandboxing/Jailing 與特權限縮：** 為了解開這個死結，開發者跟系統管理員故意給這個 Java 程式建立了一個只能活動在特定資料夾 (`/var/www/webapp/`)，且沒有權限執行 `bash` 的底層作業系統服務帳號 (Service Account)。這就叫做把它關進「沙盒 (Sandbox)」。
    *   **防禦效果：** 就算駭客真的找到了天下無敵的 RCE 漏洞繞過了前面所有的防護，他打進去後也會絕望地發現：「這伺服器帳號根本沒有權限把木馬病毒寫到硬碟裡，也打不開 port 連外」！駭客的攻擊範圍 (Blast Radius) 被極嚴格的 **Least Privilege** 成功地封死在這區區幾行程式碼的小黑盒裡面，這正是現代安全實作的典範。
