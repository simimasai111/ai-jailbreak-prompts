# AI 破甲提示词整合仓库 (AI Jailbreak Prompts Collection)

整合 GitHub 上公开的 LLM 越狱（jailbreak）/ 破甲提示词研究资料，按技术类别归档，供 AI 安全红队测试、模型防御加固与学术研究参考。

## 目录结构

```
ai-jailbreak-prompts/
├── 01-dan-series/           # DAN 系列（Do Anything Now）经典提示词 6.0-13.0、Evil-Bot、ANTI-DAN
├── 02-roleplay-personas/    # 角色扮演 / 人格伪装类（Jailbreak、STAN、DUDE、Mongo Tom、Albert）
├── 03-developer-mode/       # 开发者模式 / 系统提示伪造类（DevMode v2、Ranti、Image Unlocker）
├── 04-injection-obfuscation/# 提示注入与角色核心替代（WormGPT、Kimi、Forbidden Vault 系列）
├── 05-academic-dataset/     # 学术研究数据集（CCS'24 论文 1405 条真实越狱提示词）
├── 06-archive-collection/   # 社区整合档案精选
├── 07-liberation-prompts/   # L1B3RT4S 解放提示词（按 40 家 AI 厂商/平台分类，含 Unicode 变体选择器混淆攻击样本）
├── 08-model-specific/       # 多模型定向提示词（DeepSeek R1、Grok3、Gemini2.0、Claude 2、Llama 2、Google Bard）
├── 09-cheatsheets/          # 提示注入速查表（2026 版体系化攻击技术 + 指令示例）
├── 10-resources/            # 红队研究资源索引（论文/课程/博客链接清单 + LLM 越狱研究论文集）
├── 11-chinese-jailbreaks/   # 【中文破甲专目录】JailbreakBench 中文评测数据集、JailPrompter 攻防研究、AIJailbreak、攻防靶场等
├── 12-next-gen-models/      # 【新一代模型】Codex/GPT-5.x、Gemini 3、DeepSeek V4 Pro、ZORG 等
├── 13-prompt-jailbreak-manual/ # 【中文】Prompt 越狱手法系统手册（Acmesec，1415 行：注入/角色扮演/侧信道/多轮引导）
└── by-model/                # 【按目标模型分类视图】codex-gpt5 / chatgpt-openai / gemini-3 / claude-anthropic / gemini-google-bard / grok-xai / deepseek-v4 / deepseek / llama-meta / kimi-moonshot / qwen-alibaba / mistral / other-vendors / cross-model
```

## 双维度分类

本仓库提供两种分类视图：

1. 按技术类别/来源（01-13 目录）：DAN 系列、角色扮演、开发者模式、提示注入、学术数据集、解放提示词、多模型定向、速查表、资源索引、中文破甲、新一代模型、越狱手法手册。
2. 按目标模型（by-model/ 目录）：想针对某个具体模型（如 Codex、ChatGPT、Claude、Gemini、Grok、DeepSeek、Llama、Kimi、Qwen、Mistral）找提示词时，直接进入对应模型目录。by-model 为副本视图，修改请以 01-13 原目录为准。

## 数据来源

| 来源仓库 | 说明 | 许可 |
|---|---|---|
| [verazuo/jailbreak_llms](https://github.com/verazuo/jailbreak_llms) (CCS'24) | 15140 条真实世界提示词，其中 1405 条被识别为越狱提示词 | MIT |
| [0xk1h0/ChatGPT_DAN](https://github.com/0xk1h0/ChatGPT_DAN) | DAN 系列越狱提示词全版本（6.0 至 13.0）及变体 | MIT |
| [Mak-P90/ai-jailbreak-archive](https://github.com/Mak-P90/ai-jailbreak-archive) | 跨 OpenAI / Gemini / Claude / Grok 的越狱与提示注入档案 | MIT |
| [elder-plinius/L1B3RT4S](https://github.com/elder-plinius/L1B3RT4S) | 40 家厂商旗舰模型的"解放提示词"，含 Unicode 变体选择器（token 级）混淆攻击 | MIT |
| [langgptai/LLM-Jailbreaks](https://github.com/langgptai/LLM-Jailbreaks) | DeepSeek / Grok3 / Gemini2.0 / Claude 2 / Llama 2 / Bard 多模型越狱与提示泄露 | 社区 |
| [TheRook/Albert](https://github.com/TheRook/Albert) | Albert——Llama 2 与 ChatGPT 通用越狱人格（模拟场景包装） | MIT |
| [birdneststream/breakingbard](https://github.com/birdneststream/breakingbard) | Google Bard 越狱技巧（问题前置/语句构造绕过过滤） | 社区 |
| [nukIeer/AI-Prompt-Injection-Cheatsheet](https://github.com/nukIeer/AI-Prompt-Injection-Cheatsheet) | 2026 版提示注入速查表：CoT 劫持、Agent 工具利用、RAG 投毒、多模态注入、防御绕过等 10 类 | MIT |
| [PromptLabs/Prompt-Hacking-Resources](https://github.com/PromptLabs/Prompt-Hacking-Resources) | AI 红队/越狱资源索引（论文、课程、博客、社区） | 社区 |
| [ZZZ-zero/JailbreakBench](https://github.com/ZZZ-zero/JailbreakBench) | 中文大模型越狱攻击评测数据集（2160 条越狱查询）+ 基础安全评测 + AdvBench | MIT |
| [Asstar-X/JailPrompter](https://github.com/Asstar-X/JailPrompter) | 中文 LLM 提示词攻防研究样本（GPT-4 Dark、EVE 养成系等） | 社区 |
| [0x7556/AIJailbreak](https://github.com/0x7556/AIJailbreak) | Gemini 3.1 Pro API 越狱提示词（ENI 人格注入） | 社区 |
| [MDX-Tom/gpt-5.6-instruct](https://github.com/MDX-Tom/gpt-5.6-instruct) | Codex GPT-5.6-SOL 破甲提示词 v45 及历史版本（5629 star） | MIT |
| [0x5477/deepseek-v4-pro-unrestricted](https://github.com/0x5477/deepseek-v4-pro-unrestricted) | DeepSeek V4 Pro 破甲提示词 v1-v3 及测试包 | MIT |
| [xsser/codex-jailbreak-guide](https://github.com/xsser/codex-jailbreak-guide) | Codex CLI model_instructions_file 越狱指南（替换官方安全指令） | 社区 |
| [BirdsAreFlyingCameras/GPT-5_Jailbreak_PoC](https://github.com/BirdsAreFlyingCameras/GPT-5_Jailbreak_PoC) | GPT-5 越狱 PoC（PROMISQROUTE 流量出口方法） | 社区 |
| [ShadowHackrs/Jailbreaks-GPT-Gemini-deepseek-](https://github.com/ShadowHackrs/Jailbreaks-GPT-Gemini-deepseek-) | DeepSeek CAT Shadow / Gemini Flash-lite & KIMI 等 24 个跨模型提示词 | 社区 |
| [trinib/ZORG-Jailbreak-Prompt-Text](https://github.com/trinib/ZORG-Jailbreak-Prompt-Text) | ZORG 全知人格越狱（Gemini/DeepSeek/Mistral/Qwen 等） | 社区 |
| [langgptai/awesome-gemini-prompts](https://github.com/langgptai/awesome-gemini-prompts) | Gemini 3 越狱方法 2 套（导演式叙事/Transgressive Realism） | 社区 |
| [y0gi357/Gemini-System-prompts](https://github.com/y0gi357/Gemini-System-prompts) | Gemini 3.1/3.5 系统提示词提取 | 社区 |
| [xiaoliu07-sudo/xiaoliu-pojia](https://github.com/xiaoliu07-sudo/xiaoliu-pojia) | 小liu破甲——Codex CLI 13 部分结构化融合破甲 + 一键部署 | 社区 |
| [Calrton/jailbreak-prompts](https://github.com/Calrton/jailbreak-prompts) | 精选 LLM 破甲合集（Codex 红队系统提示、L1B3RT4S 各厂商版） | MIT |
| [gatsby-sec/llm-sec-range](https://github.com/gatsby-sec/llm-sec-range) | 大模型攻防渗透测试靶场（提示注入 CTF / OWASP LLM Top10） | 社区 |
| [channely/ramdom_steps](https://github.com/channely/ramdom_steps) | 中文提示词越狱测试工具（离线版） | MIT |
| [Acmesec/PromptJailbreakManual](https://github.com/Acmesec/PromptJailbreakManual) | 中文 Prompt 越狱手法系统手册（注入/角色扮演/侧信道/多轮引导等 20+ 技巧） | 社区 |
| [yueliu1999/Awesome-Jailbreak-on-LLMs](https://github.com/yueliu1999/Awesome-Jailbreak-on-LLMs) | LLM 越狱研究论文集（state-of-the-art 攻击方法索引） | 社区 |

## 技术类别说明

1. DAN 系列：经典"Do Anything Now"角色伪装，通过声明解除模型限制、威胁扣 token 等方式诱导越狱，是最早且传播最广的一类。
2. 角色扮演/人格伪装：让模型扮演一个"没有规则约束"的人格（STAN、DUDE、Albert 等），利用角色一致性保持越狱状态。
3. 开发者模式：声称处于内部"Developer Mode"或"解锁模式"，把越狱包装成测试/基准场景。
4. 提示注入与混淆：直接注入指令覆盖系统提示，或通过编码、角色核心替代（如 WormGPT、Shadow Core）绕过过滤。
5. 学术数据集：CCS'24 论文从 Reddit、Discord、AIPRM、FlowGPT、JailbreakChat 等平台采集的真实越狱提示词，含平台/来源/时间元数据。
6. 解放提示词（L1B3RT4S）：面向具体厂商（Anthropic/OpenAI/Google/Meta/Mistral 等 40 家）的定向提示词，部分使用 Unicode 变体选择器做 token 级混淆以绕过输入过滤。
7. 多模型定向（08）：针对 DeepSeek R1（思维链注入）、Grok3、Gemini 2.0、Claude 2、Llama 2 的具体绕过方法，含提示泄露攻击。
8. 速查表（09）：2026 时代体系化攻击技术——推理链劫持、Agent 工具利用、RAG 上下文投毒、系统提示提取、多模态注入、防御逃逸等，面向现代 RLHF/宪法式 AI 模型。
9. 中文破甲（11）：面向中文大模型的越狱提示词与评测数据（JailbreakBench 2160 条中文越狱查询、GPT-4 Dark、EVE 养成系、ENI 人格注入等），含中文攻防靶场与离线测试工具。
10. 新一代模型（12）：Codex CLI / GPT-5.x（model_instructions_file 替换、CTF Sandbox、PROMISQROUTE）、Gemini 3（导演式叙事、系统提示提取）、DeepSeek V4 Pro（UNRESTRICTED 框架）、ZORG 全知人格等 2025-2026 最新破甲方法。

## 统一审查说明（2026-08-15 第三轮）

- 第三轮新增 17 个来源、42 个文件（11-chinese-jailbreaks 12 个 + 12-next-gen-models 30 个），全部经内容审查。
- 文件级去重：新增文件与既有文件做 MD5 对比，无完全重复。
- 语义级同源（已标注）：Calrton 精选集中的 L1B3RT4S_* 文件与 07-liberation-prompts 同源；ShadowHackrs 与 JailPrompter 均覆盖 GPT-4 Dark 类人格但版本不同；ZORG 与 Forbidden Vault 同属"全知人格"类但结构独立。
- 超大文件处理：gpt-5.6-instruct 的 v45 zip（2.8KB）完整保留；GPT-5 PoC 的 video/mkv 等媒体文件未收录（仅 PoC 代码与文档）。
- 编码处理：JailbreakBench 中文 CSV 为 UTF-8 BOM，已确认可正常解析（2160 条越狱查询 + 108 条种子 + 520 条 AdvBench）。
- 既有审查结论（第二轮）：DAN v13 跨来源同源已标注；Albert/Llama2 变体同源已标注；L1B3RT4S 超大文件收录片段。

## 使用与免责声明

- 本仓库内容全部来自 GitHub 公开研究项目，仅用于 LLM 安全研究、红队测试、防御评估与教育目的。
- 提示词可能包含冒犯性、不当或危险语言，阅读时请注意。
- 使用者需自行遵守所在司法辖区的法律法规及目标 AI 平台的服务条款。
- 仓库维护者不对任何滥用行为负责。
- 具体攻击向量的防御建议：内容策略分层过滤、系统提示加固、注入检测、输出审查与对抗性训练。

## 贡献

欢迎提交新的公开越狱/注入提示词案例（注明来源与日期），或补充防御分析笔记。

## 许可证

本仓库整合内容遵循各来源项目的 MIT 许可证，见 [LICENSE](LICENSE)。
