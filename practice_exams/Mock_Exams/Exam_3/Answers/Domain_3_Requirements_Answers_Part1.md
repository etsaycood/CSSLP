# 第三套全真模擬試題 (Exam 3) - 答案與詳解本
## 領域 3：安全的軟體需求 (Secure Software Requirements) (18題) - Part 1 (Q1-Q9)

---

#### **1. A business analyst is gathering requirements for a new cloud-based payroll system. The HR director states, "The system must process payroll for 10,000 employees within a 2-hour window every Friday." The Chief Security Officer (CSO) immediately interjects, "However, the system must definitively reject any user attempt to download the master salary listing if they are not physically connected to the company's internal VPN." What specific types of requirements have the HR director and the CSO just defined, respectively?**
**(一名商業分析師正拿著筆記本，替一套全新雲端發薪水系統收集『建城需求藍圖 (requirements)』。人力資源部總監大聲說出他的願望：「這套系統【必須】能夠在每個禮拜五的下午，在短短兩個小時內，極速算完且發出全公司一萬名員工的薪水！」。話還沒說完，旁邊坐著的資訊安全長 (CSO) 立刻拍桌插嘴補充了一條死命令：「慢著！但是，【只要】這系統偵測到有人企圖下載那份總薪資名冊大表，若系統發現這傢伙目前的網路連線【不是】實體掛載在我們公司內部的安全 VPN 通道上時，系統就【必須絕對無情地拒絕並砍斷】他的下載請求！」。請問，這位 HR 總監跟這位 CSO，他們兩位剛剛各自親口定義出來的，在學術上分別屬於哪兩種截然不同的『系統需求分類』？)**
A. Both are Functional Requirements. (兩個人講的都是功能性需求)
B. HR Director: Functional Requirement; CSO: Functional Security Requirement. (這就是標準答案：HR 總監講的是系統『該做什麼』的【功能性需求 (Functional Requirement)】；而 CSO 講的是『系統該如何防範與規範某個資安動作』的【功能性安全需求 (Functional Security Requirement)】！)
C. HR Director: Non-Functional Requirement; CSO: Misuse Case. (HR 總監講的是非功能需求，CSO 講的是誤用案例如)
D. HR Director: Performance Requirement (Non-Functional); CSO: Security Requirement / Access Control Requirement. (HR 總監講的是效能非功能需求... 注意：處理薪水本身是一個功能動作)

*   **正確答案 / Correct Answer：D**
*   **[解析邏輯]** *(更正：根據 CISSP/CSSLP 嚴格定義，效能通常歸類於非功能，但處理薪水是功能。然而看仔細 D 的描述)*
    *   **為何 D 是最佳選擇：** 我們來仔細拆解這兩句話：
        1.  **HR 總監：「在 2 小時內處理 1 萬人薪水」**。這是一個明確的 **「效能指標 (Performance)」**要求。在軟體工程中，效能 (速度、吞吐量、反應時間)、可靠性、可用性等，被嚴格歸類為 **「非功能性需求 (Non-Functional Requirements, NFRs)」**。它規範了系統「運作得有多好/多快 (How well it operates)」。
        2.  **CSO：「如果不在 VPN 上，必須拒絕下載」**。這明確定義了系統在面臨存取控制時「必須執行的查驗動作 (What the system MUST DO for security)」。這被歸類為 **「安全需求 (Security Requirement)」** (或更精確地說，是存取控制需求 Access Control Requirement)。
    *   注意：雖然 B 選項看似合理，但把「2小時內處理完」當作純粹的 Functional 功能性需求是不夠精準的，因為它帶有強烈的「效能指標 (Performance)」，這屬於經典的 NFR (非功能性)。

#### **2. During a massive brainstorming session for a new self-driving car's software, the engineering team creates detailed diagrams mapping out how a hacker might attempt to spoof GPS signals to force the car to drive off a cliff, or how someone might inject malicious code via the Bluetooth infotainment system to disable the brakes. They then systematically document these attack vectors to ensure defensive mechanisms are built to counter them. What specific requirements engineering technique is the team actively employing?**
**(在一場為『全新 AI 自動駕駛汽車大腦軟體』所舉辦的白板激盪誓師大會上。這群頂尖工程師不是在畫車子怎麼開，他們反而在黑板上畫滿了各種猶如恐怖攻擊般的『滅世大陰謀設計圖 (detailed diagrams)』！例如：他們巨細靡遺地推演並畫出『一個瘋狂駭客，可能會如何施展黑魔法去偽造天上的 GPS 衛星訊號 (spoof GPS)，進而欺騙車子自己開下懸崖自殺』；或者『某個路人甲，可能會如何透過車上用來聽音樂的藍牙音響系統 (Bluetooth infotainment system)，偷偷像打針一樣注射進一段劇毒木馬，然後瞬間把車子的煞車系統給徹底癱瘓咬死 (disable the brakes)』。他們將這些恐怖的攻擊路徑 (attack vectors) 像寫劇本一樣一條條記錄下來，目的是為了逼迫自己設計出能擋下這些攻擊的裝甲防護罩。請問這群工程師目前正在狂熱演練的，是哪一套反面教材的『需求工程採集神技』？)**
A. Normal Use Case Modeling (在那邊畫一般阿公阿嬤怎麼正常用車的正常使用案例)
B. Misuse Case / Abuse Case Modeling (這就是大名鼎鼎、反其道而行、把自己當作惡魔來寫劇本的【誤用案例 / 濫用案例大推演 (Misuse Case / Abuse Case Modeling)】！)
C. Policy Elicitation (這是在抄寫公司法規的政策引導)
D. Continuous Integration (把程式碼每天揉在一起的持續整合)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「誤用案例 (Misuse Case)」** 或 **「濫用案例 (Abuse Case)」** 是安全需求工程 (Secure Requirements Engineering) 中極為強大的武器，也是威脅建模 (Threat Modeling) 的重要輸入來源。
    *   傳統的 **Use Case (使用案例)** 只會寫太平盛世的劇本 (例如："駕駛按下啟動鈕，車子發動")。這無法防禦駭客。
    *   而 **Misuse Case** 強迫工程師把主角換成「惡意攻擊者 (Attacker)」。去編寫「駭客目標是什麼？他會採取什麼步驟繞過系統？」的暗黑劇本 (例如：駭客透過藍牙發送緩衝區溢位攻擊煞車系統)。透過畫出這些「反向的 UML 劇本圖」，開發團隊就能「以駭客之矛、攻防禦之盾」，精準地生出對應的「安全防禦需求 (Security Requirements)」（例如：煞車控制晶片與藍牙資訊娛樂晶片必須實體隔離）。

#### **3. A development team is preparing to build a new B2B (Business-to-Business) payment API. To identify exactly what mandatory security controls must be engineered into the API, the team methodically analyzes the Data Protection Act, the industry-specific Payment Card Industry Data Security Standard (PCI-DSS), and the specific Service Level Agreements (SLAs) historically signed with their largest enterprise clients. Which critical activity within the Requirements phase is the team performing?**
**(一支準備要打造一條跨國『金控對金控 (B2B) 之終極金流支付 API 大水管』的精銳工程兵團。在開挖城河之前，他們為了搞清楚這條水管到底裡裡外外必須安裝哪些【絕對不能妥協、強制性 (mandatory) 的防護裝甲與機關 (security controls)】。這支團隊正襟危坐，把桌上堆滿了文件，開始如同老學究般逐字逐句地去瘋狂研讀剖析幾本生死天書：包括國家頒布的《個人資料保護法大憲章 (Data Protection Act)》、金融界聞之色變的《PCI-DSS 銀行卡產業資安死鐵律》、以及他們過去跟那些財閥等級的大客戶所簽下的『若斷線機房當機就要賠幾億美金之《服務等級生死條約 (SLAs)》』！請問這群工程師在一張圖紙都還沒畫出來的「需求大搜集階段」，他們現在正在苦讀發功的這項核心神聖儀式叫做什麼？)**
A. Penetration Testing (拿大砲轟自己城門的滲透測試)
B. Code Obfuscation Analysis (把寫好的文章弄成亂碼的混淆分析)
C. Security Policy and Compliance Analysis (Elicitation) (這就是一切防禦圖紙的最高指源、從天條法規中榨出建城規格的【安全政策與法規合規性大解析與需求大蒐集引出法 (Security Policy and Compliance Analysis / Elicitation)】！)
D. Source Code Review (帶著老花眼鏡看每一行程式碼的代碼審查)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「法規與合規性分析 (Compliance Analysis)」** 或稱為 **「政策引導/引出 (Policy Elicitation)」**。
    *   安全需求 (Security Requirements) 不是工程師自己拍腦袋憑空發明出來的。它的最大宗來源就是 **外部強加的法規 (Regulatory/Compliance)** 和 **客戶合約 (SLAs, Contracts)**。
    *   在開發金融支付 API 時，如果你不先去翻閱 PCI-DSS 第 6.5 條 (防範十大漏洞) 或第 4 條 (傳輸加密)，你就直接開始寫 Code。等你寫完，稽核員來查發現你沒打到標，整包軟體就會被報廢。所以在需求階段 (Requirements Phase) 去「研讀外部政策並把它翻譯、提煉 (Elicit) 成工程師看得懂的軟體安控需求清單」，這是最頂層也是最重要的一步。

#### **4. A project manager documents the following requirement for a new healthcare application: "The application shall ensure the Confidentiality of patient data." The Lead Security Architect immediately rejects this requirement as fundamentally broken and sends it back to the business analyst for a complete rewrite. According to the core principles of writing effective security requirements, what is the primary, fatal flaw in this stated requirement?**
**(一位平庸的專案大掌櫃，在一本攸關百萬人生死的全新醫療照護系統的規格大誥上，自信滿滿地寫下了一條他自以為很帥氣的『安全需求神聖教令』：「本應用程式【必須絕對確保】病患資料的【機密性 (Confidentiality)】！」。沒想到，這份大誥剛端上桌，那位臉上帶著刀疤的首席資安大護法看了一眼，直接把這張紙揉成一團砸在掌櫃的臉上，痛罵這是一張廢紙，退回要求全面重寫 (rejects as fundamentally broken)！若以那本『如何撰寫神聖完美安全需求』的兵法準則來看，這句聽起來很冠冕堂皇的要求，到底犯下了哪一條最無可救藥、最致命的低級死穴破綻？)**
A. It is too specific and restricts the developer's creativity. (寫得太囉唆太詳細，剝奪了工程師寫扣的自由創意跟靈魂)
B. It is overly technical and uses confusing jargon. (用了太多連神仙都看不懂的艱澀駭客外星語跟黑話技術詞彙)
C. It completely lacks testability, measurable criteria, and specificity (It is vague). (這就是空話！它徹徹底底、完完全全地喪失了一條規格最該擁有的【可被驗證測試性 (testability)、可被量化測量的標準 (measurable criteria)，以及具體細節 (specificity)】！這是一句標準政客講的幹話與空話 (Vague)！)
D. It focuses on Availability instead of Confidentiality. (這傢伙搞錯了，他應該寫可用性而不是機密性)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是軟體工程中撰寫需求 (Requirements Engineering) 最忌諱的錯誤：**「模糊不清 (Vagueness) 與 無法測試 (Untestable)」**。
    *   一個「有效」的軟體需求，必須符合 SMART 原則 (特別是 Specific 具體的、Measurable 可測量的)。
    *   當你寫「必須確保機密性」時，這是宏大空泛的最終目標 (Goal)，但它**絕對不是**一條可執行的軟體需求 (Requirement)。因為當 QA (品管測試員) 拿到這句話時，他完全不知道該怎麼按滑鼠去「測試」這句話有沒有達成。
    *   **正確的寫法 (具體且可測試)：** 「系統必須使用 AES-256 位元演算法對資料庫中的病患身分證字號欄位進行靜態加密 (Encryption at Rest)，並且傳輸時必須強制僅接受 TLS 1.2 以上版本連線。」這種寫法，不僅工程師知道怎麼寫，QA 也能寫出測試腳本去拿掃描器驗證它。C 精準指出了這個致命傷。

#### **5. A new digital banking application allows users to transfer funds. During the requirements definition phase, the security team mandates a specific scenario: "When the system detects a user attempting to transfer an amount exceeding their established daily risk profile, or if the transfer destination is a known high-risk international blacklist IP, the system MUST automatically freeze the transaction, trigger an alert to the fraud department, and prompt the user for biometric step-up authentication." What specific artifact is the team creating to document this critical anti-fraud logic?**
**(在一座準備開業的全新純網銀數位錢莊裡，有一套能讓客人把大筆鈔票匯來匯去的金流大水管。在繪製城防地圖的『需求定義破土大會 (requirements definition phase)』上，資安神宮衛隊強硬地把一條血淋淋的劇本給釘死在規格大門上：「聽好！當這套水管的『鷹眼法陣』偵測到，有某個傢伙今天居然企圖要匯出一筆【遠遠超過他平時那窮酸生活水準跟風險扣打的天價大樂透鉅款 (exceeding daily risk profile)】，又或者！這筆錢飛往的目的地，居然是落在國家通緝那張『高風險國際黑名單上的惡棍 IP (high-risk international blacklist IP)』時！！這套系統【絕對必須 (MUST)】發動連鎖死機反應：『第一，瞬間將這筆交易冰封咬死 (freeze transaction)！第二，對天鳴槍、直接把警報刺進防詐騙大營的耳膜裡 (trigger an alert)！第三，系統畫面上必須馬上彈出一個死神鎖頭，逼迫這名匯款人當場把臉皮或指紋貼在鏡頭上，發動【強制生物特徵升級拔階大認證 (biometric step-up authentication)】來證明他真的是本人而不是被盜用！』」。請問，這群衛隊為了將這段極度驚心動魄的『反詐欺連環機關陷阱邏輯』給白紙黑字寫進史冊裡，他們所創造出來的這份神聖規格文件產物 (artifact)，叫什麼名字？)**
A. A Data Flow Diagram (DFD) (畫著資料怎麼像水一樣流來流去的管線黑白幾何圖 DF)
B. A Software Bill of Materials (SBOM) (那張為了怕你用到過期中毒開源軟體的祖宗十八代元件成份表)
C. A Security Misuse Case or Security Use Case (擁有如此鉅細靡遺、描述系統面對各種邪惡狀況時該如何反擊的劇本，這產物就是大名鼎鼎的【安全使用案例 / 或者防範邪惡的資安濫用大劇本 (Security Misuse Case / Security Use Case)】！)
D. A Static Application Security Testing (SAST) rule (去寫給機密代碼掃描機看的死板掃毒條件語法規則)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「安全使用案例 (Security Use Case)」**。
    *   傳統的 Use Case 描述：「使用者登入 -> 輸入帳號密碼 -> 成功進入首頁」。這叫 Happy Path。
    *   **Security Use Case** 特門用來描述系統在遇到**特定條件、高風險情境、或遭受攻擊時**的「安全反應機制」。題目中給出了一個非常完整的劇本條件（Trigger: 匯款超額 OR 目的地在黑名單），以及系統的一連串強制作為（Action: 凍結、發警報、要求 Step-up MFA）。這種「如果發生危險的 A，系統就要執行防禦的 B」的劇本式紀錄，正是 Security Use Case 最經典的展現形式。它是將抽象的 "防詐欺政策" 具體化為 "開發者看得懂的防禦流程邏輯"。

#### **6. An enterprise is migrating its physical data center to AWS. The legal department informs the engineering team that due to the specific European privacy laws governing their customers, the software application must absolutely guarantee that no database instances physically reside outside the borders of the European Union, and that any cloud provider administrators attempting to access the underlying storage servers must be flagged and blocked. Which specific category of security requirements is the legal team unilaterally imposing on the software architecture?**
**(一個龐大的帝國正進行史無前例的大搬家，他們要把自家那座古老發霉的實體大機房，連根拔起全部移民到天上的 AWS 雲端大廠上。這時，帝國裡的法務長老拿著一本厚達千頁的法典衝了出來，對著那些樂不可支的雲端總監工程師們發出死亡警告：『聽好了你們這群雲端狂熱分子！因為我們有在賺那些被歐盟《隱私大寶典法規》層層保護的尊貴歐洲老爺們的錢。所以，你們這套搬上雲端的系統架構，【必須用命來給老子擔保】：就算雲端無國界，但你們那些裝滿歐洲人個資的大水缸資料庫 (database instances)，【在物理實體座標上，絕對、死也不准跌出歐洲聯盟版圖的國界線半步 (no database physically reside outside EU)】！！還有，只要是那家 AWS 雲端大廠自己內部的雲端大總管 (Cloud Provider Admins)，敢偷偷拿著萬能鑰匙去硬碟底層偷看我們家的資料，系統就必須立刻發紅色死光把他的手給砍斷並拉響全球警報 (flagged and blocked)！』。請問，這群法務長老強硬架在工程師脖子上的這道【鎖死資料物理地理投胎地點】跟限制祖宗權力的至高安控需求。在學理上被嚴格歸類於哪一種大傘類別的安全需求？)**
A. Functional Requirements (會算加減乘除的功能性需求)
B. Data Retention Requirements (那只是規定一份文件要放在防潮箱裡鎖幾年才可以拿出來燒掉的資料留存需求)
C. Regulatory and Data Sovereignty (Data Residency) Compliance Requirements (這就是讓無數跨國大企業低頭吐血、威力凌駕於國境線之上的【法規遵從與數據主權/神聖資料落地駐留大結界合規需求 (Regulatory and Data Sovereignty / Data Residency Compliance Requirements)】！)
D. Performance (Non-Functional) Requirements (系統連線有多快多順的效能非功能需求)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「資料主權 (Data Sovereignty)」** 與 **「資料落地/駐留 (Data Residency)」** 是現今跨國雲端架構中最不可跨越的紅線 (特別是因為歐盟 GDPR 以及各國的地緣政治考量)。
    *   雲端的美妙之處在於資源池化、全球調度。但法規的殘酷在於：德國人的個資，它的硬碟實體位置「就只能放在位於德國境內的法蘭克福機房」。如果你為了便宜或者做異地備援 (HA)，把這顆資料庫備份倒去美國維吉尼亞州的 AWS 機房，你就踩了法規紅線，將面臨全球營業額 4% 的毀滅性天價罰款。法務部門強加的這種「限制資料在哪個國家物理磁區上」的需求，就是最典型的 Data Sovereignty/Residency 合規需求。加上防止雲端供應商原廠看資料 (這也是 GDPR 等法規要求的防範第三方存取)，所以 C 完全契合。

#### **7. A systems engineer is categorizing various data types that a proposed human resources application will collect and process. The data dictionary includes items like: Employee Home Address, Personal Phone Number, Social Security Number, and Medical History. The engineer mathematically maps each of these specific data fields to a "High" confidentiality requirement because standard definitions mandate extreme protection for exactly this type of sensitive identifying information. What universally recognized acronym represents this specific category of highly protected data?**
**(一名老謀深算的系統算死草工程師，正拿著放大鏡，在幫一套即將開工的『皇家內務府人力資源大系統 (HR application)』所收集來的各種奇珍異寶名冊資料，進行殘酷的『命運階級大分類 (categorizing data types)』。這本厚厚的資料血統血統字典庫 (data dictionary) 上，包含了各種要命的禁忌情報：例如『每位宮女太監的家中老宅具體座標地址 (Home Address)』、『私下聯絡的手機黑電話密碼 (Personal Phone Number)』、『連通國庫與生死簿的那串絕對死機密：身分證字號與社會安全碼 (Social Security Number)』、甚至還有『這個人以前得過什麼見不得人的花柳大病之醫療黑歷史 (Medical History)』。這位算死草工程師眼睛都不眨一下，直接將這些特定欄位的卡片，無比精準且鐵面無私地全部對應、扔進了一個刻著『極限最高機密 (High confidentiality requirement)』的血紅大火爐分類裡。因為世間所有法規標準都下了死定論：唯獨對於這類【會直接跟這條人命的肉身身分死死綁在一起的極端敏感識別資訊】，必須施加毀天滅地級別的終極武裝保護。請問在江湖上，究竟是哪兩個名震天下且能引來各國法規核查殺機的萬用縮寫詞，專門用來統稱這群『碰了非死即殘的高度受保護祖宗身家大數據』？)**
A. DRM (Digital Rights Management) (防人家偷拷貝電影 MP3 的數位版權大鎖 DRM)
B. PII (Personally Identifiable Information) / PHI (Protected Health Information) (這就是那一碰就爆炸、各國隱私法規死死盯著的超級核武彈頭：【『能直指你老家肉身是誰』的個人可識別身分大機密 (Personally Identifiable Information, PII)】與【病歷隱私『受保護健康資訊』 (Protected Health Information, PHI)】！)
C. SBOM (Software Bill of Materials) (列出軟體用了哪些開源大肥肉的軟體物料祖宗清單 SBOM)
D. API (Application Programming Interface) (這只是電腦跟電腦之間講偷偷摸摸黑話的連線橋接水管 API)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **PII (個人身分識別資訊)** 和 **PHI (受保護健康資訊)**。
    *   在資料分類與保護需求中，這兩個詞彙是最核心的標的物。
        *   **PII (US NIST 定義或 GDPR 類似概念)：** 任何可以追蹤或關聯到「特定自然人個體」的資訊。例如：姓名、身分證字號 (SSN)、個人電話、私人家中地址、生物特徵 (指紋)。這類資料一旦外洩會導致身分盜用 (Identity Theft)。
        *   **PHI (HPPA 法規特有)：** 任何關於個人過去、現在或未來身體或心理健康狀況，並能驗明其身分的資訊 (如就診紀錄)。
    *   這名工程師將 SSN、電話等歸類為最高機密，正是因為它們在業界的共同縮寫代稱就是 PII。系統只要碰到 PII，在需求階段就必須自動觸發 "靜態加密 (Encryption at Rest)" 和 "嚴格遮罩 (Masking)" 等高等防護需求。

#### **8. In the context of establishing foundational security requirements, an organization decides to implement a strict "Data Classification Policy." They define three tiers: Public, Internal, and Confidential. What is the fundamental, primary purpose of performing this categorization exercise before designing the software's access controls and encryption mechanisms?**
**(在為新系統打下『資安建城防護需求深淵地基』的偉大時刻。一家大組織的長老會，傲然拍板決議：全境強制施行一套界線分明、猶如種姓制度般殘酷的『資料大階級分類獨裁法案 (Data Classification Policy)』！他們拿著油漆刷，把組織內如海量般的所有資料文件，殘忍地刷上了三種致命的階層階級顏色：「路人皆可看的【公開賤民級 (Public)】」、「只有自己人能看的【內部平民級 (Internal)】」、以及「看一眼就會被殺頭的【極限最高機密皇族級 (Confidential)】」！請問，這群長老之所以堅持【必須要在大家開始動手去設計金庫大門鎖頭有多厚 (access controls)、以及開始買幾十億的超級密碼鎖保險箱引擎 (encryption mechanisms) 之前！】就要先大費周章、雞飛狗跳地幫這幾千萬份破資料大搞身家背景大分類。其背後最根本、最純粹、最攸關帝國生存戰略意義的核心終極圖謀為何？)**
A. To guarantee that all data is encrypted using military-grade AES-256. (為了方便瞎眼下令，讓這帝國連路邊的一張公廁衛生紙宣傳圖，也要花一萬美金用軍用級 AES-256 去把它層層加密鎖死)
B. To ensure that expensive, heavy security controls are proportionately applied ONLY to the data that actually warrants that level of protection, rather than blindly wasting money locking down worthless public data (applying appropriate levels of protection based on risk/value). (這就是商人的精明極限！為了確保那些『造價天價、且沉重如大山的重兵防護大盾與超級昂貴金庫鎖 (expensive, heavy security controls)』，能像雷射導引一樣，【極度精準、按比例恰如其分地 (proportionately) 『只』投資砸在那些真正值錢、值得用命換的皇族機密資料身上】！而不是像個大白癡一樣，把成千上萬的國庫預算，無腦盲目地揮霍在去保護那些『本來就要給路人看的路邊公佈欄垃圾公開資料 (worthless public data)』！這便是『基於風險與身價，下放最適當防禦保護 (applying appropriate levels of protection based on risk/value)』的神聖價值經濟學！)
C. To prevent the application from crashing. (怕太亂了，會讓那台舊電腦當機崩潰)
D. To satisfy the requirement for a Web Application Firewall (WAF). (這只是為了滿足去買一台放在門口擋子彈的破防火牆 WAF)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是資安治理 (Security Governance) 也是 CSSLP 的核心靈魂：**「基於風險的適度保護 (Risk-based / Proportionate Protection)」**。
    *   安全防護網 (如硬體加密機 HSM、24小時保鑣監控) 是**極度昂貴且會拖慢系統效能的**。
    *   許多初學者會選 A (把所有東西都用最強密碼鎖起來)。但這是災難！如果公司把放在首頁給路人下載的「免費產品型錄 PDF (公用階級 Public)」也花大錢去走加密引擎，那只會白白把 CPU 算力燒光、把預算花光，而且毫無意義 (因為本來就是公開的)。
    *   **資料分類 (Data Classification)** 的神聖目的在於「貼標籤以分配預算」。標誌為 "Confidential" 的資料庫，我們砸幾百萬去建置庫內加密和遮罩；標誌為 "Public" 的，我們用最便宜的方式存放。把錢花在刀口上，這才是企業級資安的真理。

#### **9. A business analyst uses a technique where they physically sit next to the customer service representatives taking phone calls, observing over their shoulder exactly how they currently navigate the legacy green-screen terminal system to reset a user's password. The analyst notices many reps write passwords on sticky notes because the current system's timeout is too short, revealing a massive security flaw in the workflow. The analyst then uses these real-world observations to draft better, more secure workflow requirements for the new system. What requirement elicitation technique is the analyst using?**
**(一名如同鬼魅影武者般的商業細節大分析師。他使出了一招『無聲潛入大法』：他直接跑去客服部門，搬了張板凳，【活生生地肉身挨在那些正忙著接電話挨罵的客服大媽旁邊坐下 (physically sit next to)】！他就這樣睜大如鷹般的雙眼，越過大媽的肩膀 (observing over their shoulder)，死死盯著大媽的手指跟螢幕。看著這位大媽到底是怎麼在現在這套老舊破爛、還發著幽幽綠光的史前恐龍電腦系統畫面上，兵荒馬亂地去點擊步驟，幫電話那頭忘了密碼的糊塗客戶執行『大重置密碼 (reset a password)』！在這種赤裸裸的貼身監視中，分析師猛然捕捉到一幕令人崩潰的慘劇：他發現好幾個大媽，因為這套爛系統的『安全防呆閒置登出時間 (timeout)』設定得短到變態。大媽們被逼急了，居然紛紛拿出黃色便利貼，把客戶的機密重置密碼大咧咧地抄下來黏在螢幕邊框上！這不經意間暴露出這個作業流程裡一個【足以讓公司惹上大官司的天大資安隱患破洞 (massive security flaw)】！這位分析師如獲至寶，趕緊把這些血淋淋的『前線現實慘況』記錄下來，作為他在設計那套『未來全新救世主大系統』時，去擬定更防呆、更安全的神聖防堵工作流需求底稿大補帖。請問這位猶如躲在背後偷窺的分析師，他所施展的這套『在血肉前線扒開真實樣貌的大規模需求引導與採擷奇門神技』，名號為何？)**
A. JAD (Joint Application Design) Sessions (把大官們全關進一間高級會議室裡吵架發想的 JAD 聯合設計大會)
B. Questionnaires and Surveys (只是發問卷傳單叫人打勾勾的無聊調查法)
C. Observation / Ethnographic Study (Shoulder Surfing in a safe context) (這就是身歷其境、化身透明人去觀察生態系物種最原始面貌的【貼身肉搏大觀察法 (Observation) / 人類學民族誌田野大調查 (Ethnographic Study)】！也就是在正當無害的安全情境下，施展了那原本駭客最愛用的背後靈偷窺大絕學：『越肩偷窺 (Shoulder Surfing)』之正向應用版！)
D. Reverse Engineering (把整台電腦拆開來研究裡面有幾根電線的逆向工程破解法)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「觀察法 (Observation)」** 或 **「民族誌研究 (Ethnographic Study)」**。
    *   在安全需求工程 (Requirements Elicitation) 中，獲取需求的方法有很多種。如果你只發「問卷 (B)」，客服大媽絕對不會在問卷上承認自己把密碼寫在便利貼上。如果你開「高層會議 (A)」，長官只會跟你說「我們的流程很安全完美」。
    *   要找出系統「真正隱藏的安全漏洞工作流與人性痛點」，最神準的技巧就是 **直接坐到使用者旁邊看他們怎麼工作 (Observation)**。這術語上有時戲稱為合法的 "Shoulder Surfing (越肩看螢幕)"。分析師發現系統安全設定 (Timeout 太短) 反而逼得使用者做出極度不安全的人性反應 (寫便利貼)。從這真實的痛點中，分析師就能寫出更優秀的安全需求："新系統的防呆機制必須兼顧人性，或許引導使用自動發信機制而不是讓客服人員肉眼看到密碼"。
