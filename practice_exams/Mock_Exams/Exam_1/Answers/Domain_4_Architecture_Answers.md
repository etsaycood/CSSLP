# 第一套全真模擬試題 (Exam 1) - 答案與詳解本
## 領域 4：安全的軟體架構與設計 (Secure Software Architecture and Design) (18題)

---

#### **1. A financial technology (FinTech) startup is building a brand new microservices architecture for their mobile banking app. The Chief Architect mandates a strict zero-trust approach between all internal backend services. One critical developer explicitly asks: "If the 'Payment Gateway Service' needs to talk to the 'User Ledger Service,' how exactly should they mathematically prove their identities to each other without passing passwords back and forth in plaintext over the internal network?" Which of the following architectural implementations is the MOST robust and standard solution to fulfill this zero-trust inter-service authentication requirement?**
**(一家金融科技新創正在為其行動網銀打造微服務架構。首席架構師強制要求所有內部後端服務間都必須採用「零信任」原則。一位核心開發者問：「如果『支付閘道服務』需要和『用戶帳本服務』溝通，在不於內部網路傳遞明碼密碼的情況下，它們該如何用數學來向彼此證明身分？」下列哪一項架構實作是滿足這種零信任跨服務認證最標準且最強健的解決方案？)**
A. Establishing a hardware-based IPsec VPN tunnel between the two Docker containers. (在兩個 Docker 容器間建立基於硬體的 IPsec VPN 通道)
B. Implementing Mutual Transport Layer Security (mTLS) utilizing ephemeral cryptographic certificates issued by an internal Certificate Authority (CA). (實作雙向傳輸層安全協議 mTLS，利用內部憑證授權中心發行的短期密碼學憑證)
C. Hardcoding a 256-bit symmetric AES key inside the configuration files of both services to act as a shared secret. (在兩個服務的設定檔中硬編碼寫死一把 256 位元的對稱式 AES 金鑰作為共享機密)
D. Utilizing the OAuth 2.0 "Authorization Code Flow with PKCE" specifically designed for machine-to-machine backend communication. (使用專為機器對機器通訊設計的 OAuth 2.0 授權碼流程搭配 PKCE)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 在現代的微服務 (Microservices) 與服務網格 (Service Mesh) 架構中，要實現零信任 (Zero-Trust)，最有效且業界標準的作法就是 **mTLS (Mutual TLS，雙向 TLS)**。傳統的 HTTPS 只有客戶端會去驗證伺服器的憑證（確認是不是連到假網站）。而在 mTLS 中，發起連線的 A 服務（付款閘道）跟接收連線的 B 服務（帳本），雙方都會互掏出由內部 CA 簽發的 X.509 憑證。這不僅解決了「這段網路封包是否被加密 (機密性)」，更同時解決了「對面那台機器真的是我兄弟嗎 (身分認證)」。
    *   **為何 A 是干擾項：** IPsec 通常是用在跨站點 (Site-to-Site) 的兩台實體路由器之間打通網段。在成千上萬個動態生滅的 Docker 容器之間拉 IPsec VPN 是架構上的災難，缺乏彈性且管理成本極高。
    *   **為何 C 是干擾項：** 把金鑰「硬編碼寫死 (Hardcoding)」在設定檔裡是最大的資安禁忌。金鑰無法被自動輪替，且只要程式碼外洩，系統就直接崩盤。
    *   **為何 D 是干擾項：** OAuth 2.0 確實有「機器對機器 (M2M)」的流程，但它叫做「Client Credentials Grant (客戶端憑證授權)」，而不是給人類登入瀏覽器用的「Authorization Code Flow with PKCE」。選項 D 故意把人類用的流程套在機器上，張冠李戴。

#### **2. You are leading a Threat Modeling workshop for a new IoT smart home platform using the STRIDE methodology. A senior engineer points at a specific data flow arrow on the Data Flow Diagram (DFD) representing the connection between the user's mobile app and the cloud backend. She states: "If an attacker on the same local Wi-Fi intercepts this traffic, they could secretly read the user's home security camera logs." According to the STRIDE model, which specific threat category is the engineer identifying, and what is the standard architectural mitigation?**
**(你正在帶領團隊使用 STRIDE 方法論進行 IoT 智慧家庭平台的威脅建模。一位資深工程師指著資料流程圖 (DFD) 上代表「手機 APP 連至雲端後台」的資料流箭頭說：「如果駭客跟用戶在同一個區域 Wi-Fi 上攔截了這些流量，他們就能偷看用戶的家用監視器日誌。」根據 STRIDE 模型，工程師指出的是哪一種特定的威脅類別？又該用哪種標準架構策略來緩解？)**
A. Threat: Tampering. Mitigation: Implement Digital Signatures. (威脅：竄改。緩解：實作數位簽章)
B. Threat: Elevation of Privilege. Mitigation: Enforce strict Role-Based Access Control (RBAC). (威脅：特權提升。緩解：強制實施嚴格的角色存取控制)
C. Threat: Information Disclosure. Mitigation: Encrypt the data in transit using TLS 1.3. (威脅：資訊洩露。緩解：使用 TLS 1.3 對傳輸中的資料進行加密)
D. Threat: Repudiation. Mitigation: Implement comprehensive, immutable logging. (威脅：抵賴。緩解：實作全面且不可變的日誌記錄)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是 STRIDE 模型最基礎的考題。在 STRIDE (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege) 的框架中，只要提到「旁人能偷聽 / 偷看 (Eavesdropping / Sniffing)」網路傳輸中的機密資料，這就是標準的 **Information Disclosure (資訊洩露 / I)**。而要保護「資料在網路線上狂奔時不被偷看」的最佳架構緩解措施，就是為連線套上一層堅固的加密隧道，例如 **Transport Layer Security (TLS)**。
    *   **為何 A 是干擾項：** 竄改 (Tampering/T) 是指駭客不只偷看，還把你原本要匯款 100 元的封包變成了 1000 元。數位簽章主要是為了防禦竄改（保證資料完整性），而不是防禦偷看。
    *   **為何 B 是干擾項：** 特權提升 (EoP) 是指一個普通使用者想辦法拿到了 Admin 帳號的權限，這是系統內部權限控管 (RBAC) 破洞的問題，不是傳輸線上路徑被竊聽的問題。
    *   **為何 D 是干擾項：** 抵賴 (Repudiation/R) 是指做過壞事的人死不承認。需要靠日誌與數位簽章防禦，與被動的竊聽無關。

#### **3. The enterprise security architecture board is reviewing a monolithic legacy application that consists of 2 million lines of code running on a single massive application server. A critical vulnerability in the "Avatar Upload Component" allows an attacker to execute arbitrary OS commands. Because the application runs as a single process with administrative privileges, the attacker immediately gains total control over the entire database and the underlying operating system. To fundamentally prevent this total system compromise in the future, which core architectural security principle MUST be applied to restructure this monolithic beast?**
**(企業資安架構委員會正在審查一個龐大的單體式架構遺留系統（兩百萬行程式碼全跑在一台伺服器上）。系統中的「大頭貼上傳元件」有一個致命漏洞，允許駭客執行任意 OS 指令。因為整個應用程式都以「管理員最高權限」在單一行程中運行，駭客立刻取得了整個資料庫與底層作業系統的全面控制權。為了在未來根本性地防止這種「系統全毀」的慘劇，必須套用哪項核心架構安全原則來重構這隻單體式怪獸？)**
A. The Principle of Open Design (開放設計原則)
B. The Principle of Separation of Privilege (Compartmentalization) (特權分離/隔離區隔原則)
C. The Principle of Psychological Acceptability (心理可接受度原則)
D. The Principle of Failsafe Defaults (故障安全預設原則)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 把兩百萬行程式碼全部綁在一起，並且賦予它們最高權限，這就像是把潛水艇設計成只有一個超大船艙，只要外殼破一個洞，整艘潛水艇就會瞬間沉沒。要拯救這種架構，必須套用 **特權分離 (Separation of Privilege)** 或稱為 **Compartmentalization (隔艙化 / 沙河化)** 原則。這個架構理念要求將那個只負責「上傳圖片」的危險小元件給獨立切分出來，把它關在一個權限極低、無法讀取資料庫、只能寫入特定資料夾的沙盒或微服務容器裡。這樣一來，就算駭客打穿了上傳元件，他也只能被困在那個無用的沙盒裡，無法輕易擴大戰果（限制 Blast Radius 爆炸半徑）。
    *   **為何 A 是干擾項：** 開放設計指的是你的安全必須建立在演算法數學的強韌上，而不是靠把程式碼藏起來（不要依賴隱晦式安全）。這與權限切割無關。
    *   **為何 C 是干擾項：** 心理可接受度是指設計出來的安全機制（例如密碼規則）必須好用，不能讓使用者感到太痛苦而想辦法繞過。
    *   **為何 D 是干擾項：** 故障安全 (Failsafe Defaults / 預設拒絕) 指的是當系統發生例外或無法確定權限時，它的預設行為應該是「拒絕放行」，這屬於存取控制的底層邏輯，而不是切割系統船艙的架構原則。

#### **4. A cloud architect is designing the identity management strategy for a massive B2B SaaS platform that serves hundreds of different corporate clients. The sales team's primary requirement is: "Our corporate clients refuse to create new passwords for our SaaS. They demand that their employees use their existing corporate Windows Active Directory logins to access our cloud platform seamlessly." To satisfy this architectural demand for Identity Federation, which of the following standard protocols should the architect implement?**
**(雲端架構師正在為一個服務數百家企業客戶的 B2B SaaS 平台設計身分管理策略。業務部的主要需求是：「我們的企業客戶拒絕為我們的 SaaS 系統建立新帳號。他們要求員工能直接用公司現有的 Windows AD 帳號『無縫登入』我們的雲端平台。」為滿足這項對「身分聯合 (Identity Federation)」的架構需求，架構師應實作下列哪一種標準協定？)**
A. Simple Directory Access Protocol (LDAP) combined with NTLMv2 (結合 NTLMv2 的 LDAP 協定)
B. Security Assertion Markup Language (SAML) 2.0 or OpenID Connect (OIDC) (安全斷言標記語言 SAML 2.0 或是 OpenID Connect)
C. Extensible Authentication Protocol (EAP) over TLS (基於 TLS 的 EAP)
D. Fast Identity Online (FIDO2) WebAuthn (FIDO2 WebAuthn)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 當你需要跨越網際網路，讓 A 公司的員工用他們自己家的認證系統，毫無阻礙地登入到 B 公司的雲端系統時，這種架構稱為 **身分聯合 (Identity Federation)** 或是跨網域的單一簽入 (Cross-Domain SSO)。在整個資訊軟體界，能做到這件事的兩大霸主協定只有兩個：企業級比較老派的 **SAML 2.0 (透過 XML 傳遞票據)**，或是現代 Web App 比較愛用的 **OpenID Connect (OIDC, 基於 OAuth 2.0 架構)**。
    *   **為何 A 是干擾項：** LDAP 雖然是讀取帳號目錄的標準，但它通常只能在「公司企業內網 (Intranet)」防火牆內部使用。你幾乎不可能要求客戶把他們內網的 AD 伺服器打開 LDAP port 給互聯網上的 SaaS 系統直接下撈取指令。
    *   **為何 C 是干擾項：** EAP-TLS 主要用於無線網路 (Wi-Fi 802.1X) 或 VPN 的底層連線認證，不是用來設計 Web 應用程式的跨域單一簽入機制的。
    *   **為何 D 是干擾項：** FIDO2 (如利用指紋或 YubiKey 登入) 是一種「無密碼強認證裝置」的標準，這是在解決「人類怎麼跟電腦證明我是我」，而不是在解決「兩個不同網域的伺服器之間怎麼傳遞信任票據 (SSO Token)」。

#### **5. During the initial design phase of a highly classified military communications application, the lead cryptographer mandates: "If an adversary compromises our server today and steals the RSA private key we are currently using for TLS connections, they MUST NOT be able to use that stolen key to decrypt the mountains of intercepted, encrypted network traffic they recorded from us over the past five years." What advanced cryptographic design feature is the cryptographer demanding to ensure the historical confidentiality of the data?**
**(在高度機密的軍事通訊應用初期設計階段，首席密碼學家下令：「如果敵人今天攻破我們的伺服器並偷走我們正在為 TLS 連線使用的 RSA 私鑰，他們『絕對不能』用這把偷來的鑰匙，去解密他們過去五年來在網路上錄下的那些加密通訊封包。」為了確保歷史資料的機密性，密碼學家要求的是哪一種進階的密碼學設計特性？)**
A. Perfect Forward Secrecy (PFS) utilizing Ephemeral Diffie-Hellman (DHE or ECDHE) key exchange algorithms. (完美前向保密 PFS，利用短暫式的 Diffie-Hellman 金鑰交換演算法)
B. Utilizing AES-256 in Galois/Counter Mode (GCM) for extremely fast symmetric encryption. (利用 GCM 模式的 AES-256 進行極速對稱式加密)
C. Implementing Quantum Key Distribution (QKD) across the entire fiber-optic network. (在整個光纖網路上實作量子金鑰分發 QKD)
D. Forcing strict Certificate Pinning within the mobile client application. (在行動裝置客戶端中強制實行嚴格的憑證固定/綁定)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 這個極度嚴苛的軍事要求稱為 **完美前向保密 (Perfect Forward Secrecy, PFS)**。在早期的 HTTPS 中，所有的對話加密金鑰都是用伺服器上那把「長生不老」的 RSA 私鑰給包裝傳遞的。只要今天 RSA 私鑰被偷，駭客就能像解開寶箱一樣，把過去幾年錄下的流量全部倒帶解密。要打破這個惡夢，架構上必須強迫通訊雙方使用 **臨時的/短暫的 (Ephemeral)** Diffie-Hellman (DHE 或 ECDHE) 演算法。在這種模式下，每當雙方建立一次新的連線，就會在記憶體裡面當場搓出一把全新的拋棄式金鑰，通訊完畢立刻砍掉銷毀。這樣一來，就算伺服器母鑰匙日後被盜，歷史流量也永遠無法被回溯解密，因為解密金鑰早就灰飛煙滅了。
    *   **為何 B 是干擾項：** AES-GCM 是一種非常強大且自帶完整性驗證 (AEAD) 的對稱加密演算法。但即使你用了地表最強的 AES，如果用來傳遞 AES 鑰匙的那把母鑰匙 (RSA) 被偷且缺乏 PFS 保護，那 AES 封包一樣會被事後破解。
    *   **為何 C 是干擾項：** QKD 是利用量子力學在實體光纖上傳送密鑰，它是未來的物理防護技術。但題目描述的 PFS 是今日在軟體與網路協定層（如 TLS 1.3）就必須設定的架構功能。
    *   **為何 D 是干擾項：** 憑證固定 (Pinning) 是手機 APP 把伺服器憑證綁死在程式碼裡，防止駭客塞假憑證發動中間人攻擊 (MITM)。它無法保護「伺服器自己的真私鑰被駭客偷出伺服器大門」的事後錄影回溯解密問題。

#### **6. A junior developer is tasked with designing the "Password Storage Module" for a new web forum. He proudly presents his design to the Security Review Board: "To ensure blazing-fast login performance, I have decided to store all user passwords in the database after hashing them once using the incredibly fast MD5 algorithm." The Security Architect immediately rejects the design, shouting: "MD5 is dead for a reason! An attacker with a cheap GPU rig can brute-force crack millions of those hashes per second using a rainbow table!" To mathematically slow down the attacker and make off-line dictionary attacks economically unfeasible, what specific cryptographic technique MUST the developer implement?**
**(初階開發人員負責設計新論壇的「密碼儲存模組」。他得意地向安委會報告：「為確保極速登入，我決定將密碼用超快的 MD5 演算法雜湊『一次』後直接存進資料庫。」資安架構師立刻吼回：「MD5 早就死了！駭客用便宜的顯卡搭配彩虹表，一秒能破解幾百萬個這破玩意兒！」為了在數學上拖慢駭客速度，讓離線字典攻擊變得在經濟上不可行，開發者「必須」實作哪種密碼學技術？)**
A. Encrypt the database hard drives using Microsoft BitLocker or Linux LUKS. (使用 BitLocker 或 LUKS 將資料庫硬碟全盤加密)
B. Switch to the SHA-256 algorithm completely unmodified， as it is NSA-approved. (直接換成原滋原味的 SHA-256 演算法，因為它是國安局認證的)
C. Implement a slow, computationally expensive Key Derivation Function (KDF) such as PBKDF2, bcrypt, or Argon2, combined with a unique cryptographic Salt for each user. (實作緩慢且耗費計算資源的金鑰衍生函數 KDF，例如 PBKDF2、bcrypt 或 Argon2，並為每個用戶加上獨特的密碼學『鹽值 Salt』)
D. Utilize an asymmetric RSA-4096 public key to encrypt the passwords before storing them. (在儲存前使用非對稱式的 RSA-4096 公鑰將密碼加密)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 儲存人類密碼的最大核心原則就是：「絕對不能讓電腦算得太快」。像 MD5 或純種的 SHA-256 這類演算法，原本是被設計來「光速」驗證檔案有沒有損毀的。如果拿它們來存密碼，駭客偷走資料庫後，可以利用顯示卡 (GPU) 一秒鐘盲猜百萬次。軟體架構必須改用 **金鑰衍生函數 (Key Derivation Functions, KDF)**，如業界最強的 **Argon2**、**bcrypt** 或 **PBKDF2**。這些演算法最大的特色就是：它們被刻意設計得「非常慢、非常吃 CPU 與記憶體 (Work Factor)」。這會逼迫駭客在嘗試暴力破解時，電腦跑到燒掉也猜不出幾個密碼。同時，還要加上一撮隨機生成的亂數隨機字串（**Salt 鹽值**），這能徹底廢掉駭客手中準備好的彩虹表 (Rainbow Tables) 預先運算庫。
    *   **為何 A 是干擾項：** 全面硬碟加密 (FDE) 只能防止有人闖進機房拔走實體硬碟。只要資料庫軟體是開機運行狀態，駭客透過 SQL Injection 一樣能把 MD5 密碼雜湊表全部撈走。
    *   **為何 B 是干擾項：** 剛才提過，純種的 SHA-256 雖然在密碼學上沒被攻破，但它運算速度「太快了」，不適合用來儲存短且容易猜的人類密碼。必須加上 Salt 並重複運算幾萬次 (如 PBKDF2 的做法) 才行。
    *   **為何 D 是干擾項：** 密碼不能被「雙向加密 (Encryption)」，必須使用不可逆的「雜湊 (Hashing)」。如果你把密碼加密存起來，就代表系統某處必然藏有一把解密金鑰。一旦金鑰被偷，所有密碼就會瞬間還原成明碼。

#### **7. An architect is designing a highly scalable, stateless RESTful API destined for the public internet. The frontend SPA (Single Page Application) needs to prove its identity to the backend API without maintaining traditional server-side session cookies. The architect decides to use JSON Web Tokens (JWT) passed in the `Authorization: Bearer` header. However, a major security flaw in the standard JWT specification severely dictates how the architect must handle token invalidation. What is the fundamental, architectural weakness of stateless JWTs when a user clicks the "Logout" button or a token is stolen?**
**(架構師正在設計一個高擴展性、給無狀態的 RESTful API 使用的架構。前端 SPA 需要向後端證明身分，但又不想維護傳統的主機端 Session 餅乾。架構師決定採用放在 HTTP Header 裡的 JWT (JSON Web Tokens)。然而，標準 JWT 規格中有一個重大的安全缺陷，嚴格限制了架構師作廢票據的能力。當用戶點擊「登出」或票據被偷時，無狀態 JWT 的根本架構弱點是什麼？)**
A. They require massive database lookup overhead for every single API request, killing performance. (它們要求在每一次 API 請求時進行巨量的資料庫查詢，會殺死效能)
B. They are inherently unencrypted and transmit user data in plaintext base64, easily sniffed by attackers. (它們天生不加密，以純文字 base64 傳輸用戶資料，極易被駭客嗅探)
C. A stateless JWT cannot be individually revoked or invalidated before its built-in expiration time (`exp`) is reached unless complex, stateful token revocation lists (blacklists) are awkwardly introduced to the architecture. (在到達內建的到期時間前，無狀態的 JWT 無法被單獨撤銷或作廢，除非極度尷尬地在架構中引入複雜、有狀態的票據撤銷黑名單)
D. They are completely incompatible with modern OAuth 2.0 flows and Active Directory. (它們與現代 OAuth 2.0 流程與 AD 網域完全不相容)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** JWT 之所以能「無狀態 (Stateless)」讓後端飛速擴展，是因為這張票根上面已經蓋好了伺服器的數位簽章，伺服器看到簽章對了就放行，完全不需要去資料庫查這個人還在不在。但這把雙面刃的致命傷在於：**無法撤回 (Lack of Revocation)**。如果駭客偷了這張 JWT，或者使用者按下了「登出」按鈕。因為後端不會去查資料庫，所以後端根本不知道這張票應該作廢。除非等到票根上自己標示的有效期限 (`exp`) 走到盡頭，否則這張 JWT 將會一直有效。為了解決這個問題，架構師被逼得只能自己建一個「記憶體黑名單 (Deny List)」，這又把整個無狀態的美好架構給打回了有狀態 (Stateful) 的地獄。這是使用 JWT 時必須承受的最痛架構折葛。
    *   **為何 A 是干擾項：** 無狀態 JWT 正是因為「不需要查資料庫」而能提升效能，選項 A 描述的狀態恰好與 JWT 的特性完全相反。
    *   **為何 B 是干擾項：** JWT 的 Payload 的確只是 Base64 編碼（不是加密）。但這不是架構弱點，因為你可以（且應該）把 JWT 塞在 TLS 加密隧道裡傳輸，或使用進階的 JWE 去加密。最大的痛點依然是「無法撤銷」。
    *   **為何 D 是干擾項：** JWT 是目前 OAuth 2.0 和 OpenID Connect 傳遞身分資訊的主流預設格式，它們相容得不得了。

#### **8. The infrastructure team proposes a new architecture for the corporate DMZ. They plan to place the Web Server, the Application Business Logic Server, and the massive Backend Database Server all on the exact same physical machine placed directly behind the perimeter firewall. The CISO vehemently vetoes this design, citing a massive violation of a classic network security principle. The CISO demands that the architecture be split into a "Three-Tier Architecture" with strict firewalls placed *between* the Web, App, and Database layers. What foundational security principle is the CISO attempting to enforce by slicing the network into distinct, firewalled zones?**
**(基礎設施團隊提案規劃企業的 DMZ 區。他們打算把「網頁伺服器」、「應用程式邏輯伺服器」和「大型後端資料庫」全部塞在同一台實體設備上，並放在防火牆後面。CISO 痛批此設計違反了經典網路安全原則，強烈否決。CISO 命令架構必須被拆解為「三層式架構 (Three-Tier Architecture)」，並且在每一層之間都佈署嚴格的防火牆。CISO 透過把網路切分成多個防火牆區域，是在強制實施哪項基礎安全原則？)**
A. Defense in Depth (Layered Defense) (縱深防禦 / 多層防禦)
B. The Principle of Complete Mediation (徹底中介原則)
C. The Principle of Least Common Mechanism (最少共用機制原則)
D. The Security through Obscurity paradigm (隱晦式安全範式)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 如果把所有東西（大門、客廳、裝滿黃金的金庫）全部放在同一個房間裡，只要對外的網頁伺服器（大門）被駭客的任意程式碼執行漏洞 (RCE) 給打穿，駭客就能在同一台機器裡直接撈空資料庫。這叫做單點故障 (Single Point of Failure)。CISO 強制實施的經典三層式架構（Web層、App層、DB層），並用防火牆層層隔離。這意味著駭客打穿了 Web 之後，還得面對第二道防火牆的阻力去打 App 層，最後再面對第三道牆才能碰到資料庫。這種像剝洋蔥一樣，在駭客前進的路徑上佈署重重關卡與減速墊的哲學，就是最經典的 **縱深防禦 (Defense in Depth)** 或稱多層次防禦。
    *   **為何 B 是干擾項：** 徹底中介 (Complete Mediation) 是指系統的每次存取（連去讀取快取）都必須被重新檢查權限，它強調的是軟體驗證的完整性，而非物理網路的分層切割。
    *   **為何 C 是干擾項：** 最少共用機制 (Least Common Mechanism) 強調不同的使用者或服務不要共用太多資源（像不要共用同一個記憶體區塊），以免其中一個出事牽連別人。雖然與資源隔離有關，但「建立多層防禦牆」最精準的詞彙是縱深防禦。
    *   **為何 D 是干擾項：** 隱晦式安全是種把門牌拿掉假裝這裡沒房子的鴕鳥心態，通常被視為不良的資安實踐。

#### **9. When designing a secure logging and auditing capability for a centralized log server (e.g., Splunk or ELK stack), the architect must ensure that attackers who successfully breach a web server cannot simply delete their tracks by altering the logs they just sent to the central server. Which of the following architectural designs provides the STRONGEST guarantee of log integrity and prevents post-compromise tampering by the attacker?**
**(在設計集中式日誌伺服器的安全記錄與稽核架構時，架構師必須確保：那些已經打穿 Web 伺服器的駭客，不能只是簡單地竄改他們剛剛送往中央日誌伺服器的犯罪紀錄來消滅證據。下列哪一種架構設計能提供最強大的「日誌完整性保證」，防止駭客在入侵後進行竄改事後湮滅？)**
A. Storing the logs in a traditional SQL database table indexed by timestamp. (把日誌存在傳統 SQL 資料庫表裡面，並用時間戳記來建立索引)
B. Pumping the logs into a "Write-Once, Read-Many (WORM)" immutable storage bucket and cryptographically signing the log chains. (將日誌灌入「單寫多讀 (WORM)」的不可變儲存桶中，並對日誌鏈進行密碼學上的數位簽章)
C. Zipping and password-protecting the daily log files using a 4-digit PIN. (把每天的日誌檔壓縮起來，加上一個 4 位數密碼保護)
D. Storing the logs in volatile RAM on the central server for faster search querying. (把日誌存在中央伺服器會揮發的 RAM 裡以加快搜尋速度)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 當高階駭客（如 APT 組織）入侵成功時，他們做的第一件事絕對不是搬資料，而是去「清空日誌 (Clear logs)」，讓鑑識專家無從查起。為了跟這種滅證行為對抗，架構上最無敵的手段就是導入 **「唯寫一次，多次讀取 (Write-Once, Read-Many / WORM)」** 的儲存架構，或是現代雲端中的「Object Lock (不可變儲存 Immutable Storage)」。這種設備在硬體設計或底層架構上，就徹底剝奪了「刪除與修改」的權利。哪怕是你拿著最高的 Admin 權限，在硬體時間鎖到期之前，都無法刪去那行犯罪紀錄。配合將前一行日誌的雜湊值包進下一行建立成加密鏈（類似區塊鏈概念），這是業界保證日誌完整性 (Log Integrity) 最高的規格。
    *   **為何 A 是干擾項：** 傳統的女 SQL 資料庫隨時可以接受 `UPDATE` 或是 `DELETE` 指令。駭客只要拿到資料庫授權，就能輕鬆抹走紀錄。
    *   **為何 C 是干擾項：** 駭客大可以直接把你壓縮好的 Zip 檔給整個「刪除 (Shift+Del)」。而且 4 位數被秒破的 PIN 碼在密碼學上是個笑話。
    *   **為何 D 是干擾項：** RAM 只要遇到主機重新開機或斷電，資料就會瞬間蒸發歸零，完全無法作為需要永久保存的稽核證據中心。

#### **10. A cloud-native application is being built using AWS cloud services. The architecture requires a backend Lambda function (compute) to read sensitive customer photos stored in an S3 bucket (storage). The junior developer suggests creating a permanent IAM user named "lambda-user," generating long-lived Access Keys, and hardcoding those keys directly into the Lambda function's source code so it can access the bucket. In modern secure cloud architecture, this is considered a catastrophic anti-pattern. What is the standard, secure architectural method for granting the Lambda function the necessary permissions?**
**(正在使用 AWS 服務構建雲原生應用。架構需要一個後端 Lambda 函數去讀取 S3 桶內包含顧客私密照片的資料。初階開發者提議：「建立一個永久的 IAM 使用者，產出一把長期的金鑰，然後把這把金鑰硬生生寫死在 Lambda 的程式碼裡面」。在現代安全的雲端架構中，這被視為一場災難級的反模式 (Anti-pattern)。請問，賦予 Lambda 足夠權限的標準、安全架構作法是什麼？)**
A. Passing the Root account credentials to the Lambda function via environment variables. (透過環境變數把雲端根帳號 (Root) 的密碼傳給 Lambda 函數)
B. Making the S3 bucket entirely public and utilizing obscure, unguessable file names (Security by Obscurity). (把 S3 儲存桶對外完全公開，並利用難以猜解的亂碼檔名來保護資料 (隱晦式安全))
C. Assigning a temporary IAM Role directly to the Lambda function's execution environment, allowing the cloud infrastructure to automatically rotate and inject short-lived, ephemeral credentials. (直接將一個臨時的 IAM 角色 (Role) 指派給 Lambda 函數的執行環境，讓雲端基礎設施能夠自動輪替並注入「生命週期極短」的臨時憑證)
D. Requiring the Lambda function to perform a CAPTCHA challenge before downloading (要求 Lambda 函數在下載檔案前解開一個 CAPTCHA 機器人驗證圖形)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 在雲端架構 (AWS, Azure, GCP) 中，最大的噩夢就是「帶有永久生命 (Long-lived) 的金鑰不小心連同程式碼一起被上傳到 GitHub 公開庫中」。爲了徹底解決金鑰外洩的問題，雲端巨頭們發明了 **IAM 角色 (Roles) 與暫時性安全憑證機制**。架構的標準做法是，你把一件具有特定權限的「衣服 (IAM Role)」直接穿在 Lambda 這個運算環境身上。雲端的後台系統會魔法般地，在每次 Lambda 啟動時，自動丟進一把只存活 15 分鐘到 1 小時的臨時鑰匙。因為鑰匙極度短命且完全自動輪替，開發者連看都看不到鑰匙，徹底拔除了硬編碼密碼 (Hardcoded Secrets) 的架構毒瘤。
    *   **為何 A 是干擾項：** 把擁有能刪掉整間公司權限的超級根帳號 (Root) 放進應用程式裡去用，這是違反最低權限原則 (Least Privilege) 最嚴重的死刑罪。
    *   **為何 B 是干擾項：** 把桶子公開，遲早會被網際網路上的爬蟲程式給猜對並下載。這是極度糟糕的隱晦式掩耳盜鈴安全。
    *   **為何 D 是干擾項：** CAPTCHA 驗證圖形是給人類的眼睛看的。一台在後台運作的機器 (Lambda) 沒有眼睛，它解不開這個圖形，這會阻斷自動化流程。

#### **11. You are applying the STRIDE threat modeling framework to a proposed architecture for managing electronic medical records. You identify a potential flaw where a malicious nurse could alter a patient's dosage record, and the system would have absolutely no way to prove *who* actually changed the data. Which specific STRIDE threat category does this inability to trace an action back to an individual represent, and what is the required architectural control?**
**(你正把 STRIDE 威脅建模套用在電子病歷的架構草圖上。你發現一個潛在漏洞：如果有心懷惡意的護士竄改了病患的用藥紀錄，這個系統竟然完全無法證明「到底是誰」改的。這種無法將惡意行為追溯到特定人類身上的無力感，屬於 STRIDE 模型中的哪個特定類別？又需要加上哪種架構控制來制裁它？)**
A. Threat: Information Disclosure. Control: Data Masking. (威脅：資訊洩露。控制：資料遮罩)
B. Threat: Denial of Service. Control: Rate Limiting. (威脅：阻斷服務。控制：速率限制)
C. Threat: Repudiation. Control: Non-repudiation via comprehensive Audit Trails and Digital Signatures. (威脅：抵賴。控制：透過全面稽核軌跡與數位簽章達成不可抵賴性)
D. Threat: Spoofing. Control: Strong Password Policies. (威脅：偽裝身分。控制：強密碼政策)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** STRIDE 裡的 **Repudiation (抵賴 / 否認)**，指的就是壞人做了壞事，卻能雙手一攤在法官面前說：「沒有證據是我做的啊，說不定是電腦壞了」。當護士改了藥卻找不到紀錄，這就是系統在抵賴防禦上的嚴重缺失。要在軟體架構層級對付「抵賴」，最強大的武器是 **不可否認性 (Non-repudiation)** 控制措施。這包含實作堅不可摧的 **稽核軌跡 (Audit Trails / Logs)**，紀錄下人事時地物，或者使用 **數位簽章 (Digital Signatures)**，讓該護士插入醫事自然人憑證 IC 卡簽章後才能修改藥單，讓她事後百口莫辯。
    *   **為何 A 是干擾項：** 護士是合法看病歷的人，但她做了不合法的「寫入修改」動作。這不是把資料看光光的資訊洩露 (Disclosure)。
    *   **為何 B 是干擾項：** 護士沒有想要把整座醫院的伺服器給搞當機 (DoS)，她只是靜悄悄地改了一個欄位的數字。
    *   **為何 D 是干擾項：** 雖然在登入時沒有 Spoofing (因為她確實用自己的帳號登入了)，但重點是「改動後系統沒有留下追溯指紋」。 Spoofing 防的是「她假冒別的護理長登入」，但題目說的是「無法證明誰改變了數據」的事後追查能力缺失 (Repudiation)。

#### **12. A software architect is reviewing an application that utilizes an older XML parser. The application accepts XML files uploaded by users to generate PDF invoices. The security team demonstrates a terrifying attack: they upload a specially crafted XML file containing a `<!ENTITY>` directive that instructs the XML parser to silently read the contents of the server's `/etc/passwd` file and embed it into the final PDF output. What specific architectural vulnerability is the application suffering from, and how must it be mitigated at the design level?**
**(軟體架構師正在審查一個使用老舊 XML 解析器的發票應用程式。安全團隊示範了一次恐怖的攻擊：他們上傳一個精心構造的 XML 檔，裡面藏有關鍵指令 `<!ENTITY>`。這個指令竟然叫 XML 解析器去偷看伺服器底層的密碼檔 `/etc/passwd`，然後悄悄把它塞到最終產出的 PDF 收據裡。這個應用程式正遭受哪種特定架構漏洞的折磨？而且在設計層面必須如何緩解？)**
A. Vulnerability: Cross-Site Request Forgery (CSRF). Mitigation: Use Anti-CSRF tokens. (漏洞：CSRF。緩解：使用防護權杖)
B. Vulnerability: Buffer Overflow. Mitigation: Switch from C++ to a memory-safe language like Rust. (漏洞：緩衝區溢位。緩解：轉用安全的 Rust 語言)
C. Vulnerability: XML External Entity (XXE) Injection. Mitigation: The architect must explicitly configure the XML parser library to aggressively disable DTDs (Document Type Definitions) and forbid the resolution of external entities. (漏洞：XML 外部實體 (XXE) 注入。緩解：架構師必須在程式中明確設定 XML 解析庫，強硬關閉 DTDs (文件類型定義)，並全面禁止外部實體的解析行為)
D. Vulnerability: SQL Injection. Mitigation: Implement an Object-Relational Mapper (ORM). (漏洞：SQL 注入。緩解：實作 ORM)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這題描述的是極度經典且被列入 OWASP Top 10 的 **XML 外部實體 (XXE, XML External Entity) 注入攻擊**。問題的根源在於：許多老舊的 XML 函式庫，預設會非常「熱心」地去執行 XML 檔案表頭裡面定義的一種叫做 DTD 外部實體的怪異語法（例如去讀取本機檔案，或是發送 SSRF 網路請求）。這種過度熱心造成了極大的災難。在架構與實作層面的唯一解藥是：開發人員在程式開發的當下，【必須】去修改並實例化設定 XML 解析器的物件，**強制且無情地把 DTD (Document Type Definitions) 的解析功能給關閉拋棄 (Disable DTDs)**，禁止解析器去讀取外部檔案資源。這樣 XML 解析器就只會乖乖把它當作純文字來解讀。
    *   **為何 A、B、D 是干擾項：** CSRF 是誘騙瀏覽器點連結；Buffer Overflow 是記憶體爆炸；SQL Injection 是欺騙後端資料庫。全都不涉及「處理夾帶邪惡指令的 XML 文件」這個極具專一性的解析器地雷領域。

#### **13. During the architecture design phase of an API gateway that will be exposed to the public internet, the lead engineer is terrified of "Resource Exhaustion" attacks (Layer 7 DDoS), where an attacker writes a simple script to call the `/api/v1/heavy-calculate` endpoint 10,000 times per second, instantly melting the backend databases. To protect the backend services, which classic architectural defense pattern MUST be implemented directly at the API gateway layer?**
**(在設計一個要暴露在公網上的 API 閘道時，主任工程師對「資源耗盡」攻擊 (第七層應用層 DDoS) 感到無比恐懼。駭客只要寫個腳本，一秒鐘呼叫那個最吃效能的 `/api/v1/heavy-calculate` 終結點一萬次，就能在瞬間把後端資料庫給融化當機。為了保護後方嬌弱的服務，在 API 閘道這層「必須」實踐哪一種經典架構防禦模式？)**
A. Implementing rigorous Input Validation to check for SQL injection characters. (實作嚴密的輸入驗證以檢查 SQL 注入字元)
B. Enforcing strict Rate Limiting and Throttling controls per API key or IP address. (強制實行嚴格的「速率限制 (Rate Limiting)」與「節流 (Throttling)」控制，鎖定每個 API 金鑰或 IP 位址)
C. Utilizing a Global Server Load Balancing (GSLB) algorithm based on geographic latency. (利用基於地理延遲的全球伺服器負載均衡 GSLB 演算法)
D. Encrypting all backend database communication with TLS 1.3. (把所有後端資料庫通訊用 TLS 1.3 加密)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** API 這個對全世界開放的大門，最大的弱點就是它不知道節制。要解決單一資源被人類或機器人惡意瘋狂點擊榨乾的第七層 DDoS 問題，最標準的架構防護就是在 API Gateway 裝上 **速率限制 (Rate Limiting)** 與 **節流 (Throttling)** 閥門。架構師可以設定「同一個 IP 或付費帳號，一秒鐘最多只能呼叫這個複雜功能 5 次」。一旦跨過紅線，API 閘道會直接不留情面地踢回 HTTP 429 (Too Many Requests) 錯誤，連資料庫的邊都碰不到。這是在微服務架構中保護資源的黃金準則。
    *   **為何 A 是干擾項：** 輸入驗證是檢查封包裡面有沒有裝炸藥（惡意字元）。但現在駭客發送的是「100% 合法且正確」的封包，他只是用海嘯般的數量來淹死你。輸入驗證防不住「大量的正常請求」。
    *   **為何 C 是干擾項：** 負載平衡只是把這洪水般的流量平分發給 10 台機器去承受。如果駭客的火力遠超你的防線，10 台機器遲早會一起融化。你必須在門口「丟掉/阻擋」過多的請求，而不是平均接收他們。
    *   **為何 D 是干擾項：** TLS 加密是防竊聽，不是防別人不停打電話叫你幫他算數學題。

#### **14. When designing the administrative backend interface for a sprawling content management system (CMS), the architect creates three distinct roles: "Content Writer," "Editor," and "Super Administrator." The architect strictly enforces a rule: A Content Writer can draft an article, but they are physically locked out of the "Publish" button. Only an Editor, using a separate account, can review the draft and click "Publish." What foundational security design principle is the architect implementing to prevent a single rogue writer from bringing down the website with terrible content?**
**(在設計大型新聞系統的後台時，架構師切出了三種角色：「內容寫手」、「主編」和「超級管理員」。架構師強制了一個鐵律：寫手可以寫草稿，但他們物理上被拔除了『發布』按鈕。只有當換成主編登入，審查完內容後，才能點擊那個『發布』按鈕。架構師這種試圖防止單一失控員工就把垃圾文章送上網站首頁的設計，是基於哪項根本安全原則？)**
A. The Principle of Complete Mediation (徹底中介原則)
B. The Principle of Defense in Depth (縱深防禦原則)
C. Separation of Duties (Two-Man Rule) (職權分離 / 雙人驗證規則)
D. The Principle of Failsafe Defaults (故障安全預設原則)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是一個非常古老但有效的防錯與防弊機制，稱為 **職權分離 (Separation of Duties, SoD)** 或雙人規則 (Two-Man Rule，就像發射核彈需要兩把鑰匙)。它的核心哲學是：「這個高風險的關鍵動作（例如發布頭條新聞、轉出一百萬美元），絕對不能由同一個人在沒有監督的情況下完成」。必須強制拆分成「提議（寫手）」與「核准（主編）」兩個必須由「不同真實身分」來執行的權限角色，這樣可以大幅減少詐欺錯誤或單人員工崩潰報復所帶來的影響。
    *   **為何 A 是干擾項：** 徹底中介是每一次連線網路前都要查核密碼權限，這是底層計算邏輯的設計。
    *   **為何 B 是干擾項：** 縱深防禦是疊加多個不同機制的防護罩（例如密碼加上臉部辨識再加上警衛）。而職權分離純粹是在「人力行政流程」上將權力橫向切開。
    *   **為何 D 是干擾項：** 故障安全預設機制是指當意外發生時，系統該採用「允許」還是「拒絕」的預設傾向。

#### **15. A software team is building an open-source password manager application. The community raises a massive concern: "If the government subpoenas your servers, or if a rogue database admin goes rogue, they could steal all our encrypted password vaults!" To fundamentally architect the system so that *even the application creators and database administrators* mathematically cannot decrypt the user's data, which specific cryptographic architecture MUST be enforced?**
**(軟體團隊正在打造開源密碼管理器軟體。社群發出強烈質疑：「如果政府拿搜索票查扣你們的伺服器，或者有一個拿著最高權限的惡意資料庫管理員內鬼，他們就可以把我們那些加密的密碼庫備份包全偷走解密！」為了在架構層面上，保證『即使是這個 APP 的開發原廠和資料庫管理員』都絕對無法在數學邏輯上解開用戶的心血，必須強制採用哪種特定的密碼學架構？)**
A. Transparent Data Encryption (TDE) managed by the cloud provider. (雲端供應商代管的透明資料加密 TDE)
B. End-to-End Encryption (E2EE) / Client-Side Encryption, where the decryption keys are generated and held exclusively on the user's local device and are NEVER transmitted to the server. (端到端加密 E2EE / 用戶端加密，解密金鑰完全在使用者本機設備上生成並保管，【絕對不會】被上傳到伺服器)
C. Wrapping the entire database in an AES-256 encrypted volume using a key managed by a Hardware Security Module (HSM) in the data center. (用機房裡的 HSM 硬體保險箱管鑰匙，把整個資料庫用 AES-256 加密包起來)
D. Enforcing strict Multi-Factor Authentication (MFA) for the database administrators. (對所有資料庫管理員進行極度嚴苛的 MFA 認證)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 要達成這種「連官方原廠跟後台工程師都無能為力」的終極隱私型態（這被稱為零知識架構 Zero-Knowledge Architecture），唯一的解法就是將加解密的戰場，從伺服器遠遠地推到使用者手上的那支手機裡。這叫做 **端到端加密 (E2EE) 或用戶端加密 (Client-Side Encryption)**。在這種架構下，使用者在手機上打出自己的超級密碼，手機當場算出一把解密鑰匙；然後手機上的 APP 會先把密碼金庫弄成一堆亂碼後，才把這個被層層包裹的密碼金庫快遞上傳進雲端伺服器。雲端伺服器從頭到尾只是一塊「不會飛的儲存硬碟」，它從來沒有摸過也看不到這把能開鎖的實體鑰匙。這種架構保證了只要使用者不吐露超級密碼，聯邦調查局搬走伺服器也無濟於事。
    *   **為何 A 與 C 是干擾項：** TDE 或是加密磁區，都是「靜態資料加密 (Data at Rest)」的招式。問題在於，那把用來開這些磁區的加密金鑰，最終還是被「公司內部的工程師或雲端服務商」握在手中控管的！也就是說，當收到傳票或管理員發狂時，他們隨時可以拿著鑰匙去開門。
    *   **為何 D 是干擾項：** MFA 是防外人偷工程師帳號。如果工程師自己就是心懷惡意的內鬼，沒有 E2EE 保護的話，他用自己的指紋加 MFA 登入後，還是一樣能直接把所有用戶資料全拉出來看。

#### **16. An experienced architect is designing an authentication microservice. Currently, the system responds to a failed login for a non-existent username with: `"Error: Username does not exist."` And it responds to a failed login for a valid username but wrong password with: `"Error: Incorrect password."` The security review board rejects this design, stating it violates a core concept of preventing Information Disclosure. What is the standard architectural fix to mitigate this specific vulnerability?**
**(資深架構師正在設計登入微服務。目前，如果該帳號根本不存在，系統會好心回應：「錯誤：使用者帳號不存在」；如果帳號存在但密碼猜錯，則回應：「錯誤：密碼不正確」。安全審核委員會退回了這個設計，指出其違反了防止資訊洩漏的核心概念。為了修補這個漏洞，標準的架構修改做法是什麼？)**
A. The system must deliberately pause for 30 seconds before returning the error message to slow down the attacker. (系統必須故意停頓 30 秒再秀出錯誤以免駭客猜太快)
B. The system must return a generic, unified error message such as `"Invalid username or password"` regardless of which part of the credential was wrong, preventing "Username Enumeration." (不論是哪個部分打錯了，系統必須一律回傳一模一樣的模糊、中性字眼，例如：「無效的使用者名稱『或』密碼」，藉此徹底封殺「帳號枚舉/盤點攻擊」)
C. The system must immediately lock the public IP address after the first failed attempt to prevent brute forcing. (只要失敗一次立刻鎖定公網 IP 防止暴力破解)
D. The system must demand the user solve a complex CAPTCHA before displaying the exact error message. (在秀出明確的錯誤訊息之前，強迫使用者先點圖形驗證碼)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這個在業界極度被頻繁檢討的架構問題叫做 **帳號枚舉攻擊 (Username / Account Enumeration)**。如果系統「太誠實」了，駭客就可以寫個腳本，塞進全台灣兩千萬人的身分證字號。只要系統回傳「密碼錯誤」，駭客就知道「這個身分證字號確實在這個網站有註冊過」。他就能把這些有效的活人帳號盤點出來，打包去黑市賣或是進行後續的密碼撞庫攻擊。解決這個資訊洩露的架構解法極度簡單且標準：**無論對錯，一律統一回文 (Generic Error Messages)**。不管是帳戶不存在還是密碼打錯，永遠只給一句模糊的「帳號或密碼輸入錯誤」。這讓駭客無法從伺服器回覆的微小文字差異中榨取出任何有用的資訊情報。
    *   **為何 A 是干擾項：** 故意拖延時間對防護 DDoS 或暴力猜解的確有一點點用（雖然後帶通常是用 Rate limiting 而不是單純停頓）。但這並沒有掩蓋那個「有差別的錯誤訊息」。如果你停了 30 秒後，結果還是吐出「本站查無此人」，駭客只要多搞幾台肉雞平行請求，一樣能順利盤點出有誰。
    *   **為何 C 是干擾項：** 失敗一次就鎖定會引發強烈的「阻斷服務攻擊 (DoS)」。駭客只要跑一次腳本，全台灣今天連星巴克 Wi-Fi 喝咖啡的人就會全部因為共用 IP 而無法登入貴公司的 APP。這是極端糟糕的設計。
    *   **為何 D 是干擾項：** CAPTCHA 應該放在「送出登入請求」之前。如果放在後面，只是白忙一場。

#### **17. A banking application needs a secure way to allow a third-party accounting application (like Mint or Xero) to "read-only" a user's transaction history without the user ever sharing their actual banking password with the accounting app. Which standardized delegation protocol is specifically designed at the architectural level to allow a user to grant limited access to their resources to a third-party application via a scoped token?**
**(一家銀行應用程式需要一種安全機制，讓第三方的記帳軟體 (如 Mint) 可以「唯讀」這位用戶的刷卡明細。但是，銀行絕對不允許用戶把自己的「網銀密碼」直接輸入、分享給這個第三方記帳軟體。在架構層面，哪一個標準的委派協定是專門為這件事而生，讓用戶能透過發放一個「受限制的代幣 Token」，來給予第三方有限的存取權限？)**
A. SAML 2.0 Identity Federation (SAML 2.0 身分聯合認證)
B. Kerberos Key Distribution Center (KDC) (Kerberos 金鑰分發中心)
C. OAuth 2.0 (Authorization Framework) (OAuth 2.0 授權框架)
D. Lightweight Directory Access Protocol (LDAP) (輕量級目錄存取協定)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是現代 Web API 架構的基礎考題。當你要讓「應用程式 A」去讀取你在「網站 B」上面的資料，但你又死都不想把你的帳號密碼交給應用程式 A 的時候，你就必須使用 ** OAuth 2.0 網路授權框架 (Authorization Framework)**。在 OAuth2 的流程裡，你會被跳轉到銀行的官網（你的密碼是在銀行的地盤輸入的），然後銀行會問你：「這個記帳軟體想要每個月『唯讀 (Scope = Read)』你的刷卡明細，你同意嗎？」同意後，銀行不會交出你的密碼，而是會發行一張能使用有限期間的 **存取權杖 (Access Token)** 丟給這個第三方記帳軟體。這是授權委派的最核心標準做法。（備註：OpenID Connect / OIDC 則是架構在 OAuth 2.0 之上用來做「身分認證/你是誰」的）。
    *   **為何 A 是干擾項：** SAML 的主要應用場景是對企業員工實施「單一企業內部的跨系統不用掏出密碼身分登入」。雖然它也是跨域的，但 OAuth 2.0 是在網際網路上解決「授權第三方存取 API」霸主，情境更貼近於此題。
    *   **為何 B 是干擾項：** Kerberos 那隻三頭犬是在微軟古老的 Windows AD 內網裡面發號車票 (Tickets) 控制誰能印表機的那套協議，它根本走不出內網到那廣大的網際網路雲端應用程式中。
    *   **為何 D 是干擾項：** LDAP 是讀取如電話簿般員工資料庫的標準，與委派 API 授權完全無關。

#### **18. In the context of secure architectural design patterns, the concept of a "Choke Point" or "Single Point of Access Control" is highly recommended for filtering incoming traffic. If a web application forces every single incoming HTTP request to pass through a singular, heavily fortified logic module that validates authentication, authorization, and input sanitization BEFORE routing the request to the internal business logic, this monolithic gatekeeper is an application of which fundamental security principle?**
**(在安全架構設計模式下，極度推薦使用「咽喉點 (Choke Point)」或「單一存取控制點」的概念來過濾湧入的流量。如果一個網頁應用程式強迫每一個進來的 HTTP 封包，都必須【先】通過一個單一且設立重裝防禦的邏輯模組，進行極度嚴格的身分驗證、授權確認，並把輸入惡意字元砍掉後，才肯給放行前往內部的商業邏輯核心。這個宛如巨塔守門員的設計，是應用了哪一項基礎安全原則？)**
A. The Principle of Weakest Link Optimization (最弱環節優化原則)
B. The Principle of Economy of Mechanism (經濟機制原則/設計極簡原則)
C. The Principle of Complete Mediation (徹底中介原則 / 全面仲裁原則)
D. The Principle of Open Design (開放設計原則)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 當程式架構規定：「不准有後門、不准有側門！任何人想進入城堡（拿任何資源或呼叫方法），不管是內部員工還是外面來的，通通都得排隊經過『正大門口的收費站』攔檢盤查。」這個設立無敵單一咽喉關卡 (Choke Point/API Gateway pattern) 的行為，在資訊安全的哲學基礎中稱為 **徹底中介 / 全面仲裁原則 (Complete Mediation)**。它的精神在於強制所有的存取請求都必須「每次且全面的」受到檢查機制的仲裁，沒有人擁有「繞過大門」的特權捷徑。
    *   **為何 A 是干擾項：** 雖然有句名言「安全強度取決於最脆弱的那個環節」，但這並不是設立一個單一過濾大站台 (Choke point) 這個架構設計所對應的經典資安工程學名詞。
    *   **為何 B 是干擾項：** Economy of Mechanism (設計要極簡、簡單純粹才不會容易生蟲子)。這不是在講設立統一海關檢查站的事。
    *   **為何 D 是干擾項：** Open Design 重申過很多次，防禦不要靠藏招躲貓貓。跟本題情境無關。
