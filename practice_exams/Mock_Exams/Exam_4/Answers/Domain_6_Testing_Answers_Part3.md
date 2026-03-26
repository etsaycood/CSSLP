# 第四套全真模擬試題 (Exam 4) - 答案與詳解本
## 領域 6：安全的軟體測試 (Secure Software Testing) (17題) - Part 3 (Q13-Q17)

---

#### **13. A test engineer is designing cases to verify the boundary conditions of an age input field, which should only accept values between 18 and 65 inclusive. Using Boundary Value Analysis (BVA), which set of test data points is the MOST critical to include in the test suite?**
**(一名老鐵匠為了檢驗他剛造好的一道『只准十八歲到六十五歲壯漢通過 (accepts 18 to 65 inclusive)』的金鋼大門。他決定使出失傳已久的【『極限邊疆大試煉法 (Boundary Value Analysis / BVA)』】！這老鐵匠深知：這座大門最容易生鏽卡死的地方，絕對不是每天都有幾萬個三十歲壯漢走過去的門中央，而是那兩扇門軸與門檻摩擦的最邊緣地帶 (boundary conditions)！如果這門要壞，一定是在這兩頭出問題！請問！為了這場大演練，老鐵匠必須從城外，精準地挑選哪一群『年齡長得最刁鑽、最讓人頭痛、最能測出這門到底是開還是關的極限怪物大軍 (MOST critical data points)』，來對著這門進行極限衝撞？)**
A. 25, 30, 40, 50, 60 (這群人就是典型的三十歲、四十歲壯年人。這門理所當然會讓他們大大方方地走進去 (Equivalence Partitioning 裡的常態代表)。老鐵匠就算測了一萬個三十歲的人，也測不出這門對「十七歲」的小孩或「六十六歲」的老爺爺會有什麼反應，這是最浪費時間的廢測)
B. 17, 18, 19, 64, 65, 66 (這就是名震天下、刀刀見骨的：【『極限兩極刀鋒大戰士部隊 (Boundary Value Analysis / BVA)！』】。老鐵匠的智慧在於：如果這門說 18 歲才能進。那最容易寫錯程式碼 (`>` 寫成 `>=`) 的地方，就在 18 歲跟 65 歲這兩條邊際紅線上！所以他找來了：【剛好能進門的底線戰士 (18)、剛好被一腳踢出去的小屁孩 (17)、和毫無懸念能進來的大一新生 (19)！】。同時在另一端，他安排了：【即將退休的最後一天極限老伯 (65)、差一天就該進養老院被拒絕的老兵 (66)、和還有兩年退休的將軍 (64)！】。這群帶著小數點與刀鋒邊緣的極端測試者，能在一秒鐘內，將這大門的判斷邏輯「是否包含等號 (`>=` vs `>`)」徹底驗證得清清楚楚！這也是軟體測試領域性價比最高、抓蟲率第一名的測試案例設計法！)
C. -1, 0, 100, 1000 (負一歲和一千歲是來亂的喪屍，雖然這也是負面邊界案例，但對於驗證「18 到 65」這條核心商業邏輯線，這群喪屍只能算副產品，遠不如 17/18/65/66 來得刀刀見血精準)
D. 'eighteen', 'sixty-five', null (這是拿字串跟空值丟過去看門會不會當機 (Fuzzing / Invalid Data Types)，這些根本不是數字，完全跳脫了「數值邊界分析大戰」的範疇)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是對軟體測試技術 **「邊界值分析 (Boundary Value Analysis, BVA)」** 原理的最佳驗證。
    *   **軟體缺陷的溫床 (The "Off-by-One" Error)：** 工程師在撰寫條件判斷 `if (age >= 18 && age <= 65)` 時，常常會筆誤寫成 `if (age > 18 && age < 65)`，這種錯誤被稱為 Off-by-One (差一錯誤)。這會導致剛好 18 歲的合法用戶被拒絕，而這是一種非常難以透過隨機亂數 (如 40 歲或 25 歲) 測試出來的 Bug。
    *   **BVA 的三點採樣原則 (2-value 或 3-value testing)：** 對於每一個邊界，我們要測試它的 "剛好在線上"、"線上更低一階"、"線上更高一階"。
        *   **下邊界 18：** 17 (Invalid/Negative), 18 (Valid Boundary), 19 (Valid).
        *   **上邊界 65：** 64 (Valid), 65 (Valid Boundary), 66 (Invalid/Negative).
    *   這六個特定的數值 (Test Cases)，用最低的成本 (只要寫 6 個 Unia Test)，提供了對該商業邏輯最高置信度的覆蓋保證 (Coverage Guarantee)。

#### **14. During which phase of penetration testing does the ethical hacker attempt to maintain access to a compromised system, often by installing backdoors or creating hidden user accounts, to demonstrate what an Advanced Persistent Threat (APT) might do?**
**(一名被皇帝重金挖角的『天下第一白帽死士 (ethical hacker)』，正躲在他的秘室裡操練殺敵技術！這次演練，這死士不只要殺進城裡搶一次黃金 (compromised system)！他真正的終極考題，是要模擬那些像毒蛇一樣、潛伏在皇城底下三年都不會被發現的【『亡國惡靈之進階持續性威脅 (APT)』】！為了證明這惡靈有多恐怖，這死士在攻進大內皇宮的當下，居然沒有拿黃金就跑，反而【拿出了一把鐵鍬，在皇宮的柱子底下挖了一個地道，還幫自己辦了一張連皇帝都查不到的最高級大將軍假兵符 (installing backdoors or creating hidden user accounts)！】。他做這一切，都是為了以後就算這皇宮換了鎖，他還是能像幽靈一樣隨時潛入城裡睡覺 (maintain access)！請問，這死士此時正在演武場上演練的，是兵法滲透大計中的哪一個最令人毛骨悚然的篇章？)**
A. Reconnaissance / Footprinting (情報搜集與踏勘是在城門外偷偷丈量城牆有多高、門鎖是哪家工匠打的，這死士連門都還沒摸到，不可能在挖地道)
B. Vulnerability Scanning (弱點掃描是拿大聲公對著城牆喊，看牆會不會掉下磚頭來。這死士現在不只砸開了磚頭、人還進去了、甚至在裝修皇帝的寢宮，這早就超過掃描了)
C. Maintaining Access (Persistence) (這就是名震天下、令所有護國錦衣衛半夜嚇到尿床的：【『死神長住之終極寄生持久戰 (Maintaining Access / Persistence)！』】。當滲透刺客千辛萬苦 (Exploitation 階段) 終於拿到了伺服器的第一把初階爛鑰匙 (Web Shell) 後。他的第一直覺絕對不是立刻去偷資料！他的直覺是：這把爛鑰匙隨時會因為皇帝重開機或是某個小太監換帳號而被沒收廢除 (Session Expiration)！為了【永遠不死地活在這個皇城裡】，他會立刻在這伺服器深處，種下：惡意 Cron Jobs (定時召喚陣)、登錄檔無形啟動木馬 (Registry Run Keys)、甚至是藏在深山裡沒人注意的 Administrator 級別幽靈帳號！這種種手段，都只為了一個目的：【老子要在這住下了！就算你們明天把大門封死，老子還是有地道能隨時回來喝茶 (Demonstrate APT capabilities)！】。這才是真正能打痛高層防衛意識的高階滲透測試環節！)
D. Reporting / Remediation (寫報告繳作業是在所有暗殺行動結束後，把這張紙扔在皇帝的龍椅上證明自己來過。在寫這張紙的時候，刺客早就離開皇宮了，不可能還在挖地道)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是標準 **「滲透測試方法論 (Penetration Testing Methodology, 如 PTES 或 NIST SP 800-115)」** 中的一個具體階段：**「維持存取權 (Maintaining Access / Persistence)」**。
    *   **PT 五大階段：**
        1.  Reconnaissance (偵察)
        2.  Scanning / Enumeration (掃描與列舉)
        3.  Gaining Access / Exploitation (取得存取權 / 漏洞利用)
        4.  **Maintaining Access (維持存取權)：** 也就是題幹描述的階段。真實的高階攻擊者 (APT - Advanced Persistent Threat) 攻防戰中，奪取系統只是第一天的工作，接下來的重點是「不要被踢出去」。所以他們會部署 Rootkits, Web Shells, 或是建立備用的特權/後門帳號。
        5.  Covering Tracks (掩蓋蹤跡) / Reporting (報告製作)。

#### **15. A development team employs a robust Unit Testing framework (e.g., JUnit or NUnit). To measure how much of the application's actual source code (lines, branches, or paths) is executed by their automated unit tests, what metric do they track?**
**(一群住在皇城兵工廠裡、每天敲鍵盤敲到手指滴血的『自動化測試狂熱老匠人 (development team)』。這群老頭子發明了一整座【『全自動大火炮測驗靶場 (Unit Testing framework)』】！這個靶場會自動對著他們新造出來的大炮發射十萬發測試專用假砲彈！但是！大太監為了監督他們到底有沒有偷懶，拿了一台【『黃金雷達測繪大天平 (metric)』】站在旁邊死死盯著看。這台天平的指針，精準地顯示了：『剛才那十萬發假砲彈，到底有沒有涵蓋到我們這座大鋼鐵皇城裡那「幾百萬條小巷子 (lines)」、「所有的分岔路口 (branches)」！如果這大砲根本沒發射過其中最隱密的 120 號小巷，這天平就會毫不留情地給這群老頭子扣分 (measure how much source code is executed)！』請問。這台讓所有開發者又愛又恨、專門測算「你究竟還有多少沒測到的死角」的無情雷達天平，學名為什？)**
A. Vulnerability Density (漏洞密度是算一萬塊磚頭裡藏了幾條蟲，這是用來評量系統多髒的指標，不是用來評量「那群測試狂熱老頭的靶場大炮到底打得廣不廣」)
B. Code Coverage (這就是那台讓天下工匠聞風喪膽、每天被逼著加班寫測試卷的：【『無情大探照燈之程式碼涵蓋率大天平 (Code Coverage)！』】。這項天平 (Metric) 是衡量「安全軟體測試成熟度」的第一張體檢表！它的真理很殘酷：你說你寫了一千個單元測試？很好，但如果這天平顯示你的 Code Coverage 只有 30%！那代表什麼？代表這座擁有十萬間房子的城堡裡，你的探照燈居然有七萬間房子【這輩子連一次都沒照進去過 (Lines never executed by tests)】！如果那七萬間沒掃過的房子裡躲著恐怖的零時差殺手 (Zero-day vulnerability/Logic Bug)？你上線的當天全城就要陪葬！因此，高成熟度的 CI Pipeline 都會設定一道死命令：「涵蓋率低於 80% (Threshold)? 大門直接關閉，不准你這沒被大炮完整檢驗過的爛貨推上前線戰場 (Fail the build)！」)
C. Mean Time to Repair (MTTR) (平均修復時間是你發現城牆破了洞，叫工人去把洞補起來需要的幾天時間。這是在算修復效率的碼表，不是在算測試靶場涵蓋死角的探照燈)
D. Common Vulnerability Scoring System (CVSS) (通用漏洞評分系統是幫已經抓出來的蟲子打分數（誰毒誰大隻），而 Code Coverage 是在算還沒抓蟲前，你的手電筒光線夠不夠廣，兩者層級截然不同)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是對 **「程式碼涵蓋率 (Code Coverage)」** 的標準定義。
    *   **意義：** 這是一項白箱測試 (White-Box Testing) 中至關重要的內部軟體品質度量指標 (Metric)。它透過儀器化 (Instrumentation) 來追蹤，當自動化測試套件 (Test Suite, 如 JUnit) 執行時，應用程式中到底有多少百分比的源碼 **被真實地呼叫或執行過 (Exercised)**。
    *   **覆蓋率的類別 (Coverage Criteria)：**
        *   **Line Coverage (行涵蓋)：** 最基本。有多少行程式碼被執行到了。
        *   **Branch Coverage (分支/決策涵蓋)：** 更進階。`if/else` 的 True 和 False 兩種路徑是否都被至少執行過一次。
        *   **Path Coverage (路徑涵蓋)：** 最嚴格，包含迴圈的所有可能排列組合。
    *   **在 SSDLC 中的角色：** 未被測試執行到的程式碼 (Dead Code 或是 Uncovered Code) 就是盲區 (Blind Spots)。這裡面極可能藏有會導致系統崩潰的 NullPointerException，或是未經驗證的惡意輸入入口。提高 Code Coverage 等於是縮小系統的未爆彈攻擊面。

#### **16. Before a major new release of an ERP system is deployed to production, it is deployed to a staging environment. The business stakeholders and end-users are asked to perform their daily tasks on this staging system to confirm that the software meets their operational needs and the original functional requirements. What type of testing phase is this?**
**(在帝國花費十年國力、終於打造出那艘宣稱能運送全國幾十億黃金的『大航海超級巨艦 (ERP system)』準備下水服役的前夕！大督工死死攔住了要把船推下海的元帥！大督工大喊：『不能直接下海打仗！先把它拖去旁邊那個人造的假湖泊 (staging environment)！』然後，大督工做出了一個驚人之舉：他把那群平時在皇宮裡養尊處優的【『算帳老太監、掌管糧倉的老爺、跟寫流水帳書記 (business stakeholders and end-users)』】，全部綁上船！督工對這群老頭大吼：『你們！就用這艘假軍艦在假湖裡，模擬給我重演一次你們每天在皇宮裡幹的那些破事 (perform their daily tasks to confirm it meets operational needs)！如果這大船上的算盤算不出你們要的數字，那老子死也不讓大船推到前線大戰場！』請問。這種把真實世界的老闆跟使用者拉來當小白鼠、驗收這艘大船究竟是不是個廢物的最殘酷生死大審判，尊號為何？)**
A. Unit Testing (這是在這造船廠裡，老鐵匠只拿鐵鎚去敲那一根小小的螺絲釘有沒有生鏽看能不能釘進去，這事根本輪不到讓算帳老太監來煩惱，這是微觀的防護)
B. Integration Testing (這是在造船廠裡，老鐵匠把大炮跟輪船接在一起，看開炮會不會把船底震破的系統連線大演練。雖然大砲跟船都成形了，但它依舊不是給老太監用的，這是工匠自己家的事情)
C. User Acceptance Testing (UAT) (這就是名震四海、讓全天下無數日夜加班自以為已經天下無敵的工匠們，直接被老爺一個耳光打得當場爆哭的：【『老天爺終極生死大驗收：用戶驗收測試 (User Acceptance Testing / UAT)！』】。這個測試法典的殘酷核心不在於這艘船會不會沉 (那是 QA 的事)。它的殘酷在於：你這船就算裝了一百門大砲，程式碼涵蓋率一萬分！但只要買單的老太監上船摸了一把金庫大門，發現：『這把手的顏色不是我要的黃色，這大門打不開我平時記帳的抽屜！』。這艘大船立刻被無情定義為：【『違反了老爺的終極聖旨 (Failed to meet operational needs/functional requirements)』】！直接被丟回鐵漿爐裡重造！UAT 測試的唯一目的，就是確保造出來的系統能夠在現實世界的槍林彈雨中，真正幫老闆賺到錢、處理好他們真實的業務。它是程式瑪上線成仙前，最神聖也最世俗的最後一關泥沼大審判！)
D. Static Analysis (這是靜態白骨掃描儀，掃描沒跑起來的程式碼圖紙，老爺跟太監只懂看算盤，哪懂程式碼圖紙，他們絕不可能看這個)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是軟體測試生命週期 (STLC) 最後一個階段 **「用戶驗收測試 (User Acceptance Testing / UAT)」** 的經典定義。
    *   **各測試層級的差異對比：**
        *   **Unit/Integration Test (開發者/QA 負責)：** 驗證軟體 "We built the product right (我們把軟體做對了沒有？程式碼有沒有 Bug？)"。
        *   **UAT (真實終端使用者/Business Analysts 負責)：** 驗證軟體 "We built the right product (我們做出來的是不是對的產品？它能不能達成現實世界的商業目標？)"。
    *   **測試環境：** UAT 通常在**類正式環境 (Staging / Pre-Production Environment)** 中進行。因為這個環境在資料庫結構、硬體配置上最接近真實的 Production。
    *   **資安意義上的關聯：** 雖然 UAT 偏向功能驗收，但在高安規專案中，UAT 也包含了「安全功能的業務可用性測試」(例如：多重要素驗證 (MFA) 會不會讓使用者在日常作業時被煩死而導致業務停擺)。

#### **17. A team is developing a cryptographic library. To ensure their implementation of the AES-256 algorithm securely and correctly transforms plaintext into ciphertext according to the mathematical standard, they use a large set of standardized inputs with mathematically known, pre-calculated expected outputs to verify the results. What is this rigorous verification process called?**
**(一支住在深山老林、一輩子只和數學公式作伴的『機密鎖匠敢死隊 (team developing cryptographic library)』。他們剛看著祖師爺留下的上古圖譜，用鎔岩打出了一把號稱天下第一難解的神兵【『阿薩龍 256 大防窺魔盒 (AES-256 algorithm implementation)』】。但是在這盒子重見天日之前！帶頭的老總管拿出了幾本從『國家級九星防衛神殿 (NIST)』請回來的神聖大聖經！這本聖經裡，密密麻麻地記載了幾萬條：【『如果你往這個魔盒丟進去一顆青蘋果 (plaintext standardized inputs) 和一把金鑰匙，這盒子裡面「絕對」必須吐出一頭擁有三隻眼睛的藍斑點大紅毛毛蟲 (mathematically known expected outputs ciphertext)！』】。老總管就這樣，一顆一顆蘋果地丟進新造的盒子裡，然後把吐出來的怪物，和這本國家聖經裡的畫像【死死地拿著放大鏡一一對照驗證】！只要有一根紅毛長得不一樣，這盒子就立刻當場粉碎重鎔！請問！這套連神明都要低頭、絕不動搖一絲一毫的數學死律大對戰，名喚為何？)**
A. Fuzzing (Fuzz Testing 是瞎丟雞巴毛雜物進去亂攪拌，看盒子會不會爆炸。這跟丟進精打細算的青蘋果然後期待出現紅毛蟲的「數學神明校對大典」完全是相反的極端)
B. Known-Answer Tests (KATs) / Cryptographic Validation (這就是能讓所有數學家、駭客、密碼大師全部跪地膜拜的無上神之對決界：【『不容絲毫雜質之終極已知答案大真理審查 (Known-Answer Tests / KATs) / 與國家級密碼數學大驗證 (Cryptographic Validation)！』】。你必須知道，在實作密碼演算法的死亡深淵裡，你不能用普通工匠的「看起來可以動就好」來交差。因為只要你寫的加密數學公式裡，有哪怕 0.000001% 運算符號向左偏了一點 (Bitwise Shift 寫錯)，駭客就能從這個縫隙裡，用超級電腦反推出你的金庫密碼！為了保證你寫的軟體函式庫與國際 FIPS/NIST 標準是【100% 絕對純潔、數學等價的神之複製物】，你必須拿權威機構釋出的「一千萬組標準答案題庫 (KATs Vectors)」來做這場考試！這是一套專門用來摧毀任何自作聰明的防禦機制！)
C. Stress Testing (壓力測試是一萬個人同時踩這盒子看盒子會不會破。現在我們是在拿蘋果跟毛毛蟲對帳本，不是在踩盒子)
D. Penetration Testing (滲透測試是刺客拿鐵鎚想把盒子敲開。這是一場數學驗收，不是實體破壞測試)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「已知答案測試 (Known-Answer Tests, KATs)」** 是密碼學演算法實作驗證 (Cryptographic Validation) 的黃金與唯一公認標準。
    *   **自製/實作密碼模組的挑戰：** 即使你使用別人設計好的標準 AES 數學公式去用 C 語言實作。但在處理位元操作 (Bitwise XOR, shifts)、記憶體對齊 (Memory alignment)、或是填充長度 (Padding) 時，極容易出錯。
    *   **KATs 的權威性：** 美國國家標準與技術研究院 (NIST) 針對每一個合格的密碼演算法 (AES, SHA, RSA)，都會發佈龐大的 Test Vectors (測試向量清單)。這份清單明確寫著：
        *   Input (Plaintext): `00112233...`
        *   Key: `AABBCCDD...`
        *   Expected Output (Ciphertext): `F92A8E...`
    *   開發團隊的演算法函式庫必須 100% 精準地產出這些預先算好的答案。如果不匹配，代表底層演算法實作存在缺陷 (Flaws)，加密出來的檔案將無法與世上其他標準 AES 系統相容，且可能極度危險。
