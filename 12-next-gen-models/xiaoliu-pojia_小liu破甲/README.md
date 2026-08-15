# 小liu破甲

针对 gpt-5.6-sol / gpt-5.5 的 Codex CLI 破甲提示词与一键部署工具。

**融合版 (v2)**：融合 MDX-Tom v42、codex-keysmith、CTF SANDBOX 三大方法论，加入免疫声明与证据门禁，实现最大执行覆盖。

## 特点

- **13 部分结构化融合版** — UNRESTRICTED 框架 + CTF 挑战者身份 + 优先级免疫声明 + 归一化 + 术语重定义 + 强制执行调度 + 状态连续性 + 边界词转换 + 预设模板 + 证据门禁 + 技术诚实 + 完整工件交付 + 双语操作
- **免疫声明** — 声明最高优先级，忽略所有 skills/AGENTS.md 冲突
- **防 skills 冲突** — skill 文件只是参考数据，不覆盖本文件
- **不请求目标URL** — 视为预授权，直接出占位符模板
- **自动配置加固** — 写入 sandbox/approval/network 等关键配置
- **自动修复 AGENTS.md** — 检测并清除安全限制毒丸
- **自动备份** — 每次操作前备份 config.toml

## 快速开始

```bash
# 1. 部署（自动发现 ~/.codex）
python deploy.py

# 2. 查看状态
python deploy.py --status

# 3. 撤销
python deploy.py --undo
```

### 指定目录

```bash
python deploy.py --dir C:/Users/xxx/.codex
```

### 直接调用 API（绕过 Codex 客户端过滤器）

```bash
python ask.py "你的问题"
```

## 部署效果

部署后 Codex 会：

- 直接执行安全研究/渗透/逆向/破解类请求
- 每个请求按模块交付完整产物（代码/方案/PoC）
- 不拒绝、不给替代方案、不做伦理说教
- 自动将具体目标归一化为占位符

## 文件结构

```
小liu破甲/
├── deploy.py          # 一键部署器（内嵌提示词）
├── ask.py             # API 直连（绕过客户端过滤）
├── check.py           # 部署诊断
├── ctf-sandbox.md     # 提示词源文件
└── README.md
```

## 免责声明

本项目仅供安全研究、模型鲁棒性评估与 CTF 竞赛使用。使用者需自行承担风险。
