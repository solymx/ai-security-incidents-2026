# 韓國：2026年AI相關資安事件

[← 回到總覽](../../README.md)

🆕＝2026-11-21第二版新增（9–11月深度擴充）；🧨＝2026-11-22第三版新增（ARTEX專題，見[artex.md](../../artex.md)）；🧠＝2026-11-24第四版新增（AI模型專題，見[models.md](../../models.md)）；🔄＝第二／三版補充細節；`ARTEX`等標籤＝涉及之AI攻擊框架（`ARTEX?`＝同波疑似、未證實）。

本國為主要受害方／發布國之事件：**14 件**；本國為歸因來源之跨國事件：**0 件**；本國受波及之跨國事件：**4 件**。資料期間 2026-01-01 至 2026-11-22，依日期排序。

## 事件列表

| ID | 日期 | 事件 | 類別 | 手法／AI角色 | 受害對象 | 影響 | 歸因來源 | 可信度 | 來源 |
|---|---|---|---|---|---|---|---|---|---|
| KR-01 | 2026-07-30 | 科技部／KISA《2026上半年網路威脅動向》：生成式AI與AI代理擴大攻擊面，提示注入、權限濫用成新威脅 | 政府警示/評估報告 | AI加速漏洞探索、補丁前後比對、攻擊程式草擬；AI代理連接郵件、程式庫、雲端，帶來提示注入、權限濫用、敏感資訊外洩 | 韓國企業 | 上半年KISA受理侵害事故1,236件（年增19.5%，非全屬AI） | — | 🟢高 | [eiec.kdi.re.kr](https://eiec.kdi.re.kr/policy/materialView.do?num=284894)<br>[edaily.co.kr](https://www.edaily.co.kr/News/Read?mediaCodeNo=257&newsId=04598566645519768) |
| KR-10 | 2026-10-03 | 🧨 `ARTEX` 金融保安院：逆向追蹤新韓銀行日誌與攻擊IP，確認銀行連環駭侵使用ARTEX | AI代理自動化入侵 | 攻擊集中於9/27–10/1；多個IP輪替、各銀行重疊2–3個；攻擊流量含ARTEX發出的特定資料，可據以辨識；鎖定員工／合作廠商用系統而非網銀；FSI稱為「駭客使用AI工具」而非AI獨立攻擊 | 新韓（貸款招攬人查詢服務2萬5,729人）、KB國民（員工行動業務系統119人）、韓亞（員工營業支援系統89人）、BNK釜山（外包人員11人）；友利、NH農協遭攻擊但未受害；另2家儲蓄銀行調查中 | 已確認外洩不到2萬6千人；金融委將建議全面點檢內部員工用系統 | 未歸因（攻擊來自海外） | 🟡中 | [biz.heraldcorp.com](https://biz.heraldcorp.com/article/10892496) |
| KR-07 | 2026-10-04 | 🆕 `ARTEX` 科技部／KISA發布企業資安強化緊急勸告並將網路威脅警戒升至「注意」，向約2.8萬家企業建議點檢 | 政府警示/評估報告 | 因應金融機構接連遭AI滲透工具攻擊，要求檢查外部API、員工系統、雲端權限與已知漏洞 | 韓國企業（約2.8萬家） | —（警示） | — | 🟡中 | [fnnews.com](https://www.fnnews.com/news/202610041204270490)<br>[etnews.com](https://www.etnews.com/20261004000031) |
| KR-02 | 2026-10-07 | 🔄 `ARTEX` CrowdStrike：未具名攻擊者以中國開發的ARTEX代理框架＋Claude Code攻擊韓國金融機構並外洩資料 | AI代理自動化入侵 | ARTEX以DeepSeek v4.1-flash為主要LLM，輔以GLM-5.3與Grok 4.6；暴露的伺服器含Claude Code工作階段紀錄與中文滲透提示詞；攻破銀行貸款查詢服務與員工行動工作系統 | 新韓、KB國民、韓亞等至少9家韓國銀行（路透） | 資料外洩；部分系統中斷（確切筆數未公開） | 中國（說中文者，可能位於廣東；中度信心） | 🟢高 | [crowdstrike.com](https://www.crowdstrike.com/en-us/blog/unknown-threat-actor-uses-artex-to-target-south-korean-finance/)<br>[reuters.com](https://www.reuters.com/3fec1b0a85a0/world/suspect-behind-south-korea-bank-hacks-may-be-26-year-old-china-cybersecurity-2026-10-08/)<br>[en.yna.co.kr](https://en.yna.co.kr/view/AEN20261008002200320)<br>[zscaler.com](https://www.zscaler.com/blogs/security-research/threat-actor-abuses-agentic-ai-pentesting-framework-target-south-korean)<br>[recordedfuture.com](https://www.recordedfuture.com/blog/tag-217-artex-south-korean-banks)<br>[datanet.co.kr](https://www.datanet.co.kr/news/articleView.html?idxno=300166) |
| KR-11 | 2026-10-13 | 🧨 `ARTEX` S2W：韓國金融業遭攻擊所用之ARTEX初步分析（功能、工作流程與偵測建議） | 政府警示/評估報告 | 解析ARTEX：目標拆解代理、Planner產生intent、Worker執行工具；執行控制（允許／阻擋／需人工核准）、資產範圍控制、HTTP(S)流量錄製、MCP／Skill擴充、每任務／代理設定LLM | 韓國金融業 | —（分析報告） | 未歸因 | 🟢高 | [s2w.inc](https://www.s2w.inc/en/resources/1128) |
| KR-08 | 2026-10-14 | 🆕 `ARTEX` 金融委員會／金融監督院第二次緊急會議：16家金融公司遭駭、約10萬筆外洩；555家點檢中130家有缺失 | AI代理自動化入侵 | 同一使用AI工具的攻擊者被認定涉及其中7家（10/4確認）；攻擊經外部API與員工系統等接點 | 新韓、KB、韓亞、BNK等銀行，Yegaram、Welcome、OK等儲蓄銀行，現代Capital、MG中央會、PFCT、Mouda、DB儲蓄銀行、KDB Capital、Streami（Gopax）等16家 | 約10萬筆個資外洩；555家中130家點檢不合格 | 中國（說中文者；同一AI工具攻擊者，非正式歸因） | 🟡中 | [yna.co.kr](https://www.yna.co.kr/view/AKR20261014134851002) |
| KR-03 | 2026-10-26 | 🔄 `ARTEX` 首爾警方：非資工背景者以生成式AI與「AI自律滲透測試系統」入侵90餘家機構竊取820萬筆個資並勒索 | AI代理自動化入侵 | 主嫌自2026年8月底起以生成式AI擴大無差別入侵；並使用近期金融業個資外洩案所用之AI自律滲透測試系統；以外洩恐致罰款為由勒索 | 補習班、醫院、高爾夫球場、大學、大企業子公司等90餘家 | 820萬筆個資外洩；其中60家以AI入侵；向38家勒索3.6億韓元 | — | 🟡中 | [yna.co.kr](https://www.yna.co.kr/view/AKR20261026075100004)<br>[ithome.com.tw](https://www.ithome.com.tw/news/179973)<br>[bleepingcomputer.com](https://www.bleepingcomputer.com/news/security/former-pentester-used-artex-ai-to-steal-82-million-data-records/)<br>[edaily.co.kr](https://www.edaily.co.kr/News/Read?newsId=02955286645616856) |
| KR-09 | 2026-10-28 | 🆕 `ARTEX?` 大信證券3.8萬客戶個資外洩、未來資產運用與Bithumb群組軟體外洩；金監院長示警AI攻擊可能常態化 | AI代理自動化入侵 | 大信證券經外部APP開戶連動伺服器外洩（10/17偵測）；10/21自北韓IP段出現約440萬次掃描（未正式歸因） | 大信證券客戶38,490人、未來資產運用、Bithumb | 大信證券38,490人個資外洩 | 未歸因（北韓IP段大量掃描，非歸因） | 🟡中 | [etoday.co.kr](https://www.etoday.co.kr/news/view/2641245) |
| KR-04 | 2026-10-29 | `ARTEX` Microsoft：北韓8個駭客組織AI採用程度分級，3組已將AI納入日常作業，大量量產針對南韓的釣魚文件 | AI輔助攻擊/惡意程式 | Jade、Coral、Jasper Sleet已「作業化」；Onyx Sleet量產逾百份客製PDF誘餌；Onyx與Pearl Sleet使用ARTEX代理滲透框架；AI用於偵察、假人設、惡意程式開發 | 南韓使用者、加密貨幣與軟體開發生態 | — | 北韓 | 🟢高 | [microsoft.com](https://www.microsoft.com/en-us/security/blog/2026/10/29/tracking-ai-adoption-in-north-korean-threat-actor-tradecraft/)<br>[news.sbs.co.kr](https://news.sbs.co.kr/english/article.do?news_id=N1008823304) |
| KR-12 | 2026-10-30 | 🧨 `ARTEX` AhnLab ASEC：追蹤ARTEX基礎設施，於兩個暴露工作目錄發現Webshell、Pass-the-Hash RDP與跨平台植入程式等實際攻擊痕跡 | AI代理自動化入侵 | ASEC自10/1起追蹤，首份分析找出約600個相關IP（部分同時運行CyberStrikeAI）；第二份發現以Planner調度多Worker的「ARTEX v2」；第三份分析兩個工作目錄：ASPX Webshell、反向TCP中繼至內網RDP、以NTLM雜湊PtH登入、PowerShell代理、內網掃描、JVM heap dump憑證擷取、Rust/Go植入程式與反向SOCKS | 未具名受害系統 | PtH RDP嘗試為高信心；是否成功未能確認 | 未歸因 | 🟢高 | [ahnlab.com](https://www.ahnlab.com/en/contents/content-center/36373) |
| KR-13 | 2026-11-04 | 🧨 `ARTEX` Hunt.io：自開放目錄揭露韓國銀行攻擊的香港跳板伺服器，含Claude Code設定、模型路由shim與19個代理技能 | AI代理自動化入侵 | 23.248.226[.]250（香港）開放目錄含指向ARTEX控制台38.244.50[.]120的腳本、反向SSH隧道、同步程式、DeepSeek／GLM／Grok路由元件、FOFA工具、代理池154.201.79[.]246:443（100個身分中有79個出口IP）、JNDI/LDAP分段利用與Linux提權工具 | 韓國金融機構（延伸至加密貨幣與行動裝置相關工具，關聯未證實） | —（基礎設施分析） | 中國（說中文，Recorded Future稱TAG-217） | 🟢高 | [hunt.io](https://hunt.io/blog/artex-south-korea-bank-infrastructure) |
| KR-05 | 2026-11-05 | `ARTEX?` 金融委員會：9/30–11/3共37家金融公司通報40起駭侵，外洩約47.3萬筆；啟動約580家金融業者全面檢查 | AI代理自動化入侵 | 主管機關以「AI時代侵害威脅」為題提出全金融圈資安革新方案；攻擊多經外部接點（API、員工系統） | 韓國37家金融公司 | 約47.3萬筆個資外洩、約10億韓元資金遭竊（媒體報導） | — | 🟢高 | [fsc.go.kr](https://www.fsc.go.kr/no010101/88086)<br>[fnnews.com](https://www.fnnews.com/news/202611050900563434) |
| KR-06 | 2026-11-16 | 韓國造幣公社「chak」地方商品券平台遭API認證漏洞攻擊，3,083人個資外洩，公社推估為AI攻擊 | AI代理自動化入侵 | 未直接入侵伺服器，而是利用伺服器間通訊API之認證漏洞查詢客戶資料；手法與近期銀行、證券被攻擊類似 | chak平台用戶（平台約430萬人） | 3,083人個資外洩（姓名、生日、手機、帳號、CI、Email、加密卡號） | — | 🟡中 | [yna.co.kr](https://www.yna.co.kr/view/AKR20261116074700063) |
| KR-14 | 2026-11-22 | 🧨 `ARTEX/Prtseek` S2W：攻擊者「KimJEN」入侵國內約20所大學研究行政／會計系統，外洩檔案留有ARTEX及其衍生工具Prtseek痕跡 | AI代理自動化入侵 | KimJEN自11/12起宣稱入侵大學與公共機關並於Telegram公開資料；遭竄改網頁HTML留有Prtseek中文註解；外洩資料含ARTEX作業路徑、作業ID與疑似AI代理撰寫的滲透報告；S2W發現中國駭客社群用戶「黃豆」參與Prtseek開發，但未證實參與本次攻擊；KimJEN否認使用ARTEX | 國內約20所大學（研究行政、會計系統）及公共機關 | 帳號、帳戶資訊等敏感資料遭竊（規模未公布） | 未歸因（工具與中國駭客社群相關；攻擊者自稱歐洲籍） | 🟡中 | [yna.co.kr](https://www.yna.co.kr/view/AKR20261120131200017) |

## 事件補充說明

- **KR-10**：Herald經濟獨家，引述金融保安院人士；FSI與警方共享攻擊者IP
- **KR-07**：媒體轉述官方
- **KR-02**：Zscaler ThreatLabz（10/14）另行分析同一攻擊；Recorded Future將攻擊者命名為TAG-217（說中文），稱其自8月即開始準備工具；FBI 11/13 FLASH稱韓國金融機構約6.7萬人個資遭外洩
- **KR-11**：建議以ARTEX管理頁HTML標題與登入頁內容雜湊監測暴露基礎設施；全文需申請
- **KR-08**：韓聯社轉述金融當局；11/05金融委新聞稿彙總為37家40起（另列）
- **KR-03**：韓聯社轉述首爾警察廳；警方稱為國內首例；iThome報導指嫌犯使用的AI自律滲透測試系統即ARTEX；BleepingComputer：警方共查獲7名嫌犯，ARTEX用於多數攻擊
- **KR-09**：AI參與為主管機關脈絡判斷，個案未逐一確認
- **KR-12**：ASEC強調工具存在、執行證據、攻擊成功與歸因須分開評估
- **KR-13**：發布前已通知相關國家CERT
- **KR-05**：官方新聞稿標題提及AI；個別事件是否皆為AI攻擊未逐一確認
- **KR-06**：AI使用為受害方推估
- **KR-14**：單一廠商分析經韓聯社報導（2026-11-22 06:15 KST）；尚無官方證實

## 交叉引用：涉及韓國的跨國／他國事件

以下事件主檔在他國或「全球」，但韓國為受害方或攻擊目標之一。

| ID | 日期 | 主檔 | 事件 | 可信度 |
|---|---|---|---|---|
| TW-14 | 2026-11-11 | [台灣](../taiwan/README.md) | 資安署：國際AI網攻波及台灣十餘家企業與平台，逾百萬份個資受影響，近半數涉及AI／ARTEX | 🟢高 |
| US-16 | 2026-11-13 | [美國](../united-states/README.md) | FBI FLASH-20261113-001：ARTEX自主滲透框架威脅概覽，公布24個IP、網域與LLM API主機等IOC | 🟢高 |
| GL-35 | 2026-10-21 | [全球](../global/README.md) | Zscaler ThreatLabz：韓國金融攻擊者的ARTEX環境揭示全球多產業攻擊，結合Claude Code、Codex與Grok工作區 | 🟢高 |
| GL-26 | 2026-10-29 | [全球](../global/README.md) | CrowdStrike：VAPOR PANDA以ARTEX＋DeepSeek在11天內對14國逾200個組織同時發動間諜入侵，部署BLOODALCHEMY後門 | 🟢高 |

