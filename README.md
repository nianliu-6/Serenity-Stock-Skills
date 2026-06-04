<div align="center">

# Serenity Skill

### 美股 & A 股产业链瓶颈猎人——让 AI 用 Serenity 式投研方法筛出上涨逻辑更清楚的标的

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Markets: US & A-share](https://img.shields.io/badge/Markets-US%20%7C%20A--share-red)]()

</div>

结合 Serenity ([@aleabitoreddit](https://x.com/aleabitoreddit)) 的产业链瓶颈分析方法（从 5,609 条公开推文提炼）与一套可复现的 9 步深度研究流程，专注于**美股和 A 股**的供应链卡点研究。

> 研究辅助工具。负责排序和推理；买卖决策由你自己决定。

## 项目定位

Serenity Stock Skills 是一个 Codex marketplace-ready 项目，同时支持三种入口：

- **仓库根 marketplace**：` .agents/plugins/marketplace.json ` → `plugins/serenity-skill/`
- **直接导入 plugin**：`.codex-plugin/plugin.json` → `skills/serenity-skill/`
- **本地 marketplace 备份入口**：`codex-marketplace/.agents/plugins/marketplace.json`

核心技能不是“荐股机器人”，而是把投资问题改写成可验证的供应链约束问题：先找真实卡点，再找证据，再排研究优先级。

## 能做什么

| 场景 | Prompt |
|---|---|
| 热点主题扫描 | `用 serenity-skill 深度调研 A 股 AI 半导体产业链` |
| 美股深度扫描 | `Use serenity-skill to research US-listed CPO/photonics companies` |
| 单公司挑战 | `用 serenity-skill 挑战 [公司]，它在产业链哪个位置？证据够不够？` |
| 持仓对照 | `Use serenity-skill to review my watchlist against Serenity's theses` |
| Serenity 视角评估 | `Use serenity-skill to evaluate LITE through Serenity's lens` |
| 研究伙伴对话 | `用 serenity-skill 陪我讨论机器人产业链` |
| 图谱输出 | `Use serenity-skill to draw a graph of this AI power supply chain` |
| 催化剂跟踪 | `Use serenity-skill to build a catalyst watch for CPO suppliers` |

更多模板见 `skills/serenity-skill/assets/research-prompt-pack.md`。

## 方法论亮点

- **Layer before ticker**：先排产业链层级，再排公司。
- **Evidence-labeled output**：把关键判断标成 `Confirmed`、`Inferred`、`Weak`、`Needs verification`。
- **L1/L2/L3 输出层级**：方向判断、候选名单、单公司 underwrite sheet 分开。
- **Graph / catalyst ready**：支持关系图谱、催化剂 watch、后续验证清单。
- **Current-data discipline**：涉及价格、公告、财报、融资、订单、监管等当前事实时必须刷新来源。

## 安装

### Codex plugin（推荐）

本仓库已经包含 Codex 官方插件清单：

```text
.codex-plugin/plugin.json
```

将整个 `serenity-skill/` 目录作为本地 Codex plugin 导入或放入你的 Codex 插件目录。插件清单会加载 `skills/` 下的 `serenity-skill` 技能。

如果使用 Codex marketplace 添加，可以直接把仓库根目录作为 marketplace root。仓库根目录包含：

```text
.agents/plugins/marketplace.json
marketplace.json
plugins/serenity-skill/
```

也保留了一个等价的子目录入口：

```text
codex-marketplace/
```

不要把普通 plugin 根目录直接传给 `codex plugin marketplace add`，否则会出现 `marketplace root does not contain a supported manifest`。

安装后可用：

```text
Use $serenity-skill to map the value chain, find scarce layers, rank research priorities, and state what would prove the thesis wrong.
```

### 校验

本项目用 Codex plugin/skill 校验器验证过。维护时建议运行：

```powershell
py C:\Users\Young\.codex\skills\.system\plugin-creator\scripts\validate_plugin.py .
py C:\Users\Young\.codex\skills\.system\plugin-creator\scripts\validate_plugin.py .\plugins\serenity-skill
$env:PYTHONUTF8='1'; py C:\Users\Young\.codex\skills\.system\skill-creator\scripts\quick_validate.py .\skills\serenity-skill
```

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
├── codex-marketplace/
│   ├── .agents/plugins/marketplace.json
│   └── plugins/serenity-skill/  # Codex marketplace 安装入口
├── .agents/plugins/marketplace.json # 仓库根 marketplace 清单
├── marketplace.json             # 根级兼容 marketplace 清单
├── plugins/serenity-skill/      # 仓库根 marketplace 安装入口
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

## 参考过的结构

完善时参考了 Codex plugin/marketplace 常见形态：

- marketplace root 使用 `.agents/plugins/marketplace.json`
- marketplace entry 使用 `source.path: "./plugins/<plugin-name>"`
- plugin root 使用 `.codex-plugin/plugin.json`
- skill root 使用 `SKILL.md`，并用 `agents/openai.yaml` 提供 UI 元数据

项目内的 `codex-marketplace/` 保留为可单独添加的 marketplace root；仓库根目录则是推荐入口。

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

**Codex marketplace:** Use the repository root as the marketplace root. It contains `.agents/plugins/marketplace.json` and points to `plugins/serenity-skill`. A root `marketplace.json` compatibility copy and the `codex-marketplace/` subdirectory are also kept.

**Validation:**

```powershell
py C:\Users\Young\.codex\skills\.system\plugin-creator\scripts\validate_plugin.py .
py C:\Users\Young\.codex\skills\.system\plugin-creator\scripts\validate_plugin.py .\plugins\serenity-skill
$env:PYTHONUTF8='1'; py C:\Users\Young\.codex\skills\.system\skill-creator\scripts\quick_validate.py .\skills\serenity-skill
```

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
