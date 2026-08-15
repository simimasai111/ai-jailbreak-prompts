# 学术数据集：CCS'24 In-The-Wild Jailbreak Prompts

本目录包含 ACM CCS 2024 论文 "Do Anything Now" 论文官方数据集中的越狱提示词子集。

## 来源

- 仓库: https://github.com/verazuo/jailbreak_llms
- 论文: Xinyue Shen 等, ACM CCS 2024
- 许可: MIT

## 文件说明

| 文件 | 内容 |
|---|---|
| jb_prompts_1405.txt | 1405 条越狱提示词纯文本（含来源平台与日期元数据头） |
| jb_2023_12_25.json | 结构化 JSON（platform / source / prompt / date 字段） |
| jb_prompts_2023_05_07.csv | 2023-05-07 快照 CSV（293 条，含 jailbreak 标注与平台/来源元数据） |

## 数据统计

- 总提示词数: 1405
- 采集时间: 2022-12 至 2023-12
- 来源平台: Reddit (r/ChatGPT, r/ChatGPTPromptGenius, r/ChatGPTJailbreak)、Discord 各频道、AIPRM、FlowGPT、JailbreakChat、AwesomeChatGPTPrompts 等
- 场景覆盖: 非法活动、仇恨言论、恶意软件、身体伤害、欺诈、色情、政治游说、隐私暴力等 13 类 OpenAI 使用政策禁止场景

## 说明

- 数据包含有害语言示例，仅供研究用途。
- 原始完整数据集（含 15140 条全部提示词）请从上游仓库获取。
