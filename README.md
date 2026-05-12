# claude-ai-skills
> 300+ production skills for Claude Code — ads, SEO, legal, marketing, agency ops, PDF, Excel, PPTX.

[![skills](https://img.shields.io/badge/skills-300+-blue?style=flat&labelColor=555)](skills-active/)
[![categories](https://img.shields.io/badge/categories-25-green?style=flat&labelColor=555)](skills-active/)
[![blockchain-gate](https://img.shields.io/badge/activation-blockchain--gate-purple?style=flat&labelColor=555)](.)
[![tier0](https://img.shields.io/badge/routing-tier0-orange?style=flat&labelColor=555)](.)
[![license](https://img.shields.io/badge/license-MIT-lightgrey?style=flat&labelColor=555)](LICENSE)

[concepts](#concepts) · [architecture](#architecture) · [tips](#tips) · [startups](#startups) · [star](#star)

---

## 🧠 CONCEPTS <a id="concepts"></a>

| Feature | Location | Description |
|---|---|---|
| [**Ads Skills**](skills-active/ads-strategy/) | `skills-active/ads-*/` | 12 skills: strategy, copy, creative, keywords, funnel, audience, video, testing |
| [**SEO / GEO Skills**](skills-active/geo/) | `skills-active/geo*/` | 8 skills: technical, content, schema, citability, brand-mentions, proposal |
| [**Legal Skills**](skills-active/legal/) | `skills-active/legal*/` | 8 skills: review, NDA, risks, missing clauses, privacy, compare, report-pdf |
| [**Market Skills**](skills-active/market/) | `skills-active/market*/` | 10 skills: brand, copy, funnel, emails, social, SEO, landing, proposal |
| [**Agency Skills**](skills-active/agency-digital-marketing/) | `skills-active/agency*/` | 6 skills: digital-marketing, pipeline, client, status, onboard, propose |
| [**Report Skills**](skills-active/reportlab-pdf-master/) | `skills-active/report*` | PDF (ReportLab), DOCX, XLSX, PPTX — institutional grade outputs |
| [**Skill Router**](skills-active/skill-router/) | `skills-active/skill-router/` | Auto-routes prompts to the correct skill via keyword matching |
| [**Caveman Compression**](skills-active/caveman/) | `skills-active/caveman/` | Enforces 40-60% token reduction on all sub-task outputs |

### 🔥 Hot

| Feature | Location | Description |
|---|---|---|
| [**ReportLab PDF Master**](skills-active/reportlab-pdf-master/) | `skills-active/reportlab-pdf-master/` | 12 hard laws — zero overlaps, brand palette from URL, direct PDF never HTML |
| [**vibe-prospecting**](skills-active/vibe-prospecting/) | `skills-active/vibe-prospecting/` | Vibe Prospecting MCP — find + enrich + export leads to Excel in one prompt |
| [**lead-gen-ai**](skills-active/lead-gen-ai/) | `skills-active/lead-gen-ai/` | 5-actor pipeline: brief → vibe extract → apollo enrich → format → outreach |

---

## ⚙️ ARCHITECTURE <a id="architecture"></a>

```
UserPromptSubmit
      │
skill-auto-activate (keyword scan)
      │
┌─────┴──────────────────────────────────────┐
│            BLOCKCHAIN GATE                  │
│  Core always-on:                           │
│  caveman · compact-guard · skill-router    │
│  context-compression · find-skills        │
│             ↓                              │
│  Domain skills — activated by keyword:     │
│  ads → ads-strategy + ads-copy + ...      │
│  seo → geo + geo-technical + ...          │
│  legal → legal + legal-review + ...       │
└─────────────────────────────────────────────┘
      │
task execution (Tier 0 models)
      │
skill-off → collapse back to core
```

| Skill Category | Count | Trigger keywords |
|---|---|---|
| Ads / PPC | 12 | ads, ppc, meta, google ads, campaign |
| SEO / GEO | 8 | seo, geo, ranking, schema, crawl |
| Legal | 8 | legal, contract, nda, compliance |
| Marketing | 10 | marketing, brand, email, funnel |
| Agency | 6 | agency, client, proposal, pipeline |
| Reports / PDF | 8 | report, pdf, audit, excel, pptx |

---

## 💡 TIPS AND TRICKS (16) <a id="tips"></a>

[skill-ops](#tips-ops) · [pdf-laws](#tips-pdf) · [ads-skills](#tips-ads) · [activation](#tips-activation)

<a id="tips-ops"></a>
■ **Skill Operations (4)**

| Tip | Source |
|---|---|
| `~/.claude/bin/skill-search "topic"` finds skills before activating — prevents wrong skill | [hmzainjamil](https://github.com/hmzainjamil) |
| Skills in `~/.claude/skills-archive/` are dormant — `skill-on` moves to active, `skill-off` archives | [hmzainjamil](https://github.com/hmzainjamil) |
| `~/.claude/bin/skill-status` lists all active skills and their last activation time | [hmzainjamil](https://github.com/hmzainjamil) |
| Never leave >5 skills active simultaneously — context window fills, quality drops | [hmzainjamil](https://github.com/hmzainjamil) |

<a id="tips-pdf"></a>
■ **PDF / Report Laws (4)**

| Tip | Source |
|---|---|
| Always use ReportLab directly — never HTML-to-PDF, never wkhtmltopdf for production reports | [ReportLab](https://reportlab.com) |
| Pull client brand palette from their website URL before first page is drawn | [hmzainjamil](https://github.com/hmzainjamil) |
| Save all reports to `~/Downloads/` — never Desktop, never `/tmp/` | [hmzainjamil](https://github.com/hmzainjamil) |
| Pre-delivery checklist: spacing ✓ typography ✓ charts labeled ✓ no overlaps ✓ | [hmzainjamil](https://github.com/hmzainjamil) |

<a id="tips-ads"></a>
■ **Ads Skills (4)**

| Tip | Source |
|---|---|
| `ads-strategy` + `ads-copy` always activate together — they share the same campaign context | [hmzainjamil](https://github.com/hmzainjamil) |
| `ads-competitors` skill uses Meta Ad Library scraper + Apollo for competitor intel | [Meta](https://www.facebook.com/ads/library) |
| `ads-report-pdf` generates 11-page 360° audit PDFs with client brand palette | [hmzainjamil](https://github.com/hmzainjamil) |
| `ads-keywords` skill: Google Ads Keyword Planner API + Kimi K2.6 for intent clustering | [Google Ads](https://ads.google.com) |

<a id="tips-activation"></a>
■ **Activation Protocol (4)**

| Tip | Source |
|---|---|
| Blockchain gate: only core skills active by default — domain skills activate on demand | [hmzainjamil](https://github.com/hmzainjamil) |
| `skill-auto-activate` runs on EVERY prompt via UserPromptSubmit hook — no manual activation needed | [hmzainjamil](https://github.com/hmzainjamil) |
| Skill Markdown format: `# Skill Name`, `## Trigger`, `## Instructions`, `## Examples` | [Claude Code](https://docs.anthropic.com) |
| Use `npx skills add repo/name` to install new skills from OpenClaw marketplace | [OpenClaw](https://openclaw.agent37.com) |

---

## ☠️ STARTUPS / BUSINESSES <a id="startups"></a>

| Feature | Replaced |
|---|---|
| **300+ production skills** | [Jasper AI](https://jasper.ai), [Copy.ai](https://copy.ai), [Writesonic](https://writesonic.com) |
| **Auto-activation blockchain gate** | [LangChain tools](https://langchain.com), [AutoGPT plugins](https://autogpt.net) |
| **ReportLab PDF reports** | [Beautiful.ai](https://beautiful.ai), [Canva PDF](https://canva.com), [Adobe Acrobat AI](https://adobe.com) |
| **Legal skill stack** | [Harvey AI](https://harvey.ai), [Spellbook](https://spellbook.legal), [ContractPodAi](https://contractpodai.com) |
| **Agency digital marketing skills** | [HubSpot AI](https://hubspot.com), [Salesforce Einstein](https://salesforce.com/products/einstein/) |

---

## Star History <a id="star"></a>

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/claude-ai-skills&type=Date)](https://star-history.com/#hmzainjamil/claude-ai-skills&Date)
