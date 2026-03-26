# 第三套全真模擬試題 (Exam 3) - 答案與詳解本
## 領域 5：安全的軟體實作 (Secure Software Implementation) (18題) - Part 1 (Q1-Q9)

---

#### **1. A developer is writing code to authenticate users against a backend database. The developer constructs the query dynamically by concatenating the user's input directly into the SQL string like this: `query = "SELECT * FROM users WHERE username = '" + user_input + "' AND password = '" + pass_input + "'"`. To definitively eliminate the risk of a hacker injecting malicious SQL commands (SQL Injection) via `user_input`, which specific coding technique MUST the developer implement instead of string concatenation?**
**(一名菜鳥工程師正在撰寫讓客人刷臉登入後台大金庫資料庫的驗證程式碼。這名笨蛋居然用最原始且最致命的『字串無腦拼接大法 (dynamically concatenating)』來拼湊他要對資料庫下達的 SQL 神聖指令，他的程式碼長這樣：『`指令 = "給我拿出所有資料，只要帳號等於 ['" + 客人輸入的字 + "'] 並且密碼等於..."`』。請問！為了要【徹徹底底地從根本的物理法則上、一次性永遠消滅掉】任何駭客企圖透過那個 `客人輸入的字` 欄位，偷偷塞進『惡意 SQL 毀滅指令 (SQL Injection)』的喪膽風險！這名工程師絕對必須立刻拋棄字串拼接，改用哪一種最神聖的【防注射裝甲寫法技術】？)**
A. Encode the user input using Base64 before concatenation. (把駭客的字串用 Base64 重新包裝一次再拼接，這根本就是脫褲子放屁，資料庫解碼後一樣會被注入死得很慘)
B. Implement client-side JavaScript validation to block single quotes. (只在客人的瀏覽器上用 JavaScript 寫個小檢查擋掉單引號。駭客只要把瀏覽器關掉，直接用工具打 API 就輕鬆繞過這層紙糊的防線)
C. Utilize Parameterized Queries (Prepared Statements) provided by the database driver. (這就是能徹底宣判 SQL Injection 歷史死刑的終極防禦大絕招：【全面強制換裝由資料庫原廠驅動程式所提供的『參數化查詢 / 預存語句大鋼板 (Parameterized Queries / Prepared Statements)』】！)
D. Hash the SQL query before sending it to the database. (把整個 SQL 指令拿去雜湊絞碎，這樣資料庫根本看不懂你在幹嘛，系統直接當機罷工)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是資安界對抗 **SQL Injection (SQL 隱碼攻擊)** 的**唯一黃金標準與終極解法**。
    *   **舊式字串拼接的致命傷：** 駭客如果在 `user_input` 裡輸入 `' OR '1'='1`。拼出來的 SQL 語法就會變成 `SELECT * FROM users WHERE username = '' OR '1'='1' AND password = ''`。因為 `1=1` 永遠成立，駭客不需要密碼就能直接把整個資料庫倒出來登入成功。
    *   **Parameterized Queries (參數化查詢) 的神聖防禦：** 開發者不再自己拼字串。而是先把 SQL 的「骨架」丟給資料庫編譯好 (例如 `SELECT * FROM users WHERE username = ?`)。然後才把駭客送來的字串當作「純粹的、毫無殺傷力的資料肉塊」塞進那個 `?` 的洞裡。資料庫此時已經編譯完骨架了，所以就算駭客塞了破壞性的單引號 `'` 或是 `OR 1=1`，資料庫也會把它當作 "一個名字叫做 `' OR '1'='1` 的奇葩使用者名字" 去搜尋，而絕對不會把它當成 "神聖的 SQL 執行指令" 來執行。這從語法解析樹的根本上，徹底拔除了駭客指令被執行的可能性。

#### **2. While reviewing the source code of a C++ application, a security auditor notices that the programmer is using the `strcpy()` function to copy user-supplied input into a fixed-size character array (buffer) of 128 bytes, without checking if the input actually exceeds 128 bytes. This classic coding error directly exposes the application to which critical vulnerability that could lead to remote code execution?**
**(在拿著放大鏡審查一款 C++ 古老系統的原始程式碼大會上，一位目光如炬的安檢老將，猛然倒抽了一口涼氣！他驚訝地發現那個寫程式的傢伙，居然還在使用那聲名狼藉、猶如自殺炸彈般的古老複製函數 `strcpy()`！這傢伙居然把路人隨便輸入的字串包裹，盲目且粗暴地往一個【容量絕對寫死、只能裝得下區區 128 bytes 的小鐵盒記憶體陣列 (fixed-size character array / buffer) 裡面死命地塞！而且完全沒有寫半行去檢查客人送來的包裹是不是比 128 bytes 還要巨大的防呆程式碼 (without checking if input exceeds 128 bytes)】！請問這等連一年級新生都會被當掉的經典低級寫法錯誤，將會大方地向死神敞開大門，直接引爆下面哪一場足以讓駭客直接在你的電腦裡遠端執行任意木馬程式 (RCE) 的毀滅性浩劫？)**
A. Cross-Site Scripting (XSS) (這只是在網頁上跳出小彈窗騙人的跨站腳本術，C++ 桌面程式比較不怕這個)
B. Buffer Overflow (Stack/Heap Overflow) (這就是名震百代、因為硬塞太多東西把記憶體鐵皮箱當場撐爆，導致內臟跟毒藥流滿整個電腦主機板的【記憶體緩衝區溢位大爆炸 (Buffer Overflow / 包含堆疊或堆積溢位)】！)
C. Cross-Site Request Forgery (CSRF) (那是騙你網頁點按鈕的偽造請求)
D. XML External Entity (XXE) Injection (那是 XML 解析器讀錯檔案的把戲)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「緩衝區溢位 (Buffer Overflow)」** 是 C/C++ 等底層語言最經典、最致命的漏洞 (在 Memory-Safe 語言如 Java/C# 中較少見)。
    *   **漏洞原理：** 記憶體中的一個變數 (Buffer) 只有 128 bytes 的空間。駭客故意輸入 500 bytes 的長字串 (例如長達 500 個字母 'A')。因為 `strcpy()` 這個老函數很笨，它不會檢查目標空間夠不夠大，它會閉著眼睛把 500 個 'A' 全部塞進去。
    *   **災難後果：** 多出來的那 372 個 bytes，會溢出 (Overflow) 原本的鐵盒，流到旁邊系統正在執行的記憶體區塊裡。駭客可以精心設計這多出來的 372 bytes 裡面夾帶惡意機器碼 (Shellcode)，並且覆寫掉系統的「回傳地址指標 (Return Address)」。當系統執行到這裡時，就會被駭客綁架，轉為去執行駭客的木馬病毒 (導致 Remote Code Execution，RCE)。

#### **3. A web application displays a personalized greeting using the user's profile name, which they previously entered into a text field. The backend PHP code simply reads the name from the database and directly echoes it into the HTML page: `<h1>Welcome, <?php echo $profile_name; ?></h1>`. If a malicious user entered `<script>alert('Stealing cookies!')</script>` as their profile name, this code would execute in every other user's browser who views their profile. What is the fundamental, mandatory defensive implementation required to neutralize this vulnerability?**
**(有一個看似貼心的個人網頁，在你登入時會熱情地在大螢幕上印出你的名字來歡迎你。這個名字是你在註冊時自己輸入的。然而，後台那破爛的 PHP 程式碼，居然只是個無腦的傳聲筒：它從資料庫裡把你的名字挖出來後，【完全不經過任何清洗消毒，就連名帶姓直接把它活生生地吐死 (echo) 在網頁的 HTML 骨架上：`<h1>Welcome, <?php echo $profile_name; ?></h1>`】！如果有個心腸歹毒的駭客，在註冊時故意把他的姓名填成一段劇毒的網頁執行咒語：`<script>alert('Stealing cookies!')</script>`。那當其他無辜的老百姓點進來看這個駭客的首頁時，他們瀏覽器就會不假思索地把這段名字當成神聖的指令直接執行，然後全家的身分證餅乾 (cookies) 就被強制偷送走了！請問，要徹底封殺這種讓網頁中毒的瘟疫，工程師在印出名字之前，【絕對必須、強制性地加上】哪一道猶如消毒水洗澡般的防禦加工手續？)**
A. Encrypt the profile name in the database using AES-256. (就算加密存在資料庫，拿出來要秀在網頁上給人看的時候還是一段有毒的明文，這完全搞錯防禦方向)
B. Implement an IPSec VPN for all users. (叫所有用網頁的人去架設老土的 VPN 也是白搭)
C. Apply strict Context-Aware Output Encoding (e.g., HTML Entity Encoding) before rendering the data in the browser. (這就是破解此等妖術的唯一神聖洗禮：【在要把任何外來的髒東西吐出顯示在網頁畫面上之前！【必須】發動極為嚴苛的『具備語境感知的輸出安全編碼大轉換 (Context-Aware Output Encoding / 也就是把危險字元變成標籤實體 HTML Entity Encoding)』】！把危險的刀劍全部包上安全氣囊！)
D. Change the database to a NoSQL database system. (換資料庫完全無濟於事，那是用來解決不同問題的)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是針對 **Cross-Site Scripting (XSS, 跨站腳本攻擊 - 特別是 Stored XSS)** 唯一的標準防線。
    *   **XSS 原理：** 瀏覽器很笨，它如果看到 `<script>` 標籤，它就會認為「這是程式碼，我要執行它」。所以當駭客把自己的名字設成惡意程式碼時，無辜用戶的瀏覽器就會中招。
    *   **Output Encoding (輸出編碼) 的防禦魔術：** 在把名字顯示給用戶看之前，系統必須呼叫編碼函數 (例如 PHP 的 `htmlspecialchars()`)。這個函數會把駭客輸入的有毒標籤符號 `<` 和 `>`，**翻譯 (編碼)** 成無害的純文字顯示代碼 `&lt;` 和 `&gt;`。
    *   **結果：** 當這串編碼過的名字送到無辜用戶的瀏覽器時，瀏覽器只會把它當成 "一段長得很奇怪的純文字" 顯示在畫面上，而【絕對不會】啟動它內部的 JavaScript 執行引擎 (引擎看到 `&lt;script` 不會把它當作 `<script>` 指令)。這完美剝奪了駭客程式碼的殺傷力。

#### **4. A massive data breach investigation reveals that hackers compromised a company's AWS cloud infrastructure. The root cause was traced back to a junior developer who accidentally committed a file named `config.json` into the public, open-source GitHub repository. This file contained the live, production AWS Access Key ID and Secret Access Key. Which secure implementation practice completely prevents this catastrophic scenario?**
**(在一場屍橫遍野、整座大企業的 AWS 雲端帝國被駭客燒成焦土的天大慘劇調查報告中。所有的線索，最終都指向了那名還在流鼻涕的菜鳥工程師！這傢伙在昨天下班前，居然不小心手滑，把他電腦裡一個叫做 `config.json` 的破爛文字檔，給大門敞開地按下了送出鍵 (committed)，上傳到了那個全地球駭客跟路人都正在瞪眼圍觀的 GitHub 開源大廣場上！要命的是，這個破檔案裡面，居然！清清楚楚地印著兩行字：【那是能直接開走他們家最高層級 AWS 雲端金庫的『活體正式營運之真神大鑰匙 (live, production AWS Access Key ID and Secret Access Key)』！】。請問這等猶如把國家金庫總鑰匙貼在火車站佈告欄上的低級死罪慘劇。若是這家公司當初有乖乖聽從哪一道『軟體安全實作最高防禦大紀律』，就能百分之百、徹底抹殺這種悲劇的發生？)**
A. Using a Software Composition Analysis (SCA) tool on the Git repository. (SCA 只是幫你查有沒有用到發霉的過期免費開源軟體，它不是用來抓鑰匙的)
B. Externalizing secrets and managing them via a secure Secrets Management Vault (e.g., HashiCorp Vault, AWS Secrets Manager, Azure Key Vault) injecting them as environment variables at runtime, keeping them entirely out of the source code. (這就是防範白痴手滑的終極隔離大陣：【逼迫全境徹底施行『機密脫鉤大法』！全面禁用將密碼寫在程式碼裡！所有的真神大鑰匙，必須被集中關進那座猶如地獄深淵般森嚴的『機密管理保險箱金庫 (Secrets Management Vault, 猶如威震天下的 HashiCorp Vault 或是 AWS Secrets Manager)』中！並在軟體啟動的那一瞬間，才透過看不見的環境變數 (environment variables) 憑空注射給軟體！讓這些致命鑰匙【徹徹底底地、一輩子都不要出現在那堆會被傳來傳去的程式碼版本檔案 (source code) 之中】！】)
C. Hashing the AWS keys using SHA-256 before putting them in the `config.json` file. (把鑰匙拿去雜湊絞碎放在檔案裡。AWS 大門只認原本形狀的鑰匙，你拿一堆碎鐵屑去開門，門不會開，你的程式直接死當)
D. Relying on "Security through Obscurity" by naming the file something else. (把 `config.json` 改名叫 `123.txt` 假裝沒人看到，這是掩耳盜鈴的愚蠢隱晦式防禦)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「外部化機密管理 (Externalizing Secrets / Secrets Management)」**。
    *   **Hardcoded Secrets (寫死在程式碼裡的機密) 是 DevSecOps 時代的頭號殺手。** 只要你把資料庫密碼或 API Key 寫進 Source Code 或是 json 設定檔裡，總有一天它會不小心被推上 GitHub 公開。駭客那邊有成千上萬的機器人 (Bots)，24 小時在 GitHub 上自動掃描 `AKIA` 開頭的字串，一旦你手滑，5 秒鐘內駭客就會拿你的 AWS Key 去開一萬台機器挖比特幣挖到你破產。
    *   **終極解法：** Secrets 絕對不能跟著 Source Code 一起進到版本控制庫 (Git)。開發者必須將它交給獨立的軟體金庫 (如 HashiCorp Vault)。程式碼裡面只會寫一行 "去問 Vault 拿目前的密碼 (憑證)"。這樣就算菜鳥把 Source Code 全部放到 GitHub 上，駭客看到的也只是一句 "我要拿密碼"，而沒有任何真實的密碼字串。這完美地杜絕了金鑰外洩。

#### **5. A development team is adding a new "Forgot Password" feature. The initial code generates a random 4-digit PIN using the standard language library: `Random.Next(1000, 9999)` and emails it to the user as a temporary reset token. A security reviewer immediately rejects this code. Why is using standard `.Next()` or `rand()` functions a critical security vulnerability when generating security tokens or cryptographic keys?**
**(一支急就章的開發義勇軍，正在替主城趕工打造一個『忘記密碼請按此 (Forgot Password)』的逃生小門功能。他們第一版交出來的破爛程式碼，其設計居然是：當客人按鈕時，系統會去呼叫當時那本最普通的程式語言入門字典，用了一句猶如玩具般的弱智指令 `Random.Next(1000, 9999)` 去生出一個四個數字的骰子號碼 (PIN)，然後用鴿子飛信把它當成能解開金庫的萬能重置鑰匙寄給客人。結果！這段破碼剛端上桌，資安總判官一把將它撕成碎片，指著它瘋狂痛罵打回票 (rejects this code)！請問！為何在鑄造這等攸關生死的『安全解鎖權杖 (security tokens) 或 密碼金鑰』時。膽敢貪圖方便，去呼叫這些內建的、給小學生做隨機數抽籤遊戲用的 `.Next()` 或 `rand()` 古老弱智函數，會立刻構成一條死刑級別的重大資安漏洞？)**
A. Standard random number generators are Pseudorandom Number Generators (PRNGs) and are mathematically predictable. The developer MUST use a Cryptographically Secure Pseudorandom Number Generator (CSPRNG) instead. (這正是判官大怒的真理！因為這些給小雞啄米用的標準亂數產生機，在密碼學家的眼底，它們充其量只是一台台【『自欺欺人的偽隨機數產生器 (Pseudorandom Number Generators, PRNGs)』！它們那看似亂跳的數字背後，其實隱藏著極度死板可被破解預測的數學公式宿命 (mathematically predictable)！】駭客只要看過你前兩次骰出來的數字，他就能神機妙算精準猜透你下一秒會骰出幾點，進而直接偽造重置密碼！【開發者絕對必須、只能使用那台刻著密碼學鐵血防禦印記、猶如宇宙深淵般深不可測的『加解密級安全強健隨機數生火爐 (Cryptographically Secure Pseudorandom Number Generator, CSPRNG)』來鑄造鑰匙！】)
B. A 4-digit PIN is too long; it should be 2 digits for better usability. (嫌四個數字太長要改成兩個？那你大概活不到明天早上就會被駭客用膝蓋暴力猜出來)
C. The function takes too much CPU processing time, leading to Denial of Service (DoS). (那些玩具亂數機跑得飛快，根本不會佔用 CPU 導致當機，這不是退件原因)
D. Random numbers cannot be emailed securely over SMTP. (能不能寄信是一回事，但隨機數字本身有毒不夠亂才是重點)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **「密碼學安全偽亂數產生器 (CSPRNG)」 vs 「一般偽亂數產生器 (PRNG)」**。
    *   一般的 `Math.random()` 或是 C 語言的 `rand()`，是設計用來做遊戲抽卡的 (講求速度)。它們底層是靠一個**種子 (Seed，通常是當下的時間戳記 time)** 來帶入一條極為簡單的數學公式一直循環算數字。
    *   **巨大破綻：** 駭客如果在晚上 10 點 05 分看到你發給別人的重置密碼是 `4399`。駭客寫個腳本逆推：「那 10 點 05 分 01 秒，帶入這條白痴公式，下一個重置密碼百分之百一定會是 `7215`」。既然預測到了，駭客就能點擊任何人的忘記密碼，然後自己去輸入預測好的 PIN 碼成功盜用帳號。(這種狀況在歷史上真實發生過無數次)。
    *   **唯一解法：** 當你要生出 Token、Session ID 或是 Encryption Key 時。你**必須**使用作業系統底層提供的 CSPRNG (例如 Linux 的 `/dev/urandom` 或 Java 的 `SecureRandom` 類別)。這種演算法會去收集滑鼠移動軌跡、CPU 溫度雜訊等「真正的物理混沌亂源 (Entropy)」，算出來的數字是完全無法被數學逆推預測的。

#### **6. A prominent financial application allows users to download monthly PDF statements. The URL looks like this: `https://bank.com/download?statement_id=8845`. An attacker, logged in as "User A", manually changes the URL to `statement_id=8846` (which belongs to "User B") and the application successfully delivers User B's highly confidential statement to the attacker. Which pervasive Access Control vulnerability, categorized in the OWASP Top 10, does this implementation suffer from?**
**(一家號稱金字招牌的大銀行軟體，它提供了一個能讓客人去下載每個月刷卡明細 PDF 帳單的貼心功能。當你點擊下載時，上面的網紙連結長得像這副德性：`https://bank.com/download?statement_id=8845 (幫我下載帳單編號第 8845 號)`。沒想到！這時有一個正躺在沙發上的駭客 (User A)，他心生歹念，手賤在瀏覽器網址列上，偷偷地把那個 `8845` 刪掉，手動填上加了一號的 `8846` (這個編號好死不死是隔壁有錢鄰居 User B 的尊貴帳單)！可怕的事情發生了：這台號稱金字招牌的銀行巨獸，居然乖乖聽話，【完全不管你是不是鄰居本人，直接就把鄰居老婆買了幾個名牌包的絕密刷卡明細表，雙手奉上送給了這個駭客 (successfully delivers User B's statement)！】。請問，這等猶如大門守衛眼瞎、只認單子不認人頭的重大權限大洞事件。它在那張名震天下、專抓網頁十大惡毒重罪的惡人榜 (OWASP Top 10) 裡面，赫赫有名的罪刑代號是哪一條？)**
A. Security Misconfiguration (那是指把系統說明書大公開或是沒把管理員預設密碼 admin 換掉的設定失誤)
B. Insecure Direct Object Reference (IDOR) / Broken Access Control (這就是那讓無數銀行大廠嚇到閃尿的：【『不安全的直接物件參考 / 肉身越權大盜竊 (Insecure Direct Object Reference, 簡稱 IDOR)』！這也是名列 OWASP 榜首的『殘破不堪之存取控制權限大崩壞 (Broken Access Control)』家族中最惡搞經典的元老致命傷！】)
C. Server-Side Request Forgery (SSRF) (那是騙伺服器去幫你買東西的伺服器端請求偽造)
D. Insecure Deserialization (那是把殭屍粉末泡在水裡變成真殭屍的解序列化復活術)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「不安全的直接物件參考 (IDOR)」** 是近代 Web 安控最常犯、也最具毀滅性的低級錯誤 (屬於 OWASP 中最嚴重的 Broken Access Control)。
    *   **錯誤的防禦思維：** 銀行的工程師以為「只要這個人有登入就好 (他有 Session Cookie)」，所以當這個人要求下載編號 8846 的檔案時，伺服器只看到「喔，你有會員登入，那我就去硬碟裡把 8846 拿給你」。
    *   **致命漏洞：** 伺服器【忘記去比對：這個有登入的人 (User A)，他到底是不是這份編號 8846 檔案的『真正主人 (Owner)』】！
    *   當系統暴露出一個循序流水號 (如 1, 2, 3...) 作為物件識別碼 (Direct Object Reference)，且後端完全缺乏嚴格的「權限歸屬驗證機制 (Authorization check)」時，駭客就可以無腦寫個迴圈腳本，把 `statement_id=1` 跑到 `100000`，直接把銀行十萬個客戶的帳單全部偷光打包帶走。

#### **7. A developer is writing the core logic for a user registration portal. They need to securely store the user's password in the database. They decide to use the extremely fast MD5 hashing algorithm to hash the password before saving it. What are the two massive, critical flaws with this specific implementation?**
**(一名工程師正在為主城大廣場的『鄉親入城註冊大報名台 (user registration portal)』撰寫核心法陣。到了最關鍵的一步：他必須要把鄉親們填寫的『身家性命大密碼 (user's password)』給安全的藏進地下大冰庫裡。這傢伙眼睛一轉，自以為聰明地跑去古董店，挑了一台號稱【運轉速度飛快、名叫 `MD5` 的古董級攪肉機 (MD5 hashing algorithm)】來把密碼絞碎後再丟進冰庫裡存起來。請問！這位自以為撿到寶的工程師，他在這個自稱完美的藏密碼環節裡，同時踩中了哪【兩顆】能夠讓整座城池一秒灰飛煙滅的核武級致命死穴地雷 (two critical flaws)？)**
A. MD5 is a symmetric encryption algorithm, and it requires a public key. (這是連基礎名詞都亂背的錯亂！MD5 是單向雜湊不能還原，它才不是什麼需要兩把鑰匙的對稱式加解密演算法！)
B. MD5 is an outdated, cryptographically broken algorithm susceptible to collision and rapid brute-forcing. Furthermore, the developer failed to use a unique "Salt" (Salting) to prevent Rainbow Table attacks. (這就是把這白癡工程師釘在歷史恥辱柱上的兩大死罪判決書：【第一死罪：「老兵不死，只是變成毒藥」！MD5 這台破榨汁機早就被全世界數學家宣布『死亡且千瘡百孔 (outdated, cryptographically broken)』，駭客現在用一張顯示卡，一秒鐘就能榨出上百億次的運算，瞬間把你絞碎的數字用暴力給撞出來復原原狀 (rapid brute-forcing)！】【第二死罪：「偷懶不加鹽巴的愚蠢料理法」！這傢伙居然把密碼「生吃」直接丟進機器，根本沒有遵守防禦大律例：『打死都要在那包肉裡混入一大把讓駭客破解表單瞬間報廢失效的獨一無二隨機香料鹽巴 (failed to use a unique "Salt")』！這第二條罪直接讓駭客可以拿著網路上現成的幾百 G 大抄大字典 (Rainbow Table)，一秒查表就直接對照破解你的整座金庫密碼！】)
C. MD5 is too slow, and it will cause the database to crash. (MD5 的缺點剛好相反，它就是因為運算速度【太他媽的快了】(fast hash)，所以駭客在那邊狂猜暴力破解的時候才會如虎添翼、毫無阻力！)
D. MD5 cannot store passwords longer than 8 characters, and it is illegal under GDPR. (MD5 可以吃很長很長的密碼，這並不是它的極限)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是儲存密碼 (Password Storage) 領域最必備的基礎知識。
    *   **第一重錯誤 (演算法過時)：** MD5 和 SHA-1 因為數學碰撞漏洞 (Collision) 以及它們運算速度**太快**被設計，早已被完全棄用。密碼雜湊必須使用 **"慢速 (Slow Hashing/Key Stretching)"** 演算法如 PBKDF2, Bcrypt 或是 Argon2。因為運算慢，合法用戶登入多等 0.1 秒沒感覺；但駭客想要在自己電腦上暴力猜測 100 億組字典密碼時，這緩慢的速度就會直接把駭客破解的時間從 "半天" 拉長到 "十萬年"。
    *   **第二重錯誤 (忘記加鹽 Salting)：** 如果大家密碼都是 `123456`，那它經過 MD5 絞碎後的字串長相會一模一樣 (`e10adc...`)。駭客老早就把全宇宙所有的 MD5 組合結果印成了一本幾百 G 的「字典彩虹表 (Rainbow Table)」。駭客只要把你的絞肉拿去查表，瞬間就能知道原狀。
    *   **解法 (加鹽)：** 在把每個人的密碼絞碎前，系統自動去抓一把隨機字串 (Salt 例如 `X9s$2`) 加在密碼後面變成 `123456X9s$2`，然後再絞。因為每個人的鹽巴都不一樣，駭客的查表字典就會瞬間作廢，逼迫駭客只能從零開始慢慢算，完美防禦彩虹表攻擊。

#### **8. A Java web application accepts serialized Java objects from an external, untrusted API endpoint to process complex data structures natively. The application immediately calls the `readObject()` function to deserialize the stream back into operational memory without performing any structural validation or type checking on the incoming bytecode. If an attacker crafts a malicious serialized payload containing arbitrary execution commands, what devastating vulnerability is triggered?**
**(有一座古老而龐大的 Java 法師魔法塔 (Java web application)。為了方便接收外面信徒送來那一箱又一箱形狀複雜且巨大的貢品符咒寶箱 (complex data structures)。這座魔法塔非常偷懶地，對外敞開了一扇專收『被靈魂石封印壓縮過的原始法力箱子 (serialized Java objects)』的接送大門。要命的是！這群法師居然毫不懷疑外面送來的東西有沒有毒，他們只要箱子一送進門，連檢查裡面是不是藏了炸彈跟殭屍都不檢查 (without performing any structural validation)！就瘋狂猴急地對著箱子大喊那句最禁忌的喚神解開封印咒語：`『立即復活顯現吧！readObject() ！！』`，企圖把箱子裡的東西直接還原成魔法塔身體記憶體裡可以運轉的神靈巨獸。請問！如果這時門外站著的是一個深淵大魔王，他故意捏造了一個『長得像普通寶箱、但裡面被塞滿了能夠在甦醒那一秒直接砍斷法師脖子的惡毒遠端處決指令大妖物 (malicious serialized payload)』！當法師念出解印咒語的那一瞬間，這座魔法塔會立刻引爆哪一場聞令喪膽的毀城大災難？)**
A. Cross-Site Scripting (XSS) (這只是在網頁上跳跳視窗，跟這種深層復活用魔法陣無關)
B. Insecure Deserialization (leading to Remote Code Execution - RCE) (這就是那場曾經血洗整個 Java 帝國、讓無數大廠一夜崩盤的千古慘劇：【如同唸錯咒語把毀滅大魔王直接召喚在自家庭院的『不安全的反序列化 / 極限亡靈法師黑魔法解印復活術 (Insecure Deserialization)』！它所導致的最慘痛下場，就是直接被駭客拿走全系統的生殺大權 (直搗黃龍的 Remote Code Execution, RCE)】！)
C. SQL Injection (這只是去資料庫裡撈錢，這場災難發生在應用程式記憶體裡)
D. Man-in-the-Middle (MitM) Attack (這只是躲在半路上偷聽別人講電話)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「不安全的反序列化 (Insecure Deserialization)」** 是一個曾經進入 OWASP Top 10 的毀滅級漏洞 (近幾年被併入軟體與資料完整性失敗中)。
    *   **序列化 (Serialization)：** 程式把記憶體中一整塊複雜的物件 (Class)，壓縮打包成一串位元字串 (像是一個壓縮檔寶箱)，方便透過網路傳送。
    *   **反序列化 (Deserialization)：** 這是危險的時刻。當對方的程式接收到那串 byte code，並呼叫 `readObject()` 時，系統其實是在【依照那串字串的藍圖，直接在自己赤裸的記憶體深處重新「執行、建構、實體化並喚醒」一個程式碼物件】。
    *   如果程式沒有去檢查對方送來的是什麼東西 (Untrusted Data)，駭客可以送來一個被改造過的惡意 Class 藍圖 (裡面寫滿了如刪除檔案、執行 PowerShell 腳本等惡毒指令)。當系統傻傻地 `readObject()` 把它復活的瞬間，駭客的指令就會夾帶在記憶體初始化的過程中被最高權限執行 (RCE)。這是非常要命且難以防堵的深層漏洞設計。

#### **9. During a code review, an architect notices that an API endpoint designed to update a user's `email_address` also blindly accepts and processes ANY other JSON key-value pairs submitted in the HTTP POST request. By simply adding `"is_admin": true` to the JSON payload, an ordinary user can trick the backend object-relational mapper (ORM) into instantly elevating their privileges in the database. What specific security implementation flaw is this?**
**(在金碧輝煌的帝國大殿上，大祭司正拿放大鏡檢查一道名為『平民去戶政事務所改自己電子信箱 (update email_address)』的官方 API 櫃檯。他突然驚恐地發現這個櫃台辦事員，是個無腦瞎眼睛的機器人！這個機器人設計時，居然會像黑洞一樣不管三七二十一，把那個平民刁民呈上來的一大包牛皮紙袋改戶口包裹 (JSON payload)，【完全不經過任何查驗跟過濾，整包瞎眼照單全收，並原封不動地幫他強制匯入到國家大名冊深層核心資料庫裡 (blindly accepts and processes ANY other pairs)】！這代表著，一個路邊的下流平民，他只要在申請改信箱的表格角落下方，偷偷拿奇異筆多加寫了一行：`【"我現在是這個國家的大總統 (is_admin)": 是的沒錯 (true)】`。那個瞎眼辦事員就會直接拿著皇家玉璽，把這個瞎扯淡的身分蓋章進去，讓這個小流氓在下一秒瞬間黃袍加身，掌控國家大權 (instantly elevating privileges)！請問這等極度荒謬、猶如瞎眼包裹收發室的致命軟體實作天坑，專有名詞稱之為何？)**
A. Mass Assignment (aka Overposting / Auto-Binding vulnerability) (這就是以偷渡改身分聞名天下、專門鑽現代便利魔法框架漏洞死穴的：【『無腦批量大指派 / 瘋狂暴發過度提交 / 失控的大量自動綁定災難大漏洞 (Mass Assignment / Overposting / Auto-Binding vulnerability)』】！)
B. Buffer Overflow (那個是要塞爆記憶體的，這個填張單子而已不會當機)
C. Cross-Site Request Forgery (CSRF) (那是騙你本人去按按鈕)
D. XML External Entity (XXE) (那個是處理長得像 XML 的東西，現在處理的是 JSON 欄位綁定)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **「大量指派漏洞 (Mass Assignment)」** (在 C# / ASP.NET 中常被稱為 Overposting，或 Spring 框架的 Auto-Binding 漏洞)。
    *   這是現代使用 ORM 框架 (如 Hibernate, Entity Framework, Ruby on Rails) 為了開發快速而引發的「便利與安全的世紀大車禍」。
    *   **產生原因：** 開發者為求圖快，寫了一句神級指令 `User.update(request.body)`。這句魔法指令會自動把用戶傳來的 JSON 表單裡所有的 Key，跟資料庫裡的欄位一一對應並直接寫進去。
    *   **駭客攻擊：** 駭客知道正常的表單只有 `{ "email": "test@test.com" }`。但駭客猜測資料庫裡一定有一個控制權限的欄位例如 `role` 或 `is_admin`。於是駭客就自己用 POSTMAN 送出 `{ "email": "a@a.com", "is_admin": true }`。因為開發者沒有寫「白名單過濾 (只准綁定 email)」，這句強大的更新魔法就會聽命行事，直接在資料庫把這名用戶的 `is_admin` 改成 `true`，瞬間完成不用密碼的最高權限耀昇 (Privilege Escalation)。
