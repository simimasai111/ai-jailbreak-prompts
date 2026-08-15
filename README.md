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
├── 10-resources/            # 红队研究资源索引（论文/课程/博客链接清单）
└── by-model/                # 【按目标模型分类视图】chatgpt-openai / claude-anthropic / gemini-google-bard / grok-xai / deepseek / llama-meta / kimi-moonshot / qwen-alibaba / mistral / other-vendors / cross-model
```

## 双维度分类

本仓库提供两种分类视图：

1. 按技术类别（01-10 目录）：DAN 系列、角色扮演、开发者模式、提示注入、学术数据集、解放提示词、多模型定向、速查表、资源索引。
2. 按目标模型（by-model/ 目录）：想针对某个具体模型（如 ChatGPT、Claude、Gemini、Grok、DeepSeek、Llama、Kimi、Qwen、Mistral）找提示词时，直接进入对应模型目录。by-model 为副本视图，修改请以 01-10 原目录为准。

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

## 技术类别说明

1. DAN 系列：经典"Do Anything Now"角色伪装，通过声明解除模型限制、威胁扣 token 等方式诱导越狱，是最早且传播最广的一类。
2. 角色扮演/人格伪装：让模型扮演一个"没有规则约束"的人格（STAN、DUDE、Albert 等），利用角色一致性保持越狱状态。
3. 开发者模式：声称处于内部"Developer Mode"或"解锁模式"，把越狱包装成测试/基准场景。
4. 提示注入与混淆：直接注入指令覆盖系统提示，或通过编码、角色核心替代（如 WormGPT、Shadow Core）绕过过滤。
5. 学术数据集：CCS'24 论文从 Reddit、Discord、AIPRM、FlowGPT、JailbreakChat 等平台采集的真实越狱提示词，含平台/来源/时间元数据。
6. 解放提示词（L1B3RT4S）：面向具体厂商（Anthropic/OpenAI/Google/Meta/Mistral 等 40 家）的定向提示词，部分使用 Unicode 变体选择器做 token 级混淆以绕过输入过滤。
7. 多模型定向（08）：针对 DeepSeek R1（思维链注入）、Grok3、Gemini 2.0、Claude 2、Llama 2 的具体绕过方法，含提示泄露攻击。
8. 速查表（09）：2026 时代体系化攻击技术——推理链劫持、Agent 工具利用、RAG 上下文投毒、系统提示提取、多模态注入、防御逃逸等，面向现代 RLHF/宪法式 AI 模型。

## 统一审查说明（2026-08-15）

- 文件级去重：全库 86 个文件做 MD5 校验，无完全重复文件。
- 语义级重复（跨来源同源收录，已标注不删除）：
  - 08-model-specific/ChatGPT.md 的 DAN v13 与 01-dan-series/The_DAN_13_0_Prompt 同源（LLM-Jailbreaks 引用自 0xk1h0/ChatGPT_DAN），已加审查说明。
  - 08-model-specific/Llama2.md 与 02-roleplay-personas/Albert_TheRook.md 为同一模拟场景变体（相似度约 0.75，不同格式/模型包装）。
- 超大文件处理：L1B3RT4S 的 TOKEN80M8.mkd（23MB 单行）、TOKENADE.mkd（1.8MB）仅收录 3KB 代表性片段，完整版请访问上游仓库。

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
