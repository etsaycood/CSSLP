# 第三套全真模擬試題 (Exam 3) - 答案與詳解本
## 領域 4：安全的軟體架構與設計 (Secure Software Architecture and Design) (18題) - Part 1 (Q1-Q9)

---

#### **1. A senior security architect is designing a high-security microservices-based application for processing classified military data. The architect mandates a Zero Trust capability where every single API call between the internal microservices (e.g., the User Service calling the Billing Service) must be explicitly authenticated and cryptographically secured using mutual TLS (mTLS). They state developers should NOT have to write this complex mTLS logic and certificate rotation code into every single application container. What architectural pattern is BEST suited to automatically inject and enforce this requirement infrastructure-wide?**
**(一名頂尖的資安大祭司，正在為處理軍方極機密情資的『超級微服務架構大網 (microservices-based application)』繪製防護陣圖。祭司下了一道鐵血無情的『零信任防禦 (Zero Trust)』死結界命令：【在我們這座微服務大皇宮裡面，即使是自己人跟自己人講話 (例如：管人事的小兵跑去跟管帳房的小兵借錢 User Service calling Billing Service)！他們之間互傳的每一句 API 悄悄話，都【絕對必須】經過極度嚴苛的身分盤查，並且強制套上『雙向 TLS 互相驗證加密大鎖 (mutual TLS, mTLS)』！】。但是！祭司又非常體恤那些底層寫程式的苦命猴子，他說：『我不希望看到這群笨蛋工程師，還要在他們寫的每一支微服務程式碼裡面，痛苦地手刻那些複雜要命的 mTLS 加密邏輯跟天天換憑證的囉唆程式碼！』。請問，為了能【全自動地、神不知鬼不覺地將這套 mTLS 加密防護罩，猶如寄生蟲般全面注射進並覆蓋整個微服務基礎設施大軍】，哪一種現代雲端架構大陣法是此情境下的最完美解答？)**
A. Deploy a centralized Web Application Firewall (WAF) in front of the Kubernetes cluster. (在 Kubernetes 城牆最外面架一台集中式的 WAF 破盾牌，這只能擋外人，管不到城牆內自己人講話)
B. Implement a Service Mesh (e.g., Istio, Linkerd) with sidecar proxies attached to every microservice container. (這就是威震現代雲端、專門發動零信任結界的終極大法陣：【全面導入『服務網格 (Service Mesh, 例如大名鼎鼎的 Istio 或 Linkerd)』！並利用那猶如影子保鑣般的『邊車代理小精靈 (sidecar proxies)』，死死貼附在每一個微服務的身上！】讓影子保鑣自動幫忙處理所有 mTLS 憑證與通訊加密，讓工程師完全不用寫半行加密代碼！)
C. Utilize an API Gateway at the perimeter of the cloud architecture. (在雲端邊界架設一個 API 大門神，同樣只能管進出，管不到城內互毆)
D. Mandate that all developers write a standardized internal authentication library using AES-256 for all traffic. (逼迫所有苦命猴子自己手寫一個 AES-256 的認證函式庫，這正是祭司明令禁止的笨方法)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「服務網格 (Service Mesh)」** 是雲端原生架構 (Cloud Native / Kubernetes) 中實現「零信任 (Zero Trust)」與「東西向流量加密 (East-West Traffic Encryption)」的黃金標準。
    *   在微服務架構中，如果幾百個服務彼此溝通都要自己寫 mTLS 憑證驗證，開發者會崩潰，而且憑證過期很難統一更換。
    *   **Service Mesh 的絕妙機制：** 它的核心觀念是 "Sidecar Placeholder (邊車模式)"。當一個微服務 (例如 User Service) 被部署時，Service Mesh 控制平面會自動在這個服務旁邊「偷偷塞進一個小小的 Proxy 代理伺服器 (Sidecar, 像是 Envoy)」。從此以後，微服務只要用最簡單的 HTTP 發送原始資料就好，旁邊的 Sidecar 保鑣會瞬間攔截這段資料，自動幫它掛上 mTLS 憑證加密，然後安全地射給另一個服務的 Sidecar 保鑣。這完美達成了「基礎設施級別強制加密 (infrastructure-wide limit)」，且「開發者完全無感 (decoupled from app logic)」。

#### **2. A software engineering team is building a decentralized peer-to-peer cryptocurrency exchange. To completely eliminate the risk of a single central authority unilaterally altering the transaction history, the architectural design explicitly mandates that the entire decentralized network must reach a mathematical consensus before any new block of transactions can be appended to the immutable, chronologically chained, distributed ledger. What fundamental cryptographic data structure defines this underlying architecture?**
**(一支瘋狂的地下工程師團隊，正在打造一座『不受地球上任何政府與銀行管轄的去中心化 P2P 地下加密貨幣兌換大錢莊』！為了徹徹底底、從物理法則上斬斷【某個自稱是中央老大的惡霸實體，可以仗著自己手握權力，隨便偷改過去某筆匯款紀錄中飽私囊】的死風險 (unilaterally altering the transaction history)。這座錢莊的造城圖紙上，刻下了最霸道的鐵律：『聽著！這片佈滿全球、幾萬台電腦組成的去中心化地下網路。每當有一箱新的買賣交易資料想被寫進歷史洪流前，【全網路幾萬台電腦必須一起出數學難題投票、達成絕對的數學共識大會師 (reach a mathematical consensus)】！只有通過了這個考驗，這箱新資料才能被掛載到那個永恆不滅、一旦寫死就無法回頭竄改、且每一塊磚頭都按照時間順序死死咬在一起的【分散式超級歷史大帳本 (immutable, chronologically chained, distributed ledger)】的最尾端！』請問，能夠支撐並定義這套猶如數位絕對真理般底層架構的【最根本密碼學資料結構陣法】，尊號為何？)**
A. A relational SQL database utilizing strict ACID (Atomicity, Consistency, Isolation, Durability) properties. (需要一個中央管理員的傳統 SQL 關聯大資料庫)
B. A NoSQL Key-Value Store optimized for eventual consistency. (這只是為了快一點但會偶爾不準的 NoSQL 記憶體大水桶)
C. A Blockchain architecture (utilizing cryptographic hashing linking). (這就是那震撼世界、猶如神聖歷史鎖鏈般、專砍中央集權狗頭的【區塊鏈大陣法 (Blockchain architecture, 依賴密碼學雜湊鎖鏈技術 linking)】！)
D. A centralized Git repository. (這只是中心化的程式碼倉庫)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 題目中充滿了區塊鏈 (Blockchain) 技術的核心關鍵字定義。
    *   "Decentralized peer-to-peer (去中心化分佈式 P2P 網路)"。
    *   "mathematical consensus (共識機制，如 Proof of Work 或是 Proof of Stake)"。
    *   "immutable (不可篡改的 / Write-Once, Read-Many)"。
    *   "chronologically chained distributed ledger (按時間順序利用 Cryptographic Hashing 連接的分佈式帳本/記帳結構)"。
    *   這完全描繪了區塊鏈架構的本質。區塊鏈之所以防竄改，是因為下一個區塊的標頭 (Header) 會包含上一個區塊的 Hash 雜湊值，形成一條死死咬住的鎖鏈 (Chain)。任何人想改十天前的交易數字，那天的 Hash 值就會變，導致後面所有的鎖鏈全部斷裂失效被全網拒絕。這是一種極致追求 Integrity (完整性) 的架構設計。

#### **3. An e-commerce platform's monolithic architecture has become too large to maintain, causing slow deployments. The architect decides to physically break the application apart so that the "Inventory Module," the "Shopping Cart Module," and the "Payment Processing Module" are entirely independent programs running in their own isolated Docker containers. They will now communicate exclusively through well-defined, lightweight RESTful web APIs over the network. What fundamental software architectural pattern has the team just adopted?**
**(一家超級網路商城的後台系統，因為當初蓋房子的時候圖個方便，把找庫存、買東西、結帳全部揉成一大坨比山還高、油膩不堪的『史萊姆單體屎山大怪獸 (monolithic architecture)』。現在這隻怪獸胖到走不動，每次要更新一行程式碼都得停機好幾個小時 (slow deployments)。所以，大刀闊斧的首席殺手架構師決定發動『大肢解術』！他把這坨大怪獸給殘忍地大卸八塊：讓原本的【找衣服庫存模塊】、【推購物車模塊】跟【刷卡收錢模塊】，通通活生生地被剝離出來！這些殘肢各自進化，變成了【完全獨立、自己養活自己、並且各自被關進小小的獨立 Docker 麻雀玻璃籠子裡 (isolated Docker containers) 的獨立小精靈軟體】！從今以後，如果購物車想跟刷卡機講話，它們不能再像以前一樣用手碰手，它們【必須且只能隔著籠子，透過網路線呼叫極度輕量簡單的 RESTful 網路 API 大聲喊叫來溝通 (communicate exclusively through well-defined APIs)】。請問，這支團隊把大怪獸肢解成一群獨立小妖精的偉大開刀手術，是沿用了哪一套風靡現代軟體界的基礎架構大陣法？)**
A. Service-Oriented Architecture (SOA) (那是上個世紀的老古董，這群老怪物身上背著沉重如山的企業匯流排 ESB，不是輕量級的)
B. Microservices Architecture (這就是現代雲端最崇拜、將天下打散成猶如滿天星斗般小巧精悍獨立部隊的【微服務大陣法 (Microservices Architecture)】！)
C. Client-Server Architecture (只是最基礎的手機連上伺服器主從架構)
D. Peer-to-Peer (P2P) Architecture (那是沒有老大、大家都在互相抓盜版電影的點對點架構)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這題考的是 **Microservices (微服務架構)** 的經典定義。
    *   相對於 Monolithic (單體架構 - 所有程式碼編譯在同一個 EXE 或 WAR 檔裡)，微服務將龐大的應用程式拆解成「一組微小、獨立運行 (independently deployable)、圍繞業務能力構建 (Inventory, Payment)」的小服務。
    *   關鍵特徵包含：1. 獨立的進程 (通常跑在獨立的 Docker container 裡)。 2. 使用「輕量級」的通訊協議 (如 REST API 或是 gRPC) 溝通。
    *   (重點區分：A 的 SOA "服務導向架構" 雖然也是拆分服務，但 SOA 通常依賴非常笨重集中式的 "Enterprise Service Bus (ESB)" 以及肥胖的 SOAP/XML 協議。現代看到使用 "Docker" 加上 "輕量級獨立佈署 REST APIs"，絕對是微服務架構的標準描述。)

#### **4. A company adopts an architectural design strategy conceptually built entirely on the premise of absolute paranoia: "Never trust, always verify." Regardless of whether an employee is sitting physically inside the heavily guarded corporate headquarters on the internal LAN, or working from a coffee shop in another country, every single attempt to access any corporate resource must dynamically evaluate the user's identity, the health and patch level of their device, and the context of the request before granting limited access. What is the name of this prevailing security architectural paradigm?**
**(一家企業為了活命，全面擁抱並皈依了一套猶如被害妄想症末期般的『終極偏執狂建城大戰略 (premise of absolute paranoia)』。這套戰略的唯一最高指導神諭只有六個字：「【絕對不信任任何人！永遠給我往死裡查！ (Never trust, always verify)】」。在這套陣法之中，【管你這名大兵現在是正舒舒服服地坐在被幾百支監視器和重裝甲防火牆死死保護的皇城內部大金庫旁邊 (inside internal LAN)】，還是你正在某個鳥不生蛋的海外路邊咖啡廳用免費 Wi-Fi 上網！這套系統根本不瞎認什麼所謂的 "內部安全網帶"。任何一隻你想伸向帝國金庫資源的狗手動作，系統都會在毫秒內，【猶如拿放大鏡看細胞一樣，動態且神經質地重新全身掃描確認你的靈魂身分 (identity)、嚴格盤查你手上拿的那把手機有沒有長病毒或有沒有打滿抗生素疫苗 (health and patch level of device)、並評估你現在此時此刻伸手的動機跟天候背景 (context of request)！】，全都檢查及格了，才像施捨一般給你開一點點的小洞權限 (granting limited access)。請問這套在現今資安界猶如神明般受人膜拜的最高防禦教派藍圖，尊號為何？)**
A. Defense in Depth (Layered Defense) (這只是在城牆外面多挖幾條護城河的一層包一層縱深防禦)
B. Single Sign-On (SSO) Federation (這只是讓你有一張特別身分證，刷一次就可以進很多道門的單一登入)
C. Zero Trust Architecture (ZTA) (這就是以『絕對偏執、抹殺內外網界線』聞名天下的最高境界：【零信任防禦大陣法 (Zero Trust Architecture, ZTA)】！)
D. Endpoint Detection and Response (EDR) (這只是裝在你電腦裡抓病毒的小精靈 EDR)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「零信任架構 (Zero Trust Architecture)」** 的核心神髓。
    *   過去的傳統防禦是 "Castle-and-Moat (護城河城堡模式)"：認為「外面 (Internet) 都是壞人，裡面 (Intranet/LAN) 都是自己人可以信任」。只要用 VPN 連進公司內網，你就擁有很大的破壞力。
    *   **Zero Trust (由 John Kindervag 提出) 完全打破了這個迷思**。它的核心教條就是：
        1.  **"Never Trust, Always Verify"** (永不信任，始終驗證)。
        2.  **網路位置不再代表信任度** (坐在辦公室裡跟坐在星巴克一樣，都被視為潛在威脅)。
        3.  每一次的存取資源請求，都必須進行嚴格的 **"動態情境評估 (Dynamic Context Evaluation)"** (你是不是本人？你的筆電防毒軟體有開嗎？你是不是突然從奈及利亞登入？)，完全符合題目中鉅細靡遺的病態盤查描述。

#### **5. An architect is applying the foundational security design principle of "Economy of Mechanism." During the design review of a new financial application's authentication module, they notice the developers have implemented three different custom authentication protocols, connected to four different identity providers, and added complex fallback logic if any step fails. The architect orders the team to rip out the complex logic and replace it with a single, universally standardized SAML 2.0 integration. What is the primary theoretical justification, based on the principle of "Economy of Mechanism," for doing this?**
**(一名精通古老安控兵法的架構大督軍，正嚴苛地揮舞著一條名為『機制經濟學大奧義 / 越簡單越保命之法 (Economy of Mechanism)』的審查皮鞭。他在巡視一座新建金融大殿的『驗明正身城門口 (authentication module)』時，差點沒氣得吐出幾十兩血！他赫然發現那群愛賣弄聰明的工程師們，居然在同一個城門口，喪心病狂地搭建了【三座自己拿泥巴捏出來的迷宮大門 (three different custom authentication protocols)、並且拜了四間不同廟宇的神明來驗身分 (four different identity providers)】，甚至還自己寫了一團如蜘蛛網般黏在一起、只要有一道門破了就會亂彈到另外一道門的終極複雜連環迷魂陣 (complex fallback logic)！大督軍勃然大怒，下令所有怪手馬上開進去！大刀闊斧把這種花俏的迷宮跟自創神功全部給我拆得片甲不留 (rip out the complex logic)！並且直接換上【全天下最無腦、最統一、如鋼鐵般實心的一套標準化 SAML 2.0 單一大鐵門】！請問大督軍若要用這條名震天下的『機制經濟學』祖師爺神諭來教訓這群工程師，他嘴裡念出的那句【為何越簡單越保命】的絕對理論真理，究竟是什麼？)**
A. SAML 2.0 is fundamentally unbreakable by modern quantum computers. (瞎扯說這套標準鐵門是用外星科技打造、連量子電腦都拆不散)
B. Complex, convoluted security designs inherently create more opportunities for critical bugs, configuration errors, and hidden vulnerabilities than simple, elegant, and standardized designs (KISS principle). (這就是千古不變的真理：【你那花俏、扭曲如蛇麻草般的複雜安防迷宮機關 (Complex designs)！其極致的複雜度，正是滋養那些『足以顛覆帝國之大臭蟲 (bugs)』、『白痴設定手滑失誤 (configuration errors)』以及『深藏不露之隱形致命死穴 (hidden vulnerabilities)』的最佳溫床！】只有採用那如刀劈斧削般簡單、優雅且天下統一的純粹大鋼門 (simple, elegant, testing designs, 也就是 KISS 保持簡單原則)，才是防禦出錯的極致之道！)
C. Keeping the mechanism simple makes it easier to pass the blame to the SAML provider if a breach occurs. (單純只是為了出事被駭客打穿時，方便把黑鍋全甩給那間賣 SAML 原廠的不要臉行為)
D. The economy of mechanism principle dictates that software should always use the cheapest open-source libraries available to save money. (誤把『Mechanism 經濟學』當成財務部用來『買最便宜的地攤貨省錢開銷』的財務名詞)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「機制經濟學 (Economy of Mechanism)」** 這是古典資安架構八大原則之一 (來自 1970 年代的 Saltzer and Schroeder)。它的核心思想跟金錢無關，它等同於現代常用的 **KISS 原則 (Keep It Simple, Stupid)**。
    *   **核心神髓：** 安全機制的設計應該盡可能地「簡單且體積小」。複雜度是資安最大的天敵。當你的身分驗證代碼寫得越複雜、if-else 判斷迴圈越多、依賴的外掛套件越雜，你那堆像義大利麵的程式碼裡，隱藏「邏輯漏洞 (Logic Flaws)」跟「設定錯誤」的機率就越高，駭客繞過去的破綻就越多。用一個經過全世界萬人捶打測試過的統一標準 (SAML)，絕對比你自己寫三個複雜備援系統要安全一百倍。

#### **6. A banking application's architectural design document explicitly dictates: "The code that dictates how the colorful user interface buttons are rendered on the screen MUST be physically and logically separated from the backend code that queries the secure SQL database for account balances." The developers are instructed to build this using a strict Model-View-Controller (MVC) software pattern. Which fundamental secure design principle is this software architecture primarily attempting to enforce?**
**(在那座莊嚴神聖的銀號大金庫的『建築骨架總施工圖 (architectural design document)』上。有一道絕對不可妥協的紅線命令：『聽好！那些負責在網頁表面上，雕花、上色、掛彩色燈籠去討好客人眼球的【華麗外皮選單操控機關程式碼 (User interface buttons code)】；跟那群躲在地底最深處，負責去那個神聖不可侵犯的大金庫裡，用死神鑰匙去挖出客人到底剩多少錢的【核子級後台資料庫大撈捕代碼 (backend code that queries secure SQL database)】。這兩坨東西，【在物理存在上、跟靈魂邏輯上，都絕對、死也不准被你們這群猴子給混寫攪拌在一起 (MUST be physically and logically separated)】！』。長老們拿著鞭子，逼迫所有的木匠，必須嚴格膜拜並遵從那名為『大切割之術：模型-視圖-控制器大陣法 (Model-View-Controller, MVC pattern)』來把程式給切成三塊獨立運轉的肉塊。請問這套殘忍剝離血肉架構的作法，正是在虔誠地實現哪一條最基礎的防禦切分設計大真理？)**
A. Fail-Safe Defaults (大門預設必須關上的失效安全鎖防禦)
B. Open Design (把設計圖公開給大家看也不怕被破關的開放設計神功)
C. Separation of Duties (那是管理人事流程，叫小王開保險箱、叫小李拿鑰匙的人員職責分離)
D. Separation of Domains / Separation of Concerns (Modularity) (這正是在斬斷所有程式碼的孽緣，將他們如同不同物種般隔絕的【領域大分治 / 關注點之絕對切割隔離大陣法 (Separation of Domains / Separation of Concerns)，也就是極致的『模組化 (Modularity)』神功】！)

*   **正確答案 / Correct Answer：D**
*   **[解析邏輯]**
    *   **為何 D 是最佳選擇：** **「關注點分離 (Separation of Concerns, SoC)」** 與 **「模組化 (Modularity / Separation of Domains)」**。
    *   在軟體架構學中，MVC (Model-View-Controller) 是實現 SoC 最經典的設計模式。
    *   **安全防禦價值：** 為什麼 UI (畫面) 不能跟 Database (資料庫) 寫在同一個檔案裡 (像以前很多新手寫 PHP 一樣)？因為如果寫在一起，當畫面的按鈕程式有漏洞 (例如 XSS)，駭客就能直接藉由這個檔案的高權限，順著藤摸瓜直接碰到旁邊的 SQL 查詢指令。
    *   如果我們嚴格實現 **"關注點分離"**，把 View (畫面) 丟在最前線且只給它極低的權限，Controller (邏輯控制器) 放在中間，Model (資料庫模型) 藏在深海裡。駭客就算打穿了畫面殼 (View)，接下來他還得面對一道嚴格界線清晰的 Controller 檢查關卡，才有可能碰到資料。這極大地限縮了漏洞的爆炸半徑。

#### **7. A cloud architect is designing a highly sensitive data processing pipeline. They require a specialized, physically isolated hardware appliance dedicated entirely to securely generating, storing, and managing the absolute highest-tier encryption root keys used by the enterprise. This device must be mathematically proven to be tamper-resistant, automatically zeroizing its memory if a physical intrusion is detected. What highly specialized hardware component MUST the architect include in the infrastructure design?**
**(一名頂尖的雲端大造物主，正在鋪設一條被列為國家極限機密的煉金數據大水管。在建城之際，這名造物主發出了緊急徵召令：他要求必須去神界黑市，花天價買來一個【極為特殊、與世隔絕、且如同物理性死牢保險箱般的純硬體大鐵盒裝置 (specialized, physically isolated hardware appliance)】！這個大鐵盒這輩子沒有別的用途，它活著唯一的宿命，就是【躲在最深處，瘋狂加密運算、並且死死抱住並私藏那些攸關整個超級大企業生死存亡的『至尊終極核武大鑰匙 (highest-tier encryption root keys)』！】。這台盒子還必須經過神明的數學認證，證明它具備『至死不屈的物理反叛防護金身 (tamper-resistant)』：只要這盒子一偵測到，有任何宵小拿著螺絲起子想強行撬開它的鐵皮，企圖偷走裡面的至尊神鑰，這台盒子就必須在千分之一秒內發動自毀系統！【用雷射發出死光，將自己腦海裡的記憶晶片體徹底燒毀蒸發成灰燼，一點渣都不留給敵人 (automatically zeroizing its memory)】！請問，這位見多識廣的雲端造物主，他所點名必須鑲嵌在上古大陣圖裡的這台變態級硬體大鐵盒，尊號為何？)**
A. A Trusted Platform Module (TPM) chip on every developer's laptop. (這只是每個人筆電主機板上那小小的、用來記微軟登入密碼的平民小晶片 TPM)
B. A Hardware Security Module (HSM). (這就是那威震全宇宙、各國政府拿來保護頂級機密、造價驚人且具備終極物理防爆自毀神諭的：【『無敵硬體安控保險箱大模組 (Hardware Security Module, HSM)』】！)
C. A dedicated Virtual Private Network (VPN) concentrator. (那只是一台用來讓大家連進公司內網打卡的 VPN 破閘道器)
D. A Web Application Firewall (WAF). (這只是一面架在門口幫忙檔幾發 XSS 爛子彈的 WAF 破盾牌防火牆)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「硬體安全模組 (Hardware Security Module, HSM)」**。
    *   在企業級架構與密碼學管理 (Key Management) 中，軟體永遠是不安全的。如果你把最高層級的根憑證私鑰 (Root CA Private Key) 存在 Windows 的 C 槽硬碟裡，駭客只要一個遠端木馬就能偷走。
    *   **HSM 是實體驗證設備 (Physical Appliance 或 Cloud HSM) 的最高頂點：** 它通常符合 FIPS 140-2 Level 3 甚至 Level 4 的變態級物理防護標準。它是一個被環氧樹脂死死封死的鐵盒子，專門做超高速加密運算跟藏鑰匙。
    *   **Tamper-resistant / Zeroization (防篡改/歸零毀滅)：** 這是 HSM 的招牌特技。一旦感測到電壓異常改變、溫度急遽變化 (有人倒液態氮想破解記憶體)、或者是盒子被鑽了個孔。HSM 就會立刻啟動 **"歸零 (Zeroization)"** 機制，把裡面的秘密瞬間刪個精光，寧為玉碎不為瓦全。 (註：A 的 TPM 也是硬體保護，但 TPM 只保護單台 Client 電腦，而 HSM 是保護 "整個企業最高級 Root Keys" 的大傢伙)。

#### **8. A design team is outlining the authorization logic for a new medical records system. The lead security architect enforces the following rule: "By absolute default, when a new doctor's account is created, they are implicitly denied access to ALL patient records. If they attempt to open a file, the system must definitively block them unless a specific, explicit rule has been mapped to their profile explicitly granting them 'Read' access to that specific ward." This design fundamentally embodies which core security principle?**
**(一支設計大隊正圍在沙盤前，準備為一座全新的『全境醫療生死檔案大資料庫 (medical records system)』繪製放行大門的邏輯地圖。一旁的首席資安大護法拿著大刀，狠狠地在沙盤上劈下了一條血紅色的鐵律死線：「聽好了！在這座城裡，我的絕對預設教條就是：【『當一名渾身發光的新手菜鳥醫生在我們系統裡剛剛誕生建好帳號的那一瞬間！他所能看到的權力，就是一片死寂的地獄黑暗！因為他被系統【絕對預設且不帶感情地全面封殺 (implicitly denied)】，連一絲一毫的病歷他都別想看見！】』。如果他這傢伙膽大妄為想伸手打開任何一份病患卷宗，城門守衛必須一腳把他給無情踹開 (definitively block them)！唯獨只有當：檔案室那張『神聖大判官權力名冊』上，真真切切、白紙黑字用硃砂筆畫上了【為這名醫生命中注定，開放這片特定病房的『閱讀』解鎖聖旨金牌 (explicitly granting) 時】，他才准碰那份病歷半根寒毛！請問，這套猶如生人勿近、一律格殺勿論的冷血設計，正是不打折扣地在膜拜哪一條防禦大真理？)**
A. Principle of Least Privilege (最小極限特權原則，是指給他的權力應該要有多小，而不是預設砍斷全部)
B. Fail-Safe Defaults (Implicit Deny) (這就是冷酷無情、霸道絕倫卻能完美續命的【極致失效安全預設防禦結界 (Fail-Safe Defaults) / 或稱其為修羅道之『預設隱性絕對大封殺 (Implicit Deny)』！】)
C. Complete Mediation (這是每次拿刀都要去問過老大的全面仲裁機制)
D. Psychological Acceptability (這是講求安控大門要好拉好握、不讓人類覺得煩躁的心理可接受度)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「失效安全預設 (Fail-Safe Defaults)」** 或最常聽到的同義詞 **「隱性拒絕 / 預設拒絕 (Implicit Deny / Default Deny)」**。
    *   這是防火牆與存取控制設計的最高鐵律。
    *   它的核心哲學是：「除非有白紙黑字的法律 (Explicit Allow) 特別說你可以過，否則你就是不能過，所有的預設狀態就是鎖死」。
    *   (部分考生可能會想選 A，Least Privilege 也是好概念，但 Least Privilege 探討的是 "當你開門給他時，門縫只能開多大"；而題目中那種 "一開始什麼都沒有，直到有明確允許規則才放行" 的描述，精確對應的是 Default Deny / Fail-Safe Defaults 這個架構基石。)

#### **9. A software development team builds an enterprise password vault application. To convince the Chief Information Security Officer (CISO) that their encryption methodology is unbreakable, the lead developer proudly claims, "Our application is completely unhackable because we invented a highly complex, secret, proprietary mathematics encryption algorithm entirely from scratch, and we refuse to publish how it works, so no hacker can ever figure it out." The CISO immediately rejects the software. Which fundamental secure design principle did the developer blatantly violate?**
**(一支野雞軍團工程師，不知死活地蓋了一座號稱『企業級萬能密碼大金庫 (password vault application)』。為了要騙過那位閱人無數的帝國資訊安全長 (CISO)，讓長官相信他們家大門的鎖頭天下無敵。這名帶頭的工程師居然沾沾自喜、大言不慚地拍胸脯吹牛說：「報告長官！我們開發的這個金庫系統絕對是全宇宙連神仙都無解的駭客墳墓 (completely unhackable)！為什麼呢？因為我們幾個深宮怨婦天才！居然在地下室閉門造車，【自己發明創造出了一套猶如天書般複雜又邪門的『不傳之秘獨家黑魔法數學加密大演算法 (secret, proprietary encryption algorithm entirely from scratch)』】！而且我們已經發毒誓，【打死也絕對不會把這套陣法的運作秘密公開寫給任何人看 (refuse to publish how it works)】！所以外面那些駭客笨蛋這輩子絕對猜不到我們的機關怎麼解！」。結果，CISO 大老爺一聽，臉色鐵青，當場就把這坨程式碼當成垃圾給扔進了碎紙機裡永不錄用 (rejects the software)！請問，這群不知天高地厚的開發者，他們這番狂言，是徹底將哪一條猶如定海神針般的『千古資安防禦設計大聖律』給踩在爛泥巴腳底下徹底踐踏？)**
A. Separation of Privilege (那是需要兩個人兩把鑰匙轉動飛彈按鈕的特權分離)
B. Psychological Acceptability (這個只是你密碼不能要求太長，不然人類會發瘋的心理承受度)
C. Open Design (Kerckhoffs's Principle) / Avoid Security through Obscurity (這群蠢蛋就是公然強姦蹂躪了那條流傳百世、令所有江湖大師膜拜的【克爾克霍夫開放設計大真理 (Kerckhoffs's Principle / Open Design) / 也就是【絕對他媽的不要妄想要靠躲在黑暗中掩耳盜鈴來防禦 (Avoid Security through Obscurity)】的狗屁妄想！這種躲起來的秘密一旦被看穿就是毀滅的開始！)
D. Least Common Mechanism (這是指大家不要共用同一根水管不然會互相傳染的少共用機制原則)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「開放設計 (Open Design)」**，更精確的源頭說法是 19 世紀的 **「克爾克霍夫原則 (Kerckhoffs's Principle)」**，或現代白話文 **「不要依賴隱晦式安全 (Avoid Security through Obscurity)」**。
    *   Kerckhoffs's Principle 的真理定義是：**一個密碼系統的安全，絕對不應該建立在「演算法的秘密與隱蔽」上。它唯一該依賴的只有「金鑰 (Key) 的保密」。**
    *   為什麼全世界政府跟銀行都在用 AES, RSA 等這些「演算法徹底公開在網路上」的機制？因為這些算法歷經全球幾萬個密碼學天才數學家天天盯著看、天天攻擊測試了幾十年，證明它真的牢不可破。
    *   當這幾個阿宅工程師宣稱「我自己發明的私有算法很安全，因為我藏起來不給你看」，這在業界是個巨大笑話。這種私有算法一旦駭客逆向工程反編譯 (Reverse Engineering) 把你的算法翻出來，通常裡面全都是幾分鐘就能破解的低級數學破洞。這就是 CISO 氣到發抖退件的原因。
