# 荷蘭：2026年AI相關資安事件

[← 回到總覽](../../README.md)

🆕＝2026-11-21第二版新增（9–11月深度擴充）；🧨＝2026-11-22第三版新增（ARTEX專題，見[artex.md](../../artex.md)）；🧠＝2026-11-24第四版新增（AI模型專題，見[models.md](../../models.md)）；🔄＝第二／三版補充細節；`ARTEX`等標籤＝涉及之AI攻擊框架（`ARTEX?`＝同波疑似、未證實）。

本國為主要受害方／發布國之事件：**1 件**；本國為歸因來源之跨國事件：**0 件**；本國受波及之跨國事件：**0 件**。資料期間 2026-01-01 至 2026-11-22，依日期排序。

> ⚠️ 資料限制：僅DIVD受害方自述。

## 事件列表

| ID | 日期 | 事件 | 類別 | 手法／AI角色 | 受害對象 | 影響 | 歸因來源 | 可信度 | 來源 |
|---|---|---|---|---|---|---|---|---|---|
| NL-01 | 2026-09-29 | 🆕 🔄 `ARTEX` 荷蘭弱點揭露研究所DIVD遭AI代理自主入侵，攻擊「吵雜且非常混亂」 | AI代理自動化入侵 | 利用未公開系統漏洞（非Citrix NetScaler）後由AI代理自主後滲透，含密碼噴灑、干擾自身AitM攻擊、在註解中過度說明決策 | DIVD（非營利資安組織） | 影響仍在調查；已通報警方、個資主管機關與NCSC | 未歸因 | 🟢高 | [bleepingcomputer.com](https://www.bleepingcomputer.com/news/security/automated-ai-agent-used-to-breach-cybersecurity-nonprofit-divd/)<br>[divd.nl](https://www.divd.nl/hacked/) |

## 事件補充說明

- **NL-01**：受害方自述，經BleepingComputer報導；DIVD更新#8（10/31）：調查近尾聲，依事實確認入侵使用ARTEX；入口為Zammad兩個零時差（CVE-2026-102489、CVE-2026-102490），9/21首次存取、9/22於19分鐘內偵測並封鎖

