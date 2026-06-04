# Changelog

## 1.0.0 (2026-05-30)

Initial release. Merged from:
- **serenity-skill** — general supply-chain bottleneck methodology, 9-step workflow, cross-market source playbook
- **serenity-aleabitoreddit** — 14-principle analytical lens, per-ticker theses (~50 US stocks), track record, article summaries, distilled from 5,609 tweets (2025-07 to 2026-05)

### Design
- Market focus: US stocks and A-shares (HK/TW/JP/KR/EU methodology-only)
- Claude Code plugin format: `.claude-plugin/plugin.json` + `skills/serenity-skill/SKILL.md`
- Two-tier depth: SKILL.md as router (~200 lines), reference files for deep content
- Lens integration: 14 principles called out at relevant workflow steps
