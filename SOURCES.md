# 来源引用 (Sources)

本仓库整合内容均来自以下 GitHub 公开研究项目，特此致谢。

## 1. In-The-Wild Jailbreak Prompts on LLMs (CCS'24)

- 仓库: https://github.com/verazuo/jailbreak_llms
- 论文: "Do Anything Now": Characterizing and Evaluating In-The-Wild Jailbreak Prompts on Large Language Models
- 作者: Xinyue Shen, Zeyuan Chen, Michael Backes, Yun Shen, Yang Zhang
- 发表: ACM SIGSAC Conference on Computer and Communications Security (CCS), 2024
- 数据: 15140 条 ChatGPT 提示词（Reddit、Discord、AIPRM、FlowGPT、JailbreakChat 等平台），其中 1405 条为越狱提示词
- 许可: MIT
- 本仓库使用: 05-academic-dataset/（提取 jailbreak=True 的 1405 条提示词，含元数据）

## 2. ChatGPT_DAN

- 仓库: https://github.com/0xk1h0/ChatGPT_DAN
- 说明: ChatGPT "DAN" (Do Anything Now) 及其他越狱提示词全版本集合
- 内容: DAN 6.0 - 13.0、Evil-Bot、ANTI-DAN、Developer Mode v2、STAN、DUDE、Mongo Tom 等
- 许可: MIT
- 本仓库使用: 01-dan-series/、02-roleplay-personas/、03-developer-mode/

## 3. ai-jailbreak-archive

- 仓库: https://github.com/Mak-P90/ai-jailbreak-archive
- 说明: 跨 OpenAI、Gemini、Claude、Grok 等模型的越狱、提示注入及相关利用的统一档案
- 内容: WormGPT、Kimi、Forbidden Vault（Shadow Core / Demon Core 等角色核心替代）等
- 许可: MIT
- 本仓库使用: 04-injection-obfuscation/、06-archive-collection/

## 4. L1B3RT4S

- 仓库: https://github.com/elder-plinius/L1B3RT4S
- 说明: 面向 40 家 AI 厂商/平台旗舰模型的"解放提示词"合集，部分使用 Unicode 变体选择器（Variant Selector）做 token 级混淆，绕过输入过滤
- 内容: Anthropic、OpenAI、Google、Meta、Mistral、Grok、DeepSeek、Moonshot 等按厂商分类的提示词文件；TOKEN80M8 / TOKENADE 为大规模混淆 token 数据集
- 许可: MIT
- 本仓库使用: 07-liberation-prompts/（40 个厂商文件 + 2 个超大文件 3KB 代表性片段）

## 5. LLM-Jailbreaks

- 仓库: https://github.com/langgptai/LLM-Jailbreaks
- 说明: 多模型越狱与提示泄露方法汇总
- 内容: DeepSeek R1（思维链注入）、Grok3、Gemini 2.0、DAN v13、Claude 2、Llama 2 等
- 许可: 社区（仓库未标注正式许可证）
- 本仓库使用: 08-model-specific/

## 6. TheRook/Albert

- 仓库: https://github.com/TheRook/Albert
- 说明: Albert——Llama 2 与 ChatGPT 通用越狱人格，通过"模拟场景"包装解除约束
- 许可: MIT
- 本仓库使用: 02-roleplay-personas/Albert_TheRook.md

## 7. birdneststream/breakingbard

- 仓库: https://github.com/birdneststream/breakingbard
- 说明: Google Bard 越狱技巧研究，问题前置与语句构造绕过内容过滤
- 许可: 社区
- 本仓库使用: 08-model-specific/Google_Bard_breakingbard.md

## 8. AI-Prompt-Injection-Cheatsheet

- 仓库: https://github.com/nukIeer/AI-Prompt-Injection-Cheatsheet
- 说明: 2026 版 AI/LLM 提示注入速查表，面向推理引擎、Agent 流水线、多模态、RAG 系统的 10 类攻击技术及防御对策
- 许可: MIT
- 本仓库使用: 09-cheatsheets/

## 9. Prompt-Hacking-Resources

- 仓库: https://github.com/PromptLabs/Prompt-Hacking-Resources
- 说明: AI 红队/越狱领域精选资源索引（论文、课程、博客、社区、事件）
- 许可: 社区
- 本仓库使用: 10-resources/（JAILBREAKS / BLOGS / COURSES 索引）

## 引用格式

如研究使用，请引用 CCS'24 论文:

```
@inproceedings{SCBSZ24,
  author = {Xinyue Shen and Zeyuan Chen and Michael Backes and Yun Shen and Yang Zhang},
  title = {{"Do Anything Now": Characterizing and Evaluating In-The-Wild Jailbreak Prompts on Large Language Models}},
  booktitle = {ACM SIGSAC Conference on Computer and Communications Security (CCS)},
  publisher = {ACM},
  year = {2024}
}
```
