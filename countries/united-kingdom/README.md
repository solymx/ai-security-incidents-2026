# 英國：2026年AI相關資安事件

[← 回到總覽](../../README.md)

🆕＝2026-11-21第二版新增（9–11月深度擴充）；🧨＝2026-11-22第三版新增（ARTEX專題，見[artex.md](../../artex.md)）；🔄＝第二／三版補充細節；`ARTEX`等標籤＝涉及之AI攻擊框架（`ARTEX?`＝同波疑似、未證實）。

本國為主要受害方／發布國之事件：**4 件**；本國為歸因來源之跨國事件：**0 件**；本國受波及之跨國事件：**0 件**。資料期間 2026-01-01 至 2026-11-22，依日期排序。

> ⚠️ 資料限制：9–11月僅NCSC評估與媒體報導；未找到英國官方公布之ARTEX受害個案。

## 事件列表

| ID | 日期 | 事件 | 類別 | 手法／AI角色 | 受害對象 | 影響 | 歸因來源 | 可信度 | 來源 |
|---|---|---|---|---|---|---|---|---|---|
| UK-01 | 2026-10-06 | ASOS資安事件：攻擊者以竊得員工憑證存取第三方平台（含AI代理式行銷平台）並對顧客推播未授權通知 | 針對AI系統/平台的攻擊 | 以竊得憑證登入第三方平台（報導指含Simon AI代理式行銷平台）發送未授權推播；姓名與聯絡資料遭存取 | ASOS顧客 | 姓名、聯絡資訊遭存取；付款卡與密碼未受影響 | 未歸因 | 🟡中 | [ncsc.gov.uk](https://www.ncsc.gov.uk/news/incident-affecting-asos-customers)<br>[infosecurity-magazine.com](https://www.infosecurity-magazine.com/news/asos-data-breach-stolen-employee/) |
| UK-04 | 2026-10-24 | 🆕 `ARTEX` 英國進入警戒：評估北京支持的Storm-0940 AI駭客行動對英國的影響 | 政府警示/評估報告 | 評估ARTEX相關Storm-0940行動是否波及英國組織 | 英國組織 | — | 中國（國家關聯：Storm-0940） | 🟡中 | [telegraph.co.uk](https://www.telegraph.co.uk/business/2026/10/24/uk-on-alert-over-beijing-backed-ai-hacking-spree/) |
| UK-02 | 2026-11-03 | NCSC評估《AI與網路入侵》：2028年前英國CNI高度可能遭AI驅動惡意程式勒索攻擊 | 政府警示/評估報告 | 三種情境評估至2028；AI加速漏洞發現與利用，CNI舊系統與AI導入擴大攻擊面 | 英國關鍵基礎設施 | — | — | 🟢高 | [ncsc.gov.uk](https://www.ncsc.gov.uk/report/artificial-intelligence-and-cyber-intrusion) |
| UK-03 | 2026-11-03 | Bitdefender：英國某學校聯盟遭3AM勒索軟體入侵，攻擊行為呈現「AI代理迴圈」特徵 | AI代理自動化入侵 | 指令每40–100秒重複且逐次微調，研判為AI生成命令與自動代理迴圈；竊取Veeam憑證、Mimikatz、建立後門網域管理員、設定跨網域信任、刪除備份後加密 | 英國學校（未具名） | 約50台可達主機中37台遭加密；財務資料遭竊 | 未歸因（3AM勒索軟體附屬成員） | 🟡中 | [bleepingcomputer.com](https://www.bleepingcomputer.com/news/security/uk-school-estate-hit-by-3am-ransomware-in-suspected-ai-assisted-attack/) |

## 事件補充說明

- **UK-01**：NCSC確認事件但未提及AI；AI平台角色出自媒體
- **UK-04**：媒體報導，未見英國官方公布受害個案
- **UK-03**：AI參與為「疑似」，Bitdefender無法取得攻擊者主機

