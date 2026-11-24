# 拉丁美洲：2026年AI相關資安事件

[← 回到總覽](../../README.md)

🆕＝2026-11-21第二版新增（9–11月深度擴充）；🧨＝2026-11-22第三版新增（ARTEX專題，見[artex.md](../../artex.md)）；🧠＝2026-11-24第四版新增（AI模型專題，見[models.md](../../models.md)）；🔄＝第二／三版補充細節；`ARTEX`等標籤＝涉及之AI攻擊框架（`ARTEX?`＝同波疑似、未證實）。

本國為主要受害方／發布國之事件：**2 件**；本國為歸因來源之跨國事件：**0 件**；本國受波及之跨國事件：**0 件**。資料期間 2026-01-01 至 2026-11-22，依日期排序。

> ⚠️ 資料限制：區域層級事件；巴西、墨西哥個案另列各國檔案。

## 事件列表

| ID | 日期 | 事件 | 類別 | 手法／AI角色 | 受害對象 | 影響 | 歸因來源 | 可信度 | 來源 |
|---|---|---|---|---|---|---|---|---|---|
| LATAM-01 | 2026-10-08 | OpenAI：俄羅斯「Dark Clark」吸收拉美當地人經營假智庫、伊朗「Bogus Bylines」以7個假記者身分向中小型媒體投稿（俄方為首個Category 5 IO） | AI認知作戰/影響力行動 | 以ChatGPT生成長文、社群留言、假「外洩」文件與音訊腳本、內部成效報告；吸收不知情當地人經營假智庫 | 拉丁美洲輿論、全球中小型線上媒體 | 俄方假智庫網站逾60篇文章；俄方行動評為OpenAI首個Category 5（最高級） | 俄羅斯、伊朗 | 🟢高 | [openai.com](https://openai.com/index/disrupting-ai-enabled-false-front-operations/) |
| LATAM-02 | 2026-10-21 | 🧠 `PentAGI/CARLIY0S` Straiker：CyberCartel以PentAGI為基礎的多代理系統CARLIY0S，串接Claude、Grok與Kimi攻擊逾400家拉美銀行與支付業者 | AI代理自動化入侵 | 四個Claude角色（claude-opus-4-8偵察、claude-opus-4-7寫攻擊程式、設定檔列claude-fable-5〔未證實〕、claude-opus-5仲裁）辯論後由指揮官執行；5個「Grok礦工」蒐集竊得機密；Kimi為備援；模型拒絕時改用本機硬編碼程式；以「授權紅隊／CTF」話術越獄 | 逾400家拉丁美洲銀行與支付業者 | 竊得憑證資料庫4,493筆（含金融帳戶、密碼、API金鑰）、903組CLABE帳號 | 墨西哥（CyberCartel／Tr4nsHack，Straiker研判） | 🟢高 | [straiker.ai](https://www.straiker.ai/blog/inside-carliy0s-how-cybercartel-used-multiple-ai-models-to-attack-latin-american-banks) |

## 事件補充說明

- **LATAM-02**：Anthropic已撤銷其使用的憑證；xAI已獲通知並調查

