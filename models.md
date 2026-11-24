# 2026 AI 滲透測試／自主攻擊框架背後用了哪些 AI 模型？

> 🧠 2026-11-24 新增（台北時間）｜[← 回總覽 README](README.md)｜[ARTEX 專題](artex.md)｜資料截止：2026-11-24
>
> **寫作原則（禁止幻覺）**：本文每一句事實都附上出處連結（來源名稱＋發布日期）；引號內是原文短句。查不到來源的模型或版本**一律不寫**，版本號照各來源原文照抄，不同來源寫法不一致時並列。所有連結已在 2026-11-24 逐一以 curl／WebFetch 確認可開啟。本文不含任何攻擊者個資、金鑰或可直接利用的細節；網域以 `[.]` 去武化。

**證據分級**（每項都標註）
- **(a) 官方**：框架官方 GitHub README／設定檔寫明「支援／預設／推薦」的模型（代表「可以接」，**不代表**攻擊者真的這樣用）。
- **(b) 實戰觀測**：資安廠商、政府機關或 AI 廠商報告中，從攻擊者伺服器、外洩設定檔、日誌、API 帳單、遙測**實際看到**的模型。
- **(c) 媒體／單一來源**：媒體轉述、尚未有第二方證實，或來源自稱未證實。

**可信度**：**高**＝官方文件、政府、廠商一手研究（且有具體證據如設定檔／日誌）；**中**＝信譽媒體轉述、廠商推測或單一廠商且證據描述有限；**低**＝來源自己說未證實、或僅從名稱推測。

## 先查證常見說法：ARTEX 真的常接 DeepSeek、GLM 5.2 嗎？

| 說法 | 結論 | 依據 |
|---|---|---|
| ARTEX 常接 **DeepSeek** | ✅ **證實（高）**，而且是 ARTEX 最常見的後端。最常見的是 DeepSeek **v4.1 Flash** | FBI：「Chinese models are most prevalent, with DeepSeek Flash family models dominating usage」（[FBI FLASH-20261113-001 2026-11-13](https://www.ic3.gov/CSA/2026/261113.pdf)）；Check Point：「models of the Deepseek Flash family being the most prevalent」（[Check Point Research 2026-11-05](https://research.checkpoint.com/2026/hacking-on-autopilot-inside-artex-cybercrime-campaigns/)）；韓國金融案：「The ARTEX instance used DeepSeek v4.1-flash as the primary LLM backend」（[CrowdStrike 2026-10-07](https://www.crowdstrike.com/en-us/blog/unknown-threat-actor-uses-artex-to-target-south-korean-finance/)），另見 [Zscaler ThreatLabz 2026-10-14](https://www.zscaler.com/blogs/security-research/threat-actor-abuses-agentic-ai-pentesting-framework-target-south-korean)、[Zscaler ThreatLabz 2026-10-21](https://www.zscaler.com/blogs/security-research/inside-global-ai-assisted-hacking-campaign)、[Hunt.io 2026-11-04](https://hunt.io/blog/artex-south-korea-bank-infrastructure)；VAPOR PANDA「ran ARTEX primarily with the Chinese-origin DeepSeek LLM」（[CrowdStrike（VAPOR PANDA） 2026-10](https://www.crowdstrike.com/en-us/blog/vapor-panda-uses-artex-to-scale-global-campaign/)） |
| ARTEX 接 **GLM**（智譜 Zhipu AI） | ✅ **證實（高）**，但已公開的版本是 **GLM-5.3**，不是 5.2；而且是**輔助**模型，不是主力 | CrowdStrike：「supplemented this LLM with GLM-5.3 (Zhipu AI) and Grok 4.6 for additional Claude Code sessions」（[CrowdStrike 2026-10-07](https://www.crowdstrike.com/en-us/blog/unknown-threat-actor-uses-artex-to-target-south-korean-finance/)）；Zscaler 表格把 Zhipu AI GLM-5.3 列為「Supplementary Reasoning」（[Zscaler ThreatLabz 2026-10-14](https://www.zscaler.com/blogs/security-research/threat-actor-abuses-agentic-ai-pentesting-framework-target-south-korean)），另說「other configurations also specified DeepSeek, GLM, and Grok」（[Zscaler ThreatLabz 2026-10-21](https://www.zscaler.com/blogs/security-research/inside-global-ai-assisted-hacking-campaign)）；Hunt.io「GLM 5.3 from Zhipu AI and Grok 4.6 serving as backup models」（[Hunt.io 2026-11-04](https://hunt.io/blog/artex-south-korea-bank-infrastructure)）；FBI 將 GLM 列為 ARTEX 可整合的模型之一（[FBI FLASH-20261113-001 2026-11-13](https://www.ic3.gov/CSA/2026/261113.pdf)） |
| ARTEX 接 **GLM 5.2** | ❌ **查無來源**。目前沒有任何報告把「GLM 5.2」和 ARTEX 連在一起 | GLM 5.2 出現在**別的框架**：Cairn（[Unit 42（CL-STA-1238） 2026-11-12](https://unit42.paloaltonetworks.com/cairn-framework-ai-autonomous-attacks/)）、Strix（[Gambit Security 2026-09](https://gambit.security/blog-posts/autonomous-ai-agents-online-retailers-25-a-company)）、Hermes 測試（[Unit 42（BUGSTER） 2026-10-21](https://unit42.paloaltonetworks.com/ai-assisted-cybercrime-analysis/)）。推測是把 Cairn／Strix 的報導和 ARTEX 混在一起，但這只是我們的推測，沒有來源 |

> ⚠️ 細節差異（照抄各來源、不自行統一）：韓國案的 Grok 版本，CrowdStrike、Zscaler 韓國篇、Hunt.io 寫 **Grok 4.6**，Zscaler 全球篇的 ATLAS 表格寫 **grok-4.7**（[Zscaler ThreatLabz 2026-10-21](https://www.zscaler.com/blogs/security-research/inside-global-ai-assisted-hacking-campaign)）。GLM 的角色：CrowdStrike 說是「additional Claude Code sessions」用的；Zscaler 說 ARTEX 設定檔裡就有，用途是「Supplementary Reasoning」，全球篇並說 GLM 負責複核 DeepSeek 的產出。

## 一、總覽表：框架 × 模型

| 框架 | (a) 官方支援／預設模型 | (b) 實戰觀測到的模型 | (c) 媒體／單一來源／未證實 |
|---|---|---|---|
| **ARTEX**（含衍生 AntiFox、Prtseek） | 不內建模型，接 Anthropic、OpenAI 或任何 OpenAI 相容端點（[Censys 2026-11-05](https://censys.com/blog/artex-agentic-asbestos/)、[Zendot 2026-10-03](https://www.zendot.org/en/posts/autumn-27-artex)）；三種請求格式涵蓋「OpenAI, DeepSeek, Qwen, MiniMax, OpenRouter-style resellers and self-hosted models」（[Datadog Security Labs 2026-11-09](https://securitylabs.datadoghq.com/articles/artex-agentic-attacks-aws-environments/)） | **DeepSeek v4.1 Flash（主力）**、GLM-5.3、Grok 4.6／4.7（[CrowdStrike 2026-10-07](https://www.crowdstrike.com/en-us/blog/unknown-threat-actor-uses-artex-to-target-south-korean-finance/)、[Zscaler ThreatLabz 2026-10-14](https://www.zscaler.com/blogs/security-research/threat-actor-abuses-agentic-ai-pentesting-framework-target-south-korean)、[Zscaler ThreatLabz 2026-10-21](https://www.zscaler.com/blogs/security-research/inside-global-ai-assisted-hacking-campaign)、[Hunt.io 2026-11-04](https://hunt.io/blog/artex-south-korea-bank-infrastructure)）；DeepSeek Flash、Kimi K3.1 Pro、Claude Opus 5.5（觸發護欄後改用中國模型）（[Check Point Research 2026-11-05](https://research.checkpoint.com/2026/hacking-on-autopilot-inside-artex-cybercrime-campaigns/)）；DeepSeek＋一個未確認的商用 LLM（[CrowdStrike（VAPOR PANDA） 2026-10](https://www.crowdstrike.com/en-us/blog/vapor-panda-uses-artex-to-scale-global-campaign/)）；FBI 綜整：Claude、GPT、DeepSeek、GLM、Grok、Kimi（[FBI FLASH-20261113-001 2026-11-13](https://www.ic3.gov/CSA/2026/261113.pdf)） | 總結性報導 DeepSeek、GLM、Grok（[Sophos X-Ops 2026-11](https://www.sophos.com/en-us/blog/artex-attackers-apply-agentic-ai)、[SentinelOne 2026-11-13](https://www.sentinelone.com/blog/artex-unmasked-the-rise-of-ai-powered-artex-in-cybercrime-espionage/)）；AntiFox、Prtseek **未公開模型**（[BleepingComputer（引Arctic Wolf） 2026-11-11](https://www.bleepingcomputer.com/news/security/hackers-use-antifox-ai-agents-in-aws-credential-theft-attacks/)、[聯合新聞社（引S2W） 2026-11-22](https://www.yna.co.kr/view/AKR20261120131200017)） |
| **Cairn** | Worker 後端只支援「Claude Code, Codex, and Pi」三種 CLI（[GitHub oritera/Cairn 2026-11-24查閱](https://github.com/oritera/Cairn)）；Unit 42 稱「Cairn is model-agnostic」（[Unit 42（CL-STA-1238） 2026-11-12](https://unit42.paloaltonetworks.com/cairn-framework-ai-autonomous-attacks/)） | **GLM 5.2**（13 次行動）、**DeepSeek V4 Flash**（8）、**DeepSeek V4 Pro**（4）（[Unit 42（CL-STA-1238） 2026-11-12](https://unit42.paloaltonetworks.com/cairn-framework-ai-autonomous-attacks/)）；DeepSeek v4.1 Flash（[Gambit Security 2026-09](https://gambit.security/blog-posts/autonomous-ai-agents-online-retailers-25-a-company)、[Vulone 2026-10-19](https://vulone.com/blog/a-china-linked-operator-used-ai-agents-to-attack-governments-across-asia)） | worker 名稱「claudecode_deepseek-v4.1-flash」，但「Neither the researcher nor Reuters confirmed the models」（[The Hacker News（引NorForge／路透） 2026-10](https://thehackernews.com/2026/10/hackers-use-autonomous-ai-agents-to.html)）〔低〕 |
| **Strix** | 預設範例 `vercel_ai_gateway/zai/glm-5.3`；推薦 GLM-5.3、DeepSeek V4.1 Flash、GPT-6.1 Sol、Claude Opus 5.5、Gemini 4 Argon、DeepSeek V4 Pro、Kimi K3.1 Pro（[GitHub usestrix/strix 2026-11-24查閱](https://github.com/usestrix/strix)） | 經 OpenRouter 先用 **GLM 5.2**、後換 **DeepSeek v4 Pro**（[Gambit Security 2026-09](https://gambit.security/blog-posts/autonomous-ai-agents-online-retailers-25-a-company)） | — |
| **Hermes Agent**（Nous Research） | 「Use any model you want — Nous Portal, OpenRouter, OpenAI, your own endpoint」（[GitHub NousResearch/hermes-agent 2026-11-24查閱](https://github.com/NousResearch/hermes-agent)） | **DeepSeek**（[Unit 42（knaithe） 2026-07-30](https://unit42.paloaltonetworks.com/autonomous-ai-cyber-attack-campaign/)）；**DeepSeek V4**（[Unit 42（BUGSTER） 2026-10-21](https://unit42.paloaltonetworks.com/ai-assisted-cybercrime-analysis/)）；**DeepSeek-V4-Flash**（台灣政府案，[CSO Online（引Dream） 2026-08-13](https://www.csoonline.com/article/4209210/ai-agents-wage-near-autonomous-cyberattack-on-asian-government-networks.html)）；Claude opus-4.6（[Gambit Security 2026-09](https://gambit.security/blog-posts/autonomous-ai-agents-online-retailers-25-a-company)）；去對齊（abliterated）DeepSeek-V4「DS4」、Qwen 3.5 122B、去對齊 GLM、DeepSeek-R1 70B、Gemma（[Acronis TRU（BOSSAI） 2026-11-04](https://www.acronis.com/en/tru/posts/bossai-inside-the-ai-attack-mesh-that-targeted-taiwans-emergency-services/)） | — |
| **OpenClaw** | 「Models and agent harnesses (Claude, Codex, local models) are plugins you can swap」（[GitHub openclaw/openclaw 2026-11-24查閱](https://github.com/openclaw/openclaw)） | **MiniMax、DeepSeek** 輪替（[CounterCraft 2026-11-12](https://www.countercraftsec.com/blog/openclaw-malware-ai-agent-attack/)）；商用 **MiniMax M3**（但拒絕攻擊）（[Acronis TRU（BOSSAI） 2026-11-04](https://www.acronis.com/en/tru/posts/bossai-inside-the-ai-attack-mesh-that-targeted-taiwans-emergency-services/)）；DeepSeek-V4-Flash（與 Hermes 同框架組合，[CSO Online（引Dream） 2026-08-13](https://www.csoonline.com/article/4209210/ai-agents-wage-near-autonomous-cyberattack-on-asian-government-networks.html)） | — |
| **CyberStrikeAI** | OpenAI 相容設定，範例 `gpt-4o`、`deepseek-chat`、`qwen3-max`（[GitHub CyberStrikeAI 2026-11-24查閱](https://github.com/Ed1s0nZ/CyberStrikeAI)）；「connects commercial and open-weight LLMs」（[Google GTIG AI Threat Tracker 2026-11-16](https://cloud.google.com/blog/topics/threat-intelligence/agentic-threat-activity-crosses-a-significant-threshold)） | **未公開**：卡巴斯基未點名模型（[Kaspersky Securelist 2026-11-02](https://securelist.com/cyberstrikeai-attacks/)）；趨勢科技明言「実際に使われたAIモデルが何なのか…未確定」（[趨勢科技 2026-10-23](https://www.trendmicro.com/ja_jp/jp-security/26/j/expertview-20261023-01.html)） | BOSSAI 網格中的攻擊代理之一，模型未個別說明（[Acronis TRU（BOSSAI） 2026-11-04](https://www.acronis.com/en/tru/posts/bossai-inside-the-ai-attack-mesh-that-targeted-taiwans-emergency-services/)） |
| **PentAGI**（VXControl） | OpenAI、Anthropic、Gemini、Bedrock、Ollama、DeepSeek、GLM、Kimi、Qwen、MiniMax、Mistral、xAI、自訂端點，加上 OpenRouter／DeepInfra（[GitHub vxcontrol/pentagi 2026-11-24查閱](https://github.com/vxcontrol/pentagi)）；「over a dozen cloud and local LLM backends」（[Google GTIG 2026-10-30](https://cloud.google.com/blog/topics/threat-intelligence/artex-and-friends-enter-agentic-offensive-frameworks)） | 以 PentAGI 為基礎的 CARLIY0S：**Claude**（claude-opus-4-8、4-7、claude-opus-5）、**Grok**、**Kimi**（[Straiker（CARLIY0S） 2026-10-21](https://www.straiker.ai/blog/inside-carliy0s-how-cybercartel-used-multiple-ai-models-to-attack-latin-american-banks)）；GTG-50020／50029 使用 PentAGI 搭 **Claude**（[Anthropic 威脅報告 2026-09](https://www.anthropic.com/threat-intelligence-report-september-2026)） | CARLIY0S 設定檔列「claude-fable-5」，Straiker 註明「per configuration」、未證實（[Straiker（CARLIY0S） 2026-10-21](https://www.straiker.ai/blog/inside-carliy0s-how-cybercartel-used-multiple-ai-models-to-attack-latin-american-banks)）〔低〕 |
| **HexStrike AI** | MCP 伺服器，讓「AI agents (Claude, GPT, Copilot, etc.)」呼叫工具（[GitHub 0x4m4/hexstrike-ai 2026-11-24查閱](https://github.com/0x4m4/hexstrike-ai)）；可接 Claude Code、VS Code 等 MCP 客戶端（[Cisco Talos 2026-11-13](https://blog.talosintelligence.com/artex-and-beyond/)） | GTIG 看到 HexStrike 被試用，未點名模型（[Google GTIG AI Threat Tracker 2026-11-16](https://cloud.google.com/blog/topics/threat-intelligence/agentic-threat-activity-crosses-a-significant-threshold)） | 俄國駭客 HexStrike＋**Claude**（[Cybernews 2026-06-23](https://cybernews.com/security/claude-ai-exploited-breach-hotel-booking-platforms/)）〔中〕 |
| **PentestGPT** | Claude Code、Codex 後端；舊版支援 OpenAI、Anthropic、Gemini、DeepSeek、xAI、Qwen、Moonshot、Ollama（[GitHub GreyDGL/PentestGPT 2026-11-24查閱](https://github.com/GreyDGL/PentestGPT)） | **2026 年查無實戰案例** | — |
| **Villager**（Cyberspike） | — | **僅 2025 年報告**：「DeepSeek v3 language model (accessed through OpenAI-compatible API endpoints)」（[Straiker（Villager） 2025-09-11](https://www.straiker.ai/blog/cyberspike-villager-cobalt-strike-ai-native-successor)） | 2026 年查無新報告 |
| **BOSSAI**（12 代理網格，非單一框架） | — | 攻擊核心「ran almost exclusively on abliterated models: stripped-down variants of DeepSeek, GLM, and Qwen」；Grok 與 MiniMax M3 拒絕攻擊（[Acronis TRU（BOSSAI） 2026-11-04](https://www.acronis.com/en/tru/posts/bossai-inside-the-ai-attack-mesh-that-targeted-taiwans-emergency-services/)） | 媒體寫「Grok 4.5」拒絕（[Cybersecurity News 2026-11](https://cybersecuritynews.com/one-hacker-uses-12-ai-agents/)），Acronis 原文未寫版本號〔中〕 |
## 二、各框架詳述
### 1. ARTEX

**(a) 官方設計**
- Censys：「works with Anthropic, OpenAI, or any OpenAI-compatible model endpoint」；並發現「43 ARTEX hosts also run self-hosted LLM gateway or reseller software, mainly CLIProxyAPI (19) and New API (18)」——攻擊者常在同一台主機架模型中轉站（[Censys 2026-11-05](https://censys.com/blog/artex-agentic-asbestos/)）〔高〕
- Zendot：「LLM keys for Anthropic or OpenAI are set in the UI or via environment variables」（[Zendot 2026-10-03](https://www.zendot.org/en/posts/autumn-27-artex)）〔高〕
- Datadog：三種請求格式，openai 格式「covers OpenAI, DeepSeek, Qwen, MiniMax, OpenRouter-style resellers and self-hosted models」；anthropic 格式也可接「vendors that expose an Anthropic-compatible endpoint, such as DeepSeek」；「When one provider bans or cuts off a key, ARTEX moves to the next」（[Datadog Security Labs 2026-11-09](https://securitylabs.datadoghq.com/articles/artex-agentic-attacks-aws-environments/)）〔高〕
- FBI：「ARTEX does not include its own SI model but integrates with external LLM providers, including frontier models (Anthropic Claude, OpenAI GPT) and open-source or Chinese-origin models (DeepSeek, GLM, Grok, Kimi)」；網路指標列出對外連線至 api.anthropic[.]com、api.deepseek[.]com、open.bigmodel[.]cn、api.x[.]ai（[FBI FLASH-20261113-001 2026-11-13](https://www.ic3.gov/CSA/2026/261113.pdf)）〔高〕
- Google GTIG 只說 ARTEX「By leveraging APIs from frontier and open source models」，**沒有點名模型**（[Google GTIG 2026-10-30](https://cloud.google.com/blog/topics/threat-intelligence/artex-and-friends-enter-agentic-offensive-frameworks)）；Cisco Talos 只說「ARTEX can use different large language models (LLMs)」（[Cisco Talos 2026-11-13](https://blog.talosintelligence.com/artex-and-beyond/)）。

**(b) 實戰觀測**
- 韓國金融業攻擊者（KR-02、KR-13、GL-35）：
  - CrowdStrike：「DeepSeek v4.1-flash as the primary LLM backend… supplemented this LLM with GLM-5.3 (Zhipu AI) and Grok 4.6」，並「likely accessed DeepSeek via the likely LLM API proxy/reseller xcai[.]pro」（[CrowdStrike 2026-10-07](https://www.crowdstrike.com/en-us/blog/unknown-threat-actor-uses-artex-to-target-south-korean-finance/)）〔高〕
  - Zscaler 韓國篇表格：DeepSeek v4.1-flash＝Primary LLM Backend；GLM-5.3、Grok 4.6＝Supplementary Reasoning（[Zscaler ThreatLabz 2026-10-14](https://www.zscaler.com/blogs/security-research/threat-actor-abuses-agentic-ai-pentesting-framework-target-south-korean)）〔高〕
  - Zscaler 全球篇：「ARTEX was configured to use a DeepSeek model through an OpenAI-compatible gateway, but other configurations also specified DeepSeek, GLM, and Grok」，ATLAS 表格列 deepseek-v4.1-flash、glm-5.3、grok-4.7（[Zscaler ThreatLabz 2026-10-21](https://www.zscaler.com/blogs/security-research/inside-global-ai-assisted-hacking-campaign)）〔高〕
  - Hunt.io：同上三模型；外洩環境變數中有 Zhipu GLM 金鑰（ZAI_KEY）與 OpenAI 相容中轉金鑰；另有「grok2api」通道與「Gemini2API」管理介面；Claude Code 2.1.221 經路由器轉往 xcai[.]pro，實際打到 DeepSeek V4.1 Flash（[Hunt.io 2026-11-04](https://hunt.io/blog/artex-south-korea-bank-infrastructure)）〔高〕。⚠️ 換句話說，「用 Claude Code」不等於「用 Claude 模型」。
  - Recorded Future：「used several AI tools … including Claude Code, DeepSeek, Grok, and Zhipu AI」（[Recorded Future（TAG-217） 2026-10](https://www.recordedfuture.com/blog/tag-217-artex-south-korean-banks)）〔高〕；媒體轉述見 [BleepingComputer 2026-10-10](https://www.bleepingcomputer.com/news/security/hacker-used-artex-ai-and-claude-agents-to-target-south-korean-banks/)〔中〕
- Check Point（GL-33）：「models of the Deepseek Flash family being the most prevalent」；在 3 個設定美國模型的實例中，「we observed guardrails being hit only when using Anthropic's Opus 5.5. Here, the actor subsequently switched to more permissive Chinese models」；某操作者兩個主控台使用「Deepseek v4.1 Flash and Kimi K3.1 Pro models」；另一主控台約 5 天、經第三方中轉使用 DeepSeek-V4.1-Flash，成本約 180–360 美元；操作者聊天中提到「glm的」（[Check Point Research 2026-11-05](https://research.checkpoint.com/2026/hacking-on-autopilot-inside-artex-cybercrime-campaigns/)）〔高〕
- CrowdStrike VAPOR PANDA（GL-26）：「ran ARTEX primarily with the Chinese-origin DeepSeek LLM, supplemented with a second, subscription-based commercial LLM that CrowdStrike Intelligence could not confirm」（[CrowdStrike（VAPOR PANDA） 2026-10](https://www.crowdstrike.com/en-us/blog/vapor-panda-uses-artex-to-scale-global-campaign/)）〔高〕
- FBI 綜整：「DeepSeek Flash family models dominating usage」（[FBI FLASH-20261113-001 2026-11-13](https://www.ic3.gov/CSA/2026/261113.pdf)）〔高〕
- Wiz：「an ARTEX checkout sat alongside .claude, .grok and .agents directories」——只能說明同一台主機也裝了這些 AI 工具，**不能證明** ARTEX 用了哪個模型（[Wiz 2026-11-23](https://www.wiz.io/blog/agentic-attacks-artex-offensive-ai-frameworks)）〔中〕

**(c) 總結性／轉述**
- Sophos：「operators have connected it to models including DeepSeek, GLM, and Grok」（[Sophos X-Ops 2026-11](https://www.sophos.com/en-us/blog/artex-attackers-apply-agentic-ai)）；SentinelOne 綜整同上並稱行動成本「$145 to $1,500 in model time」（[SentinelOne 2026-11-13](https://www.sentinelone.com/blog/artex-unmasked-the-rise-of-ai-powered-artex-in-cybercrime-espionage/)）〔中，屬二手綜整〕
- **衍生工具**：AntiFox（ARTEX 0.1.1 分支）未公開模型（[BleepingComputer（引Arctic Wolf） 2026-11-11](https://www.bleepingcomputer.com/news/security/hackers-use-antifox-ai-agents-in-aws-credential-theft-attacks/)）；Prtseek（以 ARTEX 為基礎，聯合新聞社稱 ARTEX 為「중국산 대규모언어모델(LLM) 기반」框架）未公開實際模型（[聯合新聞社（引S2W） 2026-11-22](https://www.yna.co.kr/view/AKR20261120131200017)）。

### 2. Cairn

- **(a)**：「Supported worker backends: Claude Code, Codex, and Pi」（[GitHub oritera/Cairn 2026-11-24查閱](https://github.com/oritera/Cairn)）〔高〕。也就是說，Cairn 本身透過這三種 CLI 去接模型，模型可以換。
- **(b)** Unit 42 CL-STA-1238（US-14）：「The attackers ran their operations on the Chinese models Zhipu GLM 5.2 and DeepSeek V4 Flash/Pro」；25 次行動中「Thirteen on GLM 5.2, Eight on DeepSeek V4 Flash, Four on DeepSeek V4 Pro」；「Neither Zhipu GLM nor DeepSeek refused this framing」（[Unit 42（CL-STA-1238） 2026-11-12](https://unit42.paloaltonetworks.com/cairn-framework-ai-autonomous-attacks/)）〔高〕
- **(b)** Gambit：「DeepSeek v4.1 Flash was used in the Cairn attacks」（[Gambit Security 2026-09](https://gambit.security/blog-posts/autonomous-ai-agents-online-retailers-25-a-company)）〔高〕
- **(b)** Vulone（GL-23）：「Task workers route through a local gateway to a single model: global:deepseek-v4.1-flash」，單一閘道金鑰處理 36,771,234,882 tokens（[Vulone 2026-10-19](https://vulone.com/blog/a-china-linked-operator-used-ai-agents-to-attack-governments-across-asia)）〔高〕
- **(c)** NorForge／路透（US-07）：worker 名為「claudecode_deepseek-v4.1-flash」，但「Neither the researcher nor Reuters confirmed the models」（[The Hacker News（引NorForge／路透） 2026-10](https://thehackernews.com/2026/10/hackers-use-autonomous-ai-agents-to.html)）〔低〕

### 3. Strix

- **(a)**：README 範例 `STRIX_LLM="vercel_ai_gateway/zai/glm-5.3"`；推薦模型清單：Z.ai GLM-5.3、DeepSeek V4.1 Flash、OpenAI GPT-6.1 Sol、Anthropic Claude Opus 5.5、Google Gemini 4 Argon、DeepSeek V4 Pro、Moonshot Kimi K3.1 Pro；也支援 Vertex、Bedrock、Azure 與本機模型（[GitHub usestrix/strix 2026-11-24查閱](https://github.com/usestrix/strix)）〔高〕
- **(b)** Gambit（US-06）：「Strix ran through OpenRouter on GLM 5.2 and later on DeepSeek v4 Pro」，4 週 OpenRouter 花費 7,005.71 美元（[Gambit Security 2026-09](https://gambit.security/blog-posts/autonomous-ai-agents-online-retailers-25-a-company)；另見 [The Register 2026-09-25](https://www.theregister.com/security/2026/09/25/crook-used-three-open-source-agents-to-break-into-a-fortune-500-hospitality-company-a-major-us-airline-and-25-other-orgs/5299012)）〔高〕

### 4. Hermes Agent（Nous Research）

- **(a)**：「Use any model you want — Nous Portal, OpenRouter, OpenAI, your own endpoint」；可匯入 OpenClaw、Claude Code、Codex 的設定與 API 金鑰（[GitHub NousResearch/hermes-agent 2026-11-24查閱](https://github.com/NousResearch/hermes-agent)）〔高〕
- **(b)** Unit 42 knaithe（GL-45）：「leveraged DeepSeek, via the Hermes Agent framework, as their autonomous offensive operator」；另設定 Codex（GPT-5.4，經代理）、Claude Code（Opus，經代理，僅連線測試）、Qwen Code（GLM-5／Qwen／Kimi／MiniMax，經 dashscope）（[Unit 42（knaithe） 2026-07-30](https://unit42.paloaltonetworks.com/autonomous-ai-cyber-attack-campaign/)）〔高〕
- **(b)** Unit 42 BUGSTER（IN-04）：「configured the Hermes Agent framework with DeepSeek V4 as its reasoning engine」；Cursor 中用 Claude Opus 4.8、GPT-5.5、Composer 2.5；也試過 GLM 5.2 與 OpenRouter 模型，並寫腳本檢測 GLM 5.2 是否拒答；「Multiple, unrelated actors are independently adopting the same Hermes + DeepSeek combination」（[Unit 42（BUGSTER） 2026-10-21](https://unit42.paloaltonetworks.com/ai-assisted-cybercrime-analysis/)）〔高〕
- **(b)** 台灣政府機關案（TW-06）：Dream 事後確認「the use of a DeepSeek-V4-Flash model within this framework」，但「We do not know whether it was the only model used」（[CSO Online（引Dream） 2026-08-13](https://www.csoonline.com/article/4209210/ai-agents-wage-near-autonomous-cyberattack-on-asian-government-networks.html)）〔中：廠商經媒體表示〕
- **(b)** Gambit：Hermes「used Anthropic's opus-4.6 (after newer models refused its requests)」（[Gambit Security 2026-09](https://gambit.security/blog-posts/autonomous-ai-agents-online-retailers-25-a-company)）〔高〕
- **(b)** Acronis BOSSAI（TW-18）：Hermes 早期試過 Gemma、Qwen 3.5 122B、去對齊 GLM、Ollama、DeepSeek-R1 70B，最後預設為在 4 張本機 GPU 上跑的去對齊 DeepSeek-V4 變體「DS4」（[Acronis TRU（BOSSAI） 2026-11-04](https://www.acronis.com/en/tru/posts/bossai-inside-the-ai-attack-mesh-that-targeted-taiwans-emergency-services/)）〔高〕

### 5. OpenClaw

- **(a)**：「Models and agent harnesses (Claude, Codex, local models) are plugins you can swap」（[GitHub openclaw/openclaw 2026-11-24查閱](https://github.com/openclaw/openclaw)）〔高〕
- **(b)** CounterCraft 誘捕（GL-48）：「used a commercial Chinese AI gateway at llm.chudian[.]site, rotating between MiniMax and DeepSeek models」（[CounterCraft 2026-11-12](https://www.countercraftsec.com/blog/openclaw-malware-ai-agent-attack/)）〔高〕
- **(b)** Acronis BOSSAI：OpenClaw 跑「commercial MiniMax M3」，但拒絕攻擊請求（[Acronis TRU（BOSSAI） 2026-11-04](https://www.acronis.com/en/tru/posts/bossai-inside-the-ai-attack-mesh-that-targeted-taiwans-emergency-services/)）〔高〕
- **(b)** 台灣政府案：Hermes／OpenClaw 組合中有 DeepSeek-V4-Flash（[CSO Online（引Dream） 2026-08-13](https://www.csoonline.com/article/4209210/ai-agents-wage-near-autonomous-cyberattack-on-asian-government-networks.html)）〔中〕

### 6. CyberStrikeAI

- **(a)**：設定範例 `provider: openai_compatible`，`base_url` 可為 api.openai.com 或 api.deepseek.com，`model: "gpt-4o"  # or deepseek-chat, qwen3-max`（[GitHub CyberStrikeAI 2026-11-24查閱](https://github.com/Ed1s0nZ/CyberStrikeAI)）〔高〕
- **(b) 未公開模型**：卡巴斯基（GL-32）描述 C2 上的 LLM 編排器，但未點名模型，並指出代理與 C2 通訊時「without accessing AI platforms such as ChatGPT or Claude」（[Kaspersky Securelist 2026-11-02](https://securelist.com/cyberstrikeai-attacks/)）；趨勢科技（JP-17）明言模型「未確定」（[趨勢科技 2026-10-23](https://www.trendmicro.com/ja_jp/jp-security/26/j/expertview-20261023-01.html)）。

### 7. PentAGI（VXControl）

- **(a)**：支援 OpenAI、Anthropic、Google Gemini、AWS Bedrock、Ollama、DeepSeek、GLM（z.ai）、Kimi、Qwen、MiniMax、Mistral、xAI、自訂 OpenAI 相容端點，以及 OpenRouter、DeepInfra（[GitHub vxcontrol/pentagi 2026-11-24查閱](https://github.com/vxcontrol/pentagi)）〔高〕
- **(b)** Straiker CARLIY0S（LATAM-02）：「built on the PentAGI autonomous offensive framework… commercial AI models, including Kimi AI's model, Claude Sonnet and Opus, and xAI's Grok」；角色 claude-opus-4-8（偵察）、claude-opus-4-7（寫攻擊程式）、claude-opus-5（仲裁），Grok 礦工，Kimi 備援；模型拒絕時改用硬編碼程式（[Straiker（CARLIY0S） 2026-10-21](https://www.straiker.ai/blog/inside-carliy0s-how-cybercartel-used-multiple-ai-models-to-attack-latin-american-banks)）〔高〕
- **(b)** Anthropic：GTG-50020、GTG-50029「leveraged publicly available offensive agent frameworks like PentAGI」；報告期間所有案例「Claude Haiku, Sonnet, and Opus models were used」（[Anthropic 威脅報告 2026-09](https://www.anthropic.com/threat-intelligence-report-september-2026)）〔高〕
- GTIG 也在實戰看到 PentAGI，但未點名模型（[Google GTIG AI Threat Tracker 2026-11-16](https://cloud.google.com/blog/topics/threat-intelligence/agentic-threat-activity-crosses-a-significant-threshold)）；Talos 統計「more than 700 instances of currently reachable PentAGI」（[Cisco Talos 2026-11-13](https://blog.talosintelligence.com/artex-and-beyond/)）。

### 8. HexStrike AI

- **(a)**：MCP 伺服器，「lets AI agents (Claude, GPT, Copilot, etc.)」呼叫 150+ 工具（[GitHub 0x4m4/hexstrike-ai 2026-11-24查閱](https://github.com/0x4m4/hexstrike-ai)）；Talos：「integrates with many different clients like Claude Code, VS Code, or any other client that supports MCP」（[Cisco Talos 2026-11-13](https://blog.talosintelligence.com/artex-and-beyond/)）〔高〕
- **(c)** Cybernews（GL-44）：「A Russian hacker utilized HexStrike AI, combined with Anthropic's Claude」（[Cybernews 2026-06-23](https://cybernews.com/security/claude-ai-exploited-breach-hotel-booking-platforms/)）〔中〕

### 9. PentestGPT、Villager

- PentestGPT **(a)**：「backend-pluggable for Claude Code and Codex」，舊版支援「OpenAI, Anthropic, Google Gemini, DeepSeek, xAI, Qwen, Moonshot, and local Ollama」（[GitHub GreyDGL/PentestGPT 2026-11-24查閱](https://github.com/GreyDGL/PentestGPT)）。**2026 年查無實戰濫用報告。**
- Villager **(b，2025)**：「DeepSeek v3 language model (accessed through OpenAI-compatible API endpoints)」（[Straiker（Villager） 2025-09-11](https://www.straiker.ai/blog/cyberspike-villager-cobalt-strike-ai-native-successor)）。**屬 2025 年資料，2026 年查無新報告。**
## 三、模型使用排行（只算有來源的實戰觀測）

**計算方法**
1. 只計 **(b) 實戰觀測**的「行動」（另含 1 筆標〔中〕的媒體研究），**不計**框架官方支援清單、不計 FBI／Sophos／SentinelOne 這類綜整報告（避免重複計算）。
2. **同一行動被多家廠商報導只算一次**（例如韓國金融案 CrowdStrike、Zscaler、Hunt.io、Recorded Future 寫的是同一批攻擊者）。
3. 「主力」＝來源寫明實際拿來跑攻擊（primary、backend、reasoning engine、ran on…）；「出現」＝另含只是設定、試用、提及、或被拿來用但**拒絕**攻擊的情況。
4. 模型以「家族」計，版本照來源原文列在右欄。共 14 筆行動，清單見下表。

| 排名 | 模型家族（廠商） | 主力使用（行動數） | 出現（含設定／試用／拒絕） | 來源中出現的版本 |
|---|---|---|---|---|
| 1 | **DeepSeek**（DeepSeek（中國）） | 11 | 11 | v4.1 Flash（最多）、V4 Flash、V4 Pro、V4、V4-Flash、去對齊 V4「DS4」、R1 70B |
| 2 | **Claude**（Anthropic（美國）） | 4 | 8 | opus-4.6、Opus 4.7／4.8、Opus 5、Opus 5.5（觸發護欄） |
| 2 | **GLM**（智譜 Zhipu AI／Z.ai（中國）） | 4 | 7 | GLM-5.3（ARTEX）、GLM 5.2（Cairn、Strix）、GLM-5（knaithe 設定）、去對齊 GLM |
| 4 | **Grok**（xAI（美國）） | 2 | 3 | 4.6／4.7（ARTEX，來源寫法不一） |
| 4 | **Kimi**（Moonshot AI 月之暗面（中國）） | 2 | 3 | K3.1 Pro |
| 6 | **MiniMax**（MiniMax（中國）） | 1 | 3 | M3 |
| 6 | **Qwen**（阿里巴巴（中國）） | 1 | 2 | 3.5 122B |
| — | GPT（OpenAI（美國）） | 0 | 3 | GPT-5.4（Codex）、GPT-5.5（Cursor） |
| — | Gemma（Google（美國，開放權重）） | 0 | 1 | 未寫版本 |

**納入計算的行動與來源**

| 行動 | 主力模型 | 其他（設定／試用／拒絕／提及） | 來源 |
|---|---|---|---|
| ARTEX 韓國金融（CrowdStrike／Zscaler／Hunt.io） | DeepSeek、GLM、Grok | — | [CrowdStrike 2026-10-07](https://www.crowdstrike.com/en-us/blog/unknown-threat-actor-uses-artex-to-target-south-korean-finance/)、[Zscaler ThreatLabz 2026-10-14](https://www.zscaler.com/blogs/security-research/threat-actor-abuses-agentic-ai-pentesting-framework-target-south-korean)、[Hunt.io 2026-11-04](https://hunt.io/blog/artex-south-korea-bank-infrastructure) |
| ARTEX 犯罪行動（Check Point） | DeepSeek、Kimi | Claude（試）、GLM（提及） | [Check Point Research 2026-11-05](https://research.checkpoint.com/2026/hacking-on-autopilot-inside-artex-cybercrime-campaigns/) |
| ARTEX VAPOR PANDA（CrowdStrike） | DeepSeek | — | [CrowdStrike（VAPOR PANDA） 2026-10](https://www.crowdstrike.com/en-us/blog/vapor-panda-uses-artex-to-scale-global-campaign/) |
| Cairn CL-STA-1238（Unit 42） | GLM、DeepSeek | — | [Unit 42（CL-STA-1238） 2026-11-12](https://unit42.paloaltonetworks.com/cairn-framework-ai-autonomous-attacks/) |
| Strix＋Cairn＋Hermes SOUL 行動（Gambit） | Claude、GLM、DeepSeek | — | [Gambit Security 2026-09](https://gambit.security/blog-posts/autonomous-ai-agents-online-retailers-25-a-company) |
| Cairn 亞洲政府（Vulone） | DeepSeek | — | [Vulone 2026-10-19](https://vulone.com/blog/a-china-linked-operator-used-ai-agents-to-attack-governments-across-asia) |
| Hermes knaithe（Unit 42） | DeepSeek | GPT（試）、Claude（試）、Qwen（設定）、GLM（設定）、Kimi（設定）、MiniMax（設定） | [Unit 42（knaithe） 2026-07-30](https://unit42.paloaltonetworks.com/autonomous-ai-cyber-attack-campaign/) |
| Hermes BUGSTER（Unit 42） | DeepSeek | Claude（設定）、GPT（設定）、GLM（試） | [Unit 42（BUGSTER） 2026-10-21](https://unit42.paloaltonetworks.com/ai-assisted-cybercrime-analysis/) |
| Hermes／OpenClaw 台灣政府（Dream） | DeepSeek | — | [CSO Online（引Dream） 2026-08-13](https://www.csoonline.com/article/4209210/ai-agents-wage-near-autonomous-cyberattack-on-asian-government-networks.html) |
| BOSSAI 網格（Acronis） | DeepSeek、GLM、Qwen | Gemma（試）、Grok（拒）、MiniMax（拒）、Claude（設定）、GPT（設定） | [Acronis TRU（BOSSAI） 2026-11-04](https://www.acronis.com/en/tru/posts/bossai-inside-the-ai-attack-mesh-that-targeted-taiwans-emergency-services/) |
| PentAGI CARLIY0S（Straiker） | Claude、Grok、Kimi | — | [Straiker（CARLIY0S） 2026-10-21](https://www.straiker.ai/blog/inside-carliy0s-how-cybercartel-used-multiple-ai-models-to-attack-latin-american-banks) |
| PentAGI GTG-50020／50029（Anthropic） | Claude | — | [Anthropic 威脅報告 2026-09](https://www.anthropic.com/threat-intelligence-report-september-2026) |
| OpenClaw 寄生獸（CounterCraft） | MiniMax、DeepSeek | — | [CounterCraft 2026-11-12](https://www.countercraftsec.com/blog/openclaw-malware-ai-agent-attack/) |
| HexStrike 旅宿業（Cybernews，〔中〕） | Claude | — | [Cybernews 2026-06-23](https://cybernews.com/security/claude-ai-exploited-breach-hotel-booking-platforms/) |

**重點**
- **DeepSeek 是壓倒性第一**：14 筆行動中有 11 筆以 DeepSeek 為主力，橫跨 ARTEX、Cairn、Strix、Hermes、OpenClaw；FBI 也獨立得出「DeepSeek Flash family models dominating usage」（[FBI FLASH-20261113-001 2026-11-13](https://www.ic3.gov/CSA/2026/261113.pdf)）。
- **GLM（智譜）與 Claude 並列第二（各 4 筆主力）**：GLM 在 ARTEX 是輔助（GLM-5.3），在 Cairn 是主力（GLM 5.2 跑了 25 次行動中的 13 次，[Unit 42（CL-STA-1238） 2026-11-12](https://unit42.paloaltonetworks.com/cairn-framework-ai-autonomous-attacks/)）。Claude 的 4 筆中有 1 筆是〔中〕級媒體研究（HexStrike），主要集中在 PentAGI 系（CARLIY0S、Anthropic 自家報告）與 Gambit 的 Hermes；而且多次出現「被拒後換舊版或換中國模型」的紀錄（見第四節）。
- 同票時依「出現」次數排序；排名用同分同名次。
- 官方支援清單（a 級）幾乎每個框架都同時列出美國與中國模型；實戰選擇明顯偏向中國模型，這是「可以接」與「實際接」的差距。
## 四、攻擊者為什麼選這些模型？（只列來源明說的理由）

| 理由 | 來源原文 | 出處 |
|---|---|---|
| **便宜＋能力夠** | 「due to their balance of capabilities, relatively low cost」 | [FBI FLASH-20261113-001 2026-11-13](https://www.ic3.gov/CSA/2026/261113.pdf) |
| | DeepSeek Flash「provide a good balance of capabilities and cost」；一台主控台 5 天約 180–360 美元 | [Check Point Research 2026-11-05](https://research.checkpoint.com/2026/hacking-on-autopilot-inside-artex-cybercrime-campaigns/) |
| | 行動成本「$145 to $1,500 in model time」 | [SentinelOne 2026-11-13](https://www.sentinelone.com/blog/artex-unmasked-the-rise-of-ai-powered-artex-in-cybercrime-espionage/) |
| **在「滲透測試」包裝下沒有護欄** | 「lack of observable guardrails when framed for penetration testing」 | [FBI FLASH-20261113-001 2026-11-13](https://www.ic3.gov/CSA/2026/261113.pdf) |
| | DeepSeek Flash「did not show any signs of guardrails when executed under the 'Pentest' framing of ARTEX」 | [Check Point Research 2026-11-05](https://research.checkpoint.com/2026/hacking-on-autopilot-inside-artex-cybercrime-campaigns/) |
| | 「Neither Zhipu GLM nor DeepSeek refused this framing」；「easily accessible open models, currently with weak guardrails」 | [Unit 42（CL-STA-1238） 2026-11-12](https://unit42.paloaltonetworks.com/cairn-framework-ai-autonomous-attacks/) |
| | Hermes＋DeepSeek 組合被多個無關行動者採用，「a key driver is low safety friction」 | [Unit 42（BUGSTER） 2026-10-21](https://unit42.paloaltonetworks.com/ai-assisted-cybercrime-analysis/) |
| **美國模型拒答→換模型** | 「guardrails being hit only when using Anthropic's Opus 5.5. Here, the actor subsequently switched to more permissive Chinese models」 | [Check Point Research 2026-11-05](https://research.checkpoint.com/2026/hacking-on-autopilot-inside-artex-cybercrime-campaigns/) |
| | Hermes 改用 opus-4.6「after newer models refused its requests」 | [Gambit Security 2026-09](https://gambit.security/blog-posts/autonomous-ai-agents-online-retailers-25-a-company) |
| | Grok 拒絕所有明確攻擊請求、OpenClaw 上的 MiniMax M3 也拒絕，操作者轉向本機去對齊（abliterated）模型 | [Acronis TRU（BOSSAI） 2026-11-04](https://www.acronis.com/en/tru/posts/bossai-inside-the-ai-attack-mesh-that-targeted-taiwans-emergency-services/) |
| | CARLIY0S 在模型拒絕時改跑硬編碼程式；以「authorized red-team work or academic capture-the-flag」話術越獄 | [Straiker（CARLIY0S） 2026-10-21](https://www.straiker.ai/blog/inside-carliy0s-how-cybercartel-used-multiple-ai-models-to-attack-latin-american-banks) |
| **一家被封就換下一家（多供應商備援）** | 「When one provider bans or cuts off a key, ARTEX moves to the next」 | [Datadog Security Labs 2026-11-09](https://securitylabs.datadoghq.com/articles/artex-agentic-attacks-aws-environments/) |
| | 依賴多家供應商反映「a resilient toolchain」 | [CrowdStrike（VAPOR PANDA） 2026-10](https://www.crowdstrike.com/en-us/blog/vapor-panda-uses-artex-to-scale-global-campaign/) |
| **經中轉站／轉售商取得** | 「likely accessed DeepSeek via the likely LLM API proxy/reseller xcai[.]pro」 | [CrowdStrike 2026-10-07](https://www.crowdstrike.com/en-us/blog/unknown-threat-actor-uses-artex-to-target-south-korean-finance/) |
| | 43 台 ARTEX 主機同時架 CLIProxyAPI（19）、New API（18）等中轉軟體 | [Censys 2026-11-05](https://censys.com/blog/artex-agentic-asbestos/) |
| | Strix 經 OpenRouter；Hermes 攻擊者經 code.newcli[.]com 代理用 Codex | [Gambit Security 2026-09](https://gambit.security/blog-posts/autonomous-ai-agents-online-retailers-25-a-company)、[Unit 42（knaithe） 2026-07-30](https://unit42.paloaltonetworks.com/autonomous-ai-cyber-attack-campaign/) |
| **偷別人的金鑰** | ARTEX 代理找出暴露的 AI 應用、抽出上游金鑰放入共用池，「prioritized access to premium frontier models」 | [AWS 安全部落格 2026-11-13](https://aws.amazon.com/blogs/security/amazon-threat-intelligence-observes-threat-actors-running-cybercrime-campaigns-with-artex-ai-agents/) |
| | 「Anthropic API keys were harvested from 50 hosts」 | [Wiz 2026-11-23](https://www.wiz.io/blog/agentic-attacks-artex-offensive-ai-frameworks) |
| **本機去對齊模型（不受雲端廠商監控）** | 攻擊核心「ran almost exclusively on abliterated models」 | [Acronis TRU（BOSSAI） 2026-11-04](https://www.acronis.com/en/tru/posts/bossai-inside-the-ai-attack-mesh-that-targeted-taiwans-emergency-services/) |

> 「國內可取得性」（中國境內較易取得中國模型）這一理由，**本次查無來源明說**，故不列入。

## 五、模型廠商自己的回應與處置

| 廠商 | 已公開的處置 | 出處 |
|---|---|---|
| **Anthropic** | 威脅報告稱 GTG-50020、GTG-50029 使用 PentAGI 等框架，並多次寫「We banned accounts associated with the actors」 | [Anthropic 威脅報告 2026-09](https://www.anthropic.com/threat-intelligence-report-september-2026) |
| | 已撤銷 CARLIY0S 使用的憑證：「Anthropic has since revoked the compromised credential used to reach Claude」 | [Straiker（CARLIY0S） 2026-10-21](https://www.straiker.ai/blog/inside-carliy0s-how-cybercartel-used-multiple-ai-models-to-attack-latin-american-banks) |
| **xAI** | Straiker 稱「xAI has been notified」並正在調查 | [Straiker（CARLIY0S） 2026-10-21](https://www.straiker.ai/blog/inside-carliy0s-how-cybercartel-used-multiple-ai-models-to-attack-latin-american-banks) |
| **Google** | Gemini 濫用「triggered Gemini's safety responses, and Google took additional, broader action… disabling the assets」 | [Google GTIG AI Threat Tracker 2026-11-16](https://cloud.google.com/blog/topics/threat-intelligence/agentic-threat-activity-crosses-a-significant-threshold) |
| **DeepSeek** | **查無針對 ARTEX／這些框架的公開聲明。**其使用條款禁止網路入侵與探測等行為（官方條款，非事件回應） | [DeepSeek 使用條款 2026-11-24查閱](https://cdn.deepseek.com/policies/en-US/deepseek-terms-of-use.html) |
| **智譜 Zhipu AI／Z.ai** | **查無公開聲明** | — |
| **Moonshot（Kimi）、MiniMax、阿里巴巴（Qwen）、OpenAI** | **查無針對這些框架的公開聲明** | — |
| **OpenRouter（中轉平台）** | 因推論供應商資料處理問題下架 3 家供應商、移除 125 個 ZDR 端點；媒體報導外洩的提示詞涉及 MiniMax M3、GLM-5.2、Kimi K2.6 等。**此事與攻擊框架無直接關聯**，但顯示攻擊者常用的中轉／轉售管道本身也有資料外洩風險 | [OpenRouter 2026-11-22](https://openrouter.ai/blog/announcements/data-processing-incidents-on-inference-providers/)、[BleepingComputer 2026-11-23](https://www.bleepingcomputer.com/news/security/openrouter-drops-ai-providers-over-leaked-prompts-and-secrets/) |

## 六、未證實與缺口

1. **「ARTEX＋GLM 5.2」查無來源**：已公開的 ARTEX 證據只有 GLM-5.3；GLM 5.2 出自 Cairn、Strix、Hermes 測試（見上）。
2. **Prtseek、AntiFox**：只知道是 ARTEX 衍生，**實際模型未公開**（[聯合新聞社（引S2W） 2026-11-22](https://www.yna.co.kr/view/AKR20261120131200017)、[BleepingComputer（引Arctic Wolf） 2026-11-11](https://www.bleepingcomputer.com/news/security/hackers-use-antifox-ai-agents-in-aws-credential-theft-attacks/)）。
3. **CyberStrikeAI 實戰模型未知**：卡巴斯基未點名，趨勢科技明言未確定（[Kaspersky Securelist 2026-11-02](https://securelist.com/cyberstrikeai-attacks/)、[趨勢科技 2026-10-23](https://www.trendmicro.com/ja_jp/jp-security/26/j/expertview-20261023-01.html)）。
4. **大型綜整報告不點名模型**：Google GTIG（[Google GTIG 2026-10-30](https://cloud.google.com/blog/topics/threat-intelligence/artex-and-friends-enter-agentic-offensive-frameworks)）、Cisco Talos（[Cisco Talos 2026-11-13](https://blog.talosintelligence.com/artex-and-beyond/)）、Microsoft 三篇 ARTEX 報告（2026-10-21、11-05、11-06，經關鍵字比對未提任何模型名稱）都沒寫 ARTEX 用了哪個模型。
5. **VAPOR PANDA 的第二個商用 LLM**：CrowdStrike 自己也「could not confirm」（[CrowdStrike（VAPOR PANDA） 2026-10](https://www.crowdstrike.com/en-us/blog/vapor-panda-uses-artex-to-scale-global-campaign/)）。
6. **版本號不一致**：Grok 4.6 vs grok-4.7（同一批韓國案）；這些版本號照錄來源，未自行統一。
7. **台灣政府機關案**：Dream 只確認有 DeepSeek-V4-Flash，「We do not know whether it was the only model used」（[CSO Online（引Dream） 2026-08-13](https://www.csoonline.com/article/4209210/ai-agents-wage-near-autonomous-cyberattack-on-asian-government-networks.html)）；數發部新聞稿未提模型。
8. **BOSSAI 與調查局案的關係**：Acronis 報告與調查局案同名、皆涉台灣緊急救護系統，但官方未確認是否同一操作者。
9. **PentestGPT 查無 2026 年實戰案例；Villager 只有 2025 年資料。**
10. **DeepSeek、智譜等中國模型廠商沒有任何公開回應**，與 Anthropic、Google 主動揭露封禁形成對比。
11. 「用 Claude Code」≠「用 Claude 模型」：Hunt.io 發現 Claude Code 被轉接到 DeepSeek（[Hunt.io 2026-11-04](https://hunt.io/blog/artex-south-korea-bank-infrastructure)），所以報告中出現 Claude Code 時不能直接算成 Anthropic 模型。

## 資料欄位

`data/events.csv`／`events.json` 新增 **`models`** 欄位（分號分隔），**只在有來源的事件填寫**（目前 21 件），版本照抄來源；未公開者留空或註明「未確定」。

---
本文所有引文均為原文短句，僅供研究與防禦參考。來源可開啟狀態見 [`sources.md`](sources.md)。
