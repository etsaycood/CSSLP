# 第二套全真模擬試題 (Exam 2) - 答案與詳解本
## 領域 5：安全的軟體實作 (Secure Software Implementation) (18題) - Part 2 (Q10-Q18)

---

#### **10. An implementation developer needs to generate a highly unpredictable 128-bit session token string to assign to a user upon a successful login. They quickly write code to generate the token using the standard `Math.random()` function library provided out-of-the-box by the programming language. Why will the security architecture team immediately reject this code during review?**
**(一名正在刻苦趕工的實作工程師，身上背著一條任務：在肥羊成功輸入密碼登入帳號的那一秒，替他發送打上一條由『極度不可被猜透、128 位元長度』的連線通行金牌字串 (Session Token)。為了圖快省事，他隨手敲鍵盤呼叫了這老古董程式語言【原廠內建附送、最簡單暴力的標準 `Math.random()` 數學套件庫亂數產生器】去隨便灑出一把號碼充數。請問，為何在白皮書防禦審查時，這名菜鳥的心血結晶不僅會被這群惡魔般的資安架構前輩們直接當場砸碎駁回不屑一顧？)**
A. It generates tokens that are too long to fit in a cookie. (因為這老爺車數學庫生出來的號碼字串太冗長，導致瀏覽器餅乾塞不下去)
B. Standard random math functions are statistically predictable (Pseudo-Random) and mathematically vulnerable to sequencing attacks. The developer MUST explicitly use a Cryptographically Secure Pseudo-Random Number Generator (CSPRNG) like `/dev/urandom` or `java.security.SecureRandom`. (因為這套標準老爺車的亂數產生函數不過是個被騙小孩的『只能騙外行人的偽隨機 (Pseudo-Random) 瞎猜產生器』，在統計學上，它極其容易被有心人透過上一把的點數、反推算出下一把的底牌 (Sequencing attacks)！為了不讓公司送命，這菜鳥【被死死按頭強制規定：必須】去開外掛請出『神聖不可被預測的密碼學核彈級強化大亂數產生器 (CSPRNG, Cryptographically Secure Pseudo-Random Number Generator)』，好比說 Linux 系統的 `/dev/urandom` 黑洞或是 Java 神棍的 `java.security.SecureRandom` 加持！)
C. It relies on Open Design, which hackers can view. (因為他用這個數學庫就等於把家裡保險箱攤在陽光下被駭客笑)
D. `Math.random()` only generates letters, not numbers. (因為 `Math.random()` 是個只能製造出英文字母的殘疾產生器)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「安全的隨機數產生 (Secure Random Number Generation)」** 是密碼學實作的基礎。一般的 `Math.random()` (PRNG) 是為了解決統計學或遊戲擲骰子設計的，它的隨機性是由一個「種子 (Seed，通常是當前的時間毫秒數)」算出來的。這代表只要駭客知道你伺服器現在幾點幾分，他就能用同樣的數學公式，完美「預測 (Predict)」出你發給下一個客人的 Session Token 是幾號。而 **CSPRNG (密碼學安全偽隨機數產生器)** 則是會去收集系統中如「硬碟讀寫噪音、CPU 溫度擾動、滑鼠軌跡」等無法被物理預測的超高混亂熵值 (Entropy) 來做種子。只有用 CSPRNG 噴出來的 Token 或加密金鑰，才能保證就算駭客拿到前 100 個 Token，也絕對猜不出第 101 個。

#### **11. An application allows users to download their monthly PDF invoices by clicking a link that passes the filename in the URL exactly like this: `https://bank.com/download.php?file=invoice_jan.pdf`. A hacker manually changes the URL to `?file=../../../../etc/passwd` and successfully downloads the underlying Linux server's highly sensitive password configuration file. What is the missing secure implementation control?**
**(震驚！一個極其良善的下載頁面，設計了一個能讓好人們開心點擊連結下載自己『每月 PDF 帳單明細』的按鈕。它的網址後方是這樣乖乖夾帶參數檔名的：`https://bank.com/download.php?file=invoice_jan.pdf`。但某個手賤的無聊駭客魔將，就這樣在網址列大搖大擺地用手動把它改成了一連串詭異的：`?file=../../../../etc/passwd`。結果下一秒，這破網站的伺服器居然就像著了魔一樣，乖乖地『一路聽話退回、走入連伺服器最底層的 Linux 總司令部』，並把那本藏著這間企業主機生死命脈、最最機敏的『系統登入密碼身家設定檔』給雙手打包免費送給駭客下載！請問這破網站是丟了哪一把防護大鎖？)**
A. Missing Authentication. Mitigation: Add a login page. (這網頁肯定沒裝鎖，補救法是裝個登入頁)
B. Failure to validate and constrain path input (Directory Traversal / Path Traversal). Mitigation: Aggressively strip path manipulation characters (like `../`) and forcibly map the input string to an internal static Allowlist, refusing to ever pass raw user input directly to the operating system's filesystem APIs. (這是犯了最下三濫的【輸入路徑驗證失敗及未加拘束之大罪 (也是臭名昭彰的目錄穿越攻擊 Directory Traversal / Path Traversal)】！真正的仙丹解藥是：在收東西的大門口，用鐵絲網暴力洗刷掉攔截任何想操縱作業系統目錄的字元 (例如 `../` 退刀流)！但最強悍的作法是，強迫把外頭送進來的這些髒字串，直接在一張早寫好的『內部神聖對應白名單 (Allowlist)』上比對找翻譯，【永遠死扛著拒絕直接把充滿劇毒的輸入字串扔進去餵給那單純老實的兵工廠底層檔案系統引擎 (Filesystem APIs)】！！)
C. SQL Injection. Mitigation: Use Prepared Statements. (這是傳說中的盲注 SQL 注入，用預先防備術擋下)
D. Broken Cryptography. Mitigation: Encrypt the PDF files. (密碼學死當被戳破；補救法是把這堆 PDF 全都打亂加密鎖起來)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「目錄穿越攻擊 (Directory Traversal)」** (又稱 Path Traversal) 是一種直取作業系統心臟的攻擊。網站伺服器 (如 Tomcat/Apache) 本應該只被關在一個名為 `/webroot/` 的特定目錄箱子裡活動。當程式碼收到檔案名稱 `invoice.pdf`，它應該只去自己箱子裡找。但駭客輸入了 `../` (在 Linux 語法中代表「退回上一層資料夾」)，這迫使原本只該在箱子裡找的伺服器，一路爬出箱子、甚至爬回了最底層的系統根目錄 `/`。
    *   **實作緩解法：** 第一層防禦是「驗證與過濾輸入」，去除所有 `../` 或 `%2e%2e%2f` 這類跳脫字元。但最極致安全的防禦是 **「不直接相信使用者輸入 (Indirect Object Reference / Allowlist)」**。與其讓使用者輸入 `file=invoice.pdf` 並傳給作業系統，不如讓使用者輸入 `file=1`，然後後端有一張對照表 `[1 => /secure/invoices/jan.pdf]`。如果使用者輸入 `file=../../etc/passwd`，這張表根本查不到這個代碼，系統就會直接報錯，完美物理性阻絕穿越攻擊。

#### **12. A mobile application makes the following API call to fetch the current user's profile data: `GET /API/v1/user/account_details?id=505`. User `505` legally logs in, observes the API call in their proxy, manually changes the ID in the URL parameter from `505` to `506`, and successfully views the extremely private medical data of user `506`. What specific API authorization implementation entirely failed?**
**(一家堂堂正正提供醫療照護服務的偉大手機 App，為了撈取某個合法使用者大爺的個人健康資訊，它派兵對後台呼叫了這條天經地義的 API 密碼咒語：`GET /API/v1/user/account_details?id=505`。但這位號碼 `505` 號的病患大爺，是個深藏不露的無聊駭客。他在自己手機上架起監聽器看到這畫面後，冷笑一聲！並手動、極端白目地把那個 `505` 的參數數字給改成了 `506` 號。然後按下重送。令人驚悚的是！這座雲端大機房居然不疑有他，立刻就把那可憐的 `506` 號鄰床老先生那些極度私密且丟臉的梅毒開刀大病歷表資料全倒出來給這位駭客看了！這簡直是滅國級的慘案！請問，在實作這條 API 的那一刻，到底是哪一道『守門員武士的終極授權大門 (API authorization)』徹底睡著崩塌了？)**
A. Insecure Direct Object Reference (IDOR) / Broken Object Level Authorization (BOLA). The API merely checked if the user was logged in, but failed to assert if the logged-in user actually possessed ownership rights to the specific object (ID=506) being requested. (這就是惡名昭彰並稱霸 OWASP API 弱點排行榜首的：【不安全直接物件參考 (IDOR) / 或者在現代被尊稱為『毀滅性崩盤的物件等級權限授權大失靈 (Broken Object Level Authorization, BOLA)』】！這條守門 API 簡直是個白癡，它其實有睜開眼核對「嗯，這拿票進來的人確實有買票登入是個活生生的網站會員 (Authentication)」。但！它卻【徹底忘了】在給出資料前，轉頭問一句：「等一下！這個來跟我討『506號病歷大保險箱』傢伙，他老兄口袋裡的擁有者證書所有權，真的是這個保險箱的主人嗎？(Authorization Failed)」)
B. Lack of TLS encryption on the API endpoint. (這家 API 後門少穿了那件叫作 TLS 強加密大外套防風衣)
C. Cross-Site Scripting (XSS). (跨站大劇毒腳本 XSS)
D. Buffer Overflow. (記憶體死死塞爆之水槽滿溢大洞)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **「IDOR (Insecure Direct Object Reference) / BOLA (Broken Object Level Authorization)」** 是近年來最氾濫、殺傷力極大的 API 邏輯漏洞。與「你是不是我們網站會員 (身分驗證 Authentication)」無關。它的死穴在於「授權 (Authorization)」。當一個合法會員 A 登入後，他擁有合法的 Session Token。當他去要 `id=B` 的資料時，愚蠢的後端工程師只寫了 `if (isLoggedIn()) { return db.find(id); }`，卻忘了加上最重要的一行防禦邏輯：`if (isLoggedIn() && session.userId == input.id) { ... }`。因為少驗證了「物件擁有權」，導致任何人只要改數字就能看光所有人的資料。這在設計 API 時是必考的存取控制實作題。

#### **13. A modern Node.js web application is built entirely upon an ecosystem of 400 different open-source NPM packages imported from the internet. The internal developers meticulously write perfect, flawless secure code for their own proprietary logic. Yet, the application is still catastrophically compromised because one of the imported NPM packages contained a hidden, community-injected malicious backdoor. What SDLC implementation process failed?**
**(一支堪稱走在現代潮流最前衛、以 Node.js 為心臟所建構的巨大網路平台，它猶如一顆寄生怪獸般，大口吸納吞噬並整個架構建立在那高達『400 個從茫茫網際網路免費軟體庫 NPM 瘋狂搬回家大補貼開源包裹 (open-source packages)』的龐大溫床肩膀上。這家公司裡自家重金養的上百位工程師無比爭氣！他們日以繼夜死敲猛刻，寫出了連上帝都挑不出毛病、堪稱【完美無瑕且堅若磐石的金手指自家資安防護邏輯與原始魔法架構程式碼】！但是！就在昨夜狂風暴雨中，這套他們自信滿滿的應用平台卻依然慘遭毀滅性滅城的爆殺入侵。原因是被揭穿出：那 400 包從網路上免費搬回來兜的開源積木包裹中，有『其中一個看似無害的小套件裡，早就被那黑暗混亂的開源黑客鄉民社群給暗中偷注下了一隻深淵小門後門毒蠍 (community-injected malicious backdoor)』。請問，這堪稱含冤而死的這家公司，在當初的 SDLC 大輪迴建造流水線上，丟失沒做好哪一道神聖大門的安檢流程？)**
A. Penetration Testing was not performed aggressively enough. (只怪他們在最後一道紅隊打洞滲透演練時，大夥敲打得不夠用力)
B. Software Composition Analysis (SCA) / Dependency Management. The team failed to rigorously scan, audit, and mathematically pin the versions of their third-party supply chain libraries to detect known compromises. (最要命的疏失在這：【未能祭出軟體祖宗十八代成分血統大透視掃描儀 (Software Composition Analysis, SCA) / 徹底失能的外包依賴供貨管理 (Dependency Management)】！這支大隊沒能在生產流水線上，用Ｘ光機冷血嚴厲地一一審視、稽核那些從路邊免費撿回來的第三方代碼供應鏈積木！且沒有狠心動用那『鎖妖版本鐵釘定死』魔法，將那些外部包裹版圖死命鎮壓在當時無害的那一特定版本號上，從而未能及時偵測出這些外援早就染上毒血通敵的可怕大案)
C. The developers should not have used Node.js. (唯一不該怪別人的死罪就是：這群蠢才一開始就不該踏進那寫著 Node.js 招牌的大門寫扣)
D. Threat Modeling was skipped. (因為他們在白板前漏畫了那張名喚『威脅大兵推圖紙 (Threat Modeling)』)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是現代軟體開發最恐怖的夢魘：**「軟體供應鏈攻擊 (Software Supply Chain Attack)」**。在這個年代，90% 的程式碼其實是拿別人寫好的開源函式庫 (OSS) 湊成的。你自己寫了 10% 的無懈可擊程式碼，但卻不知道你下載的那個「幫字串上標籤顏色」的 `npm` 小套件，五天前已經被原作者轉賣給了俄羅斯駭客，並被悄悄埋入了一段「偷所有系統變數然後送回莫斯科」的後門程式 (`malicious backdoor`)。
    *   **實作防禦解法：** 這個時候，傳統的弱點掃描 (SAST) 以及滲透測試都瞎了，因為這段程式碼不是你寫的！團隊【必須必須必須】使用名為 **SCA (軟體組成分析，如 Snyk 或 Dependabot)** 的武器。SCA 會像海關一樣，把這 400 個套件攤開（產出一份 SBOM 軟體物料清單），然後每天拿著清單去全球最大的通緝黑名單資料庫裡比對。一旦發現你撿回來的這包積木今天被列入「已被駭客下毒」的死亡通報，SCA 就會立刻敲響警鐘退件。這是 DevOps 時代唯一的保命符。

#### **14. To make creating shareable bookmarks easier for users, a frontend developer implements a login flow that intentionally submits the user's username and password via an HTTP GET request, resulting in a visible URL parameter string like `https://portal.com/login?user=admin&pass=secret123`. Why is this considered a catastrophic and amateur implementation error?**
**(工程師為了一份白象般不必要的好意，想要讓鄉民顧客們可以『把登入畫面加書籤並無痛轉貼寄給阿公阿嬤』。他於是設計了一套超智障的登入放行流！這套流程居然刻意、手動大方地將用戶親手敲下那神聖不可侵犯的『大門登入帳號跟銀行密碼』，用一種【裸身赤裸在街上大喊逛街的粗糙 HTTP GET 廣播要求協議】送給了雲端！這導致在送出的那一秒鐘，所有的機密全都像是掛著長長的萬國旗一樣，清清楚楚且不要臉地『完全赤裸顯露在眾人皆見的超大字號網址列上方 (URL parameter string) 像這樣：`https://portal.com/login?user=admin&pass=secret123`』。為什麼這種設計會被資安大前輩一巴掌打飛，被視為一場災難也是極端三流業餘寫手的實作大血洞？)**
A. GET requests are strictly limited to 10 characters. (因為 HTTP 的 GET 寫法有宇宙極限，只能塞得下那可悲的 10 個字元短劇)
B. Passwords sent in the URL string of a GET request are permanently recorded in plaintext across browser histories, upstream corporate proxy logs, and the receiving web server's access logs, massively exposing the credentials. Credentials must ALWAYS be sent hidden within the POST body. (因為當你膽敢用 GET 網址傳遞密碼那一秒！這串驚天機密就會像刻在石頭上一樣，被【永恆不滅的無情明文死死記錄且烙印】在鄉民的電腦瀏覽器歷史清單裡、烙印在沿路上流經網咖與各大企業那監視一切流量代理守門伺服器老爺 (Proxy logs) 身上、更會被那遠在天邊的終點接收站大伺服器『以裸奔純文字的模樣死釘在那毫無防備的最基礎接客訪客日誌裡 (access logs)』。而引發了覆水難收的終極大走光洩密！所以那些會掉腦袋的重要機密與身分憑證牌子，【這輩子都注定永遠必須被死命暗藏裹在一件名為以 HTTP POST 所寫的隱形身體內文中 (POST body)】！)
C. GET requests cannot be encrypted by HTTPS. (因為當你選了 GET 這條路，就註定這輩子再也無緣穿上名為 HTTPS 這套加持保命防彈衣，這是物理不可能的)
D. It violates the SQL Injection parameters. (因為這種寫法一瞬間就得罪且違背了那套資料庫大魔王所謂的 SQL 注入的法典參數)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「敏感資訊不得於 URL 中傳遞 (NO Sensitive Data in URL)」** 是 Web 架構師入行第一天要背的天條。雖然在功能上，你用 GET 把密碼跟在網址後面也可以成功讓後台收到登入。但是，URL 網址是一條在網路上會被大家無心「反覆抄寫紀錄 (Logged)」的心魔。
    *   **災難後果：** (1) 使用者如果不小心把這條網址複製貼給朋友，就等於直接把帳密送人；(2) 所有公司都有 Proxy (代理伺服器) 在側錄員工上的網址，老闆能看到你明文密碼；(3) 在後端伺服器 (如 Nginx 或 Apache) 每天記流水帳的 `access.log` 裡面，會滿滿地、明文無加密地寫下全天下幾萬名會員每天的密碼 `?pass=secret123`。這是嚴重的資訊外洩！這也是為什麼規定所有登入與機敏操作，【必須永遠使用 HTTP POST，並將機密參數藏在其不透明的訊息主體 (Body) 封包內傳遞】。
    *   為什麼不是 C：這是一個很常見的謠言。即使 URL 有一百個參數，如果你的網站有使用 HTTPS，整段 URL (包含路徑跟參數) 一樣本體都有被加密傳輸，**網路線上的駭客是看不到的**。但是，那條紀錄是死在「有權限看端點 log 日誌本」的人的手上！

#### **15. A backend database engineer is explicitly tasked with securely storing new user passwords. Because the system is highly latency-sensitive, they decide to run all incoming passwords through the extremely fast, highly optimized `SHA-256` hashing algorithm before writing them to disk. Why is this implementation choice considered radically insecure by modern cryptographic standards?**
**(因為接下了這神聖無比的密令：把全天下這千萬名會員剛輸入熱騰騰的新戶密碼給妥善安全藏進大金庫！但偏偏這名大後方打雜的小資料庫工程師是個講求極致飆風速度的腦殘。因為這套系統極端講究「低延遲不延遲 (Highly latency-sensitive)」，所以這位老兄心想『天下武功唯快不破』！他決定在密碼寫進硬碟前，只把它們全部塞進那一台【講究極端光速運轉、效率被優化壓縮到頂天的『純淨無瑕 SHA-256 單向榨汁雜湊大水車引擎』】就直接了事。請問大工程師！這套自作聰明的飆車美意，在今日冷酷如冰的那一幫現代密碼學死神裁判眼中，為何被視為可恥且極度不安全大破綻的粗心爛設計？)**
A. Hash functions can be reversed instantly using Base64 decoding. (因為天下所有的雜湊函數都只是唬人的爛魔術，路過的小孩都能輕而易舉用 Base64 解碼器倒推解碼出來)
B. Fast, single-iteration hashing algorithms (like pure SHA-256 or MD5) are massively vulnerable to modern brute-force, GPU-accelerated offline cracking. The engineer MUST implement an intentionally slow, CPU/Memory-hard "Key-Stretching" or "Work Factor" algorithm like Argon2, bcrypt, or PBKDF2 alongside a unique salt. (因為在這兵器火力強大恐怖的現代戰場！那些主打『快如光電閃光、只碾過一次就不回頭的三流榨汁雜湊算法 (如最純潔的 SHA-256 甚至老古董 MD5)』，在現代那群裝載這『怪物級超級電腦冷血多核心並聯顯示卡運算 (GPU-accelerated)』大砲的無情字典與彩虹表離線猜密碼爆破大軍面前，薄弱得像張廢紙一樣秒破！為保命，這工程師【必須被迫選擇服下那猛藥：刻意反其道而行，導入那種宛如果凍般會黏死消耗 CPU 跟記憶體效能，『刻意他媽慢到有剩、故意拖時間折磨硬體的高消耗防呆拖延打怪兵法 (名喚 Key-Stretching 金鑰延展大法，或是耗時硬實力 Work Factor)，譬如如神明般的 Argon2、bcrypt 或 PBKDF2】！並親手撒下神聖專屬一員一份的鹽巴 Salt 結界共組大陣才行！)
C. SHA-256 is owned by the NSA and contains a backdoor. (這是一場天大的陰謀：他選的那根 SHA-256 魔法棒是美國老爹國家安全局 NSA 暗中留下一道走後門開關的監控眼)
D. Passwords should be stored in plaintext to prevent data corruption. (他一開始就錯了！為了不讓密碼哪天壞軌腐敗死機，所有密碼都只准、且應該永遠在硬碟裡裸身純真地保留最初始的那張明文模樣)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「密碼儲存的黃金法則 (Password Storage)」** 是資安實作的重中之重。SHA-256 是用來證明「這份百萬字電子合約有沒有被竄改」的演算法，它的設計初衷就是「**越快越好**」，而且在現代 GPU (如 Nvidia RTX 4090) 的加持下，一秒鐘能計算幾十億次的 SHA-256 雜湊。如果在資料庫存的是單純的 SHA-256，而資料庫不幸被中國駭客拖庫帶回家。駭客用他的挖礦機跑字典檔，不用一小時就能把這幾千萬人的密碼全部神不知鬼不覺地反推 (猜對) 出來。
    *   **真正用來儲存密碼的解藥** 是使用 **"Key Stretching (金鑰延展)"** 或 **"Work Factor (工作因數)"** 演算法。如 **bcrypt、Argon2 (目前第一名推薦)、PBKDF2**。這些演算法的設計哲學是「**故意把它做得超級慢且消耗巨大量 CPU 甚至記憶體運算**」。你可以設定一個「成本參數 (Cost)」，讓它算一次 hash 必須死撐整整拖延消耗掉電腦半秒鐘的時間。對於人類登入等半秒根本沒感覺；但對於駭客想要一秒狂猜一億次的大砲來說，這個「慢了十億倍」的數學沼澤泥淖，就徹底、物理性地輾碎了駭客想要用暴力破解 (Brute-force) 還原密碼的無盡痴人美夢。加鹽 (Salt) 則是順手毀掉彩虹表。

#### **16. A B2B inventory application frequently processes vendor manifests uploaded as standard XML files. A clever attacker uploads a highly crafted XML file containing a malicious `<!ENTITY>` payload instruction that explicitly commands the receiving server to quietly read its local `/etc/shadow` file and echo the contents back out in the XML response. To definitively stop this XML External Entity (XXE) attack, what single secure configuration must the developer apply to the XML Parser?**
**(在一個這年頭還頻繁且大口大口吞吐各路廠商丟上來那種老掉牙『標準 XML 電子交換檔表單包裹』的封閉 B2B 生態鏈中。某天，一位神祕魔鬼偷偷投餵了一張長得毫無破綻，卻被暗自縫進了一條『血淋淋惡毒招魂指令 (`<!ENTITY>`)』的魔改版 XML 表單巨獸。這條在包裹深處的惡毒死令，正大聲且霸道地發號施令，強迫那台自以為在乖乖收件拆信的傻伺服主機，【乖乖轉身摸黑走入地牢，把自家主機機房裡的『最高國家機密死亡名單檔案 (`/etc/shadow`)』給順手牽羊整個拿出來，然後當作收據包裹一併吐回去寄給這魔鬼】！若想要在這個『老套 XML 實體神隱招妖巨浪攻擊 (XML External Entity (XXE) attack)』中保住這最後江山，工程師只需用最後一口氣在 XML 破文字解譯器 (XML Parser) 上拉下哪【單獨唯一一座設定機關大閘】就能定乾坤？)**
A. Delete all XML files after processing them. (只在包裹拆完信讀完內容的五秒後，迅速且無用地將這被詛咒的實體 XML 檔案銷毀)
B. Force the XML parser to run via HTTPS only. (強硬死逼這解毒器 parser 在工作時一定要套上防風大衣 HTTPS 的名義結界才幹活)
C. Completely and totally disable the resolution of Document Type Definitions (DTDs) and External Entities within the XML parsing engine's configuration. (展現最殘暴的手段：死闖進去 XML 這個無腦解析引擎的大總管設定開關裡！【全面性、徹底且殘暴地去物理大絕育！關閉且封殺摧毀引擎中那本會自作主張幫人解籤抽字、聯結宇宙外部事物的『文件資料型態大預言書 (DTDs) 與所有外掛擴展魔靈 (External Entities)』的神經迴路】！！)
D. Encode the XML as JSON before reading it. (把死灰復燃的 XML 在讀的時候全部轉塗成 JSON 的樣子來自欺欺人)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「XXE (XML 外部實體注入攻擊)」** 是在 OWASP 榜上有名的毒蠍漏洞。它發生在你的伺服器收到別人上傳的 XML 檔案並解讀它時。XML 這個古董語言有一個超瞎的霸王功能叫 "External Entity (外部實體)"。駭客可以在 XML 檔頭寫下一句宣告：「我宣告一個常數變數名為 A，它代表這台伺服器本機的 `/etc/passwd` 密碼檔的內容」。當可悲的 Java/PHP XML 分析器 (Parser) 看到這句話時，它居然【真的會乖乖跑到作業系統後台】，把密碼檔抽出來並取代到那份 XML 裡面！導致駭客能看光伺服器整台硬碟。
    *   **唯一仙丹修復法：** 你絕對不該期待骇客會乖乖遵守好孩子規則。在現代的網路應用實作中，工程師必須在呼叫宣告 XML 解析器 (如 Java `DocumentBuilderFactory`) 時，多寫兩行設定去【把 "DTD (Document Type Definition)" 跟 "External Entities" 功能這兩個禍害王八蛋從底層直接徹底「關閉 (Disable / False)」】。我們只要它單純解析字串，絕對不允許它多管閒事去作業系統裡調檔案。斬斷 parser 的這個功能，XXE 攻擊就徹底失效了。

#### **17. A malicious scam website quietly loads a legitimate, fully functional banking portal inside a completely invisible, transparent `<iframe>`. The malicious site places a fake HTML button titled "Click Here to Win an iPhone!" exactly hovering over where the invisible bank's real "Confirm Wire Transfer of $10,000" button sits. When the greedy user vigorously clicks to win the phone, their mouse physically clicks the hidden bank's button instead, executing the transfer. What HTTP Response Header MUST the banking application implement to prevent its site from being hijacked in this manner?**
**(在這個暗無天日、專門吸乾人的詐騙農場鬼屋裡，駭客展開了一張如鬼魅般的魔法布幕：他用一個【肉眼絕對看不見、隱形度 100% 的玻璃窗戶 (`<iframe>`)】，暗渡陳倉地把一整個活生生、功能強大的『正牌銀行金庫轉帳大廳網頁』給神兵天降拉滿在受害者的瀏覽器畫面裡！接著，駭客在自己那層骯髒大網頁外層畫上一顆寫著『點這邊！一秒大抽獎拿金光閃閃最新 iPhone！』的假按鈕。這顆該死按鈕的物理擺放位置，居然絲毫不差地【跟那看不見的銀行底層那顆原本寫著「按此死認簽字匯出並過戶十萬美金給駭客戶頭」真實死亡大炸彈，分毫不差重疊在了一起】！這時貪婪的愚民興沖沖地奮力點下抽獎的瞬間，那隻手其實是直直戳穿圖層，直接壓上了隱形銀行金庫大發財車的點火按鈕執行了轉帳。請問那家受害的正牌大銀行，為了斬草除根去防止自家光榮門面不被抓去這等骯髒小網站裡面做賊利用，他在大門口發誓【絕對不能少掉、且必須釘死掛上】的那塊宣告天下誰也不准偷抱我家的神聖 HTTP 回傳擋煞符咒看板 (Response Header) 到底叫什麼？)**
A. `Strict-Transport-Security: max-age=31536000` (釘滿神符：這個伺服器絕對只准穿戴 HTTPS 甲冑不許脫掉)
B. `Cache-Control: no-cache` (不准用昨天快取，都給我乖乖重去大金庫討新檔)
C. `X-Frame-Options: DENY` (or the modern Content Security Policy `frame-ancestors` directive). (死守鐵律：掛上那聲若驚雷般的絕對禁止神符『X-Frame-Options: 禁斷 (DENY)』！或是新時代的新星死神大咒語『內容安全政策標配：祖宗八代都不准包我的框 (CSP `frame-ancestors` directive)』！誰敢用 iframe 綁架載入我家正門，這符咒立刻引爆碎裂並拒絕顯現顯示畫面)
D. `Access-Control-Allow-Origin: *` (開啟地獄大隨意：讓八方外人全都可以狂飆借用我家水電的放蕩通行證)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這個在透明墊板下面點按鈕的邪惡攻擊，在江湖上大名鼎鼎，名喚 **Clickjacking (點擊劫持 / UI Redressing)**。這是一種讓受害者在神智清醒的情況下，被視覺騙術引導點下了會讓他傾家蕩產的按鈕的視覺 UI 刺殺術。
    *   **唯一的終極守門法：** 作為一家受保護防護的銀行，你無法阻止駭客蓋詐騙網站，但你【可以】宣告自己的這張網頁臉龐「禁止被任何第三方網站用 `<frame>`, `<iframe>` 給偷渡嵌入渲染在他們的網頁上」。在工程實作上，你只需要在伺服器吐出回應時，在標頭加上 **`X-Frame-Options: DENY` (不准任何人包覆我)** 或是 `SAMEORIGIN` (只准我自己同網域的網頁包我)。當瀏覽器收到這個標頭，它就會鐵腕拒絕在駭客的透明 iframe 裡畫出這張網頁。現代更標準的進階作法是寫進 **CSP (Content Security Policy)** 裡面的 `frame-ancestors 'none'` 語法。當銀行加上這道符，駭客的隱形框就直接碎裂變成一堵報錯白牆，點擊劫持術瞬間破產。

#### **18. A modern web application features a dynamic tool where a user can provide a URL, and the server backend will proactively reach out, fetch the image from that URL, and securely crop it to display as their profile picture. An attacker realizes this, and instead of an image URL, they provide the string `http://169.254.169.254/latest/meta-data/`. The backend server blindly reaches out to this internal IP address and successfully fetches and returns the AWS cloud server's highly privileged, secret IAM temporary execution keys back to the attacker's screen. What specific implementation vulnerability was exploited here?**
**(一支風靡萬千少男少女的前衛潮流 App 平台大站，推出了一項超屌的客製化自訂大頭貼功能：「鄉民貴客們喔！只要你丟一張放在外頭網際網路路邊的網址 (URL) 過來，我們家裡位處深宮大院深處那台強而有力的霸主伺服大主機，【就會像溫柔女僕般，自動親身跑出門，乖乖跑腿去你指點的那條明路那裡把圖片搬回家，再幫你裁出完美大頭照幫你換上貼出來展示】」。豈知！一個無所不用其極的流氓駭客看穿了這個傻氣大方的佛心服務！他不丟什麼色情圖片網址，他居然給了這隻伺服器主機一條指向他自己內衣口袋的神祕瞎網址字串：『`http://169.254.169.254/latest/meta-data/`』！！這頭笨驢主機竟然也毫無判斷防備地照跑不誤，它就直端端伸進了這個只存在在雲端機房裡、專門儲藏雲端上帝設定身分秘寶的最禁忌內網暗房裡！並成功連本帶利、將這公司祖傳的『AWS 雲端上帝大上帝賦予的強權限無上最高機密暫時執行令牌金鑰權杖 (IAM EC2 Keys)』給一把扯下、並在截圖裁切畫面中大搖大擺如呈堂證物般印給了那坐在電腦前笑到流眼淚的駭客看個精光！！請問這場悲慘引狼入室、連帶陪葬底褲全脫的災難名詞被稱呼為什麼？)**
A. Server-Side Request Forgery (SSRF) (把自家的大總管變成瞎眼奴才幫駭客做免費壞事跑腿代購的【伺服器端請求跨域代購大偽造術 (SSRF)】！)
B. Client-Side Request Forgery (CSRF) (客戶端在不甘不願下被綁架的同捆送出術)
C. Cross-Site Scripting (XSS) (把帶毒小刀跨站給飛撲在別人家螢幕畫面上的 XSS)
D. XML External Entity (XXE) (那個從 XML 小包裹裡爆破偷檔案的古老魔鬼)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 這是雲端時代最具毀滅性、無數大廠曾為之血流成河且名列大毒梟榜單的究極魔法兵器：**「SSRF (Server-Side Request Forgery / 伺服器端請求偽造)」**。這個漏洞的本質是：駭客無法親自走進你家鎖死的機房後台，但是他發現你的伺服器有個功能是「乖乖聽話去外面抓資料 (Fetch URL)」。於是，駭客遞給伺服器一張寫著「去訪問機房內部那台不對網際網路開放、只有你自己人才看得到的內網上帝金庫 (`localhost`, `127.0.0.1` 或者是雲端最著名的特權中繼資料 IP `169.254.169.254`)」。
    *   伺服器就像個毫無防備的僕人，用它這台機房重地身分的「合法通行權證與防火牆暢通無阻內網白名單的無敵狀態」，把內網裡那些不設防的大機密通通搬回來並雙手奉上回傳給外界的駭客。
    *   **實作防禦方式：** 工程師在實作這種 "WebHook" 或是 "代抓下載 URL 檔案" 的功能時，必須在主機去抓檔案那秒前，設置死硬封鎖關卡：【強制攔截封鎖掉所有查出來解析是 `localhost`, `10.x.x.x`, `169.254.x.x` 這類內部不公開 IP 段的解析請求之路】。伺服器只能去外部公共網站取物。
