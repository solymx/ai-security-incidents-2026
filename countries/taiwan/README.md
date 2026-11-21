# 台灣：2026年AI相關資安事件

[← 回到總覽](../../README.md)

🆕＝2026-11-21第二版新增（9–11月深度擴充）；🔄＝第二版補充細節。

本國為主要受害方／發布國之事件：**19 件**；本國為歸因來源之跨國事件：**2 件**；本國受波及之跨國事件：**2 件**。資料期間 2026-01-01 至 2026-11-21，依日期排序。

> ⚠️ 資料限制：9–11月已逐週檢視資安署、國安局、調查局、刑事局／警政署、iThome與中央社；部分廠商研究（Vulone、GreyNoise）點名之台灣受害機關未見官方證實，標示為中可信度。

## 事件列表

| ID | 日期 | 事件 | 類別 | 手法／AI角色 | 受害對象 | 影響 | 歸因來源 | 可信度 | 來源 |
|---|---|---|---|---|---|---|---|---|---|
| TW-01 | 2026-01-06 | 國安局：中共對台軍演期間以「AI生成影音」擴大認知作戰並同步網攻政府機關 | AI認知作戰/影響力行動 | 軍演期間（2025/12/29–2026/1/2）運用官媒渲染、影片剪接、AI生成造假影音、盜用帳號與網軍推宣；同時對政府網路服務發動網駭（APT24、BlackTech最活躍） | 台灣民眾、政府機關網路服務 | 爭議訊息逾1.9萬則、異常帳號799組；演習首日網駭約208萬次、第2日約209萬次 | 中國 | 🟢高 | [cna.com.tw](https://www.cna.com.tw/news/aipl/202601060164.aspx)<br>[ppg.ly.gov.tw](https://ppg.ly.gov.tw/ppg/SittingAttachment/download/2026010209/00510670316930022002.pdf) |
| TW-02 | 2026-01-11 | 國安局發布「2025年中共對台認知作戰操作手法分析」：AI生成擬真影音、誘騙台灣民眾錄音以合成聲紋 | AI認知作戰/影響力行動 | 中國兵器工業集團等開發AI模型自動生成影音並精準投放；委託晴數智慧、科大訊飛開發語音系統，在台灣網站刊廣告誘騙民眾錄音，恐用於合成偽冒聲線 | 台灣民眾與輿論環境 | 2025年查報逾4.5萬組異常帳號、逾231.4萬則爭議訊息（報告涵蓋2025年度） | 中國 | 🟡中 | [cna.com.tw](https://www.cna.com.tw/news/aipl/202601110031.aspx) |
| TW-03 | 2026-02-15 | 刑事局警示：詐團以深偽／AI生成名人影像與聲音推薦投資（AI偽冒名人報牌） | 深偽詐騙/語音複製 | 以深偽或AI生成技術偽造知名企業家、財經名人、股票分析師的影像與聲音，在臉書、IG、YouTube、LINE投放廣告，引導加LINE群組、下載假投資APP | 台灣網路使用者 | 114年全年通報下架逾8萬則詐騙廣告（非全屬AI深偽，未單獨統計） | — | 🟢高 | [cib.npa.gov.tw](https://www.cib.npa.gov.tw/ch/app/news/view?id=1887&module=news&serno=2ada7b37-da8a-44cf-851e-f0e8efa8240e) |
| TW-04 | 2026-03-25 | 資安署警示：AI代理（OpenClaw「龍蝦」）成資安破口，提出五項防護 | 政府警示/評估報告 | AI代理具高權限與24小時自主運作；風險含外部網頁藏惡意指令（間接提示注入）、第三方Skill技能包藏惡意程式、長時間運作記憶壓縮遺失安全規則；引述ClawJacked漏洞CVE-2026-25253 | 導入AI代理的機關、企業與個人 | —（警示） | — | 🟢高 | [moda.gov.tw](https://moda.gov.tw/ACS/press/news/press/19294) |
| TW-05 | 2026-04-06 | 🔄 國安局向立法院報告：中共結合AI深偽、假民調與爭議訊息干擾九合一選舉 | AI認知作戰/影響力行動 | 預判中共以AI深偽造假影音、假民調、爭議訊息介入2026年11月地方選舉 | 台灣選舉與選民 | 2026年1–3月蒐獲異常帳號1萬3,000餘組、爭議訊息86萬餘則；政府服務網（GSN）第1季遭侵擾約1億7,328萬次 | 中國 | 🟢高 | [ppg.ly.gov.tw](https://ppg.ly.gov.tw/ppg/SittingAttachment/download/2026033105/84201600173026605003.pdf)<br>[cna.com.tw](https://www.cna.com.tw/news/aipl/202604060105.aspx) |
| TW-06 | 2026-08-13 | 境外駭客以AI代理（OpenClaw／Hermes）「近乎自主」攻擊台灣政府機關，並擴及核安機關與能源業 | AI代理自動化入侵 | 以開源Hermes與OpenClaw建構多代理攻擊框架，7/1–7/4共12波；反編譯政府入口網站JS取出API端點、OAuth/Keycloak設定，繪出21個系統SSO架構；找到免驗證API、AI破解CAPTCHA、依員工編號規律密碼噴灑；再平行掃描IT供應商、核安機關、7家以上能源業者 | 台灣政府機關（含核安機關）、政府IT供應商、能源業者 | 據Dream報告：破解85個政府帳號、外洩逾2,564筆人事資料、7組SSO client secret、6組資料庫憑證；數發部稱受影響單位已完成處置 | 中國（疑似，未正式歸因） | 🟢高 | [moda.gov.tw](https://moda.gov.tw/ACS/press/news/press/20394)<br>[ithome.com.tw](https://www.ithome.com.tw/news/178105)<br>[theregister.com](https://www.theregister.com/security/2026/08/12/near-autonomous-ai-agents-attack-taiwans-nuclear-safety-agency/5287055) |
| TW-07 | 2026-08-25 | TeamT5：中國國家級駭客導入DeepSeek等開源AI後攻擊量倍增，並用於攻擊台灣企業 | AI輔助攻擊/惡意程式 | Grimfengxi以DeepSeek生成漏洞利用程式；Huapi疑以DeepSeek攻擊台灣某公司電子郵件系統；Teleboyi蒐集1,000個IP並梳理網域；Slime22以Claude Code在台灣科技公司內橫向移動；CyCraft另觀察到以ChatGPT協助解密Signal資料庫 | 台灣企業（未具名）等 | 攻擊數量增加一倍以上（TeamT5說法，未公布基準） | 中國 | 🟡中 | [ctee.com.tw](https://www.ctee.com.tw/news/20260825701003-430804)<br>[zaobao.com.sg](https://www.zaobao.com.sg/news/china/story20260825-9569718)<br>[ithome.com.tw](https://www.ithome.com.tw/news/178135) |
| TW-08 | 2026-09-02 | 🔄 刑事局破獲「AI變聲」假交友詐欺集團：被害逾2萬人、詐得逾9億元 | 深偽詐騙/語音複製 | 詐團以美女照片經營交友帳號，工程師設計AI變聲軟體偽裝女聲，誘使被害人購物、贈禮、付費 | 台灣民眾（逾2萬人） | 犯罪所得逾新台幣9億元；起訴57人，查扣現金、超跑，扣押不動產與帳戶約3億元 | — | 🟢高 | [cib.npa.gov.tw](https://www.cib.npa.gov.tw/ch/app/news/view?id=1885&module=news&serno=2c6a4aa9-93d3-480b-a528-575268edbe28)<br>[news.pts.org.tw](https://news.pts.org.tw/article/825232)<br>[ettoday.net](https://www.ettoday.net/news/20260902/3230115.htm) |
| TW-09 | 2026-09-10 | 彰化縣長參選人陳素月遭AI深偽影片抹黑並付費投放廣告，競總報案 | AI認知作戰/影響力行動 | 以AI深偽變造影片，使候選人說出未曾說過的話，並透過社群付費廣告擴散 | 選舉候選人、選民 | —（報案階段，未公布散布規模） | — | 🟡中 | [cna.com.tw](https://www.cna.com.tw/news/aloc/202609100196.aspx) |
| TW-16 | 2026-09-20 | 🆕 資安署呼籲中小企業強化資安：導入代理式AI須設人工審核、最小化授權並完整留存日誌 | 政府警示/評估報告 | 針對代理式AI自動化工作流程，要求最小權限、完整操作日誌、最終動作由人工把關；禁止上傳機敏資料或原始碼至外部AI工具；同步推出中小企業資安健檢 | 台灣中小企業 | —（警示） | — | 🟢高 | [cna.com.tw](https://www.cna.com.tw/news/afe/202609200029.aspx) |
| TW-10 | 2026-10-20 | 國安局報告：中共網攻政府服務網7月暴增至1.856億次，AI用於找漏洞、零時差與郵件惡意程式；AI生成內容用於介選 | AI輔助攻擊/惡意程式 | AI用於探測弱點、選定目標、搜尋零時差漏洞與電子郵件惡意程式攻擊，自動化提高作業節奏；認知作戰使用AI生成影音與內容農場 | 台灣政府服務網（GSN）、學術、電信、國防供應鏈 | 7月網攻1.856億次；9月日均258萬次；1–9月可疑帳號貼文250萬則（年增48%） | 中國 | 🟡中 | [taipeitimes.com](https://www.taipeitimes.com/News/front/archives/2026/10/21/2003866334)<br>[cna.com.tw](https://www.cna.com.tw/news/aipl/202610200201.aspx) |
| TW-11 | 2026-10-21 | 資安署示警「新型態AI攻擊」：韓、日、法案例顯示LLM＋Agent＋自動化滲透工具大幅提升攻擊效率 | 政府警示/評估報告 | 說明AI紅隊工具於2026年7月公開後外流、滲透效率至少比人工快10倍（資安院實測）；國內7月監測到類似AI攻擊；呼籲縮小攻擊面、修補、MFA、零信任、EDR、3-2-1備份 | 台灣企業 | —（警示） | — | 🟢高 | [moda.gov.tw](https://moda.gov.tw/ACS/press/news/press/21130)<br>[ithome.com.tw](https://www.ithome.com.tw/news/179865) |
| TW-12 | 2026-10-22 | 🔄 91APP訂單資料庫遭AI自動化滲透工具（ARTEX）入侵 | AI代理自動化入侵 | 攻擊者以AI自動化工具（系統內發現ARTEX痕跡），經未更新套件的內部工具Appsmith進入內網，自GitLab取得資料庫金鑰後存取訂單資料庫。時間軸：10/3 11:00入侵、10/4首次接獲客戶通報、10/8成立緊急應變小組、10/9委由奧義智慧科技（CyCraft）鑑識、10/14 23:00完全阻斷、10/15通報主管機關；91APP稱工具鏈與韓、日同波攻擊相同 | 91APP Commerce Cloud品牌客戶與其消費者 | 最多1,329個品牌、4,798,255名消費者（2025/4/4–2026/10/14下單者）之姓名、電話、地址、Email與訂單紀錄；不含信用卡；下游品牌（如全家「行動購」10/29、高林10/27）陸續公告；已衍生詐騙 | 中國（工具來源；攻擊者未歸因） | 🟢高 | [cna.com.tw](https://www.cna.com.tw/news/afe/202610220434.aspx)<br>[91app.com](https://91app.com/91app-202610-security-incident/)<br>[taipeitimes.com](https://www.taipeitimes.com/News/taiwan/archives/2026/11/12/2003867610)<br>[ir.91app.com](https://ir.91app.com/tw/news_detail.php?id=160)<br>[ir.91app.com](https://ir.91app.com/tw/news_detail.php?id=161)<br>[ithome.com.tw](https://www.ithome.com.tw/news/180112) |
| TW-13 | 2026-11-02 | 調查局查獲散布台北市長候選人「深偽音檔」影片男子，聲押禁見 | AI認知作戰/影響力行動 | 以深度偽造聲音捏造候選人「利用軍購案收回扣」之影音，於臉書及Threads散布；調查局以深偽鑑識軟體確認 | 台北市長候選人、選民 | 1人遭拘提並聲押禁見 | — | 🟢高 | [mjib.gov.tw](https://www.mjib.gov.tw/news/Details/1/1224)<br>[news.ltn.com.tw](https://news.ltn.com.tw/news/society/breakingnews/5624454) |
| TW-17 | 2026-11-06 | 🆕 高雄市警破獲38歲男子「透過AI學習」建置自動化網路攻擊系統，入侵網站後台竊取23萬餘筆個資販售 | AI輔助攻擊/惡意程式 | 嫌犯透過AI學習程式撰寫與網路架設，整合電腦與雲端儲存建置自動化網路攻擊系統，非法侵入網站後台竊取會員與客戶資料，於暗網兜售（含台、港、泰個資） | 台灣等地網站會員與客戶 | 23萬餘筆個資遭竊；10月搜索到案，依妨害電腦使用罪移送高雄地檢 | — | 🟢高 | [pbs.npa.gov.tw](https://www.pbs.npa.gov.tw/ch/app/data/view?id=18740&module=wg183&serno=1f102e1b-90e4-4126-b29d-c6f726478736) |
| TW-14 | 2026-11-11 | 🔄 資安署：國際AI網攻波及台灣十餘家企業與平台，逾百萬份個資受影響，近半數涉及AI／ARTEX | AI代理自動化入侵 | 境外駭客自7月以AI代理工具攻擊政府，近期擴及電商、網路商店；利用PHP、Node.js、GitLab已知高風險漏洞（部分列KEV）及高權限API；部分攻擊流量來自香港IP與多國跳板；同波攻擊亦衝擊日、韓。資安署宣布72小時內五項因應措施，資安院並導入4套美國AI資安模型協防 | 台灣十餘家企業與網路平台（官方未公布名單） | 逾100萬份個資（姓名、電話、Email、訂單），尚無付款資訊外洩、未見勒索；資料於暗網販售；規模較大者五、六家 | 中國（香港IP，未正式歸因） | 🟢高 | [moda.gov.tw](https://moda.gov.tw/ACS/press/news/press/21422)<br>[ec.ltn.com.tw](https://ec.ltn.com.tw/article/breakingnews/5637709)<br>[taipeitimes.com](https://www.taipeitimes.com/News/taiwan/archives/2026/11/12/2003867610)<br>[informationsecurity.com.tw](https://www.informationsecurity.com.tw/article/article_detail.aspx?aid=13486)<br>[ai.ettoday.net](https://ai.ettoday.net/news/3270502) |
| TW-15 | 2026-11-11 | 🔄 警政署：選舉深偽假訊息已偵處219件，134件176人移送 | AI認知作戰/影響力行動 | AI生成深偽影音模仿候選人聲音與影像，於Facebook、Threads、YouTube與通訊群組散布；警方以AI深偽檢測與數位鑑識查處 | 2026年九合一選舉候選人與選民 | 219件偵處、134件176人移送（含一般假訊息，非全屬深偽） | — | 🟢高 | [npa.gov.tw](https://www.npa.gov.tw/ch/app/news/view?id=2139&module=news&serno=fb675956-bf2e-424a-8955-af9657c1b0b0)<br>[taipeitimes.com](https://www.taipeitimes.com/News/taiwan/archives/2026/11/12/2003867622)<br>[moi.gov.tw](https://www.moi.gov.tw/News_Content.aspx?n=4&s=342941) |
| TW-18 | 2026-11-16 | 🆕 調查局破獲駭客以「BOSSAI」AI代理自動化攻擊系統入侵中央與地方消防救護派遣系統，販售OHCA救護資訊予殯葬業者 | AI代理自動化入侵 | 張、林、李姓3名駭客自2026年4月起經境外VPS跳板架設「BOSSAI」AI自動化攻擊系統，以多個AI Agent攻擊救災救護勤務派遣系統，竊取OHCA（到院前心肺功能停止）等派遣資訊 | 台灣中央與地方消防機關、民眾與往生者家屬 | 11/12–13搜索8處、查扣電腦手機；林、張2人遭羈押 | 台灣（國內駭客，經境外VPS跳板） | 🟢高 | [mjib.gov.tw](https://www.mjib.gov.tw/news/Details/1/1227) |
| TW-19 | 2026-11-19 | 🆕 資安署研擬《政府機關AI資通安全參考指引》，預計明年初發布 | 政府警示/評估報告 | 涵蓋LLM與AI Agent在設計、開發、部署及營運各階段的資安控制措施，參考五眼聯盟與OWASP規範；因應AI代理攻擊浪潮 | 台灣政府機關 | —（政策） | — | 🟡中 | [ec.ltn.com.tw](https://ec.ltn.com.tw/article/breakingnews/5646038)<br>[money.udn.com](https://money.udn.com/money/story/7307/9888799)<br>[taipeitimes.com](https://www.taipeitimes.com/News/taiwan/archives/2026/11/20/2003868075) |

## 事件補充說明

- **TW-01**：國安局送立法院書面報告；中央社轉述
- **TW-02**：中央社轉述國安局新聞稿；數據為2025全年
- **TW-05**：已重新核對：中央社2026-04-06報導與國安局立法院書面報告PDF（立法院議事系統）數字一致；報告亦示警中共將以AI深偽、假民調介入年底九合一選舉。日期改為中央社公開報導日
- **TW-06**：數發部證實事件、稱攻擊來自境外但未公開歸因；技術細節與數字出自以色列資安公司Dream報告（經The Register、iThome報導），報導指操作者以中文下指令，疑為中國駭客
- **TW-07**：媒體轉述彭博社訪問TeamT5；未找到TeamT5公開原始報告
- **TW-08**：詐團自2022年起運作；破獲/起訴在2026年；ETtoday報導受害人數為「25萬」，與刑事局／公視「逾2萬」不一致，本資料採官方數字
- **TW-09**：無證據顯示與境外勢力有關
- **TW-16**：中央社報導資安署說明
- **TW-10**：國安局送立法院報告，媒體轉述
- **TW-12**：受害企業自行公布調查報告（10/22第18日、10/29第25日報告）
- **TW-13**：是否涉及境外仍待釐清
- **TW-17**：警察廣播電臺（警政署）發布；與刑事局科技犯罪防制中心共組專案
- **TW-14**：另有報導（聯合報11/12）引述「8800萬筆」、中央社轉述「約800萬筆」，與記者會「逾百萬份」不一致，本資料採官方記者會說法
- **TW-15**：內政部11/04新聞稿：截至10月底已偵處184件、移送112件153人；11/11更新為219件、134件176人
- **TW-18**：調查局新聞稿；桃園地檢署指揮偵辦
- **TW-19**：媒體報導；正式文件尚未公布

## 交叉引用：涉及台灣的跨國／他國事件

以下事件主檔在他國或「全球」，但台灣為受害方或攻擊目標之一。

| ID | 日期 | 主檔 | 事件 | 可信度 |
|---|---|---|---|---|
| GL-14 | 2026-09-09 | [全球](../global/README.md) | GreyNoise：俄語攻擊者以數百個AI代理（Codex＋DeepSeek）開發並利用PaperCut NG/MF漏洞，入侵48國395個組織 | 🟢高 |
| GL-23 | 2026-10-19 | [全球](../global/README.md) | Vulone：中國關聯操作者以Cairn AI代理對亞洲多國政府發動66次行動、48次取得存取，台灣立法院、法務部、調查局相關系統與Every8D、華航供應商受波及 | 🟡中 |

## 交叉引用：歸因來源為台灣的跨國事件

以下事件的主要受害方在他國，詳細內容見該國檔案。

| ID | 日期 | 受害國 | 事件 | 歸因說明 | 可信度 |
|---|---|---|---|---|---|
| JP-01 | 2026-01-29 | [日本](../japan/README.md) | 台日馬警方合作破獲以「AI換臉」假冒日本警察的視訊詐騙機房 | 台灣（詐團主嫌）、馬來西亞（機房所在地） | 🟡中 |
| HK-02 | 2026-04-22 | [香港](../hong-kong/README.md) | 刑事局破獲台中詐欺機房以「AI視訊」假冒大陸公安與檢察官詐騙香港民眾 | 台灣（機房所在地） | 🟢高 |

