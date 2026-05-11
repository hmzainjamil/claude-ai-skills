# claude-ai-skills
200+ skills, zero loaded by default — maximum context efficiency

![Skills](https://img.shields.io/badge/Claude_Code-Production_Skills-9B59B6?style=flat&labelColor=000) ![Total](https://img.shields.io/badge/total-9%2C565_in_archive-blue?style=flat&labelColor=555) ![Active](https://img.shields.io/badge/active_default-13_core-green?style=flat&labelColor=555) ![Gating](https://img.shields.io/badge/gating-blockchain_manifest-orange?style=flat&labelColor=555)

Production Claude skill library — 9,565 skills in archive, 13 active by default, the rest dormant until a keyword fires. The blockchain manifest system ensures only relevant skills consume context tokens. Every skill has a trigger description, output contract, model preference, and version hash.

[Gating System](#gating) · [Active Skills](#active) · [Activation Map](#map) · [Skill Format](#format) · [CLI](#cli) · [Tips](#tips) · [Gotchas](#gotchas)

## 🧠 CONCEPTS

| Concept | Location | Description |
|---|---|---|
| **Blockchain Manifest** | `~/.claude/SKILL_REGISTRY_INDEX.json` | Hash + trigger + status for every skill — read in ~50ms by hook |
| **Active Skills** | `~/.claude/skills/` | Skills loaded into context — consume tokens |
| **Archive** | `~/.claude/skills-archive/` | 9,565 dormant skills — zero token cost until activated |
| **Auto-Activation** | `~/.claude/bin/skill-auto-activate` | UserPromptSubmit hook — keyword match → activation in <100ms |
| **Skill File** | `SKILL.md` | Primary skill content — injected into context on activation |
| **Manifest Entry** | `.skill.json` | Machine-readable metadata — trigger, version, model, conflicts |
| **Metrics Log** | `~/.claude/metrics.log` | Per-prompt activation log — track what fires, what's unused |

<a id="gating"></a>
## ⚙️ GATING SYSTEM

```
UserPromptSubmit fires → skill-auto-activate runs (50ms)
  ↓
1. skill-reset: deactivate all non-core skills
2. Load SKILL_REGISTRY_INDEX.json
3. Keyword match prompt against trigger descriptions
4. Activate only matched skills (cp from archive → skills/)
5. Log activation to metrics.log
6. Claude sees prompt with new skills in context

Stop hook fires → skill-reset
  ↓
All non-core skills deactivated (rm from skills/)
Context returns to baseline 13-skill state
```

**Context budget impact:**
| State | Skills Active | Token Cost |
|---|---|---|
| Default | 13 core | ~10K tokens |
| Ads task | 13 + 4 ads | ~18K tokens |
| Full agency | 13 + 12 various | ~35K tokens |
| Everything loaded | 9,565 | ~19M tokens (impossible) |

<a id="active"></a>
## 💡 ALWAYS-ACTIVE CORE SKILLS (13)

| Skill | Token Cost | Purpose |
|---|---|---|
| `caveman` | ~500 | Compressed output — removes filler words, forces density |
| `launch-optimized` | ~800 | Fast session startup — preloads common patterns |
| `optimize-commands` | ~600 | Prefer native tools (Read/Write/Grep) over Bash |
| `optimize-dgm-command` | ~500 | DigiMinds command optimization |
| `compress` | ~400 | Output compression mandate |
| `context-compression` | ~600 | Context window management |
| `context-window-management` | ~500 | Overflow prevention, compact triggers |
| `find-skills` | ~400 | Skill discovery tool — `skill-search <keyword>` |
| `skill-router` | ~700 | Keyword → skill mapping logic |
| `compact-guard` | ~400 | Compaction warning threshold |
| `summarize` | ~500 | Smart summarization patterns |
| `token-turbo` | ~400 | Token efficiency enforcement |
| `auto-learn` | ~600 | Session learning → memory queue |

<a id="map"></a>
## 🔧 ACTIVATION MAP

| Prompt Keywords | Skills Activated | Token Addition |
|---|---|---|
| `ads, ppc, meta, google, campaign, roas, cpa, ctr` | `ads-strategy, ads-copy, ads-creative, ads-keywords, ads-competitors, ads-audience, ads-funnel` | +12K |
| `seo, geo, ranking, schema, crawl, backlink, organic` | `geo, geo-technical, geo-content, geo-schema, geo-citability` | +10K |
| `legal, contract, nda, compliance, freelance, gdpr` | `legal, legal-review, legal-freelancer` | +8K |
| `marketing, brand, email, funnel, copy, content` | `market, market-brand, market-copy, market-emails, market-funnel` | +10K |
| `agency, client, proposal, pipeline, onboard` | `agency-digital-marketing, agency-pipeline, agency-onboard` | +8K |
| `pdf, report, audit, reportlab, generate document` | `reportlab-pdf-master, ads-report-pdf` | +6K |
| `agent, multi-agent, orchestrate, paperclip` | `all-agents` | +5K |
| `apify, scrape, extract, actor, crawl` | `apify-actor-development` (archive) | +4K |

<a id="format"></a>
## 📋 SKILL FILE FORMAT

Every skill in the archive follows this schema:

**`SKILL.md`:**
```markdown
---
name: ads-strategy
version: 2.1.0
description: >
  Activate when user asks about Google Ads, Meta Ads, PPC campaigns,
  ROAS optimization, bidding strategies, or any paid media performance.
trigger_keywords: [ads, ppc, google ads, meta ads, campaign, roas, cpa, ctr, bidding]
model_preference: groq:llama3-70b
conflicts: []
requires: []
token_estimate: 2800
---

# Ads Strategy Skill

[Expert domain content injected here — platform mechanics, bidding,
audience targeting, creative frameworks, performance benchmarks,
account structure, budget allocation, attribution models]

## Output format
For every ads task: diagnosis → data needed → action → expected outcome
Never give generic advice. Always ask for specific account data first.

## Gotchas
- Don't recommend Smart Bidding before confirming ≥30 conversions/month
- Meta ROAS benchmarks vary by industry — always ask industry first
```

**`.skill.json` (manifest entry):**
```json
{
  "name": "ads-strategy",
  "version": "2.1.0",
  "hash": "sha256:abc123...",
  "status": "archive",
  "trigger_keywords": ["ads", "ppc", "google ads"],
  "model_preference": "groq:llama3-70b",
  "conflicts": [],
  "token_estimate": 2800,
  "activation_count": 847,
  "last_activated": "2026-05-11"
}
```

<a id="cli"></a>
## 🛠 CLI REFERENCE

```bash
# Find skills by keyword
~/.claude/bin/skill-search "pdf report"
# → reportlab-pdf-master, audit-generator

# Activate a skill
~/.claude/bin/skill-on ads-strategy

# Deactivate a specific skill
~/.claude/bin/skill-off ads-strategy

# Check active skills
~/.claude/bin/skill-status

# Reset to core (Stop hook calls this automatically)
~/.claude/bin/skill-reset

# View skill metrics (what fires most)
~/.claude/bin/skill-metrics
# → ads-strategy: 847 activations | geo: 312 | reportlab-pdf-master: 203

# Scan archive (find all skills with a trigger)
~/.claude/bin/skill-scanner "code review"

# Watch for skill changes (dev mode)
~/.claude/bin/skill-watcher

# Audit skill drift (what's active but shouldn't be)
~/.claude/bin/skill-guardian
```

<a id="tips"></a>
## 💡 TIPS

■ **Skill Design (6)**

| Tip | Source |
|---|---|
| Keep skill description field focused on the trigger question ("when should I fire?") not what the skill does | From Thariq @ Anthropic |
| Add a Gotchas section to every skill — highest-signal content, where Claude most often fails in this domain | |
| Don't give Claude prescriptive step-by-step in skills — give goals + constraints, let Claude route the execution | |
| Skills are folders, not files — use `references/`, `examples/`, `scripts/` subdirs for progressive disclosure | |
| Include dynamic shell injection: `` !`date +%Y-%m-%d` `` in SKILL.md — Claude sees the result at activation time | |
| Test skills by checking `metrics.log` — if a skill never activates in 100 prompts, its trigger description is wrong | |

■ **Context Management (4)**

| Tip | Note |
|---|---|
| Never activate more than 5 non-core skills simultaneously — each adds 2-4K tokens, 5+ starts crowding CLAUDE.md | |
| Skills with `requires: [other-skill]` should be loaded in dependency order — skill-on handles this | |
| Skills with `conflicts: [ads-copy]` cannot be loaded simultaneously — keyword routing checks conflicts | |
| Check context usage after activation: if > 60%, defer non-critical skills to next message | |

■ **Archive Management (4)**

| Tip | Note |
|---|---|
| Skills in `skills-archive/` are never deleted — only archived. Search before creating new | `skill-search` first |
| Version skills with semver — breaking changes increment major, improvements increment minor | `version: 2.1.0` |
| The 9,565 skills in archive came from `hmz-antigravity-awesome-skills` — the community registry | |
| `skill-guardian` should run weekly — finds orphaned skills (active but never triggered) | |

<a id="gotchas"></a>
## ☠️ GOTCHAS

| Gotcha | Fix |
|---|---|
| `skill-auto-activate` adds ~100ms per prompt — acceptable for most tasks, not for rapid-fire loops | Add `SKIP_SKILL_ACTIVATE=1` env var for loops |
| Activating a skill that's already active raises no error but causes duplicate context injection | `skill-status` first |
| Skills with large `references/` subdirectories load slowly — progressive disclosure only works if Claude loads refs on demand | Keep SKILL.md under 3K tokens, put detail in `references/` |
| `SKILL_REGISTRY_INDEX.json` grows unbounded — `skill-guardian` should prune unhashed entries monthly | |
| Old skills in archive may reference removed models — `model_preference: gpt-3.5-turbo` now routes to GPT-4o-mini | Update model fields quarterly |
