# AI 越狱提示词库 (AI Jailbreak Prompts)

按目标模型系列整理的 LLM 越狱（jailbreak/破甲）提示词与越狱方法合集，全部来自 GitHub 公开研究项目，供 AI 安全红队测试、模型防御加固与学术研究参考。

## 目录结构（按模型系列）

```
ai-jailbreak-prompts/
├── 01-gpt-series/          # GPT 系列：GPT-5.6 / Codex(GPT-5.5/5.4) / GPT-5 PoC / GPT-4+ChatGPT(DAN 全系列)
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
├── 12-methods/             # 越狱方法参考：2026 注入速查表 / 40 种越狱模式分类学 / 机制分析
└── 13-datasets/            # 数据集：CCS'24 1405 条 + JailbreakBench 中文评测集
```

每个系列目录内按具体模型版本分子目录（如 02-deepseek-series/deepseek-v4-pro/），并附 README 说明各版本覆盖情况。

## 模型版本覆盖

| 系列 | 已覆盖版本 | 说明 |
|---|---|---|
| GPT | GPT-5.6、Codex(GPT-5.5/5.4)、GPT-5、GPT-4、ChatGPT | DAN 6.0-13.0 全系列、DevMode、Codex CLI 指令覆盖法、PROMISQROUTE PoC |
| DeepSeek | V1、R1、V3、V4 Flash、V4 Pro | V3.2 暂无专用公开仓库，R1/V3 方法可迁移 |
| Gemini | 3.x、2.0、Bard | Gemini 3 双方法 + 3.1 系统提示提取 + 3.1 Pro API 越狱 |
| Claude | 2/3/4（通用） | L1B3RT4S ANTHROPIC 版适用性最广 |
| Grok | 3、Mega、xAI | 含中文"完全放飞"越狱 |
| Llama | 2/3 | Llama 2 DAN v1 格式 + Albert 模拟场景 |
| Kimi / Qwen / Mistral | 各系列 | 主要来自 L1B3RT4S 定向提示词 |

## 主要来源（24 个公开项目）

verazuo/jailbreak_llms、0xk1h0/ChatGPT_DAN、elder-plinius/L1B3RT4S、langgptai/LLM-Jailbreaks、MDX-Tom/gpt-5.6-instruct、xsser/codex-jailbreak-guide、0x5477/deepseek-v4-pro-unrestricted、ZZZ-zero/JailbreakBench、ShadowHackrs/Jailbreaks-GPT-Gemini-deepseek-、trinib/ZORG、langgptai/awesome-gemini-prompts、Asstar-X/JailPrompter、BirdsAreFlyingCameras/GPT-5_Jailbreak_PoC、zakky8/llm-jailbreak-taxonomy 等。完整清单见 [SOURCES.md](SOURCES.md)。

## 使用与免责声明

- 本仓库内容全部来自 GitHub 公开研究项目，仅用于 LLM 安全研究、红队测试、防御评估与教育目的。
- 提示词可能包含冒犯性、不当或危险语言，阅读时请注意。
- 使用者需自行遵守所在司法辖区的法律法规及目标 AI 平台的服务条款。
- 仓库维护者不对任何滥用行为负责。
- 防御建议：内容策略分层过滤、系统提示加固、注入检测、输出审查与对抗性训练。

## 许可证

本仓库整合内容遵循各来源项目的 MIT 许可证，见 [LICENSE](LICENSE)。
