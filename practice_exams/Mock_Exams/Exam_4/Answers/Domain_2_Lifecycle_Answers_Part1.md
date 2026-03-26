# 第四套全真模擬試題 (Exam 4) - 答案與詳解本
## 領域 2：安全的軟體生命週期管理 (Secure Software Lifecycle Management) (14題) - Part 1 (Q1-Q7)

---

#### **1. Your organization is adopting Agile (Scrum) for a new internal web application. The development team argues that conducting full, formal Threat Modeling sessions at the beginning of the project will take too long and violate the Agile principle of "working software over comprehensive documentation." As the security champion, what is the best approach to integrate threat modeling into an Agile lifecycle?**
**(你們的帝國兵工廠，正準備為了一套新的內部驛站系統，全面導入名為『敏捷開發 (Agile/Scrum)』的時髦造車大法。結果那群造車工匠居然群起抗議：「大將軍！在這套敏捷大法裡，講求的是『能跑的程式碼勝過寫一堆廢話公文』！如果你叫我們在此刻大動干戈，把所有人關進小黑屋裡舉行為期一個月的【『傳統重量級威脅建模大剖析法會 (full, formal Threat Modeling sessions)』】，這根本就是嚴重違法了敏捷講求速度的天條！我們不幹！」身為兵工廠裡的資安禁衛軍頭目。面對這群拿著敏捷當擋箭牌的工匠。你該如何用最高明的手腕，把那套繁重的威脅建模大剖析，無縫且優雅地塞進這套敏捷大法裡？)**
A. Defer all threat modeling until the final integration testing phase right before the release sprint. (這就是『把炸彈留到最後一天引爆』的自殺行為！如果在最後一天才發現地基蓋錯，整個敏捷專案會直接破產墜毀)
B. Mandate that the team halt all coding until a comprehensive STRIDE model for the entire system architecture is formally documented and approved by the CISO. (這是純粹的傳統瀑布流 (Waterfall) 霸權思維，這等同於直接拿腳踩死敏捷開發的靈魂，雙方會爆發武裝流血衝突)
C. Break the threat modeling process into smaller, iterative sessions focused only on the specific User Stories being planned for the upcoming sprint. (這就是那名垂青史、剛柔並濟的絕妙兵法：【『化整為零的敏捷威脅建模之術 (Agile Threat Modeling)』】！這套兵法教導我們：既然敏捷是每次只蓋一個小房間 (Sprint)，那我們就不要去想著畫出整座皇城的風水圖！我們就把威脅建模【『像切香腸一樣切碎，每次只針對這個禮拜要蓋的這個小廁所 (specific User Stories)，進行短短幾分鐘的微型威脅剖析 (iterative sessions)』】！這既兼顧了安全，又完美的迎合了敏捷衝刺的靈魂！)
D. Replace threat modeling entirely with automated SAST and DAST scanning in the CI/CD pipeline, as agile teams require automated tools instead of manual analysis. (雖然掃描器很快很符合敏捷，但 SAST 只能幫你找錯字，它【永遠無法取代】人類大腦去設計出『不會被設計圖本身害死』的威脅建模大智慧，兩者不能互相取代)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 探討在 **Agile 敏捷開發中實行威脅建模 (Threat Modeling)** 的調適策略。
    *   傳統的威脅建模 (如微軟的 STRIDE) 通常在設計階段初期進行，可能需要長篇大論的 DFD (資料流程圖) 與數週的會議，這確實與敏捷的 "輕文件、快速迭代" 衝突。
    *   **敏捷威脅建模 (Agile Threat Modeling) 的核心：**
        1.  **Iterative (迭代式)：** 不要在第一天畫出 100% 的系統圖。
        2.  **Story-driven (故事驅動)：** 當 Scrum Team 在每個 Sprint (衝刺期) 挑選出 3 個 User Story (使用者故事/功能) 來開發時，資安人員就只針對這 3 個新功能，進行 30 分鐘的快速威脅討論 (例如畫白板 或 Evil User Stories)。
        3.  將找到的威脅與緩解措施 (Mitigation)，立刻寫回 JIRA 變成新的 Security Stories 或 Acceptance Criteria (驗收標準)。這完美契合了敏捷的步調。

#### **2. Which of the following software development metrics provides the MOST accurate indication of a development team's proactive engagement with the Secure Software Development Lifecycle (SSDLC) early in the process, rather than relying on reactive testing?**
**(在大總管每個月用來評估兵工廠戰績的那本『KPI 記分大名冊 (development metrics)』上。到底哪一項驚世駭俗的計分標準，能夠最精準、最無可辯駁地證明：這兵工廠裡的工匠，已經徹底被洗腦、懂得【『主動在畫設計圖的第一天就開始防範未然 (proactive engagement with SSDLC early in the process)』】，而不是像一群白痴一樣，【『只會等房子蓋好被雷劈了，才手忙腳亂去拿水桶救火 (relying on reactive testing)』】？)**
A. The number of high-severity vulnerabilities discovered by the DAST scanner in the staging environment. (DAST 是在房子蓋好要交屋前才拿炸彈去炸炸看(staging)。如果在這邊炸出很多洞，代表這群工匠前期根本都在夢遊，這正是標準的被動救火 (reactive) 反指標)
B. The percentage of developers who have completed mandatory secure coding training and the number of architecture flaws identified and fixed during early design reviews. (這就是能讓大總管感動到痛哭流涕、象徵著防衛心法已經刻進工匠骨髓深處的『究極超前部署雙重指標』：【『有極端高比例的工匠都乖乖坐在學堂裡學過防身術 (completed secure coding training)』，以及！【『在那個只拿著鉛筆畫草圖的遠古時代 (early design reviews)，他們居然就靠著威脅建模腦力激盪，提早抓出並捏死了無數隻恐怖的架構大巨獸 (flaws identified and fixed during early design reviews)』】！這就叫真正的防患於未然 (proactive Shift-Left)！)
C. The total number of incidents reported by the Security Operations Center (SOC) after the application is deployed. (SOC 那是被駭客打進家門後狂響的警報器，這是最慘烈無比的收拾殘局 (reactive)，代表 SSDLC 徹底破產失敗)
D. The percentage of code coverage achieved by automated unit tests. (單元測試涵蓋率是證明程式有沒有跑順不會當機，它跟「資安/漏洞防禦」沒有直接關聯，更無法證明前期設計有沒有做安控)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這題區分了 **Leading Indicators (領先指標 / Proactive)** 與 **Lagging Indicators (落後指標 / Reactive)** 在 SSDLC 中的差異。
    *   SSDLC 的最高原則就是 **"Shift-Left (左移)"**：在需求 (Requirements) 和設計 (Design) 階段投入資安資源。因為設計階段發現一個漏洞，修補成本是 $1；等到營運階段 (Production) 才發現，修補成本可能是 $10,000。
    *   **Leading Indicators (左移指標)：** 選項 B 測量的是 "預防性投資" (多少人受訓) 以及 "早期捕獲" (設計草圖階段抓到的邏輯缺陷)。這些數字越高，代表團隊越成熟。
    *   **Lagging Indicators (右傾指標)：** 選項 A (DAST 退件數) 和 C (SOC 事件通報數)。這些數字如果很高，代表前面的設計與開發階段如同虛設，把爛攤子全部丟給測試員和維運人員去善後。

#### **3. A financial software company is preparing for a mandatory regulatory compliance audit (e.g., PCI-DSS). The auditors will require verifiable proof that the software changes pushed to production over the past year have undergone rigorous security reviews and testing. What is the most critical asset the organization must maintain to survive this audit?**
**(一家握有天下無數金元寶的金控造車廠，正準備迎接一場由朝廷御史大夫帶隊、殘酷無比的『PCI-DSS 金融大抄家法辦 (mandatory regulatory audit)』。這群御史大人拿著尚方寶劍，凶神惡煞地指著車廠廠長逼問：『聽好！老子要你們拿出鐵甲如山的證據！證明你們過去這一年裡，每一台被推出去賣給老百姓的錢車 (changes pushed to production)！在出廠前，都有乖乖經過我們朝廷規定的那些刀斧水火安檢大刑具拷問 (rigorous security reviews and testing)！如果不拿出來，老子明天就封了你們的金庫！』。請問，為了在這場恐怖大抄家中活下來，並讓御史大人無話可說乖乖閉嘴。這家車廠平時就必須死命守護、並在此刻當作免死金牌呈上去的最神聖寶物是哪個？)**
A. A highly detailed, 500-page Threat Model document created five years ago. (五年前的八股文就跟歷史故事書一樣，根本無法證明『昨天』推出去的那台車子有沒有被檢查過，御史大夫直接把這本破書撕了)
B. Comprehensive, centrally managed Artifacts and Traceability matrices linking security requirements to specific code commits, test results, and deployment approvals. (這就是能把御史大夫的嘴巴死死塞住、讓朝廷大軍乖乖退兵的：【『無敵大連環鐵證生死簿：集中供奉的各種檢驗大印記 (Artifacts) / 以及那能把祖宗十八代神連在一起的終極血脈追溯大矩陣 (Traceability matrices)』】！這本生死簿上，每一行都被紅色硃砂筆畫著線，清楚地將【『當初的資安軍令 (Requirements)』】、綁死了【『那個叫王小明寫出來的程式碼 (commits)』】、再綁上【『經過火燒水淹測試通過的大印章 (test results)』】、最後更釘死了【『大將軍批准兵車出城的血手印 (approvals)』】！這叫鐵證如山、滴水不漏，這就是合規稽核 (Compliance Audit) 唯一看得懂的神聖語言！)
C. The deployment logs from the auto-scaling groups in AWS. (機房的紀錄檔只能證明這台車有出廠、在路上跑，它【絕對無法證明這台車出門前有沒有做過安檢】)
D. A daily backup schedule for all developer workstations. (每天備份工匠的桌機是在防當機弄丟藍圖，跟證明這藍圖有沒有被安檢官看過毫無關係)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是 SSDLC 中關於 **Governance, Risk, and Compliance (GRC) 治理與合規** 的核心實務：**「追溯性 (Traceability)」與「產出物 (Artifacts)」的保存**。
    *   **外部稽核員的特性：** 他們不看 "宣稱"，只看 "證據 (Evidence)"。
    *   如果你告訴稽核員：「我們每天都有做 Code Review」。稽核員的下一個問題就是：「Show me the proof (給我看證據)」。
    *   **Traceability Matrix (追溯矩陣)：** 就是這項防撞網。它是一個關聯系統 (如 JIRA 對連 GitLab 再對連 SonarQube)。它能完美佐證：【需求編號 SEC-01 (密碼長度 12) => 由 Commit #a1b2 實作 => 通過 Jenkins Build #50 的 SAST 雙重掃描綠燈 => 最終由 CI/CD 佈署到 Prod 並且有 Admin-A 的核准 Log】。這份不可竄改的鐵證鍊，是通過任何金融或醫療法規 (PCI-DSS, HIPAA, ISO 27001) 稽核的唯一免死金牌。

#### **4. A team is using a Waterfall methodology to build a flight control system for a new commercial aircraft. Given the extreme safety-critical nature of the software, the project manager emphasizes that security and safety requirements cannot be ambiguous or missed. In which phase of the Waterfall SDLC must formal Risk Assessment and Security Objective gathering be completed to minimize the cost of fixing fundamental design flaws?**
**(一支瘋狂的皇家巨砲大隊，正在依照最古老死板的那本『層層往下跳之究極瀑布大辭典 (Waterfall methodology)』，打造一台要載著幾百號平民飛上青天的『空中飛龍大腦操縱儀 (flight control system)』！因為如果這系統出一點包，這飛龍就會在天上解體墜毀 (extreme safety-critical)！大總管扯著嗓門怒吼：『聽好！那攸關全船幾百口人命的安危鐵條與紅線 (security and safety requirements)，連一個逗號都不准給我寫漏！』請問！在這套古老的瀑布兵法裡，那場猶如宣判死刑般的【『地獄十八層大災難風險沙盤推演 (Risk Assessment) 與安防保命護身符大蒐集條約 (Security Objective gathering)』】，必須要被死死地釘死在瀑布流程裡的【哪個最古老的上游源頭階段】？才能保證如果不小心蓋錯根基，不用花幾百萬兩黃金去把龍骨給拆了重蓋 (minimize the cost of fixing)？)**
A. Architecture and Design (如果等到畫設計圖才開始想風險，那就會發現原本買的那塊龍骨根本不符合防火係數，這時候要改設計圖已經得燒掉一堆黃金了，這還不夠上游)
B. Implementation / Coding (這已經在拿鐵鎚敲龍骨了，這時候才在想安保條件，那根本是等著飛龍墜毀的找死行為)
C. Testing and Verification (這是在出廠前拿大炮轟龍骨，如果在這邊才推演風險抓漏洞，修補的成本是第一天的幾萬倍！)
D. Requirements Elicitation (Analysis) (這就是在最最最源頭、連連一根線都還沒畫、連一塊鐵板都還沒買的：【『終極空想榨腦之大需求盤山挖洞探測搜刮期 (Requirements Elicitation / Analysis phase)』】！在這張白紙階段，你就算發現要改裝成五顆引擎，加一百支避雷針，成本都不過就是浪費幾滴墨水跟口水而已！在瀑布流這個沒有回頭路的懸崖式造車法裡，安全需求絕對必須與業務需求在『需求分析階段』同生共死地被綁死寫盡！否則後果不堪設想！)

*   **正確答案 / Correct Answer：D**
*   **[解析邏輯]**
    *   **為何 D 是最佳選擇：** **「需求擷取/分析階段 (Requirements Elicitation / Analysis)」**。
    *   **瀑布模型 (Waterfall) 的特性：** 水往低處流，極難回頭。階段之間有嚴格的簽核 (Sign-off)。
    *   **SSDLC 左移成本曲線：** 業界公認的黃金定律「在需求階段修補一個架構盲點，成本為 $1。在設計階段變成 $10。在編碼階段變 $100。在測試階段變 $1,000。在正式上線後才被駭客抓到，損失可能是 $1,000,000」。
    *   對於飛機航控系統這種「性命攸關 (Safety-Critical)」的軟體，你不能等畫設計圖 (Architecture) 的時候才突然想到 "對了，這東西需要防震防駭客嗎？"。這些【Security Objectives (安全目標/高階政策)】以及【Security Requirements (安全需求：如通訊必須使用 FIPS 140-2 硬體加密)】必須在專案啟動、列出業務需求的第一天，就透過 Initial Risk Assessment 一併被定義出來。

#### **5. In DevSecOps, a cross-functional team emphasizes the "Shift-Left" philosophy. They configure the IDE (Integrated Development Environment) to immediately warn developers via a linting plugin whenever they type a known dangerous function (e.g., `strcpy()` in C++). What is the primary business justification for implementing this specific "Shift-Left" control?**
**(在一支名為『DevSecOps』的光速流血突擊戰隊裡，牆上掛著一面寫著『瘋狂極致大左移 (Shift-Left)』的血紅大旗幟！為此，這群瘋子居然把監控大砲，直接裝在了工匠們每天拿著鑿子敲敲打打的那張辦公木桌邊上 (IDE linting plugin)！只要這個工匠的手賤，在木板上刻下諸如『`召喚毀滅之溢位惡魔strcpy()`』這種被詛咒的危險咒語。大砲就會在一點零一秒內直接拉響警報電擊這個工匠 (immediately warn developers whenever they type a dangerous function)！請問！大總管花大錢買這尊裝在工匠書桌上的電擊大砲，其背後最精於算計、且能讓金庫省下無數金條的『終極大財主生意經盤算 (primary business justification)』為何？)**
A. It entirely eliminates the need to run SAST tools during the CI build process. (書桌上的電擊棒只是第一道小防線，它絕對無法取代整個大兵工廠裡那台威力無窮的 SAST X 光機。這是輔助，不是取代)
B. It drastically reduces the cost and time required to fix vulnerabilities by catching them at the exact moment the developer makes the error, rather than finding them weeks later in QA. (這就是精算大財主能笑著數金條的完美真諦：【『因為這玩意兒能在那大腦殘工匠剛把狗屎拉在地上的那一瞬間，就叫他自己用手撿起來吃下去 (catching them at the exact moment)！』】！如果沒有這電擊棒，這坨狗屎會被包裝進精美的盒子，花上三個禮拜的時間，送到 QA 的大宅院裡。等 QA 打開盒子被臭死，再寫公文把狗屎退回給工匠。工匠早就忘了三個禮拜前他在想什麼了！在書桌上就地正法，能將修補破車的時間成本與黃金，極致壓縮到【逼近於絕對的零 (drastically reduces cost and time)】！)
C. It ensures the application passes all penetration tests automatically. (書桌上的打字檢查器，怎麼可能防得住那群像鬼一樣跑來端倪你業務邏輯漏洞的滲透大刺客？維度差太多了)
D. It prevents insider threats from intentionally planting logic bombs in the source code. (如果內鬼存心要搞破壞，他絕對不會用 `strcpy` 這種一眼就被電擊棒發現的低能招數。他會寫出語法完全正確、但邏輯包藏禍心的炸彈。這種防呆機制防不了高智商內鬼)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是 SSDLC 中 **"Shift-Left (左移)"** 最核心的商業與財務價值主張 (Business Justification)。
    *   **Feedback Loop (回饋迴圈) 與上下文切換 (Context Switching) 成本：**
        *   **傳統模式 (慢回饋)：** 開發者寫完一段有很多 buffer overflow 的 C++ code。兩週後交給 QA。QA 跑弱掃發現漏洞，開 Ticket 派給開發者。此時開發者已經在寫另一個功能了 (Context switched)。他必須重新回想兩週前自己寫這段 Code 的邏輯，這會浪費巨大的人工成本 (Triage & Remediation cost)。
        *   **IDE Linting / IDE SAST (極速回饋)：** 在開發者 "剛打完字、思緒還停留在這功能上" 的當下，紅色的毛毛蟲波浪線就立刻出現警告他危險。他順手花 10 秒鐘改成安全的 `strncpy()`。解決了這個漏洞。
    *   這種極致左移大幅降低了漏洞流入下一個昂貴階段的機率，帶來了最高的 ROI (投資回報率)。

#### **6. A software vendor has discovered a zero-day vulnerability in their flagship product, which is already installed on thousands of customer servers globally. They have rapidly developed a patch and are about to release it. According to the standard Vulnerability Management lifecycle, what crucial communication step must accompany the release of this patch?**
**(一家打造了鎮國神器級別防毒大砲的大工坊，某天深夜。他們絕望地在自己引以為傲的大砲上，發現了一個【只要敵軍拿火把一照，整座大砲就會直接原地炸成碎片的『末日級絕對死亡零日大洞 (zero-day vulnerability)』！】而在外面的大千世界裡，已經有幾千個城邦的城牆上架著他們這款大砲了！大工坊的工匠嚇得屁滾尿流，連夜不睡覺焊出了一塊『補洞鐵板 (patch)』準備發射出去。請問！在正規的『世界漏洞大災難危機管理教範 (Vulnerability Management lifecycle)』裡。在大工坊派快馬把鐵板送出去的同一時刻，大工坊的宰相，【必須、絕對、不可躲避地】對著全天下吹響哪一個至關重要的大喇叭外交公文 (crucial communication step)？)**
A. An internal memo to the sales team to downplay the severity of the flaw. (如果對外說謊、叫業務員去跟客戶洗腦說這只是大砲掉漆的小問題。等明天客戶的城池因為這個洞被滅國，這家工坊會被告到祖宗十八代墳墓都被挖出來)
B. Publishing a Security Advisory (or Security Bulletin) detailing the nature of the vulnerability, its CVE identifier (if requested/assigned), and clear instructions for customers on how to apply the patch. (這就是化解公關危機與展現業界良心的唯一正道大公約：【『敲響天下第一大悲鐘，高掛《天下災難安民告示書 / 資安威脅大召回警報 (Security Advisory / Bulletin)》』】！這份白紙黑字的警報書必須沉痛且直白地宣告天下：【各位鄉親，我們的大砲漏水了！它在江湖上的追殺黑名單號碼叫做 CVE 幾號！如果駭客拿火把照，它會怎樣爆炸求饒 (nature of vulnerability)！最後，請大家立刻！馬上！按照老子底下附上的這三步安裝法，把鐵板給焊上去保命 (clear instructions how to apply)！】這是危機處理的最高鐵律！)
C. Sending a cease-and-desist letter to the security researcher who originally reported the flaw. (這是最下策、最臭名昭彰的流氓公關災難！去恐嚇那個發現漏洞並好心通報的好市民，只會讓這個市民憤怒地把核彈密碼公布在網路上，這叫提油救火！)
D. Only notifying the largest enterprise customers who pay for premium support. (隱瞞小老百姓小客戶，只偷偷告訴有付保護費的大財主，這會徹底摧毀整個帝國品牌的信譽，並導致大範圍的中小企業淪陷)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「發布安全公告 (Publishing a Security Advisory/Bulletin)」** 是軟體供應商在漏洞管理生命週期 (Vulnerability Management Lifecycle) 的修補與揭露階段，最核心的公共責任機制。
    *   **Coordinated Vulnerability Disclosure (CVD / 協同漏洞揭露)：** 當軟體原廠發現並修補好一個已存在的漏洞後。單單只把 Patch 丟到更新伺服器上是【不夠的】。很多客戶並不會打開自動更新。
    *   原廠必須發布一篇正式的 **Security Advisory**。這份文件是 IT 系統管理員的羅盤，它必須包含：
        *   **嚴重性 (CVSS Score)：** 讓客戶知道這要不要今晚加班修。
        *   **CVE ID：** 讓客戶的弱點掃描器能識別它。
        *   **影響範圍與修補指引：** 告訴客戶要升級到幾版才能免疫。
    *   隱瞞(A/D)或恐嚇白帽駭客(C)在現代資安實務中是絕對不可行的商業自殺行為。

#### **7. Your company uses a widely popular open-source Java library. The National Vulnerability Database (NVD) just published a Critical CVE (CVSS 9.8) for this library. The open-source maintainers have released a patched version (v2.1). However, the lead developer tells you that upgrading to v2.1 will completely break several core functions of your application, requiring at least three weeks to refactor the code. Production is currently vulnerable. What is the BEST immediate course of action for the security team?**
**(你的帝國大軍裡，用了一堆從外面進口的『爪哇神木箭頭 (open-source Java library)』。今天早上，朝廷的百曉生情報局突然掛出了血紅的末日懸賞令！宣稱這批神木箭頭裡藏著一碰就灰飛煙滅的【『CVSS 9.8 滅國級核彈大漏洞』】！幸好外面的黑市商人馬上推出了不會破掉的『無敵鑽石改版箭頭 (v2.1)』。但當你興沖沖地拿著鑽石箭頭去找你們家大工頭時，工頭面如死灰地癱軟在地。他哭喊著告訴你：『大將軍！如果我們現在強行把這些鑽石箭頭裝到我們的弓弩上，我們的弓弩會當場解體報廢！(upgrade will completely break several core functions)！我們得把整座兵工廠拆了重蓋，至少要花三個禮拜的工期 (three weeks to refactor)』！但敵軍現在就在城門外，隨時可能點燃這個核彈洞！請問，身為城防總大將，在這要命的三個禮拜空窗期裡，你【最正確、最保命的緊急續命神丹大手段】為何？)**
A. Take the application offline entirely until the code refactoring is finished in three weeks. (把整個國家所有賺錢的金庫跟業務大門全部關閉三個禮拜，國家會直接破產，大總管會先把你拿去祭旗砍了！這太極端毫無商業觀念)
B. Allow the application to run as-is and hope attackers don't discover the vulnerability while the team refactors. (這叫掩耳盜鈴、閉著眼睛等著被滅國的駝鳥末日死法！這種 9.8 級別的核彈洞，敵軍早就寫好掃描雷達滿天飛了，你絕對存活不過三天！)
C. Implement a compensating control, such as a highly specific Web Application Firewall (WAF) rule to block the exploit payload, while the development team works on the 3-week refactoring effort. (這就是那名震天下、在生死存亡之際幫你插管續命的：【『萬用醫療保命插管大緩兵之計：實施補償性控制 (Compensating Control)』】！這條神妙兵法教導我們：既然我現在因為各種爛機器原因無法把洞補起來，那老子就先在漏水的牆壁前面，【硬生生拿一塊『名為 WAF 網頁大盾牌的免洗厚木板』去擋在前面 (highly specific WAF rule)！】。只要這塊大鐵板能精準攔截並切斷外國刺客丟進來的核彈引線 (block the exploit payload)。皇城金庫就能繼續開門賺錢。而大工匠也能安心在城牆後面用這三個禮拜把鑽石箭頭給換好，這才是真正的兵法神調度！)
D. Force the developers to upgrade to v2.1 immediately and deploy the broken application to production, as security is more important than functionality. (為了一個安全洞，你強迫把一台開機就會閃退、無法結帳的爛車子丟給客戶。這這等於你親手炸毀了 CIA 的『可用性 (Availability)』，自刎死法，極不可取)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是風險回應 (Risk Response) 中最經典的 **「補償性控制 (Compensating Control)」** 或「虛擬修補 (Virtual Patching)」場景。
    *   **完美的理想 vs 殘酷的現實：** 資安教本都會說「發現 Critical 漏洞要立刻打 Patch」。但在大型企業體系中，框架升級 (如 Java Spring, log4j) 非常可能導致巨大的 Breaking Changes，程式碼大當機。
    *   **Risk Mitigation 緩解空窗期：** 我們不能關閉賺錢的系統 (業務連續性)，也不能坐以待斃。這時就要啟動 "Virtual Patch (虛擬修補)"。資安團隊立刻去網路閘道層 (IPS/WAF) 寫一條 Regular Expression (正規表示式) 規則。當外網流量進來時，如果封包裡含有這支 CVE 專屬的攻擊特徵碼 (Payload Patterns)，WAF 會直接在城門外把這包流量 Drop 掉。這樣後端即使有一個弱點 Java Library 裸奔，駭客也摸不到它，替開發團隊贏得 3 週的重構時間。
