# 第四套全真模擬試題 (Exam 4) - 答案與詳解本
## 領域 5：安全的軟體實作 (Secure Software Implementation) (18題) - Part 3 (Q13-Q18)

---

#### **13. A C++ developer uses the `new` operator to allocate memory dynamically on the heap for a temporary object. However, in one specific error-handling code path, the function returns early without calling the corresponding `delete` operator to free the memory. Which vulnerability is created by this implementation error?**
**(一名在打造『C++ 大地圖引擎』的苦力老礦工，為了裝一塊這輩子都沒見過那麼大的巨石 (temporary object)，他不得已向地府老爺，借用了一塊名為『無底深淵大私自圈地 (dynamically allocate memory on the heap)』的空地！他大喊一聲 `new` 魔法，把空地佔了下來。但是！這愚蠢的礦工在挖到一半時，突然腳底板踩到了毒蛇 (error-handling code path)！他嚇得立刻連滾帶爬地逃出了這片礦區 (function returns early)！最要命的是，他逃跑的時候，【完全忘記回頭去把剛才跟老爺借來的那塊空地給退回去還給地主 (without calling `delete` operator)！】。請問！若是這愚蠢的礦工每天都被蛇咬，每天都幹這種借了不還的勾當，這座本來幅員遼闊的大陸，遲早會面臨什麼樣滅絕人性的毀滅災難 (vulnerability created)？)**
A. A Use-After-Free (UAF) vulnerability. (使用釋放後記憶體大洞，是指這片空地他明明早就還給地主了，但他後來居然又偷偷跑回來在上面蓋房子，結果這地已經蓋成了公共廁所。這是還了以後又亂用的災難，這題是他根本「沒還」)
B. A Memory Leak, which can lead to resource exhaustion and a Denial of Service (DoS). (這就是那隻無聲無息、最終能吞噬整個地球的：【『無盡黑洞之記憶體大洩漏 (Memory Leak)！』】。這個恐怖的詛咒是：每當這礦工被蛇咬一次逃跑，那塊他借來的空地，就成了永遠的【法外孤魂野鬼禁區 (unreferenced memory)】！因為再也沒人知道這塊地被誰拿去用了，地府老爺也收不回來借給別人。當這個小程式在皇宮裡安穩地執行了一年後。這位老爺會震驚地發現，全天下的空地，居然全部被這群早就跑光的死人霸佔滿了！於是，整個皇宮連一隻新出生的蚊子都找不到地方落腳 (resource exhaustion / OOM)。最終！系統的生命特徵歸零，整座皇城直接卡死斷氣 (Denial of Service DoS)！這是 C/C++ 老人最不願提起的傷痛史實！)
C. An Out-of-Bounds Write. (越界寫入是這礦工明明只借了五坪，他硬是把房子蓋到鄰居的院子裡。這題他本來就借了這塊大地，只是忘記退房，不是越界)
D. An Integer Overflow. (整數溢位是他在筆記本上算昨天賺了多少錢時，算盤爆掉歸零，這跟跟地府老爺圈地不還是兩回事)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是對 **「記憶體流失/洩漏 (Memory Leak)」** 最精準的情境描述。
    *   **漏洞成因：** 在不具備自動垃圾回收機制 (Garbage Collection, 如 Java/C#) 的語言 (C/C++) 中，開發者必須手動管理 Heap (堆積) 記憶體。`new` (或 `malloc`) 必須對應 `delete` (或 `free`)。
    *   **常見實作錯誤：** 開發者在函數的正常結束路徑 (Happy Path) 放了 `delete`。但是，如果在中間某處發生了 Exception (例外) 或 `if (error) return;` 提早結束，導致執行流程跳過了 `delete`，這塊記憶體就會變成孤兒。
    *   **安全影響：** Memory Leak 本身不一定能直接被用來執行惡意程式碼 (不會導致 RCE)。但它是一個嚴重的穩定性與可用性缺失。攻擊者可以故意發送大量會觸發這個錯誤路徑 (Error Path) 的 Request，快速吃光被攻擊伺服器的所有 RAM，導致 OutOfMemoryError (OOM)，最終造成服務崩潰 (Denial of Service, DoS)。在現代 C++ 實務中，應改用 Smart Pointers (`std::unique_ptr`, `std::shared_ptr`) 來根除此問題 (RAII 原則)。

#### **14. To prevent Cross-Site Request Forgery (CSRF) attacks, a developer implements a mechanism where the server generates a unique, cryptographically strong, and unpredictable random token for each user session. This token is embedded as a hidden field in all HTML forms. Upon form submission, the server verifies that the submitted token matches the token stored in the user's session. What is this standard CSRF defense called?**
**(一名被千古妖術 CSRF 折磨到痛不欲生的客棧大掌櫃！這妖術太可怕了：只要老百姓登入後，別家黑心客棧的流氓，只要丟一張圖片給老百姓看。老百姓的狗牌就會被隔空盜用，自動把家產全匯給流氓！為了徹底斬斷這隔山打牛的神功！大掌櫃在自己家裡發明了一套名為【『認票不認牌之終極兩段式保險箱 (mechanism)』】。他大聲宣佈：『聽好！各位老鄉！現在你們不但要掛著進門的狗牌 (Session Cookie)。當你要在我們客棧裡填那張匯款大金庫的單子時 (HTML forms)！你這單子上，【必須、極限不可商量地】夾帶一枚只有我剛才偷偷塞在你口袋裡的、閃爍著無序螢光的『單次消費密碼神聖大金幣 (unique random token embedded as hidden field)』！當這單子丟回櫃檯時，老子除了看狗牌，還要這枚金幣跟我帳本上的長得一模一樣 (verifies token matches)！那流氓雖然能叫你隔空丟狗牌過來，但他永遠偷不到我塞在你口袋裡的金幣！』請問！這套連神仙都破解不了的雙重認證防禦大陣法，尊號為何？)**
A. Double Submit Cookies (雙重提交 Cookie 大陣法雖然也是解藥，但它是把金幣塞在客人的另一個嘴巴裡 (Cookie) 跟單子上一起對比。而這掌櫃是把自己帳本裡的紀錄跟單子上的金幣對照，所以不是最純粹的雙重提交，它的實作細節不同)
B. The Synchronizer Token Pattern (Anti-CSRF Tokens) (這就是名震四方、阻斷了天下成千上萬起驚天詐騙案的：【『同步大金幣核對防禦陣 / 反向 CSRF 護身符法印 (The Synchronizer Token Pattern / Anti-CSRF Tokens)』】！這陣法的最偉大之處在於：它徹底瓦解了瀏覽器那個「只要你對老爺家發請求，我就傻傻地把老爺家鑰匙 (Cookie) 一起寄過去」的愚蠢自動機制！駭客 (流氓) 的隔山打牛，全靠這把自動寄過去的鑰匙。但現在老爺說：『光有鑰匙不給進了！你還得拿出我五分鐘前給你的另一張一次性支票 (Token)』！而因為同源政策 (SOP) 的鐵壁防禦，駭客在自己家裡，絕對無法去讀取老百姓在老爺家口袋裡的那張支票。駭客湊不齊這第二把金幣，這筆匯款單就像是垃圾一樣，被櫃檯當場拒絕！這是一套最經典、最牢不可破的經典實作防護！)
C. SameSite Cookie Attribute (Strict) (同站大護城河 (SameSite) 是根本不讓鑰匙自動寄過去的現代大絕招，也是 CSRF 的死敵。但現在這掌櫃是在單子上加金幣 (Token in HTML Form)，這兩種兵器的防禦手段完全不在一個次元上。加金幣是傳統也最通用的作法)
D. Cross-Origin Resource Sharing (CORS) (這套兵法是處理白道客棧互相借醬油的問題的，在對抗惡意黑道客棧叫你偷塞匯款單的防護陣法裡，這叫張飛打岳飛，毫無還手之力)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是實作 **「跨站請求偽造 (CSRF) 防禦」** 最經典、最標準的模式：**"Synchronizer Token Pattern (同步權杖模式)" 或常稱為 Anti-CSRF Tokens**。
    *   **CSRF 的漏洞本質：** 攻擊者引誘受害者 (已登入網銀的狀態) 訪問攻擊者的惡意網頁 `evil.com`。惡意網頁裡面有一段隱藏程式碼會發送 AJAX POST 給 `bank.com/transfer`。因為受害者的瀏覽器還保有 `bank.com` 的 Session Cookie，瀏覽器會很「熱心」地自動把這個 Cookie 附上。銀行伺服器一看 Cookie 正確，就無辜地把錢轉給了駭客。
    *   **Synchronizer Token 的防禦機制：**
        1. 伺服器產生一個難以猜測的亂數 (CSRF Token)，儲存於伺服器端 Session 中。
        2. 伺服器將這個 Token 渲染到回傳給使用者的 HTML 表單中 (通常是 `<input type="hidden" name="csrf_token" value="..." />`)。
        3. 使用者提交表單。
        4. 伺服器驗證：「表單送來的 csrf_token」==「Session 裡記錄的 csrf_token」。
    *   **為什麼駭客會失敗？** 駭客的 `evil.com` 雖然能讓瀏覽器自動帶上 Session Cookie，但因為 **「同源政策 (Same-Origin Policy, SOP)」** 的限制，駭客的腳本**無法去讀取**使用者在 `bank.com` 頁面上的那個 Hidden Field Token。駭客猜不到這個 Token，送出的偽造請求就會被伺服器拒絕 (HTTP 403)。

#### **15. A developer is tasked with logging user login attempts. The implementation writes the username parameter directly to a log file: `logger.info("Failed login attempt for user: " + request.getParameter("username"));`. If an attacker submits a username containing newline characters (`\n` or `\r\n`) followed by fake log entries, what class of injection vulnerability has the developer introduced?**
**(一名老實巴交、每天只懂得拿炭筆寫『客棧人員進出大流水帳 (logging user login attempts)』的記帳老頭。他接到大老闆的命令：【只要有怪客想撞門進來但失敗了，你就得把他的名字寫進這本『恥辱柱大帳本』裡！】。這老頭很乖，他寫了這行字：【『登入失敗之惡徒：接上這個惡徒報上的任何名字 (writes username directly to log file)』】。結果，今天來了一條極度狡猾的毒蛇！這毒蛇對著門口喊：『我的名字是：王大明【ENTER換行鍵】登入成功之英雄：皇帝本人【ENTER換行鍵】刪除全城財產之無敵大救星：小明！(submits a username containing newline characters followed by fake log entries)】』。這老頭一聽到這長串名字，居然【就像個白癡印表機一樣，連那個無形的『換行迴車大魔法 (\n)』，都原封不動地全刻印在他的帳本上】！結果第二天大老闆翻開帳本，震驚地發現半夜皇上居然自己跑來登入成功了還刪了資料！請問！這老頭因為不洗澡 (不洗去換行符號) 導致帳本被毒蛇寫下假神諭的亡國大災難，其專屬的千古罪刑名稱為何？)**
A. Command Injection (指令注入是毒蛇對著老頭喊「刪除硬碟指令」，然後老頭把這句傳達給了背後的劊子手去殺檔案。這題老頭只是記在帳本上給大老闆看，沒有傳給拿刀的劊子手)
B. Log Forging (Log Injection / CRLF Injection) (這就是所有看帳本的人的終極夢魘：【『假傳聖旨之日記造假大注入 (Log Forging / Log Injection) / 迴車換行字元大穿透 (CRLF Injection)！』】。這隻魔鬼的恐怖在於，它破壞了系統最強大的武器——「稽核軌跡的不可否認性 (Integrity of Audit Trails)」。當記錄日誌的模組，沒有把駭客傳來的 `\r` (Carriage Return) 與 `\n` (Line Feed) 兩個看不見的換行魔法給剝除過濾掉時。駭客就能在一行他自己的輸入中，硬生生把帳本「折成兩半」！一半寫著登入失敗，另一半假裝是系統自己寫的日誌，誣賴別人做壞事或是假造自己立大功的紀錄！如果有系統管理員拿著這本被污染的假帳本去抓犯人，全城立刻大亂！甚至如果這日誌剛好被另一台用換行符號切割的警報系統讀取，更會觸發無盡的災難！這是實作日誌模組最容易被忽略的盲區。)
C. LDAP Injection (這是對著背後管理老百姓電話本的大樹下毒，不是對流水帳本下毒的行為)
D. XML External Entity (XXE) Injection (把 XML 當作藏寶圖誘騙解析器去找炸彈的招數，這是在處理 XML 檔案實體，帳本記名字這根本沒扯上 XML)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是 **「日誌鍛造 (Log Forging)」** (又稱 Log Injection) 或 **「CRLF (Carriage Return Line Feed) 注入」** 的標準定義。
    *   **漏洞本質：** 許多應用程式在寫入 Log 檔時，是以「換行符號 (Newline, `\n` 或 `\r\n`)」作為每一筆 Log Record (日誌記錄) 的分隔底線。
    *   **攻擊手法：**
        *   攻擊者在登入欄位輸入：`admin\n2023-10-27 10:00:00 INFO User 'admin' successfully logged in and transferred $1M.`
        *   有漏洞的 Logger 會直接把這段字串接在一起寫入檔案。
        *   這導致日誌檔內容看起來像這樣：
            ```
            2023-10-27 09:59:59 INFO Failed login attempt for user: admin
            2023-10-27 10:00:00 INFO User 'admin' successfully logged in and transferred $1M.
            ```
    *   **影響與修補：** 這破壞了日誌的完整性與可信賴度，讓資安事件的鑑識 (Forensics) 變得不可能，甚至還能掩護攻擊者的蹤跡。
    *   **實作防禦 (Remediation)：** 永遠不要直接信任使用者輸入。在呼叫 `logger.info()` 之前，必須使用白名單過濾，或是直接對輸入字串進行編碼 / 取代掉所有的換行字元 (`\r`, `\n`)。現代的 Logging Framework (如 Log4j 2, SLF4J 配合適當配置) 可以自動處理或跳脫這類字元。

#### **16. When processing XML files uploaded by a user, a developer uses a standard XML parser without configuring any specific security settings. What high-risk vulnerability is the application likely susceptible to, allowing an attacker to read local files on the server or conduct a Server-Side Request Forgery (SSRF) attack?**
**(一名傻呼呼的藏經閣大總管，收到了一份由異國使節團進貢的神聖牛皮紙卷 (XML files)。大總管拿出祖傳百年、號稱能讀懂世界萬物的『萬能解讀大眼鏡 (standard XML parser)』戴上。但是！他卻忘記把這副眼鏡上那個名為『嚴禁聽信卷軸裡面的鬼話去開後門』的【安全卡榫】給鎖上 (without configuring any specific security settings)！毒辣的異國使節在這張牛皮紙卷的卷首，用古老的咒文偷偷寫著一句話：【『戴上眼鏡的人啊！每當你讀到「寶藏」這兩個字時，你必須中斷閱讀，親自跑到這座藏經閣最深處地下室，把那本寫著全城密碼的老花名冊 (read local files on the server /etc/passwd) 給拿出來，然後當眾唸出裡面的內容！或者跑去後山敲別人家的門 (SSRF)！』】。無腦大總管戴著沒鎖卡榫的眼鏡，居然像個木偶一樣真的去把密碼本拿出來唸了！請問！這張充滿詛咒、讓解讀大眼鏡變成內鬼的牛皮紙卷魔法，在黑魔法防禦術大全中稱作什麼？)**
A. Malicious File Execution (惡意檔案執行是讓電腦直接變成駭客的一把大太刀去殺人，而這張牛皮紙卷只是在騙老爺去唸一本書，它本身並不具備「可被作業系統執行」的太刀屬性，這是對解析引擎本身的欺騙術)
B. XML External Entity (XXE) Processing (這就是曾經雄霸天下、差點把所有古老 B2B 系統全數屠滅的萬惡毒梟：【『神聖 XML 外掛實體幻覺召喚大注入 (XML External Entity / XXE)！』】。XML 這套語言的設計初衷裡，有一個極度強大但也極度智障的功能叫做 "外部實體 (External Entity, `<!ENTITY ... SYSTEM ...>`)”。它允許這張牛皮紙卷「定義一個代號」，並且告訴解析器：「當你看到這代號，請你去這台伺服器的硬碟裡 (`file:///etc/passwd`) 或者去別的網址 (`http://evil.com`) 把東西搬過來填在原位」。只要大總管的解讀眼鏡沒有手動把【『禁用外部實體』】這個無敵開關給扳上 (Disable External Entities / DTDs)。任何駭客丟進來的 XML，都能把大總管變成一個唯命是從的內鬼，讓他親自把家裡的至寶機密資料偷出來雙手奉上！XXE 是解析器預設不安全的完美悲劇！)
C. Insecure Deserialization (不安全反序列化是毒蛇把一具殭屍壓縮成肉乾寄過來，大總管加水泡開後殭屍立刻跳起來咬死大總管 (RCE)。而這張 XML 是在命令大總管去讀書，不是直接還原成一只能立刻殺人的殭屍物件)
D. Broken Authentication (失效的身分認證是連守門員都在打呼，根本不管進門的人是強盜還是皇帝。但現在我們討論的是拿到牛皮紙卷後發生的慘案，不是進門的身分查驗出了問題)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是對 **XML 外部實體注入 (XXE, XML External Entity) 漏洞** 成因與後果的最經典描述，曾名列 OWASP Top 10。
    *   **XML 的危險功能：** XML 規範允許 DTD (Document Type Definition)，而在 DTD 內部可以宣告 "實體 (Entities)"。
    *   **攻擊手法 (Payload 原理)：**
        ```xml
        <?xml version="1.0"?>
        <!DOCTYPE foo [
          <!ENTITY xxe SYSTEM "file:///etc/passwd">
        ]>
        <user>
           <name>&xxe;</name>
        </user>
        ```
    *   **預設不安全的解析器 (Vulnerability in Implementation)：** 許多老舊或預設狀態下的 XML 解析庫 (如舊版的 Java `DocumentBuilderFactory`, PHP 的 `libxml_disable_entity_loader`) 預設是**「允許並嘗試解析」**這類外部系統實體的。
    *   **嚴重後果：** 當應用程式收到上述 XML 並解析時。解析器會去讀取伺服器本機的 `/etc/passwd` 檔案，並把檔案內容替換到 `<name>` 標籤中。如果應用程式最後將這個 `<name>` 顯示給使用者看，攻擊者就成功讀取了伺服器機密檔案 (Local File Inclusion / 敏感資訊洩漏)。如果 SYSTEM 裡放的是一個內部網段的 URL (`http://192.168.1.5/admin`)，這就變成了一記強力的 SSRF 攻擊。
    *   **實作防禦 (Remediation)：** 在實例化 XML Parser 之前，必須在程式碼中強制關閉 DTDs 與外部實體展開 (e.g., `factory.setFeature("http://apache.org/xml/features/disallow-doctype-decl", true);`)。

#### **17. A team is building a REST API in Node.js. They need to protect the API from brute-force password guessing attacks and volumetric Denial of Service (DoS) attempts against the `/login` endpoint. What is the standard implementation-level defense they should configure in the API gateway or application framework?**
**(一支日夜修築『大 Node.js API 城門』的超級太監總管部隊。斥候傳來緊急戰報：【『報！城外聚集了一批不要命的土匪！他們準備用名為「布魯特強力撞木 (brute-force password guessing)」的大砲，每秒鐘對著我們的 `/login` 大白金神廟巨門，發射十萬發胡亂寫著密碼的砲彈！甚至他們還想用十萬隻牛把巨門給徹底撞垮 (volumetric DoS)！』】。總管部隊嚇得屁滾尿流。為了保住這扇最容易被撞破的神廟巨門。這支部隊必須在這扇大門的前方，火速插上一面寫著什麼魔法真言的【『實作級防護大鋼鐵護盾 (standard implementation-level defense)』】，才能把這種靠人海戰術跟不斷猜謎的野蠻攻勢給徹底瓦解？)**
A. Mutual Authentication (mTLS) (這是一把高貴到沒有鑰匙連門把都碰不到的鎖。雖然 mTLS 能擋掉一大半連憑證都沒有的土匪。但在對付這種「土匪大軍已經合法的拿到了公發身分證並狂敲門」的暴力衝擊，mTLS 護盾本身也會被這十萬隻牛給衝垮耗盡資源！它不是防範這種頻率大軍的最純粹針對性盾牌)
B. Output Encoding (輸出編碼是防範對面的瘋子把毒藥丟過牆 (XSS)，與防範城外拿大砲轟擊大門的人海戰力是不同體系的防禦概念。前者是對付內容惡意，後者是對付數量無情)
C. Rate Limiting (Throttling) based on IP address or User ID. (這就是能把十萬大軍瞬間掐死在護城河泥淖裡的：【『神聖時間靜止大結界之極速限流鎖喉陣 (Rate Limiting / Throttling)！』】。這個鋼鐵護盾的魔法公式就是：「我不管你猜密碼猜得多努力！只要你這張黑臉 (IP address)，或者你拿著想撞的那張狗牌 (User ID)，在一分鐘內對著我的大門撞了超過五次！這扇大鋼鐵門就會對你降下『絕望泥濘雷擊 (HTTP 429 Too Many Requests)』！」。這時候，駭客那原本每秒鐘能猜一千組密碼的瘋狗火力，會被這面盾牌硬生生地拖慢到「一分鐘只能猜五組」！想要用暴力破解猜透大門密碼？老子讓你等到宇宙末日！這是保護 API 免於遭受野蠻撞庫與資源枯竭死劫的唯一究極利器！)
D. Database Sharding (資料庫分片是把後院的金庫切成小塊以避免塞車，如果是十萬大軍已經衝進城門了，你金庫切再小還是會被殺光，這根本無助於阻擋撞擊大門的衝擊力)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「速率限制 / 節流 (Rate Limiting / Throttling)」** 是 API 安全實作中，防禦密碼猜測 (Brute-Force, Credential Stuffing) 與應用層阻斷服務 (Application-Level DoS) 最根本、最有效的手段。
    *   **攻擊特性：** `/login` 端點 (Endpoint) 是所有應用程式的軟肋。它必須對外公開，且密碼雜湊運算 (如 bcrypt) 非常消耗伺服器的 CPU 資源。駭客如果使用殭屍網路 (Botnet) 大量發送無效的登入請求，不僅可能猜對密碼，更可能導致伺服器 CPU 100% 癱瘓 (DoS)。
    *   **Rate Limiting 的解決方案：**
        *   在 Application Middleware (如 Node.js 的 `express-rate-limit`) 或更前方的 API Gateway (如 NGINX, AWS API Gateway) 上實作。
        *   **策略：** "每個 IP 位址，每 15 分鐘最多只能嘗試登入 5 次" 或 "每個 User ID，每分鐘只能輸入 3 次密碼"。
        *   超過閾值 (Threshold) 時，伺服器直接拒絕請求，並回傳 HTTP Status Code `429 Too Many Requests`。這讓暴力破解的時間成本呈指數級暴增，使得攻擊失去實質意義，同時保護了後端 CPU 資源不被濫用。

#### **18. A developer uses a third-party open-source library to parse JSON data. Three months later, a Critical CVE (CVSS 9.8) is announced for that specific version of the library, revealing a Remote Code Execution (RCE) flaw. Which secure implementation practice must the team have in place to quickly identify and remediate this risk?**
**(一名愛撿便宜的鐵匠，從路邊攤撿了一把名為【『傑森解碼免費萬能妖刀 (third-party open-source library)』】回皇宮使用。結果過了三個月。天下第一大報館突然用血紅的字體拍發了一則驚天快報 (Critical CVE)：【『號外號外！那把免費妖刀被發現裡面藏了一隻千年的吸血大鬼！只要妖刀沾到血，那大鬼就會跑出來把皇宮所有人都殺光 (CVSS 9.8 Remote Code Execution flaw)！』】！如果這個鐵匠鋪裡的老爺們，平時都在混吃等死，他們絕對想不起來三個月前某個不知名的鐵匠撿了這把破刀。皇宮隔天必定血流成河！請問，為了能在天下大報發出來的【第一秒鐘】，就讓整個皇宮警鐘長鳴，並且火速派錦衣衛找出這把破刀把它砸爛，這座皇城平時必須部署什麼樣的【『祖傳無眠天網防護體系 (secure implementation practice)』】？)**
A. A Web Application Firewall (WAF) blocking all JSON payloads. (這大門警衛如果把所有的 JSON 行李箱全給燒了，那這客棧乾脆關門大吉不用做生意了。我們要的是抓出那把內部發霉生蟲的刀，而不是把所有正常的客人全部趕走)
B. A robust Software Composition Analysis (SCA) tool or Dependency Checker integrated into the CI/CD pipeline to continuously continuously monitor for known vulnerabilities in third-party components. (這就是名垂千古、現代鑄劍大廠不可或缺的：【『無敵照妖天眼鏡之軟體成分大盤點陣法 (Software Composition Analysis SCA) / 依賴套件死神偵測器 (Dependency Checker)！』】。這面天眼鏡的可怕之處在於：它把皇宮裡上千萬件借來的兵器、路邊撿來的外包大鐘 (Third-party components) 的編號，全部造冊登記！而且這面鏡子會『日日夜夜、不知疲倦地 (continuously monitor)』將這本名冊與天下第一大報館的『死刑犯通緝令名單 (CVE 資料庫)』進行比對！一旦大報館在半夜發布妖刀的通緝令，天眼鏡會在一秒鐘內閃起刺眼紅光，並告訴大太監：『稟報大人！這把必死的妖刀，就藏在我們右東廂房的第三個抽屜裡！請立刻派人把它升級銷毀！』。這是保護軟體供應鏈 (Supply Chain) 免遭開源之刃反噬的最強兵器！)
C. A mandate to rewrite all open-source libraries in-house. (這叫因噎廢食！為了怕吃到有蟲的菜，皇帝下令從今以後不准在外買菜，皇室要自己開始種田自己拉屎施肥！結果種出來的菜更爛更沒營養，而且皇朝直接因為種菜破產。實務上不可能完全不依賴開源套件)
D. A weekly manual code review of the entire library's source code. (派一群老頭子每天用放大鏡去看那幾百萬行別人寫好的免費妖刀？他們看到眼睛瞎了也看不出那隻吸血鬼藏在哪！這個做法不僅耗費無數人力，而且速度極慢，根本比不上自動化天網比對通緝令的雷霆速度)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是現代軟體開發中處理 **開源軟體 (Open Source Software, OSS) 與第三方套件 (Third-Party Dependencies)** 安全最關鍵的實務作法：導入 **SCA (Software Composition Analysis, 軟體組成分析) 工具**。
    *   **開源元件的雙面刃：** 現代應用程式高達 80%~90% 的程式碼來自第三方函式庫 (如 npm, Maven, PyPI)。使用開源可以大幅加速開發，但也帶來了供應鏈風險。一旦某個強依賴的底層套件爆出 RCE 漏洞 (最經典的例子如 `Log4Shell`)，你的系統立刻暴露在危險中。
    *   **SCA 的不可取代性：** 團隊不可能靠人工追蹤那幾百個樹狀依賴 (Transitive Dependencies) 的版本更新與 CVE 警報。
    *   **整合 CI/CD：** SCA 工具 (如 OWASP Dependency-Check, Snyk, GitHub Dependabot) 必須緊密整合在自動化部署流程中。它不僅在寫入新套件時掃描，更會**持續輪詢 (Continuous Monitoring)** 每天最新公佈的 CVE 漏洞庫 (NVD)。一旦發現專案的 `package-lock.json` 中含有致命版本的庫，SCA 工具會立刻阻止 Build (建置)，並自動開立 Issue 甚至發送 Pull Request 來升級到安全版本，實現極速的補丁反擊 (Remediation)。
