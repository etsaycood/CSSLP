# 第四套全真模擬試題 (Exam 4) - 答案與詳解本
## 領域 6：安全的軟體測試 (Secure Software Testing) (17題) - Part 2 (Q7-Q12)

---

#### **7. Interactive Application Security Testing (IAST) has emerged as a hybrid testing approach. How does IAST primarily differ from traditional SAST and DAST in its operational deployment?**
**(在兵工廠測試兵器譜上，近年來出現了一尊名為『終極大融合：IAST 體內寄生大魔神 (Interactive Application Security Testing)』的神兵！這魔神自稱集合了『只會看圖紙的瞎子 SAST』與『只會在門外瞎撞的瘋狗 DAST』兩者的靈魂。而且，這尊魔神在戰場上的『佔位佈陣法 (operational deployment)』更是詭異到了極點！請問，這隻魔神是如何用一種前所未見的變態方式，趴在測試場上抓出漏洞的？)**
A. IAST requires physical hardware appliances to be installed in the data center. (這是十幾年前買超大鐵盒防火牆 (Physical Hardware) 的老路子，現在雲端時代誰還在裝這個，IAST 是純軟體解決方案)
B. IAST operates entirely offline without running the application. (全下線不跑死機，這就是上古時代的瞎子 SAST 看死圖紙。IAST 是要活捉的，絕對不是 Offline)
C. IAST involves deploying an agent (or instrumentation) directly *inside* the application's runtime environment (e.g., JVM or CLR) to monitor execution, data flow, and memory usage in real-time as the application is exercised (by automated tests or manual exploration). (這就是讓全天下工程師嘆為觀止的：【『人神合一之體內寄生大監控 (Deploying an agent inside the runtime environment)』】！這尊魔神的變態之處在於：它【不站在】系統外面看，它直接化化身為一隻微小的蠱蟲 (Agent / Instrumentation)，【活生生地鑽進了系統大腦的最深處 (JVM 或 .NET CLR)】！然後，當外部的瘋狗 DAST 或是 QA 人員在點擊網頁時 (exercised by automated tests)。這隻躲在腦袋裡的蠱蟲，就會在第一排搖滾區，清清楚楚地看到：「哇！外面進來了一串 SQL 單引號毒藥 (Data Flow)！而且我親眼看到這毒藥流到了資料庫準備引爆 (Execution)!」！因為它在體內，它還能順手撕下這段神經元，直接精準回報：『報告大爺！這是 `UserDao.java` 第 66 行中的毒 (SAST 的精確度)！』。這種結合動態刺激與靜態精準定位的體內寄生術，就是現代 IAST 最無敵的核心架構！)
D. IAST relies solely on manual code review by senior developers. (那是人工通靈抓大蟲，這世界上沒有任何一家公司付得起幾百個老頭子純手工看千萬行代碼的薪水。IAST 是百分之百的自動化監控儀器)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是對 **「互動式應用程式安全測試 (IAST)」** 運作原理最標準、最核心的描述。
    *   **痛點：** SAST (靜態分析) 看得到程式碼地圖，但不知道哪些路線是死的 (導致高誤報率 False Positives)。DAST (動態掃描) 知道系統哪裡會崩潰，但報不出是哪行程式碼惹的禍，除錯困難。
    *   **IAST 的解法 (Instrumentation / 裝載探針)：**
        *   開發團隊在測試環境的應用程式伺服器 (如 Tomcat, Node.js runtime) 啟動時，掛載一個 **IAST Agent (代理程式)**。
        *   這個 Agent 會在程式被載入記憶體 (Runtime) 的瞬間，對位元組碼 (Bytecode) 進行**動態插樁 (Dynamic Instrumentation)**。
        *   接下來，只要有人 (QA 人員手動點擊、Selenium 自動化 UI 測試腳本、甚至是 DAST 掃描器) 對應用程式發出 HTTP 請求。Agent 就能在**記憶體內部 (Inside-Out approach)**，全程追蹤這個使用者的輸入字串，是怎麼流經各種函數、ORM 框架，最終到底有沒有掉進危險的 Sink (如 `Runtime.exec()` 或是 `Statement.executeQuery()`)。
        *   這完美結了 SAST (能指出 100% 精準程式碼行號) 與 DAST (有真實的 Payload 數據流、幾乎零誤報 False Positive) 的雙重優勢。

#### **8. A developer wants to ensure that a newly written function specifically rejects input strings that exceed 50 characters, throwing a specific `ValidationException`. The developer writes an automated script that passes a 51-character string to the function and asserts that the `ValidationException` is indeed thrown. What type of test is this?**
**(一名老鐵匠為了測試剛打好的一面『拒絕妖言惑眾之終極小鐵盾 (newly written function)』。他對這盾牌設下了一道死命令：只要有超過半尺長 (exceed 50 characters) 的毒箭射過來！這個鐵盾必須立刻、毫不猶豫地大喊一句暗語：【『哇呀！這箭太長老子擋不住 (ValidationException)！』】。為了確保這盾牌真的會大喊。老鐵匠親自動手，削了一支剛剛好五十一公分長 (51-character string) 的箭射向它，然後站在旁邊死死聽著，聽這盾牌到底有沒有確實大喊出那句保命真言 (asserts exception is thrown)。請問，老鐵匠這種『故意拿毒藥餵盾牌看它會不會拉肚子 (Negative Testing)』的超微觀測試法，屬於哪種陣法類別？)**
A. A Unit Test (Negative Testing) (這就是名震天下、最吹毛求疵的：【『微觀顯微鏡之單一細胞大拷問 (Unit Test) / 與逆向思維之找死大演練 (Negative Testing)！』】。這老鐵匠幹了兩件事：第一，他只測試這面盾牌本身，他沒有把盾牌裝到戰車上去測試 (這叫 Integration 整合測試)，這就是純粹的【單元測試】。第二，他沒有餵給盾牌一條合法的 20 公分好箭 (Positive Testing)。他【偏偏故意】找了一根 51 公分的毒箭，就是想看這盾牌在面對超出界線的攻擊時，會不會按照規矩死去 (Throw Exception)。這種測試系統『在遭遇惡意與異常輸入時的崩潰姿態是否優雅安全』的測試，就稱作【負面測試】！兩者結合，這題就是利用單元測試框架來實施負面邊界攻擊。)
B. A Penetration Test (滲透測試是人工帶著腦袋試圖把整座城池給炸毀。老鐵匠只在測試一塊小鐵盾的邊界字數，這層級太低了。而且 Penetration Test 通常在講網路與應用系統層級，不會用來形容「測試一個 function 回傳的 Exception 類別」)
C. A User Acceptance Test (UAT) (老百姓验收是把戰車開到大街上讓老百姓買單！老百姓哪懂什麼叫做函數拋出 `ValidationException` 這種只有死工程師才看得懂的神經病暗號)
D. A Load Test (負載測試是拿十萬支箭同時射這個盾牌看它什麼時候碎掉。這題老鐵匠只射了一支 51 公分的箭，他不是在破壞壓力，他是在定點測試字數邏輯)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 這是對 **「單元測試 (Unit Testing)」** 以及其中針對例外處理的 **「負面測試 (Negative Testing)」** 最經典的範例。
    *   **Unit Test (單元測試) 的層級：** 測試層次最低、最細，專注於單一函數 (Function) 或方法 (Method) 的邏輯。題幹明確指出 `passes a 51-character string to the function`。
    *   **Negative Testing (負面測試 / 異常測試) 的精髓：** 大多數新手只會寫 Happy Path (例如傳入一個 10 字元的合法字串，Assert 函數回傳 True)。但在資安領域 (Secure Software Testing)，你更必須測試 **"當傳入絕對不該被接受的資料 (如：過長、Null、特殊字元) 時，系統有沒有被防禦機制擋下來，拋出正確的 Exception，而不是門戶大開崩潰"**。
    *   這個 51 字元的測試，正是在驗證 "Input Validation (輸入驗證 / Boundary Check)" 的實作是否正確無誤。

#### **9. During a security assessment, the testing team decides to perform "Penetration Testing" rather than just a "Vulnerability Scan." What is the fundamental, defining difference that elevates an assessment to a true Penetration Test?**
**(一名老皇帝想知道自己的皇城安防到底有多穩固。大太監獻上一計：『皇上，我們要找人來做【只在城外用望遠鏡看一圈的「弱點大掃描 (Vulnerability Scan)」】？還是要找那種真正不要命的死士，來一場真刀真槍的【「血腥終極無底線滲透大演練 (Penetration Testing)」】？』老皇帝困惑了：這兩個詞聽起來不都是找洞鑽嗎？究竟是什麼樣【最殘酷、最血淋淋 (defining difference)】的界線，把這兩個名詞一分為二，決定了到底是小孩子過家家、還是真正的皇城血鬥？)**
A. Penetration testing only uses automated tools, while vulnerability scanning is purely manual. (完全講反了！！弱點掃描 (Nessus, Qualys) 就像一台不帶感情的自動化 X 光機，只會照圖表開單子。滲透測試才是真正由【天下最狡猾的人類大腦 (Ethical Hackers)】帶隊，純手工加上工具輔助的頂級藝術)
B. Vulnerability scanning is only performed on source code (SAST). (弱點掃描也可以對著網路 IP 掃描 (DAST / 基礎設施掃描)，所以說它只掃源碼是錯誤的)
C. Penetration testing actively involves the *exploitation* (or attempted exploitation) of identified vulnerabilities to prove the risk, determine the depth of access achievable, and demonstrate the actual business impact, whereas a scan merely reports potential flaws. (這就是能讓文武百官鴉雀無聲的：【『死傷見血之真實屠城大驗證 (Exploitation and Proof of Impact)！』】。弱點掃描機 (Scan) 跑完後，只會丟給你一本厚達一千頁的天書，上面冷冰冰地寫著：『報告皇上，大門右邊可能有一塊鬆動的磚頭 (potential flaws)』。看完之後所有文武百官都在猜，這塊磚頭到底能幹嘛？沒有人知道！【但是！滲透測試不一樣！】滲透刺客看到這塊鬆動的磚頭，會當著皇帝的面，【徒手把這塊磚頭挖出來、鑽進地道、然後殺上金鑾殿，把皇帝頭上的皇冠摘下來放在桌上 (Exploitation and demonstrate business impact)】！刺客用鮮血證明了：『皇上你看見了沒！這不只是一塊鬆動的破磚！這是能讓天下易主、國破家亡的極大死穴！ (proof the risk / depth of access)』這叫有圖有真相、有皇冠有定論！)
D. Penetration testing only looks at the network perimeter firewalls. (滲透測試會從大門壁壘 (perimeter) 再殺到後宮 (internal network)，甚至殺進皇上的大腦帳本 (Web Application Pentest)，它絕對不只看大門而已)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是資安業界 (包含 CISSP, CSSLP 等 (ISC)² 認證) 對 **Vulnerability Assessment/Scan (弱點掃描)** 與 **Penetration Testing (滲透測試 / Pen Test)** 最核心的本質區別。
    *   **Vulnerability Scan (弱點掃描)：廣度大於深度。** 工具 (如 Nessus, OpenVAS, Burp Scanner) 利用已知的特徵憑證 (Signatures/Plugins) 探測系統。結束後，產出一份包含幾百個「潛在風險 (Potential Vulnerabilities)」的報告。它**止於發現，不負責證明**。誤報率 (False Positives) 極高。
    *   **Penetration Testing (滲透測試)：深度大於廣度。** 由人工 (Ethical Hacker) 主導。它的精髓在於 **"Exploitation (漏洞利用/實戰開採)"**。
        *   也就是說，當駭客掃描出一個可能的 SQL Injection 漏洞後。他不會只在報告上寫一行字。
        *   他會真正去寫一段 Exploit Payload，試圖**越過界線**，把資料庫裡的 Administrator 密碼 Hash 偷出來 (Depth of access)。破解密碼後，登入系統，甚至發動 Pivot (橫向移動) 攻擊內部網路其他機器。
        *   這目的是為了向高層 (C-Level) 證明：這個技術漏洞在現實中能造成極嚴重的**業務毀滅性打擊 (Business Impact)**，消除所有「這很難利用、駭客不會在意啦」的僥倖藉口。

#### **10. An organization is planning a "Bug Bounty" program. What is the primary strategic benefit of implementing a public bug bounty program as part of the overall security testing strategy?**
**(皇朝的一名大將軍，嫌自己家養的這群錦衣衛兵工廠太過沒用，每天只會打瞌睡看舊藍圖。某天，將軍大筆一揮，在城牆上貼出了一張震驚天下的：【『億萬黃金懸賞！萬毒朝宗大英雄榜 (public bug bounty program)！』】！榜單上寫著：『不管是哪個山頭的寨主、哪個國家的刺客。只要誰能找出這座京城的一處新死穴，老爺當場發給你一百兩黃金！童叟無欺！』。請問！將軍這種花老本錢、甚至不惜引狼入室讓全天下高手來圍毆自己家客棧的瘋狂戰略，其最深不可測的【戰略價值 (strategic benefit)】到底圖什麼？)**
A. It completely replaces the need for internal QA testing teams. (這叫引鴆止渴的自殺行為！外面的野狐禪刺客不管你這牆壁的顏色對不對，他們是來放炸彈的。如果你把家裡的監工（QA）全火革了，那這座城連給老百姓住人都不行，連個買賣都做不了。Bug Bounty 是最後一道甜點，絕對不能替代正餐！ (Complement, NOT Replace))
B. It guarantees that the software will be 100% bug-free. (就連神仙也不敢保證皇城 100% 沒漏洞。這榜單只會減少致命漏洞存在的機率，絕對不可能滅絕蟲子)
C. It leverages the crowdsourced expertise of independent security researchers to continuously discover complex edge-case vulnerabilities that internal automated tools and time-boxed penetration tests likely missed. (這就是能讓皇城長治久安的千年大計：【『借天下英雄之大腦、納四海神仙之絕學的「群眾外包極致檢驗大陣 (Crowdsourced Expertise)」！』】。大將軍精得很，他知道這世上最強的白骨探照儀器 (SAST/DAST)，甚至是他自己家裡那幾個閉門造車、視野狹隘的錦衣衛老爺 (Internal Pentester)。他們在短短兩週的演習內 (time-boxed penetration tests)，是絕對找不出最刁鑽的「神仙級邊界疊加組合技大漏洞 (complex edge-case vulnerabilities)」的！但是！外面的世界有成千上萬名天才瘋子 (independent researchers)！他們可以花半年時間，為了那一百兩黃金，日以繼夜地從成千上萬個意想不到的死角，把這皇城扒開來檢查！這種「集結合球最強獵犬的無時差跨界追殺網 (continuously discover)」，是任何一家正規軍花多少錢都僱不出的終極防禦線！)
D. It automatically fixes the bugs found in the source code. (這些賞金獵人只負責拿黃金跟遞上一張寫著漏洞的白紙報告，叫他們幫你改藍圖抓蟲，門都沒有！修 BUG 還是得你家自己的工匠加班熬夜去修，不可能自動修好)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是對 **「漏洞懸賞計畫 (Bug Bounty Program, 如 HackerOne, Bugcrowd)」** 戰略價值的最佳描述。
    *   **傳統資安測試的盲點：**
        *   內部團隊與自動化工具：視野固化 (Tunnel Vision)，掃描工具有極限。
        *   傳統滲透測試 (Point-in-Time Pentest)：通常是由 2~3 位滲透工程師，被限制在短短 2 雙週內完成的「定時、定點、定資源 (time-boxed)」測試。
    *   **Bug Bounty 的補足優勢 (Crowdsourcing)：** 透過開放式的懸賞計畫 (Crowdsourced Security)，你能僱傭到全世界數千位頂尖的白帽駭客 (White-Hat Hackers)。
        *   **多樣化技能：** 每個人專精領域不同 (有人專攻越權、有人專攻密碼學、有人專攻前端 Web3)。
        *   **持續性 (Continuous)：** 只要你的系統還在網路上，就永遠有人在幫你測 (不限時間長短)。這能在最新 CVE 或新概念攻擊手法出現的第一時間，就幫你挖出那些複雜的邊角案例 (Edge-cases) 或商業邏輯鏈接攻擊漏洞 (Chained logic flaws/Exploit Chains)。
    *   **重要注意事項 (常見陷阱選項 A 的解釋)：** Bug Bounty 絕對不應該取代內部既有的 SSDLC 流程 (SAST, DAST, Peer Review, QA)。如果連基本的 Cross-Site Scripting (XSS) 都要靠外部獵人領幾千美金來告訴你，這代表你內部的自動化防線 (Shift-Left) 完全失靈，反而會導致巨大的預算浪費。

#### **11. A developer is configuring a Continuous Integration (CI) pipeline. They want to ensure that if a developer commits code that introduces a known critical vulnerability (e.g., SQL Injection), the build process will immediately stop and notify the team. Which specific metric or mechanism is used to enforce this automatic stoppage?**
**(一名看守著『九轉兵器大洪爐鑄造流水線 (CI pipeline)』的大太監。大太監接到了一道死命令：如果在成千上萬個送進來火爐的兵器藍圖中，只要發現任何一張藍圖上畫了一隻會招來洪水的『單引號魔術大毒蛇 (Critical vulnerability SQL Injection)』。這座大洪爐的輸送帶，必須【立刻、當場、絕對不接受任何借口地卡死跳電 (build process will immediately stop)！不准這塊毒鐵進入下一關打磨！】。請問，這大太監為了能讓輸送帶自動跳電，他必須在大爐前設置一道什麼樣名為『生殺大權死亡門檻』の終極防衛機關？)**
A. Setting a "Quality Gate" (or Security Gate) failure threshold based on SAST/DAST scan results. (這就是讓無數粗心大意的小工匠哀壕的：【『無情大鍘刀：絕殺終止大陣法之自動大鐵柵欄 (Quality Gate / Security Gate)！』】。這道鐵門是用鮮血寫成的門檻法典 (failure threshold)。大太監只要在門檻上寫下：「只要前面那台白骨大眼探測機 (SAST/DAST) 回報，這批藍圖裡蟲子等級超越『Critical (致命級) > 0』！」。只要條件一觸發，這個品質大柵欄就會轟然落下！這條流水線 (Build Process) 就會直接報廢成紅色 (Failed Build)，而且警報大作 (notify the team)！這隻毒蛇，連走到下一步去裝上輪胎的資格都沒有，這就做到了實踐極致左移防禦的最完美殺手鐧！)
B. Enforcing Code Coverage metrics to reach 100%. (程式碼涵蓋率 100% 只是保證說這藍圖「每一行都被掃把掃過了」，但他就算是 100% 也看不出來裡面藏的究竟是金子還是毒藥老鼠屎。而且實務上 100% 涵蓋率是個神話，不是擋毒藥的紅線)
C. Utilizing a Web Application Firewall (WAF) blocking rule. (WAF 護城河大盾是擺在城外接客的時候，去擋強盜砲火的最後一道肉盾。現在這藍圖連大門都還沒造出來在開發爐子裡，在這時候根本沒有能套用 WAF 的目標物)
D. Running a stress test for 24 hours. (你給這個藍圖做一萬下伏地挺身 (壓力測試)，這只會累死伺服器，但它根本不會告訴你這裡面有沒有藏著單引號毒蛇 (SQLi)，更不會因此讓流水線跳電來抓安全漏洞)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 在 DevSecOps 或 CI/CD Pipeline 實務中，利用 **「安全品質閘門 (Quality Gate / Security Gate)」** 是強制阻斷有漏洞的程式碼流入正式環境的最有效手段。
    *   **CI Pipeline 流程：** 開發者 Commit Code -> CI Server (如 Jenkins/GitLab CI) 觸發 -> 編譯 (Build) -> 執行 Unit Tests -> 執行 SAST / SCA 掃描。
    *   **Quality Gate 的運作方式：** 當這些掃描工具 (SonarQube, Checkmarx 等) 完成掃描後。CI Server 會讀取報告結果。管理員事先在系統上設定好了 Thresholds (閾值)。例如：`Fail the build if (Critical vulnerabilities > 0) OR (High vulnerabilities > 5)`。
    *   如果在 SAST 報告中真的發現了一個可以導致 SQL Injection 的 High severity flaw，這個 Threshold 就會被打破。Pipeline 就會把狀態標示為 "Failed (紅色)"，後續的打包 (Dockerization)、部署到 Staging 環境的動作會全部立刻中止 (Build Breakage)。這保證了「已知毒藥絕不上線」的政策底線。

#### **12. When evaluating the effectiveness of a security testing tool, the security team notes that the tool frequently flags legitimate, safe code as a "Critical SQL Injection vulnerability," forcing developers to waste hours investigating non-issues. In security testing terminology, what is this undesirable outcome called?**
**(一名老爺為了抓賊，花八萬兩黃金買回了一頭宣稱能聞出所有賊仔氣味的『天犬探測雷達 (security testing tool)』！沒想到，這頭天犬簡直是個神經病小丑！老爺家裡的老管家只是在廚房切個菜、寫了一段正常無比幫老爺算帳的數學公式 (safe, legitimate code)。這頭天犬居然像發了瘋一樣狂吠不止，大喊：『老爺有賊啊！廚房裡有可以屠城的單引號大毒藥 (flags safe code as Critical SQLi)！』。結果老爺嚇得滿身大汗帶了一百個衛兵去廚房查了半天，發現根本就只是隻小青蛙 (wasting hours investigating non-issues)！這頭瘋狗天天狼來了，最後老爺氣得想把狗殺了。請問，在兵器驗收大全裡，這種「把好人說成是壞人」的胡亂指控冤錯假案，專有名詞叫什麼？)**
A. A True Positive (真陽性是這隻天犬真的聞到了小偷而且抓出一包毒藥，這叫英雄。而不是像這頭瞎眼瘋狗一樣亂抓錯人)
B. A False Negative (偽陰性是小偷把刀架在老爺脖子上了，這頭天犬還在睡大覺說天下太平。這也是死罪，但這是「漏抓小偷」，不是「抓錯好人」。)
C. A False Positive (這就是那隻讓全天下所有開發工匠恨得牙癢癢、每天發狂怒砸這頭雷達瘋狗的：【『狼來了之終極詐欺大騙局：偽陽性 (False Positive / FP / 誤報)！』】。這頭瘋狗叫了 (Positive/有病)，但事後查證發現這根本是它瞎猜的、根本沒病 (False/假的)！在現代自動化白骨掃描機 (SAST) 的身上這個病徵極端嚴重。如果一天報五百個偽陽性 (False Positives)。不到三天，所有的工匠都會氣到把「來自雷達瘋狗的警報」全部設定為垃圾信件靜音！這就產生了『警報疲勞 (Alert Fatigue)』的大災難，最終導致真正的狼 (真的木馬) 進城時，再也沒人理會機器的警報而導致城池覆滅！所以測試工具最大的價值，就是用最高深的演算法去降低這該死且擾民的偽陽性！)
D. A True Negative (真陰性是廚房沒小偷，這頭狗狗也很乖地趴著沒叫，天下升平。這代表工具聰明、正常發揮)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是資安測試工具評估指標中最基礎的概念。**將安全的/正常的程式碼誤判為有漏洞**，稱為 **「偽陽性 (False Positive)」或「誤報」**。
    *   **安防四象限矩陣定定義 (Confusion Matrix in Sec Testing)：**
        *   **True Positive (真陽性 / 命中)：** 系統有漏洞，工具大喊有漏洞。這是最好的。(Good Alert)
        *   **True Negative (真陰性 / 無事)：** 系統很安全，工具沒有發報。這是應該的。
        *   **False Positive (偽陽性 / 誤報 / 狼來了)：** 系統很安全，但工具狂報說有致命漏洞。這會造成開發者極大的**「警報疲勞 (Alert Fatigue)」** (Developer Friction/Time Waste)。這是多數 SAST 工具的通病。
        *   **False Negative (偽陰性 / 漏報 / 睡死)：** 系統存在嚴重漏洞，但工具掃完說 "100% 安全綠燈"。這最危險，因為它給你虛假的安全感 (False Sense of Security)，讓你有恃無恐地帶著漏洞上線，結果第二天就被駭客入侵。
    *   選購資安工具時，往往是在 "False Positives (寧可殺錯不可放過/嚴格)" 與 "False Negatives (減少太吵引發疲勞/寬鬆)" 之間根據企業風險胃納尋找平衡點。
