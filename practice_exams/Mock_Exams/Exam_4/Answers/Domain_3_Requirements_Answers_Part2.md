# 第四套全真模擬試題 (Exam 4) - 答案與詳解本
## 領域 3：安全的軟體需求 (Secure Software Requirements) (18題) - Part 2 (Q7-Q12)

---

#### **7. To fulfill a "Non-Repudiation" security requirement for high-value financial transactions, which of the following mechanisms MUST be explicitly defined in the requirements documentation?**
**(為了在一本價值連城、每筆帳單都上百萬兩黃金的『皇家大宗銀票兌換名冊 (high-value financial transactions)』上，強制烙印下一條鐵血大訓令：【『所有按過手印買賣銀票的錢莊掌櫃！就算明天這筆銀票變成了廢紙，你也絕對不准在公堂上哭爹喊娘地耍賴大喊：「這張銀票上面的手印不是老子按的！」(fulfill a "Non-Repudiation" security requirement)』】。為了徹底斬斷這群錢莊掌櫃事後翻供的後路！身為大總管，你在寫這本名冊的防禦設計圖時，【必須、絕對、毫無懸念地】把哪一套神仙也賴不掉的霸王硬上弓大陣法，死死地寫進需求條款裡？)**
A. The use of Symmetric Encryption (e.g., AES) for all database fields. (對稱加密雖然能把銀票鎖進保險箱，但這把保險箱鑰匙是兩人共用的。如果銀票出事了，你根本無法證明是【發銀票的人】放的，還是【收銀票的人自己偽造放進去的】，所以對稱加密無法提供防賴帳功能)
B. The use of Digital Signatures (Asymmetric Cryptography) where the sender signs the transaction with their Private Key. (這就是讓全天下耍賴賭徒無語問蒼天、絕望至極的：【『數位血手印大封印術 (Digital Signatures / Asymmetric Cryptography)』】！這道大陣法的核心奧義只有一句話：要下單買銀票的掌櫃，必須拿出那把【『他自己死死藏在褲襠裡、全天下除他之外無人擁有的『獨門大私鑰 (Private Key)』】！親自有如滴血認親般，把這張銀票狠狠蓋上大印 (signs the transaction)！一旦這個大印被公堂上的驗鈔官用『公鑰』驗證成功！那這掌櫃就算在法庭上撞牆自殺，也再也無法厚顏無恥地喊出「這銀票不是我買的」這句話了！這就是密碼學最高境界之不可否認性！)
C. The enforcement of two-factor authentication (2FA) during login. (雙重驗證是進銀行的第一道搜身檢查，雖然很重要，但它無法證明最後那一筆「銀票交易行為單據」本身是誰蓋的章。搜身不等於防賴帳契約)
D. The implementation of a Web Application Firewall (WAF) to log all incoming HTTP headers. (WAF 只是門口的監視器，它只能拍到有人進來，但無法提供能讓縣太爺定罪的密碼學級別鐵證)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是密碼學與資安需求中最經典的對應關係。
    *   **不可否認性 (Non-Repudiation)：** 確保交易的任何一方，都無法在事後否認自己曾經發送過或接收過該訊息 (I cannot deny I sent this message)。
    *   **唯一解法：非對稱加密 (Asymmetric Cryptography) + 數位簽章 (Digital Signatures)**。
    *   **運作原理：**
        1. 傳送者 (Sender) 使用自己的**私鑰 (Private Key)**，對交易訊息的 Hash 值進行加密，產生這份文件的「數位簽章」。
        2. 因為私鑰具備「唯一不可替代性 (只在 Sender 自己手上)」。
        3. 接收者 (Receiver) 用 Sender 公開的**公鑰 (Public Key)** 解碼這個簽章。如果解得開，代表這份文件【百分之一萬萬】是持有私鑰的 Sender 創建的，並且內容從未被竄改 (結合了 Authenticity 與 Integrity)。這構成了法庭上的鐵證 (Legal Non-Repudiation)。

#### **8. A software architect is analyzing the security requirements for an IoT (Internet of Things) temperature sensor intended for agricultural use. The sensor has 16KB of RAM and an extremely low-power 8-bit microcontroller. The product manager demands that the sensor use TLS 1.3 with an RSA 4096-bit certificate to transmit data to the cloud. What is the fatal flaw in the product manager's requirement?**
**(一名老練的神鬼工匠，正拿著放大鏡，苦惱地看著手掌心裡那顆剛打造好的『農田天氣小石頭 (IoT temperature sensor)』。這顆小石頭簡陋到了極點！它的腦袋只有可憐的 8 個齒輪 (8-bit microcontroller)，肚子裡更是小到只能裝下幾滴雨水 (only 16KB of RAM)。沒想到！那個穿著金銀綢緞、完全不懂打鐵的土財主掌櫃 (product manager) 大搖大擺地走進來，指著小石頭下了一道荒謬絕倫的死命令：『聽好！這顆量氣溫的破石頭，每天跟雲端神仙講話的時候，必須給老子披上一件全世界最厚、連大砲都打不穿的『百萬噸級超級重裝大鐵甲 (TLS 1.3 with RSA 4096-bit certificate)』！』！請問，這土財主下的這道蠢命令，根本就是犯了哪一條會把工匠逼到跳樓的兵工廠大忌 (fatal flaw)？)**
A. RSA 4096-bit is no longer considered secure by NIST. (RSA 4096 直到現在都是被視為極度安全的加解密巨獸，土財主的眼光並沒有落後，但他選錯了坐騎)
B. It violates the constraint of the operational environment; the IoT device lacks the computational power and memory to perform heavy asymmetric cryptographic handshakes like RSA 4096. (這就是把活人往死裡逼的：【『無視這隻螞蟻先天殘疾，硬要把大象綁在螞蟻背上的【徹底違反現實運作環境物理極限大死穴 (violates the constraint of the operational environment)！】』】！這老兄居然叫一顆大腦跟豆子一樣大、記憶體只有 16KB 的可憐 IoT 小石頭，去運算那【每次交握都需要消耗掉幾千倍大腦算力、足以把整顆石頭直接燒穿幾萬次的高深非對稱大矩陣數學難題 (heavy asymmetric cryptographic handshakes)】！這顆小石頭連載入鑰匙的三分之一都撐不住就會直接短路爆炸身亡了！)
C. TLS 1.3 only supports UDP traffic, but IoT devices require TCP. (完全相反的胡說八道，TLS 1.3 是跑在 TCP 上的)
D. The requirement does not specify the color of the IoT device's casing. (外殼顏色跟加解密的沉重負載生死存亡毫無關係)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這題探討在編寫安全需求時，必須把 **運算環境限制 (Operational Environmental Constraints)** 納入考量。特別是在資源受限設備 (Resource-Constrained Devices) 如 IoT、嵌入式系統 (Embedded Systems) 上。
    *   **非對稱密碼學的代價：** RSA (Rivest-Shamir-Adleman) 雖然安全，但它的數學本質 (大質數分解) 極度耗費 CPU 算力、耗電 (Power Consumption)，且需要大量的記憶體來存放那巨大的 4096-bit 金鑰。
    *   **IoT 的現實：** 一個 16KB RAM、靠鈕扣電池跑三年的農田感測器，如果被強迫執行 RSA 4096 握手。它會直接耗盡記憶體 (OOM) 當機，或是幾天就把電池抽乾。
    *   **正確的安全需求寫法：** 應該使用「輕量級密碼學 (Lightweight Cryptography)」，例如橢圓曲線密碼學 (ECC - Elliptic Curve Cryptography)，或者直接在出廠時燒錄對稱金鑰 (Pre-shared Keys)。ECC-256 具備與 RSA-3072 同等的防禦力，但只消耗兆分之一的算力與電量。

#### **9. During a threat modeling session in the requirements phase, the team identifies that an attacker might try to exhaust the server's CPU by repeatedly submitting incredibly complex, deeply nested JSON payloads to the search API. Which countermeasure should be documented as a functional security requirement to mitigate this Denial of Service (DoS) threat?**
**(在一場大家圍著營火、苦思防敵破城劇本的大法會上 (threat modeling session)。斥候滿頭大汗地衝進來回報：『大將軍！如果敵軍派幾百萬個瘋子死士，日以繼夜地從我們的尋人城門口 (search API) 裡，丟進好幾萬箱裡面【『像俄羅斯娃娃一樣，大箱子包小箱子，足足包了幾百萬層的超級變態連環鎖大謎語箱 (incredibly complex, deeply nested JSON payloads)』】！如果我們守城門的衛兵一個個傻傻地去拆包裹解謎，守城大軍的腦袋會直接過熱死機，整座城會被這幾百萬箱謎語給活生生癱瘓拖垮的啊 (exhaust the server's CPU / DoS)！』請問，為了避免這種被「惡意包裹塞爆大腦」的慘烈戰敗。大將軍在下達城門禁兵大令時，必須把哪一道『功能性殺手鐗 (functional security requirement)』，血淋淋地寫進第一頁的軍法裡？)**
A. The application shall encrypt all incoming JSON payloads using AES-256 before processing. (你把這些幾百萬層箱子又加上俄文加密再讓大腦去解一次，大腦只會燒毀得更快更慘，這是拿大砲打蒼蠅還打瞎自己的自殺式行為)
B. The application shall implement input validation to enforce a strict maximum depth limit and maximum size limit for all incoming JSON payloads. (這就是能把千軍萬馬像垃圾一樣攔在城牆外的終極防禦大盾：【『建立嚴酷的搜身站：實施極限包裹檢查大法 (implement input validation)！』】。這條城門死命令規定：任何送進門的箱子，守衛只要拉皮尺一量！『箱子超過十公斤的！一律丟下護城河 (maximum size limit)！』『箱子裡面套娃超過五層的！連拆都不拆，直接拿火燒了 (strict maximum depth limit)！』！不用浪費大腦的腦力去解謎，這就是對抗應用層資源耗盡大屠殺 (DoS) 最一針見血的續命神仙解藥！)
C. The application shall require users to change their passwords every 30 days. (逼大家 30 天換一次大門口令，根本無法阻止那個瘋子死士每天拿舊版密碼丟一卡車箱子進來炸你的伺服器)
D. The application shall store all database backups in an off-site location. (備份金庫是為了怕城被炸毀後可以重建，但現在我們是要討論【怎麼不要讓這千軍萬馬的死士把大腦給塞炸了！】，這兩者完全不在一個次元)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是針對 **「XML/JSON 炸彈 (Billion Laughs Attack)」** 或 **「深度嵌套拒絕服務攻擊 (Deeply Nested Payload DoS)」** 最標準的安全需求。
    *   **攻擊原理 (資源耗盡)：** 應用層的分散式阻斷服務攻擊 (L7 DoS)，不一定是靠百萬頻寬把網路塞爆。駭客可以只送出一個 1MB 但是包含 10 萬層大括號 `{` 的 JSON。當後端 Parser (如 Java Jackson 或 Node.js 的 JSON.parse) 試圖用遞迴 (Recursion) 把這個 JSON 拆解時。CPU 就會瞬間飆到 100%，或 Call Stack 直接爆掉而當機。
    *   **Requirement 寫法：** 預防勝於治療。安防需求必須明確寫出：「API 閘道或 Parser 【必須】設定輸入驗證。JSON 最大長度不可超過 2MB，最大深度 (Depth) 不可超過 10 層。一旦超過，立即拋棄請求 (Drop) 並返回 400 Bad Request」。這樣惡意請求連進入主業務邏輯消耗 CPU 的機會都沒有。

#### **10. A multinational company is building a cloud storage solution. The EU legal team dictates a strict requirement: "Data belonging to citizens of the European Union must be physically stored on servers located within the geopolitical boundaries of the EU." What specific type of compliance and legal requirement is this?**
**(一家在全球呼風喚雨、專門收留天下人金銀財寶的跨國大金庫 (multinational company)。有一天，歐洲總督府的律師團拿著皇帝的金牌，氣勢洶洶地衝進來下了一道猶如緊箍咒的霸王鐵令 (strict requirement)！這律師團咆哮著：『聽好！所有屬於我們歐洲子民的銀子跟戶口名簿 (data belonging to EU citizens)！【從今以後，絕對不准給老子運過大海、不准藏在地中海以外的任何一個蠻荒國家！這批歐洲老百姓的銀票，只能世世代代被埋在我們歐洲大陸自家的黃土大陸架底下 (must be physically stored on servers located within the geopolitical boundaries of the EU)！】』請問，這種極度蠻橫，硬要把資料像劃定國界一樣死死圈在某塊泥土裡的強悍法條，就是天下聞名的哪一部鎖國大律例？)**
A. Data Portability (資料可攜性是指老百姓想搬家時，你可以把銀票裝箱帶走到別家銀行，而不是像現在被綁死在歐洲泥土裡)
B. Data Residency (Data Sovereignty) (這就是震驚四海、拿『國家主權國界』來當資料金鐘罩的終極大獨裁法案：【『強迫資料在地化之資料駐留大結界 (Data Residency) / 或稱為神聖不可侵犯之資料主權 (Data Sovereignty)』】！這條法律宣告：資料是有『國籍』跟『靈魂』的！歐洲人的資料靈魂，就必須被實體硬碟死死釘在那塊名為『歐洲法治土壤』的大陸上！因為一旦這資料漂洋過海到了別國領土，就會淪為任人宰割、沒有本國法律神功護體的孤魂野鬼。這是一切雲端架構設計的超級大鐵板！)
C. Data Masking (資料遮罩是把歐洲人的名字打馬賽克，但馬賽克也無法改變這硬碟被搬去美洲大陸儲存違法的事實)
D. Safe Harbor (安全港是以前歐洲同意資料只要發誓安全就可以流去美國的一部古老過期條約，它早就因為不安全被推翻拋棄了。不是這題把資料死死綁在歐洲領土上的精神)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「資料駐留 (Data Residency)」** 或是更政治強烈的詞彙 **「資料主權 (Data Sovereignty)」**。
    *   雲端時代最大的迷思就是 "The Cloud is everywhere (雲端無國界)"。但對各國政府而言，這是不允許的。
    *   **法規核心：** (例如歐盟 GDPR 衍生的規範，或是俄羅斯的資料法)。這些國家的法律強制規定：「只要你是收集了本國公民的個人資料。這些資料存放的『實體硬碟 (Physical Servers)』，在地理位置上必須座落於本國國界之內。」
    *   **對軟體設計的影響：** 這項 Compliance Requirement 將決定雲端伺服器的建置藍圖。架構師不能把全世界的使用者資料全寫進位於美國 "US-East-1" 的資料庫裡。這將導致嚴重的違法抄家。必須在 AWS/Azure 歐洲區 (如法蘭克福) 建制完全隔離的資料庫。

#### **11. According to OWASP, which of the following is an example of an effectively written, testable Security Requirement?**
**(在傳說中的那本由全天下神機妙算工匠共同編著的『OWASP 安防聖經大寶鑑』裡，對於怎麼寫下城池防護命令條款，有著無比血淋淋的嚴酷標準。而在這四項被當成教材的聖旨中，到底哪一道，才稱得上是【『字字如刀、能精準落地斬妖除魔、連隻狗看了都知道怎麼用尺去量它有沒有蓋好 (effectively written, testable) 的完美防禦大軍令』】？)**
A. "The application must be completely secure against all hacker attacks." (這是一句沒有大腦、只會喊口號騙三歲小孩的廢話！世界上沒有什麼叫做「完全擋住所有攻擊」的鬼東西。你叫工匠拿什麼尺去量？這道命令只會淪為被丟進垃圾桶的笑話)
B. "The application shall use industry-standard encryption." (這看似冠冕堂皇，但「業界標準 (industry-standard)」這四個字比泥巴還軟爛！什麼是標準？五年前大家覺得 MD5 是標準，現在早就是垃圾了！這模糊不清的指令，最終只會讓工匠自己拿三十年前的老古董去濫竽充數)
C. "The application shall lock the user account for 15 minutes after 5 consecutive failed login attempts within a 5-minute window." (這就是那堪稱教科書等級、字字見血封喉的【『絕對可量測、可攻擊、可防禦之終極神聖金牌需求大命令 (testable Security Requirement)』】！這道命令就像是一張有刻度的藍圖：【『聽好！在五分鐘這個漏斗滴完之前 (5-min window)！只要有一個王八蛋連續猜錯五次大門密碼 (5 consecutive failed)！大門的鎖頭就必須自動關上死神的大門，將他死死封殺十五分鐘 (lock for 15 minutes)！』】。這道指令，不管是打鐵的，還是拿大砲測試的 (QA)，他們都能輕易地用碼表對著城門敲打五次，精準驗證這個防衛機制到底有沒有起作用！這就是需求工程的極致美學！)
D. "The application should have a strong password policy." (這又是另一道讓人吐血的軟泥巴指令。「強 (strong)」是什麼意思？要多長？要不要特殊符號？這句話沒有寫清楚，連神仙也無法驗證你這密碼鎖到底是強是弱)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 探討需求工程中最關鍵的原則：**「可測試性 (Testability)」** 與 **「具體性 (Specificity)」**。
    *   **好需求的特徵 (SMART 原則)：**
        *   **S (Specific 具體)：** 不用 "Industry-standard" 這種空泛詞彙。明確寫出 "AES-256-GCM" 或是題幹中的精確數字 (5 次, 5 分鐘, 15 分鐘)。
        *   **M (Measurable 可量測) / T (Testable 可測試)：** 一個 QA 工程師可以看著這條 Requirement，寫下 100% 明確的 Test Case (測試案例)。
    *   **Test Case 舉例 (對應選項 C)：**
        *   *步驟 1:* 10:00 AM，故意打錯密碼 4 次。(預期結果：帳號未鎖定)。
        *   *步驟 2:* 10:02 AM，第 5 次打錯。(預期結果：帳號被鎖定)。
        *   *步驟 3:* 10:05 AM，嘗試正確登入。(預期結果：登入失敗，顯示帳號鎖定)。
        *   *步驟 4:* 10:18 AM，嘗試正確登入。(預期結果：登入成功)。
    *   只有像選項 C 這樣寫的需求，才能被真正落實成程式碼與自動化測試腳本。

#### **12. A company requires a Single Sign-On (SSO) solution for its internal web applications. The requirement states: "When an employee logs into the central portal, they must be seamlessly logged into WebApp_A and WebApp_B without entering their credentials again. The applications rely on XML-based assertions to exchange this identity information." Which technology is the requirement describing?**
**(一家擁有幾十個跨國部門的無底洞大城管局 (internal web applications)。大老爺終於受不了那些每天為了一堆芝麻綠豆大的帳號密碼而把總機電話打爆的底層賤民了！他頒布了一道名為『一鑰開天門大赦令 (SSO solution)』！這道聖旨上清楚寫著：『聽好！從今以後，這群賤民只要在早上進皇城大門時，跟守衛亮一次那張破狗牌 (logs into central portal)。等他們走到大門裡面那名叫【大食堂 (WebApp_A)】跟【大茅房 (WebApp_B)】的兩座大樓時，這兩棟樓的守衛【絕對不准再叫他們掏狗牌！這群賤民必須能像幽靈一樣直接無縫飄進去吃屎或者吃飯 (seamlessly logged in without entering credentials again)！】』而在聖旨的最底下，偷偷加了一個專門給通信官看的大暗號：【『這幾棟大樓之間的守衛，要互相確認這賤民是不是剛剛進城門的同一個人，必須用那本古老無比、裡面寫滿了密密麻麻的尖括號與《XML 終極身分宣誓大卷宗 (XML-based assertions)》來傳遞暗號』】請問。在天下武林裡，這本拿著古老 XML 經文書寫的單一通關大典籍，尊號為何？)**
A. OAuth 2.0 (OAuth 的小弟是 JSON 格式。而且它是用來給兩隻沒有血肉的機器人互傳權限令牌，不是用來當作人類無縫穿越各個辦公大樓的萬能大總管鑰匙)
B. SAML (Security Assertion Markup Language) (這就是那本流傳千古、稱霸企業內網通關數十年不倒的：【『安全斷言大標記法語錄 / 企業級單兵通關無縫登入大神訣 (SAML, Security Assertion Markup Language)』】！這老傢伙的本命絕技，就是當你跟大門守衛 (IdP) 報上名後，大門守衛會幫你寫下一張『用又臭又長的 XML 尖括號語言包裝好的《這傢伙就是王小明這絕對無誤之神聖大宣誓票據 (Assertions)》』。只要你拿著這張 XML 神符，去內網那些認識這神符的其他大樓 (SP)。這些大樓一看到這張票，就會立刻打開大門把你當老爺一樣迎接。這就是最標準、最正宗的企業級身分證驗證大典籍！)
C. LDAP (Lightweight Directory Access Protocol) (這只是裝著幾百萬張狗牌名冊的大型電話簿，它沒有那種幫你寫 XML 神符去各家大樓通關的超能力)
D. JWT (JSON Web Tokens) (JWT 就像它的名字 JSON 一樣，是用大括號寫在現代輕薄短小令牌上的。但這聖旨明明說了要用『XML-based (古老尖括號)』這三個魔法大字。用 XML 寫的大傢伙，全天下就只有 SAML 這一位老大哥！)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是針對 **SAML (安全斷言標示語言)** 最經典的特徵描述。
    *   **SAML 的兩大黃金特徵：**
        1.  **用途：** 專為企業內部或跨網域 (Cross-Domain) 網頁瀏覽器的 **企業級單一登入 (Enterprise Web Browser SSO)** 而設計。
        2.  **資料格式 (Data Format)：** 它使用 **XML** (Extensible Markup Language)。這也是它與現代 OAuth/OIDC 最大的技術分水嶺。
    *   **SAML 運作機制 (IdP 與 SP)：**
        *   員工先在一台中心的登入神壇 (Identity Provider, IdP ；如 Okta/ADFS) 輸入密碼登入。
        *   IdP 驗證成功後，會生成一份帶有數位簽章的 **"SAML Assertion (XML 宣誓書)"**，裡面寫著："我以神壇的名義宣誓，這個人確實是王大明，而且他在 HR 權限群組"。
        *   員工的瀏覽器把這份 XML 帶去給 WebApp A (Service Provider, SP)。WebApp A 只要解得開這份 XML，就直接放行，這就是 "Seamless SSO (無縫登入)" 的原理。
