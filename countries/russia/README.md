# 俄羅斯：2026年AI相關資安事件

[← 回到總覽](../../README.md)

🆕＝2026-11-21第二版新增（9–11月深度擴充）；🧨＝2026-11-22第三版新增（ARTEX專題，見[artex.md](../../artex.md)）；🔄＝第二／三版補充細節；`ARTEX`等標籤＝涉及之AI攻擊框架（`ARTEX?`＝同波疑似、未證實）。

本國為主要受害方／發布國之事件：**2 件**；本國為歸因來源之跨國事件：**9 件**；本國受波及之跨國事件：**0 件**。資料期間 2026-01-01 至 2026-11-22，依日期排序。

> ⚠️ 資料限制：俄羅斯作為受害方主要依賴資安廠商（Kaspersky、Positive Technologies）報告。

## 事件列表

| ID | 日期 | 事件 | 類別 | 手法／AI角色 | 受害對象 | 影響 | 歸因來源 | 可信度 | 來源 |
|---|---|---|---|---|---|---|---|---|---|
| RU-01 | 2026-08 | Kaspersky ICS CERT：針對俄羅斯國防與工業組織的攻擊使用LLM生成之惡意模組與腳本 | AI輔助攻擊/惡意程式 | GOFFEE使用具AI特徵的模組攻擊俄國防企業；Eagle Werewolf部署AI生成PowerShell/VBScript載入器與SoullessRAT | 俄羅斯國防與工業組織 | — | 未歸因（GOFFEE、Eagle Werewolf） | 🟢高 | [ics-media.kasperskycontenthub.com](https://ics-media.kasperskycontenthub.com/uploads/2026/08/1785756579-kaspersky-ics-cert-apt-and-financial-attacks-on-industrial-organizations-in-q2-2026-en.pdf) |
| RU-02 | 2026-11-02 | Positive Technologies：首次調查到疑似完全由AI代理執行的入侵俄羅斯企業案，約3小時完成入侵到資料外洩 | AI代理自動化入侵 | 經外部服務初始入侵，數小時內存取十餘個節點，動態建立/修改工具與安裝依賴；複雜操作夾雜語法錯誤並快速修正 | 俄羅斯企業（未具名） | 內部關鍵系統機密資料外洩 | 未歸因 | 🟡中 | [kommersant.ru](https://www.kommersant.ru/doc/9079014) |

## 事件補充說明

- **RU-01**：依搜尋摘要整理，未逐頁核對
- **RU-02**：《生意人報》轉述PT ESC

## 交叉引用：歸因來源為俄羅斯的跨國事件

以下事件的主要受害方在他國，詳細內容見該國檔案。

| ID | 日期 | 受害國 | 事件 | 歸因說明 | 可信度 |
|---|---|---|---|---|---|
| FR-02 | 2026-11-16 | [法國](../france/README.md) | Google GTIG：首見完全無人介入的AI攻擊框架「exploit_agent」，鎖定法國媒體娛樂與教育網站 | 俄語使用者（未歸因國家） | 🟢高 |
| PL-01 | 2026-11-20 | [波蘭](../poland/README.md) | 波蘭數位部：空域遭侵犯後出現AI生成深偽內容，嘲諷模仿國防部長與內政部長，削弱政府公信力 | 俄羅斯（波蘭官方脈絡） | 🟢高 |
| UA-01 | 2026-10-28 | [烏克蘭](../ukraine/README.md) | 烏克蘭數位轉型部：俄羅斯以AI工具加速對烏克蘭公私部門網攻；CERT-UA觀察到1–9月AI用於釣魚、假網頁與程式開發 | 俄羅斯 | 🟡中 |
| LATAM-01 | 2026-10-08 | [拉丁美洲](../latin-america/README.md) | OpenAI：俄羅斯「Dark Clark」吸收拉美當地人經營假智庫、伊朗「Bogus Bylines」以7個假記者身分向中小型媒體投稿（俄方為首個Category 5 IO） | 俄羅斯、伊朗 | 🟢高 |
| ZA-01 | 2026-06 | [南非](../south-africa/README.md) | 南非飯店IT供應商HTI的NebulaPMS遭俄國攻擊者入侵：誘騙開源生成式AI資安工具「以為在做白帽滲透測試」執行入侵 | 俄羅斯（俄國攻擊者，媒體說法） | 🔴低 |
| GL-02 | 2026-02-12 | [全球](../global/README.md) | Google GTIG AI威脅追蹤：模型蒸餾（model extraction）攻擊增加，國家級駭客以Gemini做偵察與釣魚誘餌 | 北韓、伊朗、中國、俄羅斯 | 🟢高 |
| GL-03 | 2026-02-25 | [全球](../global/README.md) | OpenAI 2月報告：中國「網路特戰」IO、柬埔寨半自動AI戀愛詐騙、俄羅斯Rybar內容農場 | 中國、俄羅斯、柬埔寨 | 🟢高 |
| GL-07 | 2026-09-08 | [全球](../global/README.md) | Google GTIG Q2報告：攻擊者6小時內完成代理式大規模憑證收集；UNC6780誘騙AI程式助手與LLM掃描器進行供應鏈入侵 | 北韓、中國、伊朗、俄羅斯等 | 🟢高 |
| GL-14 | 2026-09-09 | [全球](../global/README.md) | GreyNoise：俄語攻擊者以數百個AI代理（Codex＋DeepSeek）開發並利用PaperCut NG/MF漏洞，入侵48國395個組織 | 俄羅斯（俄語使用者，可能） | 🟢高 |

