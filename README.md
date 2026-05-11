# claude-ai-skills

![Skills](https://img.shields.io/badge/Claude_Code-Production_Skills-9B59B6?style=flat&labelColor=000) ![Count](https://img.shields.io/badge/skills-200%2B_available-blue?style=flat&labelColor=555) ![Gating](https://img.shields.io/badge/gating-blockchain_manifest-orange?style=flat&labelColor=555) ![Active](https://img.shields.io/badge/default_active-12_core_skills-green?style=flat&labelColor=555)

Production Claude skill library — activatable, gated, and auto-routed via a blockchain-style manifest system. 200+ specialized skills across ads, SEO, agency ops, coding, research, and more. Default state: 12 core skills only. Everything else dormant until needed.

## 🧠 SKILL GATING SYSTEM

Skills are not prompts. They're structured capability files that inject domain expertise into Claude's context window on-demand. Loading all 200+ at once would consume ~80% of every session's context budget before the user even types.

The blockchain manifest solves this: every skill has a hash, a keyword trigger set, and an activation status. The `UserPromptSubmit` hook scans the manifest on every prompt in ~50ms.

**Default active (always loaded):**
```
caveman              → compressed output style
launch-optimized     → fast session startup
optimize-commands    → prefer native tools over Bash
compress             → output compression
context-compression  → context window management
context-window-management → overflow prevention
summarize            → smart summarization
find-skills          → skill discovery tool
skill-router         → keyword → skill mapping
compact-guard        → compaction warnings
optimize-dgm-command → DigiMinds command optimization
```

**Everything else:** dormant in `~/.claude/skills-archive/` until a keyword fires.

## ⚙️ ACTIVATION MAP

| Prompt Keywords | Skills Auto-Activated |
|---|---|
| `ads, ppc, meta, google ads, campaign` | `ads-strategy, ads-copy, ads-creative, ads-keywords, ads-competitors` |
| `seo, geo, ranking, schema, crawl` | `geo, geo-technical, geo-content, geo-schema, geo-citability` |
| `legal, contract, nda, compliance` | `legal, legal-review` |
| `marketing, brand, email, funnel` | `market, market-brand, market-copy, market-emails` |
| `agency, client, proposal, pipeline` | `agency, agency-client, agency-pipeline` |
| `apify, scrape, extract, actor` | `apify-actor-development, apify-ultimate-scraper` |
| `agent, multi-agent, orchestrate` | `all-agents` |
| `pdf, report, audit, reportlab` | `reportlab-pdf-master` |

## 💡 SKILL FILE FORMAT

```markdown
---
name: ads-strategy
version: 1.4.0
trigger_keywords: [ads, ppc, google ads, meta ads, campaign, roas, cpa]
model_preference: groq:llama3-70b  # Tier 0 first
requires: []
---

# Ads Strategy Skill

[Domain expertise injected here — platform mechanics, bidding strategies,
audience targeting, creative frameworks, performance benchmarks]

## Output format
Always return: hypothesis → data needed → recommended action → expected outcome
```

## 🔧 SKILL LIFECYCLE COMMANDS

```bash
# Find skills by keyword
~/.claude/bin/skill-search "pdf report"
# → reportlab-pdf-master, audit-generator, document-generator

# Activate a skill
~/.claude/bin/skill-on reportlab-pdf-master

# Check what's currently active
~/.claude/bin/skill-status

# Deactivate after task
~/.claude/bin/skill-off reportlab-pdf-master

# Promote skill from archive to active
~/.claude/bin/skill-promote my-new-skill

# Archive a skill (dormant, not deleted)
~/.claude/bin/skill-archive unused-skill
```

## 📊 SKILL CATEGORIES

| Category | Count | Examples |
|---|---|---|
| Paid Media | 8 | ads-strategy, ads-copy, ads-creative, ads-keywords |
| SEO / GEO | 7 | geo, geo-technical, geo-content, geo-schema, geo-ai-visibility |
| Agency Ops | 5 | agency, agency-client, agency-pipeline, agency-proposal |
| Content | 4 | market-copy, market-emails, market-brand, content-calendar |
| Technical | 6 | code-review, security-audit, api-testing, db-optimizer |
| Research | 4 | research-synthesis, competitor-intel, trend-scanner |
| Documents | 3 | reportlab-pdf-master, audit-generator, proposal-writer |
| Scientific | 6 | bio-research, stats-analysis, math-proof, physics-solver |

## ☠️ WHY NOT JUST USE THE SYSTEM PROMPT

A system prompt can hold ~100K tokens. With 200+ skills each averaging 2K tokens, loading all would consume 400K tokens — more than the context window.

The manifest + gating pattern means: at any given moment, only 5-15 skills are active, consuming 10-30K tokens total. The remaining 185+ skills exist but cost nothing until they're needed.
