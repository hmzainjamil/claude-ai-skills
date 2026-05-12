# claude-ai-skills

![Version](https://img.shields.io/badge/version-3.0-blue?style=flat&labelColor=555)
![Skills](https://img.shields.io/badge/skills-200%2B-purple?style=flat&labelColor=555)
![Status](https://img.shields.io/badge/status-active-brightgreen?style=flat&labelColor=555)
![License](https://img.shields.io/badge/license-MIT-orange?style=flat&labelColor=555)

> **200+ Claude Code skills** — blockchain-gated activation, auto-routing by keyword, Tier 0 model routing. Skills fire only when needed, auto-deactivate after task. Zero token waste.

---

## 🧠 CONCEPTS

| Feature | Location | Description |
|---|---|---|
| [Skill Manifest](skills-lock.json) | `skills-lock.json` | Blockchain-style manifest tracking all skill deps, versions, hashes |
| [Core Skills](skills/core/) | `skills/core/` | Always-on: caveman, compress, compact-guard, context-window-management |
| [Ads Skills](skills/ads/) | `skills/ads/` | ads-strategy, ads-copy, ads-creative, ads-keywords, ads-competitors |
| [SEO Skills](skills/seo/) | `skills/seo/` | geo, geo-technical, geo-content, geo-schema, geo-citability, geo-ai-visibility |
| [Legal Skills](skills/legal/) | `skills/legal/` | legal, legal-review, compliance, contract analysis |
| [Marketing Skills](skills/marketing/) | `skills/marketing/` | brand, copy, emails, funnel, market launch |
| [Agency Skills](skills/agency/) | `skills/agency/` | agency-client, agency-pipeline, proposal |
| [Startup Skills](skills/startup/) | `skills/startup/` | startup-optimized, market-launch, MVP builder |
| [Report Skills](skills/reports/) | `skills/reports/` | report-creator, PDF/DOCX/XLSX/PPTX generation, LaTeX templates |
| [Apify Skills](skills/apify/) | `skills/apify/` | apify-actor-development, ultimate-scraper, web extraction |
| [Skill Router](skills/skill-router/) | `skills/skill-router/` | Keyword → skill auto-activation on every UserPromptSubmit |
| [Skill Archive](skills-archive/) | `skills-archive/` | Dormant skills — moved out of active on session end |
| [Auto-Activate](bin/skill-auto-activate) | `bin/skill-auto-activate` | Hook script — keyword-scans every prompt → activates matching skills |
| [Skill Search](bin/skill-search) | `bin/skill-search` | Full-text search across all skill metadata and descriptions |
| [Skill On/Off](bin/skill-on) | `bin/skill-on` | Toggle individual skills — moves between active and archive |
| [Skill Creator](skills/skill-creator/) | `skills/skill-creator/` | Scaffold new skill from template — SKILL.md + metadata in 30s |
| [Context Guard](skills/compact-guard/) | `skills/compact-guard/` | Prevents context overflow on long sessions — auto-compacts |
| [Token Turbo](skills/token-turbo/) | `skills/token-turbo/` | Aggressive token reduction — caveman + compression + dedup |
| [Launch Optimized](skills/launch-optimized/) | `skills/launch-optimized/` | Full multi-LLM burst system — 15 models fire simultaneously |
| [Optimize Commands](skills/optimize-commands/) | `skills/optimize-commands/` | Always-on: code agent, report creator, agency agents, n8n router |
| [Find Skills](skills/find-skills/) | `skills/find-skills/` | Semantic skill discovery — finds best skill for any task description |
| [UGC Agency](skills/ugc-agency/) | `skills/ugc-agency/` | One prompt → 20 UGC MP4 ads via Arcads API |
| [Premium Web Design](skills/premium-web-design/) | `skills/premium-web-design/` | Stitch mockup → Nano Banana → 21st.dev → pixel-perfect site |
| [Airtable SDK](skills/airtable-sdk/) | `skills/airtable-sdk/` | Official Airtable JS SDK integration for database automation |
| [OODA Loop](skills/ooda-loop/) | `skills/ooda-loop/` | Rapid decision framework — observe, orient, decide, act on every task |

### 🔥 Hot

| Feature | Location | Description |
|---|---|---|
| [Skill Router](skills/skill-router/) | `skills/skill-router/` | Auto-activates the right skill on every prompt — zero manual triggers |
| [Launch Optimized](skills/launch-optimized/) | `skills/launch-optimized/` | 15 models fire simultaneously — G0DM0D3 races 55 models, picks winner |
| [Token Turbo](skills/token-turbo/) | `skills/token-turbo/` | 60-80% token reduction via caveman compression + aggressive dedup |
| [UGC Agency](skills/ugc-agency/) | `skills/ugc-agency/` | 20 UGC ads from 1 prompt — scripts → actors → render → MP4 |
| [Report Creator](skills/report-creator/) | `skills/report-creator/` | Institutional-grade PDF/XLSX/PPTX from any data in one command |

---

## ⚙️ ARCHITECTURE

```
┌───────────────────────────────────────────────────────────────┐
│                   CLAUDE-AI-SKILLS v3.0                       │
│                                                               │
│  Every Prompt → UserPromptSubmit hook → skill-auto-activate   │
│                         │                                     │
│              keyword scan on prompt text                      │
│                         │                                     │
│    ┌────────────────────▼────────────────────┐               │
│    │         BLOCKCHAIN SKILL GATE           │               │
│    │  Core always-on │ Domain auto-activated │               │
│    │  Archive dormant│ Released after task   │               │
│    └────────────────────────────────────────-┘               │
│                         │                                     │
│    Skills execute via Skill tool → Tier 0 model routing       │
│    Output → synthesized → user response                       │
│                         │                                     │
│    Stop hook → skill-off all non-core → back to baseline      │
└───────────────────────────────────────────────────────────────┘
```

| Layer | Technology | Purpose |
|---|---|---|
| Gate | skills-lock.json | Blockchain manifest — dep tracking, version control |
| Routing | skill-router + keyword map | Auto-activate correct skill per prompt |
| Execution | Skill tool → Tier 0 models | Zero Claude tokens for skill sub-tasks |
| Memory | ~/.claude/session-queue.jsonl | Skills write learnings for next session |
| Archive | skills-archive/ | Dormant skills — loaded only when needed |

---

## 🚀 Quick Start

```bash
# Search for a skill
~/.claude/bin/skill-search "competitor analysis"

# Activate a skill manually
~/.claude/bin/skill-on ads-strategy

# Deactivate after task
~/.claude/bin/skill-off ads-strategy

# Create a new skill from template
~/.claude/skills/skill-creator/create.sh --name "my-skill" --category ads

# Check what's currently active
~/.claude/bin/skill-search --active
```

---

## 💡 TIPS AND TRICKS (48)

<a id="tips-core"></a>
### ■ **Core Skills (6)**
| Tip | Source |
|---|---|
| Core 10 skills always active — never deactivate these even after task | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| caveman skill = 60-80% token savings on all outputs automatically | [caveman](https://github.com/hmzainjamil/claude-ai-skills) |
| compact-guard prevents context overflow on sessions > 50k tokens | [compact-guard](https://github.com/hmzainjamil/claude-ai-skills) |
| summarize skill auto-fires before context window limit hit | [summarize](https://github.com/hmzainjamil/claude-ai-skills) |
| context-window-management tracks token usage — warns at 80% capacity | [context](https://github.com/hmzainjamil/claude-ai-skills) |
| token-turbo combines caveman + compress + dedup for maximum savings | [token-turbo](https://github.com/hmzainjamil/claude-ai-skills) |

<a id="tips-activation"></a>
### ■ **Activation (6)**
| Tip | Source |
|---|---|
| skill-auto-activate runs on every prompt via UserPromptSubmit hook | [hooks](https://github.com/hmzainjamil/claude-ai-system) |
| Keyword map in skill-router covers 50+ domain categories | [skill-router](https://github.com/hmzainjamil/claude-ai-skills) |
| Manual activation: `skill-on <name>` — moves from archive to active | [skill-on](https://github.com/hmzainjamil/claude-ai-skills) |
| Always deactivate non-core after task: `skill-off <name>` | [skill-off](https://github.com/hmzainjamil/claude-ai-skills) |
| find-skills does semantic search — finds skills for vague descriptions | [find-skills](https://github.com/hmzainjamil/claude-ai-skills) |
| Multiple skills can be active simultaneously — they stack | [skill-router](https://github.com/hmzainjamil/claude-ai-skills) |

<a id="tips-reports"></a>
### ■ **Reports (6)**
| Tip | Source |
|---|---|
| report-creator auto-routes: PDF/XLSX/PPTX/DOCX based on prompt keywords | [report-creator](https://github.com/hmzainjamil/claude-ai-skills) |
| ReportLab for PDF — never HTML-to-PDF (layout breaks) | [reportlab](https://reportlab.com) |
| LaTeX templates: nasa-latex-docs for institutional, corporate-latex for branded | [templates](https://github.com/hmzainjamil/claude-ai-skills) |
| All generated files save to ~/Downloads — never Desktop | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| Brand palette auto-pulled from client URL — consistent colors in reports | [report-creator](https://github.com/hmzainjamil/claude-ai-skills) |
| Pre-delivery checklist: spacing, typography, charts labeled, data accurate | [report-creator](https://github.com/hmzainjamil/claude-ai-skills) |

<a id="tips-ads"></a>
### ■ **Ads Skills (6)**
| Tip | Source |
|---|---|
| ads-strategy + ads-copy + ads-creative all activate together on "ads" keyword | [skill-router](https://github.com/hmzainjamil/claude-ai-skills) |
| ads-keywords does full keyword research — volume, CPC, competition | [ads-keywords](https://github.com/hmzainjamil/claude-ai-skills) |
| ads-competitors scrapes Meta Ad Library + Google Ads transparency | [ads-competitors](https://github.com/hmzainjamil/claude-ai-skills) |
| Performance Marketing Agent handles full Google + Meta campaign builds | [perf-marketing](https://github.com/hmzainjamil/claude-ai-skills) |
| PPC ultra command stack: /ppc-audit /ppc-report /ppc-keywords /ppc-copy | [ppc-stack](https://github.com/hmzainjamil/claude-ai-skills) |
| Meta ads analyst skill reads last 30 days report → full 360° analysis | [meta-analyst](https://github.com/hmzainjamil/claude-ai-skills) |

<a id="tips-seo"></a>
### ■ **SEO Skills (6)**
| Tip | Source |
|---|---|
| geo skill covers AI visibility: ChatGPT, Gemini, Perplexity, Bing Copilot | [geo](https://github.com/hmzainjamil/claude-ai-skills) |
| geo-technical: crawlability, Core Web Vitals, INP, mobile, JS rendering | [geo-technical](https://github.com/hmzainjamil/claude-ai-skills) |
| geo-schema: JSON-LD structured data — Organization, Article, speakable | [geo-schema](https://github.com/hmzainjamil/claude-ai-skills) |
| geo-content: E-E-A-T signals, topical authority, readability, AI detection | [geo-content](https://github.com/hmzainjamil/claude-ai-skills) |
| geo-citability: why competitors get cited in AI answers — fix gaps | [geo-citability](https://github.com/hmzainjamil/claude-ai-skills) |
| backlink-strategy skill: 360° white-hat link building workflow | [backlink](https://github.com/hmzainjamil/claude-ai-skills) |

<a id="tips-ugc"></a>
### ■ **UGC & Creative (6)**
| Tip | Source |
|---|---|
| ugc-agency skill: 1 prompt → 20 UGC MP4s via Arcads API | [ugc-agency](https://github.com/hmzainjamil/claude-ai-skills) |
| 5 script types: testimonial / DR / pattern interrupt / problem-solution / social | [ugc-agency](https://github.com/hmzainjamil/claude-ai-skills) |
| Actor matching by age/vibe/energy — 200+ AI actors in Arcads | [Arcads](https://arcads.ai) |
| All 20 render jobs fire in parallel — not sequential | [ugc-agency](https://github.com/hmzainjamil/claude-ai-skills) |
| uni1-image-ad skill: Meta image ads via Luma uni-1 → auto-upload | [uni1](https://github.com/hmzainjamil/hmz-ads-creative) |
| KIE.ai skill: Veo 3.1 + Sora 2 + Kling 3.0 video ads | [kie-ai](https://github.com/hmzainjamil/hmz-ads-creative) |

<a id="tips-web"></a>
### ■ **Web Design (6)**
| Tip | Source |
|---|---|
| premium-web-design skill: Stitch → Nano Banana → 21st.dev → pixel-perfect | [premium-web](https://github.com/hmzainjamil/claude-ai-skills) |
| Google Stitch MCP creates mockup from prompt — no Figma needed | [Stitch](https://stitch.google.com) |
| 21st.dev asset library: 3D widgets + reactive components ready to drop in | [21st.dev](https://21st.dev) |
| website-builder-setup skill handles full vercel deploy pipeline | [website-builder](https://github.com/hmzainjamil/claude-ai-skills) |
| ai-website-cloner-template: clone any site structure in minutes | [ai-cloner](https://github.com/hmzainjamil/hmz-installed-repos) |
| vercel-react skill handles best practices for Next.js + Vercel deploys | [vercel](https://github.com/hmzainjamil/claude-ai-skills) |

<a id="tips-manifest"></a>
### ■ **Skill Manifest (6)**
| Tip | Source |
|---|---|
| skills-lock.json tracks hash of each skill — detect unauthorized changes | [skills-lock.json](https://github.com/hmzainjamil/claude-ai-skills) |
| Manifest auto-updates on skill-on/skill-off — always current | [skill-on](https://github.com/hmzainjamil/claude-ai-skills) |
| Version field in manifest — pin specific skill versions for stability | [skills-lock.json](https://github.com/hmzainjamil/claude-ai-skills) |
| Deps field: list skills that must co-activate — manifest enforces | [skills-lock.json](https://github.com/hmzainjamil/claude-ai-skills) |
| Blockchain-style = tamper-evident — any edit changes hash | [skills-lock.json](https://github.com/hmzainjamil/claude-ai-skills) |
| skill-creator auto-adds new skills to manifest on creation | [skill-creator](https://github.com/hmzainjamil/claude-ai-skills) |

---

## ☠️ STARTUPS / BUSINESSES

| Feature | Replaced |
|---|---|
| 200+ Claude Code skills | [Dust.tt](https://dust.tt) skill marketplace |
| Blockchain skill manifest | [npm](https://npmjs.com) package-lock.json |
| Auto-activation routing | [LangChain](https://langchain.com) tool router |
| UGC agency skill (20 ads/prompt) | [Arcads](https://arcads.ai) manual workflow |
| Report creator (PDF/XLSX/PPTX) | [Beautiful.ai](https://beautiful.ai) |
| Premium web design skill | [Framer AI](https://framer.com) |
| caveman compression | [tiktoken](https://github.com/openai/tiktoken) |
| SEO skill stack (geo series) | [Ahrefs](https://ahrefs.com) |
| Ads skill stack | [Madgicx](https://madgicx.com) |
| Context guard | [MemGPT](https://memgpt.readme.io) |
| Skill search | [Algolia](https://algolia.com) |
| Token turbo | [Anthropic token counting](https://docs.anthropic.com) |

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/claude-ai-skills&type=Date)](https://star-history.com/#hmzainjamil/claude-ai-skills&Date)
