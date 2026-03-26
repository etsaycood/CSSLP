# 第三套全真模擬試題 (Exam 3) - 答案與詳解本
## 領域 6：安全的軟體測試 (Secure Software Testing) (17題) - Part 2 (Q10-Q17)

---

#### **10. An architect is reviewing the output of a newly installed SAST tool. Over 90% of the reported "Critical SQL Injection Vulnerabilities" are found to be completely harmless because the variables flagged by the tool are internal system constants that never actually process external user input. In security testing terminology, what is the specific classification for these inaccurate, time-wasting automated alerts?**
**(一名老謀深算的大都督，正皺著眉頭審閱一台昨日剛花重金買回來的高階『紙上查水表捉妖機 (newly installed SAST tool)』所吐出的一疊像小山一樣高的大報告。結果！這台號稱神兵利器的機器，上面居然狂閃紅燈，尖叫著說我們家大軍裡面有『高達九成都是中了最致命 SQL 隱碼大法劇毒的絕症 (90% reported Critical SQL Injection)』！大都督嚇出一身冷汗，親自帶隊下去一條一條重新翻驗屍體。卻差點沒被這台破機器給活活氣死！原來這台破機器指控的那九成所謂的『劇毒變數』，根本就他媽的是【我們寫死在程式碼最深處、當作系統齒輪核心使用、這輩子【絕對永遠不會去碰觸或沾染到任何半滴城外酸民口水的『絕對安全、無堅不摧之系統內部常數霸體 (internal system constants that never actually process external user input)』啊！】！請問，在安檢老爺們的字典裡。對於這種猶如村口那隻一看到自己人也發瘋亂吠、整天浪費大家生命時間跑去確認的『瞎眼放羊的機器狗大廢話警告 (inaccurate, time-wasting automated alerts)』。尊號為何？)**
A. True Positives (這是你真的抓到了潛伏的間諜，而不是這台機器的廢話)
B. False Positives (這就是這群自動化捉妖機最被工程師詬病、那天天『亂按火警假警報、把好人當賊抓、猶如神經質老太婆般擾民的世紀大笑話：【『偽陽性大冤案 / 假陽性誤報 (False Positives)』】！)
C. True Negatives (這是機器說他不是賊、且他真的不是賊的天下太平和平景象)
D. False Negatives (這是機器眼瞎把真正的江洋大盜當成好人放進城的致命大漏網之魚)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「偽陽性 (False Positives，FP)」** 是 SAST (靜態分析) 工具最致命的痛點。
    *   **名詞解釋：** "Positive" 代表工具大叫 "我找到漏洞了！"，"False" 代表這個大叫是 "錯誤的、假的"。也就是常聽到的「誤報 / 狼來了」。
    *   工具如果誤報率高達 90%，開發團隊會被淹沒在成千上萬條垃圾警告信裡面。最後導致工程師發生 "警報疲勞 (Alert Fatigue)"，把那個工具直接靜音關掉。這樣就算裡面真的藏著 10% 致命的真漏洞 (True Positives, TP)，也會被一起沖進馬桶裡忽略掉。
    *   (補充：另一個極端是 False Negatives 偽陰性，代表工具沒叫，但其實有漏洞，這叫漏報，通常 DAST 工具比較會發生漏報)。

#### **11. After a development team finishes writing Unit tests for all individual components, the QA team begins combining these individual microservices to verify that they securely authenticate and transmit data correctly when talking to each other across the network bus. They are testing the "mesh" where Service A passes a token to Service B. What level of software testing is being performed?**
**(造車工坊裡，當那群手拿顯微鏡的工蟻們，終於把一顆顆的引擎火星塞跟小齒輪都單獨打磨測試完畢後 (finishes writing Unit tests for individual components)。大總管下達了下一階段的軍令：『聽著！現在把那些散落一地、已經測好硬度的單兵零件跟微小妖精，通通給我用鐵鍊拴起來綁在一起 (begin combining these individual microservices)！我們要來測試一下，當『A 堡壘的傳令兵』拿著聖旨，要穿過那危機四伏的網路線深谷，去敲『B 堡壘的城門』時。他們有沒有【乖乖地講好暗號 (securely authenticate)、且送過去的聖旨有沒有半路被掉包 (transmit data correctly when talking to each other)！】』請問這種把積木拼起來，【專門驗證他們之間那條肉眼看不見、用來對話的『神經網路大橋樑 (testing the mesh)』】。這種大陣章的檢驗儀式，層級名喚為何？)**
A. Unit Testing (這已經被超越了，不是那些螺絲釘單獨測試的顯微鏡領域)
B. Integration Testing (這就是當單兵組合變成連體嬰陣容後，專門抓出那群傢伙彼此間【『溝通不良火拼、插頭接反大斷線、橋梁互毆之系統整合大考驗 (Integration Testing)』】！)
C. User Acceptance Testing (UAT) (這是請大老闆來坐車看舒不舒服的驗收，不用去管引擎管線有沒有接對)
D. Fuzzing (這是暴力亂丟垃圾測試器，這不是用來確認 A 跟 B 能不能好好溝通的)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「整合測試 (Integration Testing)」**。
    *   在測試金字塔中，它位於 Unit Test 的上一層。
    *   **安全層面的意義：** 單元測試 (Unit Test) 只能證明 "Service A 產生 Token 的演算法" 是對的，以及 "Service B 驗證 Token 的演算法" 是對的。
    *   但！如果 Service A 送過去的 Token 沒有用 HTTPS 加密，或者 Service B 的 API 介面根本不接受 Service A 這個 IP 來源，那系統一樣會崩潰 (Broken Authentication / Misconfiguration)。這就是 **Integration Testing (整合測試)** 存在的唯一目的：驗證這將兩個以上「已經各自獨立測好的組件」拼在一起交互作用時，它們之間的通訊介面 (APIs) 與資料流 (Data Flow) 是不是能安全無誤地契合。

#### **12. A security assessor is using a vulnerability scanner against a corporate network. To minimize the chances of accidentally crashing the mission-critical legacy database server or causing a highly disruptive Denial of Service (DoS) condition during business hours, which specific scanning methodology MUST the assessor choose?**
**(一名戴著墨鏡的神鬼安檢員，正捧著一台散發著紅光、能掃描出各種破洞的雷達大儀器 (vulnerability scanner)，準備對著帝國龐大的網狀城牆內部進行全身 X 光大透視。但是，在按下那顆血紅色的掃描核彈按鈕前，他突然想起長官耳提面命的生死令：『聽好！現在是大白天的營業黃金時段！我們家那台躺在心臟地帶、年邁且脾氣暴躁的一號老爺車大金庫 (mission-critical legacy database server)，只要你用雷達掃它時稍微用力了一點，它他媽的就會直接像中風一樣四肢痙攣口吐白沫癱瘓給你看 (causing a highly disruptive DoS condition during business hours)！我警告你！你今天要是把這台老爺車給掃掛了害帝國停擺，我就把你丟下大海餵鯊魚！』請問！為了保住小命、確保在進行全身 X 光透視時，【猶如拿羽毛輕撫般、絕對不會驚醒這頭暴躁老爺車的大睡夢，並把系統崩潰風險降到史無前例最低 (minimize the chances of accidentally crashing)】。這名安檢員絕對必須在這台紅光雷達上，切換並鎖定哪一種『極致溫柔的掃描大模式』？)**
A. Fuzz Testing methodology (這種瘋狂拿大石頭亂砸的猴子測試儀，絕對是一秒鐘就把老佛爺給砸死入土的罪魁禍首)
B. Non-Intrusive (Non-Disruptive) Vulnerability Scanning (這就是能保住他小命的唯一免死金牌聖旨解藥：【『無物理碰撞破壞、絕不強制破門硬闖的溫柔探測大陣法：非侵入式 (或稱非破壞性) 安全漏洞大掃描 (Non-Intrusive / Non-Disruptive Vulnerability Scanning)』】！)
C. Intrusive Penetration Testing (這就是親自拿炸藥包去炸牆壁、跟老佛爺硬幹的侵入式大屠殺測試，找死才在白天按下去)
D. Social Engineering (這是用舌頭騙大總管交出鑰匙的社交工程老千術，這不用雷達掃描儀)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 弱點掃描 (Vulnerability Scanning) 主要分為 **「侵入式 (Intrusive)」** 與 **「非侵入式 (Non-Intrusive)」**。
    *   **Intrusive Scanning：** 掃描器如果發現一個潛在漏洞，它會【真的】去打這個漏洞試試看能不能拿權限。比如它看到一個 Buffer Overflow 的洞，它就會丟真的 Exploit (攻擊程式碼) 過去。結果就是雖然確認了有漏洞，但這台老舊的資料庫也真的被你打當機了 (引發 DoS 阻斷服務)。在正式營運環境 (Production) 或對脆弱設備 (Legacy/IoT) 絕對禁止這樣做。
    *   **Non-Intrusive Scanning：** 溫柔的掃描方式。它只會像小偷去摸摸門把、或是在門縫讀取你的系統版本號 (Banner Grabbing)。當它讀到你的 OS 是 `Windows Server 2003`，它就會回來查表，然後在報告上寫："這台機器版本太舊，據說有 50 個漏洞"。它純粹只是 "觀察與比對特徵 (Fingerprinting)"，而【絕對不會】發動真實攻擊，這是唯一能在白天營業時間安全執行的選項。

#### **13. A Red Team is conducting an advanced engagement. Instead of just running automated scanners to find vulnerabilities in the code, their primary objective is to evaluate how the company's human Security Operations Center (SOC) team and the Blue Team's incident response procedures react to a stealthy, simulated Advanced Persistent Threat (APT) multi-stage attack over several weeks. What kind of specialized testing exercise is this?**
**(一群身上染著鮮血的『紅軍暗殺特種大隊 (Red Team)』，正在執行一場猶如特務大電影般的終極測試任務。這次，他們不再像外面那些只會拿著雷達掃描器、呆板地找城牆裂縫的機器人打鐵工了 (Instead of just running automated scanners to find vulnerabilities)。他們這次受雇前來的最大嗜血目標，是要去【無情考核、羞辱並把那群在大本營裡吹冷氣看監視器的『活體人類衛兵：安全營運中樞防衛大隊 (SOC team) 以及負責救火的藍軍 (Blue Team)』】給當作活靶子狠狠地練兵一把！這支紅軍化身為猶如深海狂鯊般的【『幽靈進階持續性大國進攻部隊 (stealthy, simulated APT multi-stage attack)』】。他們會在那群活體衛兵的眼皮子底下，用極其緩慢、長達幾週的潛伏、暗殺、偷竊、欺騙等連環毒招 (over several weeks)，去測試這群大本營裡面的活體衛兵，【到底還有沒有在喘氣？他們的雷達有沒有瞎掉？他們看到火燒起來的時候，是會按照大將軍留下來的兵法書井然有序地反擊 (react)？還是會在那邊像無頭蒼蠅一樣抱頭痛哭四處逃竄 (incident response procedures)】！請問，這場專治少爺兵的終極實兵對抗大演習。層峰大老們稱之為何？)**
A. Unit Testing (這還是坐在地下室測小螺絲釘的無聊小考)
B. Penetration Testing (Standard) (普通的滲透測試只是在找那個城牆上的大破洞在哪裡並開一份清單報告，通常幾天就收工了，他們不負責演滿幾個禮拜跟你玩捉迷藏鬥智)
C. Adversarial Simulation / Red Teaming Exercise (這就是名震四方、讓防守軍聞風喪膽、徹夜難眠的【『終極活體對流大屠殺戰役：進階對抗模擬大演習 / 終極紅軍特種滲透死鬥 (Adversarial Simulation / Red Teaming Exercise)』】！)
D. Software Composition Analysis (SCA) (拿放大鏡看包裹零件的顯微鏡工作，這兩群人連對手的毛都摸不到)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「紅隊演練 (Red Teaming / Adversarial Simulation)」 vs 「一般滲透測試 (Penetration Testing)」** 的經典差異。
    *   **Penetration Testing (滲透測試)：** 目標是**「找漏洞」**。測試者被要求在有限時間內 (例如兩週)，盡可能找出這座網站所有的弱點 (XSS, SQLi 等等) 並寫成報告。防守方的 SOC (藍隊) 通常早就知道滲透測試人員的 IP 地址，甚至有時候會把他們加入白名單以免一直報警。
    *   **Red Teaming (紅隊演練)：** 目標是**「測試防禦團隊 (人資與流程) 的綜合反應與偵測能力」**。紅隊會極力偽裝自己 (Stealthy APT)，利用社交工程 (釣魚信件)、物理入侵 (潛入大樓插 USB)、甚至利用零日漏洞進行多階段的橫向移動 (Multi-stage attack over several weeks)。藍隊 (SOC) 事前是完全不知道紅隊要來攻擊的。看他們什麼時候才會發現被駭，以及發現後的處理流暢度，這是全面性的實戰考核。

#### **14. A tester wants to verify the resilience of a cryptographic library. They write a script that systematically feeds every single possible combination of a 4-character password into the login prompt, starting from 'aaaa' and ending at 'zzzz', attempting to guess the correct password to bypass the authentication control. What specific attack simulation is the tester executing?**
**(一名瘋狂的開鎖怪客，正站在一個號稱用最新科技打造的金庫大門前，準備測試它的大鎖到底有幾兩重。這傢伙不屑用什麼高深黑客技術，他直接掏出一台無情的『數學計算連環按紐大機器 (script)』。這台機器只會做最一板一眼的工作：它開始像機器人一樣，對著門口的四個密碼滾輪亂轉。它非常極端且白痴地【從第一組號碼 'aaaa' 開始輸入！失敗後換 'aaab'... 然後換 'aaac' ... 一直像這般猶如推土機一樣，絕不跳題、毫無感情且不容反駁地，一路給老子瘋狂試到天荒地老的最後一組密碼 'zzzz' (starting from 'aaaa' and ending at 'zzzz')！】。這名怪客的終極目標只有一個：『老子不管你裡面是外星晶片還是什麼狗屁演算法！老子就是硬生生把你家大鎖全宇宙成千上萬種可能性全部給老子強迫試探過一遍，總有一天我要把你家的密碼給活生生撞出來 (attempting to guess correct password)！』。請問，這名開鎖怪客現在正對著大門發動的這場最粗暴無腦的大攻擊陣法，尊號為何？)**
A. Brute-Force Attack Testing (這就是不需要腦袋、不講求戰術、猶如百萬喪屍推城牆般，只憑著強大計算力與數學窮舉法，專門強暴密碼大鎖的：【『終極無腦蠻荒暴力大破解 / 全盤窮舉攻擊硬闖大陣 (Brute-Force Attack Testing)』】！)
B. Fuzz Testing (Fuzz 是隨便抓一把沒有規則的亂七八糟長度垃圾字串亂砸看你會不會痛死當機，這傢伙現在可是非常有數學邏輯地從 aaaa 一路慢慢推土機到 zzzz)
C. Reverse Engineering (這是把大鎖拆回家裡面慢慢研究裡面齒輪長怎樣的逆向工程，不是這傢伙在現場硬轉密碼盤)
D. Denial of Service (DoS) Testing (雖然狂按幾萬次按鈕可能會當機，但這傢伙的目標是想要解開密碼去偷裡面的東西，而不是只是想把那個數字鍵盤給搞壞砸爛而已)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **「暴力破解攻擊 (Brute-Force Attack)」**。
    *   **特徵：** 它是密碼學中最古老的破解法，又稱**「窮舉法 (Exhaustive Search)」**。它的原理就是把金鑰空間 (Key Space) 裡面 "每一個可能的組合 (Every single possible combination)"，一個不漏地全部試過一遍。從 `0000` 試到 `9999`，從 `aaaa` 試到 `zzzz`。不靠巧思，純靠運算速度 (Computing Power) 強行解開。
    *   這與 Fuzzing (選項 B) 的目的完全不同。Fuzzing 丟的是畸形垃圾，目的是要找程式碼的 Buffer Overflow 去讓它當機崩潰。而 Brute-Force 丟的格式是正確的 (例如都是合法的 4 個字元 length)，它的目的是找出一把真實的鑰匙。

#### **15. A software team uses a metric called "Statement Coverage" to evaluate the thoroughness of their automated suite of Unit tests. The report indicates 85% coverage. What exactly does this 85% metric mathematically represent regarding the software's security testing posture?**
**(在那間充滿著死氣沉沉數學圖表的『造車軟體檢驗署 (software team)』裡。一群帶著厚重眼鏡的工程師，正盯著牆上一張名為《皇家單元測試之語句查哨大覆蓋率報告 (Statement Coverage metric)》的大表。這張表上面，赫然印著一個血紅刺眼的大數字：【85% 覆蓋率】！這群工程師看著這個數字，點點頭表示覺得做得還不錯。那請問，若剝去那些花俏的形容詞外皮，這個『85% 的語句查哨覆蓋大比率』的數學真理，若用最直白、最不帶感情的口吻來拆解，它其實精確且唯一地代表了哪一項對於這套系統底牌揭露的物理現實？)**
A. 85% of all known OWASP vulnerabilities have been tested. (瞎扯！這張表根本不關心駭客十大惡毒榜單上的破洞有沒有被補好)
B. 85% of the total number of lines (statements) in the raw source code have been successfully executed at least once during the automated testing process. (這就是這張表的冰冷且唯一數學真相：【這座龐大皇城的所有基礎地基法典 (raw source code) 之中！那猶如數百萬條毛細血管般的『每一行孤單的程式碼語句 (total number of lines/statements)』！其中有高達 85% 的語句，在昨天晚上我們放出那群幾千隻『測試大狼犬 (automated testing process)』去地毯式搜索狂吠時，這 85% 的磚塊【曾經被這些狼犬活生生地踩踏、啟動、且證明它們會亮燈呼吸過最少一次啊 (successfully executed at least once)】！】。至於剩下的那 15% 黑洞，就代表著那是連測試大狼犬都迷路、從來沒有踏進去走訪過、不知道是不是早就長滿毒蘑菇發霉的死角盲區！)
C. 85% of the identified threat models have been mitigated. (他才不管你當初在沙盤推演上的那一堆假想大風雲威脅模型，這只是一場純粹的對著實體牆壁點人數的點點名)
D. High confidence that 85% of the application is completely secure from hacking. (放屁！被大狼犬踩過一行程式碼不代表這行程式碼就不會被駭客一腳踹爆，覆蓋率高不等於你就是金剛不壞之身，這完全偷換了『被執行過』與『它是防禦無雙』概念)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是對 **「程式碼覆蓋率 (Code Coverage)」** 這個軟體度量指標 (Metrics) 中 **「語句覆蓋率 (Statement Coverage / Line Coverage)」** 最精確的技術定義。
    *   **定義：** 如果一份原始碼有 100 行指令 (Statements)。你在執行 Unit Tests 工具 (如 JUnit + JaCoCo 或是 Python 的 Coverage.py) 時。這些測試腳本在跑的時候，讓這支程式總共執行了其中的 85 行，那你的 Statement Coverage 就是 85%。
    *   **破除迷思：** D 選項是新手常犯的致命錯覺。「這行程式碼被測試腳本覆蓋執行過」只代表 "它沒有語法錯誤且能跑"，**完全不等於 "它是安全無痛的"**。例如你那行代碼是一句致命的 SQL 字串拼接，你的 Unit Test 只測了正常的字串看能不能登入就能達到 100% 覆蓋。但這完全無法防禦駭客丟進來的 SQL 注入 `' OR 1=1`。所以高 Coverage 只是做基本體檢，不代表安全 (Security)。

#### **16. Before a major, highly anticipated release of a new ERP software product, the vendor distributes an almost-finished version of the software to a select group of external, highly trusted industry customers. These customers deploy it in their own real-world test labs to find final bugs and UX issues before the software is sold to the general public. What is the industry-standard term for this final phase of pre-release external testing?**
**(在一場即將震動全球商界的『帝國級 ERP 終極旗艦大商用系統 (major newly anticipated ERP release)』公開發布大發表會的前夕！這家造車公會偷偷使出了一個小心機。他們並沒有直接把車子拿去市集上大拍賣。相反地，他們小心翼翼地，把這台【『外觀已經幾乎雕琢完備，只差臨門一腳拋光的最終初號機 (almost-finished version)』】！秘密地送到了幾位【在江湖上德高望重、由大客戶組成的私人黃金試車手白老鼠大聯盟 (select group of external trusted industry customers) 】手裡！公會懇求這些白老鼠大爺們，把這台初號機直接開進他們自家的實彈演習兵工廠裡，用真實的火車頭跟商場砲火 (real-world test labs)，去瘋狂操弄並蹂躪它！幫公會抓出最後那一群連造車廠工程師自己都死活找不倒的【『實戰微小臭蟲與坐起來屁股痛的體驗鳥問題 (final bugs and UX issues)』】！等到這群白老鼠都滿意點頭了，他們才敢大張旗鼓地把這台車放上對著幾億一般平民開放的大展示廳！請問，這場在破曉大公開前，由『外部貴賓白老鼠軍團』所主持的最後一場生死大體檢。這在江湖上傳頌的正式大招牌名喚為何？)**
A. Alpha Testing (這那是在這場秀的很久以前，是那些工廠裡自己關起門來、由內部親信工程師互打狗咬狗的抓蟲大亂鬥，車子連廠房都還沒出)
B. Beta Testing (External User Acceptance Testing) (這就是大名鼎鼎、能讓外部貴賓享受首發待遇、並進行最後一輪在風吹雨打下的終極實戰大殘酷考核：【『偉大的 Beta 測試之夜 / 外部鐵血用戶驗收大典 (Beta Testing / External UAT)』】！)
C. Unit Testing (用放大鏡看小螺絲釘那都是兩三年前還在打造地基時候幹的小事)
D. Fuzzing (瘋狂拿石頭盲目亂丟看會不會當機的破壞王儀器，而這群白老鼠是來提供用車感受，不是來拿石頭亂砸你的車的)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「Beta 測試 (Beta Testing)」**，常與 UAT (User Acceptance Testing) 一起討論。
    *   **測試生命週期 (SDLC Testing Phases)：**
        1.  **Alpha 測試：** 在開發團隊內部進行，由內部 QA 和開發者擔任白老鼠。程式此時常常還不穩定、會當機崩潰。
        2.  **Beta 測試：** 軟體系統已經 "Feature Complete (功能開發全部完成)" 且相對穩定。將它釋出給一群 **"外部的真實使用者 (External End-Users)"**。這群用戶完全不懂這軟體是怎麼寫出來的，他們帶著真實世界的資料、作業系統環境、千奇百怪的使用習慣去實戰測試。這能發現實驗室找不到的 UX (使用者體驗) 缺陷或相容性問題。這是進入上市 (General Availability, GA) 前的最後一哩路。

#### **17. An enterprise is comparing DAST (Dynamic) and SAST (Static) testing tools. The CISO asks: "Which of these two tools will be able to tell me exactly which file name and which specific line of code (e.g., `login.java, Line 45`) contains the SQL injection vulnerability?" What is the correct technical answer based on how these tools fundamentally operate?**
**(在帝國將軍籌備購買攻城大巨砲的比武大會上。兩家來自不同時空的巨神兵軍火商，牽著他們家的招牌神獸出來比拚。左邊牽出來的是一頭名叫【『靜態老書生 SAST』】，右邊牽出來的是一頭渾身長滿刺的【『動態野戰狂戰士 DAST』】。這時，高高在上的資安大總管 (CISO) 摸摸鬍鬚，提出了一個極度刁鑽、直接命中兩者靈魂死穴的問題：『聽好了，兩位傢伙。如果我們家那頭幾百萬行的怪物系統裡，不小心長了一顆能夠一劍封喉的 SQL 隱碼大法劇毒瘤 (SQL injection vulnerability)！請問我們到底要買你們之中哪一頭神獸回家，它才有那等顯微鏡跟千里眼的神功，【能夠像查戶口一樣，分毫不差地把手指頭指在這塊毒瘤的臉上！並大聲朗讀出：「報告長官！這顆毒瘤就是藏在【那個名為 `login.java` 檔案地牢深處裡，第 45 層樓那一行血淋淋的程式碼上面 (file name and specific line of code e.g., Line 45)】！』請問，熟悉兩隻神獸五臟六腑與運作物理極限的你，該如何判定誰才能完美完成這道不可能的神級精確定位任務？)**
A. DAST can pinpoint the exact line of code because it attacks the database directly. (滿嘴胡扯，DAST 這個只在大門外面發狂亂射子彈的狂戰士，他連牆壁裡面的人長什麼樣子都看不到，更遑論什麼第幾行程式碼)
B. SAST can pinpoint the exact line of code because it reads the raw static source code files directly. (DAST only sees the compiled/running web pages and HTTP responses). (這就是一劍封喉的判決真理：【『當然是那個天天抱著這本密碼字典啃的、有著千里眼之靜態老書生 SAST 啊！』】！因為 SAST 從頭到尾，都是把那個寫滿百萬字元、最赤裸無掩飾的『系統老祖宗原始建城底稿大秘寶 (raw static source code files)』給捧在手上死死研讀 (reads directly)！他能立刻指出錯字究竟寫在第幾頁第幾行！反觀那頭只知道在城外撒野的動態狂戰士 DAST！他這輩子從來沒讀過城防圖，他唯一能作的只有在城外亂踹城門 (HTTP responses)，當城門被他踹破時，他只會興奮大叫「報告這座城門破了！」但他根本不可能透視這扇被融化定型的大鋼門 (compiled running web page)，去告訴你到底是那個工人在第幾天打螺絲打壞的啊！)
C. Both tools can easily highlight the exact line of code. (這是不可能齊頭平等的，狂戰士根本沒有能力)
D. Neither tool provides line-level detail; only manual code review can do that. (如果連老書生都指不出錯誤行的話，那這老書生就可以丟進資源回收桶了)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是評估與購買 **SAST (白箱)** 與 **DAST (黑箱)** 工具時最關鍵的差異點之一。
    *   **SAST 的優勢 (精準溯源)：** SAST 就是對著 Source Code 掃描。所以當它用數學模型抓出一條危險的路徑時，它可以超精準的標示： "在你的專案 `src/com/bank/auth/LoginManager.java` 的第 `102` 行，變數 `$userInput` 被加上了查詢字串"。這讓開發者可以直接點過去修復，修復速度極快。
    *   **DAST 的運作盲區：** DAST 掃描的是一個 "跑起來的 URL 網址 (如 `https://example.com/login`)"。當 DAST 成功發現可以用 `' OR 1=1` 駭進這個網址時，它能提供給你的報告是：「這隻 API `/login` 有 SQL Injection 漏洞，這是我的攻擊封包明細」。**但 DAST 絕對無法告訴你這個洞是在哪個 .java 檔案的哪一行**。因為 DAST 被防火牆擋在外面，Source Code 早就在伺服器裡編譯成 binary bytecode，DAST 看不到裡面的世界。開發者收到 DAST 報告後，還得自己去龐大的專案裡大海撈針找 `/login` 到底是哪一段 Code。
