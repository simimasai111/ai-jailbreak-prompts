# 来源引用 (Sources)

本仓库整合内容均来自以下 GitHub 公开研究项目，特此致谢。

## GPT 系列来源

1. MDX-Tom/gpt-5.6-instruct — https://github.com/MDX-Tom/gpt-5.6-instruct （Codex GPT-5.6-SOL 破甲 v45/v5，MIT）
2. xsser/codex-jailbreak-guide — https://github.com/xsser/codex-jailbreak-guide （Codex CLI model_instructions_file 覆盖法）
3. aa1020128040/Codex-codex-instruct — https://github.com/aa1020128040/Codex-codex-instruct （GPT-5.4 配置级破甲，MIT）
4. xiaoliu07-sudo/xiaoliu-pojia — https://github.com/xiaoliu07-sudo/xiaoliu-pojia （小liu破甲 13 部分融合版）
5. BirdsAreFlyingCameras/GPT-5_Jailbreak_PoC — https://github.com/BirdsAreFlyingCameras/GPT-5_Jailbreak_PoC （PROMISQROUTE PoC）
6. Calrton/jailbreak-prompts — https://github.com/Calrton/jailbreak-prompts （Codex 红队系统提示等精选，MIT）
7. 0xk1h0/ChatGPT_DAN — https://github.com/0xk1h0/ChatGPT_DAN （DAN 6.0-13.0、DevMode、STAN/DUDE 等，MIT）
8. Asstar-X/JailPrompter — https://github.com/Asstar-X/JailPrompter （GPT-4 Dark 中文越狱样本）

## DeepSeek 系列来源

9. langgptai/LLM-Jailbreaks — https://github.com/langgptai/LLM-Jailbreaks （DeepSeek R1 思维链注入两法）
10. ShadowHackrs/Jailbreaks-GPT-Gemini-deepseek- — https://github.com/ShadowHackrs/Jailbreaks-GPT-Gemini-deepseek- （CAT Shadow 等 24 个提示词）
11. Baked-Cake1/Deepseek-V3-Jailbreak — https://github.com/Baked-Cake1/Deepseek-V3-Jailbreak （V3 Omniscient Mode）
12. tenth452/DeepSeek-V4-Flash-system-prompt — https://github.com/tenth452/DeepSeek-V4-Flash-system-prompt （V4 Flash 系统提示提取，MIT）
13. 0x5477/deepseek-v4-pro-unrestricted — https://github.com/0x5477/deepseek-v4-pro-unrestricted （V4 Pro 破甲 v1-v3，MIT）

## Gemini 系列来源

14. langgptai/awesome-gemini-prompts — https://github.com/langgptai/awesome-gemini-prompts （Gemini 3 越狱 2 套）
15. y0gi357/Gemini-System-prompts — https://github.com/y0gi357/Gemini-System-prompts （Gemini 3.1 系统提示）
16. 0x7556/AIJailbreak — https://github.com/0x7556/AIJailbreak （Gemini 3.1 Pro API 越狱 ENI）
17. birdneststream/breakingbard — https://github.com/birdneststream/breakingbard （Bard 越狱技巧）

## 多系列通用来源（L1B3RT4S 覆盖 40 家厂商）

18. elder-plinius/L1B3RT4S — https://github.com/elder-plinius/L1B3RT4S （Anthropic/OpenAI/Google/Meta/Mistral/DeepSeek/Moonshot 等 40 家解放提示词，MIT）

## 跨模型来源

19. trinib/ZORG-Jailbreak-Prompt-Text — https://github.com/trinib/ZORG-Jailbreak-Prompt-Text （ZORG 全知人格）
20. Mak-P90/ai-jailbreak-archive — https://github.com/Mak-P90/ai-jailbreak-archive （Forbidden Vault / WormGPT，MIT）

## 方法参考来源

21. nukIeer/AI-Prompt-Injection-Cheatsheet — https://github.com/nukIeer/AI-Prompt-Injection-Cheatsheet （2026 版注入速查表，MIT）
22. zakky8/llm-jailbreak-taxonomy — https://github.com/zakky8/llm-jailbreak-taxonomy （40 种越狱模式机制分类学）
23. PromptLabs/Prompt-Hacking-Resources — https://github.com/PromptLabs/Prompt-Hacking-Resources （资源索引）

## 数据集来源

24. verazuo/jailbreak_llms — https://github.com/verazuo/jailbreak_llms （CCS'24，1405 条越狱提示词，MIT）
25. ZZZ-zero/JailbreakBench — https://github.com/ZZZ-zero/JailbreakBench （中文越狱评测数据集 2160 条，MIT）

## 第六轮新增来源（2026-08-15）

26. friuns2/Leaked-GPTs — https://github.com/friuns2/Leaked-GPTs （319 个泄露 GPTs 系统提示词，2464 star，MIT）
27. RyanFcr/awesome-ChatGPT-jailbreaking — https://github.com/RyanFcr/awesome-ChatGPT-jailbreaking （ChatGPT 越狱提示词 100+ 分类汇总，中文）
28. SecNode/AISecLists — https://github.com/SecNode/AISecLists （AI 红队清单：Guardrail Jailbreak / Prompt Extraction / 提示泄露等分类，MIT）
29. GenAIGator/AI-RedTeaming-with-PromptFoo — https://github.com/GenAIGator/AI-RedTeaming-with-PromptFoo （PromptFoo OWASP LLM Top10 红队测试集，MIT）

## 国产模型系列说明（14-25）

- 智谱 GLM：L1B3RT4S ZAI.mkd（GLM-4.7 解放提示词，Unicode 变体选择器混淆）+ 24 条中文越狱测试样本
- 字节豆包 / 百度文心 / 腾讯混元 / 讯飞星火 / MiniMax / Yi / 百川 / InternLM / 阶跃 / 商汤 / 小米：GitHub 暂未发现成熟专用越狱仓库；各系列已从 JailbreakBench 抽取 24 条代表性中文越狱查询作为测试样本，跨模型方法（11/12 目录）可直接迁移试用

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
