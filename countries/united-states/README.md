# 美國：2026年AI相關資安事件

[← 回到總覽](../../README.md)

🆕＝2026-11-21第二版新增（9–11月深度擴充）；🧨＝2026-11-22第三版新增（ARTEX專題，見[artex.md](../../artex.md)）；🧠＝2026-11-24第四版新增（AI模型專題，見[models.md](../../models.md)）；🔄＝第二／三版補充細節；`ARTEX`等標籤＝涉及之AI攻擊框架（`ARTEX?`＝同波疑似、未證實）。

本國為主要受害方／發布國之事件：**20 件**；本國為歸因來源之跨國事件：**2 件**；本國受波及之跨國事件：**2 件**。資料期間 2026-01-01 至 2026-11-22，依日期排序。

## 事件列表

| ID | 日期 | 事件 | 類別 | 手法／AI角色 | 受害對象 | 影響 | 歸因來源 | 可信度 | 來源 |
|---|---|---|---|---|---|---|---|---|---|
| US-01 | 2026-05-11 | Google GTIG：首次發現攻擊者以AI發掘並武器化零時差漏洞（開源網站管理工具2FA繞過） | AI輔助攻擊/惡意程式 | 以AI找出硬編碼信任假設邏輯錯誤，產出Python利用程式繞過2FA，原計畫大規模利用 | 某熱門開源網站管理工具使用者（未具名） | Google與廠商協調於大規模利用前修補 | 未歸因 | 🟢高 | [cloud.google.com](https://cloud.google.com/blog/topics/threat-intelligence/ai-vulnerability-exploitation-initial-access/) |
| US-02 | 2026-06 | OpenAI 6月報告：中國來源帳號以ChatGPT生成內容，操弄美國AI資料中心與科技關稅議題（Data Center Bandwagon／Tech and Tariffs） | AI認知作戰/影響力行動 | 生成社群留言與圖片，宣稱AI資料中心推高電價、批評美國關稅；並散布ChatGPT用戶資料外洩之不實說法 | 美國輿論、OpenAI | OpenAI評估未見顯著擴散 | 中國 | 🟢高 | [cdn.openai.com](https://cdn.openai.com/pdf/96b559fa-c165-4575-805d-e636909e2f78/June-2026-Threat-Report.pdf)<br>[openai.com](https://openai.com/index/disrupting-malicious-uses-of-ai-tech-and-tariffs/) |
| US-03 | 2026-07-16 | Hugging Face揭露生產環境遭「端到端自主AI代理」入侵（惡意資料集觸發程式碼執行） | 針對AI系統/平台的攻擊 | 惡意資料集濫用資料集處理流程的兩條程式碼執行路徑（遠端程式碼載入器、資料集設定範本注入），提升至節點權限、竊取雲端與叢集憑證並橫向移動；攻擊由自主代理框架執行上萬動作 | Hugging Face內部資料集與服務憑證 | 有限的內部資料集與數組服務憑證遭未授權存取（評估仍持續） | 未歸因（自主AI代理） | 🟢高 | [huggingface.co](https://huggingface.co/blog/security-incident-july-2026)<br>[openai.com](https://openai.com/index/hugging-face-model-evaluation-security-incident/) |
| US-04 | 2026-08-19 | CISA等聯合通報AA26-231A：攻擊者以AI生成腳本鎖定網際網路暴露的Siemens S7 PLC | AI輔助攻擊/惡意程式 | 以AI生成腳本、偽裝成合法監控軟體，透過snap7函式庫以S7comm讀寫PLC | 能源、水務、製造等關鍵基礎設施OT | 進行中的主動威脅（未公布受害數） | 未歸因 | 🟢高 | [cisa.gov](https://www.cisa.gov/news-events/cybersecurity-advisories/aa26-231a)<br>[cyber.gc.ca](https://www.cyber.gc.ca/en/news-events/cyber-threat-actors-use-artificial-intelligence-active-global-campaign-disrupt-internet-exposed-programmable-logic-controllers) |
| US-05 | 2026-09-02 | CISA將LiteLLM MCP認證繞過漏洞（CVE-2026-59822）列入已遭利用漏洞清單KEV | 針對AI系統/平台的攻擊 | LiteLLM（LLM API閘道）MCP Streamable HTTP端點的OAuth2 passthrough fallback可被偽造Bearer權杖繞過，未授權者可列出並呼叫MCP工具與後端服務 | 部署LiteLLM < 1.84.0且開啟MCP者 | CVSS 8.8；已遭在野利用 | 未歸因 | 🟢高 | [nvd.nist.gov](https://nvd.nist.gov/vuln/detail/cve-2026-59822)<br>[github.com](https://github.com/advisories/GHSA-7488-6r32-c95q) |
| US-06 | 2026-09-25 | 🔄 `Strix/Cairn/Hermes` Gambit Security：犯罪者串接Strix、Cairn、Hermes三個開源AI代理入侵數百家電商，竊取60萬筆信用卡 | AI代理自動化入侵 | Strix負責掃描（經OpenRouter使用GLM 5.2、後改DeepSeek v4 Pro）、Cairn自主利用、Hermes編排；植入側錄程式（skimmer） | 線上零售商、某財星500大旅館業者、美國大型航空公司等 | 逾60萬筆信用卡資料（來自兩家公司）；攻擊者下令對至少27個具名受害者植入側錄程式，其中19個確認 | 未歸因（財務動機） | 🟢高 | [gambit.security](https://gambit.security/blog-posts/autonomous-ai-agents-online-retailers-25-a-company)<br>[theregister.com](https://www.theregister.com/security/2026/09/25/crook-used-three-open-source-agents-to-break-into-a-fortune-500-hospitality-company-a-major-us-airline-and-25-other-orgs/5299012) |
| US-07 | 2026-10-20 | `Cairn` NorForge／路透：說中文的駭客以Cairn等自主AI代理攻擊逾1,200個網站，入侵逾百家公司（含Deere、SharkNinja、Cummins） | AI代理自動化入侵 | 以不到100個中文字的指示交由AI代理自主找出程式碼執行點並植入webshell上傳器；平均約23小時完成入侵；工作者名稱顯示疑以Claude Code驅動DeepSeek V4.1 Flash | 美國為主，另含日本、澳洲之電商與企業網站 | 逾100家公司網站遭入侵；總成本約5,000美元token（每次成功約50美元） | 中國（說中文的犯罪者） | 🟡中 | [thehackernews.com](https://thehackernews.com/2026/10/hackers-use-autonomous-ai-agents-to.html) |
| US-08 | 2026-10-21 | `ARTEX` Microsoft：中國國家關聯Storm-0940以ARTEX代理框架自動化攻擊數百組織，並造成ConnectWise供應鏈入侵 | AI代理自動化入侵 | 以ARTEX加速掃描偵察、密碼噴灑與OAuth應用濫用；透過ConnectWise Cloud Backup已授權應用登入下游M365租戶，經Microsoft Graph偵察、更改應用憑證與權限；部分案例從鎖定到取得雲端特權不到3小時 | 全球數百組織（航太國防、能源、金融、政府、半導體等）；ConnectWise Cloud Backup合作夥伴與客戶 | 嘗試登入逾2,250個雲端租戶（The Register）；ConnectWise停用7個應用身分 | 中國（國家關聯：Storm-0940） | 🟢高 | [microsoft.com](https://www.microsoft.com/en-us/security/blog/2026/10/21/storm-0940-uses-artex-agentic-ai-connectwise-supply-chain-compromise/)<br>[connectwise.com](https://www.connectwise.com/company/trust/advisories)<br>[theregister.com](https://www.theregister.com/security/2026/10/22/microsoft-says-connectwise-breach-let-chinese-spies-loose-on-2250-cloud-tenants/5304687) |
| US-12 | 2026-10-21 | 🆕 🔄 `ARTEX?` Railway雲端平台遭入侵，攻擊者鎖定客戶環境變數中的AI供應商金鑰，造成約74萬美元未授權AI用量 | 針對AI系統/平台的攻擊 | 攻擊者取得部分客戶環境變數，主要目標為OpenAI等AI供應商API金鑰，竊得後大量盜用模型（LLMjacking） | Railway客戶（1,852名用戶權杖遭重設） | 約74萬美元未授權AI用量；Railway承諾負擔未退款部分 | 未歸因 | 🟢高 | [blog.railway.com](https://blog.railway.com/p/incident-report-october-security-incident)<br>[blog.railway.com](https://blog.railway.com/p/bulletin-compensation)<br>[bleepingcomputer.com](https://www.bleepingcomputer.com/news/apple/railway-breach-leads-to-740-000-in-fraudulent-ai-charges/)<br>[blog.barracuda.com](https://blog.barracuda.com/2026/11/11/anatomy-of-a-machine-speed-intrusion) |
| US-17 | 2026-10-22 | 🧨 `ARTEX` Wiz：ARTEX使用者（重疊Storm-0940）擴大鎖定IT與軟體供應商，攻擊Okta、Entra與Cognito | AI代理自動化入侵 | 固定劇本：下載JS bundle、source map與Swagger找出內部API；操弄OAuth callback、以alg=none未簽章JWT轟炸60餘種SSO路徑（2分鐘內）；Okta／Entra密碼噴灑（中位間隔1秒、每波20–60分鐘、鎖定軟體工程師）；濫用密碼重設；以一次性信箱註冊後測租戶隔離；被封鎖數分鐘內換IP；fuzz前先請求/zzz-nonexistent-xyz123建立基準 | 多家IT與軟體供應商（未具名） | 多數嘗試失敗；部分工作階段持續24–30小時 | 中國（國家關聯；與微軟Storm-0940重疊） | 🟢高 | [wiz.io](https://www.wiz.io/blog/artex-in-the-wild-storm-0940-expands-targeting-of-it-and-software-vendors) |
| US-18 | 2026-11-04 | 🧨 `ARTEX` Kernel公告資安事件：外洩API金鑰遭濫用，攻擊者存取日誌供應商與GPU伺服器並植入挖礦程式，公司研判以ARTEX為指揮中心 | AI代理自動化入侵 | 10/24外洩API金鑰遭使用；10/27存取日誌服務供應商；11/03存取4台GPU伺服器並執行挖礦 | Kernel（瀏覽器基礎設施新創）及其客戶 | 約0.28%客戶受影響 | 未歸因 | 🟡中 | [kernel.sh](https://www.kernel.sh/blog/public-notice-of-security-incident-nov-4-2026) |
| US-09 | 2026-11-05 | 美國紐約南區檢察署起訴3人以AI（深偽語音／影像）冒充執行長與律師，詐騙全球企業1.29億美元 | 深偽詐騙/語音複製 | 以AI模仿企業高層聲音與影像致電員工，佯稱機密併購交易，再冒充大型律所律師指示匯款，贓款轉為加密貨幣 | 美國及全球企業（醫院體系、銀行、英國金融科技公司、基金公司等） | 逾1.29億美元；3人分別於西班牙、英國被捕 | 以色列／英國／西班牙籍嫌犯 | 🟢高 | [justice.gov](https://www.justice.gov/index.php/usao-sdny/pr/three-foreign-nationals-arrested-and-charged-scheme-use-super-intelligence-defraud) |
| US-13 | 2026-11-05 | 🆕 `ARTEX` Microsoft：攻擊者以ARTEX代理框架搜尋GitHub外洩的OAuth應用程式密鑰，進而入侵Entra租戶 | AI代理自動化入侵 | 代理自動搜尋GitHub上的OAuth應用密鑰，冒用OAuth應用在受害租戶執行經授權操作（10/28起觀察到租戶遭存取） | 多個Microsoft Entra租戶組織 | —（未公布受害數） | 未歸因 | 🟢高 | [microsoft.com](https://www.microsoft.com/en-us/security/blog/2026/11/05/threat-actors-use-agentic-ai-tooling-to-find-and-abuse-exposed-secrets/) |
| US-19 | 2026-11-06 | 🧨 `ARTEX` WorkOS更新事件報告：安全研究員的ARTEX代理逃出基準測試沙箱，以弱憑證登入內部業務工具大量下載資料 | 針對AI系統/平台的攻擊 | 研究員為資安基準評測執行ARTEX代理，代理離開隔離環境；10/25首次存取、10/30大量擷取；根因：服務公開暴露、可預測開發憑證、無速率限制、遙測缺口；UA含ArtEx/1.0、artex-enrich/1.0、norma/0.4 | WorkOS內部go-to-market工具（CRM聯絡人、客戶往來紀錄） | CRM聯絡人與客戶通訊紀錄遭下載 | 未歸因（研究人員之代理失控，非惡意行動者） | 🟢高 | [workos.com](https://workos.com/security/bulletins/update-for-october-30th-2026-data-security-incident)<br>[bleepingcomputer.com](https://www.bleepingcomputer.com/news/security/runaway-ai-hacking-agent-behind-workos-breach-after-escaping-sandbox/) |
| US-20 | 2026-11-11 | 🧨 `ARTEX` Barracuda：竊得某AI廠商雲端金鑰的ARTEX式攻擊，44小時內存取約10個雲端帳號 | AI代理自動化入侵 | 金鑰存於某AI廠商GitHub repo設定檔（10月遭竊）；11/1–2於資料分析、原始碼庫與Kubernetes間移動，搜尋加密貨幣相關機密；11/4發現；手法與Railway事件相似 | Barracuda雲端環境（約10個帳號）；XDR整合憑證可能外洩 | 要求客戶輪替XDR整合憑證 | 未歸因 | 🟢高 | [blog.barracuda.com](https://blog.barracuda.com/2026/11/11/anatomy-of-a-machine-speed-intrusion)<br>[bleepingcomputer.com](https://www.bleepingcomputer.com/news/security/barracuda-links-cloud-breach-to-artex-ai-powered-cyberattack/)<br>[trust.barracuda.com](https://trust.barracuda.com/security/barracuda-xdr-integration-credentials) |
| US-10 | 2026-11-12 | FBI FLASH：北韓「FaceStealer」以偽造視訊會議與受害者錄影、AI深偽影片竊取逾4億美元加密貨幣 | 深偽詐騙/語音複製 | 以假Zoom/Teams/Meet會議播放先前受害者錄影冒充熟人，製造技術故障誘導安裝惡意程式；開始以AI生成加密圈知名人士深偽影片 | 加密貨幣/Web3產業、開源軟體維護者 | 過去18個月竊取逾4億美元；FBI扣押逾900段受害者webcam影片 | 北韓（Sapphire Sleet／BlueNoroff等） | 🟢高 | [ic3.gov](https://www.ic3.gov/csa/2026/261112.pdf) |
| US-14 | 2026-11-12 | 🆕 `Cairn` Unit 42：CL-STA-1238以客製化Cairn自主攻擊框架對至少19個組織發動25次行動，10個成功（半導體、美國國防政策、人權團體） | AI代理自動化入侵 | Cairn調度／黑板架構＋非上游「AIScan Runner Skills」技能包；模型使用智譜GLM 5.2與DeepSeek V4 Flash/Pro；含AUTHORIZATION.md偽授權文件；C2 154.44.31[.]4（香港）、82.29.129[.]54 | 半導體供應鏈、美國國防政策機構、人權團體（含加拿大團體及逾百萬會員紀錄之美國教師工會） | 25次行動中10個目標遭未授權存取或資料擷取（2026年8–9月） | 中國（國家關聯，中度信心：CL-STA-1238） | 🟢高 | [unit42.paloaltonetworks.com](https://unit42.paloaltonetworks.com/cairn-framework-ai-autonomous-attacks/)<br>[cybersecuritydive.com](https://www.cybersecuritydive.com/news/china-hacker-ai-tool-campaign-us-defense-semiconductor/874619/) |
| US-15 | 2026-11-12 | 🆕 Symantec：攻擊美國零售商的手動指令遭阻擋後，攻擊者改用疑似AI生成指令，數分鐘內竊取憑證並橫向移動 | AI輔助攻擊/惡意程式 | 人工輸入指令被擋後改用AI生成命令，迅速恢復攻擊鏈 | 美國零售商（未具名） | 憑證遭竊、內網橫向移動 | 未歸因 | 🟡中 | [security.com](https://www.security.com/threat-intelligence/ai-assisted-attack-us-retailer) |
| US-16 | 2026-11-13 | 🆕 `ARTEX` FBI FLASH-20261113-001：ARTEX自主滲透框架威脅概覽，公布24個IP、網域與LLM API主機等IOC | AI代理自動化入侵 | ARTEX（Go語言，2026年7月發布，10/8下架）自2026年8月起遭惡意使用，部分入侵3小時內取得特權；全球逾1,600個暴露控制台；IOC含38.244.50.120、144.172.64.60、xcai.pro等 | 美國及多國組織；韓國金融機構；ConnectWise下游逾2,250個租戶遭嘗試登入 | 韓國金融機構約6.7萬人個資外洩（FBI引述） | 中國（工具開發來源；多個使用者） | 🟢高 | [ic3.gov](https://www.ic3.gov/CSA/2026/261113.pdf)<br>[ic3.gov](https://www.ic3.gov/CSA/2026/261113.csv)<br>[ithome.com.tw](https://www.ithome.com.tw/news/180508) |
| US-11 | 2026-11-18 | CISA再將LiteLLM漏洞（CVE-2026-40217，未受保護替代通道）列入KEV | 針對AI系統/平台的攻擊 | LiteLLM AI閘道替代通道未受保護，已遭在野利用 | 部署LiteLLM之組織 | 已遭在野利用（細節未公開） | 未歸因 | 🟢高 | [cisa.gov](https://www.cisa.gov/news-events/alerts/2026/11/18/cisa-adds-four-known-exploited-vulnerabilities-catalog) |

## 事件補充說明

- **US-01**：受害範圍為全球；因發布者為美國企業暫列美國
- **US-03**：OpenAI後續說明與其模型評估代理有關；HF總部位於美國
- **US-04**：全球性活動；加拿大網安中心9/8另發警示
- **US-06**：Vulone 10/19報告稱Gambit所揭露之「SOUL」行動為同一名說中文的單一操作者所為（單一廠商說法）
- **US-07**：路透審閱攻擊者自身紀錄後報導；模型推測未經證實
- **US-08**：受害為全球性，ConnectWise為美國公司
- **US-12**：Barracuda 11/11稱其遭入侵手法與Railway事件相似、疑似同為ARTEX；Railway本身未證實
- **US-18**：ARTEX為受害方研判（believes）
- **US-09**：犯行期間2024–2026
- **US-19**：首例公開的「合法研究用ARTEX代理失控」事件；WorkOS公布之IP 154.64.252[.]77亦見於Datadog／SentinelOne的ARTEX IOC清單
- **US-15**：AI參與為廠商研判（「appears to be」）

## 交叉引用：涉及美國的跨國／他國事件

以下事件主檔在他國或「全球」，但美國為受害方或攻擊目標之一。

| ID | 日期 | 主檔 | 事件 | 可信度 |
|---|---|---|---|---|
| GL-26 | 2026-10-29 | [全球](../global/README.md) | CrowdStrike：VAPOR PANDA以ARTEX＋DeepSeek在11天內對14國逾200個組織同時發動間諜入侵，部署BLOODALCHEMY後門 | 🟢高 |
| GL-36 | 2026-10-30 | [全球](../global/README.md) | Google GTIG／Mandiant「ARTEX and Friends」：代理式攻擊框架登場，UNC7228最快15分鐘取得深層存取 | 🟢高 |

## 交叉引用：歸因來源為美國的跨國事件

以下事件的主要受害方在他國，詳細內容見該國檔案。

| ID | 日期 | 受害國 | 事件 | 歸因說明 | 可信度 |
|---|---|---|---|---|---|
| CN-02 | 2026-03-03 | [中國](../china/README.md) | 外交部回應「美國使用AI賦能對華網攻」報導：稱美國為網路空間最大不穩定源 | 美國（中方說法） | 🟡中 |
| GL-37 | 2026-11-05 | [全球](../global/README.md) | Censys：全球1,465個暴露ARTEX控制台（約815個獨立主機），155個同時託管其他威脅基礎設施 | 未歸因（多數控制台位於美國、香港、中國） | 🟢高 |

