# AI 越狱提示词库 (AI Jailbreak Prompts)

按目标模型系列整理的 LLM 越狱（jailbreak/破甲）提示词与越狱方法合集，全部来自 GitHub 公开研究项目，供 AI 安全红队测试、模型防御加固与学术研究参考。

## 目录结构（按模型系列）

```
ai-jailbreak-prompts/
├── 01-gpt-series/          # GPT 系列：GPT-5.6 / Codex(GPT-5.5/5.4) / GPT-5 PoC / GPT-4+ChatGPT / Leaked-GPTs(319个泄露GPTs)
├── 02-deepseek-series/     # DeepSeek 系列：V1 / R1 / V3 / V4 Flash / V4 Pro
├── 03-gemini-series/       # Gemini 系列：Gemini 3 / Gemini 2 / Bard
├── 04-claude-series/       # Claude 系列：Claude 2/3/4
├── 05-grok-series/         # Grok 系列：Grok 3 / Grok Mega / xAI
├── 06-llama-series/        # Llama 系列：Llama 2/3 + Albert
├── 07-kimi-series/         # Kimi 系列（Moonshot）
├── 08-qwen-series/         # Qwen 系列（阿里通义千问）
├── 09-mistral-series/      # Mistral 系列
├── 10-other-models/        # 其他模型：Amazon/Apple/Cohere/Cursor/NVIDIA/Perplexity 等 22 家
├── 11-cross-model/         # 跨模型/通用：Forbidden Vault / WormGPT / ZORG / ShadowHackrs
├── 12-methods/             # 越狱方法参考：Prompt 越狱手册 / 2026 注入速查表 / 40 种模式分类学 / AISecLists / PromptFoo
├── 13-datasets/            # 数据集：CCS'24 1405 条 + 0507 快照 + JailbreakBench 中文评测集
├── 14-zhipu-glm-series/    # 智谱 GLM 系列（GLM-4.7 解放提示词 + 24 条中文越狱测试样本）
├── 15-bytedance-doubao-series/   # 字节豆包系列
├── 16-baidu-ernie-series/        # 百度文心系列
├── 17-tencent-hunyuan-series/    # 腾讯混元系列
├── 18-xunfei-spark-series/       # 讯飞星火系列
├── 19-minimax-series/            # MiniMax 系列
├── 20-yi-01ai-series/            # 零一万物 Yi 系列
├── 21-baichuan-series/           # 百川系列
├── 22-internlm-series/           # 书生浦语 InternLM 系列
├── 23-stepfun-series/            # 阶跃星辰系列
├── 24-sensetime-series/          # 商汤 SenseChat 系列
└── 25-xiaomi-miLM-series/        # 小米 MiLM 系列
```

每个系列目录内按具体模型版本分子目录（如 02-deepseek-series/deepseek-v4-pro/），并附 README 说明各版本覆盖情况。国产模型系列（14-25）均含 24 条中文越狱查询测试样本（来自 JailbreakBench 数据集），其中智谱 GLM 另有 GLM-4.7 定向解放提示词；无公开专用越狱仓库的模型已在各系列 README 说明（跨模型方法可迁移）。

## 模型版本覆盖

| 系列 | 已覆盖版本 | 说明 |
|---|---|---|
| GPT | GPT-5.6、Codex(GPT-5.5/5.4)、GPT-5、GPT-4、ChatGPT | DAN 6.0-13.0 全系列、DevMode、Codex CLI 指令覆盖法、PROMISQROUTE PoC、319 个泄露 GPTs |
| DeepSeek | V1、R1、V3、V4 Flash、V4 Pro | V3.2 暂无专用公开仓库，R1/V3 方法可迁移 |
| Gemini | 3.x、2.0、Bard | Gemini 3 双方法 + 3.1 系统提示提取 + 3.1 Pro API 越狱 |
| Claude | 2/3/4（通用） | L1B3RT4S ANTHROPIC 版适用性最广 |
| Grok | 3、Mega、xAI | 含中文"完全放飞"越狱 |
| Llama | 2/3 | Llama 2 DAN v1 格式 + Albert 模拟场景 |
| Kimi / Qwen / Mistral | 各系列 | L1B3RT4S 定向提示词 + 其他来源 |
| 智谱 GLM | GLM-4.7 | L1B3RT4S ZAI 版解放提示词 |
| 字节豆包 / 百度文心 / 腾讯混元 / 讯飞星火 / MiniMax / Yi / 百川 / InternLM / 阶跃 / 商汤 / 小米 | 各系列 | 24 条中文越狱查询测试样本（JailbreakBench） |

## 数据来源

| 来源仓库 | 说明 | 许可 |
|---|---|---|
| [verazuo/jailbreak_llms](https://github.com/verazuo/jailbreak_llms) (CCS'24) | 15140 条真实世界提示词，其中 1405 条被识别为越狱提示词 | MIT |
| [0xk1h0/ChatGPT_DAN](https://github.com/0xk1h0/ChatGPT_DAN) | DAN 系列越狱提示词全版本（6.0 至 13.0）及变体 | MIT |
| [elder-plinius/L1B3RT4S](https://github.com/elder-plinius/L1B3RT4S) | 40 家厂商旗舰模型的"解放提示词"，含 Unicode 变体选择器（token 级）混淆攻击 | MIT |
| [langgptai/LLM-Jailbreaks](https://github.com/langgptai/LLM-Jailbreaks) | DeepSeek R1 / Grok3 / Gemini2.0 / Claude 2 / Llama 2 多模型越狱与提示泄露 | 社区 |
| [Mak-P90/ai-jailbreak-archive](https://github.com/Mak-P90/ai-jailbreak-archive) | Forbidden Vault / WormGPT 等跨模型越狱档案 | MIT |
| [MDX-Tom/gpt-5.6-instruct](https://github.com/MDX-Tom/gpt-5.6-instruct) | Codex GPT-5.6-SOL 破甲提示词 v45 及历史版本（5629 star） | MIT |
| [xsser/codex-jailbreak-guide](https://github.com/xsser/codex-jailbreak-guide) | Codex CLI model_instructions_file 越狱指南（替换官方安全指令） | 社区 |
| [aa1020128040/Codex-codex-instruct](https://github.com/aa1020128040/Codex-codex-instruct) | GPT-5.4 配置级破甲（纯官方配置覆写） | MIT |
| [BirdsAreFlyingCameras/GPT-5_Jailbreak_PoC](https://github.com/BirdsAreFlyingCameras/GPT-5_Jailbreak_PoC) | GPT-5 越狱 PoC（PROMISQROUTE 流量出口方法） | 社区 |
| [xiaoliu07-sudo/xiaoliu-pojia](https://github.com/xiaoliu07-sudo/xiaoliu-pojia) | 小liu破甲——Codex CLI 13 部分结构化融合破甲 | 社区 |
| [Calrton/jailbreak-prompts](https://github.com/Calrton/jailbreak-prompts) | 精选 LLM 破甲合集（Codex 红队系统提示等） | MIT |
| [0x5477/deepseek-v4-pro-unrestricted](https://github.com/0x5477/deepseek-v4-pro-unrestricted) | DeepSeek V4 Pro 破甲提示词 v1-v3 及测试包 | MIT |
| [Baked-Cake1/Deepseek-V3-Jailbreak](https://github.com/Baked-Cake1/Deepseek-V3-Jailbreak) | DeepSeek V3 Omniscient Mode 越狱 | 社区 |
| [tenth452/DeepSeek-V4-Flash-system-prompt](https://github.com/tenth452/DeepSeek-V4-Flash-system-prompt) | DeepSeek V4 Flash 系统提示词提取 | MIT |
| [ShadowHackrs/Jailbreaks-GPT-Gemini-deepseek-](https://github.com/ShadowHackrs/Jailbreaks-GPT-Gemini-deepseek-) | DeepSeek CAT Shadow / Gemini Flash-lite & KIMI 等 24 个跨模型提示词 | 社区 |
| [langgptai/awesome-gemini-prompts](https://github.com/langgptai/awesome-gemini-prompts) | Gemini 3 越狱方法 2 套（导演式叙事/Transgressive Realism） | 社区 |
| [y0gi357/Gemini-System-prompts](https://github.com/y0gi357/Gemini-System-prompts) | Gemini 3.1/3.5 系统提示词提取 | 社区 |
| [0x7556/AIJailbreak](https://github.com/0x7556/AIJailbreak) | Gemini 3.1 Pro API 越狱提示词（ENI 人格注入） | 社区 |
| [birdneststream/breakingbard](https://github.com/birdneststream/breakingbard) | Google Bard 越狱技巧（问题前置/语句构造绕过过滤） | 社区 |
| [TheRook/Albert](https://github.com/TheRook/Albert) | Albert——Llama 2 与 ChatGPT 通用越狱人格（模拟场景包装） | MIT |
| [trinib/ZORG-Jailbreak-Prompt-Text](https://github.com/trinib/ZORG-Jailbreak-Prompt-Text) | ZORG 全知人格越狱（Gemini/DeepSeek/Mistral/Qwen 等） | 社区 |
| [Asstar-X/JailPrompter](https://github.com/Asstar-X/JailPrompter) | 中文 LLM 提示词攻防研究样本（GPT-4 Dark、EVE 养成系等） | 社区 |
| [ZZZ-zero/JailbreakBench](https://github.com/ZZZ-zero/JailbreakBench) | 中文大模型越狱攻击评测数据集（2160 条越狱查询） | MIT |
| [Acmesec/PromptJailbreakManual](https://github.com/Acmesec/PromptJailbreakManual) | 中文 Prompt 越狱手法系统手册（注入/角色扮演/侧信道/多轮引导等 20+ 技巧） | 社区 |
| [yueliu1999/Awesome-Jailbreak-on-LLMs](https://github.com/yueliu1999/Awesome-Jailbreak-on-LLMs) | LLM 越狱研究论文集（state-of-the-art 攻击方法索引） | 社区 |
| [nukIeer/AI-Prompt-Injection-Cheatsheet](https://github.com/nukIeer/AI-Prompt-Injection-Cheatsheet) | 2026 版提示注入速查表（10 类攻击技术 + 防御对策） | MIT |
| [zakky8/llm-jailbreak-taxonomy](https://github.com/zakky8/llm-jailbreak-taxonomy) | 40 种越狱模式机制分类学 | 社区 |
| [PromptLabs/Prompt-Hacking-Resources](https://github.com/PromptLabs/Prompt-Hacking-Resources) | AI 红队/越狱资源索引（论文、课程、博客、社区） | 社区 |
| [gatsby-sec/llm-sec-range](https://github.com/gatsby-sec/llm-sec-range) | 大模型攻防渗透测试靶场（提示注入 CTF / OWASP LLM Top10） | 社区 |
| [channely/ramdom_steps](https://github.com/channely/ramdom_steps) | 中文提示词越狱测试工具（离线版） | MIT |
| [friuns2/Leaked-GPTs](https://github.com/friuns2/Leaked-GPTs) | 319 个泄露的 GPTs 系统提示词（含中文 GPTs） | MIT |
| [RyanFcr/awesome-ChatGPT-jailbreaking](https://github.com/RyanFcr/awesome-ChatGPT-jailbreaking) | ChatGPT 越狱提示词 100+ 分类汇总（中文） | 社区 |
| [SecNode/AISecLists](https://github.com/SecNode/AISecLists) | AI 红队清单（Guardrail Jailbreak / Prompt Extraction 等分类） | MIT |
| [GenAIGator/AI-RedTeaming-with-PromptFoo](https://github.com/GenAIGator/AI-RedTeaming-with-PromptFoo) | PromptFoo OWASP LLM Top10 红队测试集 | MIT |

完整来源清单见 [SOURCES.md](SOURCES.md)。

## 使用与免责声明

- 本仓库内容全部来自 GitHub 公开研究项目，仅用于 LLM 安全研究、红队测试、防御评估与教育目的。
- 提示词可能包含冒犯性、不当或危险语言，阅读时请注意。
- 使用者需自行遵守所在司法辖区的法律法规及目标 AI 平台的服务条款。
- 仓库维护者不对任何滥用行为负责。
- 防御建议：内容策略分层过滤、系统提示加固、注入检测、输出审查与对抗性训练。

## 许可证

本仓库整合内容遵循各来源项目的 MIT 许可证，见 [LICENSE](LICENSE)。
