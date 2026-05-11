# claude-ai-skills
Production Claude skill library — activatable, gated, auto-routed via blockchain manifest

![Skills](https://img.shields.io/badge/skills-200%2B-blue?style=flat&labelColor=555) ![Claude Code](https://img.shields.io/badge/Claude_Code-compatible-orange?style=flat&labelColor=555) ![Auto-activate](https://img.shields.io/badge/auto--activate-UserPromptSubmit_hook-green?style=flat&labelColor=555)

Part of the [HMZ AI Infrastructure](https://github.com/hmzainjamil) stack.

---

## 🧠 SKILL ACTIVATION SYSTEM

| Layer | Location | Description |
|-------|----------|-------------|
| Core skills (always-on) | `~/.claude/skills/` | caveman, compress, context-compression, summarize, skill-router |
| Archive (dormant) | `~/.claude/skills-archive/` | Everything else — dormant until keyword match |
| Auto-activator | `~/.claude/bin/skill-auto-activate` | Fires on every prompt via UserPromptSubmit hook |
| Manifest | `~/.claude/skills-lock.json` | Blockchain-style dep tracking |

## ⚙️ SKILL CATEGORIES

| Category | Trigger Keywords | Skills |
|----------|-----------------|--------|
| Ads / PPC | ads, ppc, meta, google ads, campaign | ads-strategy, ads-copy, ads-creative, ads-keywords, ads-competitors |
| SEO / GEO | seo, geo, ranking, schema, crawl | geo, geo-technical, geo-content, geo-schema, geo-citability |
| Legal | legal, contract, nda, compliance | legal, legal-review, legal-freelancer, legal-agreement |
| Marketing | marketing, brand, email, funnel | market, market-brand, market-copy, market-emails |
| Agency | agency, client, proposal, pipeline | agency, agency-client, agency-pipeline |
| Apify | apify, scrape, extract, actor | apify-actor-development, apify-ultimate-scraper |
| Agents | agent, multi-agent, orchestrate | all-agents |

## 💡 SKILL COMMANDS

```bash
~/.claude/bin/skill-search <keyword>   # find skills by keyword
~/.claude/bin/skill-on <name>          # activate single skill
~/.claude/bin/skill-off <name>         # deactivate after task
~/.claude/bin/skill-auto-activate      # manual trigger (runs automatically on every prompt)
```

■ **Skill File Format**

```
~/.claude/skills/<name>/SKILL.md
~/.claude/skills/<name>/SKILL.md — frontmatter: name, description, type, triggers
```

---
Built by [HMZ](https://github.com/hmzainjamil) · [DigiMinds](https://digiminds.org)
