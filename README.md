# claude-ai-skills
200+ domain skills for Claude Code — blockchain-gated, auto-activated, zero idle cost.

![skills](https://img.shields.io/badge/skills-200%2B-blue?style=flat&labelColor=555)
![active](https://img.shields.io/badge/always_on-12_core-green?style=flat&labelColor=555)
![gated](https://img.shields.io/badge/activation-on_demand-orange?style=flat&labelColor=555)
![platform](https://img.shields.io/badge/platform-Claude%20Code-lightgrey?style=flat&labelColor=555)
![license](https://img.shields.io/badge/license-MIT-blue?style=flat&labelColor=555)

[Concepts](#-concepts) · [Architecture](#️-architecture) · [Tips](#-tips-and-tricks-22) · [Kills](#️-startups--businesses) · [Stars](#star-history)

## 🧠 CONCEPTS

| Feature | Location | Description |
|---------|----------|-------------|
| [**Ads Strategy**](skills-active/ads-strategy) | `skills-active/ads-strategy/SKILL.md` | Full Google/Meta campaign planning — targeting, budgets, ROAS optimization [![ppc](https://img.shields.io/badge/domain-PPC-blue?style=flat&labelColor=555)] |
| [**Caveman Compress**](skills-active/caveman) | `skills-active/caveman/SKILL.md` | 60-80% token reduction — strips filler, compresses outputs before returning |
| [**Context Compression**](skills-active/context-compression) | `skills-active/context-compression/SKILL.md` | Manages 200K context window — triggers /compact at 70% usage |
| [**Legal Review**](skills-active/legal-review) | `skills-active/legal-review/SKILL.md` | Contract analysis, NDA triage, compliance checks — UK/AU/US law |
| [**Market Emails**](skills-active/market-emails) | `skills-active/market-emails/SKILL.md` | Email sequences, cold outreach, follow-up chains — B2B focused |
| [**Ads Creative**](skills-active/ads-creative) | `skills-active/ads-creative/SKILL.md` | Ad copy, hooks, headlines, creative briefs for Meta + Google |
| [**Ads Report PDF**](skills-active/ads-report-pdf) | `skills-active/ads-report-pdf/SKILL.md` | ReportLab 11-page 360° audit PDFs with client brand palette |
| [**Compact Guard**](skills-active/compact-guard) | `skills-active/compact-guard/SKILL.md` | Auto-fires /compact before context overflow — always-on |
| [**Skill Router**](skills-active/skill-router) | `skills-active/skill-router/SKILL.md` | Keyword→skill map — auto-activates correct skills from archive |
| [**ReportLab PDF Master**](skills-active/reportlab-pdf-master) | `skills-active/reportlab-pdf-master/SKILL.md` | 12 hard laws for ReportLab PDFs — prevents recurring layout errors |
| [**Agency Pipeline**](skills-active/agency-pipeline) | `skills-active/agency-pipeline/SKILL.md` | Client acquisition, proposal writing, pipeline management |
| [**Token Turbo**](skills-active/token-turbo) | `skills-active/token-turbo/SKILL.md` | Aggressive token savings — batching, caching, Tier 0 routing |

### 🔥 Hot

| Feature | Location | Description |
|---------|----------|-------------|
| [**All Agents**](skills-active/all-agents) | `skills-active/all-agents/SKILL.md` | Spawns all domain agents in parallel — comprehensive/360 analysis mode |
| [**Auto Learn**](skills-active/auto-learn) | `skills-active/auto-learn/SKILL.md` | Stop hook: session-queue.jsonl → persistent memory files automatically |
| [**Ads Audit**](skills-active/ads-audit) | `skills-active/ads-audit/SKILL.md` | 200+ checkpoint Google/Meta audit — structure, tracking, creative, bidding |

## ⚙️ ARCHITECTURE

```
Skill Lifecycle:
  Archive (dormant)
      │
      ▼ skill-on <name>
  Active (loaded into context)
      │
      ▼ Used in task
  Deactivated
      │
      ▼ skill-off <name>
  Archive (dormant)
```

| Category | Skills | Always On |
|----------|--------|-----------|
| Core | caveman, compact-guard, summarize, context-compression, skill-router | ✓ All 5 |
| Ads | ads-strategy, ads-creative, ads-copy, ads-report-pdf, ads-audit, ads-keywords | On-demand |
| SEO | geo, geo-technical, geo-content, geo-schema | On-demand |
| Legal | legal, legal-review, legal-freelancer, legal-report-pdf | On-demand |
| Marketing | market, market-emails, market-copy, market-brand | On-demand |
| Agency | agency-pipeline, agency-digital-marketing, agency-status | On-demand |

## 💡 TIPS AND TRICKS (22)

[activation](#tips-activation) · [writing](#tips-writing) · [core](#tips-core) · [pdf](#tips-pdf)

<a id="tips-activation"></a>■ **Skill Activation (6)**

| Tip | Source |
|-----|--------|
| `skill-on <name>` activates from archive — copies SKILL.md to skills/ and loads | [HMZ](https://github.com/hmzainjamil) |
| `skill-search <keyword>` fuzzy-searches all 200+ archive entries via fzf | [HMZ](https://github.com/hmzainjamil) |
| Auto-activation via `skill-auto-activate` fires on every prompt — keyword-matched | [HMZ](https://github.com/hmzainjamil) |
| Never load more than 5 skills simultaneously — each adds ~2K tokens to context | [HMZ](https://github.com/hmzainjamil) |
| `skill-off --all` collapses everything back to 12 core skills | [HMZ](https://github.com/hmzainjamil) |
| SKILL.md files auto-push to `claude-ai-skills` via PostToolUse hook on every Write | [HMZ](https://github.com/hmzainjamil) |

<a id="tips-writing"></a>■ **Skill Writing (5)**

| Tip | Source |
|-----|--------|
| Every SKILL.md needs: trigger keywords, model routing, output format, examples | [HMZ](https://github.com/hmzainjamil) |
| Always specify Tier 0 model in skill — never default to Claude for sub-tasks | [HMZ](https://github.com/hmzainjamil) |
| Skill description must be ≤80 chars — shown in skill-search results | [HMZ](https://github.com/hmzainjamil) |
| Include `## DEACTIVATE` section — cleanup steps after skill task completes | [HMZ](https://github.com/hmzainjamil) |
| Test skill with `skill-on <name> && claude 'trigger phrase'` before archiving | [HMZ](https://github.com/hmzainjamil) |

<a id="tips-core"></a>■ **Core Skill Usage (6)**

| Tip | Source |
|-----|--------|
| Caveman: apply to ALL sub-agent outputs — 60-80% fewer tokens returned | [HMZ](https://github.com/hmzainjamil) |
| Compact-guard: fires at 70% usage — never let context overflow silently | [HMZ](https://github.com/hmzainjamil) |
| Context-compression: `summarize` skill for mid-session compression without losing state | [HMZ](https://github.com/hmzainjamil) |
| Skill-router: keyword map lives in `automations/bin/skill-router` — edit to add triggers | [HMZ](https://github.com/hmzainjamil) |
| Token-turbo: activates when prompt includes "fast", "quick", "cheap", "save tokens" | [HMZ](https://github.com/hmzainjamil) |
| Find-skills: semantic search across skill descriptions — better than keyword search | [HMZ](https://github.com/hmzainjamil) |

<a id="tips-pdf"></a>■ **PDF / ReportLab (5)**

| Tip | Source |
|-----|--------|
| Always import: `from reportlab.lib.pagesizes import A4` — never hardcode dimensions | [HMZ](https://github.com/hmzainjamil) |
| Never use `canvas.drawString` for body text — always `platypus.Paragraph` with styles | [HMZ](https://github.com/hmzainjamil) |
| Brand palette from client URL — use Playwright screenshot + color extraction | [HMZ](https://github.com/hmzainjamil) |
| Each report page = separate Platypus flowable — never single monolithic canvas | [HMZ](https://github.com/hmzainjamil) |
| Save all PDFs to ~/Downloads — never Desktop (user preference) | [HMZ](https://github.com/hmzainjamil) |

## ☠️ STARTUPS / BUSINESSES

| Feature | Replaced |
|-|-|
| **Skill Router + Auto-Activation** | [Zapier](https://zapier.com), [Make.com](https://make.com) — no external automation needed |
| **200+ Domain Skills** | [Character.ai](https://character.ai), [Poe](https://poe.com), [OpenAI GPTs](https://openai.com/gpts) |
| **Ads Skills Stack** | [Madgicx](https://madgicx.com), [Revealbot](https://revealbot.com), [Optmyzr](https://optmyzr.com) |
| **Legal Skills** | [Harvey AI](https://harvey.ai), [Robin AI](https://robinai.com), [Spellbook](https://spellbook.legal) |
| **PDF Report Skills** | [Databox](https://databox.com), [AgencyAnalytics](https://agencyanalytics.com), [DashThis](https://dashthis.com) |

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/claude-ai-skills&type=Date)](https://star-history.com/#hmzainjamil/claude-ai-skills&Date)
