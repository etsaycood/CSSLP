# 第四套全真模擬試題 (Exam 4) - 答案與詳解本
## 領域 8：安全的軟體供應鏈 (Secure Software Supply Chain) (12題) - Part 1 (Q1-Q4)

---

#### **1. A software development company wants to improve the transparency and security of its supply chain. They decide to generate a machine-readable inventory detailing all the open-source libraries, third-party frameworks, and proprietary components used to build their final software product. This inventory will be shared with their enterprise customers to help them manage their own risk. What is this comprehensive inventory document called?**
**(一家專門打造『無敵機關木馬』的神作坊。為了讓買家安心，作坊老闆決定在交貨時，附上一張【『木馬五臟六腑全透視清單 (inventory detailing all open-source libraries, frameworks, proprietary components)』】。這張清單上密密麻麻地寫著：這隻木馬的左大腿木頭是從王老吉木材行買的、眼睛的寶石是海外進口的開源貨、肚子裡的齒輪是自家祖傳秘方打的。這張清單不是用毛筆寫的，而是用一種【『奇妙的機關文 (machine-readable)』】刻在鐵板上。這樣一來，買家只要把這塊鐵板插進自家的『驗毒羅盤』裡。萬一哪天江湖上傳出「王老吉木材行的木頭會自燃」，買家立刻就能知道自己買的這隻木馬到底會不會燒起來 (help customers manage their risk)！請問，這份能把軟體祖宗十八代成分全部起底的終極血統證明書，學名為何？)**
A. A Value Stream Map (VSM) (價值流圖是畫工匠們怎麼把一塊爛木頭變成值錢木馬的「生產流程圖」，它是用來看哪裡在摸魚浪費時間的工具，不是用來記錄木馬肚子裡裝了什麼料的成分表)
B. A Software Bill of Materials (SBOM) (這就是名震四海、美國總統甚至親自下達行政命令 (EO 14028) 強制要求的：【『軟體成分大透視：軟體物料清單 (Software Bill of Materials / SBOM)！』】。你可以把它想像成超市裡每一包餅乾背後的那張【成分營養標示表】！在現代軟體開發中，一個 App 裡面有 80% 的程式碼是從 GitHub 或是 npm 抄來的 (開源套件)。如果你不把這些借來的零件清單造冊，當 Log4j 這種核彈級漏洞爆發時，你根本不知道自家系統到底有沒有用到 Log4j！SBOM 就是一份標準化格式 (如 SPDX 或 CycloneDX) 的 XML/JSON 檔案。它精準記錄了這個軟體用了哪些套件、什麼版本、作者是誰。它讓供應鏈變得透明，是現代軟體供應鏈安全 (Supply Chain Security) 的最底層基石！)
C. A Service Level Agreement (SLA) (服務級別合約是承諾木馬如果壞了，作坊保證在兩天內派人來修。這是一張法律承諾書，不是木材跟齒輪的成分清單)
D. A Vendor Risk Assessment Questionnaire (供應商風險評估問卷是你去問木材行老闆有沒有按時洗澡洗手。這是在評估「供應商這個人」安不安全，而不是這隻「木馬本身」詳細包含了哪些零件)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「軟體物料清單 (Software Bill of Materials, SBOM)」** 是記錄軟體建置所需之所有元件 (Components)、函式庫 (Libraries) 與依賴項目 (Dependencies) 的正式記錄。
    *   **推動背景：** 隨著 SolarWinds 和 Log4j (Log4Shell) 供應鏈攻擊事件的爆發，軟體透明度 (Software Transparency) 成為顯學。美國政府於 2021 年發布行政命令，要求販售軟體給聯邦政府的供應商必須提供 SBOM。
    *   **格式與作用：** SBOM 通常使用 SPDX (Software Package Data Exchange) 或 CycloneDX 格式 (機器可讀)。當新的 CVE (漏洞) 發布時，組織可以將 CVE 資料庫與自家所有應用程式的 SBOM 進行自動比對，在幾秒鐘內盤點出哪些系統需要緊急修補，實現極速的風險識別。

#### **2. An attacker decides that hacking directly into a highly secured bank is too difficult. Instead, the attacker targets a small, less-secure company that provides a specialized charting library used by the bank's mobile app. The attacker compromises the charting library's code repository and injects a backdoor. When the bank updates the library in its next release, the backdoor is deployed to all the bank's customers. What specific class of attack does this scenario describe?**
**(一名窮凶極惡的江洋大盜，盯上了天下第一大錢莊 (highly secured bank) 的金庫。但錢莊牆高百丈，大盜連根狗毛都摸不進去 (too difficult)。於是，大盜靈機一動，他查出錢莊老闆的手機裡，裝了一個用來畫算盤圖的小軟體，而這個軟體是由城外一家只有兩個人的破窯洞工坊 (small, less-secure company) 提供的！大盜半夜潛入窯洞，把畫算盤圖的墨水裡【偷偷摻入了劇毒 (injects a backdoor in code repository)】！隔天，錢莊老闆派人去窯洞拿最新的畫圖軟體更新 (bank updates the library)。結果，這帶著劇毒的軟體，就這樣被錢莊『自己人』以最高規格的護衛，光明正大地請進了天下第一大錢莊，並且發給了所有客人 (deployed to all customers)！請問，大盜這種「打不下大山頭，就去上游小溪下毒」的陰險滅門戰術，在兵法上被稱為什麼？)**
A. Cross-Site Scripting (XSS) Attack (XSS 是在大街上的告示牌上塗抹毒藥，讓路過看的客人中毒。這跟潛入窯洞工廠，在上游生產線下毒的戰略層次完全不同)
B. Phishing Attack (釣魚攻擊是假扮成錢莊老闆寫信騙客人的密碼。這題的毒藥是實打實地藏在真正的手機軟體裡，而且是經過官方更新通道發布的，這完全不是釣魚)
C. Software Supply Chain Attack (這就是將整個軟體工業推入恐懼深淵的千古絕殺：【『上游水源投毒法：軟體供應鏈攻擊 (Software Supply Chain Attack)！』】。駭客的邏輯很簡單：既然大銀行 (Target) 的資安防禦堅不可摧，那我就去尋找大銀行依賴的那個「最弱的一環 (Weakest Link)」。現代軟體都是由無數個第三方開源套件、外包商程式碼拼裝起來的。只要駭客能攻破其中任何一個只靠志工維護的冷門套件庫 (例如透過破解開發者的 NPM 密碼)，植入後門。然後，駭客什麼都不用做，大銀行的 CI/CD 自動化建置流水線，就會【主動、熱情地】把這個有毒的套件下載回來，打包進自己的銀行 App 裡，甚至還幫它簽上合法的數位簽章發布給百萬用戶！SolarWinds 事件、Kaseya 勒索軟體事件，全都是這種防不勝防的供應鏈屠殺！)
D. Denial of Service (DoS) Attack (阻斷服務是用大石頭把錢莊的門堵死，不讓客人進去。這題的大盜是要偷進去放後門，而不是讓這錢莊停止營業)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是 **「軟體供應鏈攻擊 (Software Supply Chain Attack)」** 最典範的攻擊情境。
    *   **攻擊特徵 (Island Hopping / 跳島戰術)：** 攻擊者不直接攻擊最終目標 (因為防禦太強)，而是攻擊目標的第三方供應商、合作夥伴、或是其使用的開源元件。
    *   **破壞的信任鏈 (Chain of Trust)：** 這種攻擊可怕的地方在於，惡意程式碼是透過**合法且受信任的管道** (例如原本就存在於 `package.json` 中的依賴更新、或是合法的 Windows Update 機制) 進入目標系統。因此，傳統的防火牆或防毒軟體通常會將其視為「合法的軟體更新」而放行。
    *   **防禦難度：** 由於企業無法直接控制第三方供應商的內部安全，因此必須依賴 SBOM、SCA 工具、供應商風險評估 (SCRM) 與零信任架構來緩解此類風險。

#### **3. An organization relies heavily on several SaaS providers and third-party IT vendors. To ensure these external entities have adequate security controls in place (like encryption, access management, and incident response) before signing a contract, the organization's security team requires the vendors to complete a standardized set of security questions and provide evidence of independent audits (e.g., SOC 2 reports). What is this crucial supply chain risk management activity called?**
**(皇宮決定把煮飯、洗衣服、甚至保管小金庫的差事，全部外包給城外的幾家大商行 (relies on SaaS providers and third-party IT vendors)。但是大內總管心裡很發毛：這些商行真的可靠嗎？他們會不會把皇宮的衣服跟得麻瘋病的乞丐衣服混在一起洗？為了解決這個疑慮。總管在合約蓋章之前，派了一群錦衣衛去這些商行，丟給他們【『厚達三百頁的生死拷問卷 (standardized set of security questions)』】！考卷上問著：「你們家金庫用幾道鎖？警衛幾點換班？」。更狠的是，總管還要求商行老闆交出【『由天下第一大鏢局發放的安全認證金牌 (evidence of independent audits like SOC 2 reports)』】！如果答錯一題或拿不出金牌，皇宮一毛錢都不會給！請問！總管這種「簽字前先把你祖宗十八代的安保措施查個底朝天」的保命行為，稱作什麼？)**
A. Penetration Testing (滲透測試是派刺客去幫他們家找漏洞，這是一家公司「自己對自己」的測試。總管現在是要查「別人家」的管理制度合不合格，要的是管理面的證明書，不是幫他們做技術打擊)
B. Third-Party / Vendor Risk Assessment (Due Diligence) (這就是確保供應鏈大後方不起火的：【『外包商連坐法防禦大閘：第三方/供應商風險評估 (Third-Party / Vendor Risk Assessment) / 盡職調查 (Due Diligence)！』】。在將資料交給雲端服務 (SaaS) 或外包商之前，企業必須明白一個鐵律：【『你可以外包工作，但你永遠無法外包責任 (You can outsource the task, but not the accountability)』】！如果外包商被駭，導致你的客戶資料外洩，上法庭被告到破產的是你，不是外包商！因此，在採購階段 (Procurement/Onboarding)，資安團隊必須發送問卷 (如 SIG, CAIQ) 進行盡職調查。要求供應商證明他們實作了資料加密、有員工背景調查、並且通過了第三方會計師事務所的獨立驗證 (如 SOC 2 Type II 或 ISO 27001)。如果他們達不到要求，就拒絕簽約。這是在非技術面 (合規面) 卡控供應鏈風險的唯一解藥。)
C. Static Application Security Testing (SAST) (SAST 是用眼睛死瞪著程式碼藍圖找蟲子。這是在查程式碼的病，而總管現在是在查一整家公司 (供應商) 的管理體制有沒有生病)
D. Threat Modeling (威脅建模是自己在畫圖紙前，先拿著水晶球預測未來可能會有什麼刺客來殺自己。這屬於設計階段的腦力激盪，不包含去審查別家公司的認證證書)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是對 **「第三方風險管理 (TPRM) / 供應商風險評估 (Vendor Risk Assessment) / 盡職調查 (Due Diligence)」** 的標準描述。
    *   **雲端時代的必然：** 隨著 SaaS (Software-as-a-Service) 和雲端服務的普及，企業資料大量流向邊界之外。傳統的 Network Perimeter (防火牆) 已經無法保護這些資料。
    *   **評估機制 (Assessments & Audits)：** 由於企業通常無法 (或不被允許) 直接對供應商 (如 AWS 或 Salesforce) 發動滲透測試，因此必須依賴：
        *   **標準化問卷：** 如 CSA 的 CAIQ (Consensus Assessments Initiative Questionnaire) 或 Shared Assessments 的 SIG (Standardized Information Gathering)。
        *   **獨立稽核報告：** 最具公信力的是 **SOC 2 Type II** (證明特定安全控制措施在一段時間內有效運作) 或是 **ISO 27001 證書**。這代表供應商的資安體系已經被公正第三方檢驗過。

#### **4. A developer uses an open-source library downloaded from a public package repository (like npm or Maven Central). To guarantee that the downloaded package is the exact, unaltered version published by the original author and has not been maliciously modified in transit or tampered with on the repository server itself, what specific verification mechanism should the package manager or developer use before utilizing the library?**
**(一名老窯匠聽說京城外的大市集裡，有一種免費派發的『七彩幻影琉璃釉 (open-source library from public repository)』。他滿心歡喜地拿著罐子跑去市集裝了一罐回來。但是，大市集人多手雜，誰知道這琉璃釉在半路上有沒有被土匪摻了毒（modified in transit）？或者乾脆連大市集的掌櫃都被土匪綁架，把倉庫裡的釉料全數換成了炸藥（tampered with on repository server）？為了保證手裡這罐釉料，【絕對、完全、連一粒沙子的誤差都沒有】，就是當年發明家親手裝罐的原汁原味 (exact, unaltered version published by original author)。老窯匠在把這釉料塗上瓷器之前，他必須使出什麼樣的【滴血認親防偽大絕招】？)**
A. Checking the library's star rating on GitHub. (看星星數？如果你覺得一個星星數有十萬顆的店鋪絕對不會賣假貨，那你就是天字第一號肥羊！駭客最喜歡盜連這些名店的招牌，賣幾萬顆毒蘑菇給不長眼睛看成分的人。受歡迎不等於檔案沒被掉包！)
B. Running a dynamic analysis (DAST) scan on the downloaded `.jar` or `.tgz` file. (DAST 這種蒙眼瘋狗是去測試客棧大門會不會被踢破的，你叫它去測試一個還沒打開的罐子 (.jar 壓縮檔)？它直接就傻眼不動了！而且就算跑過沒有馬上中毒，也無法「保證檔案完全跟作者出廠時一模一樣 (Authenticity)」)
C. Verifying the library's Cryptographic Hash (checksum) and Digital Signature against the author's published public key. (這就是能把真假美猴王立刻打出原形的：【『生死指紋對照大法：密碼學雜湊值 (Cryptographic Hash) / 與作者親刻數位印信大驗證 (Digital Signature)！』】。老窯匠要做的就是兩件事：第一，拿出從官網上抄下來的原廠發明家密碼 (Hash Checksum)，然後把自己手裡這罐釉料丟進絞肉機絞一次，如果兩邊絞出來的密碼一模一樣，證明這罐釉料【一粒沙都沒被換過 (Integrity保證)】！第二，這罐釉料外面還有一個蠟封印章 (Digital Signature)。老窯匠拿出發明家公布的照妖鏡 (Public Key) 去照這個印章，如果發出金光，就證明這個印章【絕對是發明家親手蓋上去的，不是土匪偽造的店章 (Authenticity保證)】！兩者結合，這就是識別軟體供應鏈投毒的無上金身法門！)
D. Using a Virtual Private Network (VPN) to download the file. (VPN 是保證你在路上搬貨的時候，旁邊的人看不到你在搬什麼釉料。但是如果市集老闆給你的那一罐釉料，【本來就是一罐毒藥】！那你就算派三百個錦衣衛用 VPN 把它護送回家，到家打開裡面依然會是一罐能炸毀窯爐的毒藥！VPN 不驗證東西是好是壞)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「雜湊值 (Hash) + 數位簽章 (Digital Signature)」** 是驗證軟體套件的 **完整性 (Integrity)** 與 **真實性 (Authenticity / Provenance)** 的唯一技術標準。
    *   **供應鏈投毒途徑：** 駭客可能入侵套件庫伺服器 (Registry Server Compromise)，然後將原本正常的 `v1.2.0.tgz` 檔案替換成植入後門的惡意檔案。
    *   **Hash (Checksum) 的不足：** 如果只依靠 Hash，駭客在替換惡意檔案的同時，也可以把 Registry 上顯示的 Hash 值一起改掉。使用者下載後比對，依然會是「相符」的，因為他比對的是駭客留下的假 Hash。
    *   **Digital Signature 的決定性作用：** 為了防範這點，開發者通常會使用自己的私鑰 (Private Key, 離線保存) 對發佈的套件進行數位簽章 (如 GPG signing)。駭客因為沒有開發者的私鑰，無法生成有效的簽章。當使用者 (或 Package Manager 如 npm/Maven) 下載套件後，使用開發者公開的公鑰 (Public Key) 驗證簽章。如果檔案被竄改，或是駭客自己亂簽一個字，驗證都會失敗 (Signature Invalid)，從而阻斷了一場可怕的供應鏈攻擊。 (這也是 SLSA 框架中要求 Artifact 簽章的核心原因)。
