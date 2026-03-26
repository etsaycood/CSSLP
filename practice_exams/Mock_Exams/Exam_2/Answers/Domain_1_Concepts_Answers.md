# 第二套全真模擬試題 (Exam 2) - 答案與詳解本
## 領域 1：安全的軟體概念 (Secure Software Concepts) (16題)

---

#### **1. A financial institution is designing a new high-value wire transfer application. The Chief Information Security Officer (CISO) is adamant that once a trader submits a wire transfer request exceeding $10 million, they must be mathematically prevented from later claiming, "I never authorized that transaction." To achieve this specific security requirement, which cryptographic implementation is the BEST choice?**
**(金融機構正在設計一套新的高價值電匯連線系統。資安長 (CISO) 堅持：一旦交易員送出超過一千萬美元的電匯請求，就必須在數學與密碼防線上，徹底阻止他們事後耍賴宣稱「我從來沒有授權過那筆交易」。為了達成這項特定的資安要求，在這系統實作上最好、機率上無懈可擊的密碼學武器選擇是什麼？)**
A. Implementing strong two-factor authentication (MFA) using hardware security keys for all traders. (對所有交易員實施硬體安全金鑰的強大雙因素認證 MFA)
B. Requiring the trader's client application to digitally sign the transaction payload using the trader's private key before submission. (要求交易員的客戶端軟體在送出交易封包前，必須使用交易員個人的『私鑰』對該封包進行「數位簽章 (Digital Signature)」)
C. Encrypting the entire network session using TLS 1.3 with Perfect Forward Secrecy (PFS). (使用具備完美前向保密的 TLS 1.3 去加密整個網路傳輸連線)
D. Storing all transaction logs in a centralized, append-only Security Information and Event Management (SIEM) system. (把所有交易日誌存在一個集中的、只能附加寫入的資安事件管理 SIEM 系統中)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 防止系統主體（或使用者）事後否認他們曾執行的操作，這種安全服務稱為 **「不可否認性 (Non-repudiation)」**。在密碼學中，要達到完美無瑕的不可否認性，唯一的黃金標準就是 **數位簽章 (Digital Signature)**。因為數位簽章是利用交易員「自己獨有、且理論上世界上只有他本人擁有的『私鑰 (Private Key)』」進行數學運算綁定該筆交易。一旦簽署，只要公鑰驗證通過，數學上即鐵證如山證明這絕對是他本人下的指令，他絕對無法抵賴 ( repudiate )。
    *   **為何 A, C, D 皆為干擾項：** MFA 是用來加強「一開始登入時的認證 (Authentication)」，它保證門是那個人開的，但不能對後續傳輸的那筆 1000 萬美金檔案簽字背書。TLS (選項C) 保證封包在網路線上不被別人偷看 (Confidentiality 機密性)。SIEM (選項D) 是用來滿足後續的稽核 (Auditing) 與當責性，如果日誌被竄改或帳號密碼是共用的，日誌就不能算是「數學保證的無法抵賴」。

#### **2. A development team is architecting a nuclear reactor monitoring system. The system polls temperature sensors every second. If the central control software loses its network connection to the sensors, the system's default behavior must be decided. According to the foundational security design principle of "Fail Safe / Fail Secure," what is the FIRST and MOST appropriate action the software should take upon losing connectivity?**
**(開發團隊正在架構一套核子反應爐的監控軟體。系統每一秒鐘都會去輪詢溫度感測器的數值。如果不幸地，中央控制軟體與感測器之間的網路連線斷線了！必須決定系統的預設反應行為。根據安全設計的基石原則「失效安全 / 故障保護 (Fail Safe / Fail Secure)」，軟體在失去連線時【第一優先且最洽當】的處置動作是什麼？)**
A. Suppress the error message and display the last known good temperature until the connection is restored to avoid panicking the operators. (隱藏錯誤訊息，並在畫面上顯示「最後一次收到的正常溫度」直到連線恢復，以免操作員恐慌)
B. Automatically reboot the central monitoring server to attempt a clean connection reset. (自動把中央監控伺服器重新開機，試圖乾淨地重置網路連線)
C. Enter a safe default state by initiating a controlled shutdown procedure for the reactor while sounding emergency alarms. (系統直接進入「安全預設狀態」，拉響緊急警報，並自顧自地啟動反應爐的控制降溫與停機程序)
D. Switch to an alternative, untested backup network protocol to blindly attempt reconnection. (切換去使用一個從未測試過的備用網路協定，盲目試著重連)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是對 **「失效安全預設 (Fail Safe Defaults)」** 最頂尖的詮釋。這條原則要求：當一個系統的防護機制、連線或硬體因為任何原因發生故障 (崩潰、斷電、斷線) 時，它的底層程式邏輯，【必須無條件地回退到一個「拒絕存取」或是「最高安全隔離狀態」的停機預設值】。以核反應爐這種涉及人命關天的系統來說，失去溫度感測就像是遮住了駕駛員的眼睛。這時最安全 (Safe) 的舉動絕對不是假裝沒事，而是立即啟動標準停機流程，中止高危險性行動。
    *   **為何 A, B, D 皆為干擾項：** A 是實務上最可怕的災難（顯示舊溫度會讓操作員以為很涼快，結果爐心已經熔毀爆掉了）。B 跟 D 都是賭運氣的盲目補救方法，它們可能會導致系統在不穩定的狀態下持續運轉造成更巨大的破壞，這不是保護系統的 Fail Secure 標準做法。

#### **3. During a code review of a monolithic web application, a security engineer notices that when a user logs in, the system checks their permissions and creates a session cookie. For all subsequent HTTP requests (e.g., viewing records, deleting users), the application only checks if the session cookie is valid, but it never re-checks the database to see if the user's role has been revoked since their initial login. Which core security design principle is this application definitively violating?**
**(在對一個大型網頁應用程式進行代碼審查時，資安工程師注意到：當用戶登入時系統確實有去查核權限，並發給他一張通行 Session 餅乾。但此後的所有 HTTP 點擊請求（例如看紀錄、刪除使用者等），這應用程式「只去檢查這餅乾有沒有過期」，卻『再也沒回頭去資料庫檢查這個人的職位權限是不是在他登入後早就已經被老闆拔除了』。這個系統確鑿地違反了哪一條核心的安全設計原則？)**
A. Complete Mediation (完全仲裁 / 完全中介)
B. Economy of Mechanism (經濟機制 / 簡化機制)
C. Least Common Mechanism (最少共用機制)
D. Separation of Duties (職責分離)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **「完全仲裁 (Complete Mediation)」** 原則規定：每一次、每一道對於任何物件或系統資源的存取，都『必須無例外地、強制地穿過安全查核點』去驗明正身並檢查最新的權限授權，不能有任何越過守衛的後門。開發者為了追求效能，常常會使用「快取 (Cache)」把當下的權限寫進 Session 裡發給客戶。這導致當駭客或離職員工的權限已經在資料庫被老闆撤銷 (Revoke) 後，只要他手上的 Cookie 還沒過期，他就能繼續無敵暢遊並搞破壞。這種「沒有對後續每一次點擊都再次檢驗權威」的作法，就是完全仲裁的大破口。
    *   **其餘為干擾項：** 機制經濟是講究簡單 (B)；最少共用是講資源獨立 (C) 不共用廁所；職責分離是防內賊 (D)。這些原則皆與「偷懶不反覆查驗最新的權限表」無直接關聯。

#### **4. A junior security architect proposes building a custom, multi-layered encryption protocol that combines AES, ChaCha20, and a proprietary scrambling algorithm to protect data at rest. The architect believes this complexity will make it unbreakable. A senior reviewer immediately rejects the proposal and mandates using standard AES-256 with an established key management system instead. Which security design principle is the senior reviewer explicitly enforcing?**
**(一位資淺架構師提議：為了保護靜態資料，他發明了一種混合了 AES、ChaCha20，外加原創私房加鹽演算法的「客製化、多層加密協定」！他堅信這種複雜度會讓駭客完全解不開。一位資深審查員看了一眼立刻怒退他的企劃，並強硬下令：「不用搞花樣，就是單純使用標準的 AES-256 加上成熟的金鑰庫管理就好」！請問這位資深主管是在徹底貫徹哪一項資安設計原則？)**
A. Defense in Depth (縱深防禦)
B. Open Design (開放式設計)
C. Economy of Mechanism (機制經濟論 / 保持設計簡單 KISS)
D. Least Privilege (最小權限)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「機制經濟論 (Economy of Mechanism)」** 這個原則在軟體工程界有一個更響亮的通俗稱呼：KISS (Keep It Simple, Stupid)。它強調資安防護的核心應該是越簡潔、越優雅、越好懂越安全。因為「複雜性是安全的死敵 (Complexity is the enemy of security)」。當你想出一個七拼八湊的九連環四重密碼演算法時，你以為你贏了，實際上你在程式碼裡種下了無數個人類腦袋除錯不出來的緩衝區溢位以及數學邏輯死角。真正的安全大師會選擇最無聊、但被全世界公認無解且架構最直覺的標準方案 (如單純 AES)。
    *   **為何 A, B 皆為干擾項：** A 縱深防禦是在網路上架設不同廠商的防火牆跟防毒軟體疊床架屋；並不是在單一密碼學函數裡面疊加多重垃圾程式碼。B 是程式該不該開源公開。D 則是權限設定範疇而與設計過於華麗無關。

#### **5. A company creates a DRM (Digital Rights Management) software to protect video files. To prevent piracy, the developers hardcode the master decryption key deep inside a heavily obfuscated C++ Dynamic Link Library (DLL), assuming hackers will never find it. Within two days of release, the key is extracted and published online. The developers' failure stems from relying on "Security by Obscurity," which directly violates which foundational security design principle?**
**(一家公司做了一套版權保護 DRM 軟體。為了防止盜版，工程師們把可以解開所有影片的『主解密金鑰』給硬寫死在一段極度混淆過的 C++ DLL 動態程式庫深處，他們天真地假設駭客這輩子絕對找不到。結果軟體才上市兩天，這把金鑰就被抽出並公布在網路上免費大放送。這種依賴「隱晦式安全 (Security by Obscurity)」而導致的徹底失敗，直接違反了哪一項建構安全的設計原則？)**
A. Psychological Acceptability (心理可接受度)
B. Separation of Privilege (特權分離)
C. Complete Mediation (完全仲裁)
D. Open Design (開放設計原則)

*   **正確答案 / Correct Answer：D**
*   **[解析邏輯]**
    *   **為何 D 是最佳選擇：** **「開放設計 (Open Design)」** 是幾百年前密碼學大師柯克霍夫 (Kerckhoffs's Principle) 留下的鐵律。這原則主張：你所設計的這套保險箱，它的安全度絕對不該建立在「駭客不懂我是什麼牌子、不知道我家齒輪怎麼裝的」這種鴕鳥心態上 (Security by Obscurity)。一個完美安全的系統，即便你把整份 DLL 或是原始碼全部攤在陽光下 (Open) 給全世界的駭客隨便看、隨便研究，只要那把真正的「鑰匙 (Key)」還在你口袋沒被偷走，你家就是牢不可破的。硬把金鑰寫死在程式碼裡試圖藏起來，就是犯了這條大忌。
    *   **為何其餘三個皆為干擾項：** 沒有人因為心情不好去解這個密碼 (A 不對)；跟權力有沒有切割開來(B)無關；也跟有沒有每一次檢查證件(C)不相干。本題純粹是對原始碼與秘密金鑰的錯誤認知。

#### **6. A small DevOps team sets up their CI/CD pipeline. Currently, any software developer can write code, commit it to the main branch, and trigger an automated deployment directly to the live production server without any other person reviewing or approving the changes. To prevent a rogue developer from intentionally deploying malicious code, what operational security principle MUST be implemented FIRST?**
**(一個小型 DevOps 團隊架設了他們的自動化部署管線。目前的狀況是：這間公司的任何一位程式設計師，只要高興，他就能自己寫完扣、自己推上主分支，然後系統就會『自動把他的心血部署上線到服務大眾的生產伺服器上』，這中間【完全不需要】第二個人的眼睛審核與簽字放行！為了防堵某個內鬼工程師哪天發瘋，故意推上去一隻勒索或後門病毒，這條產線【必須第一步】導入什麼基礎運營安全守則？)**
A. Defense in Depth (縱深防禦)
B. Least Common Mechanism (最少公用機制)
C. Separation of Duties (Dual Control) (職責分離 / 雙重控制)
D. Cryptographic Non-repudiation (密碼學不可否認性)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 當一個人可以球員兼裁判，在沒有任何監管的情況下，從開發打程式、打包、到發布上線通通「一條龍」獨攬大權時，這就是最危險的內部威脅 (Insider Threat) 溫床。資安營運要防範內賊做怪，最核心的原則就是 **職責分離 (Separation of Duties, SoD)**。它強制規定：完成一個高度敏感的危險任務，必須有多個不相干的人彼此制衡。你負責寫 Code，但你按推播上營運主機的那顆按鈕會失效；必須由旁邊的資安官或另一位主管核發許可證按下第二把鑰匙 (這又叫雙重控制 Dual Control)，飛彈或是有毒程式才打得出去。
    *   **為何 A 是干擾項：** 縱深防禦是疊很多牆防禦外部駭客，但它擋不了從內部合法大門開車進來的全能內鬼。

#### **7. A hospital implements a hyper-aggressive AI-driven endpoint protection system. The system is configured to instantly isolate any medical device or server from the network if it detects even a minor anomaly. During a critical surgery, the AI flags a false positive and completely locks down the electronic health records (EHR) database. The surgical team cannot access patient blood types, putting lives at immediate risk. This scenario highlights a severe conflict between which two core security concepts?**
**(醫院導入了一套極端凶狠暴躁的人工智慧終端防禦系統。設定是：只要這系統的神經感受到任何甚至是一丁點的風吹草動異常，它就會『瞬間把那台伺服器或醫療機器的網路線在軟體層面給砍斷隔離』。在一場性命交關的外科手術中，這 AI 發生了誤判，直接把整棟大樓的「電子病歷資料庫 (EHR)」給上鎖封殺斷網。開刀房的醫生瞬間無法查閱病人是不是對麻醉藥過敏或是什麼血型，人命危在旦夕！！這個悲劇極度尖銳地突顯了資安領域中，哪兩大核心概念的殊死衝突？)**
A. Authentication vs. Authorization (認證 與 授權 的衝突)
B. System Confidentiality vs. System Availability (系統機密性 與 系統可用性 的衝突)
C. Data Integrity vs. Data Non-repudiation (資料完整性 與 不可否認性 的衝突)
D. Defense in Depth vs. Complete Mediation (縱深防禦 與 完全仲裁 的衝突)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是資安鐵三角 CIA Triad 常見的零和賽局。這個激進的防護 AI 滿腦子只想要保護病歷資源不要被駭客外流 **(保密性 Confidentiality)** 跟不要被勒索軟體加密 **(完整性 Integrity)**。結果它為了捍衛這兩者，採取了焦土戰術把機房給關了。卻因此徹底毀滅了醫療系統最不可碰觸的底線：**可用性 (Availability)**。當醫生需要開刀時，病歷的「無障礙快速取用與永遠維持活著的服務」遠比這病歷被多看一眼來得重要萬分。許多安全設計都在權衡這 C.I.A 的翹翹板要偏向哪方。
    *   **其他三個干擾項：** 那些都是偏向政策與查核細節的衝突，與這題所描述巨觀的保護資料不被看光，引發了讓系統直接死了沒法連線之間的兩難拉扯無關。

#### **8. The IT department issues a new password policy requiring all employees to create 24-character passwords containing uppercase, lowercase, numbers, and three special symbols. Furthermore, the password must be reset every 14 days and cannot match the last 20 passwords. Within a week, the security team finds employees writing their passwords on sticky notes attached to their monitors. Which security design principle did the IT department completely ignore?**
**(IT 部門頒布了一條地獄級密碼規定：要求全體員工必須設定長達 24 個字元的密碼！而且裡面一定要有大寫、小寫、數字，以及強制包含至少三個特殊符號。這還沒完，每 14 天必須換一次密碼，而且不能跟過去的 20 組密碼重複。結果新規定上路不到一週，資安團隊巡邏時差點暈倒：全公司九成的員工都把這密碼抄在黃色便利貼上，然後大搖大擺地貼在電腦螢幕正中央！請問這剛愎自用的 IT 部門，制定政策時徹底完全漠視了哪一項安防聖旨設計原則？)**
A. Economy of Mechanism (機制經濟論)
B. Psychological Acceptability (心理可接受度)
C. Least Privilege (最小權限)
D. Fail Safe Defaults (失效安全預設)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「心理可接受度 (Psychological Acceptability)」** 的意思是：如果你把一個安全系統設計得太過反人類、太過繁瑣複雜，導致你的員工覺得「用這爛安全系統上班，比我摸魚還要痛苦一萬倍」。那麼這群全天下最聰明懶惰的生物 (人類)，就會發明出繞過這個安全防線的方法 (例如便利貼或是直接打給 IT 裝傻重整密碼)。最終，極端高壓的安全政策不僅沒有提升安全，反而引發了一整間辦公室密碼大洩漏的資安災難。好的安全設計應該是隱藏於無形的 (Transparent) 或是方便的 (如按壓指紋)。
    *   **為何 A 不是最佳解：** 機制經濟探討的是背後演練防護的『程式或機組複雜度』，而不是針對『活人血肉之軀人類腦袋心靈』抗拒的承受力。

#### **9. A B2B application processes high-value wholesale orders via a REST API. The development team wants to ensure that an attacker sitting on the network cannot intercept a valid `$50,000` order packet and subtly change the payload to read `$50` before it reaches the server. Which of the following cryptographic solutions provides the strongest mathematical guarantee of Data Integrity for the message payload?**
**(一個企業 B2B 系統透過 REST API 在處理高價值的批發訂單。開發團隊極度害怕一件事：萬一有駭客潛伏在網路封包傳輸的半路上，把一筆合法剛送出的『五萬美金』匯款訂單神不知鬼不覺地篡改成了『五十塊』再放行游去伺服器。下列哪一個密碼學的實作方案，可以為了這個封包的「資料完整性 (Data Integrity)」提供最強悍、最無堅不摧的數學保證？)**
A. Establishing a VPN tunnel between the client and server. (在客戶端跟伺服器間拉一條 VPN 通道)
B. Encrypting the payload using the RSA Public Key algorithm. (用 RSA 公鑰演算法把這則封包加密起來)
C. Generating and appending a Keyed-Hash Message Authentication Code (HMAC) to the payload. (為這段封包資料運算出一個『金鑰雜湊訊息鑑別碼 (HMAC)』，並把它附掛在封包後面一起傳輸)
D. Encoding the payload using Base64 before transmission. (在傳送前，大費周章把它用 Base64 給編製轉換過)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 千萬別把這題跟「保密性」搞混了。企業這題**不**害怕被駭客看到「那是我買了 5 萬元」(Confidentiality)。他們怕的是數字被魔改成 50 塊錢 **(破壞了資料的完整性 Integrity)**。在密碼學中擔綱「防篡改」保證的超級戰士是一般雜湊函數 (如 SHA)，但這不夠，因為駭客砍掉原本的雜湊後，可以自己用 50 元算一份全新的假雜湊送過去。因此，無堅不摧的進階武器是 **HMAC (金鑰雜湊)**。它在算這份 50000 數字的指紋時，偷偷加入了只有雙方才知道的一根「祕密金鑰匙」一起絞碎混在指紋裡。駭客因為手上沒有這根真金鑰，他想改 50 元就永遠算不出能騙過伺服器的合法指紋，這就保證了極致的資料完整性與來源鑑別度。
    *   **為何 A, B 是干擾項：** VPN 跟 RSA 的強項是把內容打上馬賽克加密「怕給別人看 (Confidentiality 機密性)」。就算被馬賽克，某些強悍的主動竄改攻擊也是能弄壞封裝，它們並不是「專職負責針對單一封包檢驗指紋篡改」的最高保證。
    *   **為何 D 是干擾項：** Base64 是騙小孩把蘋果字母換成香蕉的二進位表頭轉換法，它完全是明文裸奔，任何駭客都能按一鍵還原並瞬間更改字元。

#### **10. Your risk management team is evaluating a newly discovered buffer overflow vulnerability in a legacy internal application. The application processes massive amounts of highly classified data (High Impact). However, the application is hosted on an air-gapped, physically isolated standalone machine with no network connection, no USB ports, and strict physical armed guards. In the context of the standard Risk Equation ($Risk = Threat \times Vulnerability \times Impact$), how should the overall risk level BEST be classified?**
**(你們的風險團隊正在評估一個超古老內部應用程式裡的「緩衝區溢位漏洞」。這隻老程式掌管了海量且會動搖國本的國家級機密 (被評為：會造成毀滅性衝擊 High Impact)。但是！這台跑著破爛漏洞軟體的伺服器，是被『物理隔離斷網 (Air-gapped)』的！它被關在地底堡壘一台孤獨無伴的主機裡，不接網路線、被熱熔膠塞滿 USB 孔，門口還有帶槍警衛全天候死守。如果套用資安風險管理恆等式：『風險 (Risk) = 威脅 (Threat) × 漏洞 (Vulnerability) × 衝擊 (Impact)』，這整件事的最終【總體風險評等】最合適的歸類為何？)**
A. High Risk, because the data is highly classified and the vulnerability is known. (高度風險！因為資料太機密且這洞太明白)
B. Critical Risk, because buffer overflows always carry an immediate critical rating. (核爆級風險！只要叫緩衝區溢位就一律是死罪)
C. Low to Minimal Risk, because despite the high impact and existing vulnerability, the likelihood of a threat agent physically accessing the isolated system is practically zero. (極低甚至是微乎其微的風險！因為儘管衝擊巨大且漏洞千真萬確存在，但是根本沒有任何威脅者 (Threat) 能插上線打的到它，觸發這個漏洞的「機率極近乎為零」)
D. Unknown Risk, until a penetration test is aggressively performed. (未知風險！直到派紅隊去用槍打穿警衛硬上測驗為止)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是風險管理 (Risk Management) 裡定心丸般的核心考點。風險，它必須是「三個輪子同時轉動才會爆胎前進」。也就是：一個擁有強烈動機與武器的「威脅者 Threat (如駭客)」，剛好找到了大門上忘記鎖的那道「漏洞弱點 Vulnerability (如那個破除緩衝區)」，最後造成了金庫起火的「龐大衝擊 Impact」。如果我們把威脅者的這個途徑 (機率，或者稱 Likelihood)，藉由把金庫深埋海底十層樓，這叫根絕了「攻擊向量 / 威脅發生率 (Threat)」。在相乘的公式上，只要有一邊歸零 (`零威脅 x 滿分10分超級大洞 x 滿分10分宇宙大炸彈 = 0 分的風險`)，那它就是一個非常低度、無須理會優先處理它的底層風險。
    *   **為何 A, B 是干擾項：** 如果你只看到高機密檔跟有重大破洞，你就被漏洞評估儀器給綁架了。沒有外星人可以摸到這機台去插進去打洞，風險即不存在。

#### **11. A user successfully logs into an e-commerce platform by supplying their username, a complex password, and a One-Time Password (OTP) sent to their phone. Once logged in, the user manually types `https://store.com/admin/delete_user` into the URL bar. The server executes the script and deletes the requested user, even though the logged-in user is only a standard customer. What specific security concept failed in this system?**
**(一個鄉民成功登入了購物網站，他過關斬將輸入了帳號、極度複雜的密碼，甚至連手機的 OTP 一次性簡訊密碼都精準填對過關！結果一登入後，這位平凡無奇的小鄉民手賤，在上方網址列手動打入 `https://store.com/後台版圖/砍掉全站用戶` 後按下確認鍵。這家沒腦子的伺服器居然就乖乖跑那隻腳本把別人砍了，儘管這個打字的人只是個普通散客！在這個悲劇系統中，究竟是哪個特定的資安閥門壞掉了？)**
A. Authentication (確認「你是誰」的身分驗證機制)
B. Accountability (究責記錄條款)
C. Data Confidentiality (資料加密保密性)
D. Authorization (查驗「你到底有沒有權力做這件事」的授權管轄機制)

*   **正確答案 / Correct Answer：D**
*   **[解析邏輯]**
    *   **為何 D 是最佳選擇：** 這是 **「認證 (Authentication, 簡稱 AuthN)」** 跟 **「授權 (Authorization, 簡稱 AuthZ)」** 之間天差地遠的分野。認證負責核對你的大頭貼與指紋，保證『你就是帳單上寫的王國榮本人』。但是授權把關的是，『這家銀行雖然確實承認你是王國榮了，但是你有權去打開別人的大金庫拿走裡面的金條嗎？』。在這題系統裡，它完美無比地核發了門票證明這乘客是買了票的本人（MFA 登入認證滿分），但它卻瞎了眼，在這名客艙貧民乘客想要隨意開啟超長官專屬的商務艙 `admin/delete` 區域時，防禦網完全失職忘記檢驗他是不是商務艙的總裁。這叫做「授權 (Authorization/ Access Control) 失敗破洞」。

#### **12. An application requires access to a backend database simply to perform daily `SELECT` queries to generate read-only sales reports. The system administrator configures the application's connection string to use the database's `db_owner` (Database Owner) account, reasoning that it makes deployment easier and avoids permission errors. Which fundamental security principle is being egregiously violated?**
**(有一支應用程式它的存在目的極其卑微：它每天只需要連進資料庫，做做溫和無害的 `SELECT` 撈取資料，印幾張昨天賣多少錢的「唯讀」銷售報表而已。但這偷懶的網管大叔在設定這程式的資料庫連線字碼字串時，居然直接灌給它這座資料庫裡如玉皇大帝般存在、能生殺砍檔予奪的『庫擁有人 (db_owner)』超級帳號密碼來連線！大叔的理由是：「這樣部署最快啦，才不會整天跳什麼權限被拒絕的煩人錯誤碼」。這位散漫大叔赤裸裸強暴了哪一條系統安防核心理念？)**
A. Least Privilege (最小權限原則)
B. Separation of Duties (職責互相制約分離)
C. Open Design (開放式原理)
D. Complete Mediation (完整強制仲裁管制)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 這是資安領域跟設計架構最無腦但也最常犯錯的 **「最小權限原則 (Principle of Least Privilege, PoLP)」**。只要你是做這個小木工活的腳色對象（不管你是活生生的人還是軟體機器人），系統只應當配發剛好夠你做到這件事的最低限度權限，連多一滴水都不能給！在這情境中，系統應該為這支印表機程式創立一個叫 `Report_Maker` 的貧困小帳號，然後這帳號被死綁只能在特定桌子上做無害且沒有破壞性的 `SELECT(讀取唯讀)`。大叔給了這支軟體一顆能毀天滅地的核按鈕，一旦這支軟體某天被俄國駭客綁架了，這隻原來只能看戲的程式，就會化身高權限的上帝當機把你整個庫給端走。
    *   **為何 B 不是最佳解：** 職責分離通常是指這件事必須有「兩個人或兩把鑰匙」牽制完成。本題強調的是「不該給不符合身分的權力跨越位階」，而不是需要第二個人審查。

#### **13. During a forensic investigation following a massive data breach, investigators look at the system logs. They see that an account named `Web_Admin` executed the malicious data export command. However, the company has six different system administrators who all know and regularly use the `Web_Admin` password to perform daily tasks. Because the company cannot pinpoint exactly which human being performed the action, the system has failed to provide which essential security attribute?**
**(一場血腥的大規模資料庫盜竊案發生了，數位鑑識小組趕到現場狂翻系統日誌。他們查到了，是由一個名為 `Web_Admin (網頁管理員總號)` 的帳棚在半夜三點下了打包帶走命令！但荒謬的是，這家公司機房裡的死老規矩是：裡頭坐著六個輪班的系統工程師，全部天天都敲這個同一組萬用密碼 `Web_Admin` 在維修網站！鑑識官崩潰了，因為這六個人互推，沒人能查出或證明當時那隻犯罪手到底是長在誰身上。請問這套系統因此喪失、徹底無法提供資安四本柱中的哪一個必要屬性？)**
A. Non-repudiation (數學密碼保證的不可否認度)
B. Authorization (過紅線的授權)
C. Individual Accountability (可追溯怪罪的個體當責性)
D. Need-to-Know (情報圈絕對須知底限)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這個老鼠屎狀況違反了 **「個別當責性 / 個體究責性 (Individual Accountability)」**。要有 Accountability，我們必須能在法院上把日誌裡的一條龍足跡 (Audit log) ，死死綁定在「地球上那單一一位有血有肉特定的人類」身上。一旦企業在管理層允許甚至是推廣他們使用「免洗、公派」的共享群體帳戶 (Shared/Group Accounts) 時，那個日誌除了告訴法官是誰按的，法官只能看到那六個人對他說：「那時候我去上廁所了，我不知道」。這種大鍋飯的帳號管理行為讓系統完全沒辦法揪出真正的內鬼是誰。
    *   **為何 A 不要選：** A 選項「不可否認性」是更高的數學證物防線，通常是用指紋或是他的密碼學私鑰簽名綁死的。但在此連帳號都是 6 個人集體擁有，它的破防是在最根基的「管理體制沒有把個體與動作鎖定關聯」，這種帳號政策的毀壞統稱為喪失 Accountability。

#### **14. A corporate network relies exclusively on a single next-generation perimeter firewall to protect its internal web servers. A security consultant warns that if a hacker exploits a zero-day vulnerability to bypass the firewall, the entire internal network will fall immediately. The consultant recommends deploying a Web Application Firewall (WAF), Host-based Intrusion Prevention Systems (HIPS) on the servers, and strict application-level input validation. What overarching security strategy is the consultant advocating?**
**(某大廠的企業網路防禦學講究「雞蛋放在神級的籃子裡」，他們孤注一擲全靠公司大門口裝的那一台號稱次世代無敵貴的邊界防火牆，來保護大門內數以百計的網站主機。一位資安顧問來看風水後大驚失色，警告他們：只要哪天駭客挖到一個零日漏洞把這堵神牆鑿開一個小洞，門裡面手無寸鐵的這些村民叢集就會一夕被屠城滅門。顧問強烈要求不僅大門要守，他要每台主機上加裝城鎮守衛 WAF、並且給主機自己穿上鎖子甲 HIPS 系統。請問這位顧問正在瘋狂傳道要求他們建構的終極宏觀安防戰略為何？)**
A. Fail Safe Defaults (失效保護鎖死門預設)
B. Defense in Depth (Layered Defense) (縱深防禦 / 多維度洋蔥式千層派防禦網)
C. Economy of Mechanism (最簡極致打架機制)
D. Least Common Mechanism (最罕見的公用共用系統)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這個在企業架構被奉為圭臬的大戰略是 **縱深防禦 (Defense in Depth / Layered Defense)**。你必須假定「絕對不可能有一道完美的系統能擋下所有的壞人，不管是再神的外牆都會被打穿一天」。因此，最卓越的安全不只是防禦邊緣，而是建立重重疊加、「多樣異質化」的關卡包圍網。就像洋蔥一樣，駭客買通了外牆的兵 (Firewall)，他爬進去時會立刻被暗巷的警網撲殺 (HIPS)；他又把狗屋打開，結果被裡面的保險箱封印封死 (WAF)。藉著串聯多重不同廠牌與技術的關卡，能極大幅度地遲滯攻擊行動並爭取救兵時間。
    *   **其他三個皆為干擾項：** 它們是一般程式運作失敗或分享元件的小戰術設定，不足以成為整個多層次兵力排兵布陣的龐大安防戰略名詞。

#### **15. A cloud provider offers multi-tenant hosting. To save RAM, the engineers design a single, shared cryptographic key generation module in the kernel. Both "Tenant A" and "Tenant B" must call this exact same physical module in memory whenever they need a new encryption key. A security researcher discovers that by exhausting the entropy pool as Tenant A, they can predict the cryptographic keys generated for Tenant B. Which design principle was violated by forcing different security domains to share the same pathway?**
**(雲端巨頭平台在做多租戶大通鋪生意 (Multi-tenant)。為了摳門省記憶體，研發工程師在伺服器深處的心臟寫了「唯一一個大家共用的、會產出魔法隨機亂碼金鑰的模組」。這意味著住左邊的「房客 A」跟住右邊的敵對公司「房客 B」，要拿加密鑰匙時，都必須排隊大鍋飯去找這個唯一的神燈要。結果某個天才駭客租了 A 房，他在裡面瘋狂戳這個神燈把它的「運算亂數池」靈力耗盡看透了這碗水的波動！接著這駭客居然能開始鐵口直斷預測，等一下對面那間房客 B 按神燈時會掉出什麼密碼！！這是因為在最初設計大樓時，工程師為了省錢把『不同安全楚河漢界的領地，硬生生逼著共用同一條管線上廁所』而觸犯的設計禁忌。此禁忌為此四者熟誰？)**
A. Open Design (極度公開開明的開放設計)
B. Least Common Mechanism (最少公用地雷網機制 / 拒絕對資源的濫泛共享)
C. Complete Mediation (鐵壁完整仲裁)
D. Separation of Duties (大權切割分離)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這題是在考安全架構裡常被遺忘，但極端冷酷的神原則 **「最少共通/公用機制 (Least Common Mechanism)」**。白話文就是：少讓兩個不同安全信任度的人共用一條船。所有被共享的機制或變數模組通道 (如記憶體亂數產生器、或是同一支用來收信的郵局大廳)，都會變成單點脆弱。這不僅容易因為某個人的海量塞爆而讓另一個人當機沒有救兵。這更恐怖的是這會建立一條暗中流通的 **「隱蔽通道 (Covert Channel)」**，像這題裡，房客 A 就能用這個大家都得摸到的資源去刺探或是操控另一間毫無關聯公司的深層隱私與機密。所以，獨立切割各玩各的，安全就最高！

#### **16. A simple mobile application designed to function as a basic calculator prompts the user to grant permissions to access their GPS location, contact list, and read SMS messages before it will launch. What core privacy and data protection principle is this application blatantly violating?**
**(一隻被設計並標榜為『超純粹！連買菜阿嬤都會用的簡單除法計算機』的低能手機 App，在你第一次安裝打開時，居然強制霸屏，並威脅你如果不同意讓它『抓取你的手機 GPS 當下經緯度、撈出所有通訊錄的親友電話、以及有權力閱讀你簡訊匣裡所有內容』，它就死當給你看。這等無法無天的吸血怪獸 App，是赤裸裸、極度無恥地踐踏了哪一條個資隱私安全保護的神聖心法？)**
A. Data Minimization / Purpose Limitation (資料超級極簡化 / 蒐集目的絕對限縮限制)
B. Non-repudiation (不讓你否認曾做過的保證)
C. Data Anonymization (打上馬賽克的資料去識別化)
D. Cryptographic Integrity (無堅不摧的密碼學完整封條)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 這個現象在 GDPR 這等最強橫的法規中被嚴厲痛打。隱私界最高原則就是 **「資料最小化 (Data Minimization)」** 以及連帶的 **「特定目的限制 (Purpose Limitation)」**。如果你的手機只是一台毫無理由要在這世界上存活的計算機，你需要的輸入素材就只有 1 到 9 號碼跟加減乘除。你【絕對不被合法具備任何正當理由 (Legitimate Interest)】去貪婪蒐集或是掃描客戶的底層網路封包或身家大典個資去建立你的廣告輪廓。只要收集的行為超出了軟體原始賦予的「單純正當意圖目的」，那就是公然違法違紀之行為。
