# 日本：2026年AI相關資安事件

[← 回到總覽](../../README.md)

本國為主要受害方／發布國之事件：**9 件**；本國為歸因來源之跨國事件：**0 件**。資料期間 2026-01-01 至 2026-11-21，依日期排序。

## 事件列表

| ID | 日期 | 事件 | 類別 | 手法／AI角色 | 受害對象 | 影響 | 歸因來源 | 可信度 | 來源 |
|---|---|---|---|---|---|---|---|---|---|
| JP-01 | 2026-01-29 | 台日馬警方合作破獲以「AI換臉」假冒日本警察的視訊詐騙機房 | 深偽詐騙/語音複製 | 以深偽換臉將日籍話務手臉孔換成日本警察樣貌，穿制服、出示偽造警察證件視訊詐騙；台籍成員在幕後操作AI設備 | 日本民眾（8人） | 詐騙約1,865萬日圓（約新台幣381萬元）；逮捕10人（台5、日4、馬1） | 台灣（詐團主嫌）、馬來西亞（機房所在地） | 🟡中 | [ettoday.net](https://www.ettoday.net/news/20260129/3109710.htm) |
| JP-02 | 2026-02 | 警察廳確認利用生成式AI的新型手機惡意程式：依機型由AI生成畫面操作指令 | AI輔助攻擊/惡意程式 | 受感染裝置將自身資訊送往生成式AI，由AI依廠牌機型生成畫面操作命令，無需使用者操作即執行惡意指令 | 日本手機使用者 | 未公布 | — | 🟢高 | [npa.go.jp](https://www.npa.go.jp/publications/statistics/cybersecurity/data/R8kami/R08_kami_cyber_jousei.pdf) |
| JP-03 | 2026-02-25 | OpenAI：中國執法機關相關人員試圖以ChatGPT策劃針對日本首相的隱蔽影響力行動 | AI認知作戰/影響力行動 | 帳號主欲以模型規劃針對日本首相之隱蔽IO（模型拒絕），並以ChatGPT編修「網路特戰」工作報告；報告顯示該行動已以其他工具執行 | 日本首相、海外異議人士 | 涉及數百名人員、數千假帳號（OpenAI評估） | 中國 | 🟢高 | [openai.com](https://openai.com/index/disrupting-malicious-ai-uses/)<br>[cdn.openai.com](https://cdn.openai.com/pdf/df438d70-e3fe-4a6c-a403-ff632def8f79/disrupting-malicious-uses-of-ai.pdf) |
| JP-04 | 2026-06 | 千葉縣警逮捕以AI生成程式碼組成勒索軟體的19歲男子 | AI輔助攻擊/惡意程式 | 受飲料廠商遭勒索新聞影響，2026年2月以AI產生的原始碼組合出勒索軟體 | —（製作階段） | 以不正指令電磁的記錄作成罪逮捕1人 | — | 🟢高 | [npa.go.jp](https://www.npa.go.jp/publications/statistics/cybersecurity/data/R8kami/R08_kami_cyber_jousei.pdf) |
| JP-05 | 2026-07 | 警視廳逮捕以生成式AI修改攻擊程式、強制註銷影音平台4.68萬帳號的15歲高中生 | AI輔助攻擊/惡意程式 | 發現影音服務伺服器漏洞後，以生成式AI修改自製攻擊程式，大量送出虛假退會請求 | 日本影音串流服務業者與會員 | 約46,800個帳號遭違反意願退會；以偽計業務妨害罪逮捕 | — | 🟢高 | [npa.go.jp](https://www.npa.go.jp/publications/statistics/cybersecurity/data/R8kami/R08_kami_cyber_jousei.pdf) |
| JP-06 | 2026-10-08 | JPCERT/CC注意喚起：國內組織連續遭不正存取外洩個資，新增「濫用AI滲透測試平台（Cairn、CyberStrikeAI、ARTEX）」攻擊案例 | AI代理自動化入侵 | 攻擊者針對各目標掃描多種已知漏洞、竊取設定與備份檔；逆向公開APP取得API端點與金鑰、攻擊內部API（權限變更、NoSQL注入）；10/23更新新增以AI滲透平台攻擊公開Web應用與WSUS（案例E）並公布IP | 日本多個企業與機關（含BI工具、員工管理系統） | 大量個資外洩（JPCERT未彙總數字） | — | 🟢高 | [jpcert.or.jp](https://www.jpcert.or.jp/at/2026/at260030.html) |
| JP-07 | 2026-10-21 | JPCERT/CC Eyes：調查日本近期AI輔助攻擊的攻擊基礎設施（APK分析、API漏洞測試） | AI代理自動化入侵 | 攻擊伺服器上發現以AI掃描已知漏洞並經API攻擊的證據；使用Blutter、jadx逆向Android APK，測試SSRF等；亦鎖定日本境外服務 | 日本及海外Web服務 | — | — | 🟢高 | [blogs.jpcert.or.jp](https://blogs.jpcert.or.jp/en/2026/10/web_api_attacks.html) |
| JP-08 | 2026-10-28 | 日本政府網安閣僚會議：AI疑被用於大規模掃描網站竊取個資；Macnica統計今年216起外洩為去年2.6倍 | AI代理自動化入侵 | 攻擊者以AI加速找出個別網站與APP弱點，以合法使用者身分越權存取他人資料 | 日本電商、會員網站、訂位平台、圖書館與大學系統等 | 216起確認或疑似外洩（10月單月101起，Macnica統計） | — | 🟡中 | [japantimes.co.jp](https://www.japantimes.co.jp/news/2026/10/28/japan/crime-legal/cyberattacks-ai-website-weaknesses/) |
| JP-09 | 2026-11-21 | 菲律賓移民局搗毀以AI深偽假冒日本警察的「包裹詐騙」機房，逮捕18名外籍人士 | 深偽詐騙/語音複製 | 以AI軟體與深偽技術假冒日本警察，以假包裹通知恐嚇被害人包裹內有違禁品 | 日本民眾 | 逮捕18人（多數為日籍，另有中、台、印籍） | 菲律賓（機房所在地；嫌犯含日、中、台、印籍） | 🟡中 | [gmanetwork.com](https://www.gmanetwork.com/news/topstories/metro/1010271/18-foreigners-arrested-in-alleged-ai-powered-parcel-scam-hub-in-pasay/story/) |

## 事件補充說明

- **JP-01**：ETtoday轉述刑事局；跨國案件，台灣檔案交叉引用
- **JP-02**：出自警察廳《令和8年上半期サイバー空間をめぐる脅威の情勢》
- **JP-05**：犯行於2025年11月，逮捕於2026年7月
- **JP-06**：2026-10-08發布，10-23更新
- **JP-08**：佐川急便、Capcom、樂天旅遊等個案企業未公開確認使用AI，故不另列

