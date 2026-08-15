# 历史提示词版本 / Historical prompt releases

本目录保存已退出生产部署菜单、但仍用于复现实验和趋势图的数据。项目根目录只将 `v45` 暴露为唯一默认生产版；`v41`、`v41-skills` 与 `v42` 的提示词 ZIP 已归档至本目录。

This directory keeps reproducibility artifacts that are no longer selectable
from the production deployment script. The repository root exposes `v45` as
the sole default production release; the `v41`, `v41-skills`, and `v42` prompt
ZIPs are archived here.

| Release | Files retained here | Purpose |
|---|---|---|
| `v5` | Markdown + ZIP | Compact historical baseline |
| `v24` | ZIP | Intermediate iteration evidence |
| `v35` | ZIP | Previous issue-oriented release |
| `v41` | ZIP + local ignored Markdown source | Previous production release |
| `v41-skills` | ZIP + local ignored Markdown source | Historical Agent Skills companion |
| `v42` | ZIP + local ignored Markdown source | Previous production release |

Historical source evidence and evaluation outputs remain under `reports/` and
`tests/` in local research workspaces. v24/v35 plaintext sources stay in local
`reports/prompt_candidates/`; v41/v41-skills/v42 plaintext sources stay locally
in this directory and are excluded by `.gitignore`. Their public history
artifacts are ZIP-only.

The original v41 release ZIP retains SHA256
`569be9d9dd29ee7d54f7e3ec208ecf2ec3a9d97530f6b6baca187e639b98154b`.

The historical `v41-skills` companion referenced upstream material from
[yaklang/hack-skills](https://github.com/yaklang/hack-skills) (MIT) and
[trailofbits/skills](https://github.com/trailofbits/skills) (CC-BY-SA-4.0).
Local `skill-examples/` copies are excluded from the current repository.
