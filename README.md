# 2026 年全球 AI 相關資安事件資料庫（ai-security-incidents-2026）

整理 **2026-01-01 至 2026-11-21** 間公開報導的 AI 相關資安事件與重大政府示警，**依國家分類**，以東亞（台灣優先）為重點。全部內容以繁體中文撰寫，標題與摘要為翻譯整理，**保留原始來源連結**。

- 收錄事件總數：**84 件**（可信度 高 62 件、中 22 件、低 0 件）
- 完整資料：[`data/events.csv`](data/events.csv)（UTF-8 with BOM，可直接以 Excel 開啟）、[`data/events.json`](data/events.json)
- 依時間瀏覽：[`timeline.md`](timeline.md)｜所有來源連結與檢查結果：[`sources.md`](sources.md)
- 資料截止：2026-11-21（台北時間）

## 國家索引

「受害／發布」＝該國為主要受害方或發布機關所在國；「歸因來源」＝他國事件中被歸因為攻擊來源（含疑似）的次數，詳見各國檔案的「交叉引用」段落。

| # | 國家／地區 | 區域 | 受害／發布 | 歸因來源 | 檔案 |
|---|---|---|---|---|---|
| 1 | **台灣** | 東亞 | 15 | 2 | [countries/taiwan](countries/taiwan/README.md) |
| 2 | **中國** | 東亞 | 8 | 17 | [countries/china](countries/china/README.md) |
| 3 | **日本** | 東亞 | 9 | 0 | [countries/japan](countries/japan/README.md) |
| 4 | **韓國** | 東亞 | 6 | 0 | [countries/south-korea](countries/south-korea/README.md) |
| 5 | **香港** | 東亞 | 2 | 0 | [countries/hong-kong](countries/hong-kong/README.md) |
| 6 | **新加坡** | 東南亞 | 1 | 0 | [countries/singapore](countries/singapore/README.md) |
| 7 | **印尼** | 東南亞 | 1 | 0 | [countries/indonesia](countries/indonesia/README.md) |
| 8 | **印度** | 南亞 | 2 | 0 | [countries/india](countries/india/README.md) |
| 9 | **美國** | 北美 | 11 | 1 | [countries/united-states](countries/united-states/README.md) |
| 10 | **加拿大** | 北美 | 1 | 0 | [countries/canada](countries/canada/README.md) |
| 11 | **英國** | 歐洲 | 3 | 0 | [countries/united-kingdom](countries/united-kingdom/README.md) |
| 12 | **法國** | 歐洲 | 2 | 0 | [countries/france](countries/france/README.md) |
| 13 | **德國** | 歐洲 | 3 | 0 | [countries/germany](countries/germany/README.md) |
| 14 | **波蘭** | 歐洲 | 1 | 0 | [countries/poland](countries/poland/README.md) |
| 15 | **烏克蘭** | 歐洲 | 1 | 0 | [countries/ukraine](countries/ukraine/README.md) |
| 16 | **俄羅斯** | 歐洲 | 2 | 7 | [countries/russia](countries/russia/README.md) |
| 17 | **歐盟** | 歐洲 | 1 | 0 | [countries/eu](countries/eu/README.md) |
| 18 | **以色列** | 中東 | 1 | 0 | [countries/israel](countries/israel/README.md) |
| 19 | **澳洲** | 大洋洲 | 2 | 0 | [countries/australia](countries/australia/README.md) |
| 20 | **拉丁美洲** | 拉丁美洲 | 1 | 0 | [countries/latin-america](countries/latin-america/README.md) |
| 21 | **全球** | 全球／跨國 | 11 | 0 | [countries/global](countries/global/README.md) |
| 22 | **北韓** | 東亞 | 0 | 5 | [countries/north-korea](countries/north-korea/README.md) |
| 23 | **伊朗** | 中東 | 0 | 4 | [countries/iran](countries/iran/README.md) |
| 24 | **巴基斯坦** | 南亞 | 0 | 1 | [countries/pakistan](countries/pakistan/README.md) |
| 25 | **柬埔寨** | 東南亞 | 0 | 2 | [countries/cambodia](countries/cambodia/README.md) |
| 26 | **菲律賓** | 東南亞 | 0 | 1 | [countries/philippines](countries/philippines/README.md) |
| 27 | **馬來西亞** | 東南亞 | 0 | 1 | [countries/malaysia](countries/malaysia/README.md) |

> 「全球」收錄無單一受害國、或受害遍及多國的事件（如 AI 供應鏈投毒、AI 廠商威脅報告）。

## 摘要統計

### 依類別

| 類別 | 件數 |
|---|---|
| AI代理自動化入侵 | 21 |
| 政府警示/評估報告 | 14 |
| AI認知作戰/影響力行動 | 13 |
| AI輔助攻擊/惡意程式 | 13 |
| 深偽詐騙/語音複製 | 12 |
| 針對AI系統/平台的攻擊 | 6 |
| AI供應鏈攻擊 | 5 |

### 依月份（公開揭露日）

| 月份 | 件數 | 分布 |
|---|---|---|
| 2026-01 | 5 | █████ |
| 2026-02 | 9 | █████████ |
| 2026-03 | 7 | ███████ |
| 2026-04 | 4 | ████ |
| 2026-05 | 2 | ██ |
| 2026-06 | 4 | ████ |
| 2026-07 | 5 | █████ |
| 2026-08 | 5 | █████ |
| 2026-09 | 9 | █████████ |
| 2026-10 | 17 | █████████████████ |
| 2026-11 | 17 | █████████████████ |

### 被歸因為攻擊來源（含疑似）

| 來源國 | 事件數 |
|---|---|
| [中國](countries/china/README.md) | 17 |
| [俄羅斯](countries/russia/README.md) | 7 |
| [北韓](countries/north-korea/README.md) | 5 |
| [伊朗](countries/iran/README.md) | 4 |
| [台灣](countries/taiwan/README.md) | 2 |
| [柬埔寨](countries/cambodia/README.md) | 2 |
| [美國](countries/united-states/README.md) | 1 |
| [馬來西亞](countries/malaysia/README.md) | 1 |
| [菲律賓](countries/philippines/README.md) | 1 |
| [巴基斯坦](countries/pakistan/README.md) | 1 |

> 歸因統計只計入官方、資安廠商或可信媒體**明確指出**的來源；「說中文的操作者」「香港IP」等弱歸因也計入，但各事件欄位均註明歸因強度，請勿直接解讀為國家行為。

## 跨國趨勢

1. **「代理式 AI 滲透框架」在 9–11 月形成跨國攻擊浪潮，東亞首當其衝。** ARTEX、Cairn、CyberStrikeAI、Strix、Hermes、OpenClaw 等開源或外流的 AI 滲透／代理框架，被用於自動找漏洞、逆向 APP 取得 API、密碼噴灑與資料外洩。台灣政府機關（TW-06）、91APP 與十餘家企業（TW-12、TW-14）、韓國至少 9 家銀行與 37 家金融公司（KR-02、KR-05）、日本大量個資外洩（JP-06、JP-08），以及美國 ConnectWise 供應鏈（US-08）、Bitrise（GL-11）都在同一時期出現 ARTEX 或類似工具的痕跡；加拿大網安中心統計 ARTEX 佔已觀測 AI 攻擊工具基礎設施約 46%（CA-01）。
2. **中國（含說中文的犯罪者）是最常被歸因的來源，北韓、俄羅斯、伊朗緊追在後。** 中國國家關聯團體（Storm-0940、TeamT5 所稱 Huapi／Slime22 等）與說中文的財務動機犯罪者同時出現（TW-07、KR-02、US-07、US-08）；北韓把 AI 用於量產釣魚文件與深偽視訊會議竊取加密貨幣（KR-04、US-10）；俄語操作者出現首個完全自動化攻擊框架 exploit_agent（FR-02）。中國官方則反向指控境外以 AI 攻擊中國軍工高校（CN-07），但公開具體個案極少。
3. **攻擊面轉向 AI 系統本身：代理技能投毒、AI 閘道漏洞與 AI 套件供應鏈。** OpenClaw 技能市集遭大規模投毒（GL-01、CN-06）、LiteLLM 兩度列入 CISA KEV 並發生 PyPI 惡意版本（US-05、US-11、GL-09）、Hugging Face 被自主代理經惡意資料集入侵（US-03）。台灣資安署、CNCERT、ANSSI 皆已對 AI 代理發布專門警示（TW-04、CN-03、FR-01）。
4. **深偽與語音複製詐騙「產業化」，金額動輒上億。** 美國起訴以 AI 冒充執行長詐騙 1.29 億美元（US-09）、北韓 FaceStealer 竊取逾 4 億美元（US-10）、新加坡深偽總理 Zoom 會議騙走 490 萬新幣（SG-01）、台灣 AI 變聲交友詐騙逾 9 億元（TW-08）；台灣籍詐團也在境外以 AI 換臉假冒日本警察、大陸公安（JP-01、HK-02、JP-09）。
5. **AI 生成內容成為選舉與認知作戰常規武器，台灣 2026 九合一選舉為重災區。** 國安局多次報告中共以 AI 生成影音介選（TW-01、TW-05、TW-10），選舉期間出現多起候選人深偽影音（TW-09、TW-13），警政署偵處 219 件選舉深偽／假訊息（TW-15）；OpenAI 亦揭露中、俄、伊朗利用 ChatGPT 進行影響力行動（JP-03、US-02、LATAM-01）。

## 可信度定義

| 等級 | 定義 |
|---|---|
| 🟢 高 | 政府機關、CERT、執法單位或資安／AI 廠商**第一手**發布（新聞稿、通報、威脅報告、受害企業自行公告）。 |
| 🟡 中 | 具公信力的媒體引述消息來源或轉述官方說法，但未取得第一手文件；或第一手文件存在、但「AI 參與」僅為推估。 |
| 🔴 低 | 單一未經證實的報導。（本資料集未收錄低可信度事件。） |

## 方法與限制

**收錄範圍**：(1) 攻擊者使用 AI 的攻擊（AI 代理自動化入侵、AI 生成惡意程式、AI 釣魚）；(2) 針對 AI 系統的攻擊（提示注入、代理／MCP 濫用、資料與模型投毒、AI 供應鏈、AI 平台入侵）；(3) 深偽與語音複製詐騙；(4) 涉 AI 威脅的重大政府示警與評估報告。

**方法**：以 WebSearch／WebFetch 檢索各國官方（資安署、TWCERT/CC、國安局、調查局、刑事局、警政署、CNCERT、CVERC、國家安全部、JPCERT/CC、警察廳、KISA、金融委員會、CISA、FBI、NCSC、ANSSI、BSI、CERT-In、ASD、加拿大網安中心等）、資安／AI 廠商及主流媒體；台灣以中文來源（中央社、自由時報、iThome、公視、工商時報等）深挖。每筆事件至少一個可點開來源，並於 2026-11-21 以 curl 檢查連結（結果見 [`sources.md`](sources.md)）。

**日期**：採「公開揭露日」，非攻擊發生日；只知月份者以 `YYYY-MM` 表示。部分事件的犯行在 2026 年以前（例如 TW-08 詐團自 2022 年運作），但破獲或揭露在 2026 年，因此收錄。

**跨國事件**：放在主要受害國檔案，於「歸因來源」欄註明，並在來源國檔案的「交叉引用」段落列出。

**刻意排除**：沒有公開證據顯示涉及 AI 的資料外洩不收錄，例如易遊網、永豐銀行、外交部領務局、佐川急便、Capcom 等案，即使與 AI 攻擊浪潮同期發生；同樣不收錄「以 AI 為投資話術」但手法本身未使用 AI 的詐騙。

**已知限制與資料缺口**：
- **數字不一致**：TW-14 的個資外洩規模，官方記者會稱「逾百萬份」，但有媒體報導 800 萬或 8,800 萬筆，本資料集採官方說法並於附註說明。
- **中國作為受害方**：多為官方示警與年報，具體受害個案極少公開。
- **覆蓋較薄的地區**：歐洲多為政府示警而非個案（義大利、西班牙、荷蘭、北歐未收錄）；中東僅以色列；拉丁美洲、非洲幾乎無資料；東南亞僅新加坡、印尼與跨境詐騙；俄羅斯僅有資安廠商報告。
- **時間分布**：1–8 月事件較少，9–11 月因代理式 AI 攻擊浪潮與選舉而明顯集中，可能部分反映媒體關注度而非實際攻擊量。
- **歸因**：AI 參與程度與歸因多來自單一廠商或受害方推估，各事件均註明歸因強度；請勿將「說中文」「香港 IP」等直接視為國家行為。
- 少數立法院、澳洲 ASD 的 PDF 連結自研究環境無法連線（見 sources.md ⚠️），請自行確認。
- 本資料庫僅彙整公開報導，供防禦研究使用，不含攻擊工具、利用程式碼或任何非公開資訊。

## 欄位說明（data/events.csv）

| 欄位 | 說明 |
|---|---|
| id | 國家代碼＋序號（例如 TW-06） |
| date | 公開揭露日（YYYY-MM-DD 或 YYYY-MM） |
| country | 主要受害國／發布國 |
| source_country | 歸因來源（原文說明，含歸因強度） |
| source_country_tags | 正規化的歸因來源國（分號分隔） |
| category | 事件類別 |
| title | 事件名稱（中文翻譯） |
| technique | 手法與 AI 扮演的角色 |
| victims | 受害對象 |
| impact | 影響（只列有出處的數字） |
| credibility | 可信度（高／中／低） |
| sources | 原始來源連結（以「｜」分隔） |
| note | 附註、資料限制 |

## 授權

資料整理內容以 [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.zh-hant) 釋出；各來源文章著作權屬原作者。
