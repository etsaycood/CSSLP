# 第二套全真模擬試題 (Exam 2) - 答案與詳解本
## 領域 5：安全的軟體實作 (Secure Software Implementation) (18題) - Part 1 (Q1-Q9)

---

#### **1. A junior developer asks the security engineering team how to permanently and mathematically eliminate the threat of SQL Injection vulnerabilities when building dynamic database search queries. What is the absolute MOST effective secure coding mechanism the team should mandate?**
**(一位剛入行的小菜鳥工程師，虛心跑來請教資安大前輩：「前輩，當我正在手刻一個需要組裝動態字串來進行資料庫搜查的搜尋引擎時。要如何才能在物理與數學的結構層面上，『永恆且徹底、100% 絕對斬斷殲滅』所有 SQL 隱碼注入 (SQL Injection) 漏洞的威脅？」。為了給他最正確的解答，團隊應該強制他使用哪一種【業界公認最極致、最絕對有效】的安全撰寫程式碼機制？)**
A. Manually filtering out characters like `'` and `OR 1=1` using a custom Regex function. (用自己手工土炮手刻寫的正規表達式 (Regex)，辛苦地去把 `'` 單引號片段和 `OR 1=1` 這些字元給一個個過濾掉)
B. Using Parameterized Queries (Prepared Statements) provided by the database driver. (直接跪求使用資料庫官方原生驅動程式所提供、神功護體的【參數化查詢 (Parameterized Queries) / 預編譯語句 (Prepared Statements)】)
C. Encrypting the entire database column with AES-256. (把整個資料庫的欄位全部用 AES-256 給密碼學加密包死)
D. Using Client-Side JavaScript validation before sending the query. (在瀏覽器前端用 JavaScript 寫幾行字串驗證，算是在送出前把關)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「參數化查詢 / 預編譯語句」** 是對抗 SQL Injection 唯一且不可動搖的黃金霸主法則！當你使用 Prepared Statements 時，資料庫的引擎會先把你的「SQL 查詢骨架結構 (SELECT * FROM users WHERE name = ?)」先拿去編譯封死。然後，系統才會把使用者輸入的那包惡意字串（例如 `a' OR '1'='1`），像「塞進一個純文字檔案封裝罐」一樣填入那個 `?` 佔位符裡。在資料庫引擎眼裡，這包字串【永遠只配當作純文字字串去解讀，絕對不可能被當成具有殺傷力的 SQL 指令去執行】。這就在底層邏輯上物理剝奪了駭客改變語句結構的能力。
    *   **為何 A, C, D 全是找死的作法：** A (黑名單過濾) 永遠會被駭客用 Unicode 編碼或花式繞過。C (加密) 保護的是硬碟被偷時資料看攏無，但完全擋不住 SQLi 把加密資料全部刪除 (Drop table) 或整把摸走。D (前端 JS 驗證) 是個笑話，駭客按下 F12 開發者工具或是用 Postman 就能一秒繞過你寫的前端防線。

#### **2. During a source code review of a modern frontend React application, the security engineer finds that user comments pulled from the database are being rendered to the DOM using the function `dangerouslySetInnerHTML`. What critical secure coding practice must the frontend developers implement to prevent catastrophic Cross-Site Scripting (XSS) here?**
**(工程師在對一套現代極其酷炫的 React 前端應用程式進行程式碼「Ｘ光大體剖析 (Source Code Review)」時，資安專家差點腦充血！他發現：系統從資料庫撈出那些「由鄉民隨便亂留的留言板文字」，準備印印畫在網頁 DOM 畫面上時，程式碼居然直接裸奔呼叫了 React 世界裡臭名昭彰、字面上就寫著會死人的 `dangerouslySetInnerHTML` 函數！為了阻止這裡爆發核彈級毀滅的【跨站腳本注入攻擊 (XSS)】，前端大軍必須趕緊亡羊補牢實作哪一招救命的防禦編碼神功？)**
A. Rate Limiting (瘋狂踩煞車限制發文速率的速率限制)
B. Input Sanitization on the backend only. (只在後端進行輸入消毒，前端就不管了)
C. Context-aware Output Encoding (escaping the data before it is rendered into the HTML). (祭出看家本領：『具備上下文語境感知的【輸出編碼轉義 (Context-aware Output Encoding)】』！也就是在資料準備被畫上 HTML 畫面的那一秒鐘，強制把它給轉義逃脫 Escaping 毒化)
D. Enabling Cross-Origin Resource Sharing (CORS). (開啟那允許別人跨域來借位吃資源的 CORS 協議)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **防禦 XSS 的終極奧義，永遠是「輸出編碼 (Output Encoding)」**。當駭客在留言板輸入惡意的 `<script>alert('死')</script>` 時，如果前端原封不動地把它畫出來，瀏覽器就會乖乖照做引爆。所謂的「輸出編碼 / Escaping」，就是在把字串印到 HTML 前，強制把 `<` 翻譯成無害的 HTML 實體 `&lt;`，把 `>` 翻譯成 `&gt;`。這樣一來，瀏覽器看到這些字串時，就只會把它當成「純文字」傻愣愣地印在螢幕上，而不會把它當成「可執行的 JavaScript 程式碼」。現代框架 (如 React, Angular) 其實預設都會幫你做 Auto-escaping，只有那些手賤硬去呼叫 `dangerouslySetInnerHTML` 的工程師，才會把這個無敵防護罩給親手關閉。
    *   **為何 B 是錯誤的：** 雖然 B (輸入消毒 Input Sanitization) 也是好事，但它是第一道防線，且常常被繞過。資安界有一句名言：「輸入驗證防垃圾，輸出編碼防死劫」。防 XSS 絕對必須依賴最後一關的「輸出前打碼 (Encoding)」。

#### **3. A legacy C/C++ application has a long history of unexpectedly crashing when malicious users input excessively long strings into the username field. A penetration tester recently proved they could carefully craft an incredibly long string to overflow the memory boundaries and overwrite the system's instruction pointer, achieving a remote shell. What is the fundamental root cause of this vulnerability, and how MUST the developer fix it at the code level?**
**(一台用活生生 C/C++ 老派上古神語刻出來的系統，這十年來有著一個惱人又悲慘的宿疾：只要遇到外頭來鬧場的白目客，在「使用者名稱」文字框裡故意狂灌『無敵超級長度破表的超長字串』，系統就會直接崩潰死當！昨天，一位來測試的紅隊駭客更進一步殘暴地證明：他只要算準了長度，塞入一段精密手工打造的極端巨砲長字串，不僅能讓記憶體像水槽一樣溢出漫出來，還能精準地『淹滅並竄改這台系統作業系統大腦裡的指令指標 (Instruction Pointer)』，直接奪舍拿到系統最高管理員的操作主控權 (Remote Shell)！究竟是什麼上古邪魔造就了這個毀滅性死洞？而在寫扣的層面上，工程師必須如何拔劍重斬修正它？)**
A. SQL Injection. Fix: Use Prepared Statements. (這是 SQL 注入，解藥是參數化查詢)
B. Buffer Overflow. Fix: Replace historically unsafe, unbounded memory functions (like `strcpy()` or `gets()`) with bounds-checking functions (like `strncpy()` or `fgets()`). (這就是震古鑠今的【緩衝區溢位 (Buffer Overflow)】大魔王！解藥就是：徹底扒出並根除掉那些在人類歷史上惡名昭彰、『完全不量杯子容量就死命無底線狂倒水的上古危險函數 (像 `strcpy()` 或 `gets()`)』！全面替換成現代版『會先乖乖丈量檢查杯子長度邊界、水滿就停手的安全極限函數 (像加了 n 的 `strncpy()` 或是 `fgets()`)』)
C. Missing Encryption. Fix: Hash the input string using SHA-256. (這是因為沒加密，解藥是用 SHA-256 把它雜湊爛)
D. TOCTOU. Fix: Implement file locking. (這是時間差攻擊，解藥是幫檔案上實體鎖)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「緩衝區溢位 (Buffer Overflow)」** 是 C/C++ 這種「開發者必須自己去管記憶體怎麼切」語言的原罪與專屬死劫。早年的工程師為了圖方便，常使用像 `strcpy()` 或 `gets()` 這樣愚蠢的函式。這些函式在把「使用者輸入的一公里長度字串」塞進「只有 10 公分大小的記憶體杯子」時，居然【完全不會去檢查杯子是不是滿了】！結果多出來的水就漫出去，把隔壁記憶體裡神聖的「程式指針」給洗掉淹沒，讓駭客能指使電腦去跑惡意程式。防堵這個洞最標準的 Secure Coding 手法，就是在源頭程式碼裡禁用這些危險函式，改用帶有 "n" (代表檢查 N 個字元長度 Length bounds-checking) 的安全替代品，例如 `strncpy()`。

#### **4. A multi-threaded, high-frequency banking application occasionally allows a user with an exact balance of `$100` to successfully submit and execute two separate `$100` withdrawal requests, resulting in the bank incorrectly handing out `$200`. The logs show both requests hit the server's checking logic at the exact same millisecond before the database could subtract the first `$100`. What specific concurrency implementation flaw is this, and how can it be fixed?**
**(一家號稱多執行緒、以每秒萬轉光速運作的高頻飆車網路銀行，偶爾會發生一種詭異且讓銀行賠大錢的靈異事件：「一個窮鬼明明戶頭帳戶理只剩下『100 塊美金』。但他用腳本狂按送出，居然成功地『連續且獨立地刷出兩筆要求領 100 美金的提款單』，系統不但亮綠燈，還真的吐出總共 200 美金給他白嫖！」。調閱機房錄影帶 (Logs) 發現：因為這兩台車 (Request) 在【連一毫秒都不差的同一瞬間】，同時衝進了銀行的檢查站。左邊的守衛查餘額說「有100塊，放行！」，右邊的守衛同時查，也說「有100塊，放行！」。然後兩台車就開過去搶錢了，此時大後方的資料庫都還來不及扣掉第一筆錢！請問這等魔幻的『多執行緒時間差併發夾擊之術』是哪一種經典程式碼死穴？又該用何種神兵利器來制裁它？)**
A. Integer Overflow; Fix by using 64-bit integers. (數字滿溢出去啦；換成 64 位元的大管子來接)
B. Race Condition (Time-of-Check to Time-of-Use); Fix by implementing atomic database transactions or strict thread/row locking mechanisms. (這就是『並行爭用條件 (Race Condition)』中的最高級殺招：【驗證到使用之間的時間差魔術 (TOCTOU, Time-of-Check to Time-of-Use)】！唯一的解藥就是：下重手祭出強力的『資料庫原子性大一統交易包 (Atomic database transactions)』，或是極端霸道的『執行緒 / 資料庫資料列物理大鎖 (Thread / Row locking mechanisms)』！誰拿到鎖誰才能進去拿錢！)
C. Buffer Overflow; Fix by using a memory-safe language like Java. (緩衝區水滿出來了；滾去寫安全的 Java)
D. Cross-Site Request Forgery; Fix by adding an Anti-CSRF token. (跨站偽造發假請求；加一張防偽 Token 標籤抓鬼)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「Race Condition (競爭條件)」** 以及它的精華 **TOCTOU (檢查與使用之間的時間差)**，是所有平行運算、多執行緒系統 (Concurrency) 的絕對夢魘。當兩個進程在極短時間內爭奪同一份資源時，如果系統的「檢查餘額」與「扣錢」是這兩個是【分開斷裂】的動作。那第二個進程就會在夾縫中透過舊狀態來騙過系統。
    *   在實作面上，要斬草除根，必須仰賴 **同步鎖 (Locks / Mutex)** 或是資料庫的 **原子性交易 (Atomic Transactions)**。當第一封請款單進來時，他會拿到一把大鎖，把這個人的戶頭直接「排他性物理鎖死 (Row-level Lock)」。此時第二張請款單只能在門口罰站。直到第一張單子「驗完餘額、把錢扣到變 0、把鎖解開」。第二張單子進去時，查到的餘額就是 0，當場被打退件。這才是程式設計師控制多執行緒的唯一正道。

#### **5. A developer wants to ensure that whenever the application fails to connect to the backend database, the debugging process is as fast as possible. They configure the production server's global error handler to print out the raw, unhandled Java Exceptions and full, verbose stack traces directly onto the user's web browser screen. Why is this considered a severe implementation failure?**
**(為了『體恤民情』跟『超高拔群的除錯效率』，工程師自作聰明地在準備上火線上戰場的偉大伺服器上，做了一個偉大的設定：當這套偉大系統萬一不小心連不上大後方資料庫，並且在陣前大當機時！那個全球通配的『錯誤攔截顯示器 (Error Handler)』會直接、豪不遮掩地把從主機最底層噴出來的『鮮血淋漓血肉模糊、完全未經包裝隱藏的 Java 原始核心異常亂碼 (Raw Java Exceptions)』，跟那如同祖宗十八代族譜般綿延不絕的『底層錯誤堆疊追蹤骨架 (Full verbose stack traces)』，【一字不落地直接血淋淋印給前台網頁上的鄉民使用者看】！為何這等貼心之舉，被資安大祭司判為極端嚴峻的實作寫扣失敗大死罪？)**
A. Stack traces run extremely slowly and will cause a Denial of Service. (因為這堆疊字印出來會跑得很慢，導致網路卡死癱瘓 DoS)
B. It violates Information Hiding principles by exposing highly sensitive internal infrastructure details (like database versions, file paths, and SQL query structures) to potential attackers. (因為它公然犯下了背叛天條、違背『資訊隱蔽 (Information Hiding)』設計原則的死罪！它居然把極度機敏的系統底層武裝內衣機密 (例如：你資料庫精準的型號版本、機房裡資料夾的完整檔案絕對路徑、還有你手寫的 SQL 查詢語法骨架) 全部脫光光大方展示給外面路過的潛在駭客觀賞摸索！)
C. It will cause the browser's JavaScript engine to crash. (這堆血腥字元會嚇死讓客人的瀏覽器 JS 引擎吐血崩潰)
D. Stack traces take up too much bandwidth on mobile networks. (因為這推疊字太長了，非常浪費客人的珍貴手機網路流量頻寬)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「安全錯誤處理 (Secure Error Handling)」** 規定：應用程式絕對不可以向前端使用者吐出包含任何一絲一毫技術底層意義的 "Stack Trace" 或是 "Raw SQL Error"。在駭客眼中，這些報錯文字簡直是無價之寶的「武功秘笈」。透過堆疊字串 (`C:\inetpub\wwwroot\admin\UserDb.java:Line45`)，駭客一秒就能知道你在用什麼語言、檔案路徑藏在哪、甚至資料庫是哪個老舊版本。這讓駭客省下幾個月的蒙眼試探時間，直接量身打造針對性核彈。正確的實作方法是：系統內部將這些血腥長篇大論紀錄在「受嚴格保護且只有工程師能看的後台日誌 Log」裡，然後在外頭只對使用者回傳一句溫暖客氣且毫無意義的客套話：「Oops！系統似乎遇到了點麻煩，請聯繫客服 (代碼: 500)」。

#### **6. A hacker creates a malicious, entirely separate website containing a hidden JavaScript form. When a victim visits the hacker's site, the hidden script automatically submits a "Transfer $1,000 to Hacker" request in the background toward the victim's banking website. Because the victim is already logged into the bank in another tab, the victim's browser automatically attaches their valid Session Cookie, and the bank executes the transfer. What specific implementation defense is missing from the bank's HTTP forms?**
**(一場邪惡的魔術：暗黑駭客在深海建起了一座充滿誘惑色情圖片的毒窟網站。在這網站的地底暗礁中，藏著一張全隱形、寫著『把一千美金過戶給大魔王』的隱形 JavaScript 傳送表單。當某天上網的肥羊鄉民，被誘騙逛進這毒窟時！這張恐怖表單就在背後無聲無息地發動，朝著肥羊的『正牌網路銀行金庫大網站』射出轉帳請款單。最要命的是！因為這頭肥羊剛好在隔壁的分頁，還正熱騰騰地登入掛著那家銀行的金庫連線沒登出！這肥羊電腦上那智障貼心的瀏覽器大管家，在看到那張射往銀行的請款單時，居然連問都不問，就『自動順手把肥羊身上的【金庫神聖通行餅乾 (Session Cookie)】給夾上去一併寄出』！銀行皇城看到餅乾，以為是國王親臨，直接把錢送給了駭客！請問！這家倒楣的銀行，在其網頁 HTML 防衛表單中，到底漏掛了哪一道免死金牌防禦結界，才會被害得如此慘？)**
A. Anti-CSRF (Cross-Site Request Forgery) Synchronizer Tokens. (少了一尊名為『反跨站請求偽造 (Anti-CSRF) 隨機同步護身符 Token』的大將軍鎮壓把關！)
B. HTTPS (TLS 1.3) encryption. (少了那幫包裹穿上鋼鐵裝甲的 HTTPS 加密外套)
C. Parameterized Queries. (少了幫人擦屁股的參數化查詢神功)
D. Output Encoding. (畫面上少了塗碼掩飾的輸出轉碼大法)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 這是對 **CSRF (Cross-Site Request Forgery / 跨站請求偽造)** 攻擊最經典、如教科書般的精準描述。此攻擊的核心利用了瀏覽器一個遠古的白癡天性：「如果在 Cookie 還沒過期的期間，只要是寄往該網域 (`bank.com`) 的信，瀏覽器都會『自動雞婆附上』那張登入 Cookie」。銀行如果只看 Cookie 來認人，就絕對會被這種跨網站釣魚攻擊給坑殺。
    *   **銀行唯一解藥：** 前後端開發者必須在寫 HTML POST 表單 (轉帳表單) 時，塞入一個防偽機制：**CSRF Token** (Synchronizer Token Pattern)。這個 Token 是一組超級隨機亂碼，【它不是存在 Cookie 裡，而是每次重新整理網頁時，銀行暗中塞在 HTML 畫面表單的隱藏欄位中】。當駭客從他的網站發動攻擊時，他有能力讓瀏覽器夾帶 Cookie，但他【絕對無法預測也猜不到現在印在那張表單上、只有一兆分之一機率猜對的 CSRF 亂碼 Token 是甚麼】。所以這張連署單一送到銀行門口，銀行看到有 Cookie 但「沒附上防偽 Token 印章」，就直接抓出這是偽造的攻擊並當場撕毀退件拒絕。此外，現代也可以設定 Cookie 的 `SameSite=Strict` 屬性來防禦。

#### **7. A developer needs the application backend to automatically authenticate to an external cloud database upon startup. To ensure the code builds seamlessly on all developer laptops without complex configuration, they copy and paste the production database password directly inside the `config.java` source code file and commit it to the Git repository. What fundamental secure coding practice is violated, and what is the proper solution?**
**(為了讓這座偉大應用系統的大腦，在開機甦醒的那一刻就能全自動連上雲端那座金光閃閃的大金庫。更為了體貼不讓其他開發兄弟們在自己筆電上跑程式時還要痛苦設定一堆參數。這位天真好心的神仙工程師，居然大筆一揮！把『營運上線能掌控幾千萬人生死的真實驗證通行密碼 (Production Password)』，大剌剌地【複製貼上、明文刻死寫入在名為 `config.java` 的原始碼檔案中】！然後再愉快地按下 Enter 遞交上傳，把它世世代代鎖進並廣播到整間公司幾百人都看得到的中央 Git 版本大倉儲中！請問，此等駭人聽聞的愚蠢暴行，是公然觸犯了哪一條防雷鐵律？且正確能拿來擦屁股的解法仙丹何在？)**
A. Violates Principle of Least Privilege. Solution: Make the database public. (觸犯了最小權限法；解法是一不做二不休把資料庫搬上街頭公諸於世)
B. Violates Open Design. Solution: Encrypt the Java file. (觸犯陽光設計法；解法是把這包 Java 原始碼用膠帶加密包起來)
C. Violates Hardcoding Secrets. Solution: Remove the password from the source code entirely and dynamically retrieve it at runtime via Environment Variables or a centralized Secrets Manager (Vault). (公然觸犯了該千刀萬剮的【將機密寫死埋屍法 (Hardcoding Secrets)】！唯一解藥：立刻把這密碼從原始代碼的祖宗十八代歷史中徹查抹除斷根！然後改為在系統甦醒運轉那一刻，在虛無縹緲的『伺服器實體環境變數 (Environment Variables)』中暗中摸取拿回它，或者派特使去向如金鐘罩般的『中央機密保險大本營 (Secrets Manager / HashiCorp Vault)』動態請領叩關調用！)
D. Violates Data Minimization. Solution: Delete the database. (觸犯資要最小化天條；解法是把那顆金庫物理刪除一勞永逸)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「把密碼或金鑰寫死在原始碼裡 (Hardcoded Secrets/Credentials)」**，在現代 DevOps 時代絕對是「離職起手式第一死罪」。因為程式碼最終會被上傳到 Git，只要有任何一個離職員工偷偷拷貝了這包代碼帶走，他明天就能連進你的大金庫搞死這家企業。
    *   在實作面上，解藥被稱為 **"Secrets Management" (機密管理)**。開發者被強烈命令：在 `config.java` 裡面只能寫 `db_password = System.getenv("DB_PASS")`。這密碼【絕對不能跟著程式碼被版本控制】，它必須存在部署那一台伺服器的作業系統「環境變數」裡；或者是更高階的做法，這台系統開機時，程式會用自己的金鑰去一個專門保固密碼的神仙洞 (例如 AWS Secrets Manager, HashiCorp Vault) 拉出當下兩小時有效的拋棄式密碼來用。

#### **8. A popular multiplayer game application stores the player's total cumulative gold as a signed 16-bit integer (which has a maximum positive value of 32,767). A clever hacker discovers that if they aggressively grind exactly 32,768 gold pieces, the computer's memory wraps around, the balance suddenly reads `-32,768`, and the game economy instantly breaks. What specific mathematical vulnerability was implemented, and what is the fix?**
**(在一款風靡全球的多人大逃殺撿金幣神作中，這群愚笨的首推工程師在畫設計圖時，把記錄鄉民身上所有家當金幣的箱子，定死成了一個只有「帶符號的 16 位元大小 (Signed 16-bit int)」的破木籠子。(這代表這爛箱子最多最多只能裝下 `32,767` 枚金幣)。一位肝帝級駭客發現了這個破綻，他不眠不休狂操一個禮拜，終於精準地吃下第【『32,768』】枚金幣的瞬間！電腦理智線崩潰，記憶體數學宇宙直接發生大摺疊 (Wraps around)，這傢伙戶頭上的財產居然瞬間如跌入谷底般變成負債累累的『-32,768』塊錢！這直接讓遊戲商城物價狂亂崩盤。請問這起慘烈的系統破產事件，是植入了哪根惡魔般的數學大毒草？工程師又得用何種仙丹補這破洞？)**
A. Buffer Overflow; Fix by adding memory randomization (ASLR). (水槽滿了漫出來；加入記憶體亂數魔法洗牌陣)
B. Floating Point Error; Fix by rounding to two decimal places. (這是有小數點的浮點數魔界；加入小數退位四捨五入大法)
C. Integer Overflow/Underflow; Fix by implementing strict mathematical bounds checking before performing arithmetic operations, or replacing the variable with a larger data type capable of holding the value. (這就是『整數滿溢 / 下溢宇宙大反轉 (Integer Overflow/Underflow)』！補救仙丹：在進行每一個加減乘除加金幣動作前，死死安插強硬的『數學極限安檢攔截哨 (Bounds Checking)』，看加了會不會爆表！或是最乾淨俐落的：老兄！直接換個「超級無底洞大容量 64 位元巨無霸箱子 (Larger data type)」來裝不就得了嗎！)
D. Cross-Site Scripting; Fix by HTML encoding the gold value. (畫面上被偷加字了；用 HTML 轉碼印出來破除它)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「整數溢位 (Integer Overflow)」** 是一個古老但至今仍會摧毀金融系統的死穴。電腦在算數學時，箱子的位元上限是一面牆壁。當一個有正負號的 16 bit 整數 (最大值 0111111111111111 = 32767) 再被加 1 的時候，最左邊的 0 會變成 1 (變成了負號標記)，導致數字瞬間大逆轉變成最小負數 -32768。
    *   在安全編碼實作中，要杜絕此事：第一是「換盆子」，在設計金融貨幣時至少要用到 64-bit int (如 `BigInteger`) 讓駭客有生之年加不滿。第二是「加邊界判斷 (Bounds Checking)」，在每一行 `balance = balance + amount` 的前面，必須插上一行檢查：如果加法算出來的數學值超過系統規定的極限值天花板，絕對不能照做賦值，而是應該丟出錯誤停止這條交易。

#### **9. A Java web application receives a Base64 encoded, serialized payload from the client's HTTP cookie, decodes it, and passes it directly into the `ObjectInputStream.readObject()` function to seamlessly reconstruct the user's profile object in memory. During a routine pentest, the server is suddenly taken over via a devastating Remote Code Execution (RCE) attack originating from that cookie. What vulnerable implementation pattern was explicitly used?**
**(在一台以 Java 刻骨銘心打造的網路主機上，它居然不知死活地把從外頭髒街（客戶端 HTTP Cookie）收進來的『一坨包裹著 Base64 亂碼偽裝的被冰凍序列化 (Serialized) 大包裹』給接進家中。拆了 Base64 外衣後，這程式甚至連問這包裹是誰寄的都不問，就張開血盆大口，【如獲至寶般直接把它整包塞進、餵入名叫 `ObjectInputStream.readObject()` 的這個具有上帝般神力、能把死人白骨直接無縫起死回生重新拼湊成記憶體裡活跳跳特權老爺物件 (Object) 的復活大函數中】！！結果顯而易見：在一次例行性的紅隊掃蕩中，這名駭客只是在 Cookie 裡塞進了一尊惡靈，這台主機在試圖復活包裹的瞬間，就慘遭地獄般的『遠端死劫大屠殺直接被奪卡接管 (Remote Code Execution, RCE)』打穿。這悲催的血案，是源自這工程師手賤實作了哪一套死亡禁忌開發模式？)**
A. Server-Side Request Forgery (SSRF) (伺服器瞎眼幫忙去外頭買東西 SSRF)
B. Insecure Deserialization of entirely untrusted data without prior strict schema validation. (把外頭那些底細完全不明、渾身是毒的包裹，在根本沒有實施嚴厲金鐘罩檢視 (Schema validation) 的情況下，就雙手敞開大方實施【「極度不安全的逆反序列化邪術招魂大開箱 (Insecure Deserialization)」】！)
C. SQL Injection (去資料庫戳瞎子漏洞)
D. Man-in-the-Middle (MitM) (駭客坐在你跟網站中間雙面間諜洗腦)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「不安全的反序列化 (Insecure Deserialization)」** 曾是 OWASP Top 10 頭號殺手，更是 Java 王朝史上最令人聞風喪膽的死穴。序列化 (Serialization) 是一種將物件變成字串冷凍送去網路上飛梭的好用魔法；反之，反序列化 (Deserialization，如 Java 的 `readObject()`) 則是將冷凍食品解凍還原生命。
    *   **核心災難點：** 如果解凍魔法引擎太過笨拙聽話。當你從極度不信任的客戶端 (Cookie) 收到一包冷凍包裹。駭客如果把包裹內容竄改掉，把一段能行使 `exec("rm -rf /")` 這樣系統毀滅指令的邪惡物件包進去。當你的 Java 一呼叫 `readObject()` 去試圖解開並建構這個物件的瞬間，惡意代碼就會被自動觸發引爆。在實作上，【絕對不能】直接反序列化不被信任的輸入；如果要收，只能改用純淨無害的 JSON，並使用不會自動啟動邪惡神功魔法的輕量級解析器 (如 Jackson 且關閉 Default Typing)。
