# 韓國：2026年AI相關資安事件

[← 回到總覽](../../README.md)

本國為主要受害方／發布國之事件：**6 件**；本國為歸因來源之跨國事件：**0 件**。資料期間 2026-01-01 至 2026-11-21，依日期排序。

## 事件列表

| ID | 日期 | 事件 | 類別 | 手法／AI角色 | 受害對象 | 影響 | 歸因來源 | 可信度 | 來源 |
|---|---|---|---|---|---|---|---|---|---|
| KR-01 | 2026-07-30 | 科技部／KISA《2026上半年網路威脅動向》：生成式AI與AI代理擴大攻擊面，提示注入、權限濫用成新威脅 | 政府警示/評估報告 | AI加速漏洞探索、補丁前後比對、攻擊程式草擬；AI代理連接郵件、程式庫、雲端，帶來提示注入、權限濫用、敏感資訊外洩 | 韓國企業 | 上半年KISA受理侵害事故1,236件（年增19.5%，非全屬AI） | — | 🟢高 | [eiec.kdi.re.kr](https://eiec.kdi.re.kr/policy/materialView.do?num=284894)<br>[edaily.co.kr](https://www.edaily.co.kr/News/Read?mediaCodeNo=257&newsId=04598566645519768) |
| KR-02 | 2026-10-07 | CrowdStrike：未具名攻擊者以中國開發的ARTEX代理框架＋Claude Code攻擊韓國金融機構並外洩資料 | AI代理自動化入侵 | ARTEX以DeepSeek v4.1-flash為主要LLM，輔以GLM-5.3與Grok 4.6；暴露的伺服器含Claude Code工作階段紀錄與中文滲透提示詞；攻破銀行貸款查詢服務與員工行動工作系統 | 新韓、KB國民、韓亞等至少9家韓國銀行（路透） | 資料外洩；部分系統中斷（確切筆數未公開） | 中國（說中文者，可能位於廣東；中度信心） | 🟢高 | [crowdstrike.com](https://www.crowdstrike.com/en-us/blog/unknown-threat-actor-uses-artex-to-target-south-korean-finance/)<br>[reuters.com](https://www.reuters.com/3fec1b0a85a0/world/suspect-behind-south-korea-bank-hacks-may-be-26-year-old-china-cybersecurity-2026-10-08/)<br>[en.yna.co.kr](https://en.yna.co.kr/view/AEN20261008002200320) |
| KR-03 | 2026-10-26 | 首爾警方：非資工背景者以生成式AI與「AI自律滲透測試系統」入侵90餘家機構竊取820萬筆個資並勒索 | AI代理自動化入侵 | 主嫌自2026年8月底起以生成式AI擴大無差別入侵；並使用近期金融業個資外洩案所用之AI自律滲透測試系統；以外洩恐致罰款為由勒索 | 補習班、醫院、高爾夫球場、大學、大企業子公司等90餘家 | 820萬筆個資外洩；其中60家以AI入侵；向38家勒索3.6億韓元 | — | 🟡中 | [yna.co.kr](https://www.yna.co.kr/view/AKR20261026075100004) |
| KR-04 | 2026-10-29 | Microsoft：北韓8個駭客組織AI採用程度分級，3組已將AI納入日常作業，大量量產針對南韓的釣魚文件 | AI輔助攻擊/惡意程式 | Jade、Coral、Jasper Sleet已「作業化」；Onyx Sleet量產逾百份客製PDF誘餌；Onyx與Pearl Sleet使用ARTEX代理滲透框架；AI用於偵察、假人設、惡意程式開發 | 南韓使用者、加密貨幣與軟體開發生態 | — | 北韓 | 🟢高 | [microsoft.com](https://www.microsoft.com/en-us/security/blog/2026/10/29/tracking-ai-adoption-in-north-korean-threat-actor-tradecraft/)<br>[news.sbs.co.kr](https://news.sbs.co.kr/english/article.do?news_id=N1008823304) |
| KR-05 | 2026-11-05 | 金融委員會：9/30–11/3共37家金融公司通報40起駭侵，外洩約47.3萬筆；啟動約580家金融業者全面檢查 | AI代理自動化入侵 | 主管機關以「AI時代侵害威脅」為題提出全金融圈資安革新方案；攻擊多經外部接點（API、員工系統） | 韓國37家金融公司 | 約47.3萬筆個資外洩、約10億韓元資金遭竊（媒體報導） | — | 🟢高 | [fsc.go.kr](https://www.fsc.go.kr/no010101/88086)<br>[fnnews.com](https://www.fnnews.com/news/202611050900563434) |
| KR-06 | 2026-11-16 | 韓國造幣公社「chak」地方商品券平台遭API認證漏洞攻擊，3,083人個資外洩，公社推估為AI攻擊 | AI代理自動化入侵 | 未直接入侵伺服器，而是利用伺服器間通訊API之認證漏洞查詢客戶資料；手法與近期銀行、證券被攻擊類似 | chak平台用戶（平台約430萬人） | 3,083人個資外洩（姓名、生日、手機、帳號、CI、Email、加密卡號） | — | 🟡中 | [yna.co.kr](https://www.yna.co.kr/view/AKR20261116074700063) |

## 事件補充說明

- **KR-03**：韓聯社轉述首爾警察廳；警方稱為國內首例
- **KR-05**：官方新聞稿標題提及AI；個別事件是否皆為AI攻擊未逐一確認
- **KR-06**：AI使用為受害方推估

