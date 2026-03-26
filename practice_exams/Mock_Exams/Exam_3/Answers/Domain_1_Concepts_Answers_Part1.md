# 第三套全真模擬試題 (Exam 3) - 答案與詳解本
## 領域 1：安全的軟體概念 (Secure Software Concepts) (16題) - Part 1 (Q1-Q8)

---

#### **1. A military defense contractor is designing a highly secure, multi-tier intelligence database. To ensure that a compromised front-end web server cannot directly access or query the backend top-secret database servers containing classified blueprints, the network architect places the web servers in a Demilitarized Zone (DMZ) and the database servers in an isolated, internal network segment. All communication between the two zones is strictly controlled by stateful firewalls enforcing specific, narrow ports and protocols. Which foundational security concept is the architect primarily establishing to limit the "blast radius" of a potential breach?**
**(一家專做軍火生意的國防承包商，正在秘密打造一座如要塞般的『多層次頂尖情報資料庫 (multi-tier intelligence database)』。為了確保萬一那台拋頭露面、放在最前線擋子彈接客的『Web 網頁伺服器』不幸被駭客攻破奪舍時！那名駭客也【絕對無法】趁機長驅直入、直接跨過大門去查詢翻找後方深處那台藏有『極機密飛彈設計藍圖 (classified blueprints)』的最核心後台資料庫伺服大娘。總架構師下了一道死命令：將網頁伺服器全部驅逐流放到猶如緩衝隔離島的【非軍事區 (DMZ)】中，而把資料庫本尊囚禁在極度深淵的【內部隔離網段 (isolated network segment)】裡。這兩座島嶼之間所有的通訊喊話，都被極端嚴格的城門守衛 (Firewalls) 死死掐住，只准許最小必要的一條小縫 (特定 ports/protocols) 通行。請問這位架構師如此勞師動眾大興土木，最主要是為了藉由建立哪一項安全國防基石概念，來死死限制住萬一前線爆炸時的『核爆毀滅半徑 (blast radius)』？)**
A. Obfuscation (把東西藏起來讓人看不懂的障眼法 (Obfuscation))
B. Non-repudiation (讓你簽了名就賴不掉的不可否認大印章)
C. Segmentation (Network Segmentation / Zoning) (這就是大刀闊斧、將國家切成無數個獨立防爆艙的【網段隔離大陣 / 區域切割術 (Network Segmentation / Zoning)】！)
D. Least Privilege (給員工最少鑰匙的最小特權)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「網路隔離 / 分段 (Network Segmentation / Zoning)」** 是縱深防禦 (Defense in Depth) 最具實體感的第一道防爆牆。它的核心思想是：「不要把雞蛋放在同一個大籃子 (扁平網路 Flat Network) 裡」。如果 web 跟 DB 放在同一個網段，駭客只要打下 web，就能用同網段的 ARP 欺騙或直接連線把 DB 端走。透過實體或虛擬的防火牆將網路「切碎 (Segmentation)」，並把最危險的 (Web/DMZ) 跟最神聖的 (DB/Internal) 徹底物理隔開。這大幅限制了一台機器被駭後，駭客能在內網『橫向移動 (Lateral Movement)』的爆炸破壞半徑 (Blast radius)。
    *   **為何 D (Least Privilege) 不是最佳解：** 最小權限偏向於「帳號身分存取控制」，例如 DB 只能讀這張表。但本題明確描述的是架設 DMZ 與修改實體/虛擬「網路網段與防火牆架構」，這是標準的 Segmentation 手法。

#### **2. An e-commerce heavily relies on a commercial cryptographic library to encrypt millions of credit card transactions daily. One evening, a massive zero-day vulnerability is publicly disclosed, indicating that a specific padding oracle attack can completely decrypt the library's ciphertexts. The company immediately realizes they have absolutely no alternative secondary cryptographic library integrated into their application to switch to. Consequently, to protect customer data, they are forced to completely shut down the entire payment processing system for three agonizing days while their developers frantically attempt to rip out and replace the compromised library. Which core security design principle did the application architectures catastrophically fail to implement?**
**(一家日進斗金的龐大網路電商大廠，他們家的收銀台死死依賴著一套花大錢買來的『商業加密函數積木庫 (commercial cryptographic library)』，每天仰賴它來把幾百萬筆顧客的信用卡卡號給上好加密鎖。不料！某個寧靜的夜晚，一聲驚天巨雷劈下：全球資安新聞頭條爆出了一個毀滅級的【零日漏洞 (Zero-day)】！宣佈只要駭客使出一招名為『Padding Oracle』的黑魔法，就能像開拉鍊一樣瞬間把這套加密庫鎖上的密文全數給解開曝光變回明文。這家公司管理層瞬間嚇到尿褲子，更讓他們絕望的是：他們猛然發現自家那龐大的應用程式裡，【根本連一套可以當備胎、緊急切換過去頂著用的第二套後備加密庫都沒有】！為了不讓卡號外洩死無全屍，他們被迫含淚拉下鐵門，把整個國家級的結帳收銀系統【活生生全面強制拔插頭關機停業了整整痛苦的三天三夜 (shut down everything for three agonizing days)】！全體工程師戴著鋼盔，發瘋似地在機房裡沒日沒夜把那套爛掉的加密庫給活活挖出來、重新換上一套新的才敢開門做生意。請問，當年這群拿高薪的系統大架構師，是在哪一條最核心的安控神殿設計教條上，犯下了導致這場傾家蕩產悲劇的不可饒恕之滔天大罪？)**
A. Complete Mediation (每進出一次都要搜身安檢的完全仲裁)
B. Open Design (演算法要公開透明接受檢驗的開放設計)
C. Defense in Depth (specifically regarding Diversity / Redundancy of critical security controls) (這就是因為他們愚蠢地把所有雞蛋全砸在同一個生鏽的籃子上！徹底違背了那要求城牆必須一重又一重、兵種必須多樣不重複的【縱深防禦大戰略 (Defense in Depth) / 尤其是針對致命安全控制點的『多樣性 (Diversity) 與備援冗餘 (Redundancy)』神聖鐵律】！)
D. Separation of Duties (把工作切開兩人做的職責分離)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「縱深防禦 (Defense in Depth)」** 不只是指「防火牆後面要加入侵偵測」。它在軟體開發中還有一個極端高級的分支：**「控制多樣性 (Control Diversity) 與備援防護 (Redundancy)」**。
    *   如果一個系統的生死存亡只依賴「單一一家廠商的一套密碼學庫 (Single Point of Failure)」或者「單一種防毒軟體」，當這個唯一的救世主爆出 Zero-day 時，企業將面臨萬劫不復的停機。一個具備縱深防禦思維的成熟架構，在設計加密模組時，會實作「加密抽象層 (Crypto Abstraction Layer)」，底層同時支援如 Bouncy Castle 和 OpenSSL 兩套不同的引擎。當一套出事被攻破，管理者只需在 config 檔裡按一個開關 (Fallback)，系統就能瞬間無痛切換到另一套完全不同血統的引擎繼續安全運作，根本不需要停機三天去改 Source Code。

#### **3. A healthcare application processes electronic health records (EHR). When a user successfully authenticates and clicks on a specific patient's profile link, the web application generates the following URL: `https://ehr.hospital.com/view_record?patient_id=88492`. A curious user (Patient A) manually changes the `patient_id` parameter directly in their browser's address bar to `88493` and hits enter. To Patient A's surprise, the application successfully displays the highly sensitive medical history of Patient B. Which fundamental access control principle did the application explicitly fail to enforce on the backend server before retrieving and displaying the data?**
**(一家聲稱極度重視病患隱私的醫療照護掛號看診大系統。今天，有一位名為『病人Ａ』的大媽成功用自己的帳號密碼登入系統後。當她興高采烈地點開心愛自己的電子病歷報告網頁時，眼角餘光瞥見了那條網頁最上方的網址列 (URL)，上面正大光明地寫著這麼一長串咒語：`https://ehr.hospital.com/view_record?patient_id=88492` (翻譯：看病歷？病人號碼=八萬八千四百九十二號)。這位無聊好奇的大媽心生一計，她把滑鼠游標點進了網址列，偷偷把最後那個數字『2』給手動倒退刪掉，改成了『3』(變成 88493) 並且果斷按下了 Enter 鍵！沒想到奇蹟發生了！這套造價百萬的醫療系統居然乖乖聽話，像個白癡一樣，【順理成章且毫無保留地將另外一位毫不相干的「病人Ｂ」那鉅細靡遺、包含各種難言之隱的極機密醫療看診紀錄與用藥歷史，直接血淋淋地展示曝光在病人Ａ的電腦螢幕前】！請問，這套軟體的後台伺服器，在傻傻去資料庫把 B 的資料挖出來送出去之前，到底公然且徹底地遺忘、死當了哪一門最基礎的存取控制看門大兵法則？)**
A. Confidentiality (Encryption at Rest) (機密性 - 把硬碟鎖進保險箱的靜態加密防護)
B. Authorization (specifically preventing Insecure Direct Object Reference / IDOR) (這就是形同把金庫鑰匙直接掛在大門上的滔天大罪！系統徹底喪失了【授權管控判斷 (Authorization) / 特別是犯下了那最愚蠢低級的『不安全直接物件參考大漏洞 (IDOR)』】！)
C. Authentication (驗明正身看你身分證的驗證大關)
D. Availability (機房不斷電不當機的可用性)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是 OWASP 歷史上最著名、最常見且破壞力最大的經典漏洞場景：**「不安全的直接物件參考 (IDOR - Insecure Direct Object Reference)」**，它屬於 **「存取控制失效 (Broken Access Control / 也就是違背了 Authorization 授權機制)」** 的範疇。
    *   **Authentication (驗證，C)** 是問「你是誰？」。病人A 確實有登入成功，所以 Authentication 沒壞。
    *   **Authorization (授權，B)** 是問「即使你登入了，你有沒有『權限』去看這份屬於病人B 的特定檔案檔案？」。這系統最大的敗筆在於：伺服器只看到「有人要 88493 號的資料」，就沒靈魂地去資料庫抓資料丟出來了。伺服器【完全沒有在後台去盤問、比對】說：「等等！現在畫面上這個拿著登入牌子的人是 A，但他討要的檔案擁有者名字是 B！A 無權看 B！擋下退件報警！」。缺少了這道 Authorization (授權驗證) 關卡，就是 IDOR 的悲劇。

#### **4. A Chief Information Security Officer (CISO) mandates that all remote employees must use a Virtual Private Network (VPN) equipped with mutual TLS (mTLS) authentication. Furthermore, the CISO decrees that the underlying cryptographic algorithms used by the VPN software (such as AES-256 and ECC) must be publicly published, extensively peer-reviewed mathematical standards governed by NIST, rather than secret, proprietary algorithms developed in-house by the VPN vendor. Which classic security principle is the CISO strictly enforcing to ensure the strength of the cryptography?**
**(一位鐵血的資訊安全長 (CISO) 降下一道全國最高保密戒嚴令：『全體在外流浪的遠端辦公傭兵團聽令！任何人想連回公司總部內網，都必須給我穿上配備著「雙向極密 TLS 核對大陣 (mTLS)」的最頂級防護隱形 VPN 隧道衣』！不僅如此，CISO 還特別對著這套大名鼎鼎的 VPN 軟體原廠供應商頤指氣使地下了一道緊箍咒：『聽好了！你們這套軟體深處用來把我的資料攪爛加密的那套核心算學齒輪 (例如著名的 AES-256 和 ECC)！【絕對、打死都必須是那種早就被攤在陽光下、被全世界公認的美國國家標準局 (NIST) 頒布、且已經被全球千萬名超級數學家與頂尖駭客用顯微鏡死命看了幾十年都找不出破綻、完美無瑕的「公開透明標準演算法」】！我絕對不准你們這家小廠商，偷偷在肚子裡塞入你們那幾隻小工程師關在地下室自己發明、見不得光、號稱超級無敵沒有人打得破的『自製獨家私有黑魔法加密公式 (proprietary algorithms)』！』。這位老謀深算的 CISO，刻意強硬要求密碼學演算法『必須扒光衣服攤在陽光下接受世人公審挑戰』的智慧，是死死捍衛並遵循了哪一條名震千古的密碼學黃金大教條？)**
A. Security through Obscurity (把頭埋進沙子裡以為別人都找不到我的鴕鳥防禦法)
B. Kerckhoffs's Principle (Open Design) (這就是以十九世紀密碼學先驅之名化為神燈巨人的【柯克霍夫偉大原則 (Kerckhoffs's Principle) / 甚至被昇華為『開放設計大同世界 (Open Design)』的無尚真理】！)
C. Fail-Safe Defaults (當機就要鎖死大門的故障安全鐵律)
D. Separation of Duties (把鎖頭跟鑰匙交給不同人管的職責分離)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是密碼學與資安架構界最被奉為圭臬的 **「柯克霍夫原則 (Kerckhoffs's Principle)」** (也是 **Open Design 開放設計原理** 在密碼學中最具體的體現)。它在 1883 年就宣告了這條真理：【一個完美的密碼學系統，它的安全性【絕對不能】建立在「它的演算法機制是保密、別人看不懂的」之上。它必須預設即使全世界所有最頂尖的敵人、駭客都完全拿到並徹底看懂了你的加密機制與齒輪構造，但只要敵人【唯獨沒有那把你藏在保險箱裡的秘密『金鑰 (Key)』】，他們就永遠解不開密碼！】
    *   **為何 A (Security through Obscurity) 是錯的：** 那些自己躲在車庫裡發明一種「左移八位、右移三位、然後加上今天日期」的自製演算法，就是在搞 Security through Obscurity (隱匿式安全 / 靠沒人知道來騙安全)。歷史證明，這種閉門造車的演算法，最終都會被真正的專家在一週內反組譯並輕易破解打爆。只用全世界公認的演算法 (如 AES)，才是真理。

#### **5. A financial trading platform must guarantee absolute, undeniable proof that a specific high-value stock execution order was definitively initiated by 'Trader X' and absolutely no one else. The system architecture achieves this by requiring Trader X to digitally sign the transaction payload using an asymmetric private key securely stored in a hardware token that physically requires Traders X's biometric fingerprint to activate. Which core security objective is this architectural design primarily fulfilling?**
**(在一座牽動千億美金、殺聲震天的終極金融華爾街交易大高台上。系統必須在上帝與法律面前立下死狀：必須完美、無可推卸、連菩薩下凡都【絕對無法否認及抵賴地鐵血保證 (absolute, undeniable proof)】！這筆高達五百萬美金買進台積電股票的『超高額斬首交易下單指令』，徹徹底底就是被眼前這位代號『交易員Ｘ』的傢伙親自簽字按下發射鈕的！天王老子來都證明不了是別人幹的！為了達到這猶如死契般的絕境要求，這套超級電腦的架構是這樣設計的：當交易員Ｘ要下單時，他必須拿出那把自己專屬的『不對稱密碼學私房私人金鑰 (asymmetric private key)』在交易契約上狠狠蓋下數位死亡大印章。更絕的是！這把超極機密的私鑰，並不存在電腦裡！它是一輩子被死死焊死、囚禁在一張實體的『硬體隨身碟法寶 (hardware token)』裡面。且要喚醒解鎖這法寶蓋章，還必須強制這名交易員親自把他的『活體指紋血肉 (biometric fingerprint)』按在隨身碟上通電才准放行！請問，如此大費周章、幾乎到了走火入魔境地的多重實體加上密碼學身分辨識極限綑綁大陣，最強烈且唯一追求的安控終極神聖戰略目標是什麼？)**
A. Availability (保證機房永不斷電一直開著的大法)
B. Non-repudiation (這就是法庭上連神明都賴不掉、逃不掉的【絕對不可否認性 / 無可抵賴死契大陣 (Non-repudiation)】！)
C. Confidentiality (怕被別人偷看到的遮眼機密保密網)
D. Least Privilege (給盡量少點鑰匙的剝削權力法)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「不可否認性 (Non-repudiation)」** 是電子對帳、金融、法律合約領域中最神聖的詞彙。它的極致目標是：【在事後交易發生糾紛鬧上法庭時，系統能拿出如同鐵證如山般的數學證據，拍在桌上，讓對方啞口無言，完全無法狡辯說「那是駭客偷了我的帳號幹的，不是我買的！」】。
    *   要達成完美的 Non-repudiation，必須靠 **數位簽章 (Digital Signatures，使用不對稱加密的『私鑰』簽名)**。因為全世界只有 Trader X 擁有那把私鑰。而題目中更用心地加上了「實體 Hardware Token」和「指紋 Biometric」，這就消滅了「我的私鑰電腦檔案被木馬偷走了」的這個最後藉口。既然私鑰被鎖在硬體裡拿不出來、且還要你本人的指紋才能通電啟動，那這張簽好名的百萬交易契約單，就絕對是你在清醒狀態下親自按下的，法官一定判你敗訴必須付錢。

#### **6. A junior developer is tasked with handling error exceptions thrown by the backend SQL database when a user searches for an invalid product ID. To proactively aid the internal helpdesk in fast-tracking debugging efforts, the developer configures the global error handler to intercept the SQL exception and display the exact, raw database error message (e.g., `Syntax error in SQL statement near 'SELECT * FROM products WHERE id =...'`) directly on the public-facing customer webpage. Which security principle has the developer grossly violated, thereby providing reconnaissance gold to potential attackers?**
**(一名剛出社會、滿腔熱血但腦袋裝屎的新手菜鳥工程師，接下了一個幫忙處理『使用者在電商網站上打錯商品編號時，後面那台負責算帳的 SQL 資料庫大娘會噴出崩潰報錯大絕叫 (error exceptions)』的修補任務。為了展現他那自作聰明、想當大好人的雷鋒精神，他心想：『如果我能主動幫公司裡的內部維修工客服兄弟們，省下去機房翻找除錯紀錄的時間，那該有多棒啊！』。於是，這隻菜鳥在全站最外層放了一塊『全域捕捉報錯廣播大看板 (global error handler)』！當後台的 SQL 資料庫一噴出錯誤，這塊大看板居然直接把那夾雜著一堆血淋淋內臟、最原始露骨的技術靈魂崩潰慘叫語言（例如：『警告！SQL 語法在執行 `SELECT * FROM products WHERE id =...` 的附近發生了致命語法斷裂破壞！』），【完全不加修飾、直接一字不漏地血淋淋全部公開投射在那任何人都能看到的大街上顧客點餐螢幕網頁上！】。這等猶如主動把家裡保險箱構造跟暗門地圖，大方攤開送給外頭徘徊的駭客刺客當作尋寶指南圖的找死行為，是狠狠踐踏褻瀆了哪條資安防禦大教條？)**
A. Psychological Acceptability (讓系統好用到一般人不會想繞過的人性化介面)
B. Separation of Duties (職責分離)
C. Fail-Safe (specifically, improperly handling errors and leaking sensitive internal state information) (這就是跌倒時不但沒護頭，還主動把脖子伸出去給人砍的【故障安全大失敗 (Fail-Safe) / 尤其是犯下了那最致命的『錯誤處理不當與內部狀態機密大洩漏大忌 (improperly handling errors and leaking state)』】！)
D. Least Common Mechanism (盡量不要讓不同用戶共用一條獨木橋機制)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「故障安全 (Fail-Safe / Fail Secure)」** 原則在軟體設計中有一個極度重要的實作面，叫做 **安全錯誤處理 (Secure Error Handling)**。
    *   當系統發生非預期的錯誤 (Exception) 時，一個成熟的系統應該要做到兩件事：(1) 把這個長滿刺、夾雜著資料庫名稱、伺服器目錄路徑的原始報錯 (Raw Error Message)，默默地寫進連駭客都進不去的最深處內部 Log 日誌檔中留底。(2) 然後在對外端給客人的畫面上，換上一張面帶微笑、非常無聊官方的警告圖（例如：「糟糕，系統發生未知的錯誤，請稍後再試。」）。
    *   如果像這個菜鳥一樣，把包含著 `SELECT * FROM...` 這種透露著後台資料庫長相、欄位名稱的原始錯誤丟給前台。這就是給駭客提供了極為寶貴的 **「情報偵察黃金 (Reconnaissance Gold)」**。駭客本來還在猜測你要怎麼發動 SQL Injection，現在看了報錯，連你的資料表叫 `products` 都知道得一清二楚，這直接加速了系統的死亡。

#### **7. A highly secure government data center mandates a strict physical access control policy: To enter the server room, an employee must first swipe an authorized smart badge (something they have), simultaneously enter a memorized 6-digit PIN on a keypad (something they know), and finally, submit to a biometric retina scan (something they are). What fundamental access control concept does this rigorous, multi-layered entry process represent?**
**(在一座守備森嚴、能防導彈轟炸的極度機密政府深淵超級電腦大機房門前。軍方指揮官立下了一道毫無破綻、近乎變態的實體城門進出安檢鐵律大刑法：任何人要是想活著踏過這道大鐵門進入伺服器聖殿！請聽好：他【必須先】冷酷地掏出身上那張被將軍賜福開過光的『特製高頻智慧識別證大兵牌 (swipe a smart badge)』，對著感應器逼一下 (這代表他出示了【身上隨身攜帶持有之神物 / something they have】)！但在鐵門打開前，還沒結束！他【還必須同時】在旁邊那台佈滿指紋的九宮格數字鍵盤上，快速且精準無誤地盲打敲下那段深深刻在他大腦皺褶深處、無法被偷走的『六位數死亡通關密碼 (memorized 6-digit PIN)』 (這代表他出示了【他腦袋裡死背下來的腦力智慧密碼 / something they know】)。最後！重頭戲來了，他還必須把那顆眼珠子死死瞪著門口那台發著血紅光芒的顯微鏡，強制讓機器射出死光去掃描核對他那『獨一無二生物眼底微血管脈絡網 (biometric retina scan)』 (這代表他獻出了【他骨血肉身不可抹滅的生物實體本質 / something they are】)！只有當這三道不同次元的安檢結界全部完美契合亮起綠燈，天國大門才會開啟放行。請問這等繁複如剝洋蔥般、變態到了極點的多重重疊安防檢查大通關術，在學術上代表了什麼基礎存取控制名詞的終極化身？)**
A. Two-Factor Authentication (2FA) (這只是小兒科、只有兩個因子的雙因素認證)
B. Single Sign-On (SSO) (那是只要刷一次臉就能到處上網吃霸王餐的大平台單一登入術)
C. Multi-Factor Authentication (MFA) (這就是聚齊了天地人三界核對法寶大集結的【終極無敵多因子重重認證大鐵門 (Multi-Factor Authentication, MFA)】！)
D. Federation (這是大公司之間互相結盟承認互通簽證的邦聯大帳)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是資安認證與存取控制中最經典的「認證因子 (Authentication Factors)」理論。業界將認證因子分為三大類本質：
        1.  **Type 1 - Something you KNOW (你大腦知道的東西)：** 例如：密碼 (Password)、圖形解鎖、童年寵物名字 (PIN/Passphrase)。
        2.  **Type 2 - Something you HAVE (你口袋握有的實體防偽物品)：** 例如：家裡鑰匙、這題的實體智慧識別證 (Smart Badge)、手機上的 OTP 簡訊、實體安全金鑰 (YubiKey)。
        3.  **Type 3 - Something you ARE (你自己的肉身生物特徵)：** 例如：指紋、本題的視網膜眼珠微血管掃描 (Retina Scan)、臉部辨識 (FaceID)、聲紋。
    *   這道大門同時強硬掛上了 Know (門禁密碼) + Have (識別證) + Are (視網膜)。因為它大於或等於三種不同屬性的因子結合，所以這是標準的 **「多因子認證 (MFA)」** 完美範例。只要其中有一類因子被人偷走了 (例如卡片被偷、密碼被看光)，駭客也進不去，因為他無法偽造你的眼珠子。

#### **8. A monolithic legacy application historically ran entirely under the context of the highly privileged `root` (or `NT AUTHORITY\SYSTEM`) operating system account, meaning a single web vulnerability could allow an attacker total control over the server. The architecture team decides to refactor the application, breaking it down into smaller, individual microservices. They configure the operating system so each specific microservice runs under a dedicated, stripped-down service account that literally only has file-system read access to its specific configuration folder and nothing else. Which foundational security design principle is the team applying?**
**(在古老黑暗的史前時代，有一隻名叫『無敵鐵金剛 (monolithic legacy app)』的無腦肥大巨獸程式。這隻笨獸當時在伺服器上奔跑運作時，居然是直接冠著作業系統中最可怕、能呼風喚雨殺人全家的玉皇大帝最高權限頭銜『`root` 或 `SYSTEM`』在狂奔！這導致了一個毀滅性的恐怖平衡大黑洞：只要外面的網路小毛賊，隨便在這隻蠢巨獸某個指甲縫的網頁小破洞上戳一下。駭客就能瞬間借助這隻巨獸那通天徹地的大帝帳號，當場奪舍綁架整台伺服器，愛殺誰殺誰 (total control)！為了終結這荒謬悲劇。新上任的架構大殺手團隊！直接派出持刀劊子手，將這隻大肥獸給『活活肢解、切碎分屍』成幾十個微型單人帳篷服務小哨站 (microservices)。更絕的是，他們直接沒收褫奪了這些小哨兵的大帝王冠。他們為每一個微小的服務兵，量身打造了一套『權力被徹底閹割、拔牙拔爪』到極點的窮酸難民小帳號！例如：這個負責看門的哨兵帳號，其權力可憐到【這輩子只准看、而且只准讀取他腳下那個小板凳資料夾裡的一封信 (`read access to its specific config folder`)，除了這個，他什麼門都開不了、連寫字的權力都沒有】！請問這拔刀斬斷極權、剝奪無用特權的架構大清洗，是深深貫徹了哪一條神聖的資安創世大教條？)**
A. Economy of Mechanism (叫你設計越簡單越好越不容易出錯的機制作業)
B. Principle of Least Privilege (這就是把權力閹割到只剩生存底線的殺手鐧：【最低極限特權至高不滅原則 (Principle of Least Privilege, PoLP)】！)
C. Open Design (把系統攤在陽光下的開放設計)
D. Separation of Duties (把一張表單切給兩個人簽字的職責分離)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「最小特權原則 (Principle of Least Privilege)」** 是防禦駭客最最核心的地基。它的精髓是：「任何一隻程式、一個使用者、一個系統程序在執行任務時，系統只應該配給他【剛好能夠完成他手邊這份無聊工作所需的最極限最低、最微小的權力鑰匙】，連半分多出來的權力都不准給」。
    *   老程式用 `root` 跑網站，就是犯了特權過剩的死罪。因為這網站根本不需要去更改系統開機檔的權限，但它卻拿到了整串國家鑰匙。把肥大程式打碎成微服務 (Microservices)，並嚴格限縮每一個微小 Container 或是 Account 的檔案資料夾讀寫權限，這大幅降低了系統的受攻擊面 (Attack Surface)。即使某個微服務被駭客攻破了利用了漏洞，駭客也只能被關在那個微雲端牢房裡看那唯一一個資料夾，根本哪裡都去不了，這完美體現了 Least Privilege 的神聖防禦力。
