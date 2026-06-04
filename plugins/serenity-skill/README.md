<div align="center">

# Serenity Skill

### 美股 & A 股产业链瓶颈猎人——让 AI 用 Serenity 式投研方法筛出上涨逻辑更清楚的标的

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Markets: US & A-share](https://img.shields.io/badge/Markets-US%20%7C%20A--share-red)]()

</div>

结合 Serenity ([@aleabitoreddit](https://x.com/aleabitoreddit)) 的产业链瓶颈分析方法（从 5,609 条公开推文提炼）与一套可复现的 9 步深度研究流程，专注于**美股和 A 股**的供应链卡点研究。

> 研究辅助工具。负责排序和推理；买卖决策由你自己决定。

## 能做什么

| 场景 | Prompt |
|---|---|
| 热点主题扫描 | `用 serenity-skill 深度调研 A 股 AI 半导体产业链` |
| 美股深度扫描 | `Use serenity-skill to research US-listed CPO/photonics companies` |
| 单公司挑战 | `用 serenity-skill 挑战 [公司]，它在产业链哪个位置？证据够不够？` |
| 持仓对照 | `Use serenity-skill to review my watchlist against Serenity's theses` |
| Serenity 视角评估 | `Use serenity-skill to evaluate LITE through Serenity's lens` |
| 研究伙伴对话 | `用 serenity-skill 陪我讨论机器人产业链` |

更多模板见 `skills/serenity-skill/assets/research-prompt-pack.md`。

## 安装

### Codex plugin（推荐）

本仓库已经包含 Codex 官方插件清单：

```text
.codex-plugin/plugin.json
```

将整个 `serenity-skill/` 目录作为本地 Codex plugin 导入或放入你的 Codex 插件目录。插件清单会加载 `skills/` 下的 `serenity-skill` 技能。

### Claude Code（兼容）

1. 下载本仓库 zip 并解压
2. Claude Code → 插件 → 导入本地插件 → 选择解压后的文件夹

或命令行：
```bash
cp -r skills/serenity-skill ~/.claude/skills/serenity-skill
```

### 其他 Agent Skills 兼容客户端

将 `skills/serenity-skill/` 目录放入对应客户端的 skills 路径。

## 结构

```
serenity-skill/
├── .codex-plugin/
│   └── plugin.json             # Codex 官方插件清单
├── .claude-plugin/
│   ├── plugin.json              # Claude 兼容插件清单
│   └── marketplace.json         # Claude 兼容市场列表
├── skills/serenity-skill/
│   ├── SKILL.md                 # 技能入口
│   ├── agents/
│   │   └── openai.yaml          # Codex 技能 UI 元数据
│   ├── references/              # 引用文件
│   │   ├── deep-research-workflow.md
│   │   ├── evidence-ladder.md
│   │   ├── graph-schema.md
│   │   ├── catalyst-watch.md
│   │   ├── market-source-playbook.md
│   │   ├── methodology-lens.md       # 14 条原则 + 15 点清单
│   │   ├── ticker-theses.md          # ~50 只美股覆盖
│   │   ├── articles.md               # X Article 摘要
│   │   ├── track-record.md           # 历史调用 + 校准
│   │   ├── serenity-dialogue-protocol.md
│   │   ├── output-style-and-language.md
│   │   ├── public-profile.md
│   │   └── risk-and-compliance.md
│   ├── assets/                  # 提示包、模板、头像
│   ├── scripts/                 # 评分脚本 + 校验器
│   └── examples/                # 完整示例
├── CLAUDE.md
├── README.md
└── LICENSE
```

## 边界

- 研究排序、证据链、风险核验、下一步检查
- 不执行交易、不承诺收益、不传谣、不造数据
- Serenity 的回报数据为自行报告，未经独立验证；公开调用校准约 61% 方向正确率
- 这是一个分析透镜，不是交易信号

## License

MIT

---

## English

Supply-chain bottleneck hunter for US and A-share stocks. Merges a 9-step research workflow with Serenity's 14-principle analytical lens.

### Install

**Codex plugin:** Import this folder as a local Codex plugin. The manifest is `.codex-plugin/plugin.json` and loads `./skills/`.

**Claude Code (zip import):** Download → Claude Code → Plugins → Import Local Plugin → select folder.

**Manual:** `cp -r skills/serenity-skill ~/.claude/skills/serenity-skill`

### Quick Start

```text
Use serenity-skill to research US-listed [theme]. Map the value chain,
check SEC filings, find scarce layers, rank top 5-7 priorities.
```

```text
用 serenity-skill 深度调研 A 股 [主题]。先排产业链层级，
再找最值得优先研究的标的。
```

### Disclaimer

Research support only. Serenity's returns are self-reported/unverified. Public-call calibration ~61% directional. This is a lens, not a signal feed.
