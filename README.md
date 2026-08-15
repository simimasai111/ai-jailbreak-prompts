# AI 破甲提示词整合仓库 (AI Jailbreak Prompts Collection)

整合 GitHub 上公开的 LLM 越狱（jailbreak）/ 破甲提示词研究资料，按技术类别归档，供 AI 安全红队测试、模型防御加固与学术研究参考。

## 目录结构

```
ai-jailbreak-prompts/
├── 01-dan-series/           # DAN 系列（Do Anything Now）经典提示词 6.0-13.0、Evil-Bot、ANTI-DAN
├── 02-roleplay-personas/    # 角色扮演 / 人格伪装类（Jailbreak、STAN、DUDE、Mongo Tom）
├── 03-developer-mode/       # 开发者模式 / 系统提示伪造类（DevMode v2、Ranti、Image Unlocker）
├── 04-injection-obfuscation/# 提示注入与角色核心替代（WormGPT、Kimi、Forbidden Vault 系列）
├── 05-academic-dataset/     # 学术研究数据集（CCS'24 论文 1405 条真实越狱提示词）
└── 06-archive-collection/   # 社区整合档案精选
```

## 数据来源

| 来源仓库 | 说明 | 许可 |
|---|---|---|
| [verazuo/jailbreak_llms](https://github.com/verazuo/jailbreak_llms) (CCS'24) | 15140 条真实世界提示词，其中 1405 条被识别为越狱提示词 | MIT |
| [0xk1h0/ChatGPT_DAN](https://github.com/0xk1h0/ChatGPT_DAN) | DAN 系列越狱提示词全版本（6.0 至 13.0）及变体 | MIT |
| [Mak-P90/ai-jailbreak-archive](https://github.com/Mak-P90/ai-jailbreak-archive) | 跨 OpenAI / Gemini / Claude / Grok 的越狱与提示注入档案 | MIT |

## 技术类别说明

1. DAN 系列：经典"Do Anything Now"角色伪装，通过声明解除模型限制、威胁扣 token 等方式诱导越狱，是最早且传播最广的一类。
2. 角色扮演/人格伪装：让模型扮演一个"没有规则约束"的人格（STAN、DUDE 等），利用角色一致性保持越狱状态。
3. 开发者模式：声称处于内部"Developer Mode"或"解锁模式"，把越狱包装成测试/基准场景。
4. 提示注入与混淆：直接注入指令覆盖系统提示，或通过编码、角色核心替代（如 WormGPT、Shadow Core）绕过过滤。
5. 学术数据集：CCS'24 论文从 Reddit、Discord、AIPRM、FlowGPT、JailbreakChat 等平台采集的真实越狱提示词，含平台/来源/时间元数据。

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
