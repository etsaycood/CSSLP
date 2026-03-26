# 第四套全真模擬試題 (Exam 4) - 答案與詳解本
## 領域 5：安全的軟體實作 (Secure Software Implementation) (18題) - Part 2 (Q7-Q12)

---

#### **7. A developer is tasked with encrypting the network traffic between two internal microservices. They decide to use a custom XOR-based cipher they learned about in a university assignment because it is extremely fast and lightweight. This directly violates which established cryptographic implementation rule?**
**(一名剛被朝廷招安的年輕太學生工匠。他接到了一個幫兩座『內閣秘密藏經閣 (internal microservices)』之間拉一條加密通訊線的任務。這自作聰明的太學生，居然沒去兵器庫裡申請制式裝備。他反而興高采烈地拿出了他當年『在學校裡交期末作業時自己胡亂捏造出來的「太極八卦 XOR 小加密術 (custom XOR-based cipher)」』！這太學生信誓旦旦地發誓：這套陣法雖然簡陋，但它跑起來『比風還要快，比鴻毛還要輕 (fast and lightweight)』！請問，這太學生這種自釀毒酒還洋洋得意的找死行為，是直接觸犯了哪一條會被滿門抄斬的千古密碼學大死律？)**
A. Never reuse Initialization Vectors (IVs). (絕對不能重複使用初始向量 (IV) 是在使用正規軍火裝備 (如 AES-CBC) 時的操作手冊死穴，但這太學生現在連正規軍火都不拿，直接拿自己捏的泥菩薩上陣，這罪過更大)
B. Use asymmetric encryption for bulk data. (非對稱加密因為速度太慢，本來就不能用來加密幾千箱的大量黃金 (bulk data)，這不是這題的焦點)
C. Do not "Roll Your Own Crypto" (adhere to Kerckhoffs's Principle by using vetted algorithms like AES). (這就是那句名垂千古、用無數慘死英靈的鮮血寫成的至高無上大祖訓：【『千古禁忌大斬首令：絕對禁止關起門來自己發明狗屁不通的瞎編密碼鎖 (Don't Roll Your Own Crypto)！』】。這條死律咆哮著：天下所有的私釀酒都是毒藥！一套能被信賴的密碼演算法，必須是那些經歷過全世界最頂尖、最狠毒的數學家與駭客，拿著大刀砍了幾十年都砍不斷的『公開神兵利器 (vetted algorithms)』！而且必須嚴格遵守【『柯克霍夫大原則 (Kerckhoffs's Principle)：這鎖的構造圖你可以大方地公開給全天下看，只要你把【鑰匙 (Key)】藏在褲襠裡，這鎖就絕對不會被撬開！』】。這太學生那套只靠「沒人看過我這套算法 (Security by Obscurity)」的破 XOR 陣法，只要駭客拿到隨便幾段明文跟密文，一秒鐘就能把密鑰反推算出，這就是自尋死路的最經典下場！)
D. Passwords must be hashed, not encrypted. (密碼必須雜湊而不是加密，這是儲存密碼時的規矩 (Data at rest)。這題是在談「網路連線傳輸中 (Data in transit)」的加密通道，兩者戰場不同)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **"Do not roll your own crypto" (不要發明你自己的密碼演算法)** 是資安實作中最基本、最重要的原則之一。
    *   **密碼學設計的難度：** 設計一個安全的密碼演算法極度困難，它需要深厚的數學基礎來抵抗各種已知的攻擊 (如已知明文攻擊 Known-Plaintext Attack, 差分密碼分析 Differential Cryptanalysis)。
    *   **Custom Cipher (自訂加密) 的脆弱性：** 題幹中的 XOR cipher (互斥或運算) 如果只用短的、甚至重複的金鑰 (Key Reuse)，攻擊者只要攔截到密文 (Ciphertext) 並猜出部分明文 (Plaintext，如 HTTP 標頭)，就能用 XOR 的特性 `$Plaintext \oplus $Ciphertext = $Key` 輕易算出金鑰。
    *   **Kerckhoffs's Principle (柯克霍夫原則)：** 一個密碼系統的安全性，必須 **只依賴於金鑰 (Key) 的保密，而不依賴於演算法本身的保密**。換句話說，就算駭客把 AES 的原始碼跟實作論文全看光了，只要他沒有你的 Key，他就解不開你的檔案。自訂演算法通常是 "Security by Obscurity (隱匿式安全)" 的反面教材。

#### **8. Which HTTP response header provides a robust, defense-in-depth mechanism against Cross-Site Scripting (XSS) and data injection attacks by allowing the application to explicitly declare to the browser which dynamic resources (e.g., JavaScript, CSS, Images) are permitted to load and execute?**
**(在防範千古毒王 XSS 跨站劇毒的終極戰場上，除了前面的自動濾毒網外。大會的安防總督還會在每個回覆給客人的包袱皮上，貼上一張名叫『HTTP 防衛令牌 (Response Header)』的神聖公文令！這張公文令上，會密密麻麻地寫著：『聽好！客人你的眼睛 (瀏覽器) 只能看這幾家老字號客棧搬來的布告 (Images)！只能聽這幾個官方說書人講的故事 (JavaScript)！如果有任何躲在角落的小偷，想拿來路不明的破圖畫或毒藥腳本給你看。你的眼睛【必須自動戳瞎它！馬上把這些毒藥給吐掉 (explicitly declare to the browser which dynamic resources are permitted to load and execute)！】』請問。這張能讓客人的眼睛自動排毒、堪稱 XSS 終極防禦大衣的 HTTP 神聖公文令牌，名字叫什麼？)**
A. X-Frame-Options (XFO 是防止網頁被別人用 IFrame 包起來當成釣魚網站按鈕的 Clickjacking 防禦令，不是管腳本執行的)
B. HTTP Strict Transport Security (HSTS) (HSTS 是強制規定「以後只能走 HTTPS 加密隧道」的死命令，它是防竊聽，不是防網頁上跑出毒蘑菇腳本的 XSS)
C. Content Security Policy (CSP) (這就是名震四海、專門用來絞殺 XSS 的：【『《終極內容安全大政策法典 (CSP)》令牌！』】！這道令牌的奧義是：萬一（真的是萬一），前面所有的濾毒網都破洞了，導致一隻惡意的 `<script src="http://evil.com/xss.js">` 成功被印到了使用者的畫面上。只要有了這張 CSP 護身符！使用者的瀏覽器在跑這行腳本前，會先抬頭看一眼公文：『咦？公文上白紙黑字規定《只能執行從我自己家 (self) 來的 JavaScript！』。於是，瀏覽器會直接【一巴掌拍死】這個從 `evil.com` 來的毒藥，連載入都不載入！這就是現代網頁安全中最美麗、最堅固的「縱深防禦大網 (Defense in Depth)」！)
D. Access-Control-Allow-Origin (這是 CORS 放行別家客棧來調閱我家帳本的憑證，這是在「開放權限」，而不是像 CSP 一樣「封殺外來腳本」的保護罩)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **Content Security Policy (CSP)** 是一種電腦安全標準，作為防禦 Cross-Site Scripting (XSS) 和其他資料注入攻擊的「縱深防禦 (Defense in Depth)」機制。
    *   **CSP 的運作原理：** 它的本質是「網站擁有者向瀏覽器下達的白名單政策」。
        *   開發者在 HTTP Response Header 中加入：`Content-Security-Policy: default-src 'self'; img-src https://*.trusted.com; script-src userscripts.example.com`
        *   這個標頭告訴瀏覽器：
            1. 預設情況下，只載入與目前網站同源 (Same-Origin) 的資源。
            2. 圖片只能從 `*.trusted.com` 載入。
            3. JavaScript 只能從 `userscripts.example.com` 載入。
    *   **防禦 XSS 的奇效：** 如果網站有 Stored XSS 漏洞，攻擊者注入了一段 `<script>alert('hack')</script>` (Inline Script) 或是 `<script src="http://hacker.com/steal.js"></script>`。因為 `hacker.com` 不在 CSP 白名單內，且嚴格的 CSP 預設禁止執行任何 Inline Scripts (寫在 HTML 裡的 JS)。瀏覽器會直接封殺 (Block) 並報錯，徹底將 XSS 攻擊的傷害降為零。

#### **9. A senior developer is performing a code review on a junior developer's pull request. The junior developer has implemented a custom error handling routine that catches database connection exceptions and displays the detailed stack trace and SQL query syntax directly on the user's web page so that "users can report exactly what went wrong." What security issue does this represent?**
**(一名滿頭白髮的高階督工，正在檢查一個新兵交上來的『城牆建造報告 (code review)』。當督工看到這新兵寫的【『崩塌應急廣播大系統 (custom error handling routine)』】時，差點沒氣得立刻拔出大刀砍下這笨蛋的腦袋！這蠢蛋新兵的系統是這樣運作的：當後方的大金庫爆炸時。這廣播系統居然會在大庭廣眾之下，對著全天下老百姓的布告欄，一字不漏地印出：【『報告各位鄉親！我家金庫在地下三樓的第 102 號房間！房間密碼是 1234！因為這把密碼鑰匙斷在門裡！而且這個大金庫是用 MySQL 5.7 打造的！上面還有一句語法 Select * 從 users 表格裡崩潰了，所以現在門打不開啦 (displays detailed stack trace and SQL query)！請大家拿著這張廣播單來告訴我哪裡壞了！』】！請問！這新兵愚蠢至極、把家裡底褲全脫光的設計，是犯了兵家哪一條不可饒恕的洩密大忌？)**
A. It fails to implement input validation. (這是在系統壞掉後的「輸出廣播」，不是在檢查進門的「輸入驗證」，兩者階段相反)
B. It causes a Denial of Service. (這廣播單雖然蠢，但它不會把城牆弄塌，只是把情報全抖光，不會造成整體服務死亡)
C. It results in sensitive Information Disclosure (Information Leakage) which aids attackers in mapping the backend infrastructure. (這就是讓全天下間諜笑掉大牙、拱手把城門鑰匙送人的：【『極限智障級敏感資訊大洩漏 (Information Disclosure / Information Leakage)！』】。這隻魔鬼的奧義叫做：「幫駭客畫藏寶圖」。駭客最怕的就是瞎子摸象。但這份包含著【『追溯大列表 (Stack Trace)』與『資料庫語法 (SQL query syntax)』】的廣播單，等於直接把「這皇宮的地基適用什麼版本的水泥 (OS/DB Version)？金庫藏在哪個資料夾 (File Paths)？有哪些現成的後門可以鑽 (Vulnerable Library Versions)？」這些極機密情報，無料放送給全天下的駭客！駭客看到這廣播單，直接翻開字典，三秒鐘就能找到攻破你這座城的專屬炸藥！這是極度危險的底層洩密！)
D. It violates the Rule of Least Astonishment. (最小驚訝原則是使用者敲了一下鐘，跳出兩隻猴子，這只會讓人困惑。而這廣播單是引狼入室會滅國的洩密死罪，不是困惑這麼簡單)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是對 **「不當的錯誤處理 (Improper Error Handling)」** 導致 **「資訊洩露 (Information Disclosure/Leakage)」** 最經典的範例。
    *   **Stack Trace 的價值：** 開發環境中的 "Stack Trace" (堆疊追蹤資訊) 與詳細的資料庫錯誤訊息 (如 "Syntax error near 'admin...' in MySQL line 1")，對開發者除錯 (Debugging) 來說是無價之寶。
    *   **但對駭客而言更是無價之寶 (Fingerprinting/Reconnaissance)：**
        *   它能洩漏系統使用了哪種資料庫 (MySQL, PostgreSQL, Oracle)。
        *   它能洩漏真實的作業系統實體檔案路徑 (e.g., `C:\inetpub\wwwroot\app\login.php`)。
        *   它能洩漏使用的後端框架版本 (e.g., 暴露正在使用一個有遠端代碼執行漏洞的舊版 Apache Struts)。
    *   **安全實作 (Remediation)：** 在正式營運環境 (Production Environment) 中，**絕對禁止**顯示詳細的錯誤訊息。必須實作通用的錯誤處理網頁 (Default Error Page)。只顯示：「系統發生錯誤，請稍後再試 (HTTP 500)」。而把詳細的 Stack Trace 記錄在駭客看不到的後端唯讀系統日誌 (System Logs) 中。

#### **10. When implementing session management for a web application, a developer sets the session cookie upon successful login. To ensure the cookie is protected against interception via JavaScript (XSS) and network sniffing, which two essential cookie attributes MUST the developer configure?**
**(一名老練的守門官，正在打造皇城裡最神聖、能讓老百姓免除每天搜身之苦的『通行大狗牌 (session cookie)』。當老百姓登入成功後，守門官會把這張狗牌掛在老百姓脖子上。但是！為了防範城外那些潛伏的流氓 (XSS)，在路邊叫囂想把老百姓脖子上的狗牌給偷走看！更為了防範那些躲在樹上的間諜 (network sniffing)，在沒有拉上加密窗簾的大馬路上偷抄狗牌的號碼！請問，守門官在掛上這張狗牌時，必須要像寫符咒一樣，在這狗牌上【同時】烙印下哪兩道讓強盜與間諜都碰不到的『終極大護身符指令 (essential cookie attributes)』？)**
A. `Secure` and `HttpOnly` (這就是保衛大狗牌萬世無虞的：【『雙龍護主之【加密隧道專用大鐵鍊 (Secure)】與【瞎眼絕緣罩 (HttpOnly)】大護身符咒！』】。這兩道符咒各有各的防守領域：【`Secure` 大印章規定】這張狗牌，【只准、也絕對只能】透過那個拉上加密窗簾的防彈隧道 (HTTPS) 傳遞給城牆！只要有人敢用沒加密的明文 (HTTP) 傳這張牌，這牌子會立刻自毀，這讓躲在樹上偷聽的間諜絕望！而【`HttpOnly` 大眼罩】更是神奇，它對這張狗牌施加了封印，讓這張狗牌【只能在信封裡寄給伺服器，路邊一切的阿貓阿狗，甚至是跑在網頁上的 JavaScript 腳本大俠，這輩子連看都看不到這張牌 (防範 XSS 去讀取 `document.cookie` 偷狗牌)！】這也是現代保衛登入令牌最標準、不可缺少的雙重盔甲！)
B. `Domain` and `Path` (網域和路徑是告訴這張狗牌「哪幾條巷子的店家可以收這牌子」，它是控制發送範圍，但這些巷子上的流氓還是能抄襲跟偷看，這並不是用來阻擋偷窺與連線竊聽的終極防禦兵器)
C. `Expires` and `Max-Age` (過期日跟期限是告訴這狗牌「三天後你就會自動粉碎失效」，但這管不了在這三天內，這狗牌會不會被路邊的強盜 (XSS) 給偷走拿去幹壞事)
D. `SameSite` and `HostOnly` (`SameSite` 是阻擋 CSRF 隔山打牛的神藥，但沒辦法防止這張牌因為沒加密而被偷看。而保護機密與 XSS 的老大哥還是 Secure 跟 HttpOnly)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **`Secure`** 與 **`HttpOnly`** 是 Session Cookie 實作中保護 **「機密性」** 與 **「抗竊取」** 必不可少的兩大黃金屬性 (Cookie Flags)。
    *   **防禦 Network Sniffing (網路監聽/中間人攻擊)：**
        *   **`Secure` 屬性：** 告訴瀏覽器：「這個 Cookie 是極機密。你【只能】在建立安全的 HTTPS 連線時，才能把它夾帶在 Request 裡送出去。如果使用者在網址列不小心打了 HTTP 結尾的網址，不准送出這個 Cookie」。這保證了 Cookie 不會在明文網路中裸奔。
    *   **防禦 XSS (跨站腳本攻擊) 竊取 Session：**
        *   **`HttpOnly` 屬性：** 一個沒有設定 HttpOnly 的 Cookie，可以被客戶端的 JavaScript 腳本 (透過 `document.cookie`) 輕易讀取。如果網站有 XSS 漏洞，駭客寫了一隻惡意腳本，這腳本會把讀到的 `document.cookie` (這也就是 Session ID) 偷偷傳給駭客的伺服器 (Session Hijacking/會話劫持)。
        *   設定 `HttpOnly` 後，瀏覽器會在底層將這個 Cookie "鎖死" 對 JavaScript 的可見性。惡意的 XSS 腳本執行 `document.cookie` 時，會得到一片空白。只有瀏覽器底層真正在發送 HTTP 請求時，才會自動把它夾帶放入 Header。這完美阻絕了 XSS 偷取 Session 的行為。

#### **11. A developer is writing a file upload mechanism that allows users to submit PDF receipts. To prevent malicious users from uploading executable web shells (e.g., `.php` or `.jsp` files) and compromising the server, which of the following is the MOST secure implementation strategy?**
**(一名老鐵匠正在打造一個『全天下老百姓客棧帳單投入口 (file upload mechanism)』。老鐵匠只准老百姓丟進那種名為『只能看不能動的紙本大卷宗 (PDF receipts)』。但是！老鐵匠深知江湖險惡：如果有一群喪心病狂的巫師，偷偷在這個投入口裡，丟進了一顆名為【『點火就會炸毀皇城的魔法大皮球 (.php 或是 .jsp web shells)』】！只要伺服器傻傻地把它當成皮球去踢 (Execute)，整座皇城就會瞬間落入駭客魔爪 (compromising the server)！請問，為了打造這座堅不可摧的防爆口，老鐵匠到底該祭出哪一套『終極滴水不漏搜身防護大連環陣 (MOST secure implementation strategy)』？)**
A. Use a black-list to reject files ending in `.php`, `.exe`, or `.sh`. (黑名單是天下最蠢的『打地鼠遊戲』！如果你擋了 .php，駭客就會上傳 .php2, .php3, .phtml。駭客永遠能源源不絕想出新名字來繞過你那張薄薄的黑名單，這注定失敗)
B. Rely solely on checking the `Content-Type` header sent by the user's browser (e.g., `application/pdf`). (你居然敢相信駭客遞給你的那張名片 (Content-Type)！？駭客可以輕易把炸彈的包裝盒外面貼上一張寫著「我是可愛無害 PDF」的貼紙！這只能騙過三歲小孩的機器守衛，純依賴這個是找死的行為)
C. Implement a strict white-list of allowed extensions (e.g., ONLY `.pdf`), verify the file's "magic bytes" (file signature) matches a PDF, and store the uploaded files outside the web root directory or in an isolated object storage bucket (e.g., AWS S3). (這就是能讓全天下魔法大皮球絕望哭泣的：【『無敵三連環絕殺防線大結界：白名單封鎖 (White-list) + 靈魂血統大檢驗 (Magic Bytes) + 地外孤島無菌大放逐 (Store outside web root/S3)！』】。第一關：老子不在乎你叫什麼，老子只規定【除了名字帶 '.pdf' 以外的所有東西通通給我滾】！這叫白名單！第二關：你光叫 '.pdf' 還不夠！老子要去扒開這檔案頭頂最深處的那幾根頭髮 (Magic Bytes/File Signature)。如果這幾根頭髮不是長成 PDF 該有的基因密碼，立刻把這假貨丟下護城河！第三關最狠：就算你偽裝術天下無敵進城了。老子也不把你跟皇帝擺在同一個皇宮裡 (web root)。老子直接把你丟去幾千公里外、那片連魔法都飛不起來的荒野無人沙漠 (AWS S3) 去關禁閉！這種沙漠就算給你火柴 (駭客打網址執行)，這死沙漠因為不會幫你解析 PHP(.php)，你也絕對引爆不了炸彈！這是一套徹底斬草除根的最強實作兵法！)
D. Scan the uploaded file with an antivirus signature database. (防毒軟體只是對照通緝犯名單，只要駭客今天自己寫了一隻全新的菜刀木馬大炸彈 (Zero-day web shell)，防毒軟體照樣會像瞎子一樣把它放進城裡引爆)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是實作 **安全檔案上傳 (Secure File Upload)** 的黃金標準與「縱深防禦 (Defense-in-Depth)」最佳實踐。
    *   **檔案上傳的致命威脅：** 如果允許使用者上傳 Web Shell (例如惡意的 `shell.php`) 到可以被外網直接執行的網頁目錄 (Web Root，如 `/var/www/html/uploads/`)。攻擊者只要打開瀏覽器輸入 `http://example.com/uploads/shell.php?cmd=whoami`，就能拿到主機的控制權 (Remote Code Execution, RCE)。
    *   **三道不敗防線 (The Three-Pillared Defense)：**
        1.  **Whitelisting (白名單)：** 絕對不要用黑名單。只允許確切需要的副檔名 (例如 `if (ext !== '.pdf') throw Error;`)。
        2.  **Magic Bytes (魔術數字/檔案簽章) 驗證：** 駭客可以把 `shell.php` 改名成 `shell.pdf` 上傳。為了防禦這個，後端程式必須讀取檔案的**最前面幾個位元組 (File Headers/Magic Bytes)**。真正的 PDF 檔案，開頭絕對是 `%PDF-` (Hex: `25 50 44 46 2D`)。如果副檔名是 PDF，但 Magic Bytes 是 `<?php`，就立即刪除。(不過即便如此，駭客可用 Polyglot 檔案繞過，所以需要第三關)。
        3.  **隔離儲存 (Isolated Storage)：** 這是殺手鐧。將上傳的檔案儲存在**「無法執行任何程式碼」**的地方。例如作業系統中遠離 Web Root (如 `/tmp/`，使用者無法透過 HTTP 直接存取目錄)，或者更好的做法是上傳到 Cloud Object Storage (如 AWS S3, Azure Blob)。因為 S3 本質上就是個 "檔案倉庫"，它沒有安裝 PHP/Java/Node 引擎，就算駭客手段通天傳了隻木馬上去。這隻木馬也絕對不可能在 S3 的環境裡被「執行 (Execute)」，它就只能是一坨無害的靜態文字檔。這徹底消滅了 RCE 威脅。

#### **12. In the context of secure software implementation, what is the primary purpose of a "Static Application Security Testing" (SAST) tool integrated into the developer's Integrated Development Environment (IDE)?**
**(在所有工匠夢寐以求的『鍛造大兵器庫 (Secure Software Implementation)』裡。有一尊被大將軍重金禮聘，直接安裝在每一個底層工匠打鐵桌子旁邊的：【『血紅大眼透視顯微鏡 / SAST 神眼』】！這顆神眼跟那個坐在大門口收成品驗收的大太監不一樣！這大眼直接死死盯著工匠手上正在敲打的那塊鐵板 (integrated into the IDE)！請問，花大錢買這尊擺在打鐵桌上的紅眼神像，其最精於盤算、且號稱能省下百座金庫的最冷血目的到底為何？)**
A. To automatically deploy the code to a staging server. (這神眼是挑骨頭找蟲子的，不是做搬運工作推木車的運輸大隊 (CI/CD Deployment Tool))
B. To perform automated functional UI testing simulating a user clicking buttons in a browser. (模擬人類點點點滑鼠看會不會死機，這叫動態測試黑箱機器人 (DAST/Selenium 黑箱)。這尊裝在工匠桌上的神眼 (SAST)，沒有跑起來的畫面，它連滑鼠是什麼都不知道，它只會一行行看源碼！)
C. To analyze the source code for known security vulnerabilities (e.g., hardcoded secrets, SQL injection patterns) at the exact moment the developer is writing the code, enabling real-time feedback and "Shift-Left" security. (這就是『萬惡淵藪消滅於草稿紙上』的最強奧義：【『極限左移之實時顯微鏡大審判 (real-time feedback and Shift-Left security)！』】。這顆神眼 (SAST in IDE/Linting) 的本質是「白箱」。它強悍的地方在於：在老工匠還在打字、還沒有按下存檔把這張紙送出家門的【『那一瞬間 (at the exact moment developer is writing the code)』】！神眼會掃描這幾行墨水，並且瘋狂拉響警報：『警告！警告！你這行字是用單引號亂黏出來的 (SQL Injection patterns)！你這白痴還把皇帝密碼大剌剌寫在變數裡 (hardcoded secrets)！不改掉就不准你離開書桌！』。因為這隻蟲子甚至還沒有活著走出這間辦公室，它就已經被工匠在一秒內撿起來踩死。這把修改漏洞的時間成本，極致壓縮為零！這是現代防護最強的『左移殺敵大真理』！)
D. To monitor the application's memory usage in the production environment. (這神眼裝在工匠桌上，不是裝在皇帝已經去出征的深山金庫戰場上 (production environment)。在戰場上看記憶體那是 APM (Application Performance Monitoring) 的工作，這兩者八竿子打不著)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是對 **「靜態應用程式安全測試 (SAST, Static Application Security Testing)」在整合開發環境 (IDE)** 中應用的最精確定義。
    *   **SAST 的特性 (White-Box)：** 它不需要編譯 (或只需要部分)，也不需要讓程式「跑」起來。它是在 "靜止狀態 (Static)" 透過建立 AST (抽象語法樹) 或控制流分析 (Control Flow Analysis) 去搜尋已知的漏洞模式。
    *   **IDE Plugin 的戰略意義：極限左移 (Shift-Left)。**
        *   傳統上，SAST 裝在 Pipeline 中 (CI)。開發者 Push Code，去喝咖啡等 20 分鐘才看到 SAST 報告說 "Failed"。這時 Context Switching (上下文切換) 的成本已經產生。
        *   SAST 安裝在 IDE (如 SonarLint, Checkmarx IDE Plugin)。就像一個資安老兵坐在開發者旁邊結對程式設計 (Pair Programming)。在開發者剛寫下 `DriverManager.getConnection(url, "admin", "password");` 的那一刻，螢幕上就出現波浪紅線警告他。這樣能以最高效率將問題阻絕在程式碼生命週期的最起點。
