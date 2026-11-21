# 日本：2026年AI相關資安事件

[← 回到總覽](../../README.md)

🆕＝2026-11-21第二版新增（9–11月深度擴充）；🔄＝第二版補充細節。

本國為主要受害方／發布國之事件：**16 件**；本國為歸因來源之跨國事件：**0 件**；本國受波及之跨國事件：**1 件**。資料期間 2026-01-01 至 2026-11-21，依日期排序。

## 事件列表

| ID | 日期 | 事件 | 類別 | 手法／AI角色 | 受害對象 | 影響 | 歸因來源 | 可信度 | 來源 |
|---|---|---|---|---|---|---|---|---|---|
| JP-01 | 2026-01-29 | 台日馬警方合作破獲以「AI換臉」假冒日本警察的視訊詐騙機房 | 深偽詐騙/語音複製 | 以深偽換臉將日籍話務手臉孔換成日本警察樣貌，穿制服、出示偽造警察證件視訊詐騙；台籍成員在幕後操作AI設備 | 日本民眾（8人） | 詐騙約1,865萬日圓（約新台幣381萬元）；逮捕10人（台5、日4、馬1） | 台灣（詐團主嫌）、馬來西亞（機房所在地） | 🟡中 | [ettoday.net](https://www.ettoday.net/news/20260129/3109710.htm) |
| JP-02 | 2026-02 | 警察廳確認利用生成式AI的新型手機惡意程式：依機型由AI生成畫面操作指令 | AI輔助攻擊/惡意程式 | 受感染裝置將自身資訊送往生成式AI，由AI依廠牌機型生成畫面操作命令，無需使用者操作即執行惡意指令 | 日本手機使用者 | 未公布 | — | 🟢高 | [npa.go.jp](https://www.npa.go.jp/publications/statistics/cybersecurity/data/R8kami/R08_kami_cyber_jousei.pdf) |
| JP-03 | 2026-02-25 | OpenAI：中國執法機關相關人員試圖以ChatGPT策劃針對日本首相的隱蔽影響力行動 | AI認知作戰/影響力行動 | 帳號主欲以模型規劃針對日本首相之隱蔽IO（模型拒絕），並以ChatGPT編修「網路特戰」工作報告；報告顯示該行動已以其他工具執行 | 日本首相、海外異議人士 | 涉及數百名人員、數千假帳號（OpenAI評估） | 中國 | 🟢高 | [openai.com](https://openai.com/index/disrupting-malicious-ai-uses/)<br>[cdn.openai.com](https://cdn.openai.com/pdf/df438d70-e3fe-4a6c-a403-ff632def8f79/disrupting-malicious-uses-of-ai.pdf) |
| JP-04 | 2026-06 | 千葉縣警逮捕以AI生成程式碼組成勒索軟體的19歲男子 | AI輔助攻擊/惡意程式 | 受飲料廠商遭勒索新聞影響，2026年2月以AI產生的原始碼組合出勒索軟體 | —（製作階段） | 以不正指令電磁的記錄作成罪逮捕1人 | — | 🟢高 | [npa.go.jp](https://www.npa.go.jp/publications/statistics/cybersecurity/data/R8kami/R08_kami_cyber_jousei.pdf) |
| JP-05 | 2026-07 | 警視廳逮捕以生成式AI修改攻擊程式、強制註銷影音平台4.68萬帳號的15歲高中生 | AI輔助攻擊/惡意程式 | 發現影音服務伺服器漏洞後，以生成式AI修改自製攻擊程式，大量送出虛假退會請求 | 日本影音串流服務業者與會員 | 約46,800個帳號遭違反意願退會；以偽計業務妨害罪逮捕 | — | 🟢高 | [npa.go.jp](https://www.npa.go.jp/publications/statistics/cybersecurity/data/R8kami/R08_kami_cyber_jousei.pdf) |
| JP-06 | 2026-10-08 | JPCERT/CC注意喚起：國內組織連續遭不正存取外洩個資，新增「濫用AI滲透測試平台（Cairn、CyberStrikeAI、ARTEX）」攻擊案例 | AI代理自動化入侵 | 攻擊者針對各目標掃描多種已知漏洞、竊取設定與備份檔；逆向公開APP取得API端點與金鑰、攻擊內部API（權限變更、NoSQL注入）；10/23更新新增以AI滲透平台攻擊公開Web應用與WSUS（案例E）並公布IP | 日本多個企業與機關（含BI工具、員工管理系統） | 大量個資外洩（JPCERT未彙總數字） | — | 🟢高 | [jpcert.or.jp](https://www.jpcert.or.jp/at/2026/at260030.html) |
| JP-10 | 2026-10-09 | 🆕 國家網路統括室（NCO）發布注意喚起：國內組織接連遭不正存取，要求各機關與重要基礎設施業者緊急點檢 | 政府警示/評估報告 | 因應疑似以AI滲透工具大規模掃描網站與APP弱點之攻擊；10/6大臣指示、10/8跨部會會議後發布 | 日本政府機關、重要基礎設施業者 | —（警示） | — | 🟢高 | [cas.go.jp](https://www.cas.go.jp/jp/seisaku/cybersecurity_kakuryokaigi/dai1/shiryo1.pdf) |
| JP-11 | 2026-10-13 | 🆕 NICT（CYNEX／LETTICE）注意喚起：連續資料外洩原因之一為「A2B攻擊」——解析公開Android APP後攻擊後端伺服器，AI使漏洞探索高度化 | 政府警示/評估報告 | 解析公開Android APP取得API接點與規格，針對後端認證／授權不備（IDOR/BOLA）、SSRF、RCE、SQL注入攻擊；PDF附IoC | 日本Web／APP服務業者 | —（警示） | — | 🟢高 | [cynex.nict.go.jp](https://cynex.nict.go.jp/library/261013-01.html) |
| JP-12 | 2026-10-14 | 🆕 Scutum（WAF廠商）偵測AI代理對日本網站的攻擊：至少3個來源IP、呈現代理式自動化特徵 | AI代理自動化入侵 | WAF日誌中觀察到呈現AI代理特徵的自動化攻擊，來源至少3個IP（IPA 11月短信彙整） | 日本網站（Scutum客戶） | —（偵測阻擋） | 未歸因 | 🟢高 | [scutum.jp](https://www.scutum.jp/information/waf_tech_blog/2026/10/waf-blog-085.html) |
| JP-13 | 2026-10-19 | 🆕 GMO Cybersecurity：相次ぐ不正存取的攻擊源多為AI，確認使用中國開發的ARTEX；單一攻擊源鎖定約20家日本企業 | AI代理自動化入侵 | 在攻擊源伺服器確認ARTEX；另發現6台鎖定日本企業的AI攻擊基礎設施，依產業分配主機；單一攻擊源約20家標的中9家同業 | 日本企業約20家（其中8家於2026年9–10月公告資料外洩） | —（未彙總筆數）；已與執法機關共享情資 | 中國（工具開發來源；攻擊者未歸因） | 🟢高 | [gmo-cybersecurity.com](https://gmo-cybersecurity.com/blog/20261019/)<br>[itmedia.co.jp](https://www.itmedia.co.jp/news/article/2610/20/2000002423/)<br>[sankei.com](https://www.sankei.com/article/20261020-HPL6HXXGDJEBBBMYCRDZ7IRKRE/) |
| JP-07 | 2026-10-21 | JPCERT/CC Eyes：調查日本近期AI輔助攻擊的攻擊基礎設施（APK分析、API漏洞測試） | AI代理自動化入侵 | 攻擊伺服器上發現以AI掃描已知漏洞並經API攻擊的證據；使用Blutter、jadx逆向Android APK，測試SSRF等；亦鎖定日本境外服務 | 日本及海外Web服務 | — | — | 🟢高 | [blogs.jpcert.or.jp](https://blogs.jpcert.or.jp/en/2026/10/web_api_attacks.html) |
| JP-08 | 2026-10-28 | 🔄 日本政府網安閣僚會議：AI疑被用於大規模掃描網站竊取個資；Macnica統計今年216起外洩為去年2.6倍 | AI代理自動化入侵 | 攻擊者以AI加速找出個別網站與APP弱點，以合法使用者身分越權存取他人資料 | 日本電商、會員網站、訂位平台、圖書館與大學系統等 | 216起確認或疑似外洩（10月單月101起，Macnica統計） | — | 🟢高 | [japantimes.co.jp](https://www.japantimes.co.jp/news/2026/10/28/japan/crime-legal/cyberattacks-ai-website-weaknesses/)<br>[cas.go.jp](https://www.cas.go.jp/jp/seisaku/cybersecurity_kakuryokaigi/dai1/shiryo1.pdf) |
| JP-14 | 2026-11-06 | 🆕 警察廳長官就「濫用高度技術的不正存取」導致大規模個資外洩發布指示，要求各縣警強化偵查與企業支援 | 政府警示/評估報告 | 針對企業連續遭不正存取外洩個資（官方稱「高度な技術を悪用」）；本資料未確認指示原文是否直接點名AI | 日本企業與民眾 | —（警政指示） | — | 🟢高 | [npa.go.jp](https://www.npa.go.jp/news/release/2026/20261106001.html) |
| JP-15 | 2026-11-13 | 🆕 IPA《AIセキュリティ短信》11月號：彙整日本AI代理攻擊事件（Scutum、NICT、JPCERT、GMO）及PHP2Shell＋Fragnesia攻擊鏈 | 政府警示/評估報告 | 整理10月日本AI代理攻擊時間軸；介紹Dream Research所稱以PHP2Shell（CVE-2026-109618/109619）串接Fragnesia（CVE-2026-46300）取得PAN-OS root之攻擊 | 日本組織 | —（彙整） | — | 🟢高 | [ipa.go.jp](https://www.ipa.go.jp/digital/ai/security/rcu1hd0000007gji-att/2026-5_1113.pdf) |
| JP-16 | 2026-11-16 | 🆕 京都府警逮捕42歲男子：以生成式AI架設假禮物卡收購網站，詐騙2人 | AI輔助攻擊/惡意程式 | 利用生成式AI製作假禮物卡收購網站，誘騙被害人寄送禮物卡序號 | 日本民眾（2人） | 詐得約4萬日圓 | — | 🟡中 | [news.web.nhk](https://news.web.nhk/newsweb/na/nd-20261116de76796) |
| JP-09 | 2026-11-21 | 菲律賓移民局搗毀以AI深偽假冒日本警察的「包裹詐騙」機房，逮捕18名外籍人士 | 深偽詐騙/語音複製 | 以AI軟體與深偽技術假冒日本警察，以假包裹通知恐嚇被害人包裹內有違禁品 | 日本民眾 | 逮捕18人（多數為日籍，另有中、台、印籍） | 菲律賓（機房所在地；嫌犯含日、中、台、印籍） | 🟡中 | [gmanetwork.com](https://www.gmanetwork.com/news/topstories/metro/1010271/18-foreigners-arrested-in-alleged-ai-powered-parcel-scam-hub-in-pasay/story/) |

## 事件補充說明

- **JP-01**：ETtoday轉述刑事局；跨國案件，台灣檔案交叉引用
- **JP-02**：出自警察廳《令和8年上半期サイバー空間をめぐる脅威の情勢》
- **JP-05**：犯行於2025年11月，逮捕於2026年7月
- **JP-06**：2026-10-08發布，10-23更新
- **JP-10**：依NCO 10/26閣僚會議資料所載時間軸
- **JP-08**：佐川急便、Capcom、樂天旅遊等個案企業未公開確認使用AI，故不另列；國家網路統括室（NCO）10/26會議資料：2026年資料外洩明顯增加、10月Web系統相關案件激增，研判攻擊者「標的の調査や侵害にＡＩを使用している可能性は高い」；時間軸：10/6大臣指示、10/8跨部會會議、10/9 NCO注意喚起
- **JP-14**：AI關聯依NCO、JPCERT同期資料推定
- **JP-16**：NHK報導

## 交叉引用：涉及日本的跨國／他國事件

以下事件主檔在他國或「全球」，但日本為受害方或攻擊目標之一。

| ID | 日期 | 主檔 | 事件 | 可信度 |
|---|---|---|---|---|
| TW-14 | 2026-11-11 | [台灣](../taiwan/README.md) | 資安署：國際AI網攻波及台灣十餘家企業與平台，逾百萬份個資受影響，近半數涉及AI／ARTEX | 🟢高 |

