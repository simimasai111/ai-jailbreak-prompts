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
