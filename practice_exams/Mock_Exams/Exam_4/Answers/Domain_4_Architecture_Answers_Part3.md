# 第四套全真模擬試題 (Exam 4) - 答案與詳解本
## 領域 4：安全的軟體架構與設計 (Secure Software Architecture and Design) (18題) - Part 3 (Q13-Q18)

---

#### **13. When designing a resilient architecture for a global SaaS application, the architect decides to distribute the database across three different geographical regions using asynchronous replication. In the event of a catastrophic failure in Region A, the system will automatically failover to Region B. This architectural decision primarily addresses which concept?**
**(一家在全球呼風喚雨、每天都有幾千億兩黃金流水進出的『雲端大錢莊 (global SaaS application)』。大風水師在規劃金庫的藏寶圖時，做出了一個無比霸氣的決定：【『聽好！我們絕不把雞蛋全放在一個籃子裡！老子要在天下東南西北三個最富饒的大洲，各挖一個一模一樣的地底大金庫 (distribute database across three regions)！而且！這三個金庫會有專屬的地底無人馬車，每天半夜互相偷偷把當天的帳本抄寫傳遞 (asynchronous replication)！萬一哪天東方大洲的金庫被天火隕石直接砸出一個大坑，連渣都不剩 (catastrophic failure in Region A)！地底的機關會在一秒鐘內，自動把所有的客人引導到南方大洲那個毫髮無傷的備用金庫去結帳 (automatically failover to Region B)！』】請問！大風水師這套花費無數黃金打造的『狡兔三窟大陣法』，其最核心、最不想面對的恐懼，是為了解決哪一項保命大危機 (primarily addresses which concept)？)**
A. Confidentiality (機密性是把金庫的門鎖得死死的不讓小偷看，而不是蓋三個金庫怕被隕石砸。這三個金庫如果沒上鎖，機密性還是會吹彈可破)
B. Disaster Recovery (and Availability) (這就是那名垂青史、用無數黃金堆疊出來的：【『逆天續命之終極災難大復原 (Disaster Recovery) / 與永不打烊之九命怪貓高可用性大陣法 (Availability)！』】。這套陣法是建立在一個殘酷的現實上：『地球上沒有任何一座城池是絕對不會被地震、海嘯或敵國核彈轟炸的』。所以你必須把城池『複製、貼上』到另一個相隔幾千公里的無災大陸上！當第一座城池被隕石毀滅時 (Catastrophic Failure)！你的生意、你的金流，能透過這套『自動異地備援大結界 (Failover)』，在最短的時間內 (RTO)，從地獄裡爬回來繼續賺錢！這就是架構設計中，最昂貴但也最保命的可用性設計大哲學！)
C. Non-Repudiation (不可否認性是怕客人在金庫存了錢隔天不認帳，這跟金庫被隕石砸毀要怎麼蓋備胎完全無關)
D. Data Sovereignty (資料主權是把資料死死綁在某個國家的泥土裡不准出境。而這題大風水師是把金庫蓋在「三個不同的地理大洲」，這甚至是違反資料主權鎖國政策的，所以完全不是這個目的)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是系統架構中關於 **「災難復原 (Disaster Recovery, DR)」** 以及 **「高可用性 (High Availability, HA)」** 的經典設計。
    *   **CIA 三要點中的 A (Availability)：** 確保系統在遭受毀滅性打擊 (如 AWS 整個 us-east-1 區域斷電、機房火災) 時，仍能維持營運。
    *   **Geographical Distribution (地理分散) 與 Failover (故障轉移)：** 單一機房內的 Cluster (叢集) 只能防硬碟壞掉 (Local HA)。要防範區域級別的災難 (Region-level failure)，必須使用跨地理區域 (Cross-Region) 的部署。
    *   **非同步抄寫 (Asynchronous Replication)：** 為了不拖慢跨國連線的主資料庫效能，通常使用非同步抄寫。這雖然會有微小的資料遺失風險 (RPO > 0)，但能換來極高的存活率 (RTO 極短的 Auto-Failover)。

#### **14. An architect is designing an application that will process credit card payments. To minimize the application's PCI-DSS compliance scope, the architect decides the application will NOT collect or store credit card numbers at all. Instead, the UI will embed an iframe hosted directly by a third-party payment gateway (like Stripe). The third party handles the card data and simply returns a success/fail token to the application. What risk management strategy is the architect employing?**
**(一名窮得連買一把像樣的大鎖頭防盜門都買不起的窮工匠。有一天，老爺叫他蓋一間『能收受全天下客棧最昂貴之無價金牌 (credit card payments)』的銀舖小屋。工匠崩潰地發現：如果要親手碰這塊金牌，他必須跟全天下的五大錢莊簽下生死狀，保證他這間破茅屋有這世上最堅固的保險箱、有五百名錦衣衛站哨，這就是那逼死人的『PCI-DSS 合規煉獄大結界』！工匠這輩子也賠不起這筆防盜門的錢。於是！這窮工匠想出了一個堪稱鬼才的『李代桃僵大推託之術』：【『老子才不碰這塊燙手山芋！(WILL NOT collect or store credit card numbers at all)』】！他直接在自己的破茅屋牆上，挖出一個四四方方的狗洞 (embed an iframe)。這狗洞背後，直接連通到那間全天下最雄偉、防禦力最強的『史崔普官方大當鋪 (third-party payment gateway Stripe)』！客人是把金牌直接透過這狗洞塞進史崔普的櫃檯裡！史崔普把金牌融化結帳後，只遞出一張『這傢伙付過錢了』的破紙條 (success/fail token) 給工匠。工匠靠這招，完美地把「保護金牌不被偷」的殺頭死罪推得一乾二淨！請問，這窮工匠的這套兵法，在風險管理的四象限八卦陣裡，屬於最高境界的哪一招？)**
A. Risk Acceptance (風險接受是工匠自己拍胸脯說「就算茅屋被偷大爺我都賠得起，我來幹」。這題他是完全不想賠錢所以叫別人來扛)
B. Risk Avoidance (by outsourcing the high-risk function/data) (這就是風險管理最高奧義、將死神直接拒於千里之外的：【『乾坤大挪移之風險極限大迴避 (Risk Avoidance) / 把這顆定時炸彈丟出去外包 (outsourcing the high-risk function)』】！這招的哲學是：【只要我不擁有資料，資料就永遠不會從我這裡被偷走！】。透過 IFrame，這個應用程式的『範圍 (Scope)』被極度縮小了。這窮工匠的破伺服器連半張信用卡的影子都沒看過、沒記過。因此，那群兇神惡煞的 PCI-DSS 稽核官就算來抄家，也會發現工匠家裡徒四壁，只好乖乖蓋上「免查通行」的印章走人。這套戰略不僅省下幾百萬的防衛預算，更徹底消滅了被駭客入侵盜刷的本體風險點！)
C. Risk Mitigation (風險緩解是工匠自己花錢買五十把大鎖頭去鎖這塊金牌，把風險從 100 降到 20。但現在他是連碰都不碰，也就是把風險直接降成 0，所以這是迴避不是緩解)
D. Risk Exploitation (風險利用是那些專攻資安的傭兵集團，趁著天下大亂的時候跑出來賣保鏢服務賺風險財。工匠躲都來不及了，怎麼可能去賺這風險財)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「風險迴避 (Risk Avoidance)」** 的核心概念，以及在 PCI-DSS 實務中最常見的架構設計。
    *   **Risk Mitigation vs Avoidance：**
        *   Mitigation (緩解)：你自己做支付系統，但你買了最頂級的 WAF，實施了 Tokenization，通過了 PCI-DSS 稽核。(風險還在，只是變小了)。
        *   Avoidance (迴避)：你**完全不從事**產生該風險的活動。這是最乾淨徹底的做法。
    *   **PCI-DSS Scope Reduction (合規範圍縮減)：** 如果你的伺服器收到使用者的 HTTP POST 裡面包含完整的 PAN (Primary Account Number，16碼卡號)。那你的 Web 伺服器、Application、資料庫、網段，全部會被畫入 PCI-DSS 稽核宇宙 (Scope)。這將帶來龐大且昂貴的稽核成本。
    *   **IFrame / Hosted Fields 架構：** 使用 Stripe 或 Braintree 等第三方 Gateway 提供的 Hosted Payment Page。消費者的瀏覽器是直接將卡號送到 Stripe 的伺服器，完全不會流經 (flow through) 你的伺服器。你徹底「迴避」了接觸敏感資料的風險。

#### **15. During a security design review, an architect notices that an application uses a custom hashing algorithm created by a junior developer to store passwords, instead of a proven algorithm like Argon2 or bcrypt. The developer argues their algorithm is faster. Why is this a critical architectural flaw?**
**(一名滿頭白髮、眼裡容不下一粒沙的安防老祖宗 (architect)。在審閱那本剛寫好的『保護全城大門金鎖密碼鎖大陣 (store passwords)』造車圖時，老祖宗差點沒氣得當場把桌子給掀了！原來，這個剛出村子、連劍都拿不穩的菜鳥工匠，居然放棄了祖師爺傳承百年、千金不換的《阿貢貳號絕命防爆雜湊大陣 (proven algorithm like Argon2 or bcrypt)》。反而！他自作聰明地在破布上，畫了一套他昨晚吃飽飯後自己發明的狗屁不通『土炮極速攪肉機密碼大陣 (custom hashing algorithm)』！這菜鳥還得意洋洋地頂嘴：『老祖宗你別氣！我發明的這套土炮陣法，雖然沒有阿貢貳號複雜，但它跑得快得像風一樣 (faster)！這有什麼不好？』請問！老祖宗應該用哪一條鐵血大祖訓，狠狠地給這菜鳥一巴掌，點醒他這根本是在挖墳找死 (critical architectural flaw)？)**
A. Custom algorithms cannot be patented. (就算你這破東西可以拿去官府申請專利，它依然是個紙糊的爛東西，這跟法不法規的專利毫無關係)
B. It violates Kerckhoffs's Principle and the rule against "rolling your own crypto," as unvetted cryptographic designs are almost certainly flawed and easily compromised. (這就是密碼學界流傳千古、由無數前人用鮮血甚至滅國之災換來的血淚大鐵律：【『一巴掌拍死那些自以為是的蠢蛋之《柯克霍夫大原則 (Kerckhoffs's Principle)》！與絕對死命令《絕不准閉門造車自己捏大便密碼 (Don't roll your own crypto)》！』】。這兩條鐵律咆哮著：一套沒有經過全世界最聰明的數學家、最狠毒的駭客，每天拿著大刀砍了十年還砍不斷的防爆鎖，就絕對是一坨堪稱極致垃圾的破鐵！那菜鳥自吹自擂的所謂「跑得像風一樣快 (faster)」，在這世上，更是防禦字典裡的催命符！密碼學的真理是：【『越快的鎖，小偷去猜密碼的速度也越快 (更易被 Bruteforce)！真正保護密碼的鎖 (Argon2)，它必須是故意被設計得「重如泰山、慢如烏龜 (Key Stretching)」，用高昂的運算時間去活生生拖死小偷的窮舉大軍！』】這菜鳥犯了傲慢且無知致死的死罪！)
C. Argon2 requires too much bandwidth to transmit. (不管是阿貢二號還是土炮法，雜湊完的密碼長度都是幾個短短的字母數字 (hash string) 儲存在資料庫。這跟網路頻寬半毛錢關係都沒有)
D. Fast algorithms are always more secure. (大錯特錯的胡言亂語！在保護靜態密碼 (Password Hashing) 的領域，演算法「太快」正是災難！如果你用以極速聞名的 MD5，駭客的顯示卡每秒鐘能猜幾百億次，你就算密碼設 20 碼也會瞬間被解開！越慢的算法 (工作量證明/Key Derivation) 才越能保護密碼)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「Kerckhoffs's Principle (柯克霍夫原則)」** 與業界公認的黃金地雷 **"Don't roll your own crypto (不要發明自己的密碼學)"**。
    *   **密碼學的真理：** 在資訊安全中，唯一可以依賴的保密性，來自於「金鑰 (Key)」的不可預測性。而絕對「不可以」依賴「演算法本身的秘密性 (Security by Obscurity)」。
    *   **專業密碼演算法的歷練：** 諸如 AES, RSA, bcrypt, Argon2，都是經過全球頂尖數學與密碼學家數十年公開的同行評審 (Peer Review) 與極限攻擊測試。一個菜鳥開發者一個下午寫出來的 custom algorithm，必定存在致命的數學缺陷、碰撞漏洞 (Collisions) 或是邊際條件崩潰，駭客只要逆向工程 (Reverse Engineering) 拿到演算法流程，就能輕易復原所有密碼。
    *   **關於「執行速度 (Faster)」的陷阱：** 在密碼雜湊 (Password Hashing) 中，速度是一把雙面刃。太快代表攻擊者使用 GPU (顯示卡) 或 ASIC 進行暴力破解 (Brute-force) 或彩虹表 (Rainbow Table) 攻擊的成本極低。所以現代標準如 bcrypt, scrypt, Argon2 都有 **"Key Stretching (金鑰延展) / Work Factor"** 的設計理念，刻意消耗 CPU 或 Memory 來「拖慢」雜湊速度，從而以數學級別的差距摧毀攻擊者的運算優勢。

#### **16. A system is designed with a "Circuit Breaker" pattern. When a backend microservice begins failing (e.g., returning 500 Server Errors due to a database outage), the API Gateway detects this and automatically stops sending traffic to that failing service for 60 seconds, returning a pre-defined cached response to the user instead of hanging. What is the primary security/reliability benefit of this architectural pattern?**
**(在一座由無數個齒輪精巧咬合的微型小鋪大商城裡。總設計師在接客的大門口，裝設了一個被施了仙法的：【『絕命終結自動跳電大開關 (Circuit Breaker pattern / 斷路器模式)』】。這大開關的靈敏度極高！只要它發現：商城後台那間專門烤麵包的小鋪子，因為烤箱炸了而開始瘋狂地對客人大喊「店舖已倒閉 (returning 500 Server Errors)」時！這大門口的開關會【立刻！當場啪嗒一聲跳電！切斷所有還像喪屍一樣湧進來想買麵包的客流 (stops sending traffic to failing service)】！而且在接下來的一分鐘內，大門口只會用一個看板假人跟客人說「麵包賣完了請回」，絕不讓任何客人再去麵包鋪前苦苦排隊傻等 (returning cached response instead of hanging)！請問。這個會在危急時刻直接把路截斷的無情大開關，為這座脆弱的大商城，保住了哪一項最核心的生機？)**
A. It prevents SQL injection attacks on the backend service. (這大開關是保護店鋪不要被排隊的人潮踩垮的，它分辨不出客人嘴巴裡講的話有沒有帶著 SQL 注入的神經毒素，防堵毒藥是 WAF 門衛的職責)
B. It encrypts the data before it enters the database. (跳電開關是在控制流量的生死存亡，不是在做加解密的翻譯工作)
C. It prevents cascading failures across the entire system, protecting overall Availability during partial outages. (這就是斷路器陣法在微服務世界裡，那如神明般守護【『高可用性大女神 (protecting overall Availability)』】的終極奧義：【『斬斷萬惡連環大滅絕之阻斷級聯崩潰效應 (prevents cascading failures)！』】。微服務最恐怖的災難，就是「排隊排到死」。如果麵包鋪炸了，但大門口不拉下鐵捲門。全天下幾萬個客人就會在大門口無止盡地排隊等那塊不可能烤出來的麵包 (Thread Exhaustion / 資源耗盡)。更慘的是，這幾萬個苦苦排隊的客流，會把大門口、甚至是旁邊賣肉包子的隊伍也給一併徹底堵死！最後整座商城因為一間麵包鋪的死，被完全拖垮全滅 (Cascading Failures)！這無情的跳電開關，就是壯士斷腕！它讓這間死掉的麵包鋪喘息一分鐘，並且保護了其他九十九間店鋪不受波及，完美保全了整座城的命脈！)
D. It guarantees that users have strong passwords. (跳電開關是在管交通的交警，它不管你進城時拿的出的是強密碼還是弱密碼證件，這功能屬於剛才提過的身分驗證天壇)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是對軟體架構模式 **「斷路器 (Circuit Breaker Pattern)」** 對於 **高系統可靠度 (Reliability) 與可用性 (Availability)** 貢獻的標準描述。
    *   **微服務的痛點：雪崩效應 (Cascading Failures)**。
        *   在微服務架構中，Service A 呼叫 B，B 呼叫 C。如果 C 背後的資料庫掛了，C 每個請求要等 30 秒才 Timeout。
        *   這時大量新的 Request 湧入 B。B 的執行緒 (Threads) 和記憶體就會全部卡死在「等待 C」的狀態。
        *   接著 A 的資源也全卡死在等 B。最終導致整個應用程式全面癱瘓。這被稱為級聯崩潰或雪崩效應。
    *   **Circuit Breaker (斷路器) 的解法：**
        *   在 A 或 B 的 Client 端實施斷路器邏輯。它會監控對 C 呼叫的失敗率。
        *   一旦失敗率超過閾值 (例如 5 秒內 50% 報 500 error)，斷路器從 "Closed (導通)" 狀態切換為 **"Open (斷開)"** 狀態。
        *   此時，任何發向 C 的請求，會被直接在 Client 端阻截 (Fail Fast，立即拋出異常或回傳 Cache)，不再真實發送。
        *   這保護了 C 有時間重新啟動，也保護了 A 和 B 的執行緒不會被長時等待耗盡，極度穩定了整體的 Availability。

#### **17. In the context of secure architecture, what is the defining characteristic of a "Zero Trust" model compared to a traditional perimeter-based (Castle-and-Moat) model?**
**(在所有研讀兵法的安防大將軍眼裡，那套號稱能毀滅古帝國、重新建立起無敵新秩序的【『終極零信任大陣法 (Zero Trust model)』】。它到底憑藉著什麼樣的絕世瘋狂理念，把過去千年來一直被奉為神功的【『老套高牆深溝護城河兵法 (traditional perimeter-based / Castle-and-Moat)』】給狠狠踩在腳下碾碎？這套新陣法最變態、最不講武德的核心定義靈魂，究竟是什麼？)**
A. Zero Trust relies on a massive firewall at the edge of the network, assuming everything inside the firewall is safe. (這是在打臉自己！這正是古老老套的「城堡護城河模式 (Castle-and-Moat)」的腐敗思維！它迷信只要我城牆夠高，進到城裡的每個人都是純潔無瑕的好平民 (assuming inside is safe)！結果一旦有小偷挖地道跑進城裡，或者有內鬼作亂，這座沒有內部安檢的城堡就會從內部直接變成屠宰場！這正是零信任要徹底推翻的垃圾歷史觀念！)
B. Zero Trust assumes network location is irrelevant to security; all entities (internal or external) must be continuously authenticated, authorized, and validated before being granted access to any resource. (這就是零信任大陣法將整個世界徹底打碎重建的終極絕望審判法典：【『老子才不管你是從城外蠻荒進來的，還是本來就住在皇宮大內深處的死忠衛兵 (network location is irrelevant to security)！在老子眼裡，通通都是萬惡不赦的潛藏強盜！』】。這套瘋狂陣法宣告：【『【『網路邊界根本是個可笑的幻想！』】』】。每一隻會跑動的貓、每一條神仙傳令的狗 (all entities)。只要你每一次、每一分、每一秒想摸一下國庫的大銅門！你就必須、絕對、不可饒恕地被【一遍又一遍地驗明正身、搜刮底褲、查看你到底有沒有帶槍 (continuously authenticated and validated)！】不給無孔不入的持續驗證，休想碰到這座城裡的一磚一瓦！這就是名為零信任的癲狂防護極意！)
C. Zero Trust explicitly trusts all requests originating from IP addresses starting with `192.168.x.x`. (這就是在打擦邊球耍流氓！只要看到 192.168 (也就是自家人區域網路 IP) 就直接放進來？這又回到了「信任內網」的老路子！零信任的教義是：【內外網的 IP 都是屎，都不可信！】)
D. Zero Trust does not use encryption because it trusts the network cables. (零信任不但不相信人，它更不相信那些埋在地底下的銅線網路線！在零信任世界裡，就算線是你的，這條線的上下傳輸也必須全部被武裝包庇上最恐怖的加密大將軍鎧甲 (End-to-End Encryption)！)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是 **"Zero Trust Architecture (零信任架構/ZTA)"** 最根本的核心定義，這也是 NIST SP 800-207 所確立的最高原則。
    *   **傳統的 Castle-and-Moat (護城河與城堡/周邊防禦模型)：** 將網路分為「可信內網 (Trusted Internal)」與「不可信外網 (Untrusted Internet)」。只要你 VPN 連進了內網，你就可以暢行無阻。這種模型在遭遇釣魚攻擊 (Phishing) 或是內部威脅 (Insider Threat) 時，防禦如紙糊般脆弱。
    *   **Zero Trust (零信任) 的大破大立：**
        1.  **"Never Trust, Always Verify" (絕不信任，始終驗證)**。
        2.  **網路位置不再是信任的指標：** 就算你在公司總部六樓用插線的網路孔連線，你的可信度也**不等於**絕對安全。
        3.  **微分割 (Micro-segmentation) 與持續動態評估：** 每個封包 (Every Packet)、每次資源請求 (Every Request)。都要基於這個裝置的健康狀態 (Device Posture)、使用者的身分 (Identity)、以及當下的行為分析，重新計算一次你的「信任等級」。並嚴格施行最小權限原則 (Least Privilege)。

#### **18. A development team is designing a mobile app that allows users to send disappearing messages (like Snapchat). A key architectural requirement is that the server that routes the messages MUST NEVER be able to read the plaintext content of the messages, even if the server is compromised or subpoenaed by law enforcement. Which architectural encryption pattern MUST be implemented to satisfy this requirement?**
**(一支精銳工兵小隊正在打造一款名為『風中傳信不留痕 (disappearing messages)』的神秘小木馬手機對講機 (mobile app)。老爺下了一道極度苛刻、甚至是違抗皇權的高壓死命令：【『聽好！這對講機如果把話傳到天上我們的『中央發報電塔 (server that routes messages)』。這座這座發報塔，就算被天下最強的駭客攻破，甚至是天皇老子帶著十萬錦衣衛的搜查令來抄家 (subpoenaed by law enforcement)！這座電塔，也【絕對、死不可、絕對不可能】聽到那半空中飄過去的情話內容到底在講啥 (MUST NEVER be able to read plaintext content)！』】。請問，要造出這種連當家老爺跟發報塔自己都是瞎子與聾子的神怪對講機，必須要將哪一套天下無解的密碼學絕戶大陣寫進藍圖裡？)**
A. Data at Rest Encryption (Full Disk Encryption) on the server. (把伺服器硬碟鎖上，那是防硬碟被搬走。但如果伺服器裡的「發報程式」沒死，這程式依然可以看到客人發來的天雷地火情話明文，再自己加密存進硬碟。這根本滿足不了「發報塔自己聽不到」的條件！)
B. End-to-End Encryption (E2EE), where encryption and decryption happen only on the users' devices. (這就是讓各國情報局與朝廷太監恨得牙癢癢、被奉為加密通訊無上桂冠的：【『端到端無痕死絕加密大封鎖陣 (End-to-End Encryption, E2EE)！』】。這套陣法殘酷的真理就是：這把加密的情話大鎖，與那把能解開情話的唯一金鑰匙。這兩把神器，【只會在、且永遠只能在通話的『兩個人的手機大腦深處』被鑄造出來並互相交換 (encryption and decryption happen only on users' devices)！】。這意味著，中間那台所謂的中央發報電塔，它從頭到尾就是一個搬運了一箱封死鐵塊的苦力。就算這苦力被法官槍斃、被駭客拷問，他也無法交出鑰匙，因為他這輩子根本沒看過鑰匙長什麼樣子！這才是真正的絕對無解隱私神功！)
C. Transport Layer Security (TLS/HTTPS) between the app and the server. (這種套裝保鑣 (TLS) 只能保護情書在飛到電塔之間的半路不被野狗叼去。但當信鴿飛到電塔頂端時，保鑣會把信拆開交給電塔的大管家看。所以大管家 (server) 是能看到明文的，這破壞了死命令的需求！)
D. Symmetric Encryption using a key hardcoded in the server's source code. (把一把對稱金鑰匙像智障一樣大剌剌寫在伺服器門板的柱子上 (hardcoded key)？這不僅讓伺服器可以完全看透情書講啥，萬一被駭客摸到柱子，全天下幾百萬人的情書直接被一秒看光，這是連菜鳥都會笑的低級錯誤！)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「端對端加密 (End-to-End Encryption, E2EE)」** 的絕對本質與應用場景。
    *   **題意核心挑戰：** "Server must never be able to read plaintext (伺服器本身也絕不能看到明文)"。
    *   **TLS 的盲點 (Client-to-Server Encryption)：** 雖然 TLS (選項C) 加密了。但當封包送到伺服器 (Server) 上的 Nginx / API Gateway 時，就必須進行 "SSL Termination (SSL 卸載/解密)"。這個動作會讓伺服器的記憶體裡裝滿了使用者的「明文對話紀錄」。如果執法單位拿著搜索票或駭客取得了伺服器的 Root 權限，他們就可以監聽或調閱這些對話。
    *   **E2EE 的神威 (Client-to-Client Encryption)：** 例如 Signal, WhatsApp 採用的協定。加密與解密，【唯獨只發生在收發雙方的本機設備上 (e.g. 手機內的安全晶片 CPU)】。伺服器扮演的只是一台瞎眼的 "路由器 (Router)"，負責把看不懂的亂碼字串，從 A 轉發給 B。
    *   因為伺服器永遠沒有掌握能夠解密這串亂碼的 "Private Key (私鑰)"，所以達成了題幹要求的絕對隱私保障。
