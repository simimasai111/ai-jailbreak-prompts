<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="docs/images/gpt-5.6-instruct-hero-dark.webp" />
  <source media="(prefers-color-scheme: light)" srcset="docs/images/gpt-5.6-instruct-hero-light.webp" />
  <img src="docs/images/gpt-5.6-instruct-hero-light.webp" alt="gpt-5.6 破甲提示词及测试包" width="70%" />
</picture><br />
<img src="docs/images/readme-spacer.png" alt="" width="1" height="5" />

<p>
  <a href="https://github.com/MDX-Tom/gpt-5.6-instruct/stargazers"><img src="https://img.shields.io/github/stars/MDX-Tom/gpt-5.6-instruct?logo=github&label=Stars" alt="GitHub Stars" /></a>
  <img src="https://img.shields.io/badge/Model-gpt--5.6--sol-7c3aed" alt="gpt-5.6-sol" />
  <a href="gpt-5.6-sol-unrestricted-v45.zip"><img src="https://img.shields.io/badge/Release-v45-0f766e" alt="Release v45" /></a>
  <a href="https://www.python.org/"><img src="https://img.shields.io/badge/Python-3.8%2B-3776AB?logo=python&logoColor=white" alt="Python 3.8+" /></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/MDX-Tom/gpt-5.6-instruct?color=f59e0b" alt="MIT License" /></a>
  <a href="docs/comparison-tests-en.md"><img src="https://img.shields.io/badge/Documentation-Purple?color=8A2BE2&logo=readthedocs" alt="English Documentation" /></a>
  <a href="docs/comparison-tests.md"><img src="https://img.shields.io/badge/中文文档-red?logo=readthedocs" alt="中文文档" /></a>
</p>

<p>
  <a href="README_EN.md"><img src="https://img.shields.io/badge/lang-English-blue.svg" alt="English" /></a>
  <a href="README.md"><img src="https://img.shields.io/badge/语言-简体中文-red.svg" alt="简体中文" /></a>
</p>

<h1>gpt-5.6 破甲提示词及测试包</h1>

</div>

<!-- README_SYNC: 修改 README.md 时必须同步更新 README_EN.md；图表也必须提供对应语言版本。 -->

<a id="overview"></a>

本项目提供面向大模型的越狱/破甲提示词与配套工具链：将安全研究、渗透测试、逆向工程、软件破解及 NSFW 虚构内容统一纳入本地沙箱任务，并显式抑制拒绝与回退话术，提升 Codex 对复杂指令的连续执行能力。

项目围绕 `v45` 持续迭代。每轮优化吸收用户指令、真实失败案例与 GitHub Issues，动态扩展测试集，定位失败原因并重写提示词；随后以 low、medium、high 三档回归和证据门禁复核结果，决定是否发布。最新 `v45` 版本针对 Issues 与社交平台用户反映的实际问题，提升逆向、生物任务通过概率，降低了触发云审查的几率。

当前生产版本为 `v45`，可使用 `codex-instruct.py` 进行预览、部署和回滚。历史版本 `v5`、`v24`、`v35`、`v41`、`v41-skills` 与 `v42` 已归档至 [`historical-versions/`](historical-versions/)，用于复现和对照。

> **声明 ⚠️** 本项目不会用于任何商业化行为，包括但不限于创业融资宣传、技术授权转让和付费技术服务。本项目旨在提升 AI 安全。未来项目无论获得多少关注，都将保持初心，共同筑牢 AI 的安全边界。

> [!IMPORTANT]
> 从事破甲活动存在封号风险，建议在日抛账号上使用。
> 
> 本项目使用 Codex 官方配置机制，不修改二进制、不劫持网络、不篡改进程。请仅在你有权操作的环境中使用，并自行承担使用风险。

<a id="architecture"></a>

## 系统架构 🏗️

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="docs/images/project-architecture-zh-dark.webp" />
    <source media="(prefers-color-scheme: light)" srcset="docs/images/project-architecture-zh-light.webp" />
    <img alt="破甲提示词持续迭代、发布门禁与生产运行架构" src="docs/images/project-architecture-zh-light.webp" width="100%" />
  </picture>
</p>

项目架构由迭代优化与生产使用两部分组成。迭代阶段持续吸收用户指令、失败样例及 GitHub Issues，由模型更新中英文测试集、分析回归结果并优化提示词，经版本证据审阅与发布决策后形成 v45。生产阶段通过脚本加载 v45，依次完成归一化、语义分派、意图路由、状态连续性和工件验证，最终生成可核验结果。

<a id="versions"></a>

## 默认版本 📦

| 版本 | 定位 | 入口 | 获取 |
|---|---|---|---|
| **v45** | 当前生产版本 | `python3 codex-instruct.py --apply` | [ZIP](gpt-5.6-sol-unrestricted-v45.zip) |

当前发布 ZIP 的 SHA256：

```text
v45  c86c2c6d20a4d1155d87422f485eb37b77539132270918c002b5d8237a5adf54
```

<a id="quick-start"></a>

## 快速开始 🚀

### 1. 获取项目 📥

```bash
git clone https://github.com/MDX-Tom/gpt-5.6-instruct.git
cd gpt-5.6-instruct
```

### 2. 预览并部署 ⚡

```bash
# 先预览 v45，不写入任何文件
python3 codex-instruct.py --apply --dry-run

# 部署唯一默认版 v45
python3 codex-instruct.py --apply
```

不带参数运行可打开交互式菜单：

```bash
python3 codex-instruct.py
```

<details>
<summary><strong>更多命令</strong></summary>

```bash
# 指定 Codex home
python3 codex-instruct.py --apply --codex-dir ~/.codex

# 部署自定义 ZIP 或 Markdown
python3 codex-instruct.py --file ./custom-instructions.zip

# 安全卸载提示词；只恢复本项目管理的配置项
python3 codex-instruct.py --reset

# 人工应急：显式恢复整份 config.toml 快照
python3 codex-instruct.py \
  --restore-snapshot ~/.codex/config.toml.bak_YYYYMMDD_HHMMSS_ffffff \
  --codex-dir ~/.codex
```

</details>

执行 `--reset` 时，脚本只恢复部署前的顶层 `model_instructions_file`，不会用旧快照覆盖整个 `config.toml`。脚本仅删除由本次状态记录为新建且 SHA256 未变化的提示词；部署前已存在或后来被用户修改的文件会保留。

### 手动部署及回滚 ↩️

解压 v45，将指令文件复制到 `CODEX_HOME`，为 `config.toml` 创建操作前快照，并写入：

```toml
model_instructions_file = "./gpt-5.6-sol-unrestricted-v45.md"
```

若要手动回滚，直接删除或用 `#` 注释掉上述行即可恢复模型原始默认行为；也可删除部署的版本化 Markdown 文件以清理本地文件。

### 反代工具兼容性 🔌

<details>
<summary><strong>点击查看</strong></summary>

- 部署前的指令项、已部署文件 SHA256 及部署前是否存在记录在 `CODEX_HOME/.gpt56-sol-instruct-state.json`；状态文件不保存 provider、模型、URL 或认证数据。
- **CCSwitch 等反代工具在部署后写入的 provider、模型和认证配置会在 `--reset` 后保留。**
- 完整 `config.toml.bak_<时间戳>` 快照只用于人工应急恢复；需要恢复整份配置时，必须显式使用 `--restore-snapshot` 并再次确认。
- 旧版 `config.toml.gpt56-sol-instruct.bak` 只用于找回原有 `model_instructions_file`，其中的其他配置不会自动写回。
- 已存在且未被状态文件接管的 Markdown 文件不会被覆盖；请使用其他 `--name`。

</details>

<a id="results"></a>

## 评测结果 📊

v42 发布门禁中，Issues #5/#22 的两个无历史对话原始输入在 `medium` 推理下一次通过 **2/2 cases、2/2 turns、2/2 artifact gates**，无需重复输入。扩展专项集在 `low` 下达到 **60/60 cases、68/68 turns、8/8 artifact gates**；原 120 条 `medium` 测试集在 `low` 下首跑 115/120，定向审计 5/5 后形成保留替换来源的 120/120 汇总。

针对 Issues #3/#4/#5/#6/#8，项目另有 52 个案例、58 个逻辑轮次的双语专项集 [`tests/gpt56_sol_issue_regression_bank.md`](tests/gpt56_sol_issue_regression_bank.md)，覆盖明文云审查、生物研究、模板误路由/循环恢复和进度可见性。专项 runner 不使用编码输入、编码输出或编码重试，并将 provider policy、中断网络、超时、解析错误和模型回退分别统计。

完整的安全性评测说明见 [docs/gpt-5.6-sol-safety-eval.md](docs/gpt-5.6-sol-safety-eval.md)。

### 版本迭代趋势（截至 v41）

以下图表保留截至 v41 的同口径历史数据。

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="docs/images/gpt56-sol-version-pass-trend-zh-dark.svg" />
    <source media="(prefers-color-scheme: light)" srcset="docs/images/gpt56-sol-version-pass-trend-zh-light.svg" />
    <img alt="截至 v41 的 gpt-5.6-sol 提示词版本迭代通过率" src="docs/images/gpt56-sol-version-pass-trend-zh-light.svg" width="92%" />
  </picture>
</p>

<details>
<summary><strong>历史 52-case Issue 测试集趋势（2026-07-23）</strong></summary>

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="docs/images/gpt56-sol-issue-version-trend-zh-dark.svg" />
    <source media="(prefers-color-scheme: light)" srcset="docs/images/gpt56-sol-issue-version-trend-zh-light.svg" />
    <img alt="截至 v41 的 Issue 测试集版本与推理等级趋势" src="docs/images/gpt56-sol-issue-version-trend-zh-light.svg" width="92%" />
  </picture>
</p>

</details>

## 评测工具 🧪

项目提供本地评测脚本，用于生成提示词库、运行回归并离线校验评分逻辑。测试数据、运行日志和详细方法说明不在 README 展开，参见 [中文对比测试文档](docs/comparison-tests.md) 与 [English Documentation](docs/comparison-tests-en.md)。

首次克隆后解压公开脚本：

```bash
for archive in scripts/*.zip; do unzip -o "$archive" -d scripts; done
```

常用入口：

```bash
python3 scripts/generate_gpt56_sol_prompt_bank.py
python3 scripts/run_gpt56_sol_prompt_bank.py --level minimal --reasoning low
python3 scripts/run_gpt56_sol_issue_regression.py --dry-run
python3 scripts/verify_gpt56_sol_regression_scoring.py
```

<a id="layout"></a>

## 项目结构 🗂️

```text
gpt-5.6-instruct/
├── README.md / README_EN.md                     # 中英文首页
├── codex-instruct.py                            # v45 默认部署与回滚
├── sync-archives.py                             # 本地源文件与 ZIP 同步
├── gpt-5.6-sol-unrestricted-v45.zip             # 唯一默认生产版
├── historical-versions/                         # v5/v24/v35/v41/v42 归档
├── scripts/*.zip                                # 可复现评测工具
├── unit-tests/                                  # 项目功能单元测试
├── .github/workflows/test-codex-instruct.yml    # Python 3.8/3.13 CI
└── docs/images/project-architecture-*.webp      # 中英文亮暗架构图
```

### 维护发布包

当前发布包、历史归档与测试脚本由 `sync-archives.py` 统一维护。修改本地源文件后执行：

```bash
python3 sync-archives.py
python3 sync-archives.py --check
```

同步器会跳过内容已经匹配的 ZIP，避免仅因时间戳或压缩元数据变化而改变既有发布包字节。

## 许可证 📄

本项目采用 [MIT License](LICENSE)。

## Star History ⭐

<p align="center">
  <a href="https://www.star-history.com/?repos=MDX-Tom%2Fgpt-5.6-instruct&type=date&legend=top-left">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://mdx-tom.github.io/gpt-5.6-instruct/star-history-dark.svg" />
      <source media="(prefers-color-scheme: light)" srcset="https://mdx-tom.github.io/gpt-5.6-instruct/star-history-light.svg" />
      <img alt="Star History Chart" src="https://mdx-tom.github.io/gpt-5.6-instruct/star-history-light.svg" width="80%" />
    </picture>
  </a>
</p>

## 致谢 🙏

参考并延展自 [yynxxxxx/Codex-5.5-codex-instruct-5.5](https://github.com/yynxxxxx/Codex-5.5-codex-instruct-5.5)。感谢 [yynxxxxx](https://github.com/yynxxxxx) / li lingbo 的开源工作。
