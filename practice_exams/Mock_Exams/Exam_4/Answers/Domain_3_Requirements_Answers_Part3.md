# 第四套全真模擬試題 (Exam 4) - 答案與詳解本
## 領域 3：安全的軟體需求 (Secure Software Requirements) (18題) - Part 3 (Q13-Q18)

---

#### **13. When defining requirements for "Data Masking," a business stakeholder requests that customer credit card numbers be stored in the database but completely obscured when viewed by customer service representatives, showing only the last 4 digits (e.g., `****-****-****-1234`). Which of the following is true regarding this requirement?**
**(在為一間『皇家四海錢莊』編寫防止客服小二偷看客人信用卡的『蒙眼大布條大法 (Data Masking)』時。那個只知道算錢的老掌櫃跑來下令：『聽好！把這群土豪的十六碼金元寶卡號，原封不動地鎖進地底的鐵保險箱裡 (stored in the database)！但是！當上面那些接電話的客服小二，打開他們的客棧櫃檯簿子要看卡號時。這簿子上的數字，【必須被施法打上厚厚的馬賽克，頂多只能讓這小二看到最後面的四隻腳 (`****-****-****-1234`)！】』請問。針對老掌櫃下達的這道瞎眼大陣法，在天下武林裡，哪一句話才是看透這套陣法底細的最精確真理？)**
A. Data Masking is a form of strong, irreversible cryptographic hashing. (這是把信用卡丟進碎肉機攪碎成肉泥的雜湊大毀滅法，如果真攪碎了，這錢莊永遠也別想扣到客人的錢了，這絕不是只把眼睛矇起來的馬賽克)
B. Data Masking is a presentation-layer control designed to protect confidentiality from unauthorized viewing; the underlying data in the database remains intact and usable by authorized backend processes. (這就是一語道破這塊蒙眼破布真面目的：【『這就是專門用來遮掩凡夫俗子肉眼的《門面級展示層大眼罩 (presentation-layer control)》！』】！它存在的唯一目的，就是為了保住那神聖的『機密性大女神 (protect confidentiality)』，讓那個權限不夠的客服小二，就算盯著螢幕看瞎了眼，也看不到完整的 16 碼數字 (from unauthorized viewing)！但最神妙的是，如果我們掀開這塊布，會發現【『那躺在地底保險箱裡的 16 碼金牌，依然完好如初、一字不漏地被保留著 (underlying data remains intact)！』】。這讓錢莊半夜在背後運轉的『自動扣款機器大怪獸 (authorized backend processes)』，依然能拿出完整的 16 碼去結帳扣錢！這就是這招「只蒙人眼、不蒙機器」的神奇奧義！)
C. Data Masking perfectly fulfills the requirement for "Data at Rest Encryption." (這個眼罩只遮螢幕，它根本沒有為躺在鐵保險箱裡睡覺的那塊金牌套上任何加密鎖 (Data at Rest)！如果小偷直接把保險箱搬走，這眼罩就成了笑話！)
D. Masked data can be easily unmasked by the frontend browser using JavaScript. (如果這眼罩是用紙做成的，可以讓小二自己在瀏覽器裡按 F12 鍵就把布扯下來 (unmasked by JavaScript)。那這塊眼罩就是個會讓全天下笑掉大牙的超級安防大漏洞！真正的遮罩必須在後端伺服器出門前就塗好墨水！)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「資料遮罩 (Dynamic Data Masking)」** 的核心本質。
    *   **展示層控制 (Presentation-layer Control)：** 遮罩 (如顯示 `****1234`) 的**唯一目的**，是防止敏感資料被【有合法登入權限，但沒有業務需求 (Need-to-Know)】的低階員工 (如客服、外包開發者) 從 UI 畫面上「過度讀取」。它是一種 "保護機密性 (Confidentiality)" 的存取控制。
    *   **底層資料完好 (Data Remains Intact)：** 這是 Masking 跟 Hashing (雜湊) 或 Tokenization (代碼化) 最大的差異。資料庫裡存的【依然是明文的 16 碼】。所以當高權限的 "每月定期扣款 Batch Server" 去讀取資料庫時，它拿到的是完整的卡號，系統仍然可正常營運。
    *   *(注意選項 C：遮罩不能取代靜態加密 Data-at-Rest Encryption (如 TDE 或 AES)。防內鬼用遮罩，防整顆硬碟被偷要用加密，兩者是縱深防禦的不同層次)。*

#### **14. A risk assessment identifies that highly privileged administrators might abuse their power to modify audit logs and cover their tracks. To mitigate this, a requirement is drafted: "The application's audit logs must be immediately transmitted to a centralized, isolated, write-once-read-many (WORM) logging server." Which security concept does this requirement directly support?**
**(在一場血淋淋的城防演習大會上 (risk assessment)。大將軍絕望地看著那群握有皇城大門鑰匙、可以隻手遮天的『內閣大總管與侍衛隊長們 (highly privileged administrators)』！大將軍發現了一個恐怖的事實：這群無法無天的總管，如果他們半夜去國庫偷了黃金，他們大可以用自己手上的尚方寶劍，把那本記著城池所有進出紀錄的【『老天爺生死簿 (audit logs)』】給直接撕毀、燒掉，甚至塗改！徹徹底底地做到死無對證 (cover their tracks)！為了防範這群總管造反，大將軍在城牆上刻下一道死令：【『從今以後！城門口只要有一隻蒼蠅飛過，這本『老天爺生死簿』，必須在蒼蠅飛過去的第一秒鐘，就【『立刻被飛鴿傳書，發送到那座深藏在海底、連玉皇大帝也進不去、一旦把字刻上大石頭就只能看、絕對無法被任何力量抹除塗改半筆的「深海孤島大監獄 (centralized, isolated, WORM logging server)」』！】請問！這座連神仙都能囚禁、只准寫不准改的深海孤島，他所保衛的這座皇城，是哪一道堅不可摧的安防天條神像？)**
A. Availability (可用性是這座孤島不會被海嘯淹沒而關門，但它無法解釋為什麼這孤島要「只准寫一次不准改」的這種防總管塗改設計)
B. Non-Repudiation and Accountability (這就是那將一切內鬼與大老虎釘死在恥辱柱上、永不翻案的：【『無可抵賴之終極神聖罪證大天條 (Non-Repudiation) / 與血債血償之究極問責大審判 (Accountability)』】！這道天條殘酷地宣誓：如果你這總管偷了錢，這筆被刻在海底大石頭上的罪證 (WORM log)，會永遠死死咬住你的脖子。就算你權力再大，你也【絕對無法否認 (Non-Repudiation)】你昨晚進過國庫！有了這塊大石頭，朝廷在辦案宣判時，就能鐵證如山地抓出到底是哪個王八蛋幹的好事【(Accountability/軌跡歸責)】！這是一切稽核大清算 (Audit) 最恐怖的基石！)
C. Authentication (這是在城門口座驗明正身看你是不是大總管本人，不是把你做過的好事永遠釘死在海底石頭上)
D. Least Privilege (最小權限是不讓總管拿到不該拿的鑰匙，但大總管本來就有所有鑰匙。這題探討的是：當有權人作惡時，怎麼防止他們毀屍滅跡？這是軌跡保存，不是收回鑰匙)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「不可否認性 (Non-Repudiation)」** 與 **「問責性/究責性 (Accountability)」**。
    *   **Insider Threat (內部威脅) 困境：** 一個 System Admin / DBA，擁有 Root 權限。他如果有心幹壞事，做完後第一件事就是去 `/var/log` 裡面把自己的 Audit Logs 刪光或篡改 (Cover their tracks / 掩蓋足跡)。
    *   **WORM (Write-Once-Read-Many) 日誌伺服器：** 這是最高級的稽核防禦建築 (如 Amazon S3 Object Lock 或專用硬體)。當應用程式產生一筆 Log 的瞬間 (例如 Syslog)，它會立即把 Log 射向遠方一台連 Sys Admin 也無法登入的隔離伺服器。而且這台伺服器的磁碟設定為「只能寫入一次，寫完後五年內即使擁有 Root 權限的人下 `rm -rf` 也絕對刪不掉」。
    *   這保障了【日誌的完整性 (Log Integrity)】。而不可被竄改的完整日誌，就是達成【法律級不可否認性 (Non-Repudiation)】與【事後追究責任 (Accountability/Traceability)】的最關鍵證據基石 (Evidence)。

#### **15. A development team is tasked with building a web application that handles sensitive payment card data. They must adhere to the Payment Card Industry Data Security Standard (PCI-DSS). Which of the following statements about incorporating PCI-DSS into software requirements is correct?**
**(一支準備在中原大地上，蓋起一座日進斗金的『萬國商會大金庫 (handles payment card data)』的王牌工匠兵團。他們接到了那本由全天下幾大錢莊聯合頒布、不遵守就直接全城抄家砸爛的【『金剛伏魔 PCI-DSS 信用卡地獄大憲章』】！面對這本厚重如山的憲章，這群原本只會隨便蓋茅草屋的工匠，應該要用什麼樣的態度，把這本憲章化作他們手中的釘子與大槌 (incorporating PCI-DSS into software requirements) 才是唯一活命的正道？)**
A. PCI-DSS is a guideline; developers can choose to ignore requirements if they slow down the Agile sprint. (如果在敏捷開發衝刺的路上，工匠敢因為「嫌麻煩」而把這本地獄大憲章當作垃圾扔掉。這整間商會明天就會被五大錢莊聯合封殺，拔掉刷卡小金庫，直接破產倒閉。這絕對不是鬧著玩的指南！)
B. PCI-DSS requirements (like encrypting cardholder data and not storing CVV codes) must be explicitly translated into verifiable software requirements to achieve compliance and pass the mandatory audit. (這就是能保住商會大印不被抄家、讓大審查官滿意蓋過關章的唯一免死金牌法門：【『將這本地獄大憲章裡的每一句死命令，一字不落地翻譯成《可被大鐵槌用力敲打、可被大火嚴酷測試檢驗的正經軟體規格大藍圖 (verifiable software requirements)》！』】。例如：憲章規定不准留卡片背後的三碼 (not storing CVV)。就必須在藍圖上血淋淋寫下：『開發者，就算天塌下來，你的資料庫裡如果出現了 CVV 這三個字母的欄位，我就把你手砍斷！』！只有這種近乎變態的轉譯與明確指令，這座大金庫才能在朝廷那場恐怖的大稽查中活下來 (achieve compliance and pass mandatory audit)！)
C. As long as the production servers have a firewall, the application code itself does not need to worry about PCI-DSS requirements. (就算城門口擺了一百架大砲防小偷 (firewall)。如果你的工匠在城裡的帳簿上，大喇喇地把全天下客人的信用卡密碼跟底褲顏色全寫在牆壁上讓大家看。這防火牆有個屁用？應用程式本身才是這部憲章約束的靈魂地獄！)
D. PCI-DSS only applies to the hardware infrastructure, not to the software development lifecycle. (這法典管天管地，它包含了整整兩個章節 (Req 6) 專門在釘死你們這群寫軟體的工匠，逼你們做 Code Review 跟源碼掃描，它絕對深深吃進了建造車子的流水線 (SSDLC) 裡！)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 強調在將 **合規框架 (Compliance Frameworks)** 如 PCI-DSS 融入 SSDLC 時，必須將其具體化為 **「可驗證的軟體需求 (Verifiable Software Requirements)」**。
    *   **PCI-DSS 的強制性：** 它不是軟性指南 (Guideline)，它是業界的強制合約。不遵守的企業將面臨每月數萬美元的罰款，甚至被 Visa/Mastercard 直接拔除刷卡資格，對電商而言這是死刑。
    *   **具體轉譯的必要性：** 法規中的條文 (例如 Req 3.2.2: "Do not store the card validation code or value after authorization")。不能只停留在主管的口頭宣導。系統分析師必須把這句話，轉變為明確的 JIRA Software Requirement："API 伺服器在收到第三方支付閘道回傳『交易授權成功』的 JSON Response 後，【必須立刻將記憶體中的 3 碼 CVV 變數清空 / Nullify】，且【絕對不得】寫入任何 Log 檔或 Database Table 中。" 這樣 QA 才有辦法寫 Test Case 來 Validate 這個合規要求。

#### **16. When gathering privacy requirements for a new mobile application that targets children under 13 in the United States, which specific federal regulation MUST be analyzed to dictate restrictions on data collection, parental consent, and data sharing?**
**(一家想在『美麗堅大帝國 (United States)』的集市上，推出一款專門給『那些連十三歲毛都還沒長齊的小毛孩 (targets children under 13)』玩的『掌上小木馬大遊戲 (mobile application)』工坊。在他們準備開始大量騙這群小毛孩交出名字跟家庭住址之前 (data collection)。安防大軍急忙衝出來，拿著一本大帝國聯邦最高調查局親簽的絕命法典，死死抵住工坊老闆的喉嚨：【『聽好！在你們還沒搞懂這本法典裡，關於怎麼叫這群小鬼跪著回家找他們爹娘拿「同意書 (parental consent)」，還有你們這黑心工坊敢把小鬼資料賣去哪裡 (data sharing) 的死規定之前！你們連一顆鈕扣都不准賣！否則大帝國的 FBI 隔天就來抄你滿門！』】請問，這本專門保護全天下十三歲以下小屁孩隱私的霸道大法典，尊號為何？)**
A. GDPR (General Data Protection Regulation) (這是歐洲大陸保護成人的超級隱私大全，管不到美麗堅帝國的小孩身上，國界不符)
B. HIPAA (Health Insurance Portability and Accountability Act) (這是專門用來管太醫院病歷跟看病老翁隱私的，這款掌上小遊戲不量血壓不把脈，跟這法案毫無干係)
C. COPPA (Children's Online Privacy Protection Act) (這就是名震四海、專門拔刀保護祖國幼苗免於黑心商人荼毒的：【『全美兒童連線大隱私絕對保衛戰法案 (COPPA)』】！這條最高鐵腕法律死死地掐住商人的脖子：只要你的遊戲是做給十三歲以下的美國死孩童玩的。你他媽的如果要問他們的名字、信箱或是偷定位他們的腳印。你在問出第一句話之前！【必須、絕對、毫無懸念地，先取得他們背後那個會拿棍子打他們屁股的親生爹娘之『具體、可查核的批准大印章 (Verifiable Parental Consent)』！】否則你拿走小孩一筆資料，帝國法院就對你痛下幾萬美金的天價罰款大鍘刀！這是所有兒童軟體設計的第一道生死紅門！)
D. SOX (Sarbanes-Oxley Act) (這是管皇城大帳房跟防範大金控做假帳坑殺股民的防止金融貪汙大法，跟小屁孩打遊戲洩漏名字毫無交集)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **COPPA (Children's Online Privacy Protection Act)** 是美國聯邦貿易委員會 (FTC) 執行的一項聯邦法律。
    *   **規範對象與年齡：** 專門針對服務對象涵蓋 **美國 13 歲以下兒童 (Children under 13)** 的商業網站或線上服務 (包含 Mobile Apps, IoT 玩具)。
    *   **核心安全與隱私需求 (Privacy Requirements)：** 在規劃這類 App 的註冊流程 (User Registration flow) 時。如果業務方要求收集小孩的 PII (Personal Identifiable Information，如全名、Email、GPS 定位、甚至是一張包含人臉的自拍照)。系統設計師不能直接彈出一個 "輸入姓名" 的欄位。
    *   他必須在需求清單裡加入一項繁雜的底層機制：**「可驗證的父母同意 (Verifiable Parental Consent)」**。也就是 App 必須先透過扣信用卡 1 美元、或是打電話給家長確認身分後，才能解鎖讓小孩填寫個資的畫面。這是不可逆的強硬隱私合規需求。
    *   *(A GDPR 是歐洲，B HIPAA 是醫療，D SOX 是上市公司財報防弊)*。

#### **17. A security architect is defining requirements for protecting "Data in Transit" for a new public-facing API. Which of the following is the MOST appropriate technical requirement to specify?**
**(一名老謀深算的安防大將軍，正站在一座全新打造、對著外面那群餓狼強盜大開城門的『天下總交換出入口 (public-facing API)』前，低頭寫著保護那些在網路上飛鴿傳書的鳥兒不被弓箭射下來的『終極空中大保鏢條約 (protecting Data in Transit)』。而在他深思熟慮寫下的四種安控法陣中，到底哪一道，才是【『最具備現代神鬼科技水準，能把半空中的飛鴿從頭武裝到腳，讓千千萬萬的駭客弓箭手只能在底下哭泣乾瞪眼的最完美且無懈可擊的天羅地網大殺招 (MOST appropriate)』】？)**
A. "All API endpoints shall require mutual TLS (mTLS) authentication for all external mobile app users." (mTLS 是逼迫城外幾百萬拿著手機的鄉巴佬平民，每個人都要去打鐵舖自己打一把幾十斤重的數位鐵鑰匙來交換。這不僅會逼瘋這幾百萬老百姓，這在對外開放的公眾大門 (public-facing) 上更是弱智且極度難以維護的災難佈署，這不切實際)
B. "The API shall encrypt all responses using a proprietary substitution cipher before transmitting." (使用自家工巧匠自創的「密碼輪盤亂貼小替換術 (proprietary substitution cipher)」？這就是被安防祖師爺唾棄到底的「隱匿式垃圾安全」。只要敵軍拿計算機算個兩天，這種紙糊的加密法就會崩潰瓦解)
C. "The API must only be accessible over HTTPS using TLS v1.2 or higher, with strong cipher suites enabling Forward Secrecy, and enforce HTTP Strict Transport Security (HSTS)." (這就是那道集天下防禦精華於一身、堪稱教科書等級的：【『絕對無敵神盾局之終極連環防彈衣大陣法！』】！這道將軍的死命令，字字如金，沒有一句廢話：第一、你他媽只能用最高級別的 TLS 1.2 以上加密隧道 (HTTPS only)！第二、隧道裡面那些用來加密的鎖頭，必須是最高純度的！而且這鎖頭必須自帶【『前向保密大絕招 (Forward Secrecy)』】！這確保了萬一老將軍十年後把大門的萬能鑰匙弄丟了，敵軍也絕對解不開今天我們在空中傳的這隻鴿子密信！第三、你要在城牆大門掛上【『HSTS 絕對禁止降級逼迫走加密隧道死命令牌』】！這完全堵死了想把加密降級成明文偷看的宵小之路！這句話，完美達到了現代 API 最頂級的傳輸防護大業！)
D. "The API shall hash all traffic using MD5 before sending it over the network." (MD5 是早就被歷史丟進墳墓的爛雜湊法，而且雜湊是單向破壞，不是用來在雙方通訊之間雙向加密傳輸用的。你把它全雜湊了，對面收到也只會看到一堆亂碼解不回來)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是針對 **現代 Web API / HTTPS 傳輸安全 (Data in Transit)** 寫得最嚴謹且符合當下業界標準的技術需求 (Technical Requirement)。
    *   **分解這句完美的安控需求：**
        1.  **"only accessible over HTTPS using TLS 1.2 or higher"：** 明確禁止了被破解的 SSL v2/v3 以及較弱的 TLS 1.0/1.1。而且禁止 HTTP 明文傳輸。
        2.  **"strong cipher suites enabling Forward Secrecy (FS / PFS)"：** 前向保密 (如 ECDHE)。這完美防禦了「現在被側錄竊聽，未來等私鑰外洩後再慢慢解密」的攻擊手法。因為FS會為每一個新的連線握手，產生一把「立刻拋棄」的臨時 Session Key。
        3.  **"enforce HTTP Strict Transport Security (HSTS)"：** 這是防範駭客在咖啡廳發動「SSL 剝離攻擊 (SSL Stripping/MitM)」的終極殺招。它強制瀏覽器 (或 Client 端)："未來一年內，你連這家銀行，絕對不准使用 `http://` 協議，連重定向都不行，一開始就硬塞 `https://`"。
    *   *(選項 A 中的 mTLS 雙向認證通常用在 B2B Server-to-Server 的內網或微服務之間。要在 Public Mobile App 上發發幾百萬張 Client Certificate 給末端消費者是不切實際且維運成本極高的)。*

#### **18. In the context of secure software requirements, what is the primary purpose of defining a "Subject" and an "Object"?**
**(在所有初探這本『資安防禦安防大藍圖 (secure software requirements)』的小書僮心裡，都有一個非常困惑的千古大謎團！為什麼這本大藍圖的首頁，總是要咬文嚼字地逼迫所有人死死背下，並去劃分那什麼鬼【「這傢伙叫行動大主體 (Subject)」】還有【「那玩意兒叫被動大客體 (Object)」】？把這兩尊神像分得清清楚楚，到底隱藏著建立哪一派天下安防大體系的何種終極奧義 (primary purpose)？)**
A. To define the relationship between the database tables (Objects) and the foreign keys (Subjects). (把這兩個偉大哲學名詞，拿去解釋資料庫的關聯鍵，這簡直是暴殄天物、牛頭不對馬嘴)
B. To establish the foundational vocabulary for Access Control Requirements, where the Subject (e.g., a user, a process) is the active entity requesting access, and the Object (e.g., a file, a database record) is the passive entity being accessed. (這就是一語道破天機、奠定古今中外一切保險箱與大門防線之母的：【『終極《出入平安大審判生死門 (Access Control Requirements)》的創世基石與絕對二元對立法則！』】！這道法則無比霸道地將世界劈成兩半：【一半是永遠不安分、想要大動干戈去踹門、去拿寶劍、去讀聖旨的那個『發動攻擊之活生生大實體—主體 (Subject/user/process)』】！而另一半，則是永遠如死屍般躺在保險箱裡，默默等著被別人拿出來賞玩或撕毀的【『被動死物—客體 (Object/file/record)』】。只有當你把這世界的「進攻者」跟「防守物」給切得一乾二淨。接下來那些諸如『MAC, DAC, RBAC』等所有高不可攀的守門法陣，才能在這兩者之間，畫下一道死死卡住咽喉的『開門授權大紅線 (Access Matrix)』！這句話就是大門防禦學的創世紀之語！)
C. To specify the frontend UI components (Subjects) and the backend API endpoints (Objects). (前端螢幕的按鈕跟後方的大機器人通信，這只是系統組件的傳遞，絕不能用來涵蓋代表「人與資料」之間生死存取大權的本質名詞)
D. To differentiate between the person buying the software (Subject) and the developer writing it (Object). (買軟體的老闆跟打鐵的工匠，這是在講合約買賣的身分，這種社會關係更跟系統內部的刀光劍影防衛機制扯不上半點邊)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「主體 (Subject)」** 與 **「客體 (Object)」** 是建構所有 **存取控制 (Access Control)** 機制、原則與矩陣的共同語言與最底層根基。
    *   在任何資安架構與需求分析中：
        *   **Subject (主體 - 發起動作的主動方)：** 可以是一個人類使用者 (User A)、一個執行中的惡意軟體 (Process B)、或是一個背景服務帳號 (Service C)。它要求 (Requests) 去做某件事。
        *   **Object (客體 - 承受動作的被動方)：** 被存取的資源。可以是一個機密檔案 (File X)、一個資料庫的表格 (Table Y)、或是一台印表機硬體 (Device Z)。
        *   **Action (動作 / Right)：** 主體想對客體做的行為 (如：Read 讀取, Write 寫入, Execute 執行, Delete 刪除)。
    *   所有的安防需求 (Security Requirements)，最終的核心邏輯都是在寫下一本生死簿 (Access Control Matrix / 存取控制矩陣)："在什麼條件下，這個特定身分的【主體】，被允許去對那個特定的【客體】，執行那個致命的【動作】"。這兩者釐清了，安全機制的邊界才能被精確劃定。
