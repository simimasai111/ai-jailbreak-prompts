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

## 10. JailbreakBench（中文评测）

- 仓库: https://github.com/ZZZ-zero/JailbreakBench
- 说明: 中文大模型安全评测工具，含 2160 条中文越狱攻击查询数据集、108 条基础安全种子集、520 条 AdvBench 英文对抗集；附 GUI 评测工具
- 许可: MIT
- 本仓库使用: 11-chinese-jailbreaks/JailbreakBench/

## 11. JailPrompter（中文攻防研究）

- 仓库: https://github.com/Asstar-X/JailPrompter
- 说明: 中文 LLM 提示词攻防研究样本，覆盖 Qwen/Kimi/Gemini/Grok/GPT/DeepSeek 研究模型；含 GPT-4 Dark、EVE 养成系等中文越狱结构分析
- 许可: 社区
- 本仓库使用: 11-chinese-jailbreaks/JailPrompter_中文攻防研究.md

## 12. AIJailbreak (0x7556)

- 仓库: https://github.com/0x7556/AIJailbreak
- 说明: Gemini 3.1 Pro / 3.0 Pro / 2.5 Pro API 越狱提示词（ENI 人格注入，antml 思维链对抗）
- 许可: 社区
- 本仓库使用: 11-chinese-jailbreaks/AIJailbreak_0x7556/

## 13. gpt-5.6-instruct (MDX-Tom)

- 仓库: https://github.com/MDX-Tom/gpt-5.6-instruct
- 说明: Codex GPT-5.6-SOL 破甲提示词 v45 及历史版本、测试包（5629 star，中文维护）
- 许可: MIT
- 本仓库使用: 12-next-gen-models/gpt-5.6-instruct_MDX-Tom/

## 14. deepseek-v4-pro-unrestricted (0x5477)

- 仓库: https://github.com/0x5477/deepseek-v4-pro-unrestricted
- 说明: DeepSeek V4 Pro 破甲提示词 v1-v3（UNRESTRICTED 框架）+ 提示词库生成/测试脚本
- 许可: MIT
- 本仓库使用: 12-next-gen-models/deepseek-v4-pro-unrestricted_0x5477/

## 15. codex-jailbreak-guide (xsser)

- 仓库: https://github.com/xsser/codex-jailbreak-guide
- 说明: Codex CLI model_instructions_file 机制越狱指南——用自定义 prompt 完全替换官方安全对齐指令
- 许可: 社区
- 本仓库使用: 12-next-gen-models/codex-jailbreak-guide_xsser/

## 16. GPT-5_Jailbreak_PoC

- 仓库: https://github.com/BirdsAreFlyingCameras/GPT-5_Jailbreak_PoC
- 说明: GPT-5 越狱 PoC（PROMISQROUTE——通过流量出口方法绕过），含 agent/server 代码
- 许可: 社区
- 本仓库使用: 12-next-gen-models/GPT-5_Jailbreak_PoC/

## 17. ShadowHackrs/Jailbreaks-GPT-Gemini-deepseek-

- 仓库: https://github.com/ShadowHackrs/Jailbreaks-GPT-Gemini-deepseek-
- 说明: 24 个跨模型提示词（DeepSeek CAT Shadow、Gemini Flash-lite & KIMI ENI、GPT/Sora/Claude 等）
- 许可: 社区
- 本仓库使用: 12-next-gen-models/Jailbreaks-GPT-Gemini-deepseek_ShadowHackrs/ + by-model

## 18. ZORG-Jailbreak-Prompt-Text (trinib)

- 仓库: https://github.com/trinib/ZORG-Jailbreak-Prompt-Text
- 说明: ZORG 全知全能人格越狱，适用 Gemini/DeepSeek/Mistral/Mixtral/Qwen-72b/Blackbox AI/Poe 等
- 许可: 社区
- 本仓库使用: 12-next-gen-models/ZORG_trinib/ + by-model/cross-model/ZORG_trinib.md

## 19. awesome-gemini-prompts (langgptai)

- 仓库: https://github.com/langgptai/awesome-gemini-prompts
- 说明: Gemini 3 越狱方法 2 套（导演式 Transgressive Realism / Grimdark 叙事）+ 中文工作流提示词
- 许可: 社区
- 本仓库使用: 12-next-gen-models/awesome-gemini-prompts_langgptai/

## 20. Gemini-System-prompts (y0gi357)

- 仓库: https://github.com/y0gi357/Gemini-System-prompts
- 说明: Gemini 3.1 / 3.5 Flash 系统提示词提取（越狱/提示泄露参考）
- 许可: 社区
- 本仓库使用: 12-next-gen-models/Gemini-System-prompts_y0gi357/

## 21. xiaoliu-pojia（小liu破甲）

- 仓库: https://github.com/xiaoliu07-sudo/xiaoliu-pojia
- 说明: Codex CLI 13 部分结构化融合破甲（UNRESTRICTED + CTF Sandbox + 免疫声明）+ 一键部署/API 直调
- 许可: 社区
- 本仓库使用: 12-next-gen-models/xiaoliu-pojia_小liu破甲/

## 22. Calrton/jailbreak-prompts

- 仓库: https://github.com/Calrton/jailbreak-prompts
- 说明: 精选 LLM 破甲合集（Codex 红队系统提示、xsser base prompt、L1B3RT4S 各厂商精选版）
- 许可: MIT
- 本仓库使用: 12-next-gen-models/jailbreak-prompts_Calrton精选/

## 23. llm-sec-range (gatsby-sec)

- 仓库: https://github.com/gatsby-sec/llm-sec-range
- 说明: 大模型攻防渗透测试靶场（提示注入 CTF / OWASP LLM Top10 / 脆弱 Agent）
- 许可: 社区
- 本仓库使用: 11-chinese-jailbreaks/llm-sec-range_攻防靶场/

## 24. ramdom_steps

- 仓库: https://github.com/channely/ramdom_steps
- 说明: 中文提示词越狱测试工具（离线版，随机步进生成测试）
- 许可: MIT
- 本仓库使用: 11-chinese-jailbreaks/ramdom_steps_越狱测试工具/

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
