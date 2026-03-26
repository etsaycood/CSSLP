# 第三套全真模擬試題 (Exam 3) - 答案與詳解本
## 領域 8：安全的軟體供應鏈 (Secure Software Supply Chain) (12題)

---

#### **1. Following a devastating supply chain attack where a compromised third-party library was injected into their flagship product, the CISO mandates that the engineering team must automatically generate and publish a cryptographic inventory of every single open-source and proprietary component used to build the software. What specific artifact serves as this transparent "ingredients list" for the software supply chain?**
**(在經歷了一場猶如末日般的供應鏈慘案：自家的招牌產品裡，居然被偷偷混進了一個『包著糖衣的劇毒第三方程式庫毒藥 (compromised third-party library)』後。嚇破膽的資安大總管 (CISO) 下達了死命令：『從今以後！我們造車工坊裡的所有工程師。在生出任何一套軟體時，都必須使用密碼學技術，強制印出一張【『鉅細靡遺地羅列出這台車子到底用了幾根螺絲釘、那些開源零件是從哪間黑心工廠買來的『終極原料成份大清單 (cryptographic inventory of every single component)』】！這張終極防禦大清單，就像是超市裡食品包裝背後的【『透明度極佳的絕對成分履歷表 (ingredients list)』】一樣！請問，在供應鏈防禦的老爺車界，這張能把產品祖宗十八代的底細翻出來給大家檢查的成分履歷表，正式尊號為何？)**
A. A Code Signing Certificate (雖然有簽章，但這只是一張證明這台車是我做的身分證，它沒有交代車子裡面是用什麼螺絲做清單)
B. A Service Level Agreement (SLA) (這是保證我們服務幾小時不會斷線的賠償合約)
C. A Software Bill of Materials (SBOM) (這就是名震當代、被各國政府強制要求標配的供應鏈大殺器：【『軟體強迫大起底之終極原料物料清單 (Software Bill of Materials, SBOM)』】！)
D. A Static Application Security Testing (SAST) Report (這只是抓出你自己寫錯字的一份安全考卷成績單，它沒有交代你買了什麼外部零件)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是軟體供應鏈安全 (Supply Chain Security) 中最核心的概念：**「軟體物料清單 (SBOM, Software Bill of Materials)」**。
    *   **比喻：** 就像買餅乾要知道裡面有沒有過敏原 (花生、大豆) 一樣。現代軟體有 80% 的碼是開源的。如果有一天 Log4j 漏洞爆發，CISO 問：「我們家 500 個系統，有誰用了 Log4j？」如果沒有 SBOM，團隊只能像瞎子一樣去翻海量的原始碼。
    *   如果 CI/CD 流水線上自動產出了 SBOM (常見格式有 SPDX 或 CycloneDX)，CISO 只要把 SBOM 丟進掃描器，一秒鐘就能查出旗下哪 5 個軟體含有致命的 Log4j 零件版本，這是透明度 (Transparency) 的極致展現，也是美國拜登總統行政命令 (EO 14028) 強制規定的基礎防線。

#### **2. An attacker wants to compromise a popular Node.js application. Instead of attacking the application's servers directly, the attacker notices that the application relies on an open-source npm package named `data-parser-utils`. The attacker creates a malicious package with an almost identical name, `data-parsr-utils` (missing the 'e'), hoping developers will accidentally make a typo when installing the dependency. What specific type of supply chain attack is this?**
**(一名老謀深算的刺客，想要毒殺一座名為 Node.js 的大商城。他評估了一下，這座商城大門太硬 (attacking servers directly) 實在不好打。但他發現了一個天大的破綻：這座商城每天都會派採購員去城外的『開源市集 (open-source npm)』，購買一個名為『`資料解析好幫手 (data-parser-utils)`』的調味料包裹。於是，這名刺客心生一條毒計：他在市集裡擺了一個攤位，賣一種長得一模一樣、且名字幾乎完全仿冒的毒藥包裹，名字居然叫做『`資料解>析<好幫手 (data-parsr-utils，少寫了一個母音字母 e)`』！這名刺客就天天坐在攤位前守株待兔，【就等著哪天商城新來的菜鳥採購員，手殘點錯字或者眼殘看錯名字 (accidentally make a typo)，不小心就把這包毒藥買回皇宮裡煮給所有人吃 (installing the dependency)】！請問這等極度下流，專騙老花眼與胖手指的偷樑換柱偽裝術大攻擊，尊號為何？)**
A. Dependency Confusion (這是利用公私立名稱一樣，騙系統去載外面的那個高版本假貨。而現在刺客是用『拼字錯誤』來騙人類的眼睛，兩者稍有不同)
B. Typosquatting (這就是以『欺負手殘黨、專門蹲點在那些容易拼錯的熱門單字隔壁』聞名的：【『打字錯誤仿冒大蹲點攻擊 / 誤植域名蹲點 (Typosquatting)』】！)
C. Cross-Site Request Forgery (CSRF) (這是在網頁上偽造轉帳按鈕，這跟買包裹的拼字錯誤無關)
D. Man-in-the-Middle (MitM) (這是躲在橋中間攔截信件，不是躲在市集裡賣假貨)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這題精準描述了 **「Typosquatting (誤植/拼寫錯誤蹲點攻擊)」** 在開源生態系 (Npm, PyPI, RubyGems) 的應用。
    *   **攻擊原理：** 攻擊者註冊一個與極受歡迎的套件 (如 `lodash`) 名稱極其相似的惡意套件 (如 `lodassh` 或 `ldash`)。這個套件裡面寫滿了後門或惡意軟體。
    *   當受害者工程師在終端機打字安裝時，因為手滑打滿字 (`npm install lodassh`)，系統就會從公開資料庫把這個冒牌毒藥載下來。而且冒牌毒藥通常會包含正版的所有功能，所以軟體還能正常運作，讓開發者甚至沒發現自己裝錯了，直到木馬在系統內爆發。

#### **3. A large financial institution is evaluating a small, independent software vendor to provide a critical new payment processing module. Before signing the contract, the institution demands to review the vendor's internal security policies, their latest penetration testing results, and their employee background check procedures to ensure the vendor won't introduce unacceptable risk into the institution's ecosystem. What is the formal name for this rigorous evaluation process?**
**(一家財大氣粗、堆滿如山黃金的皇家金庫，正在考慮把『全國金條搬運大陣 (payment processing module)』這個最要命的任務，外包給城外一家只有五個人的小鐵匠舖 (small vendor)。但在大總管拿出金印蓋章簽約前，他突然變臉，拍著桌子提出了一籮筐極度苛刻的【『查戶口祖宗十八代大公文 (demands to review)』】！他命令這家小鐵匠舖：『聽好！把你們鐵匠舖的《門禁警衛管理法典 (internal security policies)》、上個月《給武林高手來暗殺家裡找破洞的滿地鮮血戰報 (penetration testing results)》、甚至你們那五個鐵匠有沒有《前科犯殺人紀錄的身家清白犯罪調查表 (employee background check procedures)》全部給我呈上來！老子必須百分之兩萬確定，老子把這個搬黃金的工作交給你們，不會引狼入室把我們金庫給搞垮 (ensure the vendor won't introduce unacceptable risk)！』。請問，這等猶如豪門選媳婦般，把下游外包商扒光衣服極限審查的嚴酷大拷問流程，正式官名為何？)**
A. Software Composition Analysis (SCA) (SCA 是查包裹裡面的三秒膠有沒有毒，這總管現在可是在查整間外包公司的保安與人品)
B. Third-Party Risk Assessment (or Vendor Risk Management) (這就是以高高在上的姿態、用錢砸死人的：【『第三方致命風險大審判 (Third-Party Risk Assessment) / 供應商風險終極大管控 (Vendor Risk Management, VRM)』】！)
C. Dynamic Application Security Testing (DAST) (這是對著別人的網站亂點亂踹測試，這種查閱祖宗十八代背景文件的行政查核不叫 DAST)
D. Incident Response Planning (這是火災發生後要怎麼逃跑的兵推演練規劃)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 在供應鏈安全中，你的防禦強度取決於「最弱的那一個環節」。如果大銀行自己的防火牆固若金湯，但他的外包商 (Vendor) 防護像紙糊的。駭客就會先打穿外包商，再利用外包商與銀行間的合法信任連線 (VPN) 反打進銀行大內 (這就是 Target 信用卡洩漏案與 SolarWinds 事件的翻版)。
    *   **Vendor Risk Management (VRM) 第三方風險管理：** 在採購 (Procurement) 與整合 (Integration) 任何外部軟體或服務前，必須對供應商進行全面的「盡職調查 (Due Diligence)」。評估他們的存取控制、加密標準、甚至實體機房與員工背景。如果評估不及格，就取消簽約 (Risk Avoidance)。

#### **4. To prevent unauthorized modifications to the source code after it has been reviewed and approved, a development team enforces a strict policy: Every single commit to the main production branch in Git must be cryptographically signed by the developer using their private GPG key. This ensures the organization can definitively prove which specific developer authored the altered code. Which fundamental security principle does this code-signing mandate enforce?**
**(為了防止這辛苦寫好的神聖程式碼法典 (source code) 上面，被人半夜偷偷塗改成辱罵皇帝的髒話 (prevent unauthorized modifications)！大將軍在放行藍圖的最後一關卡 (Git)，下了死命令：『聽好了！這本法典只要加上任何一個標點符號的增修 (Every single commit)，那個寫字的工匠，就必須要在這行字的旁邊，拿出他藏在內褲裡、這輩子【『只有他本人獨占擁有、別人絕對偷不走的那把名為 GPG 鑰匙的大私鑰印章 (signed using private GPG key)』】，在這行字旁邊狠狠蓋上血手印！這枚血手印能保證在審判法庭上，【被指控的傢伙百口莫辯、絕對無法賴帳說「這行罵皇帝的話不是我寫的」 (definitively prove which specific developer authored the code)】！』。請問這項逼迫所有人蓋血手印的鐵血大規定，其靈魂深處是為了伸張哪一項無可狡辯的絕對大真理？)**
A. Non-Repudiation (and Authenticity) (這就是那不容狡辯、把人定罪的神聖枷鎖大天條：【不可否認性 (Non-Repudiation) / 以及驗明正身的絕對真實性 (Authenticity)】！)
B. Availability (這是保證網站活著不當機，不管你賴不賴帳)
C. Obfuscation (這是把法典寫成火星文讓外人看不懂，這跟作者畫押蓋印章無關)
D. Least Privilege (這是只給小菜鳥掃地的權限，這並不是用密碼學蓋手印的定義)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **「數位簽章 (Digital Signatures / PGP/GPG Signing)」** 的核心目的。
    *   在 Git 版本控制中，任何人都可以隨便假造名字。例如駭客可以輕鬆地在 Git 裡下指令 `git config user.name "Linus Torvalds"`，然後用這個大神的名字送出一段含有後門的木馬 Code。這會讓調查人員完全找不到真兇。
    *   **不可否認性 (Non-Repudiation)：** 如果強制作業系統必須驗證 開發者本人的 GPG 私鑰 (Private Key) 簽章才能 Merge Code。因為私鑰只有該開發者獨有，一旦簽章吻合 (Authenticity 驗證通過)，這個工程師在法庭上就【無可抵賴、絕對無法否認】這段 Code 是他寫的。這是防護內部惡意員工 (Insider Threat) 竄改源碼的最強防線。

#### **5. An enterprise development team uses a private, internal artifact repository (like JFrog Artifactory or Sonatype Nexus) to cache approved versions of open-source libraries (e.g., Maven, npm). The build servers are strictly configured to pull libraries ONLY from this internal repository, completely blocking them from downloading packages directly from the public internet. What is the primary supply chain risk this architecture mitigates?**
**(一家豪強帝國的造車大本營裡。大將軍在後山的深宮內院，修築了一座【『重兵把守的皇家私有內網大糧倉 (private, internal artifact repository like JFrog Artifactory/Nexus)』】。這座糧倉裡面存放著的，全都是那些經過太醫【拿銀針試過毒、並且蓋上皇室核可大印的開源零件大米 (approved versions of open-source libraries)】。大將軍並下達最嚴酷的封山大鎖國軍令：『廠房裡所有正在組裝馬車的無腦工作台機器人 (build servers)。你們這輩子肚子餓需要零件時，【絕對、死都不可以擅自跑出城外，去那龍蛇雜處、骯髒不堪的公共網際網路大市集上隨便亂撿別人賣的套件 (completely blocking them from downloading packages directly from public internet)】！你們要拿零件，唯一合法的管道，就是乖乖去後山那個被我們把關的內網大糧倉領料 (pull ONLY from this internal repository)！違者直接斷電砍頭！』。請問，這座猶如『關防內網大糧倉』的絕育陣法，它最先要封殺並抵禦的，是外部毒氣供應鏈世界裡的哪一種劇毒污染崩潰大劫？)**
A. It prevents SQL Injection attacks on the build server. (SQL Injection 是因為你從網頁沒消毒被塞指令，現在是組裝機器人在下載零件，風馬牛不相及)
B. It drastically reduces the risk of developers accidentally downloading malicious, unvetted, or tampered packages directly from public repositories, enforcing a single source of truth for approved dependencies. (這就是這座黃金內網糧倉的偉大奧義：【它能徹頭徹尾地斷絕那群眼殘手殘的工匠與無腦組裝機，在外面那個大病毒庫裡『不小心誤撿到被下毒的蘋果、未經皇室太醫審查的劣等劣質品、或是被人偷偷調包的暗殺包裹 (malicious, unvetted, or tampered packages)』！並且以霸權威信，強制在城內豎立起『全世界就只有我這座糧倉裡的米才是唯一合法的真理之源活結界 (single source of truth)』！】)
C. It ensures the build runs faster because internal networks have more bandwidth. (內網的確比較快，但那只是順便的好處。為了安全才是花大錢蓋資安隔離糧倉的最霸氣主因)
D. It automatically encrypts all source code before compiling. (這座糧倉只是拿來放別人寫好的零件庫存發放，它不是拿來把你自己的藍圖加密的兵工廠)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是軟體供應鏈安全中的黃金防禦架構：建立 **Internal/Private Artifact Repository (如 JFrog, Nexus)** 做為唯一的依賴項代理 (Proxy)。
    *   **痛點：** 公開的 npm 或 Maven Central 是無國界的，任何人都可以上傳名為 "好用套件" 的木馬。如果開發人員和 CI/CD Build Server 每次都直接從網路上 `npm install`，只要某一天原作者的帳號被盜用發布了有毒版本，你們公司的 Build Server 就會立刻吃下這包毒藥，直接把毒藥編譯進公司的心臟產品裡。
    *   **防禦機制：**
        1.  企業**封鎖**了開發機與 CI 伺服器連往外網 `registry.npmjs.org` 的權限。
        2.  他們只能向 "內部的 JFrog 伺服器" 請求套件。
        3.  JFrog 會攔截請求，先去網路上把套件載回來，然後**先用內部的 SCA (如 Xray) 軟體掃毒掃漏洞**。確認無毒後，才放在內部倉庫裡提供給 CI 伺服器。這確保了進入廠房的每一塊磚頭都是乾淨的。

#### **6. A company develops firmware for medical devices. To assure hospitals that the firmware update files downloaded from the company's website have not been tampered with or replaced by malware while in transit across the internet, the company provides a SHA-256 hash value next to the download link. Providing this cryptographic hash ensures which core tenet of the CIA triad for the supply chain artifact?**
**(一家專門鑄造『讓窮人吊命用之皇家續命大機器』的心臟晶片大工坊 (develops firmware for medical devices)。為了讓天下醫館的太醫們放心，工坊在天下公告板上貼出：『為了證明這包你們從網路上載回去準備灌進病人身體裡的續命大晶片，在經過那強盜橫行的長途運送馬車半路上。絕對沒有被外星駭客半路綁架、偷偷掉包、並往裡面塞進一隻會讓病人馬上歸西的木馬惡靈 (have not been tampered with or replaced by malware in transit)！我們大工坊在這包晶片的下載門口旁邊，刻下了一道連老天爺也無法仿造的【『神聖之 SHA-256 終極驗明正身碎骨大印記數字 (SHA-256 hash value)』】！太醫們下載完，只要把晶片拿去磨碎比對這串印記，如果數字一摸一樣，就證明這包晶片連一顆灰塵都沒被動過手腳！』。請問，這枚神聖大印記所保衛的，正是那名揚天下的 CIA 資安大三合一神主牌裡的哪一尊偉大神明？)**
A. Confidentiality (機密性是確保晶片內容不被小偷偷看，而這個大印記只保證沒有被竄改，它是明文公開貼在網頁上的)
B. Integrity (這就是能證明晶片在運送過程中，沒有缺一口肉、沒有被灌水、絕對維持原汁原味那最神聖不可侵犯的：【『完整性大權威 (Integrity)』】！)
C. Availability (那是確保下載的按鈕隨時都按得下去不會當機，這跟晶片有沒有被下毒無關)
D. Authorization (這是決定太醫有沒有資格進門買東西的特權警衛機制，這保護不了下了網以後的晶片安全)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 密碼學雜湊 (Cryptographic Hashing，如 SHA-256) 的**唯一**且最神聖的目的就是保證 **「完整性 (Integrity)」**。
    *   **Hash 的特性：** 給定一個 500MB 的 Firmware 更新檔，經過 SHA-256 運算後，會產生一串 64 個字元的固定字串 (如 `1A3B...`)。這串數字是該檔案的 "數位指紋 (Digital Fingerprint)"。只要途中駭客把更新檔裡面的任何**一個位元 (Single Bit)** 改掉 (例如植入了一行木馬)，這個檔案算出來的 Hash 值就會雪崩式改變，變得跟官方公布的 `1A3B...` 完全不一樣。
    *   所以醫院在安裝前，自己算一次下載檔案的 Hash，比對官網提供的數字。若吻合，就保證檔案 100% 沒有被竄改過 (Tampered/Altered)，完美維持了供應鏈交付過程的 Integrity。

#### **7. A cloud-native startup utilizes hundreds of open-source container images from Docker Hub. The security team implements an automated policy that immediately blocks any container image from running in the production Kubernetes cluster if the image has not been scanned for CVEs within the last 24 hours and if its digital signature cannot be verified against the trusted corporate registry. What process is the security team enforcing?**
**(一群在雲端飛簷走壁的新創遊俠，他們從名為『大鯨魚海港中心 (Docker Hub)』的跳蚤市場裡，牽了幾百隻野生的大鐵櫃貨櫃車回來用 (utilizes hundreds of open-source container images)。但這群遊俠的保安局長發飆了！他在最後那條要送進天界大營運場 (production Kubernetes cluster) 的入口關卡上，架起了一座會自動開槍發射紅外線的：『終極死亡大鍘刀 (automated policy locks image)』！這座鍘刀的法規血淋淋寫著：任何一台大鐵櫃車，只要【牠的身體在過去 24 小時內沒有被捉妖機給徹底 X 光掃毒過 (not been scanned for CVEs)！或者！牠的車牌號碼上，拿不出那枚由我們家皇室專屬打鐵舖親自打上去、證明這台車血統純正的『數位血統大簽名鋼印 (digital signature cannot be verified)』！】，鍘刀就會當場落下把它就地斬首，絕對不准它開進天界大營 !請問！這套連環驗車驗血統的恐怖絕殺大把關陣法，其學名稱之為何？)**
A. Penetration Testing (這是派刺客去偷看，不會寫在這種自動運轉封殺的貨櫃車流水線上)
B. Container Image Provenance and Attestation Verification (這就是這座鍘刀真正執行死刑的法條奧義：【『貨櫃大怪獸之血統履歷來源大盤查 (Provenance) / 以及終極無瑕數位宣誓簽章驗證大防線 (Attestation Verification)』】！)
C. Static Application Security Testing (SAST) (這是看書找錯字的工具，不是用來阻擋會活蹦亂跳裝滿各種環境垃圾的 Docker 貨櫃車上架的查哨站)
D. Distributed Denial of Service (DDoS) Mitigation (DDoS 是阻擋外面瘋狗進來亂按連線把你的大門擠破，這是內網自己在攔截不合規範的貨櫃車，並非防禦網路塞車攻擊)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「容器映像檔來源與證詞驗證 (Container Image Provenance and Attestation Verification)」**。
    *   這是 Kubernetes / 雲端原生供應鏈安全中非常強大的「部署時控制 (Deployment-Time Controls)」概念。(常見實作如 OPA/Gatekeeper 或 Kyverno，結合 Notary/Cosign)。
    *   **痛點：** Docker Hub 上面有太多暗藏惡意挖礦軟體的毒貨櫃。如果任由開發人員隨意 `kubectl apply` 抓網路上的貨櫃來跑，生產環境會立刻淪陷。
    *   **防禦機制 (Admission Controller)：** 在貨櫃要啟動的前一秒。Kubernetes 的守門員會檢查這顆打包好的映像檔 (Artifact)：
        1.  它近期有沒有 CVE 掃描及格的 "證書 (Attestation)"？
        2.  這個映像檔是不是有被我們公司內部的私鑰 "數位簽章 (Signature)" 認證過？(代表這顆貨櫃的來源 Provenance，確實是由我們家可信的 CI 產出的，而不是憑空竄出來的)。
    *   如果驗證不過，Kubernetes 伺服器會直接拒絕執行 (Block pod creation)，斬斷供應鏈中段的非法入侵物。

#### **8. The "SolarWinds" attack is often cited as the textbook example of an Advanced Persistent Threat (APT) supply chain compromise. How did the attackers primarily distribute their malicious code to thousands of highly secure government and corporate customer networks?**
**(震驚全球、被寫進資安教科書卷首那場名為『太陽風暴 (SolarWinds) 帝國大崩塌』的末日浩劫，是世界公認【幽靈級國家大軍 (APT) 完美執行了『供應鏈斬首大行動』】的最強鐵證神話！請問，這群如鬼魅般的太陽風暴外星人，當初到底是用哪一種【猶如木馬屠城記般極致邪惡、且能一次把劇毒灑滿防備森嚴的大一統美國四大國家情報局與幾萬家頂尖帝國的心臟地帶】的究極下毒管道送毒的？)**
A. By sending massive phishing email campaigns to the target companies' employees. (如果只是亂發那些騙菜鳥點擊的釣魚信，那根本進不了國家情報局，因為這些高級單位不允許點奇怪的信。而且這也稱不上是「供應鏈」的高級戰略)
B. By compromising the SolarWinds build environment and injecting a digitally signed, malicious backdoor into a legitimate software update, which the customers then downloaded and installed automatically. (這就是這場世紀神級鬼吹燈大劫難的最真實且令人毛骨悚然的原貌：【駭客居然逆天而行，直接殺進去太陽風暴原廠的『黃金兵工廠 (build environment)』裡面把廠長給宰了！然後他們把那隻名叫 SUNBURST 的恐怖後門木馬，悄悄塞進了太陽風暴『看起來完全合法、而且上面還活生生蓋著原廠大金印數位簽章的超級更新大福袋裡面 (digitally signed legitimate software update)』！幾千家國家情報局與帝國，完全沒有懷疑，開開心心地讓這個大福袋沿著自動更新的通道，光明正大地從正門被迎進了自己的最深無塵室裡，自動安裝並引爆 (customers downloaded and installed automatically)！】這就是利用官方通道運毒的最強無解死局供應鏈大殺戮！)
C. By exploiting a zero-day vulnerability in the customers' Cisco firewalls. (如果只是打穿防火牆，那這是基礎設施破防，這不算典型的供應鏈下毒。供應鏈是從上游原物料廠偷放毒藥進下游水庫裡的戰法)
D. By physically breaking into data centers and plugging in infected USB drives. (這些特務就算會飛天遁地，也不可能在同一個晚上同時潛入一萬家國家最高級的保險庫去插隨身碟)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是對 **SolarWinds (太陽風) 供應鏈攻擊事件** 歷史與技術路徑最精確的總結。
    *   **攻擊的核心本質 (Upstream Compromise)：** 駭客 (俄羅斯 APT29 / Cozy Bear) 的目標是美國財政部、國土安全部等極難直接攻破的機構。所以他們採取了一種「打你信任的上游廠商」的供應鏈戰略。他們攻擊了這些機構廣泛使用的網路監控軟體 "SolarWinds Orion" 的開發原廠。
    *   **Build Server 污染與簽章背書：** 駭客潛入 SolarWinds 的 CI/CD Build 伺服器，在軟體打包成更新檔前，把一段名為 SUNBURST 的後門程式碼塞了進去。最致命的是，這個被下毒的軟體更新包，**仍舊完美地簽上了 SolarWinds 官方的合法憑證 (Digitally Signed)**。這導致全球 18,000 個客戶的資安防護系統 (IPS/Antivirus) 把這個劇毒木馬當作「親兒子原廠官方合法的升級版」，一路綠燈自動安裝到各家公司內部的最高權限監控伺服器上，釀成無法挽回的世紀災難。

#### **9. A development organization specifies in its vendor contracts that any third-party software library integrated into their product must have a "Time-to-Remediate" Service Level Agreement (SLA) of less than 72 hours for critical CVEs. If the open-source project or vendor cannot patch critical vulnerabilities within this timeframe, the organization will refuse to use the library. What specific aspect of supply chain security management does this address?**
**(一家氣焰囂張的皇家軟體開發大兵團，在他們所有的外借零件採購契約 (vendor contracts) 上面。用人血畫押了一套猶如催命符般的『絕命死亡倒數大條款 (Time-to-Remediate SLA)』：『聽好了外面的鐵匠庫！如果你們家賣給我們的模組零件，有一天被百曉生通報說上面有一個被核彈炸出來的大洞 (critical CVEs)！老子規定你們這些鐵匠，【必須在漏網的 72 個時辰之內，給我熬夜把這個洞補好的解藥貼布給生出來交給老子 (less than 72 hours for critical CVEs)】！如果你們這群廢物補洞太慢，那老子這輩子絕不會用你們的爛東西，立刻解約退貨！』。請問，這套嚴酷的買家老爺大條款，它是為了在對付這整條外掛供應鏈大生態圈時，狠狠捏住了哪個防禦的命脈弱點？)**
A. Intellectual Property (IP) Protection (專利保護是不准別人偷去賣錢，而不是在算你補洞生出解藥的速度)
B. License Compliance (e.g., GPL, MIT) (這是看你偷用別人東西有沒有付錢或是要被抓去關，這是版權律師幹的活)
C. Vulnerability Management and Response Capabilities of the Supplier (這就是直指核心的唯一法眼：【『供應商那群傢伙在修補漏洞與應對大災難時的『反應與救火生存大能力 (Vulnerability Management and Response Capabilities of the Supplier)』』！】！這兵團深知，用別人的套件不可怕，可怕的是洞爆發了卻找不到人補！如果鐵匠鋪擺爛兩個月都不出修補程式，這段空窗期這兵團就會被駭客活生生當作活靶子打死！合約逼迫鐵匠鋪 72 小時交卷，就是在確保下游保命的速度！)
D. Code Obfuscation Requirements (這是要求你把軟體外殼塗成泥巴保護演算法不要給別人看懂，這防不了被公開在百曉生上面的漏洞大危機)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 在軟體供應鏈安全中，評估開源社群或商業供應商時，其中一個最關鍵的指標就是：**「供應商的漏洞修補能力與反應時間 (Vendor's Remediation/Response capability)」**。
    *   **開源/第三方的隱患：** 現代軟體依賴海量的第三方套件 (Third-party libraries)。當一個嚴重等級 (Critical, CVSS > 9.0) 的漏洞爆發時。因為這段代碼是別的廠商寫的，你家裡的工程師【根本無權、也看不懂】要怎麼去改這個原始碼深處的 Bug。你唯一能做的，就是雙手合十，祈禱上游的那個開源作者趕快釋出新版 Patch 解藥。
    *   **SLA 的威懾：** 很多死氣沉沉的開源專案 (Abandonware)，可能漏洞爆發了半年都沒人去修。這會讓依賴它的企業長期處於高度曝險的 0-Day 狀態。因此，透過合約 (SLA) 強制規範「高危漏洞 72 小時必須給解藥」，是供應鏈保命 (Supply Chain Risk Management, SCRM) 的核心行政與法務控制手段。

#### **10. An attacker discovers that a corporate application relies on private internal packages (e.g., `com.mycompany.utils`). The attacker publishes a malicious package with the exact same name (`com.mycompany.utils`) to the public internet repository (like public npm) but gives it a much higher version number (v99.0.0). Because the corporate build tool is misconfigured, it automatically pulls the highest version number from the public internet instead of using the local v1.0.0 internal package, inadvertently executing the attacker's code. What is this specific supply chain attack called?**
**(一名躲在暗處的小偷，有一天趴在帝國皇城的老鼠洞偷看時。發現那些在做苦力的皇家工程師，每次都在私下流傳一包叫做『`我們家自己的無敵工具大包裹 (com.mycompany.utils)`』。小偷心生一條移花接木的奇妙毒計！這小偷居然跑去城外大市場那個完全不用身分證就能上架的『公開跳蚤市場大集線台 (public internet repository like npm)』！並且在那裡，他也捏造上架了一顆名字『一字不漏、百分之百字體完全一模一樣也叫這名字的劇毒包裹 (exact same name)』！但他耍了個賤招，這小偷把這包毒藥的【『集數版本號碼，直接灌爆灌水到 第九十九代神盾版 (much higher version number v99.0.0)』】！這時皇宮裡的阿呆機器人肚子餓要拿包裹，因為他被寫定的程式是『貪慕虛榮、永遠只拿集數最高版本 (pulls highest version)』！所以阿呆機器人就瞬間眼瞎，直接放棄了皇宮內牆裡那包原廠的第一代正版包裹，轉頭伸出手去城牆外的毒海市集裡，把那包光鮮亮麗的第九十九代毒藥帶進肚腹裡 (instead of using the local v1.0.0 inadvertently executing attacker's code)！請問這等極度戲謔瘋狂的版本號數字霸凌混淆欺騙術，尊號為何？)**
A. Dependency Confusion (or Dependency Hijacking) (這就是以此神不知鬼不覺、玩弄內網外網傻傻分不清楚的真假美猴王世紀大騙局而名垂青史的：【『供應鏈依賴關係之狸貓換太子大混淆騙局 / 依賴劫持 (Dependency Confusion / Dependency Hijacking)』】！)
B. Typosquatting (這小偷根本沒有故意去寫錯名字騙人眼花，他就是一模一樣的正體大字名字，不玩錯字把戲)
C. Cross-Site Scripting (XSS) (這是去別人的網頁裡面貼一段隱形小廣告讓訪客中毒，這不是騙機器人裝外面的軟體)
D. Buffer Overflow (這是把包裹強行塞破記憶體的小箱子，而不是這種智商輾壓的高智商騙術)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 這是 2021 年震驚安全界的 **「相依性混淆 (Dependency Confusion)」** 攻擊，由安全研究員 Alex Birsan 首創，成功駭入蘋果、微軟、Paypal 等幾十家頂級科技巨頭。
    *   **攻擊原理 (Namespace 碰撞與版本解析缺陷)：**
        1. 大公司大多自己開發內部套件 (Private Package)，如 `paypal-core-utils`，這些套件平時都只放在內網的倉庫裡。
        2. 開發工具 (如 `npm`, `pip`) 預設的行為很天真。當你要安裝 `paypal-core-utils` 時，它會【同時向】"內網私有倉庫" 和 "外網公開倉庫 (Registry)" 查詢這個套件。
        3. 當工具發現內外網都有同樣名字的套件時。預設的演算法是：「誰的 Version 數字比較大，誰就是最新版，我就裝誰！」(這是一個致命的預設邏輯缺陷)。
    *   所以攻擊者只要去公開的 npm 上註冊這個名字，然後把版本設成 `v99.9.9`，大公司的 Build 機器就會像貪小便宜的傻子一樣，把外網的惡意木馬裝回家，徹底繞過所有防火牆。

#### **11. A developer copies a large block of code from a popular open-source project on GitHub that is licensed under the strict GNU General Public License (GPL) and pastes it directly into their company's proprietary, closed-source commercial software product. According to standard open-source licensing compliance, what is the most likely severe consequence for the company?**
**(一名手腳不乾淨的偷吃步工程師，有一天深夜，偷偷摸進了那座名叫 GitHub 的開源大武林藏經閣裡。他看到一部寫得絕妙無雙的神祕劍譜，上面貼著一個閃著刺眼血紅大字標籤：【『GNU 極端偏執共產絕對開放通用大版權聖物 (GPL License)』】。這工程師居然看都不看一眼旁白寫的警告，就直接拿剪刀把這幾百頁劍譜，硬生生地整段黏貼縫合進他們家原本用來賺大錢的【『祖傳絕對不外傳之頂級黑盒閉源印鈔大機器商業產品 (closed-source commercial product)』】裡面！請問，根據江湖上那令大財主聞風喪膽的開源版權律法。這工程師手滑的這一剪刀，日後被發現時，會為這家帝國招致哪一種最血淋淋的連坐法家法大清算慘案？)**
A. The company's database will automatically encrypt itself. (版權又不是有知覺的活體電腦病毒勒索軟體，他哪會自動去封印你的保險庫)
B. The company faces significant legal risk, as the "viral" nature of the GPL may legally force the company to open-source and publish their entire proprietary codebase for free. (這就是讓那些大財主夜半驚醒的恐怖詛咒深淵：【因為這條 GPL 版權法，被江湖恐懼地尊稱為『無法免疫之絕對傳染絕症大病毒 (viral nature of the GPL)』！只要你的印鈔機身上沾染了哪怕只有一行 GPL 的血脈。根據死神法典：這間可憐的閉源印鈔兵工廠將面臨天價的律師團起訴，最後他們可能被法庭強制逼迫：【把那台這輩子都不准人看的祖傳印鈔黑盒機器 (proprietary codebase)，直接像扒光衣服一樣，被逼著免費開源並公諸於世免費送給全地球人看 (open-source and publish entire codebase for free)】！這簡直是把江山直接斬草除根阿！】)
C. The code will fail to compile. (編譯器是機器，機器是文盲不懂什麼法律版權條例的，他照樣給你變成印鈔機運轉)
D. The company will be fined by the FBI for hacking. (FBI 抓的是拿鐵鎚打別人家門的駭客，如果是你侵權，那是這段原版劍譜開源作者委託智財律師來告到你脫褲子，這不是犯罪駭客行為，而是智慧財產權民事糾紛)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這題探討的是軟體供應鏈安全中的 **開源授權合規風險 (Open Source License Compliance Risk)**，特別是針對 **GPL (GNU General Public License)**。
    *   **開源授權的兩極端：**
        *   **Permissive (寬鬆授權，如 MIT, Apache)：** 大方的神仙。你可以拿我的 Code，怎麼改都行，甚至拿去包成黑盒軟體賣錢也可以，只要附上我的名字宣告。
        *   **Copyleft/Restrictive (強著佐權/限制性，如 GPL, AGPL)：** 被稱為具有 **"病毒式傳染性 (Viral)"** 的版權。它的理念是強制的開源共產：「如果你使用了我的任何 GPL 程式碼並打包發布。為了回報社群，你【必須】把你自己的全部專案，也按照 GPL 授權條款，把原始碼 100% 免費公開上網 (This requires you to open-source your entire derivative work)」。
    *   所以如果一家原本賣黑盒軟體的公司，工程師不小心把 GPL 的元件塞進去，公司就會在法律上被原作者控告，面臨要把幾千萬美金的商業機密原始碼 "全盤開源裸奔" 的巨大威脅。

#### **12. During the build process, a Continuous Integration (CI) server compiles the source code into a binary executable. The CI pipeline is configured to calculate the hash of the source code repository states, the specific compiler version used, and the final output binary, packaging these cryptographically signed metadata records together. This verifiable record that proves *how* and *from what* the software was built is known fundamentally as:**
**(在那個暗無天日的兵工廠造車大熔爐裡 (Continuous Integration server compilation)。當那塊熱騰騰的鐵餅 (binary executable) 剛被大槌敲定成形的那一剎那！這座兵工廠的履歷中心，啟動了一項『最高階的終極出生證明烙印法陣』！這個法陣不但紀錄了：【當初這塊生鐵皮是出自那一座礦山第幾個土坑 (hash of source code repository states)！】、【我們剛剛是用幾磅重、那個叫什麼型號的鐵鎚敲它的 (specific compiler version used)！】、【甚至連最後出爐時鐵餅的精確水分子指紋重量都記錄在案 (final output binary hash)！】！最後，老和尚會把這些祖宗十八代出處、工具細節，全部用一張『數位血手印符咒 (cryptographically signed metadata)』大印封死在一起！請問這張能【向全天下世人證明：這塊鐵餅到底他媽的是『從什麼娘胎裡生出來、並且是老子用什麼刀法親自割下來的 (proves how and from what it was built)』】！這份無敵的生平驗明正身履歷文件，正式的道名尊稱為何？)**
A. A Non-Disclosure Agreement (NDA) (那是不准你出去到處亂講話洩密的封口費死契，跟這種履歷表查生平無關)
B. Software Provenance (or Build Attestation) (這就是那神聖不可侵犯、把血統證明推升到藝術境界的：【『軟體出處血統大證明 / 產銷履歷 (Software Provenance) / 或稱不可抵賴之「建置宣告大誓詞」 (Build Attestation)』】！)
C. A Threat Model (這是在黑板上用粉筆討論哪裡有漏洞的假想敵劇本，不會做這種滴水不漏的數位簽名)
D. An End-User License Agreement (EULA) (這是賣軟體給你時，逼你在下面勾選同意打勾的又臭又長法律使用者條款，這不是交代這軟體是怎麼生出來的履歷)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「軟體出處/溯源 (Software Provenance)」** 與 **「建置證詞 (Build Attestation)」**。
    *   自從 SolarWinds 事件爆發後，大家發現「你就算給我程式碼 (Source) 跟執行檔 (Binary)，我怎麼知道它編譯的過程中有沒有被植入別的木馬？」。
    *   這就是 SLSA (Supply-chain Levels for Software Artifacts) 框架試圖解決的問題。我們需要在 Build (建置) 的當下，記錄一份不可竄改的 "出處證明 (Provenance)"。
    *   這份 Attestation 記錄了：我是用 Git 版本 Hash 結尾 `1a2b` 的代碼，搭配 `GCC v9.0` 編譯器，在 `Ubuntu 20.04 CI Runner 03` 機器上，在 2:00 PM 編譯成這個二進位檔的。而且為了防偽，這整包紀錄本身還被 CI 伺服器的私鑰簽名了。所以客戶拿到軟體後，可以從頭到尾驗證它「血統的純潔性」，確保中間絕對沒有被動過手腳。
