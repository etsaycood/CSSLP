# 第四套全真模擬試題 (Exam 4) - 答案與詳解本
## 領域 5：安全的軟體實作 (Secure Software Implementation) (18題) - Part 1 (Q1-Q6)

---

#### **1. A developer is writing a C function that copies a user-supplied string into a fixed-size local character array using the `strcpy()` function. Which of the following vulnerabilities is the developer explicitly introducing into the application?**
**(一名老眼昏花的打鐵匠，正在用古老的 C 語言打造一把名為『拷貝大法 (copy string)』的寶印。他從客人的手裡接過一張寫滿字的長長宣紙 (user-supplied string)，然後準備把這些字，原封不動地拓印到一個他自己釘好、只有十公分寬的小木框裡 (fixed-size local character array)。最要命的是！這老頭居然使用了兵器譜上惡名昭彰、絕不問長短只管死命塞的被詛咒神印：【『`strcpy()`』】！請問，這老頭因為用了這顆被詛咒的神印，親手把哪一隻會撐破肚皮、讓整座皇城大腦爆裂的千古大妖魔給釋放到了這套系統裡？)**
A. Cross-Site Scripting (XSS) (跨站腳本是網頁上的毒藥，這跟 C 語言底層記憶體操作是完全不同世界的東西)
B. Buffer Overflow (這就是名震天下、在 C/C++ 洪荒時代殺死無數英雄好漢的：【『記憶體大潰堤之緩衝區溢位大爆炸 (Buffer Overflow)』】！這隻魔鬼的原理極度單純卻致命：那個叫 `strcpy()` 的愚蠢神印，它【絕對不會去拿尺量】你那個小木框 (Buffer) 只有十公分寬！如果客人給你的宣紙有一百公分長，`strcpy()` 會閉著眼睛死命地把這一百公分的字全部塞進去！結果就是：裝不下的九十公分，會像洪水一樣直接【溢出木框】，把隔壁存放著『皇城玉璽 (Return Address/Instruction Pointer)』的抽屜給淹沒竄改！駭客就能藉此直接竊取主機的最高控制權！這是軟體實作史上最經典的死穴！)
C. SQL Injection (SQL 注入是用單引號騙資料庫，跟 C 語言的記憶體滿出來毫無關係)
D. Integer Underflow (整數下溢是把數字減到零以下變成無限大，這是在玩弄數學數字，而這題是在玩弄長度與字串)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **`strcpy()`** 是 C/C++ 中引發 **「緩衝區溢位 (Buffer Overflow)」** 最經典、最惡名昭彰的不安全函式 (Insecure Function)。
    *   **漏洞原理：** `char dest[10]; strcpy(dest, user_input);`。`strcpy` 沒有邊界檢查 (No Bounds Checking)。如果 `user_input` 的長度超過 9 個字元 (加上結尾的 `\0` Null byte)，多出來的字元就會覆寫 (Overwrite) 記憶體堆疊 (Stack) 上相鄰的空間。
    *   **嚴重後果：** 攻擊者可以精準計算溢出的長度，覆寫函數的回傳位址 (Return Address)，將執行流程導向攻擊者自己注入在記憶體中的惡意程式碼 (Shellcode)，達成遠端程式碼執行 (RCE)。
    *   **實作防禦 (Remediation)：** 永遠禁止使用 `strcpy()`, `sprintf()`, `gets()`。必須改用有邊界檢查的安全版本：`strncpy()`, `snprintf()`, `fgets()`，或是直接使用 C++ 的 `std::string`。

#### **2. You are reviewing the source code of a web application built in PHP. You encounter the following line of code used to execute a system command: `exec("ping -c 4 " . $_GET['target_ip']);`. What is the MOST effective secure coding practice to remediate this specific vulnerability?**
**(你身披錦衣衛大氅，正在巡視一座用 PHP 爛泥巴糊成的驛站。突然，你在一塊殘破的牆板上，看到了一行會讓任何有常識的將軍當場嚇到心肌梗塞的血紅大字：【『`exec("ping -c 4 " . $_GET['target_ip']);`』】！這行字的意思是：這間驛站居然把大門口外鄉人嘴裡喊出的隨便一句話 (GET target_ip)，【沒有經過任何大腦思考，直接當作皇帝的聖旨、交給底下掌管生死大權的劊子手 (作業系統 Shell exec) 去無腦執行 (execute a system command)】！請問，為了徹底根除這個等同於把玉璽直接交給路人的恐怖亡國死穴，哪一招才是釜底抽薪的【最有效大防禦法門 (MOST effective secure coding practice)】？)**
A. Use a regular expression to strip out all non-alphanumeric characters from the `target_ip` variable. (用正則表達式去洗澡 (Sanitization) 雖然可以洗掉惡意的分號 `;`。但這種「黑名單/過濾」作法永遠有漏網之魚，駭客總能發明出新型的繞過符號，這不是最釜底抽薪的做法)
B. Avoid passing user input directly to the operating system shell altogether; instead, use safe, built-in language APIs (e.g., a specific DNS or ICMP library) if possible. (這就是資安實作領域裡，對付這隻魔王的最崇高、最無懈可擊的無上大真理：【『徹底斬斷與死神共舞的橋樑：絕對禁止將刁民的隻字片語直接餵給作業系統大黑洞去跑 (Avoid passing user input directly to the OS shell)！』】。治本之道就是：【你根本就不應該去呼叫 `exec()` 這種能毀滅世界的底層指令！】。如果你這個功能只是想問對方的門牌號碼能不能通 (ping)，你應該使用 PHP 語言本身內建的、安全無害的『純網路發信函式庫 (built-in language APIs / specific ICMP library)』。這些函式庫只會發網路封包，就算駭客輸入了 `127.0.0.1; rm -rf /`，函式庫也只會報錯說「這不是個 IP」，而絕對不會把這個可怕的刪除指令交給作業系統去炸毀皇城！這叫架構與實作層面的徹底免疫！)
C. Encrypt the `target_ip` variable before passing it to the `exec()` function. (你把駭客的話加密再丟給作業系統，作業系統解碼後還是一樣照著駭客的話把伺服器炸了，又或者作業系統根本看不懂加密文，這都是無意義的搞笑動作)
D. Append a null byte (`%00`) to the end of the `target_ip` variable. (Null byte 截斷是十年前用來騙 PHP 讀檔案老招，它根本無法阻止 `exec()` 執行前方已經寫好的惡意系統指令。)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 探討防禦 **「作業系統指令注入 (OS Command Injection)」** 的最佳實務 (Best Practice)。
    *   **漏洞原理：** 題幹中的 `exec("ping -c 4 " . $_GET['target_ip']);` 是致命的。如果駭客輸入的 `target_ip` 是 `127.0.0.1; cat /etc/passwd`，這整齊句變成 `ping -c 4 127.0.0.1; cat /etc/passwd`。Shell 會先 ping 完，然後立刻執行後面的 `cat` 指令把密碼檔印出來。
    *   **Remediation (修補策略)：**
        *   **次等防禦 (Input Validation / Escaping)：** 雖然可以使用 `escapeshellarg()` 或 Regular Expression (如要求必須是合法 IP 格式) 來驗證輸入。但這依然依賴開發者的細心，容易出錯。
        *   **最高級防禦 (API Replacement / Avoidance)：** 根本不要呼叫 Shell (不要用 `exec`, `system`, `passthru`)。如果需要執行網路操作，就用該程式語言內建的、不依賴 OS Shell 的網路 API。就算真的要呼叫外部程式，也必須使用不喚起 /bin/sh 環境的 `execFile` 或參數陣列化的 `spawn()`，從物理上阻絕 Shell 元字元 (Meta-characters) 被解析的可能。

#### **3. A Java developer needs to store a highly sensitive API key in the application's source code for a temporary proof-of-concept (PoC) demonstration. They intend to remove it before pushing the code to the central Git repository. What is the fundamental security principle being violated, even for a temporary PoC?**
**(一名急著向老爺展示自己最新發明的小工匠。為了一個『只演一次就拆掉的小型皮影戲 (temporary PoC demonstration)』。他便宜行事，居然把能開啟天下第一大金庫的『純金萬能大鑰匙 (highly sensitive API key)』！【直接大喇喇地刻在他用來演皮影戲的劇本竹簡上 (store in the application's source code)！】。小工匠心虛地告訴自己：『哎呀，反正演完戲，我在把竹簡交給大書庫 (Git repository) 收藏之前，我一定會把這行字給刮掉的！(intend to remove it before pushing)』。請問！即便這只是個臨時的皮影戲，小工匠的這種僥倖心態，已經徹底觸犯了哪一條會被判處極刑的兵工廠防衛大天條？)**
A. Principle of Least Privilege (最小權限是不該給小工匠這把萬能鑰匙，但現在問題是他把鑰匙『刻在竹簡上』這個動作，而不是他該不該擁有鑰匙)
B. Separation of Duties (職責分離是防範一個人既能開保險箱又能塗改帳本。這跟把密碼寫死在劇本上無關)
C. Never hardcode credentials or secrets directly into source code, as they can easily be committed to version control or extracted from compiled binaries. (這就是名震四海、只要觸犯一次就會讓整座皇城被抄家滅族的絕對底線天條：【『斬立決大罪：絕對禁止！永遠禁止！將任何金鑰、機密與通關密語，直接死死刻印在你的程式碼劇本裡 (Never hardcode credentials or secrets directly into source code)！』】。這條死律沒有任何「臨時的例外」！因為人類是無比愚蠢且健忘的生物。你說你等一下會刮掉，結果你轉頭吃個便當就忘了，直接把整捆竹簡丟進了大書庫 (committed to version control)。從此，這把萬能大鑰匙將永遠烙印在歷史紀錄 (Git History) 中，駭客只要用掃描器一照，這把鑰匙就直接天下皆知、金庫秒空！連「臨時測試」都不准 Hardcode，這是鐵則！)
D. Perfect Forward Secrecy (完美前向保密是保護過去的對話即使鑰匙丟了也不會被解密，這是在談加密演算法的特性，不是在談密碼保管的亂寫死罪)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「禁止硬編碼機密 (Never Hardcode Secrets)」** 是安全寫碼 (Secure Coding) 最基礎、也是最常被破壞的守則。
    *   **現實的殘酷 (The "Temporary" Fallacy)：** 開發者常說 "這只是 Local 測試" 或 "這只是 PoC"。但現實是，這些帶有 Hardcoded API Keys、AWS Credentials、Database Passwords 的程式碼，有極大機率被意外地 `git commit` 並推送到 GitHub 或企業內部的 GitLab。
    *   **後果 (Git History 的不朽性)：** 一旦機密進入了 Git 的版本歷史 (Version Control History)，即使你在後續的 Commit 把它刪除了。駭客憑藉源碼掃描工具 (如 TruffleHog, GitLeaks)，依然可以從舊的 Commit 中把這把鑰匙挖出來，導致嚴重的雲端資源被盜用或資料外洩。
    *   **正確作法：** 即使是 PoC，也必須養成習慣，將機密寫入外部的 `.env` 檔案 (並將 `.env` 加入 `.gitignore`)，或是從作業系統環境變數 (Environment Variables) 讀取，甚至使用 Secret Management (如 HashiCorp Vault)。

#### **4. In modern web development (e.g., using React, Angular, or Vue.js), which built-in framework feature serves as the primary defense mechanism against Cross-Site Scripting (XSS) by automatically treating user-provided data as text rather than executable HTML/JavaScript?**
**(在現代那些飛天遁地、華麗無比的『網頁三大門派神功 (React, Angular, or Vue.js)』裡。雖然這群神仙打架花招百出，但他們的地基裡，都不約而同地埋藏著一套用來防範『千古毒王 XSS 跨站惡意咒語』的【絕對防禦被動大光環】！這個大光環神妙無比：每當外面刁民嘴裡吐出那些長得像危險魔咒的【『`<script>爆炸</script>`』】時！這個光環會【自動、無腦且強悍地】，把這些危險的魔法文字，全部貶為凡間最普通的『死文字 (text)』，硬生生地拔掉它們能爆炸的引信，只把它們當作畫布上的顏料展示給其他客人看 (treating data as text rather than executable HTML/JS)！請問，這套被寫死在現代三大門派骨髓裡的防禦大光環，尊號為何？)**
A. Automatic Parameterization (自動參數化是用鐵籠關住 SQL 注入的，那是對付後端資料庫的大絕招。而這題現在是在講對付前端網頁畫面上的毒藥 XSS，戰場完全不同)
B. Context-Aware Output Encoding (Auto-Escaping) (這就是現代網頁前端框架能橫行天下、不再懼怕 XSS 毒藥的終極免死金牌：【『上下文感知之全自動輸出編碼大淨化法 / 自動跳脫字元大陣 (Auto-Escaping / Context-Aware Output Encoding)』】！在古老的 PHP 時代，工匠必須自己記得把 `<` 變成 `&lt;`。只要忘記一次，皇城就毀了。但現代的 React (在寫 JSX `{data}` 時) 或 Angular (在寫 `{{data}}` 時)，框架本身就內建了這套神功！他們會在把使用者的話釘上網頁畫面前的最後一秒鐘。自動把所有危險的尖括號 `< >` 和引號 `' "`，物理性地轉換 (Encode) 成無害的 HTML 實體符號！這讓這段惡毒的 `<script>` 腳本，在瀏覽器眼裡就只是「一段用來閱讀的可愛字串」，而絕對不會被當成「程式碼」去執行炸毀使用者的電腦！這就是實作層最高級的『預設安全 (Secure by Default)』！)
C. Cross-Origin Resource Sharing (CORS) enforcement (CORS 是管兩家不同客棧能不能互相借醬油的跨來源協議，跟把你臉上這碗麵裡的毒藥過濾掉的 XSS 防護完全無關)
D. Content Security Policy (CSP) report generation (CSP 雖然是防禦 XSS 的極致第二道防線 (Defense-in-Depth)，但它是透過發布「白名單政策公文」給瀏覽器。而這題問的是「框架內建、自動把資料當成純文字跳脫」的行為，這指的正是自動輸出編碼 (Auto-Escaping)。兩者的手段機制不同)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是現代前端框架 (Frontend Frameworks) 最強大的安全特性：**自動輸出編碼 (Auto-Escaping / Output Encoding)**。
    *   **XSS 的防禦核心：** 攔截 XSS 的最有效地點不是在輸入端 (Input Validation)，而是在資料即將被「渲染 / 輸出 (Output)」到使用者的瀏覽器畫面的那一瞬間。
    *   **框架的神威：**
        *   在 React 中，你寫 `<div>{userInput}</div>`。
        *   如果 `userInput` 是 `<img src=x onerror=alert(1)>`。
        *   React 會在底層自動進行 HTML Entity Encoding，將其轉為 `&lt;img src=x onerror=alert(1)&gt;`。
        *   瀏覽器只會在畫面上印出這段字，而不會去執行這個有害的 `alert(1)`。這大幅度 (雖然不是 100%) 地消滅了現代 Web App 中的 XSS 漏洞。

#### **5. A developer is implementing an "Update Profile" feature where users can change their own email address. The backend API endpoint is `PUT /api/users/{id}/email`. The developer writes the code to read the `{id}` from the URL and update the corresponding record without checking if the currently logged-in user's session token actually matches that `{id}`. Which vulnerability has been introduced?**
**(一名粗心大意的大掌櫃，正在打造『天下客棧個人名牌更換服務』。他在櫃檯前掛了個牌子：只要來到這條名為 `PUT /api/users/{id}/email` 的專屬小巷子，任何人都可以換掉自己名牌上的信箱。但這蠢蛋掌櫃在寫工作手冊時，犯下了一個讓全城大亂的恐怖錯誤！他寫道：【『只要路人走到這巷子，大喊「我要換 102 號客人 ({id}) 的信箱！」。【你就把 102 號客人的信箱換掉！絕對不要去查這個大喊的人，他脖子上的狗牌 (session token) 到底是不是 102 號本人 (without checking matching ID)！】』】。結果就是：一個編號 999 的窮乞丐，只要在巷口大喊「我要改 1 號皇帝的信箱」，皇帝的信箱就被改了！請問，這蠢蛋掌櫃引狼入室的這種越權大災難，專有名詞為何？)**
A. Cross-Site Request Forgery (CSRF) (這不是 CSRF。CSRF 是騙皇帝自己點了那條巷子的按鈕，利用皇帝的狗牌發信。這題是乞丐直接拿自己的狗牌去喊皇帝的名字，這是越權)
B. Insecure Direct Object Reference (IDOR) / Broken Object Level Authorization (BOLA) (這就是名震四海、專門用來偷看別人底牌、篡奪別人皇位的：【『千古第一越權大漏洞：不安全的直接物件參考 (IDOR) / 也就是新時代魔王：失效的物件層級授權 (BOLA)！』】。這隻魔王的核心精髓在於：系統大門雖然有檢查你是不是合法登入的良民 (Authentication 通過)。但是！當你想去動「第 102 號抽屜 (Object)」時，系統卻【少做了最後一道最致命的檢查：確認你這個良民，有沒有資格碰這個不是你的抽屜 (Authorization Failed)】！這導致攻擊者只要像猜猜看一樣，無聊地把 URL 上的 `{id}` 從 102 改成 103、104。就能橫行霸道地看光全天下老百姓的資料甚至隨意竄改！這是現代 API 實作中最常見、排名第一的死穴！)
C. Session Fixation (Session 固定攻擊是駭客塞一張舊狗牌給你看病，等你發布最高權限後駭客再拿這舊狗牌進來。這跟在 URL 上瞎猜別人號碼的越權行為不同)
D. Directory Traversal (目錄穿越是在 URL 打 `../../etc/passwd` 試圖爬出網頁資料夾去偷看作業系統的核心檔案。這題是改資料庫裡的 ID 數字偷看別人的帳戶，兩者維度截然不同)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是對 **IDOR (Insecure Direct Object Reference)**，現在 OWASP API Security Top 10 稱為 **BOLA (Broken Object Level Authorization)** 的最經典描述。
    *   **漏洞本質：** 認證 (Authentication - 你是誰) 和 授權 (Authorization - 你能做什麼) 是兩回事。
    *   **開發者的錯誤實作：** 開發者只驗證了「這是一個合法登入的 Session Token」，就直接信任了 Client 端傳來的 URL Parameter `/{id}/` 作為資料庫 UPDATE 指令的目標條件。
    *   **正確實作 (Remediation)：** 在撰寫 API 業務邏輯時，必須執行 **「物件層級的權限檢查 (Object Binding/Authorization Check)」**。開發者應該從目前這個 Request 夾帶的 Session Token (或 JWT) 中，反解出目前發出請求的使用者 `user_id_from_token`。然後在背後去比對：`if (user_id_from_token != id_from_url) { return 403 Forbidden; }`。唯有如此，才能防禦攻擊者隨意修改 URL ID 導致的水平越權 (Horizontal Privilege Escalation) 攻擊。

#### **6. When generating cryptographically secure random values (such as session IDs, password reset tokens, or initialization vectors), which type of random number generator MUST a developer use to prevent attackers from predicting the next value?**
**(在鍛造諸如『金庫大門臨時通行令牌 (session IDs)』、『免死金牌 (password reset tokens)』這類關係到身家性命的神聖寶物時。打造這塊牌子的數字，必須是猶如天上繁星、絕對無法被任何凡人占卜算出的【終極無序大亂數 (cryptographically secure random values)】！如果這數字被人算出規律，那明天天下大亂！請問，在那本『鍛造神兵利器安全大典』中規定，工匠只能去哪一種『搖錢樹 (random number generator)』上摘取數字，才能確保這些數字連神仙都預測不了後續的發展 (prevent attackers from predicting the next value)？)**
A. A Pseudorandom Number Generator (PRNG) initialized with the current system time (e.g., `java.util.Random`). (這是用【現在手錶上的時間 (system time)】去當算命種子的偽亂數 (PRNG)。這簡直是自殺防線！如果駭客知道你是早上八點整發的牌子，他只要拿一樣的時間丟進同樣的數學公式裡，他能一秒不差地把你接下來發的一萬張牌子號碼全部算得一清二楚！這叫有跡可循，絕不能用在保命符上！)
B. A hardware-based True Random Number Generator (TRNG) only. (純硬體的真亂數產生器，是利用放射性同位素衰退或是宇宙微波背景輻射來算數字。這雖然是最偉大也最不可猜測的。但如果規定所有人間的造車工廠「只能(ONLY)」買這台昂貴的硬體來造牌子，那天下沒人能寫程式了。在軟體實務上，我們有更實用的折衷方案)
C. A Cryptographically Secure Pseudorandom Number Generator (CSPRNG) (e.g., `/dev/urandom` or `java.security.SecureRandom`). (這就是名震當代、能在沒有硬體輻射爐的情況下，依然能用數學魔法榨出讓駭客算斷手也算不出身家底細的：【『無敵密碼學級之終極偽亂數大熔爐 (CSPRNG)！』】。這個大熔爐 (`java.security.SecureRandom` 或 Linux 系統神物 `/dev/urandom`) 的奧義在於：它【不只】看時間。它還會瘋狂地去吸取這台電腦上最無序的靈魂：【老鼠游標滑了多遠、風扇轉了幾圈、硬碟讀寫了幾次 (Entropy Box/熵池)】！把這些隨機到極致的現象全部融合成一顆大種子。在這種極限的混亂下，它確保了產生的亂碼在密碼學上是【絕對不可預測的 (Unpredictable)】！這是一切安全實作產生密碼的唯一首選！)
D. A Linear Congruential Generator (LCG). (線性同餘生成器，這是數學家發明的一種超快速、公式極簡的亂數法線。但正因為公式太簡單，它只需要拿到前面幾個數字，就能像小學生算數一樣推導出後面所有發展，這在密碼學界是徹頭徹尾的垃圾)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是安全實作 (Secure Implementation) 中關於 **「亂數生成 (Randomness / Entropy)」** 的鐵律。
    *   對於產生具有高機密性與安全價值的資料 (如 Session Token, CSRF Token, Encryption Key, Initialization Vector (IV))，**絕對不能使用一般的 PRNG (Pseudorandom Number Generator, 偽亂數產生器)** 如 `rand()` (C/C++) 或 `Math.random()` (JavaScript) 或是 `java.util.Random`。
    *   **PRNG 的死穴：可預測性 (Predictability)。** 普通 PRNG 通常使用系統時間 (Timestamp) 作為種子 (Seed)。這代表如果攻擊者知道大概的 Server 時間，就能輕易逆向推導出隨機數序列，從而偽造 Session Token 接管帳號。
    *   **CSPRNG (密碼學安全偽亂數產生器) 的神威：** 為了具備密碼學強度 (Cryptographic Strength)，CSPRNG (如 `java.security.SecureRandom` 或是 Node.js 的 `crypto.randomBytes()`) 會從作業系統的「熵池 (Entropy Pool)」中獲取足夠混亂的環境變數 (如鍵盤敲擊中斷、滑鼠移動軌跡) 來不斷播種 (Seed)。這確保了隨機數能夠通過嚴格的統計隨機性測試，具備計算上無法預測的特性 (Computationally Unpredictable)。
