# 第二套全真模擬試題 (Exam 2) - 答案與詳解本
## 領域 6：安全的軟體測試 (Secure Software Testing) (17題) - Part 2 (Q10-Q17)

---

#### **10. An organization decides to hire an external cybersecurity firm to conduct a comprehensive Penetration Test. The organization provides the hired hackers with full administrative credentials, complete access to the Git source code repositories, detailed network architecture diagrams, and the API swagger documentation before the test even begins. What specific type of penetration testing engagement is this?**
**(一家財大氣粗的公司，決定斥巨資去外面雇用一整個武裝到牙齒的黑帽駭客傭兵團 (外包資安公司)，來為自家堡壘舉行一場『史詩級的血腥滲透測試大戰 (Penetration Test)』。不可思議的是，在這場無情的廝殺連第一聲槍響都還沒打出【之前】！這家公司的高層居然大門四開，【雙手奉上所有的最高皇帝權限帳號密碼 (administrative credentials)、把鎖著祖傳程式碼的 Git 大金庫鑰匙連根拔起送給對方、還攤開那連自家工程師都沒看過的最機密網路架構地圖、以及那寫著所有後門穴道的 API 真經秘笈】！請問，在滲透測試的江湖規矩裡，這等如同白晝般完全沒有一絲秘密的終極邀請戰，被特別尊稱為什麼名號大戰？)**
A. Black-Box Testing (什麼都瞎著眼看不到的純黑箱瞎打盲戰)
B. Grey-Box Testing (半脫半掩看部分說明書的灰箱摸象戰)
C. White-Box (Crystal-Box) Testing (如同用顯微鏡看玻璃般透明的【終極白箱 (White-Box) / 水晶箱 (Crystal-Box) 大滲透測試】)
D. Blind Testing (蒙上眼睛找門把的瞎子測試大會)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是滲透測試的基礎分類題。在 **「白箱測試 (White-Box Testing)」** (有時被稱為 Crystal-Box 水晶箱或 Clear-Box 透明箱測試) 中，防禦方 (甲方) 會在攻擊前，把「自家底褲脫光光，所有機密毫無保留地交給攻擊方 (乙方)」。駭客擁有原始碼、管理員帳號、架構圖。這種測試的目的不是測「駭客能不能從外頭找到門」，而是假定「一個最懂你們家內部系統的離職高級工程師叛變，他能對你們造成多深的破壞」。白箱測試因為省去了瞎子摸門的時間，可以直接針對最複雜的核心邏輯漏洞進行手術刀般的精準打擊，抓出黑箱測試一輩子都找不到的深層架構死穴。
    *   **為何不是其他 (A, B)：** 如果什麼都不給，把攻擊方當路人，這叫 黑箱 (Black-Box)。如果是只給一組「一般會員帳號」，讓攻擊方從普通使用者的視角去看看能不能越權，這叫 灰箱 (Grey-Box)。

#### **11. After a severe security breach where hackers exploited a missing validation check in the password reset logic, the development team patches the vulnerability. However, the exact same vulnerability accidentally reappears in the production system three months later because a different developer overwrote the patch with an older branch. What specific type of automated security testing MUST be heavily implemented in the CI/CD pipeline to prevent previously fixed bugs from ever returning?**
**(在這個曾發生過慘烈駭客攻破密碼重置系統深淵、導致百萬筆個資血流成河的戰場上。雖然英勇的開發大軍後來終於趕出了一磚一瓦，把那個漏洞補上了。可是！三個月後，某個眼瞎的菜鳥工程師，在送版本上線時操作失誤，居然拿了一塊三個多月前的破爛舊版本磚塊，【硬生生地把那個已經修好的補丁給洗掉覆蓋了 (overwrote the patch)】。於是這隻本該下地獄的漏洞喪屍，居然在營運火線上活跳跳地重生了！為了讓這種『明明修好了卻又他媽的不小心跑出來』的白癡低級錯誤永世不得超生。在開發大軍的高速公路 (CI/CD pipeline) 上，【絕對必須強制綁上】哪一套專門防喪屍復合的自動化安檢機關大砲？)**
A. Fuzzing (盲打餵食大砲)
B. Regression Security Testing (這就是發誓死守陣地、專司不讓舊病復發的【無情回歸安全大安檢 (Regression Security Testing)】！)
C. Red Teaming (紅隊特種部隊大突襲)
D. Threat Modeling (坐在白板前紙上談兵的威脅兵推大會)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「回歸測試 (Regression Testing)」** 的核心精神就是：「修好一個洞之後，我必須寫一份自動化考卷 (Test Case)，【每次任何人要上線新程式碼前，電腦都必須自動把這份舊考卷再重考一次。只要這原本考過 100 分的考題，今天突然有任何一題不及格 (洞又裂開了)，流水線就立刻鳴紅色警笛並強制拉下鐵門不准上線部署】」。在資安領域，這稱為 Security Regression Testing。防禦這類 "退步 (Regression)" 災難的唯一解法，就是將當時修補漏洞用的特定 Payload 轉換成自動化 DAST 或 Unit Test 腳本，讓機器每天跑一萬次，絕對不再相信人類工程師的手動合併 (Merge) 技巧。

#### **12. A company maintains a strict benchmark policy that code coverage for unit tests must exceed 85% before an application can be deployed. A developer writes unit tests that execute 90% of the lines of code in a specific class. However, during a production incident, the class fails catastrophically when a specific combination of input parameters causes an untested execution path (a complex nested `if/else` statement) to trigger an exception. What does this reveal about code coverage metrics in the context of security testing?**
**(一家被 KPI 數字蒙蔽雙眼的老古板公司，在牆上掛著一條自嗨的鐵律：『所有的程式，其單元積木顯微測試的【程式碼行數覆蓋率 (Code Coverage)】絕對小於 85% 就得殺頭，超過才能上架！』。一位小聰明工程師寫出了高達【90% 行數被測試機器跑過】的驚人滿分考卷傲視群雄。沒想到！當晚上程式放到戰場上運轉時，突然遇到了一組外頭從未見過的詭異變態組合參數。這組點穴法直接觸發了程式深處某個『剛好夾在那未被測到的 10% 裡面的龐大巢狀 `if/else` 連環迷宮結點』，這程式當場吐血死當引發大火。這活生生血淋淋的悲報，像是一個響亮的巴掌！它向全世界的資安測試界揭露了一條關於「覆蓋率數字神話」的什麼殘酷真相？)**
A. 100% line coverage guarantees that an application is free of security vulnerabilities. (只要數字達到 100% 滿分，就代表上帝親自保證這程式這輩子絕對不可能有安控死穴，完美無瑕)
B. High line coverage percentage does not inherently guarantee high security or that all logical execution paths and edge cases have been adequately tested. (數字高？那都是騙小孩的！它赤裸裸地揭露了：【極高比例的程式碼行數覆蓋率 (Line coverage)，天生且根本無法保證軟體的高防護力。它更無能證明：那些多如星河般的『邏輯轉彎執行路徑 (execution paths)』與變態到極點的『極端邊界死角 (edge cases)』有被好好虐待毒打測試過這件事情】！)
C. Code coverage metrics are completely irrelevant to software engineering. (因為寫扣這件事，數字本身根本毫無任何一絲一毫意義，直接全廢)
D. The developer should have aimed for 75% coverage instead of 85%. (因為工程師數字抓錯了，越低越好，要抓 75% 才會過關)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「程式碼覆蓋率 (Code Coverage)」** 是一個在開發界被嚴重濫用與神化 (KPI-driven) 的雙面刃指標。即使一隻程式的「行數 (Line)」被測試機器跑過了 90%，這【絕對不代表】它的「邏輯路徑 (Path)」與「條件狀態 (Condition)」被完整測試了。
    *   例如：一行除法 `c = a / b` 必定會被跑到 (Line coverage 100%)。但如果測試案例中只有寫 `10 / 2`，這行程式看似安全無虞。到了晚上真實駭客輸入了 `10 / 0` (Edge case 極端邊界案例)，系統就直接除以零崩潰當機了！這個慘痛教訓警告我們：傳統的 Line Coverage 是無法找出安全漏洞 (如 Buffer Overflow, Injection, Divide by Zero) 這種深藏在惡意邊界條件內部的鬼魂的。我們必須依賴更多的 Abuse Cases (濫用測試案例) 與 Fuzzing 才行。

#### **13. During a vulnerability assessment, a security analyst uses an automated network scanner to discover that a specific server is running an older version of OpenSSL. The scanner flags this as a "High Request" vulnerability because this version of OpenSSL is known to be vulnerable to the 'Heartbleed' bug. The analyst manually drafts a report and hands it to the operations team to patch. The analyst did not attempt to actually steal data from the server using the Heartbleed exploit. This activity is precisely defined as:**
**(在進行一場安靜地盤查任務 (Vulnerability Assessment) 中，一位負責掃地的工作人員，拿著一台發出逼逼聲的全自動雷達掃描機掃過機房。這台大機器突然瘋狂亮起『高危險級死劫 (High Risk)』紅燈！因為雷達照出，角落有台孤獨老機器，它身上流著過期八百年的 OpenSSL 舊版血液。這台掃描機告訴他：『這台裝病的老頭，身上正帶著那威震天下、能吸出心臟血的『心跳出血大洞 (Heartbleed bug)』！』。這名掃地僧點點頭，轉身拿起桌上的鋼筆，把這個紅燈記錄在一張紙本報告上，然後走過去遞給了負責修機器的維修班要求他們打補丁。從頭到尾，這名掃地僧【連一秒鐘都沒有、更不敢試圖真的去用這個漏血洞，把那台主機裡的機密給抽血偷出來看看】。這般斯文、不流一滴血的點名動作，在資安界精準且不容錯認地被稱作什麼專門術語？)**
A. Penetration Testing (拿刀子真槍實彈捅進去的滲透測試大亂鬥)
B. Vulnerability Scanning (Vulnerability Assessment) (這就是純粹點名、不動刀動槍的【弱點盤查儀器大掃描 (Vulnerability Scanning) / 弱點評估盤點 (Vulnerability Assessment)】！)
C. Fuzzing (盲打亂碼瞎砸機器的隨機破壞法)
D. Red Teaming (紅藍兩軍機房肉搏的紅隊大演練)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是區分 **弱點掃描 (VA, Vulnerability Assessment)** 與 **滲透測試 (PT, Penetration Testing)** 最經典、必考的一條分水嶺紅線。
    *   **弱點掃描 (VA)：** 是拿著清單 (Scanner) 在大門口點名。掃描機發現「啊這台伺服器門鎖用的是會生鏽的老舊銅鎖 (舊版 OpenSSL)，會被小偷用萬能鑰匙撬開 (Heartbleed)」。掃描員的責任就到此為止：「他把這個可能生鏽的風險記錄在公文上，交給上級」。他【絕對不會、也不被允許】真的把萬能鑰匙放進門鎖裡轉動，去證實到底能不能撬開。
    *   **滲透測試 (PT)：** (與之相反) 滲透測試員會拿著一串真正的萬能鑰匙 (Exploit Payload)，直接捅進那把生鏽的銅鎖裡轉動。如果門開了，他會衝進去把桌上的黃金拍照 (取得實質控制權 Shell / 偷出資料)，然後大喊：「報告！我不只發現門鎖會生鏽，我還成功用它闖進大金庫了，這是確實能殺人的漏洞！這就叫 **Exploitation (漏洞利用/剝削)**」。
    *   這名員工只是寫了報告沒有開槍 (Exploit)，所以這是純粹的弱點掃描 (VA)。

#### **14. A security team is planning a massive "Red Team" exercise. Unlike a standard penetration test that focuses purely on finding software vulnerabilities within a specific application scope, what is the primary, overarching objective of a comprehensive Red Team engagement?**
**(資安大部隊正在秘密籌畫一場撼動公司的超級『紅隊 (Red Team) 大軍特種演習』！這可不是那些只知道坐在冷氣房裡、戴著眼鏡死命盯著單一網路打洞漏洞的普通滲透測試員 (Standard pen test) 在玩的無聊打靶遊戲。相比於那些只懂找軟體程式碼小臭蟲的活動，這場驚天動地的【全範圍紅隊大軍特種奇襲演練 (comprehensive Red Team engagement)】。其在戰略層級上，所真正瞄準的、懸掛在那雲端大旗上最不可告人、最巨大的一統首要核心任務目標到底是什麼？)**
A. To train the developers on how to write secure Java code using secure libraries. (為了去機房開補習班，教那群猴子工程師怎麼寫好安全的程式碼積木)
B. To evaluate the organization's holistic security posture, including the physical security guards, employee susceptibility to social engineering, and the active detection and response capabilities of the internal "Blue Team" (SOC). (它化身為死神，為了去無情檢驗這整座帝國的【全方面、神明死角般的全息安全體質 (holistic security posture)】。這包含去無情測試：樓下警衛室的大門保全會不會被騙、去釣魚試探公司裡那些無知小白兔員工會不會被社會工程學話術騙走密碼、以及最最最核心殘酷的：『去活教材殘酷驗證自家裡養那幫負責守夜抓賊的「藍隊大軍 (Blue Team / SOC)」，在遇到這種級別的隱形入侵時，他們手上的雷達警報能力與大兵反擊反應速度到底有多垃圾遲鈍』！！)
C. To achieve 100% SAST code coverage. (為了去達成老闆那可悲的百分之百滿分靜態安全掃描代碼行數的神話數字)
D. To patch and update all Windows servers in the data center. (去幫整個地下室機房的所有 Windows 老舊爺爺主機重灌打好微軟的系統大補丁包)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「紅隊演練 (Red Teaming)」** 與普通滲透測試 (Pen Test) 有著巨大的戰略維度差異。
    *   滲透測試 (Pen Test) 是：甲方給你一個 IP 跟三天時間，請你幫我把這個網站看有沒有 XSS 或 SQLi 漏洞。
    *   **紅隊演練 (Red Team)：** 是一場**沒有範圍界線 (No Scope limits)** 的全方位真實駭客軍事演習。紅隊的目標不是「找到一個洞」，而是「拿到老闆的機密檔案並離開」。因此，紅隊無所不用其極：他們會寫釣魚信件騙前台小妹點擊木馬 (社會工程學)、甚至會親自穿上水電工制服拿著假識別證騙過大樓警衛，把 USB 隨身碟插進公司的印表機裡 (實體安全入侵 / Physical Security)。而紅隊最龐大的目的，是為了「磨練自家防守方 (藍隊 Blue Team / SOC 中心)」。當紅隊在裡面像鬼影般潛行時，藍隊的機器雷達有沒有響？藍隊有沒有在三小時內把紅隊踢出去？這是一場人對人 (Adversarial) 的綜合體能大測驗。

#### **15. A software engineering team implements a "Bug Bounty" program, inviting independent security researchers from around the world to attack their production application and report vulnerabilities in exchange for monetary rewards. What is the most significant inherent risk or challenge of relying heavily on a public bug bounty program as a primary testing strategy?**
**(一家自我感覺極端良好的軟體科技大廠，自豪地在全球拉下了名為『懸賞找蟲大賞 (Bug Bounty 抓漏獎金)』的神聖黃金大榜。他們拍胸鋪發出通緝死令：『歡迎全地球各路神仙、綠林好漢與獨立蒙面駭客們！儘管放馬過來向我們營運中火線大主機發動瘋狂無底線突變攻擊！只要你打壞了找出了洞，拿著人頭來，我老子就大把撒現金獎勵賞你！』。雖然看似霸氣，但若這家公司愚蠢到把這種『全公開懸賞大魔鬥』當成了自家防護網的第一且最主要的保命測底底牌。他們將無可避免、與生俱來會立刻陷入並被哪一種『最大的內在混亂魔咒與挑戰風險』給凌遲溺斃而死？)**
A. Researchers will find zero bugs because the application is already heavily tested. (那是不可能的：根本沒人會找到半隻蟲子，因為駭客看到他們寫的扣太美就自動投降了回家)
B. Bug bounty programs provide consistent, predictable, and fully comprehensive test coverage of every single feature in the application. (這是假象：他以為這樣就能像機器一樣，保證每個按鈕、每次點擊都能獲得百分百完美、穩定且完全被覆蓋的安全檢察證明)
C. It generates a massive volume of duplicate submissions, out-of-scope reports, and "beg bounty" spam, requiring significant internal triage resources to verify the legitimacy of the findings. (這就是『被蟲海淹死的活摘大慘案』！這個榜單會在一瞬間讓天下所有三教九流的瞎眼無腦投機客蜂擁而上，向這家公司狂暴傾瀉倒滿出【猶如土石流大屠殺般發了瘋：無數個早已重複八百遍的老掉牙舊洞回報、根本不在規定的防衛區域內 (out-of-scope) 瞎扯的亂打靶狗皮膏藥、甚至像是一群伸手拿碗乞討的「討飯賞金獵人 (beg bounty spam)」灌爆你的信箱】！這會逼迫這公司自己的內部維修工，必須耗費天文數字般的精神與血淚時間，一封封像山一樣高去挑糞、鑑定那些垃圾投報信件到底是真的還是來騙錢的 (triage resources)！)
D. It replaces the need to run SAST and DAST in the CI/CD pipeline. (從此他們就可以正大光明把 CI/CD 那堆什麼 SAST 和 DAST 老古董機器全部丟進火爐燒了不再需要買)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「漏洞賞金計畫 (Bug Bounty)」** 雖然是尋找未知漏洞 (Crowdsourced security) 的絕佳補充方案，但它絕對不能成為「主要測試策略」。它最大的痛點在於 **"訊噪比極低 (High Signal-to-Noise Ratio)"** 以及 **"審查分類 (Triage) 成本巨大"**。當程式一公開開放賞金，印度或全球的初級腳本小子 (Script Kiddies) 會拿著全自動掃描機對你的網站狂轟濫炸。他們會為了賺 50 塊美金，一天寄給你 500 封「報告」，其中 490 封是「發現網站沒有設定防止點擊劫持 (X-Frame-Options) 啦」這種無聊至極的低級、重複 (Duplicate) 的垃圾警報，更有甚者是直接來信要錢的 "Beg Bounty"。這會瞬間榨乾公司內部資安小組每天的精力，害他們沒空處理真正致命的漏洞。

#### **16. A developer is writing Unit Tests for a newly created 'User Authentication' module. Which of the following test cases represents the BEST example of "Negative Testing" (Abuse Case Testing) for this module?**
**(一名孤苦伶仃的工程師，正趴在鍵盤前幫他剛剛一手捏成的『使用者登入身分核實驗證把關精靈大模組 (User Authentication)』撰寫小如螞蟻般的【單元測試劇本積木 (Unit Tests)】。在下列被選召的各大測試場景劇本中。到底哪一齣戲，才是被資安大祭司認為，最能狗血完美、無比殘忍演示何謂『反向破壞性負面大測試 (Negative Testing) / 被往死裡打的惡意濫用場景神測試 (Abuse Case Testing)』的最佳金獎範本代表作？)**
A. Submitting a correct username and a correct password to verify the user is successfully logged in. (平淡無趣的爛戲：拿著『絕對正確的名字』跟『完美匹配的銀行密碼』敲門，看到門乖乖打開，並鼓掌說主角登入成功了過著幸福快樂日子)
B. Submitting a username that does not exist in the database with a random password to verify the system explicitly rejects the login attempt and returns a generic error message. (這是一齣血淋淋折磨機器的【反派惡質測試神劇本 (Negative Testing)】！故意塞進去一個『資料庫祖宗十八代歷史都未曾記載過、根本不存在瞎編的鬼魂假名字』，再胡亂配上一把『像是用臉滾鍵盤打出來的密碼亂碼』。目的就是要拿來狠狠考驗、鞭打這個門房系統，看它是不是有長眼睛、能【直接且極度冷血無情地當場拒絕踢飛這隻鬼魂】。甚至！還要確保這門房不會口沒遮攔大嘴巴洩密這傢伙不存在，而是只丟下一句『無聊且千篇一律的官方撲克臉客套客套打槍警告信 (Generic error message)』作終結！)
C. Verifying that the login screen renders correctly on a mobile device browser. (無聊透頂的看美工：測試這登入版面在手機瀏覽器上不會跑版長得很帥)
D. Confirming that the login process completes within 500 milliseconds. (無恥的飆車測試：拿著碼表測量這登入開門的關閘動作會不會超過半秒鐘)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 在軟體測試理論中，測試分為兩大陣營。
    *   **正向測試 (Positive Testing, 俗稱 Happy Path)：** (如同選項 A)。給程式「正確的、預期的好寶寶輸入」，看系統有沒有正常執行。這是傳統 QA 注重的。
    *   **負向測試 (Negative Testing, 也是資安最重心的 Abuse Case 濫用測試)：** (如同選項 B)。給程式「充滿惡意、極端、故意找碴、超出邊界範圍的壞壞垃圾輸入」。看軟體在面對這些無理取鬧時，是會堅強地擋下攻擊並報錯，還是會崩潰噴出滿屏的密碼 (資料外洩)。不僅如此，在登入模組的錯誤處理中，傳回「模糊統一的錯誤訊息 (Generic error) 如："帳號或密碼錯誤"」也是資安天條，因為這能防止駭客利用錯誤訊息猜出「到底這帳號在資料庫存不存在」(User Enumeration / 使用者釣魚探測防禦)。

#### **17. Following a major architectural refactoring of a monolithic application into microservices, the QA team wants to verify that the newly independent 'Order Service' can successfully communicate, authenticate, and exchange data with the 'Payment Service' across the internal network. What specific level of testing must be performed to validate this interaction?**
**(在一場壯烈如史詩般的『萬年祖宗單體大鐵塊架構大屠殺 (architectural refactoring of monolithic application into microservices)』！經歷了無情的分屍切割重獲新生後，原本擠在同一個肚子裡的器官們，現在全變成散落在內網四處、獨立漂流的微型戰艦 (Microservices)。現在，QA 品保總司令下了一道聖裁：『我必須親眼看見並確認那些重獲自由的獨立小部隊！尤其是那艘【下單指揮戰艦 (Order Service)】，在穿越一片汪洋火海的內部網路後，它有辦法【成功順暢地呼叫、通關安插驗證識別證 (authenticate) 並且跟另一艘【結帳收款要錢母艦 (Payment Service)】無縫串接並轉移幾十萬的物資黃金資料交易 (exchange data)】！』為了這場如大橋接點確認般的歷史性一刻相會，大總管必須降下啟動哪一項【專屬、甚至為這而生的特種層級測試防線大典】？)**
A. Unit Testing (微型單元小測試)
B. Integration Testing (這就是見證兩軍勝利會師神聖大結合的【整合測試大連線大典 (Integration Testing)】！)
C. SAST (靜態白箱死屍大掃描)
D. User Acceptance Testing (UAT) (拉著大老闆跟貴賓阿婆來按網頁按鈕的使用者最後驗收滿意度調查大會 (UAT))

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是典型的「軟體測試層級金字塔 (Testing Pyramid)」考題。
    *   **單元測試 (Unit Test, A)：** 負責測 Order Service 自己內部的一個小函數 (如算加法)。
    *   **整合測試 (Integration Test, B)：** 當涉及「兩個以上」的模組、服務 (Service to Service)、或者服務連線到資料庫、連線到外部 API 之間的「介面溝通與交火握手 (Interaction)」時，這就必須靠 Integration Testing 來驗證。在微服務架構中，這一步更是重中之重，它要確保服務 A 用來呼叫服務 B 的 API 端點長相與通關密語 (TLS / JWT Tokens) 是兩邊兜得起來的。
    *   **為何不是 SAST (C)：** SAST 只是看死屍，無法驗證實際網路連線是否暢通。
    *   **為何不是 UAT (D)：** UAT 是最後上線前，讓「真正的終端用戶客戶」去試用畫面滿不滿意的一種走流程黑箱體驗，與測試兩個後台微服務通訊毫無關係。
