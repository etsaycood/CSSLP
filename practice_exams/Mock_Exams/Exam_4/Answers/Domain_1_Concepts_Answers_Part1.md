# 第四套全真模擬試題 (Exam 4) - 答案與詳解本
## 領域 1：安全的軟體概念 (Secure Software Concepts) (16題) - Part 1 (Q1-Q8)

---

#### **1. A new developer on your team suggests implementing a complex, custom cryptographic algorithm for storing user passwords, arguing that because the algorithm is unknown to attackers, it will be impossible to break. As a senior security architect, which fundamental security principle should you immediately cite to correct this dangerous misconception?**
**(你團隊裡新來的一名熱血工匠，興沖沖地跑來跟你獻計。他提議要幫金庫大門打造一個【『全世界只有他自己懂、連神仙都看不懂的超複雜奇門遁甲機關鎖 (complex, custom cryptographic algorithm)』】來保護顧客的密碼。他的理由很理直氣壯：「長官！因為這把大鎖是我們獨門暗器，外面的小偷根本不知道這鎖裡面有幾個齒輪 (unknown to attackers)，所以這大鎖絕對是舉世無敵、無人能破的 (impossible to break)！」身為經歷過無數大風大浪的資安大將軍，聽到這種毛骨悚然的提議。你應該立刻搬出祖師爺留下的哪一條『絕對鐵律金句』，來一巴掌打醒這個危險的井底之蛙？)**
A. The Principle of Least Privilege (最小權限原則是在講城門守衛只能看自己的房間，而不是在探討大鎖到底該怎麼打造)
B. Kerckhoffs's Principle (Open Design) (這就是一巴掌打醒無知小兒的唯一密碼學天道真理：【『柯克霍夫絕對真理 (Kerckhoffs's Principle) / 開放式設計鐵則 (Open Design)』】！這條真理咆哮著：「一把真正偉大的鎖，就算小偷把整張設計圖拿回家研究十年，只要他沒有唯一的那把實體『鑰匙』，他就絕對打不開！【絕對不要把安全寄託在『小偷不知道機關長怎樣的遮掩與無知上 (Security by Obscurity)』】！因為機關圖紙遲早會外洩！」)
C. The Principle of Fail-Safe Defaults (失效安全是在說如果你不知道來的人是誰就預設不准進，不是用來評價機關鎖的好壞)
D. The Principle of Economy of Mechanism (機制經濟原則是說鎖越簡單越好越不會壞，雖然也反對複雜，但這不是針對「獨門暗器」這個概念最一針見血的打臉)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **柯克霍夫原則 (Kerckhoffs's Principle)** 是密碼學與資安架構設計的基石。
    *   **核心思想：** "A cryptographic system should be secure even if everything about the system, except the key, is public knowledge." (一個密碼系統，即使系統的一切設計細節都被公諸於世，只要「金鑰 (Key)」還保密，它就必須是安全的)。
    *   **錯誤觀念 (Security by Obscurity)：** 新手常犯的致命錯誤是「隱匿式安全 (Security by Obscurity)」。他們以為自己發明的加密演算法 (Custom Crypto) 前無古人後無來者。但實際上，未經全球密碼學家數十年來千錘百鍊、公開數學驗證的自創演算法，99.9% 都有嚴重的數學漏洞。駭客一旦透過逆向工程 (Reverse Engineering) 把你的獨門演算法挖出來，瞬間就能秒解你的密碼。
    *   **正確做法 (Open Design)：** 絕對要使用「公開、標準、經歷過時間考驗」的演算法 (如 AES, SHA-256, RSA)。安全的基石在於保護 "Key (鑰匙/鹽值)"，而不是保護 "Algorithm (演算法機器本身)"。

#### **2. A healthcare application stores highly sensitive Patient Health Information (PHI). The database is encrypted using AES-256 (Data at Rest), and all network traffic uses TLS 1.3 (Data in Transit). However, a malicious insider with database administrator privileges runs a direct SQL query, exports the entire unencrypted patient table, and sells it on the dark web. Which core tenet of the CIA Triad was compromised in this scenario?**
**(在保護一間存放著幾千萬份『極高機密皇家太醫院病歷 (sensitive PHI)』的大金庫裡。雖然門口已經加上了號稱天下第一的『AES-256 靜態大鐵櫃鎖 (Data at Rest)』，運送病歷的馬車也全標配了『TLS 1.3 終極防彈裝甲 (Data in Transit)』。可是防不勝防！金庫裡一個擁有最高開門權限的『內鬼總管 (malicious insider with DBA privileges)』，他居然趁半夜自己打開了大鐵櫃，把幾千萬張病歷【原汁原味、未加密地全部整車推出去 (exports unencrypted table)】，然後跑到黑市上賣給敵國情報局 (sells it on the dark web)！請問，在這場太醫館防線大崩潰中，那座偉大 CIA 三神像裡，是哪一尊主掌隱私的神明，祂的金身被這名內鬼給活生生敲碎了？)**
A. Confidentiality (這就是被這名內鬼連根拔起、摔在地上踐踏的：【『絕對隱私與機密性大女神 (Confidentiality)』】！機密性的唯一教條就是「【絕對不准讓沒有資格看的人，看到裡面寫什麼】」。如今國家幾千萬病人的隱私，活生生被敵國老百姓在黑市上當笑話看，這就是機密性徹底死亡的終極體現！)
B. Integrity (完整性是確保病歷沒有被內鬼亂寫成別的病，現在內鬼是拿出去賣，不是把感冒改成癌症，所以並未破壞完整性)
C. Availability (可用性是確保隔天太醫來上班還有病歷可以看。內鬼只是拷貝帶走，原本的病歷還在金庫裡，太醫還是能正常看病)
D. Non-Repudiation (不可否認性是事後可以證明是誰偷的，這不是 CIA 三本柱的主體)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **「機密性 (Confidentiality)」**。
    *   **CIA Triad (機密性、完整性、可用性)：**
        *   **Confidentiality (機密性)：** 防止未經授權的「存取 (Access)」或「揭露 (Disclosure)」。
        *   **情境分析：** 題目中，內部的 DBA 擁有解密資料庫的權限。他濫用職權，將明文資料 (Unencrypted plaintext) 轉賣到網路黑市 (Dark Web)。這導致了大規模的 Data Breach (資料外洩)。駭客或公眾獲得了他們不該看到的敏感資料，這是對機密性 (Confidentiality) 100% 的破壞。
    *   雖然系統有做 Data-at-Rest 加密，但在面對擁有合法密碼的「內部威脅 (Insider Threat)」時，這層防護是無效的，機密性依然淪陷。

#### **3. When designing a new online voting system, the architecture team decides to split the final "Tally Votes" function into two distinct sub-processes. Process A is responsible for decrypting the individual ballots, and Process B is responsible for actually adding the decrypted votes to the final total. A single administrator cannot execute both processes; they require two different senior election officials to log in and authorize the respective steps. What security principle is this design pattern enforcing?**
**(在打造一個能決定全大陸皇帝誰來當的『終極天網大投票系統 (online voting system)』時。長老院的大建築師們，對於最後那個能決定生死的『開箱計票結算大按鈕 (Tally Votes function)』，做了一個極度令人崩潰的設計！他們把這個按鈕硬生生劈成了兩半！【前半段按鈕 A，只能負責把投票箱的鎖給敲開把票倒出來 (decrypt ballots)；而後半段按鈕 B，才能真正開始算票數 (adding to final total)！】。最要命的是，大建築師規定了死命令：【『全天下絕對沒有任何一個人，可以同時擁有按這兩顆按鈕的權力 (single administrator cannot execute both)！要清點全國大選，必須要兩個互相瞪眼、誰也不服誰的不同派系大長老，一個人按左邊、一個人按右邊，這台計票機才會啟動 (require two different senior officials)！』】。請問，這群大建築師這種防人防到骨子裡的極端龜毛陣法，是在貫徹哪一條大兵法？)**
A. Separation of Duties (SoD) (這就是防範獨裁者與內鬼隻手遮天的千古帝王制衡之術：【『終極權力大撕裂與職務分隔對立大陣法 (Separation of Duties, SoD)』】！只要權力不集中在一個人手裡，就算其中一個大長老發瘋想竄改選票，但因為他按不到另一半按鈕，他就永遠無法發動政變！)
B. Defense in Depth (這是一層層像千層糕的城牆，這題探討的是「人」的權力分割，而不是建幾道牆)
C. Psychological Acceptability (心理可接受度是要求東西要好用，逼兩個人才能開保險箱是非常麻煩的事，這完全違反心理可接受度)
D. Complete Mediation (完全仲裁是指每一次進門都要查身分證，這確實有查，但這題的靈魂在於把「一件事拆成兩個人做」，所以職務分隔才是最一針見血的精髓)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **「職務隔離 (Separation of Duties, SoD)」** (在系統操作上有時也體現為 **Two-Man Rule 雙人控制**)。
    *   **核心理念：** 將一個高風險、關鍵的「流程 (Process)」(如：發射核彈、高額匯款、計票)，拆分成多個離散的步驟，並強制要求**由不同的人員或角色來分別執行**。
    *   **防禦價值：** Its primary goal is to prevent fraud and errors by ensuring that no single individual has the complete end-to-end authority to perform a critical task. (為了防止單一個人的惡意舞弊或失誤。如果要作弊，這兩個不同的人必須 "共謀 (Collusion)"，這大大提高了作弊的難度)。

#### **4. A cloud-based HR application allows employees to update their own home address. A flaw in the application's authorization logic allows an aggressive employee to modify the API request parameters (e.g., changing `employee_id=105` to `employee_id=1`) to successfully view and modify the CEO's salary information. In security terminology, what specific type of access control violation is this?**
**(在雲端之上的一座龐大『百工坊戶政大系統 (HR application)』裡，原本開放讓每個基層小工匠，都能進去改改自己租房子的地址 (update their own home address)。沒想到，這個戶政大系統的守門員是個瞎子！有個包藏禍心的小工匠發現了這個秘密。他在交出地址變更單的時候，居然大膽地拿橡皮擦，把自己公文底下那個【原本寫著底層賤民代號叫『勞工編號 105 (employee_id=105)』的號碼給擦掉，換上了那個只有大總裁才能用的神聖王族號碼『帝王編號 1 (employee_id=1)』！】。結果瞎眼守門員連查都沒查，直接把大總裁的【終極金庫薪水存摺 (CEO's salary information)】給叫了出來，還讓這個小工匠大搖大擺地在上面隨便塗改加薪！請問，在安控衙門的卷宗裡，這等賤民僭越王座的死罪，被冠上何等罪名？)**
A. A Cross-Site Scripting (XSS) attack (這是在網頁上貼隱形小廣告罵人的把戲，這傢伙現在可是直接篡位當皇上，維度不同)
B. Vertical Privilege Escalation (這就是那足以讓朝代更迭、底層賤民一夕之間坐上龍椅的：【『極限篡位登天門之垂直權限大升級 (Vertical Privilege Escalation)』】！這小工匠不僅越俎代庖看了別人的資料，他更可怕的是從一個根本沒看薪水權限的基層，【垂直往上、跨越了無數階級】，拿到了只有大總裁才有的『修改薪水大權限』！這種往上爬樓梯的奪權，就是最致命的『垂直篡位』！)
C. Horizontal Privilege Escalation (如果他只是編號 105 偷看隔壁編號 106 另一個可憐工匠的戶籍，那叫『平輩偷窺大觀園之水平越權 (Horizontal)』。但這傢伙現在是看總裁薪水啊！)
D. A Buffer Overflow (這是把包裹塞爆信箱讓房子爆炸的蠻力攻擊，不是這種智商輾壓的高級篡位)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「垂直權限提升 (Vertical Privilege Escalation / Privilege Elevation)」**。
    *   **授權缺失 (Broken Access Control)：** 這是 OWASP Top 10 中名列前茅的巨大漏洞。API 後端只相信了前端傳來的 ID 參數 (Insecure Direct Object Reference, IDOR)，卻沒有去驗證「目前登入的這個 Session Token 持有人，他的權限群組 (Role) 到底有沒有大到可以看這個 ID」。
    *   **垂直 (Vertical) vs 水平 (Horizontal)：**
        *   **Vertical (垂直)：** 普通 User (只能改地址) 變成了 Admin/Management (具有看薪水、改薪水、刪除帳號的特權)。權限**「向上」**爬升了階級。
        *   **Horizontal (水平)：** User A (只能看自己的地址) 無意間看到了 User B (也是普通員工) 的地址。權限階級沒變，但看到了「同輩份」但不屬於自己的資料。
    *   題幹中基層員工修改了 CEO 的高特權資料，符合垂直權限提升的定義。

#### **5. To comply with strict financial regulations, a bank's trading application must ensure that once a trade is executed by a broker, the broker can never later claim, "I did not authorize that trade." To achieve this, the system generates a cryptographic digital signature using the broker's private key for every transaction block. Which specific security concept is directly satisfied by this implementation?**
**(為了向朝廷那要命的金融大法規低頭，一間皇家大錢莊的地下盤口 (trading application) 立了一條血淋淋的規矩：【『任何買賣手只要敢在盤口上拍下買單，就算明天這筆單跌到傾家蕩產，這名買賣手也絕對！死都不可以！在公堂之上耍賴大喊：「我不認識字！那張買單絕對不是老子我蓋章的！(can never later claim "I did not authorize that trade")」』！】。為了徹底封死這些賭徒耍賴的後路，大錢莊祭出了終極法寶：每一張盤口帳單，都必須逼這個買賣手，【把那張他自己用命根子保護、全天下只有他自己擁有的『私家獨門大掌印私鑰 (cryptographic digital signature using private key)』】，死死地印在帳單的正中央！請問，這道逼賭徒蓋下血手印的防賴帳大法陣，精確完美地實現了安防界裡的哪一道無上神諭？)**
A. Integrity (完整性是確保這張帳單上面的數字 100 塊不會被塗改成 200 塊，雖然這很重要，但它無法解決『是誰蓋這個章』的耍賴問題)
B. Authorization (這是決定你這賭徒有沒有本錢進入黃金大盤口的門衛，他不管防賴帳)
C. Non-Repudiation (這就是那令天下所有詐欺犯與耍賴賭徒聞風喪膽、絕對無法推翻翻供的：【『鐵證如山死活不可抵賴大天條 (Non-Repudiation)』】！只要這枚天下獨一無二的血手印驗證通過，你在公堂上就算喊破喉嚨說這不是你按的，縣太爺也會直接把你拖下去砍了！這就是密碼學簽章帶來的最高境界：無法否認性！)
D. Availability (這管的是盤口會不會大當機關門，不管賭徒賴不賴帳)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「不可否認性 (Non-Repudiation)」** 是數位簽章 (Digital Signatures / Asymmetric Cryptography) 的核心價值之一。
    *   **痛點：** 在電子商務或金融交易中，如果沒有不可否認性，買家下單後反悔，可以輕易說「我的密碼被盜了，這筆訂單不是我下的」，賣家將求償無門。
    *   **解法：** 使用非對稱加密 (Asymmetric Crypto/PKI)。交易人必須用自己保管的**私鑰 (Private Key)** 對交易內容進行簽章加密。因為私鑰具備「唯一擁有性」。一旦法院用交易人的「公鑰 (Public Key)」成功解開了這個簽章，就等同於取得了數學鐵證，證明「這份文件【絕對】是這個持有私鑰的人所批准的，且他無法抵賴」。

#### **6. A corporate firewall is configured with a rule at the very bottom of its Access Control List (ACL) that explicitly drops any incoming packet that did not match any of the "Allow" rules listed above it. This specific configuration strategy perfectly illustrates which core security design principle?**
**(在把守帝國皇城大門的那座千鈞巨型防火牆 (corporate firewall) 裡面。城門口的一萬條『放行大名冊 (ACL)』的最底端最後一條，被大將軍用鮮血刻下了如此一段冰冷刺骨的死亡諭令：【『聽好！任何一個走到這個關卡的外鄉人，只要他身上的特徵，沒有符合上面那九千九百九十九條老子白紙黑字同意放行的條件！那不管他是來送包裹的還是來要飯的，【不需要問理由、不需要請示！直接給老子亂棍打死丟進護城河裡 (explicitly drops any incoming packet that did not match any of the "Allow" rules)！】』】。請問，這種猶如暴君般『寧可錯殺一萬，絕對不漏放半個無名小卒進城』的鐵血城門架構，完美詮釋了資安建城大清律例裡的哪一道金牌法則？)**
A. Defense in Depth (這是說後面還有很多道牆，而這題只探討眼前這面大牆的預設死命令法則)
B. Fail-Safe Defaults (Implicit Deny) (這就是以極端不信任人類聞名、六親不認的：【『絕對失效安全預設法則 / 隱性大封殺死令 (Fail-Safe Defaults / Implicit Deny)』】！它的哲學是：如果我不認識你，如果名單上沒有你，那我預設你就是帶著炸彈要來殺我的恐怖份子！所以在不知道該怎麼處理之前，【預設最安全的狀態 (Fail-Safe) 就是把你擋在門外 (Deny)！】！這是一切防火牆與門禁系統的地基！)
C. Least Common Mechanism (少共用模組法則，是說為了怕傳染病大家不要共用同一個水管，這跟門禁攔截無關)
D. Open Design (這是說要公開城牆設計圖讓天下人來檢驗，跟這道濫殺無辜的預設命令無關)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「失效安全預設 (Fail-Safe Defaults)」** 或稱 **「隱式拒絕 (Implicit Deny)」**。
    *   **定義：** 當一個系統遇到「未特別定義或預期外的狀況 (例如收到一個不知道該怎麼分類的網路封包)」時，系統預設的反應必須是拒絕存取 (Deny Access/Fail-Closed)，而不是好心放行 (Allow Access/Fail-Open)。
    *   **防火牆實務 (Default Deny Any-Any)：** 這是所有網路設備 (防火牆、路由器 ACL、AWS Security Groups) 組態設定的第一課。你先在一張白紙的最底層寫下 `Deny All Traffic`，然後才一條一條、最小幅度地往上加上如 `Allow Port 443` 或 `Allow Port 22 for Admin IP`)。如果一個封包沒有命中上面任一條 Allow Rule 落到了最後一行，就會吃下 Implicit Deny 被丟棄。

#### **7. A software engineering team is building a microservices architecture. They decide that the "Inventory Service" and the "Billing Service" will communicate over the internal network using mutual TLS (mTLS) for encryption and authentication. Furthermore, they implement a strict network policy blocking the two services from communicating with any database other than their own dedicated instances. What foundational security mindset are they applying to their internal network architecture?**
**(一支瘋狂的皇家工程兵團，正在打造一座由無數個小堡壘串聯而成的大都會 (microservices architecture)。這群瘋子為了防範內亂，居然對自己的弟兄下了最殘酷的禁令！他們規定大都會地圖上的『後勤糧草補給堡壘 (Inventory Service)』跟『財政部收稅大堡壘 (Billing Service)』，這兩棟蓋在【自家皇城內網 (internal network)】的自家人建築物！如果他們要走地道傳紙條聊天，居然【還得雙方拿出最高規格的加密公文跟雙重口令互相驗明正身 (using mutual TLS for encryption and authentication)！就好像對方是城外的敵國間諜一樣防備】！更病態的是，這兩座自家人的堡壘，被加上了粗大的鐵鍊，徹底釘死在自己的茅坑上！【這輩子除了自己專屬的那個金庫小房間外，絕對禁止跟別棟堡壘的小房間有任何一根網路線的互通 (blocking any connection to database other than their own)！】請問，這群工程兵團把自家的皇城內部當成修羅地獄來互相防備，貫徹的正是一套什麼樣駭人聽聞的嶄新神聖兵法？)**
A. Zero Trust Architecture (這就是近十年橫掃全宇宙、推翻古老和平幻象的：【『終極人間不信大陣法：零信任防禦骨架 (Zero Trust Architecture)』】！這套兵法的核心信仰只有一個：【『老子連自己老媽都不信！別以為你拿到內網大城的護照就等同於好人！內網外網一樣都有內鬼漫天飛舞！所有的微小堡壘之間，每次見面都要重新查身分證！所有的道路能切多斷就切多斷 (Micro-segmentation)』】！)
B. Perimeter-Based Security (Castle-and-Moat) (這剛好是 Zero Trust 想要推翻掉的【古城牆舊思維 (Perimeter-Based)】！舊思維覺得只要進了外城門，皇城裡面的弟兄就全都是好兄弟，大家不設防隨意聊天，殊不知只要城門一破，裡面就像綿羊一樣被駭客吃到撐死)
C. Security by Obscurity (這是在玩躲貓貓藏紙條的無聊遊戲，而這群工程兵可是大張旗鼓裝修加密隧道，完全不是隱匿式安全)
D. Open Design (這是公開設計圖讓全世界檢驗，雖然這個陣法圖是可以公開，但這個防禦思想的主軸不是因為它公開了，而是它內部互相『不信任』)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **「零信任架構 (Zero Trust Architecture, ZTA)」**。
    *   **古老思維 (Castle and Moat)：** 傳統架構中，工程師專注於在最外圍 (DMZ/Internet Edge) 架設巨大的防火牆城牆 (Perimeter)。只要駭客沒打穿防火牆，內部的 Service A 和 Service B 之間就可以無條件、不加密 (HTTP) 地互相相信、互相溝通。這導致了如果駭客透過釣魚信件駭入內部一台員工電腦，他就可以在內網如入無人之境般橫向移動 (Lateral Movement)。
    *   **零信任思維：** "Never Trust, Always Verify (從不信任，持續驗證)"。ZTA 認為「內部網路跟外部網路一樣危險，沒有所謂的受信任區」。
        *   Service Mesh mTLS 分段防禦：即使在同一個 Kubernetes Cluster 內網裡，Inventory 和 Billing 這兩個自家服務要講話，也強制要求互相交換證書並加密通訊 (Authentication & Encryption)。
        *   微切分 (Micro-segmentation)：用硬指標限定誰只能跟誰講話。把內部攻擊面 (Blast Radius) 壓縮到最小，這就是 Zero Trust 的實踐。

#### **8. During a security audit, it is discovered that the company's flagship web application uses a single, shared "superadmin" service account database connection string hardcoded in the application's configuration file. Every single user action out on the frontend website, from a guest viewing the catalog to a manager deleting a product, is executed against the backend database using this one omnipotent account. Which principle has been catastrophically violated?**
**(在一年一度的照妖鏡大審判 (security audit) 中，安檢官差點沒被嚇出心臟病！他把這家店最賺錢的旗艦大商城剖開來一看，發現這家店蓋房子時犯下了全天下最弱智的低級死罪！原來，那座能呼風喚雨的『地底神聖大金庫 (backend database)』，它的最高統帥【無敵萬能大總裁鑰匙 (single shared superadmin service account string)】，居然被偷懶的工匠像黏口香糖一樣，死死地用黑筆刻寫在商城的公開告示板背後 (hardcoded in config file)！更荒謬可笑的是：【在這個商城外面，不管是無聊路過進來看個商品目錄的純潔死老百姓，還是想要放火燒了整個倉庫的大掌櫃。這家店的店小二，居然全是拿出同一把『無敵大總裁鑰匙』去開那座地底金庫的門，去執行所有的取件或燒倉命令 (every single user action executed using this one omnipotent account)】！請問，這種把毀滅國家大權下放給村口看門狗的白痴設計，是殘忍地把哪一道防禦界裡的神聖法則給放在地上摩擦？)**
A. Separation of Duties (這是一件事分兩個人做防作弊，這間店現在連最基礎的防外人都沒做好，這不是職務分割探討的層次)
B. Principle of Least Privilege (這就是這場大悲劇的千古原罪，徹頭徹尾地違背並強姦了：【『最小極限之剝削大特權天條 (Principle of Least Privilege)』】！這條天諭明明咆哮著：那個只負責幫路人拿型錄的店小二，他只能擁有一張『只准讀字不准動手』的老百姓乞丐通行證！你他媽的怎麼可以給一個端盤子的路人，發配一張【『可以把整座金庫炸爛的五星上將大總管萬能黑卡』】去執行工作啊！這會讓任何一個小小的網頁漏洞，瞬間引爆變成核彈級別的滅國大屠殺！)
C. Kerckhoffs's Principle (這是不要依賴隱匿式防禦，雖然他們也確實把密碼刻在門上很蠢，但「權限過大」才是這題造成災難的主因)
D. Psychological Acceptability (這是系統好不好用，把總管鑰匙給大家用當然超好用超不會報錯，所以他反而符合了錯誤的心理可接受度)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「最小權限原則 (Principle of Least Privilege, PoLP)」** 遭到災難性破壞。
    *   **定義：** 一個實體 (User, Program, Service Account) 應該【只被授予其執行業務所需之「最少必要權限」與「最短時間」】。
    *   **常見反模式 (Anti-pattern)：** 開發者為了省事，在 Java 或 Node.js 程式裡面，直接把一個具有 `DROP TABLE`, `DBA` 特權的 `sa` 或 `root` 帳密寫死在 Web App 裡連線資料庫。
    *   **災難後果：** 如果網站有一個非常微小的 SQL Injection 漏洞 (例如在商品搜尋欄)。駭客送出攻擊字串後，這個 Web App 會【拿著 `sa` (Superadmin) 的無敵權限】，把那句惡意指令送到資料庫執行。因為是 DBA 身分，駭客就可以直接 `DROP DATABASE` 把整間公司資料刪光，或是用 `xp_cmdshell` (SQL Server) 拿到作業系統控制權。如果 Web App 只有 "唯讀 (Read-only)" 的乞丐帳號，這個漏洞造成的傷害 (Blast Radius) 會小成千上萬倍。
