# 第四套全真模擬試題 (Exam 4) - 答案與詳解本
## 領域 6：安全的軟體測試 (Secure Software Testing) (17題) - Part 1 (Q1-Q6)

---

#### **1. A security analyst is configuring a dynamic analysis tool to test a REST API. The tool is set to automatically send thousands of malformed JSON payloads, extremely long strings, and unexpected data types to various API endpoints while monitoring the application for unhandled exceptions or crashes. What specific type of testing technique is this?**
**(一名專門修理妖魔鬼怪的安防老道士，正對著皇城那扇接收香油錢的『數位大牌坊 (REST API)』佈下一個喪心病狂的陣法。這個陣法會【自動、無情、且瘋狂地，每秒鐘對著牌坊丟出幾萬包『長得像癩蛤蟆的銀票 (malformed payloads)』、『長達八萬公里的祈福絲帶 (extremely long strings)』、還有『根本不是錢的石頭跟大便 (unexpected data types)』】！丟完之後，老道士死死盯著這座標坊，看它會不會因為吃到這些亂七八糟的東西而【當場嘔吐、翻白眼、甚至直接崩塌死機 (monitoring for unhandled exceptions or crashes)】！請問，在安防界兵器譜上，這套專門用「無意義的垃圾」把系統活生生給撐死、逼出系統隱藏死穴的瘋狂陣法，名喚為何？)**
A. Fuzzing (Fuzz Testing) (這就是名震天下、以暴力狂暴著稱的：【『混沌無序垃圾大轟炸 / 模糊測試大陣法 (Fuzzing / Fuzz Testing)！』】。這套陣法是系統穩固性的終極夢魘！它的哲學是：「人類寫的測試太溫柔了，只會餵系統吃標準的狗糧。老子要餵你吃炸藥跟鐵釘！」Fuzzer 會自動生成成千上萬的「畸形資料 (Mutated Data)」，用來探測那些工程師作夢都沒想過的「邊緣條件 (Edge Cases)」。只要系統在吃了這些垃圾後崩潰 (Crash) 或是拋出未處理的異常，這就代表系統底層存在著潛在的「緩衝區溢位 (Buffer Overflow)」、「空指標提領 (Null Pointer Dereference)」或是「錯誤處理不當」。這是尋找零時差漏洞 (Zero-Day) 最強悍的動態測試兵器！)
B. Static Application Security Testing (SAST) (靜態測試是老夫子拿著放大鏡看建築藍圖抓蟲子，它不會產生任何垃圾資料去轟炸系統，更不會把系統搞當機，因為它根本沒把系統跑起來！)
C. Code Coverage Analysis (程式碼涵蓋率是老夫子在檢查「這支掃把有沒有掃過皇宮的每一個角落」，它是一個指標 (Metric)，而不是去丟垃圾的攻擊陣法)
D. Penetration Testing (滲透測試是人工帶著腦袋去尋找系統漏洞，雖然滲透測試中「可能」會用到 Fuzzing，但這題精確描述了「自動狂丟畸形垃圾找崩潰」的這個具體動作，它的專有名詞就是 Fuzzing)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 這是對 **「模糊測試 (Fuzzing / Fuzz Testing)」** 最標準、最經典的情境描述。
    *   **Fuzzing 的定義與目的：** Fuzzing 是一種自動化的軟體測試技術。它向電腦程式的輸入端 (如 API, 檔案解析器, 網路 Port) 提供大量無效、非預期或隨機的資料 (Fuzz)。其目的是監控程式是否發生崩潰 (Crash)、斷言失敗 (Failing built-in code assertions)，或發現潛在的記憶體洩漏 (Memory Leaks)。
    *   **在 REST API 中的應用：** 對 API Fuzzing 時，工具會大量變異 (Mutate) JSON/XML 結構，例如將 Integer 欄位塞入 `A` 字元，將 String 欄位塞入 100MB 的文字，藉此找出 API 處理邏輯與邊界檢查 (Boundary Checking) 的死角。這是動態分析 (DAST) 中非常進階且重要的一環。

#### **2. Which of the following vulnerabilities is Static Application Security Testing (SAST) generally LEAST effective at detecting due to its inability to understand the runtime execution environment and business logic context?**
**(在所有工匠桌上都裝有一台名為『SAST 靜態透視白骨掃瞄機』。這台機器雖然厲害，能一眼看穿工匠寫下的每一行墨水。但是！這台機器有一個致命的瞎點：【它就像個沒有靈魂的讀死書書呆子，它只懂文法，卻完全不懂這句話在戰場上「真實的意義」跟「人情世故的邏輯」 (inability to understand business logic context)】！請問，因為這個瞎點，這台掃描機對於抓出哪一種在兵法上極度狡猾的致命漏洞，幾乎是個睜眼瞎子 (LEAST effective at detecting)？)**
A. Hardcoded symmetric encryption keys. (如果你把鑰匙寫死在程式碼裡，因為這是白紙黑字的「靜態字串 (文法)」，SAST 機器用規則比對一秒鐘就能抓出這行字，這是它最拿手的項目)
B. Use of deprecated and insecure cryptographic algorithms (e.g., MD5). (如果程式碼裡寫了 `MD5.hash()`，這種「使用了禁忌字彙 (文法)」的錯誤，SAST 憑字典比對一掃就抓到了，非常有效)
C. Insecure Direct Object Reference (IDOR) / Business Logic Flaws. (這就是 SAST 掃描機永遠解不開的死穴：【『人情世故之業務邏輯大崩塌 / 與不安全的直接越權提領 (IDOR / Business Logic Flaws)！』】。你想想，程式碼明明寫著：「接收客人的單號 (ID 123)，然後從金庫拿出 123 號的黃金給他」。這在 SAST 眼裡，文法完美、沒有 SQL 注入、沒有緩衝溢位！但是！SAST 根本不知道這個「正在發送指令的客人」，他其實是 124 號乞丐，他根本無權拿 123 號老爺的黃金！這種【身分與物件之間錯綜複雜的擁有權（邏輯與授權）】，唯有在系統「真槍實彈跑起來 (Runtime) 並且帶有真實人類身分上下文」的時候才能被驗證。靜態掃瞄機讀不懂這種人類社會的邏輯，所以對這類越權漏洞幾乎束手無策！)
D. Buffer overflows from the use of unsafe C libraries (e.g., `strcpy`). (當程式碼出現 `strcpy` 這種危險函數，這也是 SAST 的守備範圍，它能輕易透過靜態分析抓出這個函數的呼叫)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「業務邏輯漏洞 (Business Logic Flaws)」** 以及其代表性的 **IDOR (越權)** 是 **SAST (靜態測試)** 的阿基里斯腱。
    *   **SAST 的強項 (Syntax/Pattern Matching)：** SAST 擅長找出「有明確程式設計模式的錯誤」(Patterns)。例如：寫死密碼 (Hardcoded Secrets)、使用了 `md5()`、字串相加組裝 SQL 語句。這些都可以在不執行程式碼的情況下，透過語法樹分析找出來。
    *   **SAST 的弱點 (Context/State Ignorance)：** IDOR (BOLA) 的問題在於邏輯。程式碼 `User target = db.getUser(request.id); target.update();` 在語法上完全合法且安全。SAST 無法判斷出「目前登入的 User session ID」與「傳入的 `request.id`」是否屬於同一個人。這需要理解應用程式的「意圖與授權邏輯」，只有人工代碼審查 (Manual Code Review) 或是具備邏輯狀態設定的 DAST / 滲透測試才能有效發現。

#### **3. During the testing phase, a QA engineer needs to verify that the application correctly handles sensitive Personally Identifiable Information (PII) without violating privacy regulations. To create a realistic test dataset that mimics production data properties without exposing actual user PII to the QA environment, which technique should the engineer employ?**
**(在演練場上，一名 QA 演練教官需要測試一套能處理【全天下老百姓身分證與生辰八字 (sensitive PII)】的點名大系統。但是，按皇朝的隱私大律法規定，這座用來演練沙盤推演的兵營 (QA environment)，【絕對、死也不准】把真實老百姓的身分證拿進來玩，萬一丟了要誅九族 (without exposing actual user PII)！可是教官又需要這些假身分證『長得跟真的一模一樣（有英文字母、有地區碼等 properties）』才能測試系統會不會報錯。請問，為了無中生有生出一堆逼真的假人來演練，教官必須使出哪一套千古障眼大陣法？)**
A. Live Production Data Cloning (把真實世界老百姓的資料，直接全部拷貝一份送到演練場？這叫帶頭犯法！這直接讓老百姓底褲看光，違反了所有隱私法規)
B. Data Masking (or Data Obfuscation / Synthetic Data Generation) (這就是名垂千古、既能應付演練又能保護老百姓的：【『千面人易容大迷宮：資料遮罩 (Data Masking) / 與無中生有之合成基因數據大陣 (Synthetic Data Generation)！』】。這套陣法是：我們可以用「演算法」把真實的『A123456789』洗牌變成『X987654321』，或者乾脆用 AI 根據身分證的規則，憑空「捏造 (Synthesize)」出一千萬筆【這世上根本不存在，但格式完美無缺的幽靈身分證】！這樣一來，點名系統依然能驗證格式對不對、身分證字號最後一碼的檢查碼能不能算得出來 (Realistic Properties)。但就算演練場被駭客攻破，駭客偷走的也只是一堆根本不存在的幽靈資料！這完美解決了測試需求與合規隱私的衝突！)
C. Symmetric Encryption using the production key (就算你把資料加了密送到演練場，如果演練場的系統拿著同一把鑰匙解密出來測試，那演練場的工匠還是看到了真實老百姓的資料，這依舊違法洩密)
D. SQL Injection (SQL 注入是駭客把金庫炸掉偷看資料的攻擊招式，跟教官想生出安全的測試用假人檔案完全不相干)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「資料遮罩 (Data Masking) / 混淆 (Obfuscation)」** 以及 **「合成數據生成 (Synthetic Data)」** 是在測試環境中保護隱私資料 (如 GDPR, HIPAA 規範的 PII/PHI) 的黃金標準。
    *   **測試環境的風險：** 開發/測試環境 (Dev/QA) 通常不如正式環境 (Production) 保護得那麼嚴格。如果直接將大把的 Production Data 拷貝到 QA 給開發者測試，一旦 QA 資料庫外流，就會造成真實災難。
    *   **解決方案：**
        *   **Static Data Masking (SDM)：** 在資料從 Prod 倒出到 QA 前，將名字改為亂碼 (John -> Xqpt)，信用卡號保留前後四碼中間補 X (`1234-XXXX-XXXX-5678`)。這稱為去識別化 (De-identification)。
        *   **Synthetic Data (合成數據)：** 更進階的做法是用工具生成完全虛假的「假名、假信箱、假信用卡」，但這些假資料符合真實資料的規則 (例如能通過 Luhn 演算法的假信用卡號)。這樣測試的功能涵蓋率不減，但隱私風險降為零。

#### **4. A penetration testing team is hired to evaluate a new web application. The client provides the team with full access to the application's source code, architecture diagrams, API documentation, and database schemas before the test begins. Which testing methodology is this client employing?**
**(一支收錢辦事的『黑影刺客大隊 (penetrating testing team)』來到了皇城腳下。沒想到，請他們來的皇帝居然無比大方！皇帝在刺客還沒動手前，就直接把這座皇城的【『四張底牌：連工匠私藏的建築藍圖、牆壁裡水管怎麼接的圖、所有大門鑰匙的形狀、甚至連城牆是用那一家磚頭蓋的全套帳本 (full access to source code, diagrams, schemas)』】，全部攤在桌上給這群刺客看得清清楚楚！皇帝說：『各位殺手，這城從裡到外全給你們看透了，現在請用力找出這座城還有什麼死穴吧！』請問，這種把自家底褲全脫光光給刺客看、讓刺客進行極限攻擊演練的方法，在兵法學上稱之為何？)**
A. Black-Box Testing (黑箱是瞎子摸象。皇帝把城門鎖死，什麼都不跟你說，只丟給你一個城門地址，讓你自己在外面猜裡面長怎樣。這跟題幹中「全盤托出」完全相反)
B. White-Box (Clear-Box) Testing (這就是名震四海、讓刺客能像神明一樣以上帝視角俯瞰整座城池發動死刑審判的：【『水晶宮極限大透視：白箱大測試 (White-Box / Clear-Box Testing)！』】。在白箱陣法中，這座城對刺客來說是完全透明的晶瑩水晶。刺客不用浪費三個禮拜在城外瞎猜牆壁有多厚，他直接看著藍圖 (Source Code) 就能精準算出「第三根柱子後面藏著一個後門 (Logic Flaw)」！這種測試法雖然不像真實世界裡駭客的瞎猜，但它能以【最極致的效率跟最深的穿透力】，把系統最深層、最難被黑箱猜到的邏輯大漏洞給徹底連根拔起！這也是找出潛在隱藏死穴最徹底的方法！)
C. Gray-Box Testing (灰箱是半透明。皇帝只給你一張簡單的地圖跟一把普通客人的鑰匙，沒給你底層的藍圖源碼。這跟題幹的「全套給你看 (Full Access)」還是差了一截)
D. Fuzz Testing (Fuzz 是用垃圾炸彈狂轟濫炸看會不會死機的自動化技術，它是一種「技術手法」，而白箱/黑箱指的是這場戰爭的「情報對稱性大框架」，層次不同)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「白箱測試 (White-Box Testing)」** (也稱 Clear-Box 或 Glass-Box) 的定義，就是測試方在擁有系統**所有內部資訊 (Full Knowledge)** 的情況下進行測試。
    *   **不同測試型態的情報等級：**
        *   **Black-Box (黑箱)：** 零情報 (Zero Knowledge)。測試者只知道 URL 或 IP。模擬外部無背景知識的駭客攻擊。花費大量時間在 Reconnaissance (偵察)。
        *   **Gray-Box (灰箱)：** 部分情報 (Partial Knowledge)。測試者通常擁有一般使用者的登入帳號 (Credentials)，或是 API Endpoints 的列表，但沒有源碼。這最常被用來測 IDOR 等越權漏洞。
        *   **White-Box (白箱)：** 完全情報 (Full Knowledge)。測試者有 Source Code, 架構圖, DB Schema。因為不用瞎猜，白箱可以極高效率地追蹤隱含的業務邏輯漏洞與邊界條件，涵蓋率最高。

#### **5. What is the primary focus and objective of a "Regression Test" in the context of the Secure Software Development Lifecycle (SSDLC)?**
**(在皇城大兵工廠裡，有一道名為『時光倒流大檢驗 (Regression Test)』的反覆必經手續。每當工匠們在昨天剛造好的一支無敵大火槍上，只為了換上一顆「看起來比較漂亮的螺絲釘 (code changes)」後！大督工就會發狂似地，把這支火槍送回去那個【『所有舊關卡全部重測一遍的大靶場』】，把這隻槍能發射子彈、能上刺刀、能抵擋水柱的所有舊功能，【死死地重新再測一次】！請問！大督工這種看似神經質、只換了個螺絲卻要把千百項舊測試全部重跑一遍的偏執狂行徑，其最核心的靈魂目的為何？)**
A. To measure how quickly the system can process one million concurrent requests. (測試能不能擋住一百萬個人排隊，那叫「負載/壓力測試 (Load/Stress Testing)」，是用來看城牆夠不夠硬的，不是檢驗昨天拔螺絲造成的影響)
B. To discover brand-new zero-day vulnerabilities in third-party libraries. (發現從沒人看過的全新漏洞那是從天上掉下來的駭客級發現 (Fuzzing/Pentesting)。我們現在做的是用『已經寫好的舊考卷』去重考一次)
C. To verify that recent code changes (e.g., bug fixes or new features) have not inadvertently broken or re-introduced vulnerabilities into previously tested, working functionality. (這就是兵工廠大督工最深沉的恐懼與 Regression Test 的唯一救贖真理：【『防範庸醫治駝背、連命都給治沒了的：新傷口復發大檢驗 (Verify changes have not inadvertently broken previously working functionality)！』】。軟體開發最恐怖的魔咒就是：【『牽一髮而動全身』】。工匠明明只為了修好大門的門把 (Bug fix)，結果這根鐵鎚一敲，居然震斷了地下金庫的防盜鎖連線 (broken previously tested functionality)！如果不做 Regression Test，這大門修好上線的當天，金庫就被偷空了！甚至更慘，新換上的代碼把五年前好不容易補好的 SQL 注入漏洞又給帶回來了！所以，回歸測試的目的就是宣告：『老子不管你今天加了什麼神仙功能，你【絕對不准】把我昨天本來活得好好的舊系統給搞壞！』這叫守住底線！)
D. To analyze the source code for hardcoded passwords. (看源碼抓密碼這是靜態白骨掃描機 (SAST) 的守備範圍，不是把槍拿去靶場測試功能有沒有壞掉的回歸測試)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「回歸測試 (Regression Testing)」** 的終極定義：確保過去運作正常的程式碼與功能，不會因為這次的「新程式碼合併 (New Commit, Bug Fix, Feature Addition)」而產生退化 (Regress) 或損壞。
    *   **在資安 (SSDLC) 的意義：**
        *   **Security Regression (安全回歸)：** 當開發者為了解決漏洞 A 修改了驗證邏輯，很有可能不小心把原本正常的權限控制模組 B 給改壞了，導致一個舊的安全漏洞重新暴露出 (Re-introduced vulnerabilities)。
        *   為了防範這種 "修一漏二" 的慘劇，所有的單元測試 (Unit Tests)、整合測試 (Integration Tests) 與自動化安全掃描，都必須在每次程式碼變更 (每次 CI Pipeline) 時全部重新跑一遍，這就是 Automated Regression Testing。

#### **6. A security testing team integrates a Dynamic Application Security Testing (DAST) tool into the deployment pipeline. The tool interacts with the running web application exactly as a normal user would, clicking links and submitting HTML forms to find vulnerabilities like Reflected XSS. What is the most significant limitation of DAST tools compared to SAST tools?**
**(兵工廠裝了一台名為『DAST 蒙眼瘋狗機器人』在前線的演練場裡。這隻瘋狗完全不看工程圖紙！它就像個普通的客人一樣，跑到客棧大門口，對著每個按鈕狂踩、對著每個投訴箱狂丟塗滿毒藥的信件 (submitting HTML forms)，藉此來看客棧會不會中毒吐血 (Reflected XSS)。雖然這瘋狗找出來的毒都是千真萬確、真正活著的漏洞。但是！這隻不看圖紙的瘋狗，跟那台坐在辦公室裡把藍圖看透的『SAST 白骨透視機』相比，它有一個最讓大督工頭痛欲裂的【先天致命瞎點/殘疾 (significant limitation)】。這瞎點是什麼？)**
A. DAST tools cannot detect vulnerabilities in deployed, running code. (大錯特錯！DAST 蒙眼瘋狗的使命就是在「已經跑起來的前線跑道上 (deployed, running code)」發動攻擊，這是它的天職，不是它的殘疾)
B. DAST tools are prone to a high rate of False Negatives because they cannot "see" the backend source code to identify exact line numbers, and they struggle to navigate complex authentication workflows or single-page applications (SPAs) effectively. (這就是瞎眼瘋狗機器人永遠無法跨越的兩道地獄高牆：【『盲人摸象的黑箱悲哀 (High False Negatives) 與錯綜複雜的迷宮困局 (Struggle with Workflows)！』】。首先，因為瘋狗看不到背後的藍圖，它只能從大門口丟毒藥。如果客棧有 100 條隱藏的地道沒放路標，瘋狗看不見，就永遠不會去測那 100 條地道 (造成深層漏洞被漏掉的 False Negatives 偽陰性)！而且就算它把客棧炸了，它也只能跑回來含糊地喊：「大門按鈕有毒！」。它【絕對指不出】是藍圖上的第幾行程式碼寫錯了 (no exact line numbers)，這讓修復異常痛苦。第二，現代客棧像個大迷宮 (SPAs)，甚至要拿著九張不同身分的通行證才能走到金庫 (complex authentication)。這隻笨狗經常卡在第一道登入大門不會填驗證碼，導致後山所有的大寶殿它連摸都摸不到！這就是它的致命殘疾！)
C. DAST tools scan too fast and consume too much CPU on the developer's laptop. (DAST 需要用網路發送幾千個 HTTP Request 還有等伺服器回應，速度慢得像烏龜一樣。SAST 掃源碼才叫快。所以 DAST 絕對不會被說成 scan too fast)
D. DAST tools only support older languages like C++ and COBOL. (這完全說反了！DAST 是對著 HTTP Web 發測試的，只要是網頁它都能點，它才不管你在後端是用 Node.js, Python 還是 Java 寫的，這叫技術語言無關性 (Language Agnostic)，這是它的優點而非限制)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 點出 **「動態測試 (DAST, Black-Box)」相對於「靜態測試 (SAST, White-Box)」的兩大先天缺陷。**
    *   **缺陷一：無法指出源碼位置。** SAST 在報錯時，會精準地說 "Main.java Line 45 SQL Injection"。但 DAST 是從網路上攻擊運作中的應用程式，它只能回報 "URL /api/search?q=test has Cross-Site Scripting"。開發者必須自己去成堆的原始碼中，通靈找出 `/api/search` 到底是哪一段 Code 負責渲染的。
    *   **缺陷二：爬蟲迷航 (Crawling Limitations)。**
        *   **認證牆 (Authentication Wall)：** 很多應用程式有複雜的 OIDC 登入、多重要素驗證 (MFA)。DAST 工具的爬蟲 (Spider) 必須被極其小心地設定，否則它可能根本登入不進去，導致只能掃瞄登入頁面 (涵蓋率不到 1%)。
        *   **現代前端框架 (SPA - React, Angular)：** 現代網頁不是單純的 `<a href>` 連結，而是透過 JavaScript 動態渲染畫面。傳統的 DAST 爬蟲很難理解那些綁定在 `onclick` 事件背後的複雜前端路由 (Client-side Routing)，導致大量功能遺漏，產生高度的「偽陰性 (False Negatives - 系統有病但機器沒檢查出來)」。
