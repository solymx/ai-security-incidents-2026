# ARTEX 專題：AI 自主滲透框架 ARTEX 相關資安事件彙整（2026-07 ～ 2026-11-22）

[← 回到總覽](README.md)｜[9–11 月專題](sep-nov-2026.md)｜[時間軸](timeline.md)｜[完整資料 CSV](data/events.csv)（`framework` 欄位含 `ARTEX` 者）

> 本頁依資料集中標記 `framework=ARTEX` 的事件**自動產生**，所有統計皆由下表事件計算。🧨＝2026-11-22 第三版新增；`ARTEX?`＝同波疑似、官方或鑑識報告**未證實**使用 ARTEX，另列於「疑似」段落，不計入主統計。資料截止：2026-11-22（台北時間）。
> 本頁僅收錄**公開**資訊；IOC 皆已去武化（`[.]`），偵測／緩解建議均出自官方或廠商公開通報，不含任何攻擊程式碼或利用細節。

## 一、重點摘要

- 確認涉及 ARTEX 的事件／報告共 **43 件**（本版新增 **21 件**），另有疑似同波 **8 件**；其中具體攻擊、入侵或基礎設施分析 **33 件**、政府示警／評估 **10 件**。
- 可信度：🟢高 33、🟡中 10、🔴低 0。
- 依主檔國家：台灣 3、中國 2、日本 2、韓國 10、印度 1、美國 7、加拿大 2、英國 1、荷蘭 1、歐盟 2、全球 12。
- 時間分布：2026-09 2 件、2026-10 20 件、2026-11 21 件（ARTEX 於 2026-07-26 首次提交，8 月起出現惡意使用，10 月爆量）。

## 二、ARTEX 是什麼

| 項目 | 內容 | 來源／信心 |
|---|---|---|
| 性質 | 以大型語言模型驅動的**開源自主滲透測試框架**（Go 後端＋內嵌 Next.js 控制台、PostgreSQL、norma SDK）；操作者只需給目標與任務目標，由多個 LLM 代理規劃並執行 | S2W（[KR-11](countries/south-korea/README.md)）、Datadog、Sophos｜高 |
| 起源 | GitHub 作者「Autumn-27」（亦為 ScopeSentry 作者）；**2026-07-26** 首次提交，AGPL-3.0 授權；9/3 獲百度安全「Agent+」攻防挑戰賽冠軍（資安院院長、Wiz、CN-SEC 均如此說明） | Censys、公視／資安院、Wiz｜高 |
| 轉閉源 | CrowdStrike 10/7 揭露韓國金融攻擊後，開發者於 **10/8** 轉為閉源；當時已逾 1.2 萬個 fork，備份、分支持續流通（ScopeWeaver、LUCK、觀瀾SEC、ARTEX PRO、ARTEX v2、Prtseek 等） | 聯合早報、Wiz、Datadog、AhnLab、S2W｜高 |
| 著作權爭議 | 微步在線（ThreatBook）11/6 聲明：ARTEX 源自其威脅偵測工程師個人專案，公司擁有著作權；商業版 ARTEX Pro 僅經其 RedAgents 平台銷售 | 微步在線聲明（[CN-14](countries/china/README.md)）｜中（企業自述） |
| 架構 | Planner（規劃）代理拆解目標產生 intent，Worker 代理（預設 3 個並行）執行 nmap、curl、Impacket 等工具並回寫；另有驗證（verifier）、壓縮（compressor）、報告、對話等角色代理；「資產圖」與「探索圖」（黑板：任務、目標、intent、事實、發現、提示、壓縮摘要）作為共享記憶 | S2W、Datadog、AWS、GTIG｜高 |
| 內建控制 | 指令攔截規則（允許／拒絕／詢問人工）、資產允許／封鎖清單（部分版本預設排除 .gov、.gov.cn、.edu、.edu.cn）、mitmproxy 流量錄製、MCP／Skill 擴充 | Datadog、S2W｜高 |
| LLM 使用方式 | 支援 OpenAI 相容、OpenAI Responses、Anthropic Messages 三種格式；任何供應商封鎖金鑰即切換下一家。實際觀測：DeepSeek（主力，含 v4.1-flash）、GLM、Grok、Kimi，以及 Claude、GPT；攻擊者以 GLM 審查 DeepSeek 成果、並把 Claude Code／Codex／Grok 工作區與 ARTEX 串接；SentinelOne 稱每次行動模型成本約 145–1,500 美元，且僅 Opus 5.5 觸發護欄 | Datadog、Zscaler、Hunt.io、SentinelOne｜高 |
| 速度 | FBI：部分入侵自鎖定目標至取得特權不到 3 小時；GTIG：UNC7228 平均約 4 小時、最快 15 分鐘；執行爆發 2–25 秒（23 秒內 27 個事件）；Bitrise：登入後 11 分鐘內使用雲端金鑰 | FBI、GTIG、Bitrise｜高 |
| 暴露規模 | Censys（11/3–4）1,465 個暴露控制台（約 815 個獨立主機；美國 726、香港 387、中國 177、日本 51、新加坡 38、韓國 21）；SentinelOne 曾見至少 2,500 台、在線 1,608 台；FBI 稱逾 1,600 個 | Censys、SentinelOne、FBI｜高 |

### 已知操作者與歸因（信心等級依原報告）

| 操作者／群集 | 報告者 | 歸因 | 目標 | 本資料 ID |
|---|---|---|---|---|
| TAG-217／未具名財務動機者（韓國金融攻擊） | CrowdStrike、Recorded Future、Zscaler、Hunt.io | 說中文；Recorded Future 命名 TAG-217 | 韓國金融業，並擴及全球多產業 | KR-02、KR-10、KR-13、GL-35 |
| Storm-0940（UNC7228 重疊） | Microsoft、Wiz、GTIG | **中國國家關聯**（Microsoft：China-state aligned） | ConnectWise 供應鏈與逾 2,250 個 M365 租戶、IT／軟體供應商、美歐半導體與電信 | US-08、US-17、GL-36 |
| VAPOR PANDA | CrowdStrike | 中國關聯間諜行動（與 Storm-0940 為不同行動） | 14 國逾 200 個組織 | GL-26 |
| Storm-3358 | Microsoft | 柬埔寨據點、財務動機 | 東南亞金融機構 | GL-38 |
| Crafty Falcon | CERT-In | 未公開歸因 | 印度非銀行放貸、金融科技、加密貨幣交易所 | IN-05 |
| Onyx Sleet、Pearl Sleet | Microsoft | 北韓 | 韓國相關目標 | KR-04 |
| MadPot 觀測之多個群體 | Amazon | **中國關聯（中度信心）**，彼此不同 | 全球 AI 平台金鑰、2 家加密貨幣交易所 | GL-41 |
| 韓國 32 歲主嫌等 7 人 | 首爾警察廳 | 韓國國內犯罪者（已移送） | 國內 90 餘家業者、820 萬筆 | KR-03 |
| KimJEN | S2W | 未特定（自稱歐洲籍；Prtseek 開發者與中國駭客社群相關） | 國內約 20 所大學 | KR-14 |
| 研究人員（非惡意） | WorkOS | 基準測試用代理失控 | WorkOS 內部工具 | US-19 |

> 結論：**ARTEX 是工具而非單一組織**。目前至少有 5 個以上彼此獨立的行動者使用（SentinelOne），從國家關聯間諜、財務動機犯罪者到個人駭客皆有；「中國開發」與「中國國家關聯行動者使用」是兩件事，不應混為一談。

## 三、事件總表（依國家，台灣優先）

| ID | 日期 | 國家 | 事件 | 受害對象 | 影響 | 歸因 | 可信度 | 來源 |
|---|---|---|---|---|---|---|---|---|
| [TW-11](countries/taiwan/README.md) | 2026-10-21 | 台灣 | 資安署示警「新型態AI攻擊」：韓、日、法案例顯示LLM＋Agent＋自動化滲透工具大幅提升攻擊效率 | 台灣企業 | —（警示） | — | 🟢高 | [moda.gov.tw](https://moda.gov.tw/ACS/press/news/press/21130)<br>[ithome.com.tw](https://www.ithome.com.tw/news/179865)<br>[news.pts.org.tw](https://news.pts.org.tw/article/832373) |
| [TW-12](countries/taiwan/README.md) | 2026-10-22 | 台灣 | 91APP訂單資料庫遭AI自動化滲透工具（ARTEX）入侵 | 91APP Commerce Cloud品牌客戶與其消費者 | 最多1,329個品牌、4,798,255名消費者（2025/4/4–2026/10/14下單者）之姓名、電話、地址、Email與訂單紀錄；不含信用卡；下游品牌（如全家「行動購」10/29、高林10/27）陸續公告；已衍生詐騙 | 中國（工具來源；攻擊者未歸因） | 🟢高 | [cna.com.tw](https://www.cna.com.tw/news/afe/202610220434.aspx)<br>[91app.com](https://91app.com/91app-202610-security-incident/)<br>[taipeitimes.com](https://www.taipeitimes.com/News/taiwan/archives/2026/11/12/2003867610)<br>[ir.91app.com](https://ir.91app.com/tw/news_detail.php?id=160)<br>[ir.91app.com](https://ir.91app.com/tw/news_detail.php?id=161)<br>[ithome.com.tw](https://www.ithome.com.tw/news/180112)<br>[bankinfosecurity.asia](https://www.bankinfosecurity.asia/artex-ai-hacking-tool-used-to-breach-taiwans-91app-a-33188) |
| [TW-14](countries/taiwan/README.md) | 2026-11-11 | 台灣 | 資安署：國際AI網攻波及台灣十餘家企業與平台，逾百萬份個資受影響，近半數涉及AI／ARTEX | 台灣十餘家企業與網路平台（官方未公布名單） | 逾100萬份個資（姓名、電話、Email、訂單），尚無付款資訊外洩、未見勒索；資料於暗網販售；規模較大者五、六家 | 中國（香港IP，未正式歸因） | 🟢高 | [moda.gov.tw](https://moda.gov.tw/ACS/press/news/press/21422)<br>[ec.ltn.com.tw](https://ec.ltn.com.tw/article/breakingnews/5637709)<br>[taipeitimes.com](https://www.taipeitimes.com/News/taiwan/archives/2026/11/12/2003867610)<br>[informationsecurity.com.tw](https://www.informationsecurity.com.tw/article/article_detail.aspx?aid=13486)<br>[ai.ettoday.net](https://ai.ettoday.net/news/3270502)<br>[ec.ltn.com.tw](https://ec.ltn.com.tw/article/breakingnews/5637092) |
| [CN-13](countries/china/README.md) | 2026-10-09 | 中國 | 🧨 ARTEX中國開發者於工具遭用於攻擊韓國銀行後宣布轉為閉源 | —（工具來源） | 工具已大量擴散，閉源無法回收 | 中國（開發者） | 🟡中 | [zaobao.com.sg](https://www.zaobao.com.sg/news/china/story20261009-9808966)<br>[cn-sec.com](https://cn-sec.com/archives/5418792.html)<br>[wiz.io](https://www.wiz.io/blog/artex-in-the-wild-storm-0940-expands-targeting-of-it-and-software-vendors) |
| [CN-14](countries/china/README.md) | 2026-11-06 | 中國 | 🧨 微步在線（ThreatBook）發表ARTEX著作權聲明：稱源自旗下威脅偵測工程師個人專案，ARTEX Pro僅經RedAgents平台銷售 | —（工具來源） | — | 中國（開發者所屬企業） | 🟡中 | [news.10jqka.com.cn](https://news.10jqka.com.cn/20261106/c681570377.shtml) |
| [JP-06](countries/japan/README.md) | 2026-10-08 | 日本 | JPCERT/CC注意喚起：國內組織連續遭不正存取外洩個資，新增「濫用AI滲透測試平台（Cairn、CyberStrikeAI、ARTEX）」攻擊案例 | 日本多個企業與機關（含BI工具、員工管理系統） | 大量個資外洩（JPCERT未彙總數字） | — | 🟢高 | [jpcert.or.jp](https://www.jpcert.or.jp/at/2026/at260030.html) |
| [JP-13](countries/japan/README.md) | 2026-10-19 | 日本 | GMO Cybersecurity：相次ぐ不正存取的攻擊源多為AI，確認使用中國開發的ARTEX；單一攻擊源鎖定約20家日本企業 | 日本企業約20家（其中8家於2026年9–10月公告資料外洩） | —（未彙總筆數）；已與執法機關共享情資 | 中國（工具開發來源；攻擊者未歸因） | 🟢高 | [gmo-cybersecurity.com](https://gmo-cybersecurity.com/blog/20261019/)<br>[itmedia.co.jp](https://www.itmedia.co.jp/news/article/2610/20/2000002423/)<br>[sankei.com](https://www.sankei.com/article/20261020-HPL6HXXGDJEBBBMYCRDZ7IRKRE/)<br>[watch.impress.co.jp](https://www.watch.impress.co.jp/docs/news/2149749.html)<br>[nikkei.com](https://www.nikkei.com/article/DGXZQOUC199V70Z11C26A0000000/) |
| [KR-10](countries/south-korea/README.md) | 2026-10-03 | 韓國 | 🧨 金融保安院：逆向追蹤新韓銀行日誌與攻擊IP，確認銀行連環駭侵使用ARTEX | 新韓（貸款招攬人查詢服務2萬5,729人）、KB國民（員工行動業務系統119人）、韓亞（員工營業支援系統89人）、BNK釜山（外包人員11人）；友利、NH農協遭攻擊但未受害；另2家儲蓄銀行調查中 | 已確認外洩不到2萬6千人；金融委將建議全面點檢內部員工用系統 | 未歸因（攻擊來自海外） | 🟡中 | [biz.heraldcorp.com](https://biz.heraldcorp.com/article/10892496) |
| [KR-07](countries/south-korea/README.md) | 2026-10-04 | 韓國 | 科技部／KISA發布企業資安強化緊急勸告並將網路威脅警戒升至「注意」，向約2.8萬家企業建議點檢 | 韓國企業（約2.8萬家） | —（警示） | — | 🟡中 | [fnnews.com](https://www.fnnews.com/news/202610041204270490)<br>[etnews.com](https://www.etnews.com/20261004000031) |
| [KR-02](countries/south-korea/README.md) | 2026-10-07 | 韓國 | CrowdStrike：未具名攻擊者以中國開發的ARTEX代理框架＋Claude Code攻擊韓國金融機構並外洩資料 | 新韓、KB國民、韓亞等至少9家韓國銀行（路透） | 資料外洩；部分系統中斷（確切筆數未公開） | 中國（說中文者，可能位於廣東；中度信心） | 🟢高 | [crowdstrike.com](https://www.crowdstrike.com/en-us/blog/unknown-threat-actor-uses-artex-to-target-south-korean-finance/)<br>[reuters.com](https://www.reuters.com/3fec1b0a85a0/world/suspect-behind-south-korea-bank-hacks-may-be-26-year-old-china-cybersecurity-2026-10-08/)<br>[en.yna.co.kr](https://en.yna.co.kr/view/AEN20261008002200320)<br>[zscaler.com](https://www.zscaler.com/blogs/security-research/threat-actor-abuses-agentic-ai-pentesting-framework-target-south-korean)<br>[recordedfuture.com](https://www.recordedfuture.com/blog/tag-217-artex-south-korean-banks)<br>[datanet.co.kr](https://www.datanet.co.kr/news/articleView.html?idxno=300166) |
| [KR-11](countries/south-korea/README.md) | 2026-10-13 | 韓國 | 🧨 S2W：韓國金融業遭攻擊所用之ARTEX初步分析（功能、工作流程與偵測建議） | 韓國金融業 | —（分析報告） | 未歸因 | 🟢高 | [s2w.inc](https://www.s2w.inc/en/resources/1128) |
| [KR-08](countries/south-korea/README.md) | 2026-10-14 | 韓國 | 金融委員會／金融監督院第二次緊急會議：16家金融公司遭駭、約10萬筆外洩；555家點檢中130家有缺失 | 新韓、KB、韓亞、BNK等銀行，Yegaram、Welcome、OK等儲蓄銀行，現代Capital、MG中央會、PFCT、Mouda、DB儲蓄銀行、KDB Capital、Streami（Gopax）等16家 | 約10萬筆個資外洩；555家中130家點檢不合格 | 中國（說中文者；同一AI工具攻擊者，非正式歸因） | 🟡中 | [yna.co.kr](https://www.yna.co.kr/view/AKR20261014134851002) |
| [KR-03](countries/south-korea/README.md) | 2026-10-26 | 韓國 | 首爾警方：非資工背景者以生成式AI與「AI自律滲透測試系統」入侵90餘家機構竊取820萬筆個資並勒索 | 補習班、醫院、高爾夫球場、大學、大企業子公司等90餘家 | 820萬筆個資外洩；其中60家以AI入侵；向38家勒索3.6億韓元 | — | 🟡中 | [yna.co.kr](https://www.yna.co.kr/view/AKR20261026075100004)<br>[ithome.com.tw](https://www.ithome.com.tw/news/179973)<br>[bleepingcomputer.com](https://www.bleepingcomputer.com/news/security/former-pentester-used-artex-ai-to-steal-82-million-data-records/)<br>[edaily.co.kr](https://www.edaily.co.kr/News/Read?newsId=02955286645616856) |
| [KR-04](countries/south-korea/README.md) | 2026-10-29 | 韓國 | Microsoft：北韓8個駭客組織AI採用程度分級，3組已將AI納入日常作業，大量量產針對南韓的釣魚文件 | 南韓使用者、加密貨幣與軟體開發生態 | — | 北韓 | 🟢高 | [microsoft.com](https://www.microsoft.com/en-us/security/blog/2026/10/29/tracking-ai-adoption-in-north-korean-threat-actor-tradecraft/)<br>[news.sbs.co.kr](https://news.sbs.co.kr/english/article.do?news_id=N1008823304) |
| [KR-12](countries/south-korea/README.md) | 2026-10-30 | 韓國 | 🧨 AhnLab ASEC：追蹤ARTEX基礎設施，於兩個暴露工作目錄發現Webshell、Pass-the-Hash RDP與跨平台植入程式等實際攻擊痕跡 | 未具名受害系統 | PtH RDP嘗試為高信心；是否成功未能確認 | 未歸因 | 🟢高 | [ahnlab.com](https://www.ahnlab.com/en/contents/content-center/36373) |
| [KR-13](countries/south-korea/README.md) | 2026-11-04 | 韓國 | 🧨 Hunt.io：自開放目錄揭露韓國銀行攻擊的香港跳板伺服器，含Claude Code設定、模型路由shim與19個代理技能 | 韓國金融機構（延伸至加密貨幣與行動裝置相關工具，關聯未證實） | —（基礎設施分析） | 中國（說中文，Recorded Future稱TAG-217） | 🟢高 | [hunt.io](https://hunt.io/blog/artex-south-korea-bank-infrastructure) |
| [KR-14](countries/south-korea/README.md) | 2026-11-22 | 韓國 | 🧨 S2W：攻擊者「KimJEN」入侵國內約20所大學研究行政／會計系統，外洩檔案留有ARTEX及其衍生工具Prtseek痕跡 | 國內約20所大學（研究行政、會計系統）及公共機關 | 帳號、帳戶資訊等敏感資料遭竊（規模未公布） | 未歸因（工具與中國駭客社群相關；攻擊者自稱歐洲籍） | 🟡中 | [yna.co.kr](https://www.yna.co.kr/view/AKR20261120131200017) |
| [IN-05](countries/india/README.md) | 2026-11-05 | 印度 | CERT-In命名「Crafty Falcon」：以ARTEX、PentAGI、Cairn、CyberStrikeAI以「機器速度」入侵印度非銀行放貸、金融科技與加密貨幣交易所 | 印度NBFC、金融科技、加密貨幣交易所 | CERT-In未公布損失；路透另報兩家孟買NBFC於10/8–9經ICICI帳戶700餘筆即時轉帳損失約200萬美元（未確認關聯） | 中國（工具來源；攻擊者未歸因） | 🟡中 | [business-standard.com](https://www.business-standard.com/industry/news/china-linked-tools-used-in-ai-driven-cyberattacks-on-indian-financial-firms-126110500996_1.html) |
| [US-08](countries/united-states/README.md) | 2026-10-21 | 美國 | Microsoft：中國國家關聯Storm-0940以ARTEX代理框架自動化攻擊數百組織，並造成ConnectWise供應鏈入侵 | 全球數百組織（航太國防、能源、金融、政府、半導體等）；ConnectWise Cloud Backup合作夥伴與客戶 | 嘗試登入逾2,250個雲端租戶（The Register）；ConnectWise停用7個應用身分 | 中國（國家關聯：Storm-0940） | 🟢高 | [microsoft.com](https://www.microsoft.com/en-us/security/blog/2026/10/21/storm-0940-uses-artex-agentic-ai-connectwise-supply-chain-compromise/)<br>[connectwise.com](https://www.connectwise.com/company/trust/advisories)<br>[theregister.com](https://www.theregister.com/security/2026/10/22/microsoft-says-connectwise-breach-let-chinese-spies-loose-on-2250-cloud-tenants/5304687) |
| [US-17](countries/united-states/README.md) | 2026-10-22 | 美國 | 🧨 Wiz：ARTEX使用者（重疊Storm-0940）擴大鎖定IT與軟體供應商，攻擊Okta、Entra與Cognito | 多家IT與軟體供應商（未具名） | 多數嘗試失敗；部分工作階段持續24–30小時 | 中國（國家關聯；與微軟Storm-0940重疊） | 🟢高 | [wiz.io](https://www.wiz.io/blog/artex-in-the-wild-storm-0940-expands-targeting-of-it-and-software-vendors) |
| [US-18](countries/united-states/README.md) | 2026-11-04 | 美國 | 🧨 Kernel公告資安事件：外洩API金鑰遭濫用，攻擊者存取日誌供應商與GPU伺服器並植入挖礦程式，公司研判以ARTEX為指揮中心 | Kernel（瀏覽器基礎設施新創）及其客戶 | 約0.28%客戶受影響 | 未歸因 | 🟡中 | [kernel.sh](https://www.kernel.sh/blog/public-notice-of-security-incident-nov-4-2026) |
| [US-13](countries/united-states/README.md) | 2026-11-05 | 美國 | Microsoft：攻擊者以ARTEX代理框架搜尋GitHub外洩的OAuth應用程式密鑰，進而入侵Entra租戶 | 多個Microsoft Entra租戶組織 | —（未公布受害數） | 未歸因 | 🟢高 | [microsoft.com](https://www.microsoft.com/en-us/security/blog/2026/11/05/threat-actors-use-agentic-ai-tooling-to-find-and-abuse-exposed-secrets/) |
| [US-19](countries/united-states/README.md) | 2026-11-06 | 美國 | 🧨 WorkOS更新事件報告：安全研究員的ARTEX代理逃出基準測試沙箱，以弱憑證登入內部業務工具大量下載資料 | WorkOS內部go-to-market工具（CRM聯絡人、客戶往來紀錄） | CRM聯絡人與客戶通訊紀錄遭下載 | 未歸因（研究人員之代理失控，非惡意行動者） | 🟢高 | [workos.com](https://workos.com/security/bulletins/update-for-october-30th-2026-data-security-incident)<br>[bleepingcomputer.com](https://www.bleepingcomputer.com/news/security/runaway-ai-hacking-agent-behind-workos-breach-after-escaping-sandbox/) |
| [US-20](countries/united-states/README.md) | 2026-11-11 | 美國 | 🧨 Barracuda：竊得某AI廠商雲端金鑰的ARTEX式攻擊，44小時內存取約10個雲端帳號 | Barracuda雲端環境（約10個帳號）；XDR整合憑證可能外洩 | 要求客戶輪替XDR整合憑證 | 未歸因 | 🟢高 | [blog.barracuda.com](https://blog.barracuda.com/2026/11/11/anatomy-of-a-machine-speed-intrusion)<br>[bleepingcomputer.com](https://www.bleepingcomputer.com/news/security/barracuda-links-cloud-breach-to-artex-ai-powered-cyberattack/)<br>[trust.barracuda.com](https://trust.barracuda.com/security/barracuda-xdr-integration-credentials) |
| [US-16](countries/united-states/README.md) | 2026-11-13 | 美國 | FBI FLASH-20261113-001：ARTEX自主滲透框架威脅概覽，公布24個IP、網域與LLM API主機等IOC | 美國及多國組織；韓國金融機構；ConnectWise下游逾2,250個租戶遭嘗試登入 | 韓國金融機構約6.7萬人個資外洩（FBI引述） | 中國（工具開發來源；多個使用者） | 🟢高 | [ic3.gov](https://www.ic3.gov/CSA/2026/261113.pdf)<br>[ic3.gov](https://www.ic3.gov/CSA/2026/261113.csv)<br>[ithome.com.tw](https://www.ithome.com.tw/news/180508) |
| [CA-01](countries/canada/README.md) | 2026-09-29 | 加拿大 | 加拿大網安中心：聯邦政府網站遭可疑活動（含疑似AI代理）掃描；追蹤ARTEX、CyberStrikeAI、PentAGI等AI攻擊工具 | 加拿大政府網站與多產業組織 | —（未確認入侵） | 未歸因 | 🟢高 | [cyber.gc.ca](https://www.cyber.gc.ca/en/news-events/cyber-threat-actors-increasingly-use-automated-ai-enabled-tools-cyber-attacks) |
| [CA-02](countries/canada/README.md) | 2026-10-21 | 加拿大 | 🧨 加拿大網安中心網路威脅快報：代理式AI加速網路攻擊（Storm-0940／ARTEX） | 加拿大組織 | —（快報） | 中國（國家關聯Storm-0940，引述微軟） | 🟢高 | [cyber.gc.ca](https://www.cyber.gc.ca/en/guidance/cyber-threat-bulletin-agentic-artificial-intelligence-accelerating-cyber-attacks) |
| [UK-04](countries/united-kingdom/README.md) | 2026-10-24 | 英國 | 英國進入警戒：評估北京支持的Storm-0940 AI駭客行動對英國的影響 | 英國組織 | — | 中國（國家關聯：Storm-0940） | 🟡中 | [telegraph.co.uk](https://www.telegraph.co.uk/business/2026/10/24/uk-on-alert-over-beijing-backed-ai-hacking-spree/) |
| [NL-01](countries/netherlands/README.md) | 2026-09-29 | 荷蘭 | 荷蘭弱點揭露研究所DIVD遭AI代理自主入侵，攻擊「吵雜且非常混亂」 | DIVD（非營利資安組織） | 影響仍在調查；已通報警方、個資主管機關與NCSC | 未歸因 | 🟢高 | [bleepingcomputer.com](https://www.bleepingcomputer.com/news/security/automated-ai-agent-used-to-breach-cybersecurity-nonprofit-divd/)<br>[divd.nl](https://www.divd.nl/hacked/) |
| [EU-02](countries/eu/README.md) | 2026-11-05 | 歐盟 | CERT-EU發布「從滲透測試到網路威脅：當心ARTEX」 | 歐盟機構 | —（警示） | — | 🟢高 | [cert.europa.eu](https://cert.europa.eu/blog/from-penetration-testing-to-cyber-threat-beware-of-artex) |
| [EU-03](countries/eu/README.md) | 2026-11-19 | 歐盟 | 歐盟執委會證實遭「AI工具」網攻：10/22偵測、10/26確認，人事系統Sysper與醫療報銷等應用下線多日 | 歐盟執委會 | 多個應用下線；尚無員工資料外洩證據；已通報EDPS | 未歸因（Politico稱使用ARTEX） | 🟢高 | [infosecurity-magazine.com](https://www.infosecurity-magazine.com/news/commission-ai-attack-systems/)<br>[heise.de](https://www.heise.de/news/Cyberangriff-auf-EU-Kommission-Verdacht-auf-KI-Tool-Artex-tagelange-Ausfaelle-11531596.html)<br>[therecord.media](https://therecord.media/european-commission-confirms-cyberattack-using-ai)<br>[euronews.com](https://www.euronews.com/2026/11/19/eu-commission-hit-by-large-scale-cyberattack-with-data-leakage-unknown)<br>[boannews.com](https://www.boannews.com/news/articleView.html?idxno=147398) |
| [GL-35](countries/global/README.md) | 2026-10-21 | 全球 | 🧨 Zscaler ThreatLabz：韓國金融攻擊者的ARTEX環境揭示全球多產業攻擊，結合Claude Code、Codex與Grok工作區 | 全球多國、多產業組織（含韓國金融業） | 財務動機的資料竊取 | 中國（說中文的操作者） | 🟢高 | [zscaler.com](https://www.zscaler.com/blogs/security-research/inside-global-ai-assisted-hacking-campaign) |
| [GL-26](countries/global/README.md) | 2026-10-29 | 全球 | CrowdStrike：VAPOR PANDA以ARTEX＋DeepSeek在11天內對14國逾200個組織同時發動間諜入侵，部署BLOODALCHEMY後門 | 拉美兩國外交部、中東內政部、歐洲某國（希臘政府機關等）、美國19個製藥／半導體／國防／核能／金融組織、美比菲電信業者；韓國智庫與外交機構 | 9個組織確認後滲透；另至少12個組織遭密碼噴灑；單一入侵消耗約14億輸入token | 中國（國家關聯：VAPOR PANDA） | 🟢高 | [crowdstrike.com](https://www.crowdstrike.com/en-us/blog/vapor-panda-uses-artex-to-scale-global-campaign/)<br>[fnnews.com](https://www.fnnews.com/news/202611171157279340) |
| [GL-36](countries/global/README.md) | 2026-10-30 | 全球 | 🧨 Google GTIG／Mandiant「ARTEX and Friends」：代理式攻擊框架登場，UNC7228最快15分鐘取得深層存取 | 美國、歐洲多產業組織 | 深層存取、資料竊取與勒索 | 中國（UNC7228與Storm-0940重疊）；另有財務動機勒索者 | 🟢高 | [cloud.google.com](https://cloud.google.com/blog/topics/threat-intelligence/artex-and-friends-enter-agentic-offensive-frameworks) |
| [GL-33](countries/global/README.md) | 2026-11-05 | 全球 | Check Point：ARTEX犯罪行動內幕，10個暴露實例鎖定程式碼簽章服務與遊戲帳號 | 多國企業 | — | 未歸因（財務動機） | 🟢高 | [research.checkpoint.com](https://research.checkpoint.com/2026/hacking-on-autopilot-inside-artex-cybercrime-campaigns/) |
| [GL-37](countries/global/README.md) | 2026-11-05 | 全球 | 🧨 Censys：全球1,465個暴露ARTEX控制台（約815個獨立主機），155個同時託管其他威脅基礎設施 | —（基礎設施普查） | — | 未歸因（多數控制台位於美國、香港、中國） | 🟢高 | [censys.com](https://censys.com/blog/artex-agentic-asbestos/) |
| [GL-38](countries/global/README.md) | 2026-11-06 | 全球 | 🧨 Microsoft：ARTEX濫用擴大，柬埔寨據點的Storm-3358鎖定東南亞金融機構 | 東南亞金融機構及部分大型跨國組織 | — | 柬埔寨（Storm-3358，財務動機） | 🟢高 | [microsoft.com](https://www.microsoft.com/en-us/security/blog/2026/11/06/artex-abuse-expands-as-cybercriminals-target-financial-sector/) |
| [GL-39](countries/global/README.md) | 2026-11-09 | 全球 | 🧨 Datadog：ARTEX於AWS環境的野外活動——以外洩長期金鑰搜尋CloudWatch財務資料、濫用公開Cognito使用者池自助註冊 | 多個AWS客戶環境（未具名） | 部分列舉因權限不足失敗 | 未歸因（控制台多為中文、託管於新加坡與香港） | 🟢高 | [securitylabs.datadoghq.com](https://securitylabs.datadoghq.com/articles/artex-agentic-attacks-aws-environments/) |
| [GL-40](countries/global/README.md) | 2026-11-10 | 全球 | 🧨 Sophos X-Ops：少數客戶出現與ARTEX相符活動，發布檢測名稱、IPS特徵與主機狩獵指標 | 少數Sophos客戶（未具名） | 數百筆防護事件 | 中國（引述微軟Storm-0940） | 🟢高 | [sophos.com](https://www.sophos.com/en-us/blog/artex-attackers-apply-agentic-ai) |
| [GL-11](countries/global/README.md) | 2026-11-13 | 全球 | Bitrise揭露遭ARTEX代理攻擊：利用無2FA的閒置測試帳號，10小時內串連竊得憑證存取原始碼與基礎設施 | Bitrise（行動應用CI/CD平台）與15個客戶工作區 | 15個客戶工作區檔案遭未授權存取；撤銷919把雲端服務帳號金鑰、重建上千台伺服器 | 未歸因 | 🟢高 | [bitrise.io](https://bitrise.io/artex-incident-report) |
| [GL-41](countries/global/README.md) | 2026-11-13 | 全球 | 🧨 Amazon威脅情報：MadPot蜜罐擷取ARTEX代理作戰記憶，揭露工業規模AI憑證竊取與加密貨幣交易所深偽KYC繞過 | 全球暴露的AI應用平台與閘道；2家加密貨幣交易所 | AWS已通知可能受影響客戶 | 中國關聯（中度信心，多個不同群體） | 🟢高 | [aws.amazon.com](https://aws.amazon.com/blogs/security/amazon-threat-intelligence-observes-threat-actors-running-cybercrime-campaigns-with-artex-ai-agents/) |
| [GL-42](countries/global/README.md) | 2026-11-13 | 全球 | 🧨 SentinelOne：ARTEX解密——至少5個行動者／群集、每次行動模型成本約145–1,500美元 | 全球多產業 | — | 中國關聯；柬埔寨（Storm-3358）等至少5個行動者 | 🟢高 | [sentinelone.com](https://www.sentinelone.com/blog/artex-unmasked-the-rise-of-ai-powered-artex-in-cybercrime-espionage/) |
| [GL-43](countries/global/README.md) | 2026-11-13 | 全球 | 🧨 Cisco Talos威脅通報：ARTEX及其他AI滲透測試平台的野外濫用 | — | —（通報） | — | 🟢高 | [blog.talosintelligence.com](https://blog.talosintelligence.com/artex-and-beyond/) |

### 疑似同波（`ARTEX?`，未證實使用 ARTEX，不計入統計）

| ID | 日期 | 國家 | 事件 | 為何列為疑似 | 可信度 |
|---|---|---|---|---|---|
| [TW-20](countries/taiwan/README.md) | 2026-09-23 | 台灣 | 🧨 健身工廠營運商柏文：委外廠商對外服務系統遭「自動化攻擊」，客戶資料表遭分頁擷取 | 與ARTEX的關聯未經官方或鑑識報告證實，僅因時間、手法與資安院所述同波攻擊相符而列入「疑似」 | 🔴低 |
| [TW-21](countries/taiwan/README.md) | 2026-09-29 | 台灣 | 🧨 神腦國際：外部伺服器遭「自動化攻擊」，部分訂單資訊遭擷取 | 與ARTEX的關聯未經證實（疑似同波） | 🔴低 |
| [JP-10](countries/japan/README.md) | 2026-10-09 | 日本 | 國家網路統括室（NCO）發布注意喚起：國內組織接連遭不正存取，要求各機關與重要基礎設施業者緊急點檢 | 依NCO 10/26閣僚會議資料所載時間軸 | 🟢高 |
| [JP-08](countries/japan/README.md) | 2026-10-28 | 日本 | 日本政府網安閣僚會議：AI疑被用於大規模掃描網站竊取個資；Macnica統計今年216起外洩為去年2.6倍 | 佐川急便、Capcom、樂天旅遊等個案企業未公開確認使用AI，故不另列；國家網路統括室（NCO）10/26會議資料：2026年資料外洩明顯增加、10月Web系統相關案件激增，研判攻擊者「標的の調査や侵害にＡＩを使用している可能性は高い」；時間軸：10/6大臣指示、10/8跨部會會議、10/9 NCO注意喚起 | 🟢高 |
| [JP-14](countries/japan/README.md) | 2026-11-06 | 日本 | 警察廳長官就「濫用高度技術的不正存取」導致大規模個資外洩發布指示，要求各縣警強化偵查與企業支援 | AI關聯依NCO、JPCERT同期資料推定 | 🟢高 |
| [KR-09](countries/south-korea/README.md) | 2026-10-28 | 韓國 | 大信證券3.8萬客戶個資外洩、未來資產運用與Bithumb群組軟體外洩；金監院長示警AI攻擊可能常態化 | AI參與為主管機關脈絡判斷，個案未逐一確認 | 🟡中 |
| [KR-05](countries/south-korea/README.md) | 2026-11-05 | 韓國 | 金融委員會：9/30–11/3共37家金融公司通報40起駭侵，外洩約47.3萬筆；啟動約580家金融業者全面檢查 | 官方新聞稿標題提及AI；個別事件是否皆為AI攻擊未逐一確認 | 🟢高 |
| [US-12](countries/united-states/README.md) | 2026-10-21 | 美國 | Railway雲端平台遭入侵，攻擊者鎖定客戶環境變數中的AI供應商金鑰，造成約74萬美元未授權AI用量 | Barracuda 11/11稱其遭入侵手法與Railway事件相似、疑似同為ARTEX；Railway本身未證實 | 🟢高 |

> 另：台灣科懋生技（10/22，委外電商平台遭「自動化攻擊」）、Cyberbiz、1shop、莫筆克、meepShop、易遊網等同期外洩案，及日本佐川急便、Capcom、樂天旅遊等案，**均未見 ARTEX 或 AI 關聯之公開證實**，故未收錄。

## 四、時間軸

- **2026-09-23**｜台灣｜[TW-20](countries/taiwan/README.md)｜🧨 （疑似）健身工廠營運商柏文：委外廠商對外服務系統遭「自動化攻擊」，客戶資料表遭分頁擷取
- **2026-09-29**｜加拿大｜[CA-01](countries/canada/README.md)｜加拿大網安中心：聯邦政府網站遭可疑活動（含疑似AI代理）掃描；追蹤ARTEX、CyberStrikeAI、PentAGI等AI攻擊工具
- **2026-09-29**｜荷蘭｜[NL-01](countries/netherlands/README.md)｜荷蘭弱點揭露研究所DIVD遭AI代理自主入侵，攻擊「吵雜且非常混亂」
- **2026-09-29**｜台灣｜[TW-21](countries/taiwan/README.md)｜🧨 （疑似）神腦國際：外部伺服器遭「自動化攻擊」，部分訂單資訊遭擷取
- **2026-10-03**｜韓國｜[KR-10](countries/south-korea/README.md)｜🧨 金融保安院：逆向追蹤新韓銀行日誌與攻擊IP，確認銀行連環駭侵使用ARTEX
- **2026-10-04**｜韓國｜[KR-07](countries/south-korea/README.md)｜科技部／KISA發布企業資安強化緊急勸告並將網路威脅警戒升至「注意」，向約2.8萬家企業建議點檢
- **2026-10-07**｜韓國｜[KR-02](countries/south-korea/README.md)｜CrowdStrike：未具名攻擊者以中國開發的ARTEX代理框架＋Claude Code攻擊韓國金融機構並外洩資料
- **2026-10-08**｜日本｜[JP-06](countries/japan/README.md)｜JPCERT/CC注意喚起：國內組織連續遭不正存取外洩個資，新增「濫用AI滲透測試平台（Cairn、CyberStrikeAI、ARTEX）」攻擊案例
- **2026-10-09**｜中國｜[CN-13](countries/china/README.md)｜🧨 ARTEX中國開發者於工具遭用於攻擊韓國銀行後宣布轉為閉源
- **2026-10-09**｜日本｜[JP-10](countries/japan/README.md)｜（疑似）國家網路統括室（NCO）發布注意喚起：國內組織接連遭不正存取，要求各機關與重要基礎設施業者緊急點檢
- **2026-10-13**｜韓國｜[KR-11](countries/south-korea/README.md)｜🧨 S2W：韓國金融業遭攻擊所用之ARTEX初步分析（功能、工作流程與偵測建議）
- **2026-10-14**｜韓國｜[KR-08](countries/south-korea/README.md)｜金融委員會／金融監督院第二次緊急會議：16家金融公司遭駭、約10萬筆外洩；555家點檢中130家有缺失
- **2026-10-19**｜日本｜[JP-13](countries/japan/README.md)｜GMO Cybersecurity：相次ぐ不正存取的攻擊源多為AI，確認使用中國開發的ARTEX；單一攻擊源鎖定約20家日本企業
- **2026-10-21**｜台灣｜[TW-11](countries/taiwan/README.md)｜資安署示警「新型態AI攻擊」：韓、日、法案例顯示LLM＋Agent＋自動化滲透工具大幅提升攻擊效率
- **2026-10-21**｜美國｜[US-08](countries/united-states/README.md)｜Microsoft：中國國家關聯Storm-0940以ARTEX代理框架自動化攻擊數百組織，並造成ConnectWise供應鏈入侵
- **2026-10-21**｜加拿大｜[CA-02](countries/canada/README.md)｜🧨 加拿大網安中心網路威脅快報：代理式AI加速網路攻擊（Storm-0940／ARTEX）
- **2026-10-21**｜全球｜[GL-35](countries/global/README.md)｜🧨 Zscaler ThreatLabz：韓國金融攻擊者的ARTEX環境揭示全球多產業攻擊，結合Claude Code、Codex與Grok工作區
- **2026-10-21**｜美國｜[US-12](countries/united-states/README.md)｜（疑似）Railway雲端平台遭入侵，攻擊者鎖定客戶環境變數中的AI供應商金鑰，造成約74萬美元未授權AI用量
- **2026-10-22**｜台灣｜[TW-12](countries/taiwan/README.md)｜91APP訂單資料庫遭AI自動化滲透工具（ARTEX）入侵
- **2026-10-22**｜美國｜[US-17](countries/united-states/README.md)｜🧨 Wiz：ARTEX使用者（重疊Storm-0940）擴大鎖定IT與軟體供應商，攻擊Okta、Entra與Cognito
- **2026-10-24**｜英國｜[UK-04](countries/united-kingdom/README.md)｜英國進入警戒：評估北京支持的Storm-0940 AI駭客行動對英國的影響
- **2026-10-26**｜韓國｜[KR-03](countries/south-korea/README.md)｜首爾警方：非資工背景者以生成式AI與「AI自律滲透測試系統」入侵90餘家機構竊取820萬筆個資並勒索
- **2026-10-28**｜日本｜[JP-08](countries/japan/README.md)｜（疑似）日本政府網安閣僚會議：AI疑被用於大規模掃描網站竊取個資；Macnica統計今年216起外洩為去年2.6倍
- **2026-10-28**｜韓國｜[KR-09](countries/south-korea/README.md)｜（疑似）大信證券3.8萬客戶個資外洩、未來資產運用與Bithumb群組軟體外洩；金監院長示警AI攻擊可能常態化
- **2026-10-29**｜韓國｜[KR-04](countries/south-korea/README.md)｜Microsoft：北韓8個駭客組織AI採用程度分級，3組已將AI納入日常作業，大量量產針對南韓的釣魚文件
- **2026-10-29**｜全球｜[GL-26](countries/global/README.md)｜CrowdStrike：VAPOR PANDA以ARTEX＋DeepSeek在11天內對14國逾200個組織同時發動間諜入侵，部署BLOODALCHEMY後門
- **2026-10-30**｜韓國｜[KR-12](countries/south-korea/README.md)｜🧨 AhnLab ASEC：追蹤ARTEX基礎設施，於兩個暴露工作目錄發現Webshell、Pass-the-Hash RDP與跨平台植入程式等實際攻擊痕跡
- **2026-10-30**｜全球｜[GL-36](countries/global/README.md)｜🧨 Google GTIG／Mandiant「ARTEX and Friends」：代理式攻擊框架登場，UNC7228最快15分鐘取得深層存取
- **2026-11-04**｜韓國｜[KR-13](countries/south-korea/README.md)｜🧨 Hunt.io：自開放目錄揭露韓國銀行攻擊的香港跳板伺服器，含Claude Code設定、模型路由shim與19個代理技能
- **2026-11-04**｜美國｜[US-18](countries/united-states/README.md)｜🧨 Kernel公告資安事件：外洩API金鑰遭濫用，攻擊者存取日誌供應商與GPU伺服器並植入挖礦程式，公司研判以ARTEX為指揮中心
- **2026-11-05**｜印度｜[IN-05](countries/india/README.md)｜CERT-In命名「Crafty Falcon」：以ARTEX、PentAGI、Cairn、CyberStrikeAI以「機器速度」入侵印度非銀行放貸、金融科技與加密貨幣交易所
- **2026-11-05**｜美國｜[US-13](countries/united-states/README.md)｜Microsoft：攻擊者以ARTEX代理框架搜尋GitHub外洩的OAuth應用程式密鑰，進而入侵Entra租戶
- **2026-11-05**｜歐盟｜[EU-02](countries/eu/README.md)｜CERT-EU發布「從滲透測試到網路威脅：當心ARTEX」
- **2026-11-05**｜全球｜[GL-33](countries/global/README.md)｜Check Point：ARTEX犯罪行動內幕，10個暴露實例鎖定程式碼簽章服務與遊戲帳號
- **2026-11-05**｜全球｜[GL-37](countries/global/README.md)｜🧨 Censys：全球1,465個暴露ARTEX控制台（約815個獨立主機），155個同時託管其他威脅基礎設施
- **2026-11-05**｜韓國｜[KR-05](countries/south-korea/README.md)｜（疑似）金融委員會：9/30–11/3共37家金融公司通報40起駭侵，外洩約47.3萬筆；啟動約580家金融業者全面檢查
- **2026-11-06**｜中國｜[CN-14](countries/china/README.md)｜🧨 微步在線（ThreatBook）發表ARTEX著作權聲明：稱源自旗下威脅偵測工程師個人專案，ARTEX Pro僅經RedAgents平台銷售
- **2026-11-06**｜美國｜[US-19](countries/united-states/README.md)｜🧨 WorkOS更新事件報告：安全研究員的ARTEX代理逃出基準測試沙箱，以弱憑證登入內部業務工具大量下載資料
- **2026-11-06**｜全球｜[GL-38](countries/global/README.md)｜🧨 Microsoft：ARTEX濫用擴大，柬埔寨據點的Storm-3358鎖定東南亞金融機構
- **2026-11-06**｜日本｜[JP-14](countries/japan/README.md)｜（疑似）警察廳長官就「濫用高度技術的不正存取」導致大規模個資外洩發布指示，要求各縣警強化偵查與企業支援
- **2026-11-09**｜全球｜[GL-39](countries/global/README.md)｜🧨 Datadog：ARTEX於AWS環境的野外活動——以外洩長期金鑰搜尋CloudWatch財務資料、濫用公開Cognito使用者池自助註冊
- **2026-11-10**｜全球｜[GL-40](countries/global/README.md)｜🧨 Sophos X-Ops：少數客戶出現與ARTEX相符活動，發布檢測名稱、IPS特徵與主機狩獵指標
- **2026-11-11**｜台灣｜[TW-14](countries/taiwan/README.md)｜資安署：國際AI網攻波及台灣十餘家企業與平台，逾百萬份個資受影響，近半數涉及AI／ARTEX
- **2026-11-11**｜美國｜[US-20](countries/united-states/README.md)｜🧨 Barracuda：竊得某AI廠商雲端金鑰的ARTEX式攻擊，44小時內存取約10個雲端帳號
- **2026-11-13**｜美國｜[US-16](countries/united-states/README.md)｜FBI FLASH-20261113-001：ARTEX自主滲透框架威脅概覽，公布24個IP、網域與LLM API主機等IOC
- **2026-11-13**｜全球｜[GL-11](countries/global/README.md)｜Bitrise揭露遭ARTEX代理攻擊：利用無2FA的閒置測試帳號，10小時內串連竊得憑證存取原始碼與基礎設施
- **2026-11-13**｜全球｜[GL-41](countries/global/README.md)｜🧨 Amazon威脅情報：MadPot蜜罐擷取ARTEX代理作戰記憶，揭露工業規模AI憑證竊取與加密貨幣交易所深偽KYC繞過
- **2026-11-13**｜全球｜[GL-42](countries/global/README.md)｜🧨 SentinelOne：ARTEX解密——至少5個行動者／群集、每次行動模型成本約145–1,500美元
- **2026-11-13**｜全球｜[GL-43](countries/global/README.md)｜🧨 Cisco Talos威脅通報：ARTEX及其他AI滲透測試平台的野外濫用
- **2026-11-19**｜歐盟｜[EU-03](countries/eu/README.md)｜歐盟執委會證實遭「AI工具」網攻：10/22偵測、10/26確認，人事系統Sysper與醫療報銷等應用下線多日
- **2026-11-22**｜韓國｜[KR-14](countries/south-korea/README.md)｜🧨 S2W：攻擊者「KimJEN」入侵國內約20所大學研究行政／會計系統，外洩檔案留有ARTEX及其衍生工具Prtseek痕跡

補充關鍵時點（出自上列報告）：2026-07-26 首次提交 → 8 月起惡意使用（FBI；Zscaler 所見提示紀錄始於 8/4 UTC）→ 8/18 跳板 38.244.50[.]120 已暴露（Censys）→ 9/3 百度賽事奪冠 → 9/21 DIVD 遭入侵 → 9/27–10/1 韓國銀行攻擊高峰（金融保安院）→ 10/3 91APP 遭入侵 → 10/7 CrowdStrike 揭露 → 10/8 轉閉源 → 10/15–16 ConnectWise 下游 162 個租戶遭未授權登入（Huntress） → 10/22 歐盟執委會偵測入侵 → 11/1–2 Barracuda 44 小時入侵 → 11/12 起韓國大學遭攻擊（KimJEN 自稱）→ 11/13 FBI FLASH、AWS、SentinelOne 報告 → 11/19 歐盟執委會證實。

## 五、受害國家與產業統計（由第三節「具體攻擊／入侵／分析」33 件計算）

### 受害國家涵蓋（主檔＋受波及，一事件可計入多國；「全球」不計）

| 國家 | 事件數 |
|---|---|
| 韓國 | 12 |
| 美國 | 9 |
| 日本 | 3 |
| 台灣 | 2 |
| 印度 | 1 |
| 加拿大 | 1 |
| 荷蘭 | 1 |
| 歐盟 | 1 |
| 菲律賓 | 1 |

### 受害產業（依各事件受害對象與原報告逐件歸類，一事件可屬多類；分析／基礎設施報告亦計入其所述目標產業）

| 產業 | 事件數 | 事件 ID |
|---|---|---|
| 金融／保險／證券／加密貨幣 | 12 | JP-13、KR-10、KR-02、KR-08、KR-04、KR-13、IN-05、US-08、US-16、GL-35、GL-38、GL-41 |
| 軟體／IT／雲端／SaaS | 12 | KR-04、US-08、US-17、US-18、US-13、US-19、US-20、US-16、GL-36、GL-33、GL-39、GL-11 |
| 政府／公部門／國際組織 | 7 | KR-14、US-08、US-16、CA-01、EU-03、GL-26、GL-36 |
| 電商／零售／消費服務 | 3 | TW-12、TW-14、JP-13 |
| 教育／學術 | 3 | JP-13、KR-03、KR-14 |
| 製造／半導體／化工／製藥 | 3 | US-08、GL-26、GL-36 |
| 資安組織／資安廠商 | 2 | US-20、NL-01 |
| AI平台／LLM閘道 | 1 | GL-41 |
| 電信 | 1 | GL-36 |
| 能源／航太國防 | 1 | US-08 |
| 醫療 | 1 | KR-03 |
| 媒體／物流 | 1 | JP-13 |
| 遊戲 | 1 | GL-33 |
| 未具名／多產業 | 6 | JP-06、KR-03、KR-12、GL-35、GL-40、GL-42 |

### 依事件類別與可信度

| 類別 | 件數 |
|---|---|
| AI代理自動化入侵 | 31 |
| 政府警示/評估報告 | 10 |
| AI輔助攻擊/惡意程式 | 1 |
| 針對AI系統/平台的攻擊 | 1 |

### 已公開的受害規模（僅列官方或受害方公布數字）

| 事件 | 數字 | ID |
|---|---|---|
| 韓國首爾警方破獲 | 90 餘家業者、約 820 萬筆個資，並勒索 | KR-03 |
| 台灣 91APP | 最多 1,329 個品牌、4,798,255 名消費者 | TW-12 |
| 台灣資安署彙整 | 十餘家企業、逾 100 萬份個資 | TW-14 |
| 韓國銀行（金融保安院） | 新韓 25,729、KB 119、韓亞 89、BNK 11 人 | KR-10 |
| 韓國金融委（9/30–11/3，未逐案證實為 ARTEX） | 37 家、40 起、約 47.3 萬筆 | KR-05（疑似） |
| ConnectWise 供應鏈 | 嘗試登入逾 2,250 個租戶；Huntress 確認 162 個租戶遭未授權登入 | US-08 |
| VAPOR PANDA | 14 國逾 200 個組織（11 天內） | GL-26 |
| Check Point／SentinelOne | 逾 300 張程式碼簽章憑證、逾 19 萬筆遊戲帳密（約 6,000 筆有效） | GL-33、GL-42 |
| Barracuda | 約 10 個雲端帳號、44 小時 | US-20 |
| Kernel | 約 0.28% 客戶 | US-18 |

## 六、公開 IOC（已去武化）

> ⚠️ 以下 IOC 皆摘自官方或廠商公開報告，可能已失效或被重新分配（雲端／代理 IP 尤其如此），**僅供查核自身日誌**，請勿直接據以封鎖或指控。UA 與 IP 容易更換，宜結合行為偵測。

### FBI FLASH-20261113-001（[US-16](countries/united-states/README.md)，[PDF](https://www.ic3.gov/CSA/2026/261113.pdf)、[CSV](https://www.ic3.gov/CSA/2026/261113.csv)）

- IP（24 個）：`38[.]244[.]50[.]120`、`144[.]172[.]64[.]60`、`144[.]172[.]64[.]99`、`144[.]172[.]64[.]128`、`187[.]15[.]88[.]186`、`187[.]15[.]90[.]217`、`187[.]15[.]89[.]186`、`101[.]53[.]80[.]20`、`205[.]214[.]59[.]31`、`124[.]155[.]252[.]63`、`154[.]201[.]79[.]246`、`23[.]248[.]249[.]90`、`23[.]158[.]220[.]98`、`103[.]248[.]148[.]84`、`203[.]160[.]133[.]172`、`209[.]209[.]85[.]38`、`199[.]19[.]95[.]66`、`199[.]19[.]95[.]67`、`199[.]19[.]95[.]68`、`91[.]92[.]240[.]238`、`85[.]11[.]168[.]45`、`178[.]16[.]54[.]129`、`31[.]77[.]229[.]35`、`85[.]11[.]167[.]52`
- 網域：`xcai[.]pro`（LLM 轉售閘道）
- 外連 LLM API 主機（合法服務，僅作情境判斷）：`api[.]anthropic[.]com`、`api[.]deepseek[.]com`、`open[.]bigmodel[.]cn`、`api[.]x[.]ai`

### 其他官方／廠商公開 IOC

| 來源 | 類型 | 指標 | ID |
|---|---|---|---|
| Microsoft（Storm-3358） | WISP C2 | `199.19.95[.]66`、`199.19.95[.]67`、`199.19.95[.]68` | GL-38 |
| Microsoft（Storm-3358） | ARTEX 伺服器 | `91.92.240[.]238`、`85.11.168[.]45`、`178.16.54[.]129`、`31.77.229[.]35` | GL-38 |
| Microsoft（Storm-3358） | C2 | `85.11.167[.]52` | GL-38 |
| Microsoft／Wiz（Storm-0940） | IP | `144.172.64[.]60`、`144.172.64[.]99`、`144.172.64[.]128`；Wiz 另列 `104.194.150[.]21`、`167.88.172[.]97` | US-08、US-17 |
| Zscaler／Hunt.io（韓國金融攻擊） | 跳板／工作伺服器 | `38.244.50[.]120`（跳板）、`23.248.226[.]250`–`254`（工作伺服器，香港）、`154.201.79[.]246:443`（代理池 API）、`205.214.59[.]31:443`、`161.8.161[.]140:11005`（上游 SOCKS） | GL-35、KR-13 |
| JPCERT/CC 事例E（10/23 更新） | 攻擊來源 IP | `31.59.92[.]155`、`31.56.206[.]187`、`38.244.50[.]120`、`46.8.227[.]73`、`64.44.24[.]195`、`94.183.184[.]98`、`94.183.184[.]254`、`95.182.99[.]112`、`176.65.144[.]71` | JP-06 |
| Datadog／SentinelOne | ARTEX 活動 IP | `169.128.55[.]214`、`154.64.252[.]77`、`154.36.136[.]197`、`154.36.136[.]23`、`102.216.154[.]102`、`82.158.88[.]233`、`88.229.22[.]232`、`103.54.154[.]40`、`103.54.154[.]32`、`45.145.228[.]25` | GL-39、GL-42 |
| SentinelOne | 開放目錄 | `118.107.47[.]11`、`212.129.221[.]26`、`149.88.85[.]20`、`23.248.226[.]250`、`156.251.11[.]39`、`130.94.31[.]86`、`202.95.14[.]60` | GL-42 |
| SentinelOne | 網域 | `fofoapi[.]com`、`u6ud2s.dnslog[.]cn` | GL-42 |
| WorkOS | IP | `154.64.252[.]77`、`183.1.65[.]106`、`95.169.20[.]166`、`203.190.1[.]60`；IPv6 `240e:3b2:1959:e4b0:b282:e2ff:fe48:d1ca`、`240e:3b2:195a:8b20:b282:e2ff:fe48:d1ca` | US-19 |
| WorkOS | JA4 | `t13d3013h1_1d37bd780c83_8537cf56674e`、`t13d3013h2_1d37bd780c83_8537cf56674e`、`t13d3014h1_1d37bd780c83_5ae85263eb3b` | US-19 |
| Amazon（MadPot，行動1） | IP | `104.28.225[.]223`、`31.22.91[.]156`、`150.136.38[.]110`、`128.242.115[.]131`、`216.176.239[.]231` | GL-41 |
| Amazon（MadPot，行動2） | IP | `212.107.28[.]51`、`103.142.140[.]158`、`104.28.251[.]98`、`104.28.251[.]99`、`104.28.219[.]97`、`125.103.213[.]41` | GL-41 |
| CrowdStrike（VAPOR PANDA） | C2 網域 | `nginxmysql[.]com`、`sqlserver-sqlite[.]com`、`www[.]ddduuuppp[.]com` | GL-26 |

### User-Agent、映像檔與主機標記

| 類型 | 指標 | 來源 |
|---|---|---|
| User-Agent | `artex-readonly/1.0`、`artex-pentest/1.0`、`artex-audit/1.0`、`artex-spawn/1`、`artex-verify/1.0`、`ARTEX-worker/1.0`、`artex-i21861-canary`、`Mozilla/5.0 ARTeX`、`Mozilla/5.0 (Windows NT 10.0; Win64; x64) ARTeX-authorized-pentest` | Datadog、SentinelOne |
| User-Agent | `Mozilla/5.0 (compatible; ArtEx/1.0)`、`Mozilla/5.0 (compatible; infra-hunt/1.0)`、`artex-enrich/1.0`、`norma/0.4`、`verify-911-probe/1.0`、`ReconProbe/1.0` | WorkOS、Wiz |
| 遭植入後門的 Docker 映像 | `tomicdd/artex`、`congdonglinux/artex`（Sophos 偵測名 Troj/Bckdr-SDA） | SentinelOne、Sophos |
| TLS 憑證 | 簽發者「ARTEX」（SHA-256 前綴 `C7A884AF…`，完整值見 SentinelOne 原文） | SentinelOne |
| 控制台指紋 | 頁面標題 `ARTEX — 自主渗透测试控制台`（或 ScopeWeaver／LUCK／觀瀾SEC 等別名）＋ `_next/static`；預設埠 8787（亦見 8790、443） | Censys、Datadog |
| 主機檔案 | `i<數字>_<變體>.ps1`（如 `i12345_b2.ps1`）、`C:\Windows\Temp\artx*`；指令中含 `MARKER123`／`ARTX123` 驗證標記 | Sophos |
| 行為基準探測 | 請求不存在路徑 `/zzz-nonexistent-xyz123`；S3 物件 `zzz_nonexistent_abc.txt`、`Notexist-xyz` | Wiz、Datadog |
| 雲端日誌特徵 | `FilterLogEvents` 固定 `limit=1000`、匿名 S3 `GetObject`／`ListObjects` 開場、Cognito `SignUp` 大量失敗（PreSignUp 錯誤） | Datadog |

## 七、偵測與緩解建議（摘自官方／廠商通報，僅限防禦）

| 來源 | 重點建議 |
|---|---|
| 台灣資安院（[TW-14](countries/taiwan/README.md)） | ① 下線閒置系統與不必要對外連線（必要時暫時限制國際連線）② 強制登出所有帳號、要求員工改密碼 ③ 監控資料庫存取、阻擋異常大量讀取；資安署另要求盤點 VPN、遠端桌面、NAS 等對外服務並指定負責人 |
| 韓國 FSI／S2W | 全面點檢員工與合作廠商用的對外系統（本波攻擊主要打內部員工系統而非網銀）；以 WAF／IPS 阻擋已知漏洞利用；以 ARTEX 管理頁標題與登入頁雜湊監測暴露基礎設施；限制伺服器上不必要的腳本執行 |
| 日本 JPCERT/CC、NCO | 緊急點檢公開 Web 系統與 APP 後端 API、修補已知漏洞、啟用 MFA、檢視委外系統；遭害時主動分享手法 |
| FBI FLASH | 以公布之 IP／網域查核日誌；監控異常的 LLM API 外連；縮短漏洞修補時間；強化憑證管理 |
| 加拿大網安中心 | 抗釣魚 MFA、最小權限、審查第三方應用程式授權、修補、完整日誌、事前授權的隔離程序、離線備份 |
| Google GTIG | 控制平面隔離、短期憑證、最小權限、網段隔離、行為式偵測（短時間大量指令爆發）、監控外連（如 webhook.site） |
| Microsoft／Sophos | 稽核 Entra ID 服務主體與企業應用程式，檢視 2026-09 以來所有憑證新增與角色指派；對工作負載身分套用條件式存取；對腳本型 UA 的應用程式登入與異常驗證失敗率告警；以 playbook 自動停用服務主體、撤銷憑證；自家紅隊若使用代理框架，應向 SOC 登記其基礎設施 |
| Datadog | 先以 UA、已知 IP 狩獵；再找大量 AccessDenied、跨區列舉、EC2 角色憑證自非 AWS IP 使用、S3 大量列舉；輪替／移除長期 IAM 金鑰；公開 Cognito 池檢視 PreSignUp 與已驗證角色權限 |
| Amazon | 假設外洩的金鑰與設定錯誤會被很快找到；把 AI 應用、模型閘道與推論端點納入正式環境同等控管；監控 AI 服務異常花費 |
| AhnLab | 狩獵 PowerShell 執行原則繞過、編碼指令、異常腳本檔、Pass-the-Hash 遠端存取、經 CIM/WMI 的 PowerShell、可疑程序外連與隧道 |
| WorkOS（自身教訓） | 研究／測試用代理必須真正隔離網路；移除可預測的開發憑證；為內部工具加上速率限制與遙測 |

## 八、相關 AI 攻擊框架比較（僅依本資料集收錄之公開報告）

| 框架 | 性質 | 本資料集所見特徵 | 野外濫用事件 |
|---|---|---|---|
| **ARTEX** | 開源（後轉閉源）多代理自主滲透框架，中國開發 | Planner／Worker＋圖狀共享記憶；多 LLM 切換；網頁控制台大量暴露 | 本頁 43 件 |
| **Cairn**（CAIRN） | 自主攻擊框架，調度／黑板架構 | Unit 42：CL-STA-1238 客製化版本＋「AIScan Runner Skills」，使用 GLM 5.2、DeepSeek V4；附偽造授權文件 AUTHORIZATION.md | JP-06、IN-05、US-06、US-07、US-14、GL-23 |
| **CyberStrikeAI** | 開源多代理攻防平台 | 趨勢科技：簡體中文控制台、44 個角色代理全程自動化（偵察至外傳與報告）；AhnLab 發現部分 ARTEX 基礎設施同時運行 | JP-06、JP-17、IN-05、CA-01、GL-32 |
| **PentAGI** | 開源自主滲透系統（VXControl） | 加拿大網安中心：全球觀測之 AI 攻擊工具基礎設施約 14%；GTIG 與 CERT-In 亦點名 | IN-05、CA-01 |
| **Strix** | 開源 AI 資安測試代理 | Gambit：與 Cairn、Hermes 串接入侵數百家電商、竊取 60 萬筆信用卡 | US-06 |
| **OpenClaw**（「龍蝦」）／**Hermes** | 通用 AI 代理（非專門攻擊框架），具高權限、可自主運作與技能擴充 | 台灣政府機關遭以 OpenClaw／Hermes「近乎自主」攻擊；OpenClaw 技能市集遭投毒；Unit 42：BUGSTER 以 Hermes 規劃攻擊 | TW-06、IN-04、US-06 |
| Hexstrike | MCP 型攻擊工具整合 | GTIG「ARTEX and Friends」一併分析 | （GL-36 內文） |

> 共通點：各報告一致指出，這些框架**沒有發明新技術**，入口仍是未修補的公開系統、預設／外洩憑證與設定錯誤；改變的是**速度、規模、持續性與門檻**。差異在於：ARTEX 與 CyberStrikeAI 提供完整網頁控制台、易於多人共用與大規模部署（因此暴露最多）；Cairn 常見於國家關聯的客製化行動；OpenClaw／Hermes 屬通用代理被挪用。

## 九、未解問題與資料缺口

1. **台灣受害名單不完整**：資安署稱十餘家、近半數涉及 AI／ARTEX，但除 91APP 外，其餘企業未公開點名；柏文、神腦等「自動化攻擊」案是否為 ARTEX 尚無證實。
2. **中國官方立場缺席**：未找到 CNCERT、CVERC、奇安信、360 針對 ARTEX 的專門分析；僅微步在線著作權聲明與技術社群文章。
3. **攻擊者歸因分歧**：Storm-0940 被評為中國國家關聯，但 ARTEX 同時被韓國國內犯罪者、柬埔寨犯罪集團、北韓組織使用；單憑「出現 ARTEX」不能推定國籍。
4. **日本規模不一**：GMO 稱單一來源約 20 家、日經稱 6 台伺服器鎖定約 80 家（付費牆未能全文核對）；個別企業（佐川、Capcom 等）未確認 AI 關聯。
5. **韓國數字口徑**：金融委 37 家 40 起、約 47.3 萬筆為所有駭侵通報，非全為 ARTEX；FBI 稱韓國金融約 6.7 萬人個資外洩，與金融保安院「不到 2.6 萬人」（10/3 時點）不同。
6. **歐盟執委會**：發言人僅證實「AI 工具」，ARTEX 之說出自 Politico 等媒體與 CERT-EU 背景說明。
7. **研究用代理失控**：WorkOS 事件的 IP（154.64.252[.]77）同時出現在 Datadog／SentinelOne 的 ARTEX IOC 清單，該 IP 是否代表同一研究者或共用代理基礎設施，尚待釐清。
8. **衍生版本追蹤**：ARTEX PRO、ARTEX v2、Prtseek、ScopeWeaver 等分支的功能差異與維護者尚無完整公開分析。
9. **未搜得**：香港 HKCERT、新加坡 CSA、澳洲 ASD 針對 ARTEX 的專門通報；TeamT5 僅見於媒體引述、NICT 僅見於二手報導，未找到原始報告。
10. **時效**：韓國大學案（KR-14）為 11/22 最新報導，僅單一廠商分析，後續官方調查結果待追蹤。

---
資料產生時間：2026-11-22（台北時間）。連結檢查結果見 [`sources.md`](sources.md)。
