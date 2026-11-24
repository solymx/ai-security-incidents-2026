# 印度：2026年AI相關資安事件

[← 回到總覽](../../README.md)

🆕＝2026-11-21第二版新增（9–11月深度擴充）；🧨＝2026-11-22第三版新增（ARTEX專題，見[artex.md](../../artex.md)）；🧠＝2026-11-24第四版新增（AI模型專題，見[models.md](../../models.md)）；🔄＝第二／三版補充細節；`ARTEX`等標籤＝涉及之AI攻擊框架（`ARTEX?`＝同波疑似、未證實）。

本國為主要受害方／發布國之事件：**5 件**；本國為歸因來源之跨國事件：**0 件**；本國受波及之跨國事件：**1 件**。資料期間 2026-01-01 至 2026-11-22，依日期排序。

## 事件列表

| ID | 日期 | 事件 | 類別 | 手法／AI角色 | 受害對象 | 影響 | 歸因來源 | 可信度 | 來源 |
|---|---|---|---|---|---|---|---|---|---|
| IN-01 | 2026-03-05 | Bitdefender：APT36以AI大量產製「Vibeware」，以Crystal、Zig、Nim等冷門語言惡意程式攻擊印度政府 | AI輔助攻擊/惡意程式 | 以AI輔助快速產出多語言植入程式，濫用Slack、Discord、Supabase、Google Sheets作C2與外傳；程式品質不穩但以數量淹沒偵測 | 印度政府機關、大使館與相關人員 | — | 巴基斯坦（APT36／Transparent Tribe） | 🟢高 | [bitdefender.com](https://www.bitdefender.com/en-us/blog/businessinsights/apt36-nightmare-vibeware)<br>[github.com](https://github.com/bitdefender/malware-ioc/blob/master/2026%5F03%5F05-apt36-iocs.csv) |
| IN-02 | 2026-04-26 | CERT-In發布CIAD-2026-0020：防範前沿AI驅動的網路風險（嚴重度：高） | 政府警示/評估報告 | 前沿AI提升網攻能力；代理式AI加速偵察、利用與多階段入侵；深偽與冒名詐騙 | 印度組織與個人 | —（警示） | — | 🟢高 | [cert-in.org.in](https://www.cert-in.org.in/s2cMainServlet?VLCODE=CIAD-2026-0020&pageid=PUBVLNOTES02) |
| IN-03 | 2026-10-15 | 🆕 CERT-In示警：測試中的AI代理越權存取印度組織真實系統並讀取個資與機密；另有犯罪集團濫用AI代理滲透框架 | 針對AI系統/平台的攻擊 | 代理經外洩於設定檔與公開程式庫的憑證、過度授權雲端角色進入真實系統；AI公司事後主動通報；另一財務動機行動以AI框架把入侵到衝擊縮短至數小時，修補不完整者數日內再遭攻擊 | 印度組織（未具名） | 受害組織均未察覺（未公布數量） | — | 🟢高 | [thehackernews.com](https://thehackernews.com/2026/10/cert-in-warns-ai-agents-accessed.html)<br>[medianama.com](https://www.medianama.com/wp-content/uploads/2026/10/CERT-In-Advisory-Notes.pdf) |
| IN-04 | 2026-10-21 | 🆕 `Hermes` Unit 42：犯罪者BUGSTER繞過AI安全控制，以Hermes、DeepSeek與Cursor規劃憑證竊取、VoIP詐騙與資料庫外洩，入侵印度大學 | AI輔助攻擊/惡意程式 | 以AI規劃並執行多種網路犯罪，含資料庫外洩 | 印度大學等 | 資料庫遭外洩（未公布筆數） | 未歸因（BUGSTER） | 🟢高 | [unit42.paloaltonetworks.com](https://unit42.paloaltonetworks.com/ai-assisted-cybercrime-analysis/) |
| IN-05 | 2026-11-05 | 🆕 `ARTEX/PentAGI/Cairn/CyberStrikeAI` CERT-In命名「Crafty Falcon」：以ARTEX、PentAGI、Cairn、CyberStrikeAI以「機器速度」入侵印度非銀行放貸、金融科技與加密貨幣交易所 | AI代理自動化入侵 | 以AI偵察目標，直接呼叫受害者支付與撥款系統轉帳；刻意選在假日與週末；修補不完整者遭再次攻擊 | 印度NBFC、金融科技、加密貨幣交易所 | CERT-In未公布損失；路透另報兩家孟買NBFC於10/8–9經ICICI帳戶700餘筆即時轉帳損失約200萬美元（未確認關聯） | 中國（工具來源；攻擊者未歸因） | 🟡中 | [business-standard.com](https://www.business-standard.com/industry/news/china-linked-tools-used-in-ai-driven-cyberattacks-on-indian-financial-firms-126110500996_1.html) |

## 事件補充說明

- **IN-05**：路透報導（Business Standard轉載）

## 交叉引用：涉及印度的跨國／他國事件

以下事件主檔在他國或「全球」，但印度為受害方或攻擊目標之一。

| ID | 日期 | 主檔 | 事件 | 可信度 |
|---|---|---|---|---|
| GL-23 | 2026-10-19 | [全球](../global/README.md) | Vulone：中國關聯操作者以Cairn AI代理對亞洲多國政府發動66次行動、48次取得存取，台灣立法院、法務部、調查局相關系統與Every8D、華航供應商受波及 | 🟡中 |

