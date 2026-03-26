# 第四套全真模擬試題 (Exam 4) - 答案與詳解本
## 領域 8：安全的軟體供應鏈 (Secure Software Supply Chain) (12題) - Part 2 (Q5-Q8)

---

#### **5. In the context of securing a CI/CD pipeline against supply chain threats (like the SolarWinds attack), a security engineer implements a policy requiring that any code merged into the `main` branch must have been reviewed and approved by *at least one other developer* who did not author the code. The build machine will physically reject the code if this condition is not met in the Git repository. What security principle is being enforced here?**
**(在皇城最大的『神兵鍛造流水線 (CI/CD pipeline)』中。大太監為防有內鬼偷偷在即將上貢給皇帝的神劍上刻下毒咒。他頒佈了一道死命令：打從今天起，不管是哪位天才工匠打出來的好劍，要送進這最後一條名為 `main` 分支的火爐前，【絕對、極限不可商量地，必須有另一個不是打這把劍的老師傅，親眼看過這把劍，並且在上面蓋章大喊「此劍無毒 (reviewed and approved by at least one other developer)」！】。如果有任何一個工匠敢把沒有蓋過第二人私章的黑劍偷偷塞進爐子，這口大火爐的機關將會直接鎖死，把這把黑劍原封不動地吐出來 (physically reject the code)！請問，在這套防範內鬼投毒的最高級別兵法教條中，大太監祭出了哪一把傳說中的「權力制衡大屠龍刀 (security principle)」？)**
A. Separation of Duties (Two-Person Rule / Peer Review) (這就是名垂千古、不管在哪個朝代都能防堵內鬼與失智誤判的：【『雙人成行之權限切割大法：職責分離 (Separation of Duties / SoD) / 與同行盲測大審查 (Two-Person Rule / Peer Review)！』】。在這條鐵律之下，沒有任何一個人 (即便是首席工匠/Tech Lead) 擁有「單憑一己之力，就能把程式碼推送進火爐 (Merge to Main)」的至高無上神權！只要權力集中，這座皇城就可能因為這一個人被惡魔附身 (Account Compromise) 或是一時腦霧 (Accidental Error)，而直接被一枚藏著毒咒的炸彈 (Malicious code like SolarWinds backdoors) 給炸毀！大太監透過 Git 儲存庫的分支防護規則 (Branch Protection Rules in GitHub/GitLab)，強制要求 `Require approvals` 必須大於等於 1。這種「你寫 Code，我來看 Code」的強制隔離，正是防止內部投毒、阻斷惡意程式碼污染軟體供應鏈 (Supply Chain) 的最後且最強大的防波堤！這是一套將人類社會制衡法則與自動化 CI/CD 器官完美融合的無敵陣法！)
B. Data Minimization (資料最小化是身上不要帶太多錢以免被搶。這跟工匠打鐵需要幾個人看藍圖完全是兩個世界的概念)
C. Fuzzing (Fuzzing 是叫個瞎子對客棧狂丟石頭看門會不會破。現在我們是在工廠內部檢查藍圖有沒有被下毒，而且是一個正常人類在審核另一個正常人類寫的藍圖。這不叫 Fuzzing)
D. Obfuscation (代碼混淆是打仗前把盔甲塗花讓敵人看不出自己的臉長什麼樣，雖然可以增加逆向工程的難度。但在這題的脈絡中，它是要防止「內鬼或帳號被盜的開發者」偷偷把毒藥塞進去，並不是為了防「敵人偷看源碼」)

*   **正確答案 / Correct Answer：A**
*   **[解析邏輯]**
    *   **為何 A 是最佳選擇：** **「職責分離 (Separation of Duties, SoD)」** (或是其衍生的 **雙人防護規則 Two-Person Rule / Peer Review**) 是防範內部威脅 (Insider Threat) 與供應鏈攻擊中最關鍵的流程控制。
    *   **CI/CD 的供應鏈風險：** 攻擊者 (如國家級 APT 組織) 若成功竊取了一名開發者的 GitHub 帳號密碼與 Session Token (Account Takeover)。攻擊者可以直接 Commit 一段惡意的後門程式碼，如果沒有攔截，CI 伺服器會自動把後門打包成正式版 App 發佈給百萬用戶 (SolarWinds SUNBURST 攻擊的變形)。
    *   **Branch Protection (分支保護) 的防禦力：** 現代的 VCS (Version Control Systems，如 Git) 允許設定 `Branch Protection Rules`。
        *   開發者必須透過 Pull Request (PR) 提交變更。
        *   這規則強制要求 `Required Approvals >= 1` (或 2)。
        *   **關鍵機制：** 提交 PR 的作者 (`Author`) **被禁止** 核准自己的 PR。
        *   這意味著，駭客現在必須 **同時攻破兩名** 不同開發者的帳號，才能成功將惡意程式碼合併到 `main` 分支。這在實務上呈指數級增加了攻擊難度，這完美的體現了 SoD 互相制衡的精神。

#### **6. A software vendor utilizes a component licensed under the GNU General Public License (GPL). According to the strict "copyleft" nature of this specific open-source license, if the vendor dynamically links or incorporates this GPL component into their own proprietary, closed-source application and distributes it to the public, what is the vendor legally obligated to do?**
**(一家想發大財的黑心打鐵鋪，偷偷從城外的『共產老和尚大草原 (Open Source)』牽走了一匹名為【『加倍奉還至尊神馬 (GPL licensed component)』】的汗血寶馬！這打鐵鋪老闆原本打著如意算盤：他把這匹神馬，跟他自家祖傳的一台破爛生鏽的『極速送貨三輪車 (proprietary, closed-source application)』綁在一起 (dynamically links or incorporates)。然後老闆跑到大街上，把這台『綁著神馬的三輪車』宣步是自己獨創的神兵，並用天價賣給了幾萬個無辜 老百姓 (distributes it to the public)！老闆以為他賺翻了。但是！這匹神馬身上，可是刻著由共產老和尚下達的【『天下無狗、萬物皆空之絕對感染大毒咒 (strict copyleft nature)』】！這道毒咒在踏出大草原的那一刻就已生效！請問，如今老闆把這神馬牽出來炫耀並賣錢，這道毒咒將會逼迫這黑心老闆，必須把什麼東西也給【一併免費送入大草原】才能贖罪 (legally obligated to do)？)**
A. The vendor only needs to pay a small royalty fee to the original GPL author. (大草原上的老和尚是不收你這三個臭銅板的版權費的！他們要的不是錢，他們要的是這世上再也沒有能藏私的武功秘笈！這跟一般要付錢的商用軟體完全不同，所以只付錢是解不開這道毒咒的！)
B. The vendor must release the entire source code of their own proprietary application under the same GPL license (or a compatible open-source license). (這就是讓全天下所有的黑心打鐵鋪老闆嚇到尿失禁、連夜把車砍掉重練的：【『連坐法之絕對財產充公大天怒 (Copyleft Infection / GPL Infection)！』】。GPL 是一種傳染力極強的「病毒式開源授權條款 (Copyleft/Viral License)」。它的核心教條是：『你既然用了我們全村老百姓無私奉獻打出來的神兵。那你這輛跟神兵綁在一起的破車，也就被神兵的仙氣給感染了！所以，你這家客棧【不准再把藍圖藏在祖傳保險箱裡】！你必須、且極限強制地，把這台你自以為是獨門絕活的三輪車的『全部原始設計藍圖 (release entire source code)』，用跟我們一模一樣的『天下老百姓皆可免費印製』的條件 (under same GPL license) 給無私公開』！如果老闆拒絕交出自己三輪車的藍圖？那共產老和尚會帶著全天下的衙役 (著作權法)，把這家打鐵鋪告到當場破產、連內褲都不剩！這是企業在使用開源組件時最致命的【授權合規大死穴 (Compliance/Legal Risk)】！)
C. The vendor must ensure the software has no zero-day vulnerabilities. (老百姓只要求你把藍圖公開，至於你那破爛三輪車有沒有零時差漏洞，他們才不管，因為就算有漏洞，反正藍圖大家都看得到，大家會自己想辦法修。GPL 從來不保證軟體無毒無蟲)
D. The vendor can keep their source code closed, provided they mention the GPL author in the "About" menu. (如果只是在感謝名單裡面寫上一句「謝謝王大明」，就可以繼續把藍圖鎖在保險箱裡賺大錢，那這匹馬就不叫傳染性極強的 GPL 汗血寶馬了，那叫 MIT 或是 Apache 這種好好先生授權。這題講的是最兇殘的 GPL，它絕對不是只憑一句謝謝就能打發的)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是對 **GNU General Public License (GPL)** 授權條款最核心的 **"Copyleft" (著佐權 / 傳染性授權)** 特性的正確解讀。
    *   **開源軟體授權的兩大陣營：**
        1.  **Permissive Licenses (寬鬆授權，如 MIT, Apache, BSD)：** 你可以用這段程式碼，你甚至可以把它包進你賣錢的商業閉源軟體裡，只要你在 `LICENSE.txt` 裡宣告一句「我用了這套軟體，作者不負任何責任」即可。你【不需要】公開你的商業軟體源碼。
        2.  **Copyleft/Viral Licenses (強傳染性授權，如 GPL v2/v3, AGPL)：** 這是企業法務部的夢魘。只要你使用了 GPL 的元件 (包含靜態或動態連結編譯、甚至包含在修改後發佈)，你的整個衍生作品 (Derivative Work) 就**必須同樣基於 GPL 條款開源釋出 (Must release entire source code under same GPL)**。
    *   **供應鏈合規風險 (Supply Chain Compliance Risk)：** 如果企業的開發者為了貪圖方便，偷偷拿了一段 GitHub 上的 GPL 程式碼並塞進公司要賣錢的金融交易系統中，一旦被發現 (透過 SCA 工具或被告)，公司可能面臨天價索賠，並被法院強制要求將這套價值數百萬的金融系統原始碼免費公開給競爭對手看。

#### **7. An organization discovers that a critical open-source library used throughout their microservices architecture has just been assigned a CVE for a Remote Code Execution (RCE) vulnerability. However, the original maintainer abandoned the project two years ago, and no official patch will be released. This is a classic supply chain risk. What is the MOST viable long-term remediation strategy for the organization?**
**(皇宮的幾百座大殿裡，全都裝上一種名叫『百年不倒無敵大力木樑 (critical open-source library)』的建材。結果！！天降快報！國家地震局突然宣告這塊木樑裡面住了一萬隻白蟻，這白蟻會在半夜把木頭吃光，讓大殿當場崩塌 (CVE for RCE vulnerability)！皇上嚇得魂飛魄散，派大將軍帶著黃金去請發明這木樑的老工匠立刻打幾根沒蟲的木樑過來。結果大將車到了老工匠家門口，發現這老工匠在兩年前早就死在路邊了 (maintainer abandoned project two years ago, no official patch)！這下皇上絕望了，全皇宮幾百座大殿即將毀滅。請問，為了解決這個沒有人會來救你、只能等死的死亡倒數恐懼 (classic supply chain risk)。在長治久安的國運大計中，大將軍必須採取什麼樣【這輩子再也不怕別人死掉的終極自救大絕招 (MOST viable long-term remediation strategy)】？)**
A. Implement a temporary WAF rule and continue using the vulnerable library indefinitely. (在大門口畫一道符咒騙白蟻 (WAF)，然後繼續抱著這根隨時會斷掉的神經病木樑住個五百年？這叫慢性自殺。WAF 雖然能擋住外面飛來的幾隻新白蟻，但擋不住裡面原本就在啃的恐怖死法。而且如果這木樑以後又長出另一種 WAF 擋不住的飛象蟲，你這大殿還是照樣死機)
B. Fork the repository, apply a custom fix internally (if possible), and plan to migrate to a different, actively maintained library that provides similar functionality. (這就是名震四海、專治「孤兒元件依賴症」的：【『壯士斷腕自救雙刃陣：先分家自製假肢 (Fork and apply custom fix)！再連根拔起大換血 (migrate to a different library)！』】。當原作者死掉 (開源專案被遺棄 / Abandonware)，你想要活命，就不能再靠別人。第一步：既然大殿馬上要塌了，大將軍必須立刻把這張木頭藍圖搶回來【自己蓋一間自家專屬的小打鐵鋪 (Fork repository)】，然後派自家兵工廠的工匠，親手抓出白蟻然後上一打滅蟲膠 (apply custom fix internally)，暫時先把這殿頂住，不要讓他今天晚上塌下來！第二步：但這木樑的設計早就落後百年。為了不再每天擔心受怕，大將軍必須頒佈五年計畫，把全皇宮的破木頭，一根一根地拆下來，【全部換成現在市面上活得最好、每年還有一萬口工匠在保固修理的『最新無敵合金大鋼鐵樑 (migrate to actively maintained library)』】！這才是唯一能長命百歲、不受死人牽連的千秋大業！)
C. Threaten to sue the open-source author for abandoning the project. (老爺，人家兩年前就因為沒錢去天國了。這開源軟體免錢給你用了三十年，條款裡寫明了「AS-IS 概不負責」，你去法院告鬼魂？這是在浪費國家公帑，完全無助於解決大殿要塌的物理崩潰危機)
D. Ignore the vulnerability if the organization uses a cloud-native Kubernetes architecture. (雲端神仙也是要踩在這爛木頭上面住大樓的！如果駭客讓這白蟻發動攻擊，K8s 會跟著被一劍穿心 (RCE)。你不能因為自己住在雲端，就以為連根拔起的毒藥毒不到你)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是面對開源軟體供應鏈中 **「孤兒專案 (Orphaned / Abandoned Projects)」** 的標準 (且唯一長期有效) 的資安實務策略。
    *   **問題的嚴重性：** 許多強烈依賴 `npm` 或 `PyPI` 的專案，可能依賴了一個 5 年前某個大學生寫的 parsing 套件。如果這套件出現 0-day RCE 漏洞，由於沒有上游社群 (Upstream) 在維護發布 補丁，SCA 工具只會一直亮紅燈，但給不出升級版本的建議。
    *   **短/中期的應急之策 (Fork & Patch)：** 既然沒有人來救你，而系統必須立刻上線止血。你有權利 (多數開源授權允許) Fork 這個程式碼庫到你公司內部的 Git 伺服器，由內部的開發團隊自行寫 Patch (如果你們修得好的話) 並包裝成內部版 (`v1.0-internal-patched`)。也可以搭配 WAF 作為防禦縱深 (Defense in Depth)。
    *   **長期的治本之策 (Migration/Replacement)：** 維護別人寫的古老冷門套件會產生巨大的技術債 (Technical Debt)。團隊的最終目標必須是評估、重構 (Refactor)，並將整個依賴項替換成另一個功能相似、但是擁有龐大活躍社群維護的現代化函式庫。

#### **8. Which of the following is considered a "malicious" supply chain attack technique where attackers discover a popular, legitimate open-source package (e.g., `requests`) and publish a malicious package with a deliberate, subtle typo in the name (e.g., `reqeusts` or `requestts`) on a public registry, hoping developers will accidentally download the poisoned version?**
**(一名陰險的土匪，在京城最大的公共藥舖 (public registry) 對面，偷偷開了一間長得一模一樣的小破店。京城本來有一款全天下都在買的老字號保平安仙丹，名叫『大補金丹 (requests)』。這土匪非常陰險，他造了一大批吃了會讓人七孔流血的毒藥丸 (malicious package)。然後！他在這毒藥丸的罐子上，貼了一張叫作【『大補金丹丹 (requestts)』或『大補金舟 (reqeusts)』】的標籤！他把這毒藥丸跟真藥丸一起擺在拍賣大架上。結果，許多剛進城的菜鳥小太監，因為眼花或者手殘按錯了字，不小心就把這罐長得差點一模一樣的毒藥買了回家。小太監一吃當場暴斃！請問，這種靠著「錯字、多半個字不長眼」來坑殺無辜百姓的超下三濫投毒大騙局，學名為何？)**
A. Dependency Confusion (依賴性混淆是土匪在大街上賣一罐『我家私房秘方毒藥』，然後名字剛好跟老爺家保險箱裡的祖傳秘方『一字不差的同名』。然後土匪利用管家喜歡貪便宜買外站仙丹的智障邏輯，把真品給狸貓換太子。這題土匪是故意寫錯名字惹人眼盲，不是名字一模一樣的高層次騙局)
B. Typosquatting (這就是名震四海、無數開發者半夜敲鍵盤敲到眼瞎而成為冤魂的：【『錯字大陣法之視覺詐欺投毒法：錯植網域名稱/錯字套件詐騙 (Typosquatting)！』】。這種攻擊手法低級但致命！駭客們深知，開發者在終端機輸入 `pip install requests` 或是 `npm install express` 的時候，極容易因為鍵盤按太快而打成 `requsts` 或 `exrpes`。於是駭客就先去 npm/PyPI 註冊這幾十個長得很像的「錯字套件 (Poisoned version)」。這些錯字套件裡面，除了包含真正的正常功能 (為了不讓你起疑心)，更會偷偷埋藏惡意挖礦程式或是把你的 SSH Key 用 HTTP POST 全給偷傳回俄羅斯！因為開發者輸入完指令後通常就去喝咖啡了，等他回來發現環境裝好了，根本不知道自己剛把引狼入室的毒藥裝進了公司的核心伺服器裡！這是開源生態系中最難根除的人性死神襲擊！)
C. Account Takeover (ATO) (帳號接管是土匪直接拿刀架在賣真藥『大補金丹』的老闆脖子上，拿老闆的密碼登入進去，在真正的真藥裡面下毒。這題土匪是自己去開別家店、賣別的名字的毒藥，沒有去盜用老掌櫃的帳號密碼)
D. Build Environment Compromise (環境建置被駭這是連整個鍊丹爐的底下金屬都被換成毒氣管線 (SolarWinds等級)。這題土匪只是擺了一個爛攤子等你這智障走錯路，而不是強行闖入你的鑄劍廠大本營)

*   **正確答案 / Correct Answer：B**
*   **[解析邏輯]**
    *   **為何 B 是最佳選擇：** 這是對 **「錯字搶註 / 誤植域名詐騙 (Typosquatting)」** 攻擊手法的經典定義 (在軟體供應鏈中通常稱為 套件誤植套用 Package Typosquatting)。
    *   **運作原理：** 攻擊者利用了人類打字容易出錯的心智盲點。他們在 npm, PyPI, RubyGems 等自動化註冊且無嚴格人工審查的公共套件庫上，大量註冊一些與知名套件極為相似的名稱 (`lo-dash` 代替 `lodash`, `urllib2` 代替 `urllib3`)。
    *   **惡意負載 (Payload)：** 這些惡意套件通常在 `post-install` 腳本 (如 `package.json` 的 `preinstall` 或 Python 的 `setup.py`) 中動手腳。當你一打錯指令安裝，惡意程式會立刻在背景執行，竊取環境變數 (Environment Variables, 如 AWS Access Keys) 或下載建立 RCE 後門。
    *   **防範機制：** 開發團隊必須使用 SCA 工具、在內部設定私有鏡像庫 (Private Proxy Repository 如 Nexus, Artifactory)，並且強烈建議不要讓開發者手動在 CLI 自由 `npm install`，所有的依賴都應該經過嚴格宣告的鎖定檔 (`package-lock.json`, `requirements.txt`) 與雜湊校驗。
