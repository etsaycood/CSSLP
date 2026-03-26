# 第四套全真模擬試題 (Exam 4) - 答案與詳解本
## 領域 8：安全的軟體供應鏈 (Secure Software Supply Chain) (12題) - Part 3 (Q9-Q12)

---

#### **9. An organization provides an API key to a contracted third-party marketing vendor so their systems can read customer analytics data. However, the organization's security team configures the API key so that it can ONLY execute `GET` requests on specific endpoints and explicitly Denies any `POST`, `PUT`, or `DELETE` operations. What security principle is the organization applying to manage this third-party risk?**
**(皇城大內總管發了一張銀牌通行證給城外專門來數人頭的『八卦包打聽算命仙 (third-party marketing vendor)』。這算命仙需要進皇宮來看看皇帝今天穿什麼顏色的內褲，好去外面發佈新聞。但是大總管非常堤防這個外人。這張銀牌上被太監總管刻滿了這輩子最惡毒的【『斷手腳之只能看不能摸死咒 (ONLY execute GET requests and explicitly Denies POST, PUT, DELETE)』】！這咒語規定：只要算命仙拿著銀牌進宮，他【只准用眼睛看 (GET)，連呼吸都不准出聲】！如果這算命仙敢試圖動手把皇帝的內褲拿下來 (DELETE)、或者想給皇帝套上一件綠皮襖 (PUT/POST)！這張銀牌會直接爆炸把算命仙的手炸斷！請問，大總管用這張銀牌防範外包商搞破壞的兵法，體現了哪一個最經典的安防核心大原則？)**
A. Security through Obscurity (隱蔽式安全是把銀牌藏在尿壺裡祈禱算命仙找不到，而這張銀牌是光明正大掛在算命仙脖子上的，而且上面明白刻著他只能幹嘛的規矩，這完全不隱蔽)
B. Principle of Least Privilege (PoLP) (這就是名震古今、斬斷無數野心家雙手雙腳的：【『絕對苛刻之極限閹割大枷鎖：最小權限原則 (Principle of Least Privilege / PoLP)！』】。在資安的鐵律裡，對於【任何外人 (Third-party) 與自己人 (Employees)】的授權，永遠都是【你只配拿到你剛好餓不死的權力 (only privileges necessary to perform its intended function)】！既然這算命仙的任務只是「讀取數據發新聞 (Read data)」，那皇宮就絕對沒有理由給他一張能「刪除資料或修改庫存 (Write/Delete)」的萬能金牌！就算未來這算命仙在城外被人綁架 (API Key Compromised)，駭客拿著這張銀牌殺進皇宮，駭客崩潰地發現他除了當個偷窺狂之外什麼破壞也幹不成，爆炸半徑被完美地鎖死在最小範圍。這是防堵第三方風險擴大的最有效 IAM (身分與存取管理) 實務！)
C. Fail-Safe Defaults (失效安全預設是如果皇城失火大門會自動打開讓老百姓跑出去。這題的大總管是主動發放一張寫死只有單一權限的銀牌，並沒有探討「當這張銀牌失效時會發生什麼事」)
D. Economy of Mechanism (經濟機制是把算命仙的核驗機制做得越簡單越好，這跟大總管去限制算命仙手腳的行為完全無關)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是 **「最小權限原則 (PoLP)」** 在身分與存取管理 (IAM, Identity and Access Management) 及 API 安全中的標準實踐。
    *   **供應鏈 (SaaS/Vendor) 風險的核心：** 企業為了方便整合 (Integrations)，常會核發過大權限 (Over-privileged) 的 API Keys 或 Service Accounts 給第三方供應商。
    *   **風險後果：** 如果該行銷公司的伺服器被駭，駭客會偷走這把 API Key。如果這把 Key 有 `Write/Delete` 權限，駭客可以輕易地刪除委託企業的雲端基礎設施或資料。
    *   **防堵策略 (PoLP as a Control)：** 透過強制設定 IAM Policy (如 AWS IAM roles)，將 API Key 限制為只讀 (Read-only / HTTP `GET`) 且綁定特定資源 (Resource-level granularity)。這樣就算 Key 外洩，造成的損害也僅限於資料的 Confidentiality (機密性) 外洩，而不至於影響到系統的 Integrity (完整性) 或 Availability (可用性)。

#### **10. To mathematically prove the provenance and integrity of a software artifact (e.g., a Docker container image) moving through a CI/CD pipeline, organizations increasingly adopt frameworks like SLSA (Supply chain Levels for Software Artifacts). What critical mechanism does SLSA primarily rely on to bind an artifact to its build metadata and source code origin?**
**(在皇城最大的大鑄劍神爐 (CI/CD pipeline) 裡，每天都會掉出幾萬把新造好的『神盾航空母艦 (software artifact / Docker image)』！但是！太陽神皇帝根本不相信這群鑄劍工匠！皇帝害怕這鐵船在出爐子的那一刻，就被工匠偷偷放了一隻吸血鬼進去。為了解決這個信任危機。天上降下了一部名為【『SLSA：神聖天條驗鈔機大陣法 (Supply chain Levels for Software Artifacts)』】！這部陣法的最神聖真理是：【『要讓天下萬民相信這艘鐵船是真的、是純潔的，我不聽工匠用嘴巴發誓！我這部驗鈔機只認一種絕對無法造假的數學奇蹟！』】。這部陣法要求：在這艘小鐵船剛出爐、還沒離開火爐口的那一秒鐘 (build time)！必須用【某種連玉皇大帝都無法篡改的天道手段】，把這艘鐵船的靈魂 (artifact) 跟它當初那張還沾著工匠口水的設計圖 (source code origin / build metadata) 給死死地、永生永世地【綁在一起 (bind)】！請問！在這套連美國國防部都在用的神聖供應鏈天法中，究竟是靠著什麼樣霸道的技術來完成這個不可分割的靈魂綁定大典？)**
A. Storing the artifacts in a hidden, unlisted directory. (把它藏在後山的隱私倉庫裡？那只是讓這鐵船比較晚被土匪找到！這這根本無法「用數學證明 (mathematically prove)」這鐵船不是瞎拼湊的假貨，這叫自欺欺人的遮掩法，完全沒有鑑識效力)
B. Cryptographically signing the build provenance (the metadata describing how, when, and by whom the artifact was built). (這就是 SLSA 聖典的核心靈魂：【『數學死律之終極鎖靈陣：來源證明之密碼學大簽章 (Cryptographically signing the build provenance)！』】。SLSA (唸作 Salsa) 是 Google 推出的這套框架，它的最高指導原則是「不可否認性」。在鐵船出爐時，CI 系統會自動生成一張「履歷表 (Build Provenance)」紀錄：這船是張三在早上八點，用第 33 號火爐，拿 GitHub 上第 `abc1234` 號藍圖造出來的！【最變態的是！】這履歷表寫完後，CI 系統會自己掏出只有它有的那一枚『打假神界私鑰 (Private Key)』，對著鐵船跟這張履歷表，【狠狠蓋上一個永遠無法洗掉的金印 (Cryptographic Signature)】！以後這鐵船開出海被老百姓買到時，老百姓只要拿天上發放的『打假神鏡 (Public Key)』一照！金印若是破了，代表船被掉包；如果那履歷表上面的時間被土匪塗改了一秒鐘，這金印也是當場粉碎！這種「出廠履歷死鎖」的極致變態認證，是現代防範 CI/CD 流水線上駭客偷偷塞毒籤的最強無敵神防線！)
C. Running a comprehensive Penetration Test before release. (發揮白帽大隊來當死士拿鐵鎚去敲這艘鐵船找洞？這確實也是好事，但在這個題目的重點裡，我們不是想找鐵船有沒有漏洞！我們是要證明【這鐵船真的是當初那張圖紙造出來的，中途沒被換成假貨 (Provenance and integrity)】。這兩件事南轅北轍)
D. Encrypting the entire source code repository with AES-256. (即便你把藏寶圖用密碼鎖死在全天下最硬的保險箱裡！這也無法保證「從保險箱拿出圖紙，到圖紙變成鐵船」的途中，這條傳送帶沒有被土匪加上大便！你保住了圖紙的機密性，但 SLSA 要證明的是流水線產出物的真實性，這完全是答非所問)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是 Google 提出的 **SLSA (Supply chain Levels for Software Artifacts)** 安全框架防範供應鏈攻擊 (如 SolarWinds) 的核心機制。
    *   **SLSA 的目標：** 抵抗 CI/CD pipeline 中可能發生的篡改。例如：防止惡意開發者繞過原始碼管控，直接上傳惡意的編譯結果 (Artifact) 到映像檔庫；或防止駭客入侵 CI 伺服器，在編譯時 (Build Time) 偷偷注入惡意程式碼。
    *   **核心技術 (Provenance & Code Signing)：**
        *   **Provenance (出處/來源證明)：** 是一份 Metadata (中繼資料)，詳細記錄了 Artifact 是由什麼 Source Code (Commit SHA)，在哪一個 Build Environment (例如 GitHub Actions 的特定 Runner)，使用了哪些依賴套件建置而成的。
        *   **署名綁定 (Cryptographic Binding)：** SLSA Level 2 及以上要求這份 Provenance 必須由建置環境 (Build Service) 自動進行**數位簽章 (Digital Signature)**。通常結合如 Sigstore、Cosign 等無金鑰 (Keyless) 簽章技術。
        *   **結果：** 當 Kubernetes 要部署這個 Container Image 時，K8s 上的 Admission Controller 會驗證這個簽章與 Provenance。如果驗章失敗，代表這個 Image 可能是駭客從外部私自上傳的，系統將拒絕部署。

#### **11. A developer copies a 50-line algorithm from a popular coding forum (like Stack Overflow) directly into the company's proprietary trading software. The developer did not check the licensing terms of the snippet or understand exactly how the algorithm allocates memory. What are the two primary supply chain risks introduced by this action?**
**(一名急著交差的爛泥小工匠，為了打造出皇城裡最值錢、能預測天下萬物漲跌的『超級發大財算盤 (proprietary trading software)』。這小工匠懶得自己發明齒輪，居然跑去城外專門收留流浪乞丐跟瘋子的『堆高高垃圾山 (Stack Overflow)』！他從路邊隨手撿了一個『發著金光的 50 圈小齒輪 (50-line algorithm)』，連看都不看這齒輪是哪個朝代的和尚丟的、有沒付錢 (did not check licensing terms)、甚至連它會不會自己把皇宮的錢漏光都不知道 (understand how it allocates memory)，就直接塞進了皇城最高機密的發大財算盤裡！請問，這小工匠這手『垃圾山撿寶直接拿來用』的白癡行徑，替這價值連城的算盤引來了哪兩隻在背後冷笑、隨時要讓皇城破產的終極死神 (two primary supply chain risks)？)**
A. Increased application performance and reduced infrastructure costs. (這哪叫風險，這叫天上掉黃金白日夢發大財。我們現在是在問：他沒看說明書就去垃圾堆撿破爛回來裝，會有什麼死法，絕不是會讓他升官發財)
B. Potential Intellectual Property (IP) / Licensing infringement and the introduction of unvetted security vulnerabilities or malicious code. (這就是名震四海、讓所有企業法務跟安防太監同時腦溢血暴斃的：【『雙殺滅門大慘案：天價版權官司索命 (Licensing infringement) / 與引狼入室之千古毒蟲附體 (security vulnerabilities or malicious code)！』】。這隻懶惰的工匠犯下了開源供應鏈的兩條死罪！第一罪：你這爛算盤可是皇城用來賺百億兩黃金的商業閉源兵器！但這小齒輪如果原本是那個瘋老頭用 GPL 授權放出來的，只要你一接上去，這瘋老頭就有權利衝進皇宮，要求你把整座皇宮的藍圖免費攤在陽光下 (IP 侵權與 Copyleft 污染)，直接賠到破產！第二罪：這小齒輪是你在垃圾山撿的！裡面極度可能埋藏著能在一瞬間偷走所有國庫黃金的終極記憶體爆炸符號 (Buffer Overflow)！甚至這更本是西域刺客故意丟在路邊等你撿的木馬程式 (Malicious code)！這兩把懸在頭上的達摩克利斯之劍，將皇城原本堅不可摧的防線瞬間炸碎！)
C. The code will automatically be deleted by the compiler, causing build failures. (編譯器是翻譯官，它只負責把火星文翻譯成給電腦懂的神諭。它才不管這段字是不是你從垃圾堆撿來的，它只看這字有沒有寫錯文法。如果是寫對文法的惡意毒藥，編譯器照樣順利翻譯給你喝，它並不會自動把它刪掉)
D. The company's servers will immediately be targeted by a DDoS attack. (DDos 是外面的人瘋狂用大石頭砸你的大門。你內部的工匠塞了一根毒骨頭在自家藍圖裡，這是慢性病與後門，不代表明天就會有十萬大軍來砸門，兩者的觸發點不相干)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這個情境涵蓋了 **開源軟體使用 (OSS Usage) 的兩大核心風險：法遵風險 (Compliance/Legal Risk) 與 安全風險 (Security Risk)。**
    *   **風險一：法遵與智財權 (Legal/IP Risk)：** Stack Overflow 上的程式碼片段通常有預設的授權 (例如 CC BY-SA)。如果這段演算法具備高度原創性，未經宣告就用於專利/商業軟體，競爭對手或原作者可以發起著作權侵權訴訟，甚至引發 Copyleft 傳染條款的悲劇。
    *   **風險二：未經審核的漏洞 (Security/Vulnerability Risk)：** 許多網路論壇上的「速成解答 (Quick Fixes)」是為了讓功能快速跑起來而寫的，根本沒有考慮過邊界檢查 (Boundary checking) 或記憶體安全。直接複製貼上，形同繞過了公司內部開發的安全編碼標準 (Secure Coding Standard)，這極可能引入 Buffer Overflow 或 SQL Injection 等高危漏洞。

#### **12. When evaluating a potential third-party software vendor, an organization requests the vendor's incident response plan and their historical track record of patching vulnerabilities (Mean Time to Repair - MTTR). What specific aspect of the vendor's security posture is the organization trying to assess?**
**(一名見過無數世面的皇城總管大爺，正坐在談判桌上，審查一家想接下皇宮幾億兩銀子外包案的新進大商行 (potential third-party software vendor)。總管大爺不要看他們家有幾座金山銀山，他只冷冷地丟出兩份考卷：第一，把你們家失火時候的【『逃生救命演練連環畫 (incident response plan)』】拿出來！第二，告訴老夫，你們過去這三年，每次被人發現金庫破了個洞，你們【『平均花了是兩個時辰還是三個月才把那破洞補起來的補天計時表 (historical track record of patching - MTTR)』】！請問，總管大爺問這兩個一針見血、招招致命的問題，他到底是在看這家商行的什麼【底牌 (specific aspect of security posture)】？)**
A. The vendor's financial stability and revenue growth. (這家商行就算富可敵國，每天賺幾千斤黃金，但如果他發現金庫破洞卻花了半年都不去補，那他賺再多錢也會很快被駭客搬空！總管問的是技術活，不是查他的財務報表)
B. The vendor's UI/UX design capabilities. (查別人怎麼救火和怎麼修補城牆破洞，這跟他們的裝備設計得好不好看、用起來順不順手 (UI/UX) 完全是八竿子打不著的事！這是生死存亡之際的防禦姿態，不是選美大會)
C. The vendor's operational resilience and their commitment to ongoing security maintenance and transparency. (這就是名震四海、專打紙老虎的：【『生死關頭防禦真章大檢驗：看透其營運韌性 (Operational resilience) / 與對安全維護的終極承諾 (commitment to maintenance and transparency)！』】。總管大爺深知資安界的一條千古鐵律：【『天下沒有防不勝防的城牆！被攻破是遲早的事 (Assume Breach)！』】。既然遲早會被攻破，那這家商行的實力跟價值，就不是取決於他平常吹牛自己有多安全。而是取決於當【第一隻白蟻侵入木樑、當第一滴血濺出的那一個時辰內】！這家商行有沒有一套已經演武過幾千遍的【救命指南 (IR Plan) 】能光速止血？這家商行會不會為了面子而掩蓋災情 (Transparency)？當這破洞出現時，他的工匠是不是有能力在黃金 24 小時內把膏藥貼上去，還是擺爛不管拖了三個月 (MTTR)？唯有能在逆風的爛泥坑裡，快速爬起來並補好傷口的供應商，才能與皇城共存亡！這叫韌性 (Resilience)！)
D. The vendor's ability to conduct White-Box penetration testing. (請別人來自己家測漏洞是為了找出哪裡壞了。而現在總管大爺在問的是：當你這家大商行【已經被人發現你哪裡壞了的時候，你到底有病會不會治、多久治的好？】。這不是測不測的問題，這是事後修補與危機處理的能力)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是 **第三方風險管理 (TPRM/SCRM)** 在盡職調查 (Due Diligence) 階段中最核心的評估指標之一：**營運韌性 (Operational Resilience) 與持續改進的承諾**。
    *   **評估思維的轉變：** 過去的供應商評估只看 "你現在用了什麼防火牆"。現在的安全標準 (如 Zero Trust 框架的 Assume Breach 理論) 承認，沒有完美的軟體，供應商一定有漏洞。
    *   **MTTR (平均修復時間) 的意義：** Mean Time to Repair/Remediate 揭露了供應商防禦的 "真實肌肉"。如果一個廠商的 MTTR 長達 6 個月，這代表該供應商的維護文化極度惡劣 (Technical Debt 高或 Security 優先級低)。在採用這家產品後，如果爆發 0-day 漏洞，你的組織將會有長達半年的空窗期暴露在被攻擊的風險中。
    *   **IR Plan 的意義：** 評估供應商在真正遭受勒索軟體或資料外洩時，是否有一套成熟的溝通機制能在 SLA 規定的短時間內通報客戶 (Transparency)，這是保護你自家企業合規性 (如 GDPR 的 72 小時通報限制) 的防火牆。
