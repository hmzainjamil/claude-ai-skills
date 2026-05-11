<p align="center">
  <img src="https://img.shields.io/badge/HMZ-AI%20SKILLS-246DFF?style=for-the-badge&logoColor=white" alt="HMZ AI Skills" height="60">
</p>

<h1 align="center">Claude AI Skills</h1>

<p align="center">
  <strong>45+ production-grade Claude Code skills — auto-activate on keyword detection, zero manual setup</strong>
</p>

<p align="center">
  <a href="https://github.com/hmzainjamil"><img src="https://img.shields.io/badge/By-HMZ-6C3EE8?style=for-the-badge" alt="By HMZ"></a>
  <a href="#skills"><img src="https://img.shields.io/badge/Skills-45%2B-246DFF?style=for-the-badge" alt="45+ Skills"></a>
  <a href="#"><img src="https://img.shields.io/badge/Claude%20Code-Native-15C1E6?style=for-the-badge" alt="Claude Code Native"></a>
  <a href="#"><img src="https://img.shields.io/badge/Auto%20Activation-ON-20A34E?style=for-the-badge" alt="Auto Activation"></a>
  <a href="https://github.com/hmzainjamil/claude-ai-skills/stargazers"><img src="https://img.shields.io/github/stars/hmzainjamil/claude-ai-skills?style=for-the-badge&color=9D97F4&label=Stars" alt="Stars"></a>
</p>

<p align="center">
  <a href="#overview">Overview</a> &bull;
  <a href="#quick-start">Quick Start</a> &bull;
  <a href="#skills">Skills</a> &bull;
  <a href="#use-cases">Use Cases</a> &bull;
  <a href="#installation">Installation</a> &bull;
  <a href="#resources">Resources</a>
</p>

---

## Overview

**Claude AI Skills** is the active skills library for the HMZ AI system. Each skill is a `.md` file that extends Claude Code with deep domain expertise, tool integrations, and automatic activation — when you mention a relevant keyword, the right skill fires without you doing anything.

Skills are self-contained, composable, and production-tested:
- **Auto-activation** — keyword hooks fire skills before Claude even processes your prompt
- **Tool-aware** — each skill knows exactly which MCP tools, APIs, and commands to call
- **Composable** — skills chain together (e.g. `ads-strategy` + `ads-creative` + `ads-copy` for a full campaign)
- **Zero overhead** — non-core skills deactivate after each task; only 12 core skills always run

---

## Quick Start

```bash
# Skills activate automatically — just describe what you need:
"Audit my Google Ads campaign structure and wasted spend"
# → ads-strategy + ads-keywords + ads-competitors auto-activate

"Find top 50 plumbers in Austin — phone, email, rating. Export Excel."
# → lead-gen-ai auto-activates + runs Vibe Prospecting + Apollo MCP

"Generate 20 UGC video scripts for skincare brand, match Arcads actors"
# → ads-creative + ugc-agency auto-activate

"Build a premium Next.js site for my agency. Deploy to Vercel."
# → website-builder + launch-optimized auto-activate
```

---

## Skills

### Paid Media & Ads (7 skills)

| Skill | Trigger keywords | What it delivers |
|---|---|---|
| `ads-strategy` | ads, ppc, google ads, meta ads, campaign | Full campaign architecture, budget allocation, bidding strategy |
| `ads-creative` | creative, ugc, video ad, arcads | AI ad creative generation — image, video, UGC, scripts |
| `ads-copy` | ad copy, headlines, RSA, ad text | RSA optimization, headline banks, description rotation |
| `ads-keywords` | keywords, search terms, negative keywords | Keyword research, match types, negative architecture |
| `ads-competitors` | competitor ads, spy ads, ad library | Meta Ad Library scraping → Airtable swipe file |
| `ads-audience` | audience, targeting, lookalike | Audience research, lookalike stacks, exclusions |
| `ads-funnel` | funnel, TOFU, MOFU, BOFU | Full funnel strategy + landing page mapping |

### SEO & GEO (5 skills)

| Skill | Trigger keywords | What it delivers |
|---|---|---|
| `geo-technical` | seo, crawl, indexability, core web vitals | Technical SEO audit: crawlability, INP, schema, robots |
| `geo-content` | content quality, E-E-A-T, topical authority | Content audit: depth, readability, AI content detection |
| `geo-schema` | schema markup, JSON-LD, structured data | Schema generation: Organization, Article, FAQ, Product |
| `geo-citability` | AI search, ChatGPT citations, Perplexity | AEO/GEO: why competitors get cited, how to fix it |
| `geo-platform` | AI Overviews, Gemini, Bing Copilot | Readiness audit for Google AI Overviews, ChatGPT search |

### Marketing & Content (8 skills)

| Skill | What it does |
|---|---|
| `market-launch` | Full GTM strategy: ICP, messaging, channels, calendar, KPIs |
| `market-copy` | Conversion copy: landing pages, VSLs, email, ad copy |
| `market-brand` | Brand voice extraction, guideline generation, enforcement |
| `market-emails` | Email sequences: cold, nurture, re-engagement, transactional |
| `market-social` | Social content: LinkedIn, Twitter, Instagram, TikTok |
| `market-funnel` | Funnel architecture: TOFU → MOFU → BOFU → retention |
| `market-ads` | Paid media creative brief + channel selection |
| `market` | General marketing strategy and planning |

### Scraping & Data (3 skills)

| Skill | What it does |
|---|---|
| `apify-ultimate-scraper` | Universal scraper: 130+ Actors for any site, automatic Actor selection |
| `apify-actor-development` | Create, debug, deploy Apify Actors from scratch |
| `apify-actorization` | Convert any script to an Apify Actor |

### Infrastructure & Optimization (6 skills)

| Skill | What it does |
|---|---|
| `launch-optimized` | Multi-LLM burst: 15 models fire in parallel, best wins |
| `optimize-commands` | Always-on: code agent, report creator, agency agent routing |
| `optimize-dgm-command` | DGM (Directed Graph Model) command optimization |
| `compress` | Context compression: extract signal, strip noise |
| `token-turbo` | Token minimization: caveman compression on all outputs |
| `caveman` | Ultra-compressed responses: max 150 words, bullets only |

---

## Use Cases

| Goal | Skills activated | Example prompt |
|---|---|---|
| **Full Google Ads audit** | `ads-strategy` + `ads-keywords` | "Audit campaign structure — quality scores, impression share, wasted spend by ad group" |
| **Meta competitor swipe file** | `ads-competitors` | "Scrape last 90 days of ads for [brand] from Meta Ad Library, save to Airtable by format" |
| **Technical SEO audit** | `geo-technical` + `geo-schema` | "Full technical audit of [domain] — Core Web Vitals, crawlability, schema coverage, AI visibility" |
| **Cold email sequence** | `market-emails` + `market-copy` | "7-email B2B cold sequence for digital agency targeting DTC brands doing $1M+ revenue" |
| **Lead generation** | `lead-gen-ai` (Vibe + Apollo) | "50 chiropractors in Chicago — name, phone, email, Instagram, Google rating. Excel export." |
| **AI search optimization** | `geo-citability` | "Why does [competitor] get cited in ChatGPT for [query] but we don't? Fix it." |
| **Product launch** | `market-launch` | "Full GTM for SaaS tool targeting SMB e-commerce — ICP, positioning, 90-day launch calendar" |

---

## Installation

### Claude Code

```bash
# Add the full skills library
git clone https://github.com/hmzainjamil/claude-ai-skills.git ~/.claude/skills

# Or install individual skills via plugin
/plugin install ads-strategy@claude-ai-skills
/plugin install apify-ultimate-scraper@claude-ai-skills
```

### Auto-activation setup

The `skill-auto-activate` hook runs on every prompt. To enable:

```bash
# Verify hook is registered
cat ~/.claude/settings.json | grep skill-auto-activate

# Manual skill activation
~/.claude/bin/skill-on ads-strategy
~/.claude/bin/skill-off ads-strategy   # deactivate after task
```

---

## Resources

- **[claude-ai-system](https://github.com/hmzainjamil/claude-ai-system)** — Full HMZ system
- **[hmz-skills-archive](https://github.com/hmzainjamil/hmz-skills-archive)** — 200+ archived skills
- **[hmz-antigravity-awesome-skills](https://github.com/hmzainjamil/hmz-antigravity-awesome-skills)** — 55K char curated skill collection
- **[claude-ai-agents](https://github.com/hmzainjamil/claude-ai-agents)** — 210 specialist agents
- **[Apify MCP server](https://mcp.apify.com/)** — powers the scraping skills

---

## Support

- [Open an issue](https://github.com/hmzainjamil/claude-ai-skills/issues)
- [LinkedIn](https://linkedin.com/in/hmzainjamil)

## License

MIT

---

<p align="center">Built by <a href="https://github.com/hmzainjamil">Hafiz Muhammad Zulqarnain</a> &mdash; HMZ AI Agency</p>