# 第四套全真模擬試題 (Exam 4) - 答案與詳解本
## 領域 4：安全的軟體架構與設計 (Secure Software Architecture and Design) (18題) - Part 1 (Q1-Q6)

---

#### **1. During the architectural design phase of a new microservices-based application, the security team decides to implement a central Identity Provider (IdP) and an API Gateway. All external client requests must pass through the API Gateway, which validates an OAuth 2.0 JWT (JSON Web Token) before routing the request to any internal microservice. What specific security design pattern is being applied here to manage access control efficiently?**
**(一支精銳大軍正在畫一張『碎鑽級微服務大商城 (microservices-based app)』的建築草圖。安防總管大筆一揮，在大門口外建了一座『天下總兵馬通行大檢驗門 (API Gateway)』，旁邊還配了一座『御用意旨身分神壇 (IdP)』。總管下令：『聽好！全天下老百姓要進我們商城買東西，【所有的手推車，必須、絕對、只能從這個唯一的大檢驗門推進來 (must pass through the API Gateway)】！而且這個大門上的守衛，會拿著放大鏡檢查每個人脖子上的那張用 OAuth 2.0 寫的《JWT 魔法通關符》。如果符是真的，守衛才會幫你指路，讓你走到後面的小碎鑽店鋪去！』請問！在軟體架構兵法書上，這種『把所有安檢火力全部集中在一個大門口』的高能陣法，稱之為何種經典模式？)**
A. The Strangler Fig Pattern (絞殺榕模式是用來慢慢把舊系統的血吸光、新系統長大的過渡淘汰兵法，跟集中火力驗證身分無關)
B. The Singleton Pattern (單例模式是確保全天下只有一個玉皇大帝物件存在的程式設計模式，跟網路存取大門無關)
C. The API Gateway / Federated Identity Pattern (Single Point of Entry) (這就是名震當代微服務架構的最強大門防禦陣型：【『總 API 閘道器 / 單一入口大咽喉防禦模式 (API Gateway / Single Point of Entry)』】！這陣法的精妙之處在於：如果你的商城有 200 家小店鋪 (微服務)。你不用逼這 200 家小店鋪的掌櫃都去學怎麼驗證 JWT 神符。你只要在商城【唯一的大門口 (Single Point)】擺上最精銳的禁衛軍。這群禁衛軍幫你擋下所有沒有帶神符的刁民！然後才把好人放進商城。這就是『安控機制統一集中化』之美！)
D. The Circuit Breaker Pattern (斷路器模式是當後面的小店鋪被火燒掉時，大門口自動掛上「本店今日休業」牌子，避免排隊人潮把商城踩垮的容錯陣法，主治高可用性，不是驗證身分)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是現代微服務架構 (Microservices) 中最典型的 **安全設計模式 (Security Design Pattern)**。
    *   **痛點：** 在分散式架構中，如果不使用 Gateway，客戶端必須直接打給 50 個不同的後端微服務。這意味著這 50 個微服務都需要各自撰寫 JWT 解析、CORS 設定、Rate Limiting 邏輯。這產生了巨大的安全負擔與漏洞擴散風險。
    *   **API Gateway (Single Point of Entry) 的優勢：** 它實現了 **「特權 / 機制經濟 (Economy of Mechanism)」** 與 **「集中控制 (Centralized Control)」** 的資安原則。API Gateway 作為所有 Inbound Traffic (內部流量) 的唯一咽喉 (Choke Point)。它能統一執行：
        1. JWT Token Validation (身分驗證)
        2. SSL Termination (解密 HTTPS)
        3. WAF 阻擋 SQLi
    *   這樣後端的微服務就不用再去處理這些繁雜的安控，可以專心處理業務邏輯。

#### **2. A development team is designing a highly secure voting application. They identify a critical threat: a malicious database administrator (DBA) could directly alter the vote counts in the backend database. To mitigate this specific threat at the architectural level, they mandate that all votes must be digitally signed by the voter's client application before transmission, and the backend tally service will only count votes with valid signatures. Which element of the STRIDE model does this architectural control directly address?**
**(一支準備幫助朝廷舉辦『天下大選 (voting application)』的工匠大隊，在畫設計圖時發現了一個能讓國家直接覆滅的恐怖黑洞：【『那個拿著金庫鑰匙、掌管存放選票地下室的貪污大總管 (malicious DBA)！他居然可以半夜偷偷打開地下室，直接用立可白把皇帝的選票從十萬改成一萬 (directly alter the vote counts)！』】。為了防範這個擁有最高權力的大內鬼，工匠在架構圖上加上了一道死神也破解不了的陣法：【『從今以後，老百姓在家裡投完票，這張選票在離開他家門口前，必須親手用他的「微縮滴血大印章」蓋上數位簽名 (digitally signed by client)。等這張票送到地下室時，算票的機器只認這個血手印！如果大總管半夜去偷改選票數字，這血手印就會瞬間玉石俱焚爆裂，這張票直接作廢！』】。請問，這套用血手印防塗改的架構，是為了精準刺殺微軟 STRIDE 威脅兵法裡的哪一隻惡魔？)**
A. Spoofing (假冒是指小兵穿上將軍的衣服騙人。數位簽章也能防 Spoofing，但本題的重點是防 DBA "偷改數字"，而不是防 DBA 假裝自己是老百姓投票)
B. Information Disclosure (資訊洩漏是 DBA 把老百姓投給誰的秘密賣給報社。這題的血手印只防塗改，如果沒做欄位加密，DBA 還是能看到選票內容，這控制防不了洩密)
C. Denial of Service (阻斷服務是 DBA 把庫房炸了讓大家都不能投票，血手印防不了炸金庫)
D. Tampering (這就是 STRIDE 六大魔王中，專門在半夜偷改帳本、在水井裡下毒的：【『【『惡意竄改與毀滅完整性大魔王 (Tampering)』】！』】這道防線精準地使用了【非對稱加密之數位簽章 (Digital Signature)】。數位簽章的最大神效就是保障資料的「完整性 (Integrity)」。只要有任何人 (即便他是擁有資料庫 Root 權限的神仙 DBA)，敢動這張選票上的一個小數點！那這個簽章的 Hash 值就會徹底崩潰對不上。算票機器會立刻發現這票是被竄改過的垃圾而丟棄。這完美防堵了高階特權人士竄改資料的威脅！)

*   **正確答案 / Correct Answer：D**
*   **[解析邏輯]**
    *   **為何 D 是最佳選擇：** **「竄改 (Tampering)」** 在 STRIDE 中對應的是破壞 **「完整性 (Integrity)」**。
    *   **威脅場景 (Threat Scenario)：** 內部威脅 (Insider Threat) 中的特權使用者 (Privileged User) 濫用。DBA (資料庫管理員) 擁有直接對資料庫下達 `UPDATE votes SET candidate='Attacker' WHERE id=123;` 的能力。傳統的應用程式登入驗證 (Authentication) 根本擋不住 DBA 的直接存取。
    *   **架構層級的緩解 (Mitigation at Architecture Level)：** 為了防範這點，必須實施 **"Client-Side Digital Signatures (客戶端數位簽章)"**。
        *   因為簽章的「私鑰 (Private Key)」只存在於使用者的手機/電腦裡。
        *   當 DBA 試圖修改資料庫裡的選票時，他會改變選票的內容。但因為 DBA 手上沒有使用者的私鑰，他無法重新產生一份符合這張新選票的合法簽章。
        *   後端的驗票邏輯 (Tally Service) 只要看見簽章破裂，就會判定這張票遭到 **Tampering (竄改)** 而拒絕計票，完美守住了資料的完整性。

#### **3. You are conducting an architecture review of a multi-tier web application. You notice that the web server (Tier 1) connects directly to the backend database server (Tier 3) without passing through an application logic tier (Tier 2). Furthermore, the web server is placed in the DMZ. What is the fundamental security flaw in this architecture?**
**(你身為朝廷派來的王牌建城風水巡視官。當你視察一座號稱有『三層樓高』的大商城 (multi-tier application) 時。你差點沒被這張蠢到極點的風水圖給氣得吐血！你發現：這座商城那扇直接面著大街、每天給形形色色的乞丐跟強盜進進出出的『第一層接客大廳 (web server in DMZ)』。居然！居然在它的櫃檯底下，直接挖了一道暢通無阻、直達皇宮最深處那個『第三層裝滿黃金與機密卷宗大金庫 (Tier 3 database server)』的地道！中間完全沒有派任何管家或護衛階層 (Tier 2) 去盤問檢查！請問，這種『城門大廳直通老爺金庫』的智障風水陣，犯了哪一條會讓整座城被瞬間屠滅的兵家大忌？)**
A. It implements Defense in Depth too aggressively. (如果大廳直通金庫這叫縱深防禦？這叫開門揖盜、引狼入室！這根本沒有深度可言)
B. It exposes the database directly to a compromised web server in the DMZ, lacking a necessary logical boundary and separation of concerns. (這就是一針見血戳破這個智障風水圖死穴的宣判：【『這就是把裝滿黃金的無價大金庫，直接脫光衣服暴露在隨時會被敵軍攻陷的最前線大廳砲火下 (exposes the database to a compromised web server in DMZ)！徹底喪失了那名為《邏輯護城河大結界》與《各司其職分層把關大陣法》的偉大屏障 (lacking logical boundary and separation of concerns)！』】。你想想！DMZ (非軍事區) 就是個最容易被敵軍破門而入的火藥包。一旦第一層大廳的守衛被殺了 (Web Server 被駭)。這個駭客走到櫃檯後，發現居然有一條直通金庫的地道 (port 3306/1433 沒被擋住)！他連腦袋都不用動，直接順著地道進去就把金庫搬空了！這就是缺乏安全邊界的恐怖下場！)
C. It requires too much memory to run three tiers. (三層架構是為了安全跟效能，記憶體花費根本不是安防巡視官在乎的重點，更何況這題根本少蓋了一層 Tier 2)
D. The web server cannot use HTTPS in the DMZ. (DMZ 區的 Web 伺服器本來就是裝 HTTPS 憑證對外接客的最佳地點，這選項完全是在胡扯)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是評估 **N-Tier (多層式) 架構** 與 **網路區隔 (Network Segmentation)** 時最常見的致命缺陷 (Architectural Flaw)。
    *   **三層式架構 (3-Tier Architecture) 的標準防禦縱深模型：**
        1.  **Tier 1 (Web / Presentation Tier)：** 放在 DMZ (非軍事區)。面對 Public Internet。最容易被攻陷。
        2.  **Tier 2 (App / Logic Tier)：** 放在 Internal Network (內網)。處理業務邏輯。只允許來自 Tier 1 的 Request。
        3.  **Tier 3 (Database / Data Tier)：** 放在高度保護的 Restricted VLAN (極機密內網)。【絕對、絕對、絕對】不允許 Tier 1 (DMZ) 直接連線到 Tier 3。它只能接收來自 Tier 2 的連線。
    *   **這題的架構缺陷：** Web Server (Tier 1) 直接對接 Database (Tier 3)。這破壞了**關注點分離 (Separation of Concerns)** 與**縱深防禦 (Defense in Depth)**。
        *   如果 Web Server 被駭客透過 RCE (例如 Apache 漏洞) 攻陷並取得 Shell。
        *   因為 Web 到 DB 的網路是通的 (Firewall rule allows port 1433/3306)。駭客可以直接從這台中繼機 (Web Server) 對資料庫發動攻擊或傾印資料。中間沒有 App 邏輯層來攔截惡意的行為。

#### **4. A cloud architect is designing a system that processes highly sensitive credit card transactions. To isolate the processing environment, they place the payment processing virtual machines (VMs) in a dedicated Virtual Private Cloud (VPC) subnet that has NO route to the public Internet (no Internet Gateway). They communicate with the frontend web servers via a heavily firewalled internal load balancer. What architectural security concept does this highly restricted subnet represent?**
**(一位在雲端上畫著太極八卦陣的雲遊仙人 (cloud architect)。為了保護一座專門熔煉全天下最敏感金元寶（信用卡交易）的煉金爐。仙人使出了一招名為「畫地為牢」的終極大結界！他將這幾台煉金爐 (processing VMs) 扔進一個名為『絕對封死之幽冥虛空子網域 (dedicated VPC subnet)』！這個幽冥空間恐怖到了極點：【它完全沒有跟外面大千世界（網際網路）相連的任意門 (NO route to the public Internet)！連一隻蒼蠅都飛不出去！】。這群煉金爐如果肚子餓想吃東西，只能透過一台由重兵把守、僅限內部通行的送飯小推車 (firewalled internal load balancer) 拿到前面的接客大廳丟進來的原料！請問，這種把最重要的核心，死死封印在一個不見天日的無氧空間裡的佈陣兵法，在西洋兵書上稱作什麼？)**
A. An Enclave (or Secure Execution Environment) (這就是名震當代、能讓駭客望門興嘆、絕望到想哭的：【『神聖不可侵犯之絕對隔離大飛地 / 孤島死獄結界陣 (Enclave / Secure Execution Environment)』】！這道結界的奧義在於：哪怕駭客把前面的接客大廳給炸了。當駭客想順藤摸瓜摸進這個煉金爐時，會發現這個虛空結界根本【沒有對外的門】。就算駭客在煉金爐裡種了木馬病毒，這隻木馬也【絕對無法向外面的駭客母艦發送任何信號 (Data Exfiltration/C&C 通訊全部失敗)】！因為這個空間物理上就是個沒有網路出口的瞎子孤島！這是保護極機密資料最強悍的網路架構堡壘！)
B. A Honeypot (蜜罐是一個放滿假黃金來誘騙小偷進來抓人的陷阱大廳。這題是在保護真正的煉金爐，不是要騙人)
C. A Content Delivery Network (CDN) (CDN 是為了讓圖片跑得快，在全球各地建立的幾千個任意門放送塔。這跟把金庫封死在沒有門的黑暗虛空完全是背道而馳的概念)
D. A Reverse Proxy (反向代理是放在大門口幫你擋子彈跟檢查包裹的守衛，它本身並不是這個被封死的幽冥空間體)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **「Enclave (飛地 / 隔離區)」** 或 **「Secure Execution Environment (安全執行環境)」** 在網路架構與雲端架構中的概念。
    *   **定義：** 一個 Enclave 是一個被嚴格隔離、獨立的網路或運算區域。它的設計初衷就是為了處理極度敏感的資料 (例如 PCI-DSS 制定的 Cardholder Data Environment, CDE)。
    *   **技術特徵：**
        *   **No Egress/Ingress to Public Internet：** 沒有 Internet Gateway (IGW) 或 NAT Gateway。它無法連上網際網路，網際網路也連不到它。
        *   **嚴格的控制點 (Choke Point)：** 只能透過嚴格設定規則的 Internal Load Balancer 或 Bastion Host (跳板機) 進行內部通訊。
    *   **安全防護力：** 即使該 Enclave 內部的伺服器突然中了一隻 Zero-day 病毒。這隻病毒也無法向外部的 C&C Server 建立反向連線 (Reverse Shell)，更無法把信用卡號偷傳到外部 (Data Exfiltration)；因為網路路由 (Route Table) 根本不通。這就是硬體/網路級別的「圍堵 (Containment)」。

#### **5. When performing Threat Modeling using the STRIDE methodology, during which specific phase of the Secure Software Development Lifecycle (SSDLC) should the initial Data Flow Diagram (DFD) ideally be created and analyzed to maximize its cost-effectiveness?**
**(當帝國兵工廠準備舉行一場盛大無比、旨在將未來的災難扼殺於搖籃之中的【『STRIDE 威脅大剖析降魔火把法會 (Threat Modeling)』】時。大將軍手裡拿著那張畫滿了城池水管跟護城河的『生命水源大風水圖 (Data Flow Diagram, DFD)』！大將軍環顧四周的將領，嚴肅地問道：『諸位！我們必須把「造車成本」壓到最低。為了在這張圖上抓出那群企圖在水管裡下毒的魔鬼，這場降魔法會，【最完美、性價比最高、也是唯一能阻止我們傾家蕩產的黃金舉辦時機】，到底是在這漫長的造車流水線歲月裡的哪一個良辰吉時 (specific phase of the SSDLC)？』)**
A. During the final Penetration Testing phase. (老天！這是在車子都已經造好、馬上要賣掉出城前，才請刺客來用大炮轟。如果在這時候才拿水管圖出來找魔鬼，就算找到了，你也得把整座城拆了重接水管！這叫傾家蕩產，哪來的 cost-effective 成本效益可言？)
B. During the Architecture and Design phase (before coding begins). (這就是那名傳千古、能救下帝國千百萬兩黃金的唯一正解良辰：【『就在那只用鉛筆在白紙上畫房子的【神聖空想與架構大設計期 (Architecture and Design phase)】！』】。這兵法教導我們：在牆壁還沒糊上水泥、連一根鐵釘都還沒敲下去 (before coding begins) 的時候！你就對著這張紙上的水管圖發動攻擊。抓出漏洞後，你只需要浪費【一塊橡皮擦跟三秒鐘的口水】，就能把水管重新畫過！這時候修補城池死穴的成本，逼近於【絕對零度】！這就是左移大戰略 (Shift-Left) 追求極致性價比的最高潮！)
C. Immediately after the Incident Response team detects a breach. (這是敵軍已經打進城裡殺紅眼、開始四處搶劫時才做的事。這是在寫驗屍報告找死因，早就血本無歸了，太晚太晚了！)
D. During the Decommissioning phase. (在把報廢車子丟進焚化爐時，才把設計圖拿出來看他有什麼設計缺陷？這是在對屍體作法，毫無任何意義)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「威脅建模 (Threat Modeling)」的最佳介入時機是「架構與設計階段 (Architecture and Design Phase)」**。
    *   **DFD (Data Flow Diagram) 的本質：** 威脅建模的第一步是釐清系統架構，畫出 DFD (資料流程圖)。
    *   **Shift-Left 成本曲線：**
        *   在**設計階段 (Architecture Stage)** 發現一個設計缺陷 (例如：兩個系統之間忘記設計互相驗證的加密通道)，修改成本極低。架構師只需要在白板上重畫一條線，然後把需求加進去。
        *   如果在**上線測試階段 (Penetration Testing, 延遲抓 Bug)** 才發現這個架構缺陷。團隊必須花三個禮拜重寫底層通訊模組，甚至還要改 Database Schema，成本呈指數型暴增 100 倍以上。
    *   因此，微軟的 SDL (Security Development Lifecycle) 強烈規範：Threat Modeling 必須在寫下第一行 Code 之前進行。

#### **6. A software architect is designing a system where users can upload profile pictures. The architect designs the application to automatically strip all EXIF metadata (e.g., GPS coordinates, camera model) from the uploaded image files before saving them to the storage bucket. What specific type of privacy design strategy is this?**
**(一名心地極度善良又精通隱遁之術的神鬼架構師。他在設計這座『天下客棧大臉盆 (profile pictures app)』時，偷偷在裝洗臉水的盆子底部加裝了一套神奇的『過濾大陣法』！當客人在這盆子裡洗臉、留下他們的面容倒影時 (upload image)。這陣法會【自動、無情且精準地，把這張倒影背後偷偷黏著的【那張寫著『你家就住在長安街三段二號』的恐怖追蹤黃符紙 (automatically strip all EXIF metadata e.g., GPS coordinates)】】，在上傳金庫的最前一秒，直接在半空中給燒得連灰都不剩！確保金庫裡只留下一張單純的臉，而沒有任何可以被刺客拿去尋仇的蛛絲馬跡！請問，這種『不該留的就趁早斬草除根』的菩薩心腸隱私陣法，名喚為何？)**
A. Data Masking (資料遮罩是在顯示給小二看的時候打馬賽克，金庫裡還是有那張追蹤黃符。而這題是直接把黃符給燒了解體了，兩者手段境界不同)
B. Data Minimization (Stripping unnecessary data) (這就是《GDPR大隱私法典》與《Privacy by Design》裡最至高無上的第一保命鐵律：【『非必要，勿囤藏之【極限資料最小化大斷捨離法則 (Data Minimization)】』】！這兵法告訴我們：最安全的秘密，就是你『根本沒有擁有這個秘密』！既然我們只是要客人的臉孔 (大頭貼)。那我們就絕對！沒有任何理由！去保存那張被手機相機偷偷塞進去的【GPS 定位座標、拍攝時間、手機型號 (EXIF data)】。在第一時間直接把它剝除 (Stripping) 肉身消滅，未來就算金庫被炸開，駭客也查不到客人住哪！這就是最徹底的防護術！)
C. Encryption Data-in-Transit (這是幫照片穿防彈衣飛鴿傳書，但照片裡的黃符紙依然完好無缺傳到了金庫)
D. Database Sharding (分片是把太大的金庫切成三個小金庫來放黃金，跟刮除臉頰上的毒藥黃符完全是不沾邊的兩回事)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「資料最小化 (Data Minimization)」** 是隱私保護設計 (Privacy by Design, PbD) 的核心策略之一。
    *   **EXIF Metadata 的威脅：** 當使用者用手機拍大頭貼時，照片檔案 (JPEG/HEIC) 預設會夾帶大量的 EXIF 屬性，包含精準的經緯度 (GPS Locality)。過去有非常多案例是公眾人物發布照片，結果被跟蹤狂從照片的 EXIF 找出真實住址。
    *   **Data Minimization 的實踐：** 在架構設計上，因為應用程式的業務邏輯 (Business Need) 只是「顯示一張圖片」，完全不需要知道使用者的 GPS 位置。因此，最安全的做法就是在伺服器接收到圖檔、存入 AWS S3 之前，利用影像處理函式庫 (如 ImageMagick) 強制將所有的 Metadata 剝除 (Strip/Scrub)。
    *   這種「在源頭直接消滅非必要敏感數據」的策略，遠比存下來再想辦法加密或遮罩來得更安全、更沒有包袱。
