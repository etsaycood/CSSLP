# 第三套全真模擬試題 (Exam 3) - 答案與詳解本
## 領域 2：安全的軟體生命週期管理 (Secure Software Lifecycle Management) (14題) - Part 1 (Q1-Q7)

---

#### **1. A highly regulated financial institution is launching a new initiative to build a customer-facing wealth management portal. The Chief Information Security Officer (CISO) establishes a strict policy: Before a single line of code is written or wireframe designed, a specialized cross-functional team must formally document the exact types of sensitive data the application will handle (e.g., PII, financial portfolios), define the regulatory compliance frameworks it must adhere to (e.g., GDPR, PCI-DSS), and classify the overall risk level of the project. Which phase of the Secure Software Development Lifecycle (SSDL) is this critical foundational activity occurring in?**
**(一家受到國家級法規嚴密監管的金控財閥，正雄心勃勃地準備打造一座全新的『面向全球頂級 VIP 客戶的巨大財富管理尊榮入口平台 (wealth management portal)』。在這座大金庫還是一張白紙時，那手握生殺大權的資訊安全長 (CISO) 斬釘截鐵地下了一道死命令：『聽好了！在你們這群死工程師敢敲下【第一行程式碼 (single line of code is written)】、在那些搞美工的設計師敢畫出【第一張 UI 草圖 (wireframe designed)】這兩件破事發生「之前」！我要求立刻成立一支跨部門的敢死隊！這支隊伍必須給我生出一份白紙黑字的太廟聖旨：這系統到底會碰哪些會殺頭的極機密資料 (例如：客戶身分證 PII、幾十億的投資組合)？我們這次到底會被哪些會把我們罰到破產的國際恐怖法規 (像 GDPR、PCI-DSS) 給盯上？最後，給我把這個專案的「整體死亡風險等級」給鑑定出來！』。請問，這等猶如在蓋大樓前先去拜拜看風水、查明地下有沒有未爆彈的這顆最神聖基石動作，是精準落在那偉大的『安全軟體開發生命週期 (SSDL)』中哪一個極度前哨的發展階段？)**
A. Requirements Specification (收集具體該怎麼設計密碼長度、登入畫面的那套規格大典 Requirement)
B. Project Initiation / Planning Phase (這就是萬物始動之前！在還沒討論怎麼蓋、只討論『該不該蓋、蓋了會不會死』的【專案發起誓師大會 / 戰略初始計畫階段 (Project Initiation / Planning Phase)】！)
C. Architecture and Design (已經開始畫出房子幾根柱子的架構設計階段)
D. Deployment and Operations (把房子蓋好推出去賣的部署與營運階段)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是 SSDL 最經典的第一步。很多人會誤選 A (Requirements / 需求分析)。但請注意題目中的關鍵字：「在寫 code 或畫圖之前」、「確定這專案會碰什麼資料、適用什麼法規、並作**風險分類 (Risk Classification)**」。這是比盤點「系統需要哪些資安功能 (Requirements)」還要更早一步的 **Initiation (發起階段)** 的核心任務。
    *   在專案發起階段 (Planning/Initiation)，主要是長官在拍板決策。他們必須做「隱私衝擊評估 (PIA / Privacy Impact Assessment)」的初步預估，決定這專案是「高風險 (碰信用卡)」還是「低風險 (只是一頁式廣告)」。如果判定是高風險，才會進入下一個階段 (Requirements) 去制定「密碼要幾碼、要用什麼加密器」這種具體的功能規格。

#### **2. A veteran software development team decides to transition from a Traditional Waterfall methodology to an Agile framework (Scrum) to improve time-to-market. The Lead Security Architect is highly concerned about integrating security into this fast-paced environment. To successfully embed security into Agile without becoming a massive bottleneck that universally blocks developers, what is the MOST effective strategic approach the Architect should mandate?**
**(一支滿臉鬍渣、習慣了以前那套像老牛拉車般『傳統瀑布式開發大陣法 (Traditional Waterfall)』的老軍隊。為了追求天下武功唯快不破，他們決定大誓師、全面轉型皈依那一出拳如風的『敏捷開發神教 (Agile Scrum)』，以求光速出貨 (time-to-market)！但這時，軍隊裡的首席資安大護法卻愁眉苦臉、心驚膽跳：『這群猴子現在跑這麼快、兩週就出兵一次。我以前那種習慣等到最後一天才擋在門口慢慢搜身的資安大絕招，絕對會被這群猴子嫌慢給踩死，甚至成為拖垮全軍速度的罪人 (massive bottleneck)！』。為了能完美將這笨重的龜殼資安防護網，如絲綢般無縫融入這超高速的敏捷閃電戰中。請問這位護法【最必須】痛下決心採取那一套最高明的核心戰略轉型手法？)**
A. Require a comprehensive, final, two-month-long penetration test at the very end of the project before the first release goes live. (頑固不化：逼迫這群敏捷部隊在最後要上線前，硬生生停下來等你做兩個月慢吞吞的最終滲透大安檢)
B. Demand that developers write all security requirements into a massive, 500-page document before coding begins. (逼工程師在開工前寫五百頁的資安廢話說明書)
C. Integrate automated, lightweight security testing tools (like SAST and DAST plugins) directly into the Continuous Integration/Continuous Deployment (CI/CD) pipeline to provide immediate, iterative feedback to developers on every code commit. (這就是『天下武功唯快不破』的最高奧義：【以自動化魔法打敗人工速度！直接將那些如幽靈般輕巧、快如閃電的自動化防毒照妖鏡小精靈 (猶如輕量級的靜態掃描 SAST 或動態 DAST 套件)，如寄生蟲般活生生融合注射進部隊那條每天出兵必經的高速公路大管線 (CI/CD pipeline) 裡！】。讓這群猴子每次提交程式碼的瞬間，立刻遭到雷劈反彈、即時(immediate) 且不厭其煩地 (iterative) 教訓他們程式碼哪裡有毒並打回去重改！)
D. Assign one dedicated security auditor to manually review every single line of code written during each two-week sprint. (派一個老花眼的資安老頭子，手工去一行一行看那每兩週幾千萬行的爛扣)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「將資安融入敏捷 (DevSecOps)」** 是現代軟體安全最高指導原則。敏捷開發 (Agile) 講求快、兩週一個衝刺 (Sprint)、每天推 code 幾十次。如果資安還停留在傳統瀑布流時代的「人工看扣 (D)」、「寫好寫滿 500 頁安規合約書 (B)」，或是「最後一關才來花兩個月做滲透 (A)」。這會把敏捷開發那高昂的出貨速度給徹底捏斷，資安會變成所有開發大軍唾棄的絆腳石。
    *   **唯一解法：** 把沉重的人工資安，化作 **"輕量自動化 (Automated, lightweight testing)"** 工具。嵌入到 CI/CD 高速公路 (Jenkins, GitLab CI) 中。工程師一按 Save，SAST 就自動掃 10 秒鐘。沒事就過，有毒就亮紅燈退件。這種快速、自動、微小的回饋循環 (Fast Feedback Loop)，是 DevSecOps 唯一的存活之道。

#### **3. An organization relies heavily on offshore development teams to build proprietary software. Recently, several source code repositories were found exposed on a public GitHub server. To drastically reduce the risk of intellectual property theft and malicious code injection by internal developers, the security policy explicitly mandates that all developers are physically barred from saving source code onto their local laptops' hard drives. Instead, they must connect remotely to a centralized, heavily monitored server environment where the IDE and code reside, preventing data exfiltration. What type of security control is this centralized development environment?**
**(一家家大業大但又想省錢的帝國，極度仰賴國外那群龍蛇混雜的海外低價外包傭兵團來寫最核心的搖錢樹程式體。最近發生了一場大醜聞：這帝國好幾包價值連城的祖傳程式碼庫，居然被人像垃圾一樣扔在那個全世界路人都能圍觀的公開大廣場 (GitHub) 上免費任人看！為了徹底斬斷這幫海外傭兵當內鬼、偷取商業機密智財產 (intellectual property theft) 的齷齪髒手、以及防範他們偷把木馬塞回來的危險。安全長下了一道近乎禁錮的非人道絕殺令：『聽好了！從今以後，這群外包仔的破爛筆記型電腦實體硬碟上，【絕對物理性不准、永遠被剝奪】存下半滴我們家的神聖程式碼權力！』。這群傭兵這輩子只能用他們的遠端軟體，像是看電影一樣連線回我們這座『重兵看守、四處都是監視器、連蒼蠅都飛不出去的中央隔離死牢開發廠』！所有的寫扣軟體 (IDE) 跟程式碼都只准死死鎖在這座死牢裡，斷絕任何偷拷貝外流 (data exfiltration) 的可能。請問這座猶如『代碼血汗防洩大監獄』的集中營設施，是哪一套安控制度？)**
A. Endpoint Detection and Response (EDR) (監視電腦有沒有被病毒入侵的端點神探小精靈 (EDR))
B. Software Composition Analysis (SCA) (打開程式碼看裡面有沒有用到過期開源軟體的 SCA X 光機)
C. Virtual Desktop Infrastructure (VDI) / Secure Remote Development Environment (這就是如同將靈魂抽離肉體、把大腦鎖在雲端大保險箱裡不給你看拿的【虛擬桌面死牢控制大陣 (Virtual Desktop Infrastructure, VDI) / 極淨無塵室之雲端安全遠端開發堡壘 (Secure Remote Development Environment)】！)
D. Data Loss Prevention (DLP) Network Appliance (在網路出口檢查你有沒有偷夾帶機密檔案出去的 DLP 攔截網)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 面對「外包團隊 (Offshore / Third-party Developers)」最致命的挑戰就是：**你無法控制他們那邊的硬體與環境安全，他們隨時能把你的 Source Code 放進 USB 隨身碟帶走去賣錢**。
    *   **VDI (Virtual Desktop Infrastructure) 或 DaaS (Desktop as a Service)：** 這是終極的物理與邏輯隔離殺手鐧。外包工程師的筆電就只是一個「瞎眼的螢幕與鍵盤 (Thin client)」。他們透過遠端桌面 (RDP/VNC) 連進公司總部的伺服器。所有的撰寫、編譯、儲存動作，都 100% 發生在公司總部的「虛擬桌面」機房裡。工程師的實體筆電裡連 1KB 的公司程式碼都沒有，而且 VDI 會強制鎖死「無法把雲端文字複製貼上 (Copy-Paste) 拿回本地電腦」，也「無法將本機 USB 送上虛擬機」。這徹底斷絕了 Data Exfiltration (資料外流)。雖然 D (DLP) 也有些微阻止外流的防禦力，但只有 VDI 是連檔案都不讓它落地，屬於治本的根源隔離解法。

#### **4. A project manager is calculating the budget for a major software rewrite. The security team requests a significant portion of the budget to conduct thorough Threat Modeling and Secure Architecture Reviews during the early Design phase. The project manager, trying to cut costs, suggests skipping these steps and just fixing any bugs found during the final testing phase right before release. According to the foundational principles of Secure Software Lifecycle Management, what is the most scientifically accurate argument the security team should use to definitively reject the project manager's proposal?**
**(一位滿眼只有錢跟成本、每天都在拿算盤斤斤計較的專案大掌櫃。正在為一場如史詩般的『全境軟體大重寫工程』編列微薄的糧草預算。這時，窮凶極惡的資安護衛大隊衝進來，大開獅子口要求分走一大塊預算黃金，說要在專案【剛開始畫地圖找方向的早期設計大發想階段 (early Design phase)】，舉行那玄之又玄的『白板威脅兵棋大推演 (Threat Modeling) 與建築學安控風水大盤查 (Secure Architecture Reviews)』！大掌櫃為了省錢，居然翻了個白眼提出一個找死的提議：『拜託喔！這幾百萬的兵推預算能不能省了直接砍掉？我們何不把錢省下來，等你們那些工程師兩年後把城牆全部蓋好、快要開門做生意前 (final testing phase right before release)。我們再來舒舒服服地請個安檢員去抓蟲子、看到洞再補水泥修補就好了嘛！』。若要以『神聖資安生命週期』的最基礎偉大定理來反擊，資安大隊應該把哪一條科學且絕對無法辯駁的神諭金律狠狠砸在這位大掌櫃臉上，讓他徹底閉嘴？)**
A. Fixing a fundamental architectural security flaw discovered during the final testing or production phase is exponentially more expensive, time-consuming, and difficult than finding and mitigating that exact same flaw on paper during the early design phase. (這就是流傳千古的『軟體界蝴蝶效應天條』：【聽好你這瞎眼的老頭！如果在快要完工甚至上線營業時 (final testing/production)，才猛然發現整座大樓的承重地基根本打錯爛透了！這時你要拆掉重建、付出的血汗、時間與幾千萬美金的代價 (exponentially more expensive)。將會比你當初在畫紙上 (early design phase) 用麥克筆找出一條爛畫線並順手擦掉防堵的成本，還要高出『呈指數級幾百倍爆炸的幾何級數毀滅代價』啊！】)
B. Threat modeling guarantees that the final code will be 100% bug-free. (用吹噓的神話騙他說只要畫了兵棋圖，寫出來的程式碼就會被天使降臨保佑 100% 不會有一隻蟲子產生)
C. It is illegal under federal law to skip threat modeling. (瞎扯說不畫兵棋推演，美國聯邦警察會來把你抓去坐牢)
D. Developers are incapable of fixing bugs found during testing. (怒罵那些負責寫扣的猴子太蠢，如果在最後測試才找到漏洞，他們那破腦袋是絕對修不好的)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 這是軟體工程史 (包括資安工程) 最經典的一張曲線圖：**「The Cost of Fixing Defects (修復缺陷成本曲線 / 又稱 Boehm 曲線)」**。
    *   這條定律是：在「需求發想 (Requirements)」或「設計 (Design)」階段，你在白板上發現「登入流程少加了忘記密碼身分驗證」，你只要花 5 分鐘把白板上的字擦掉重寫就解決了。但如果你是為了省錢不畫白板，讓工程師自己瞎搞。到了「快要上線測試 (Testing) 甚至是已經開賣 (Production)」才發現！這時候程式碼已經寫了幾十萬行、資料庫已經開好長滿了資料。你要修這個洞，你必須打斷無數的模組關聯、重建資料庫、重新走一次漫長的 QA 測試流程。這個修補成本，會比在設計初期揪出來，高出 **30 倍、100 倍甚至更多 (Exponentially more expensive)**。這就是為何 **"Shift Left (安全左移，在生命週期越早階段做資安越好)"** 是無可撼動的黃金準則。(所以 A 完全正確地描述了這等指數級膨脹的毀滅性代價)。

#### **5. In defining the Governance, Risk, and Compliance (GRC) framework for a massive software engineering department, the CISO tasks a committee with writing the absolute highest-level, overarching, non-negotiable directive. This single document must formally declare the CEO's absolute commitment to secure coding practices, state the ultimate goals of protecting customer data, and mandate that all software projects must undergo a security review. This document does not contain step-by-step instructions or technology-specific rules. What specific type of governance document is this?**
**(在這家龐大如帝國般擁堵的軟體大軍中，資訊安全長 (CISO) 為了建立那傳說中能統御百官的『至高無上治理、大風險與鐵律合規神聖教條 (GRC framework)』。他下令一群長老會，去幫他起草一份【位階凌駕於天地法則之上、有如玉皇大帝登基聖旨般神聖且完全沒有商量妥協餘地、絕對獨裁的大綱憲法 (highest-level, overarching, non-negotiable directive)】！這份唯一的太廟聖旨上，會由當今統治天下的皇帝 (CEO) 親自按上血指印，向著全天下大聲宣誓：『寡人發誓！這家大軍必定死守絕對安全的無瑕程式碼撰寫大義！並且以死守那千萬子民的身家資料保護為我軍霸業之最終極目標！所有膽敢違反跳過資安大安檢的專案，皆視為謀反！』。注意！這張薄薄幾頁的聖旨上，【徹徹底底、完全沒有寫上任何一條教你怎麼拿筆寫程式的囉唆細節 SOP、也絕對隻字不提任何一家廠商或那些不入流的具體技術死規定】。這張只宣示大愛與死命令的帝王級統治文件。在 GRC 治理學殿堂裡，尊稱為何？)**
A. A Standard (一份精準規定密碼要十二個字元的標準度量尺 / Standard)
B. A Procedure (一本充滿箭頭圖案、教你先按哪個按鈕再按哪個按鈕的傻瓜 SOP 說明書 / Procedure)
C. A Guideline (一本苦口婆心、拜託你最好乖乖照著做如果不聽也就算了的教導推薦手冊 / Guideline)
D. A Policy (這就是至高無上、無情獨裁、代表皇帝親臨且只有方向大限而無囉唆細節的【絕對皇權安控大政策憲法 (A Policy)】！)

*   **正確答案 / Correct Answer：D**
*   **[解析邏輯]**
    *   **為何 D 是最佳選擇：** 這是 CISSP/CSSLP 的 GRC 文件四層金字塔基礎必考題：
        1.  **Policy (政策)：** 金字塔最頂端。由 CEO/高層發布。它是非常高層次、指導性、宣示性的 (例如："保護客戶隱私是第一要務"、"禁止共用帳號")。它**絕對不會**寫 "請使用 RSA-2048 加密"，因為三年後技術變了 policy 就會過時。它必須是長期且不容妥協的目標。
        2.  **Standards (標準)：** 把 Policy 具體化、量化的鐵律。例如 "根據保護隱私政策，本公司所有網頁伺服器【必須】使用 TLS 1.2 以上版本，密碼至少 12 碼"。這也是強制性的 (Mandatory)。
        3.  **Guidelines (指南)：** 建議、最佳實踐 (Best practices)。例如 "建議開發者使用 C# 而不是 C++"。如果不聽也不會被開除，是非強制的 (Optional)。
        4.  **Procedures (程序)：** 最底層的 Step-by-step 說明書。例如 "如何安裝 TLS 憑證的 10 個無腦步驟教學"。
    *   題目中明確描述「最高層級 (highest-level)」、「CEO 背書」、「沒有具體技術細節 (no technology-specific rules)」且「無妥協空間 (non-negotiable)」，這完全是 **Policy** 的完美定義。

#### **6. A development team actively maintains a large, cloud-native application. The team explicitly monitors multiple threat intelligence feeds and the National Vulnerability Database (NVD). Upon receiving an immediate alert that a critical Zero-Day Remote Code Execution vulnerability has just been discovered in the exact version of the `Log4j` logging library their application currently uses in production, the team instantly halts all new feature development. They immediately pivot their entire Sprint capacity to ripping out the vulnerable library, applying the official patch, and redeploying the application within 24 hours. This rapid, proactive response is a classic example of which critical lifecycle management process?**
**(一支負責顧著這片如繁星般龐大『雲原生大堡壘』的開發義勇軍隊！他們平時不只會寫扣，他們還分心派出了好幾名斥候，天天死盯著各國黑市情報站與那份發著紅光的『美國國家神聖漏洞通緝大榜單 (NVD)』。某天中午！警報聲以劃破天際之姿狂響！雷達顯示：外面剛誕生了一隻毀天滅地、能直接凌空遠距殺人的零日處決大病毒 (Zero-Day RCE)！而這隻病毒唯一攻擊的宿主死穴元件，正是他們家目前每天大門敞開正在熱烈使用的『那組最關鍵的 `Log4j` 日誌看門狗小積木的某個特定版本』！這支義勇軍二話不說，【瞬間吹起集結號、將手邊正在幫老闆趕工的所有賺錢新功能專案全部活生生掐斷停工 (instantly halts all new feature development)！全員武裝上陣！他們把未來這兩週的所有火炮資源，全部拿去瘋狂開膛破肚，把那有毒的小狗積木給活生生拔出剔除！換上神聖解藥大補丁！並在短短如奇蹟般的「24小時內」讓整座大堡壘重新上線迎戰！】。這等電光石火般的高速拆彈與救援神反應，是演繹了哪一套拯救蒼生的核心生命週期防護流程大陣？)**
A. Vulnerability Management / Patch Management Lifecycle (這就是令無數防衛戰士肝腦塗地、跟死神瘋狂賽跑的【無限弱點死穴追捕獵殺與極限疫苗補丁修補注射生命大巡迴 (Vulnerability Management / Patch Management Lifecycle)】！)
B. Change Advisory Board (CAB) approval process (這是在開冗長且無聊、三十個人投票決定能不能改門口燈泡的變更審查大鳥龍會議)
C. Disaster Recovery Tabletop Exercise (這只是泡著咖啡坐在長桌前，拿著大富翁地圖演練兵推大災難逃生演習)
D. Software Composition Analysis (SCA) onboarding (這只是新兵報到去採購一台軟體基因掃描機來放)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **「弱點管理 (Vulnerability Management)」** 是一個不眠不休的動態大防衛生命週期。它包含四個步驟：發現漏洞 (Discovery/NVD alert) -> 衝擊評估 (Assessment, 發現自家有在用) -> 修補/緩解 (Remediation/Patching, 團隊停下手邊工作去打補丁) -> 驗證修復 (Verification, 成功上線)。
    *   題目描述了從「盯著情報網收到 NVD 警報」到「24 小時內瘋狂打好補丁 (Patching) 上線上營運」，這是對 Vulnerability Management Lifecycle 運作最生動的血淚寫照 (活生生的 2021 年 Log4j 事件翻版)。這是一個在營運維護階段 (Operations & Maintenance) 永遠不會停止的恐怖大迴圈。

#### **7. A global healthcare software vendor is undergoing an arduous external audit. The auditor demands undeniable proof that the vendor possesses a formalized, reliable, and repeatable process for securely wiping all Patient Health Information (PHI) from development databases, securely archiving the final version of the source code, and permanently revoking developers' access permissions to that specific project's repositories once the software product officially reaches its End-of-Life (EOL) and is completely retired. Which final phase of the Secure Software Lifecycle Management is the auditor rigorously investigating?**
**(一家握有全球生殺大權的跨國醫療軟體大盤商，正被一位近乎變態、吹毛求疵的外部稽核死神給層層逼問拷打。這死神拿著鐮刀指著這群廠商要求提出無可抵賴的鐵證：『你們這群貪圖暴利的傢伙！我不管你們以前寫軟體有多認真！我現在要看到你們到底有沒有一套【冷血、無情、且能夠次次完美發動如終極送行者大典般的固定火葬儀式 SOP】！當你們家某套賺不到錢的老骨董軟體，被宣判死刑、正式宣告【停止呼吸、走到生命的盡頭 (End-of-Life / EOL) 且準備關門大吉報廢拋棄時 (retired)】！你們是不是真的有派人去那落塵的舊資料庫裡，把那些成千上萬的極機密無辜病患醫療報告 (PHI) 給無情地用化骨水銷毀抹除掉？你們有沒有把這套軟體最後最古老的那份始祖程式碼給鎖進神聖的冰層時空膠囊裡永久保存？最後！你們有沒有像拔掉呼吸器一樣，【絕對且永久地褫奪斬斷、拔掉那些老工程師們這輩子再也不准進去那片荒廢程式碼舊區亂翻舊地圖的通行證權力 (permanently revoking dev access)】？』。請問，這死神這般近乎對死人鞭屍的嚴厲拷問。他所盤查盯哨的，正是神聖軟體生命大輪迴週期 (SSDL) 中那最無情、最後一道哪一個終點站階段？)**
A. Incident Response (機房起火狂拉警報的事件應變大火拚)
B. Disposal / Decommissioning / End-of-Life Phase (這正是輪迴終點那化為宇宙灰燼的安息之地：【無情銷毀廢置 / 萬物終結報廢處決 / 軟體生命終結告別大典階段 (Disposal / Decommissioning / End-of-Life Phase)】！)
C. Deployment and Release (敲鑼打鼓放風箏歡慶軟體上架的部署與釋放階段)
D. Maintenance and Operations (每天幫系統吃藥打燈籠的維護與營運階段)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 任何一條成熟的資安生命週期 (Life Cycle) 絕對不是到 "Deployment (部署營運)" 就結束了。它的最後一個階段、也是企業最容易怠惰忽視引爆大災難的，就是 **"Disposal (處置銷毀)"** 或是 **"Decommissioning (報廢退役) / EOL"**。
    *   當系統不再賺錢要被淘汰時，最大的資安地雷就是「那些舊系統主機、沒有刪除的舊客戶機密資料 (Data remanence)、以及工程師留在舊資料庫身上的 SSH backdoor keys」。這些東西如果沒被一套嚴密標準的處置程序 (銷毀資料、封存 Code 備查、撤銷權限) 安全地收掉，往往會在幾年後變成駭客「摸進荒廢老房子、打穿內網」的致命捷徑。稽核員查的正是這個收尾動作有沒有做好 (Secure Disposal)。
