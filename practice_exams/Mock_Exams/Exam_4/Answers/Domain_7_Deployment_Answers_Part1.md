# 第四套全真模擬試題 (Exam 4) - 答案與詳解本
## 領域 7：安全的軟體部署、營運與維護 (Secure Software Deployment, Operations, Maintenance) (13題) - Part 1 (Q1-Q5)

---

#### **1. A DevOps engineer is configuring a CI/CD pipeline. Instead of a human administrator manually SSHing into production servers to run installation scripts (which creates configuration drift and security risks), the engineer writes configuration files (e.g., Terraform or Ansible playbooks) that define the required state of the production environment. The pipeline automatically provisions the servers exactly as defined in the files. What is this security-enhancing deployment paradigm called?**
**(一名看守著『大內皇宮流水生產線 (CI/CD pipeline)』的機關總管。過去，每當皇宮要蓋一座新偏殿 (production servers)，總管都得派十幾個老師傅，每個人拿著鐵鎚進去敲敲打打 (manually SSHing to run scripts)。結果每次蓋出來的房子，窗戶大小都不一樣，甚至還有人忘記上鎖 (configuration drift and security risks)！為了解決這個大麻醉，機關總管發明了一種神聖的【『天兵造物符咒 (Terraform/Ansible playbooks)』】！他把「這座偏殿需要三根柱子、兩道金屬門、而且門上必須掛著三道九重大鎖 (required state)」的要求，全部寫在符咒上。接著，他把符咒丟進流水線裡，系統就會自動在皇宮裡【憑空變出】一座跟符咒上寫得一模一樣、分毫不差的完美偏殿 (automatically provisions exactly as defined)！請問，這種用寫符咒來代替工人敲打、保證每一座房子都絕對安全標準的革命性建設兵法，尊號為何？)**
A. Manual Patch Management (手動貼膏藥是發現城牆破洞了派大爺去抹泥巴，這是最會出錯的老舊做法，完全跟「自動化符咒生成」沾不上邊)
B. Infrastructure as Code (IaC) (這就是名震四方、讓所有手工敲打伺服器的老爺爺集體失業的：【『上帝創世之基礎架構即程式碼 (Infrastructure as Code / IaC)！』】。在過去 (Pet Servers 時代)，每一台伺服器都是系統管理員當寵物養的，裡面有著無數手動敲進去的黑魔法設定，只要管理員離職，伺服器一壞就徹底死機。有了 IaC 之後 (Cattle Servers 時代)！你要蓋一百台一模一樣、且【預設已經套用所有國防級安全設定 (Hardened)】的伺服器。你不需要派一百個人，你只需要寫一份 JSON 或 YAML 的「建築藍圖 (Code)」。當這份藍圖通過了 CI/CD 的測試與安檢後，執行程式 (如 Terraform) 就會在一分鐘內，在雲端精準地把這一百台伺服器一磚一瓦地造出來！沒有人為疏失、沒有擅自打開的防火牆 Port、而且隨時可以一鍵推倒重建！這是在雲端時代保證部署安全性的絕對第一真理！)
C. Continuous Monitoring (CM) (持續監控是在房子蓋好之後，派幾千條警犬在房子裡到處聞看有沒有小偷。它管的是「營運」時的眼睛，不管「部署」時房子怎麼蓋出來的)
D. Chaos Engineering (混沌工程是故意派一隻哥吉拉去把城牆踢破，看看城市會不會因此毀滅。這是一種壓力與容錯測試，不是蓋房子的正規手法)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是對 **「基礎架構即程式碼 (Infrastructure as Code, IaC)」** 的標準定義。
    *   **IaC 的核心精神：** 不再透過點擊 UI (ClickOps) 或手動登入伺服器敲指令來建立與設定伺服器、網路資源 (VPC, Firewall rules)、資料庫。而是將這些 "環境需求" 撰寫成機器可讀的宣告式檔案 (如 Terraform的 `.tf`, AWS CloudFormation, Ansible)。
    *   **在 SSDLC/DevSecOps 中的安全價值：**
        *   **消除組態飄移 (Configuration Drift)：** 確保每次部署的環境都是 100% 一致的，消除了 "在 Dev 可以跑，在 Prod 卻報錯" 或是 "Prod 上的防火牆被手動偷開了一個洞" 的風險。
        *   **可審查與可版本控制：** IaC 檔案與應用程式碼一起放在 Git 中。任何人想修改防火牆規則，都必須發 PR (Pull Request) 並經過安全團隊的 Code Review。
        *   **IaC 掃描 (Shift-Left Security)：** 可以在部署 *之前*，使用工具 (如 Checkov, tfsec) 掃描這些 IaC 檔案，確保沒有「S3 Bucket 設為 Public」這類致命錯誤被建置出來。

#### **2. An organization is deploying a new version of their e-commerce application. To minimize downtime and reduce the risk of a catastrophic failure affecting all users simultaneously, they deploy the new version alongside the old version. They configure the load balancer to route only 5% of real user traffic to the new version initially to monitor for errors. If it is stable, they will gradually increase the traffic to 100%. What deployment strategy is this?**
**(一家掌管全國百萬老百姓買菜的『皇家線上大菜市場 (e-commerce application)』要推出極致升級版的「2.0 豪華純金菜攤」了！但大總管非常怕死，他怕這金菜攤如果一開張就垮了，全城老百姓買不到菜會暴動 (catastrophic failure affecting all users)。為了保住腦袋，大總管使出了一計【『試水溫大陣法』】！他把新打造的金菜攤，偷偷蓋在舊木頭菜攤的旁邊 (deploy new version alongside old version)。然後，他在大門口掛了個牌子，讓門鈴機關 (load balancer) 【只把進門的「百分之五」的懵懂老百姓，偷偷引導去新的金菜攤買菜 (route only 5% of traffic)】，剩下的百分之九十五還是去原本安全的舊菜攤。大總管躲在後面死死盯著，如果那 5% 的客人沒被毒死、沒抱怨，他才慢慢把門鈴調成 10%、50%，直到最後把舊菜攤拆掉。請問！這種「先拿少數人當小白鼠探雷，安全了再全面推進」的超高安全部署兵法，名喚為何？)**
A. Blue/Green Deployment (藍綠部署陣法也是蓋兩座菜攤。但它的做法是「一刀切」！也就是蓋好新菜攤後，把大門口原本指向藍攤的牌子，【瞬間 100% 翻轉】指向綠色新菜攤！如果綠菜攤出事，再【瞬間 100% 翻回去】藍菜攤。它沒有「5%、10% 慢慢調整」的這個過渡期。所以雖然它也能無縫接軌，但這題特別強調「流量漸進比例」，所以藍綠不是最精準的答案)
B. Canary Release (這就是名震四海、讓無數工程師免於因為大爆炸而被祭天的：【『金絲雀試毒大無畏陣法 (Canary Release / 金絲雀部署)！』】。這個名字來自於早期礦工下礦坑時，會提著一隻對毒氣極度敏感的「金絲雀」走在前面。如果前面有毒氣，金絲雀會先死掉，礦工就能趕快逃命。在軟體部署中，那 5% 被導向新系統的真實使用者流量，就是我們的金絲雀！我們拿這些真實流量來測試新版本到底有沒有潛在的雷。如果這 5% 的伺服器開始瘋狂報錯 (Error Rate 飆高)，監控系統會立刻判定「金絲雀死了」，並且【自動把這 5% 的人踢回舊系統 (Rollback)】，這讓災情被完美控制在極小範圍。如果金絲雀活得好好的，就慢慢推進。這是現代雲端微服務追求「零停機且極低風險」的最高級部署術！)
C. In-Place Update (就地更新是直接把舊菜攤拆除，然後在原來的土地上蓋新菜攤 (停止服務 -> 升級 -> 重啟)。這種陣法在施工期間，客人完全沒菜買 (Downtime)，而且萬一新菜攤蓋壞了，你連舊菜攤都回不去，這是最危險的古老部署法)
D. Big Bang Deployment (大爆炸部署是選在一個夜黑風高的半夜，把全國所有的舊菜攤同時炸毀，然後同時升起所有的新菜攤！這叫「不成功便成仁」。一旦出差錯，全國死機，老總管明天就人頭落地。這是高可用性營運絕對要避免的禁忌)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是 **「金絲雀發佈/部署 (Canary Release / Canary Deployment)」** 的經典定義。
    *   **關鍵辨識點：** 題幹中的 **"route only 5% of real user traffic"** 與 **"gradually increase"** 是 Canary 獨有的特徵。
    *   **Blue/Green (藍綠部署) 的區別：** 藍綠部署也是兩套環境 (Blue 和 Green) 同時存在。但流量切換通常是 100% 的 (在 Router/Load Balancer 層級一鍵切換)。雖然可以做到 Zero-Downtime，但如果新版本有 Bug，100% 的使用者都會瞬間受影響（儘管可以光速切換回來）。
    *   **Canary 的安全優勢：** 它可以將 "釋出新版本帶來的不預期風險 (爆炸半徑 Blast Radius)" 限制在非常小的使用者群體內 (這常與 Feature Toggles / Feature Flags 搭配使用)，在持續交付 (CD) 中屬於進階的安全營運策略。

#### **3. During the operational phase of a software system, a massive Distributed Denial of Service (DDoS) attack hits the application's main login endpoint. The Incident Response (IR) team is activated. According to standard IR frameworks (like NIST SP 800-61), after "Detecting and Analyzing" the attack, what is the immediate NEXT critical phase the team must execute to limit the damage?**
**(在皇城歌舞昇平的營運期。突然！警鐘狂鳴！鋪天蓋地的十萬蠻族大軍 (DDoS Attack)，像瘋了一樣在死命衝撞皇宮的『登入大正門 (main login endpoint)』！皇城的『神聖救火錦衣衛 (Incident Response team)』立刻被喚醒。這群錦衣衛站上城牆，用望遠鏡看清楚了敵人的長相，並確認了這不是演習，而是真正的攻擊 (Detecting and Analyzing)！請問！在看清楚敵人是誰之後，根據《帝國防衛聖典 (NIST SP 800-61)》，錦衣衛們【下一秒鐘】最該執行的救命第一動作是什麼？)**
A. Post-Incident Activity (Lessons Learned) (事後檢討大會在寫作文。現在城門都快被撞破了，敵人的刀已經架在脖子上了，你叫大家坐下來開會做投影片檢討為什麼城門這麼脆弱？這叫找死！)
B. Preparation (備戰演練。這是平常還沒打仗的時候在操場上練兵、買盾牌的時期。現在敵人都衝到門口了，早就過了 Preparation 的階段了)
C. Eradication and Recovery (根除與復原是把已經進城的蠻族全部殺光，把被燒掉的房子重新蓋回來。但在你做這件事之前，你得先保證這門不會直接被擠爆！如果大門不關，你殺十個蠻族，外面又湧進來一萬個，你永遠殺不完)
D. Containment (這就是救火的千古不變唯一真理：【『止血保命之終極大封鎖：圍堵結界 (Containment)！』】。當你發現敵人的大軍正在衝擊大門時，你第一件要做的事，就是啟動大門外的護城河，拉起拒馬，或者請出那一尊名為『流量黑洞防護罩 (CDN/DDoS Mitigation Service)』的神器，【先把源源不絕的攻擊火力給強制隔離、攔截在城牆之外 (Limit the damage)！】。止血永遠優先於治病！在沒有把水管破洞堵住之前，你擦地板是沒有任何意義的。圍堵 (Containment) 的唯一目標就是：停止損失擴大，保護剩下的系統不被牽連，為後續的殺毒跟重建爭取時間！)

*   **正確答案 / Correct Answer：D**
*   **[解析邏輯]**
    *   **為何 D 是最佳選擇：** 這是標準的 **事件回應生命週期 (Incident Response Lifecycle, NIST SP 800-61)** 的鐵律順序。
    *   **NIST IR 生命週期四階段：**
        1.  **Preparation (準備)：** 建立團隊、撰寫 Playbook、建置監控系統。
        2.  **Detection and Analysis (偵測與分析)：** 發現異常、確認是真實攻擊、評估影響範圍 (題幹說這步剛剛做完)。
        3.  **Containment, Eradication, and Recovery (圍堵、根除與復原)：**
            *   **Containment (圍堵) 永遠是第一優先。** 目的：防止災害擴大 (Stop the bleeding)。例如：將受感染的機器斷網 (隔離 Network Isolation)、在 WAF 或邊界路由器上封鎖攻擊來源的 IP，或啟用 DDoS 緩解服務。
            *   **Eradication (根除)：** 拔除惡意程式、刪除駭客留下的後門、修補被利用的漏洞。
            *   **Recovery (復原)：** 將系統從備份還原、小心翼翼地重新上線並持續監控。
        4.  **Post-Incident Activity (事後活動/經驗學習)：** 寫報告、檢討哪裡做得不好、更新 Playbook 防範下次發生。

#### **4. A cloud architecture uses auto-scaling groups to match server capacity with user demand. The security team insists on building virtual machine images (AMIs) that contain the OS, application code, and all security hardening configurations fully baked in. When a new server spins up, it boots from this image and *never* receives updates or configuration changes while running; if a patch is needed, a completely new image is built to replace the old running instances. What operational security concept does this represent?**
**(在一座蓋在天雲之上的超級神殿裡。如果來拜拜的香客變多，神殿會「自動憑空變出 (auto-scaling)」幾十座接待小廟。神殿的安防總教頭立下了一條鐵律：『每一座接待小廟，都必須是用【天上火爐燒製好的「一體成型純鋼鑄劍模具 (baked-in AMIs)」】直接倒模做出來的！這模具裡已經刻好了所有的防禦符咒跟武功秘笈。最重要的一點是：只要這座小廟一落地開始接待香客。這座廟就成為了【絕對不准敲打、不准修補、連換一顆螺絲釘都是死罪的「不朽堅冰」 (never receives updates while running)】！如果今天天上頒布了新的防禦符咒該怎麼辦？安防總教頭說：『那就直接用新符咒重新燒一個新模具。然後把舊模具做出來的小廟全部一槌子砸碎 (replace old instances)！完全不修，直接換新！』請問！這種「寧可砸爛換新，也絕對不准在服役期間塗塗抹抹」的終極潔癖營運防禦大陣法，尊號為何？)**
A. Immutable Infrastructure (這就是名震四方、讓所有駭客絕望到想跳樓的：【『金剛不壞之無常生滅大陣：不可變基礎架構 (Immutable Infrastructure)！』】。在過去的觀念裡，伺服器生病了 (有漏洞)，管理員要上去打針吃藥 (Patching)。但這給了駭客機會：駭客可以潛入伺服器偷偷改配置，植入後門，而且沒人會發現！但在【不可變 (Immutable)】的法則下。每一台運行中的伺服器，就如同燒好的瓷器，出窯後永遠定型 (Read-Only)。如果你要更新版本或打補丁，你必須去修改 CI/CD 裡的藍圖，重新烘焙出一個全新版本的「黃金鏡像 (Golden Image / AMI)」，然後把舊的伺服器直接賜死銷毀 (Terminated)，讓新的伺服器誕生取代它！這種陣法直接從根源消滅了「組態飄移 (Configuration Drift)」的災難，而且就算駭客真的摸進了系統，他也活不過下一次的 Auto-scaling 重生大洗牌 (短命伺服器 Ephemeral)！)
B. Mutable Architecture (可變架構就是那種活了五年，上面縫縫補補打了幾百個膏藥的祖父級伺服器，這是 Immutable 的完全相反詞)
C. Legacy Server Management (這也是上一代老觀念的代名詞，通常代表著手工管理、一台機器寵愛一輩子的 Pet Server 模式)
D. Defense in Depth (縱深防禦是在城牆外挖水溝、牆上擺大炮、裡面藏地雷的多層次防禦。雖然 Immutable 也是一種防禦手段，但題幹描述的「不修補只替換」是專指 Immutable 這一個特定戰術名詞)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** 這是對 **「不可變基礎架構 (Immutable Infrastructure)」** 的完美與標準定義。
    *   **傳統模式 (Mutable / Pets)：** 伺服器壽命很長。當需要更新軟體或 OS Patch 時，管理員會 SSH 進去 (或用 Ansible) 執行 `apt-get update`。這導致長時間運作後，每台機器的狀態可能會變得不一致 (Snowflake servers)。
    *   **不可變模式 (Immutable / Cattle)：** 伺服器被視為免洗筷 (disposable)。軟體與環境的所有設定，在 **"Build (建置鏡像)"** 階段就已經「完全烤熟 (Baked-in)」，形成 Golden Image (黃金鏡像，如 AWS AMI 或 Docker Container Image)。
    *   **運作方式與安全優勢：**
        *   在運作期間 (Runtime)，嚴格禁止任何變更 (甚至可以將檔案系統掛載為唯讀 Read-Only)。
        *   遇到漏洞需要修補？改 Code -> 觸發 Pipeline 產出新的 Image -> 透過 Auto-scaling 或 Kubernetes 滾動更新 (Rolling update)，把舊機器砍掉，新機器重生。
        *   這最大程度保證了環境的一致性，並讓潛伏的惡意程式 (Persistence) 成為泡影，因為伺服器隨時會被重置。

#### **5. In the context of secure operations, what is the primary security objective of implementing "Continuous Monitoring" (Continuous Defend / Continuous Security Monitoring)?**
**(在大內皇宮平安無事，老百姓安居樂業的營運時期。大皇帝在皇宮的每一根柱子上，都綁了一隻名為『永不闔眼之千眼守望大鵬鳥 (Continuous Monitoring)』！這大鵬鳥不吃不睡，一輩子就死死盯著皇宮裡的每一扇門、每一條水管、甚至連太監上廁所沖幾次水它都紀錄下來！請問！皇帝花那麼多錢，在這個「看起來根本沒人打來」的和平時期，放這幾萬隻大鵬鳥在天上二十四小時不間斷盤旋，它最神聖的【安全戰略終極目標 (primary security objective)】，究竟在圖什麼？)**
A. To automatically fix bugs in the source code as soon as developers type them. (大鵬鳥是掛在【正在線上營運服務】的皇宮裡，而不是掛在【工匠打造藍圖】的兵工廠桌上。監控營運系統的大鵬鳥不管寫程式抓蟲的事，那是 SAST 白骨透視機的責任)
B. To provide historical data exclusively for annual compliance audits. (雖然每年一度的天下大盤問 (Compliance Audit) 確實會來跟皇帝要大鵬鳥記錄的歷史畫面。但如果大鵬鳥『只是』為了應付一年一次的考試而寫流水帳，那這種死了才來收屍的防禦根本連個屁都不如。大鵬鳥最大的價值在於「當下」！)
C. To gain real-time visibility into the security posture, performance, and potential anomalies of the production system, enabling rapid detection and response to active threats or degraded states. (這就是『千眼大鵬鳥』之所以為神器的唯一真理：【『點亮黑夜之全知全能的即時洞察力 (gain real-time visibility) 與光速雷霆反擊 (rapid detection and response)！』】。在廣袤的雲端國度裡，最恐怖的不是敵人有多強大，最恐怖的是：【你的金庫已經被搬空了三個月，你卻完全不知道！】。大鵬鳥在天上盤旋，為的就是當哪怕有一個刺客的指甲刮到了後山的圍牆 (potential anomalies)，大鵬鳥能在【一秒鐘內】發出震天警報！讓底下的錦衣衛能用最快的速度衝上去把刺客砍死，防止小傷口變成亡國滅種的大災難。這是在營運階段維持活命的最後一道呼吸線！)
D. To ensure the software license has not expired. (盯著合約版權看有沒有到期，這是負責算錢的老太監該做的事。花大錢買安防大鵬鳥去盯那幾張紙，這是大砲打蚊子，完全偏離了資安營運的核心防禦主軸)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「持續監控 (Continuous Monitoring, CM)」** 在營運階段 (Operations Phase) 的核心價值，就是提供**「即時的可視性 (Visibility)」與「異常偵測能力」**。
    *   **SSDLC 的盲點：** 無論在開發階段你做了多少 SAST、DAST、Pen Testing。軟體上線營運後，永遠可能遭遇前所未見的 Zero-Day 攻擊，或是內部員工的惡意操作 (Insider Threat)。
    *   **CM 的作用：** 透過收集應用程式日誌 (Application Logs)、伺服器指標 (Metrics)、網路流量 (Network Traffic) 等遙測數據 (Telemetry)，並集中到 SIEM 等平台上分析。
    *   **最終目標：** 縮短 **「威脅潛伏時間 (Dwell Time)」** (從駭客入侵到被發現的時間)。讓 Incident Response 團隊能夠 "Detect and Respond" (偵測並回應) 進行中的攻擊，而不是幾個月後才在新聞上看到自家的資料被外洩。
