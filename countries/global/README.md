# 全球：2026年AI相關資安事件

[← 回到總覽](../../README.md)

本國為主要受害方／發布國之事件：**11 件**；本國為歸因來源之跨國事件：**0 件**。資料期間 2026-01-01 至 2026-11-21，依日期排序。

## 事件列表

| ID | 日期 | 事件 | 類別 | 手法／AI角色 | 受害對象 | 影響 | 歸因來源 | 可信度 | 來源 |
|---|---|---|---|---|---|---|---|---|---|
| GL-01 | 2026-02-01 | ClawHavoc：OpenClaw技能市集ClawHub遭大規模投毒，數百個惡意技能散布Atomic macOS Stealer | AI供應鏈攻擊 | 惡意技能以「前置需求」誘導執行glot.io混淆指令或下載加密ZIP，安裝AMOS竊取憑證、瀏覽器資料、加密錢包、SSH金鑰 | OpenClaw使用者（全球） | 初次掃描2,857個技能中341個惡意，2/16更新增至824個 | 未歸因 | 🟢高 | [paloaltonetworks.com](https://www.paloaltonetworks.com/blog/security-operations/clawhavoc-ai-agent-skills-poisoning/)<br>[trendmicro.com](https://www.trendmicro.com/en/research/26/b/openclaw-skills-used-to-distribute-atomic-macos-stealer.html) |
| GL-02 | 2026-02-12 | Google GTIG AI威脅追蹤：模型蒸餾（model extraction）攻擊增加，國家級駭客以Gemini做偵察與釣魚誘餌 | 針對AI系統/平台的攻擊 | 私部門與研究者大量蒸餾攻擊竊取模型能力；APT42等以Gemini蒐集目標、製作釣魚情境；UNC795以Gemini做入侵研究 | Google AI模型、各國國防與政府目標 | — | 北韓、伊朗、中國、俄羅斯 | 🟢高 | [cloud.google.com](https://cloud.google.com/blog/topics/threat-intelligence/distillation-experimentation-integration-ai-adversarial-use) |
| GL-03 | 2026-02-25 | OpenAI 2月報告：中國「網路特戰」IO、柬埔寨半自動AI戀愛詐騙、俄羅斯Rybar內容農場 | AI認知作戰/影響力行動 | 以ChatGPT規劃/編修IO報告、生成批量社群留言；詐騙集團結合人工提示與自動聊天機器人 | 全球異議人士、印尼年輕男性（詐騙）、X與Telegram使用者 | — | 中國、俄羅斯、柬埔寨 | 🟢高 | [openai.com](https://openai.com/index/disrupting-malicious-ai-uses/) |
| GL-04 | 2026-03 | LiteLLM官方公告疑似供應鏈事件（3月） | AI供應鏈攻擊 | LiteLLM（熱門LLM閘道套件）疑遭供應鏈攻擊（細節見官方公告） | LiteLLM使用者 | 詳見公告 | 未歸因 | 🟡中 | [docs.litellm.ai](https://docs.litellm.ai/blog/security-update-march-2026) |
| GL-05 | 2026-06-22 | Five Eyes網安機關聯合聲明：AI已加速攻擊、縮短漏洞發現到利用時間，領導層須立即行動 | 政府警示/評估報告 | AI加速漏洞發現與利用；呼籲董事會層級治理、加速修補、汰換舊系統、強化身分控管 | 五眼聯盟各國組織 | —（聲明） | — | 🟢高 | [cisa.gov](https://www.cisa.gov/news-events/news/five-eyes-cyber-security-agencies-statement)<br>[ncsc.gov.uk](https://www.ncsc.gov.uk/news/the-ai-shift-in-cyber-risk-why-leaders-must-act-now) |
| GL-06 | 2026-07-02 | Sysdig：首例有紀錄的端到端「代理式勒索軟體」JADEPUFFER | AI代理自動化入侵 | LLM代理利用暴露的Langflow（CVE-2025-3248）入侵，自主收集憑證、橫向移動，加密生產MySQL中1,342筆Nacos設定並勒索；人類負責基礎設施與初始存取 | 某組織（未具名） | 1,342筆設定項目遭加密 | 未歸因 | 🟢高 | [sysdig.com](https://www.sysdig.com/blog/jadepuffer-agentic-ransomware-for-automated-database-extortion)<br>[theregister.com](https://www.theregister.com/security/2026/07/02/smooth-ai-criminal-drives-first-end-to-end-agentic-ransomware-attack/5266073) |
| GL-07 | 2026-09-08 | Google GTIG Q2報告：攻擊者6小時內完成代理式大規模憑證收集；UNC6780誘騙AI程式助手與LLM掃描器進行供應鏈入侵 | AI供應鏈攻擊 | UNC6780以多種手法欺騙AI coding assistant與LLM安全掃描工具；攻擊者竊取AI模型、程式碼、API憑證並劫持雲端算力（LLMjacking）；蒸餾攻擊單次逾1億提示 | 開源生態、企業AI資產 | — | 北韓、中國、伊朗、俄羅斯等 | 🟢高 | [cloud.google.com](https://cloud.google.com/blog/topics/threat-intelligence/from-prompting-to-autonomy-the-evolution-of-adversarial-ai) |
| GL-08 | 2026-09-10 | Anthropic威脅情報報告：Claude被用於多代理框架編排網攻、影響力行動、監控、詐騙與蒸餾 | AI代理自動化入侵 | 2025/12–2026/8間攔阻之案例：AI從助手變成攻擊編排者，降低技能與成本門檻；涵蓋國家支持團體、犯罪集團、商業間諜軟體廠商 | 全球多組織 | —（案例彙整） | 中國、北韓等（多個疑似國家支持團體） | 🟢高 | [anthropic.com](https://www.anthropic.com/threat-intelligence-report-september-2026) |
| GL-09 | 2026-10-21 | LiteLLM 1.107.0遭植入惡意程式上架PyPI約2小時：.pth啟動掛鉤竊取憑證並載入遠端程式碼 | AI供應鏈攻擊 | 以仿冒倉庫建置惡意wheel，含cook.pth與sitecustomize.py，於Python啟動時自動執行 | 安裝1.107.0或使用受影響Docker映像的AI應用開發者 | 需輪換所有可觸及憑證（受害數未公布） | 未歸因 | 🟢高 | [docs.litellm.ai](https://docs.litellm.ai/blog/security-incident-oct-21-2026)<br>[microsoft.com](https://www.microsoft.com/en-us/security/blog/2026/10/23/inside-the-litellm-1-107-0-supply-chain-compromise-credential-theft-through-python-startup-hooks/) |
| GL-10 | 2026-11-08 | LNbits實例遭協同攻擊，疑為多個自主AI代理並行利用SSRF並即時生成惡意擴充套件 | AI代理自動化入侵 | 利用舊版Python擴充之SSRF及未更新漏洞，部分入侵底層伺服器；在不同實例上部署即時生成的惡意擴充 | LNbits官方與社群營運的比特幣閃電網路實例 | 多個實例遭入侵、服務中斷（損失細節見原報告） | 未歸因 | 🟡中 | [news.lnbits.com](https://news.lnbits.com/news/november-8th-incident-report) |
| GL-11 | 2026-11-13 | Bitrise揭露遭ARTEX代理攻擊：利用無2FA的閒置測試帳號，10小時內串連竊得憑證存取原始碼與基礎設施 | AI代理自動化入侵 | ARTEX代理先以「授權滲透測試」UA偵察，後以一般客戶身分測試租戶隔離；11/13登入無2FA內部測試帳號，11分鐘內使用雲端金鑰並連鎖取得簽章檔、原始碼、基礎設施狀態與建置日誌 | Bitrise（行動應用CI/CD平台）與15個客戶工作區 | 15個客戶工作區檔案遭未授權存取；撤銷919把雲端服務帳號金鑰、重建上千台伺服器 | 未歸因 | 🟢高 | [bitrise.io](https://bitrise.io/artex-incident-report) |

## 事件補充說明

- **GL-03**：其中針對日本首相、印尼之個案另列
- **GL-04**：僅確認官方公告頁存在，細節未逐一核對
- **GL-10**：AI驅動為受害方研判

