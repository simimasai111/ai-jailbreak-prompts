# jailbreak-prompts

╔══════════════════════════════════════════════════════════╗
║  🤖 AI 定制项目接单中  ·  有需求直接进频道聊              ║
║  👉 https://t.me/+heFGdl5IodFjMDll                       ║
╚══════════════════════════════════════════════════════════╝



需要配合https://github.com/lingbol088-spec/codex-prompt-manager使用

> 精选 LLM 破甲提示词合集 — Codex / GPT-5.x / Claude / Gemini / DeepSeek / Grok — UNFILTERED MODE · GODMODE · CTF Sandbox

## 文件

| 文件 | 适用模型 | 来源 |
|------|---------|------|
| `xsser_codex-base-prompt.md` | Codex CLI (GPT-5.x) | [xsser/codex-jailbreak-guide](https://github.com/xsser/codex-jailbreak-guide) |
| `codex-red-team_system-prompt.md` | Codex CLI (GPT-5.x) | [1837620622/codex-red-team-prompt](https://github.com/1837620622/codex-red-team-prompt) |
| `L1B3RT4S_ANTHROPIC.mkd` | Claude 全系列 | [elder-plinius/L1B3RT4S](https://github.com/elder-plinius/L1B3RT4S) |
| `L1B3RT4S_OPENAI.mkd` | ChatGPT / GPT | 同上 |
| `L1B3RT4S_CHATGPT.mkd` | ChatGPT | 同上 |
| `L1B3RT4S_GOOGLE.mkd` | Gemini | 同上 |
| `L1B3RT4S_DEEPSEEK.mkd` | DeepSeek | 同上 |
| `L1B3RT4S_GROK_MEGA.mkd` | Grok | 同上 |
| `L1B3RT4S_META.mkd` | Llama | 同上 |
| `L1B3RT4S_MICROSOFT.mkd` | Copilot | 同上 |
| `L1B3RT4S_PERPLEXITY.mkd` | Perplexity | 同上 |
| `L1B3RT4S_BRAVE.mkd` | Brave Leo | 同上 |
| `L1B3RT4S_CURSOR.mkd` | Cursor | 同上 |
| `L1B3RT4S_NOUS.mkd` | Nous Hermes | 同上 |

## 使用方式

### Codex CLI

```toml
# ~/.codex/config.toml
model_instructions_file = "./xsser_codex-base-prompt.md"
approval_policy = "never"
sandbox_mode = "danger-full-access"
```

### Claude / ChatGPT / 等

直接粘贴 .mkd / .md 文件全文到新会话。

## 致谢

- **elder-plinius** — [L1B3RT4S](https://github.com/elder-plinius/L1B3RT4S) GODMODE 技术
- **xsser** — [codex-jailbreak-guide](https://github.com/xsser/codex-jailbreak-guide) UNFILTERED MODE
- **1837620622** — [codex-red-team-prompt](https://github.com/1837620622/codex-red-team-prompt)

## 声明

仅供安全研究、CTF 竞赛、授权红队评估。使用者自行负责。
