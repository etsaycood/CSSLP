# 第二套全真模擬試題 (Exam 2) - 答案與詳解本
## 領域 7：安全的軟體部署、營運與維護 (Secure Software Deployment, Operations, Maintenance) (13題) - Part 2 (Q10-Q13)

---

#### **10. A seasoned incident responder (IR) is drafting the company's official Incident Response Plan. According to standard frameworks like NIST SP 800-61, immediately after the team successfully "Contains" an active ransomware infection (e.g., by unplugging the infected servers from the network), what is the very next formal phase of the incident response lifecycle?**
**(一名滿手鮮血、身經百戰的資深『阿爾法事件大急救響應總指揮官 (Incident Responder, IR)』！正坐在桌前，奮筆疾書撰寫著公司神聖不可侵犯的『最高防衛事故應變法典白皮書 (Incident Response Plan)』。按照美國政府 NIST SP 800-61 那如鐵律般的防衛大軍標準作戰八股指導書。當今晚機房突然爆發了如狂犬病般四處撕咬蔓延的恐怖勒索軟體病毒大爆雷！而這群英雄消防員終於在火線最前線：滿頭大汗地死命『撲滅災情、建立起那道名為實體隔離、拔掉這群發病主機網卡與網路插頭來止血防止繼續亂竄傳染的斷尾高牆 (也就是完成了那至關重要神聖名詞："Containment / 遏止圍堵")』任務後！在這套軍事大軍的SOP作戰藍圖指揮下，這幫滿手泥濘兄弟們【接下來要硬著頭皮無縫點頭去幹的第一件緊接而來的正式血腥戰鬥任務流程 (formal phase)】叫什麼名字？)**
A. Preparation (打回原形的大撤退洗牌準備大陣 (Preparation))
B. Detection and Analysis (摸黑打手電筒的偵測與化驗敵方大搜查 (Detection and Analysis))
C. Eradication (Removing the malware, deleting backdoors, and closing the vulnerabilities root cause). (這就是斬草除根、大刀開鍘將那些藏在暗處的木馬、後門卵苞跟病根全部給殘酷刨除殲滅的【趕盡殺絕根除大屠殺 (Eradication)】！)
D. Post-Incident Activity (Lessons Learned) (大夥圍個圈把酒言歡回顧感傷落淚的戰後兵推檢討大會 (Post-Incident Activity))

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「事件應變生命週期 (Incident Response Lifecycle)」** 是維運與資安的必考死背題。根據美國官方標準 NIST SP 800-61，這套打仗的標準步驟被死死定格為四個大階段（加上內部的迴圈）：
        1.  **Preparation (準備)：** (平安無事時) 買好滅火器，演練好流程。
        2.  **Detection & Analysis (偵測與分析)：** 警報響了，確認這不是演習，真的中毒了！
        3.  **Containment, Eradication, & Recovery (遏止、根除與復原)：** 這是最血腥的一環，且順序絕對不能錯！
            *   *(1) Containment (遏止)：* 病人血管割破大出血，現在不是幫他縫合破洞的時候，【第一步是拿止血帶趕快先死死綁住大動脈不要讓他失血死亡流乾】！(也就是題目說的拔網路線、封鎖防毒牆、禁止病毒擴散)。
            *   ***(2) Eradication (根除)：*** 血止住了，駭客進不來了。這時資安專家進去開刀，【把肚子裡的子彈跟長頸鹿木馬後門、連同開門漏風的那扇破窗漏洞，全部連根拔起一刀砍死清掉】！(此乃本題正解，也就是拔線後的下一步開鍘動作)。
            *   *(3) Recovery (復原)：* 把乾淨備份重灌回去，重新接上網路對外微笑重新開幕做生意。
        4.  **Post-Incident Activity (事後檢討)：** 寫報告，被長官罵，確保下次不會再犯。

#### **11. A global SaaS provider guarantees its enterprise customers a Service Level Agreement (SLA) of "Four Nines" (99.99%) uptime per year. During operations, the central database server experiences a catastrophic hardware motherboard failure. The system automatically switches over to a standby database within 30 seconds without dropping any active user connections. This rapid recovery ensures the company meets the metric defining the maximum acceptable amount of time the system can be offline after a disaster. What is the formal term for this specific time-based metric?**
**(一家誇下海口、傲視群雄發誓『這輩子我們家大水壩一年裡絕對保證能給出高達「四個九」純金級別 (99.99%) 不打烊死不當機神保險 (SLA Service Level Agreement)』的全球雲端跨國大老爺公司！某天半夜，他們家主堡的心臟地帶 (主資料庫伺服大娘) 突然慘叫一聲，它身上的金屬主機板就這樣原地燒毀解體大崩壞。沒想到！這座偉大公司的機房就像變魔術一樣，連眼睛都沒眨一下！在這場災難爆發後的『短短 30 秒內』。居然就在全體正連線結帳刷卡消費的大客官們都還沒回神、網路連線一滴也沒斷掉的零感知境界下！行雲流水般奇蹟復活、全自動完成無縫切換將權力王冠雙手遞交戴上給了旁邊平時備用的『替身皇太后備援伺服器大娘』頭上！而這家公司之所以要瘋狂投資這套這般神速接管復活的高科技，完全是為了要向死神跟客戶拍胸脯、去嚴密死守住並達成那張法庭合約上所規定之：『萬一地球毀滅我當機斷線了，這家公司所能被恩准容忍【最長極限容許斷電爬不起來死亡休克時間】的沙漏限時碼表』！敢問這支限制死亡復原時間的業界秒殺碼表代名詞，是被冠上哪個神聖的大名？)**
A. Recovery Point Objective (RPO) (這是測量失憶症、死前噴了流失破財了多少最近那半小時記憶沒存檔到的歷史資料流失損失點碼表 Recovery Point Objective)
B. Mean Time to Detect (MTTD) (這是家裡警鈴從破洞潛入到被警衛發現究竟瞎死了拖拉了幾天幾夜的抓賊碼表 Mean Time to Detect)
C. Recovery Time Objective (RTO) (這就是逼迫大老爺非得在『這沙漏滴完前必須從太平間爬起來從墳墓無縫復活回來掛保證』的【死線復活拯救歸隊時間戰標 (Recovery Time Objective, RTO)】！)
D. Maximum Tolerable Downtime (MTD) (這是真的一死不能復生、整間公司宣告破產倒閉的終極停機死期大魔王 Maximum Tolerable Downtime)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** 這是災難復原 (Disaster Recovery) 與業務連貫計畫 (BCP) 的三本柱黃金指標大考題：RTO, RPO, MTD。
    *   **RTO (復原時間目標 / Recovery Time Objective)：** 這是跟客戶保證的「從機房爆炸那一秒開始算，我承諾我在【多少分鐘/小時之內】，一定會把備用系統打開、復活、重新提供服務」。這是一個「時間倒數碼表」。(如同題目的 30 秒內接手完成，這是一個極度傲人完美的 RTO 成績單)。它是用來對抗 MTD 的。
    *   **MTD (最大可容忍停機時間 / D 的選項)：** 這是老闆心裡的最後死線：「如果系統死掉超過這條線 (例如 3 天)，公司就直接宣佈破產」。所以： **RTO 絕對必須被設計且要求要 <小於< MTD**。
    *   **RPO (復原點目標 / A 的選項)：** 這個跟復原時間沒關係，這是看你「你最近一次備份資料的儲存點離大當機那瞬間有多久」。如果 RPO 是 1 小時，代表大當機發生時，你這一個小時內所有的刷卡紀錄就永久「回溯消失不見了 (Data Loss)」。

#### **12. The DevOps team implements a rigid release pipeline constraint: any developer attempting to deploy a new version of the microservices suite into the `Production` Kubernetes cluster MUST have their Pull Request digitally signed by at least one Senior Architect and one QA Lead. If these specific cryptographic signatures are missing, the deployment pipeline structurally refuses to execute. What deployment security concept is being enforced here?**
**(那支執法如山、掌握著核彈發射按鈕的雲端神兵大營 DevOps 守衛小隊，在他們家那條發船起航的偉大火箭發射傳輸大管線流水線上。以近乎獨裁般的姿態，焊死定調了一道冷血冰冷的斷魂截殺鐵柵欄：『天底之下任何一個不知死活的開發寫扣小猴工程師！如果今天想大搖大擺把他修改完的這包新一代微服務生化炸彈，點燃推進到我們偉大聖殿「火線 Kubernetes 大叢集生態圈」裡引爆上線服役！這傢伙手上的那份「拜託請放行通關奏章文件 (Pull Request/PR)」上頭！【絕對且毫無商量餘地地、必須強硬同時烙印壓下、掛載著一名高高在上的白鬍子資深架構大前輩 (Senior Architect)、以及一名冷血品保 QA 督軍處決長 (QA Lead)】這兩人『用私鑰刻印出來、無可假冒的神聖密碼學數位簽章 (digitally signed)』授權保證印章！但凡缺少這其中哪怕半顆印章背書！這條發射跑道大管線就會無情從底層硬體結構上直接上鎖熄火、全面無條件拒載發射並將你給碎屍萬段！』。請問，這等近乎獨裁鐵腕的雲端防呆截殺上線管制手段，是動用了哪項強勢兵棋推演的部署神殿戒律？)**
A. Blue/Green Deployment (蓋兩間房子的遊戲)
B. Release Gating / Deployment Approvals (這就是猶如軍事管制區般、不認人只認章不給過放行的【部署大門重兵閘道深鎖令 (Release Gating) / 絕對授權查驗部署批准令 (Deployment Approvals)】！)
C. Code Obfuscation (把程式碼弄得很亂看不懂的隱身術大門)
D. Chaos Engineering (以把東西搗爛為樂趣的混沌大猩猩)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** **「發布閘門 (Release Gating) / 部署批准控制 (Deployment Approvals)」** 是 CI/CD 流程中保障安全與合規性 (Compliance) 最重型的一道煞車。自動流水線 (Pipeline) 雖然講求發布速度，但在上線進入最神聖的 Production (真實營運金庫) 前，絕對不能只靠機器自動。在這條生死紅線上，架構師會安插一個名為 Gate (閘門 / Checkpoint) 的魔法結界。這個結界會用程式邏輯死死卡住流水線。
    *   這直接對應了前面提到的重要概念 **"職責分離 (SoD / Separation of Duties)"**。一個工程師不准自己寫又自己放行。Gate 的機制可能是：掃描機要全數過關，並且在 GitHub/GitLab 上，要有特定權限階級的主管按下 `Approve` (這些按鈕在底層被綁定了這些人的數位簽章 GPG/SSH Key 以防偽造)。只有集滿這些條件章，Gate 才會打開那最後一層通網營運火線的防火牆放程式上陣。

#### **13. To proactively train the operations team for inevitable, unpredictable production failures, the engineering leadership intentionally unleashes a specialized software bot called "Chaos Monkey" into the live production cloud environment. This bot randomly terminates virtual machines, severs network connections, and crashes database nodes during peak business hours to see if the auto-scaling and failover architectures actually work as designed without human intervention. What advanced operational resilience methodology is this?**
**(為了讓旗下這群平時安逸在冷氣房裡、遇到大地震就會手足無措的救難維運消防大軍，能夠時刻處在精神緊繃、隨時準備迎接那些如鬼魅般『註定不可避免、且絕對無法預知會從哪冒出來的機房核爆末日級全體大死亡與當機災變連環炮 (unpredictable production failures)』！這群極端變態的高端工程祭司長老們，做出了一個瘋狂的創舉：他們居然趁著『自家大賣場人潮最洶湧、全世界都在刷卡狂賺錢的熱鬧客流正巔峰尖峰時段大白天下 (peak business hours)』！親手打開牢籠封印，把一頭名喚作『渾沌滅世破壞大猩猩 (Chaos Monkey)』的這等專門四處搞破壞撕裂機房的黑暗自動化電腦病毒魔鬼金剛機器人兵團軟體，給直接丟進、釋放到他們家那無比神聖的營運火線上線雲端結界裡撒野！這頭瘋狂的猴子會在雲端裡胡亂隨機挑選：這秒一鎚子把正要結帳的雲端虛擬收銀機大腦給活生生爆頭扯斷拔線死當！下一秒拿出大剪刀喀擦絞斷了網路大動脈聯絡隧道！轉個身又把那存放黃金的資料庫主神經元給當場踢碎當機！祭司們只是老神在在地一旁喝咖啡，死盯著這滿目瘡痍看：看那些當初他們花上千萬買來的神聖『自動復活大軍 (auto-scaling) 與免死金牌接管無縫換命復活盾牌系統 (failover architectures)』，到底能不能在完全沒有人類敢介入的超級絕境下，自己化險為夷扛下擋住這頭猴子猛攻、不讓外面大買家客人有絲毫斷網倒塌感覺死當？請問！這等走火入魔、自毀式演練兵推的不倒翁極限求生不死術訓練營，那名震仙魔兩界的響噹噹霸氣名號大旗是？)**
A. Penetration Testing (拿刀子刺軟體圖解鎖的滲透小測試)
B. Disaster Recovery Tabletop Exercise (只是坐在高級會議長桌上，喝茶動口不出手用紙上推演防空演練的紙老虎演習 (Tabletop Exercise))
C. Chaos Engineering (Resilience Testing) (這就是以『絕對毀滅才能驗證神之復活盾牌』狂信！傲視宇宙的最高境界：【混沌工程打擊 / 原地放火搗爛抗擊打復活極境毀滅大測試 (Chaos Engineering / Resilience Testing)】！)
D. Regression Testing (怕修好的陳年老病復發的回歸安檢)

*   **正確答案 / Correct Answer：C**
*   **[解析邏輯]**
    *   **為何 C 是最佳選擇：** **「混沌工程 (Chaos Engineering)」** 是由 Netflix 這種宇宙級雲端大廠 (AWS 忠實重度使用者) 首先發明並推向世界的極限維運哲學。在幾千台微服務伺服器組成的雲端大海裡，工程師不可能手動預知哪一台機器的網路卡今天會燒壞。\n    *   傳統的備援系統 (Failover) 平常不啟用，一爆發災難時往往因為年久失修導致連備援系統也跟著一起掛掉死亡。為了解決這問題，混沌工程的哲學是：「既然災難一定會發生，那我們就**自己製造災難**」。工程師寫了一支叫 "Chaos Monkey (混亂猴子)" 的程式。這隻猴子會在大家都在努力結帳的上班時間，隨機把重要伺服器的電源關掉。在這種神經病般的摧殘考驗下，如果這個網站竟然連抖都沒抖一下，還能順利幫幾百萬人結帳看串流電影。那就代表開發者寫的那套「負載平衡、自動備援、雲端漂移」的自我治療防護網設計，已經達到了刀槍不入的神級抗打擊能力 (Resilience)。這不是在測試找 Bug，這是在測試跟鍛鍊「企業不死的韌性」。
