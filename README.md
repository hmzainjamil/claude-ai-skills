# claude-ai-skills

> **80+ battle-tested Claude Code skills** powering HMZ AI Agency's ads, SEO, lead gen, web design, and automation pipelines.

Part of [claude-ai-system](https://github.com/hmzainjamil/claude-ai-system) — the full HMZ AI infrastructure.

---

## What Is a Skill?

A Claude Code **skill** is a `SKILL.md` file that permanently extends Claude's behavior in a specific domain. Skills are:

- **Blockchain-gated** — dormant until triggered, auto-loaded by keyword matching
- **Composable** — multiple skills activate together for complex tasks
- **Version-controlled** — tracked, archived, deduplicated
- **Auto-synced** — pushed to GitHub daily at 6:30 AM via LaunchAgent

---

## Skill Architecture

```
~/.claude/skills/                  ← ACTIVE (loaded this session)
~/.claude/skills-archive/          ← ARCHIVED (dormant, 1,000+ versions)
~/.claude/bin/skill-auto-activate  ← Keyword router (fires on every prompt)
~/.claude/bin/skill-on             ← Manual activation
~/.claude/bin/skill-off            ← Manual deactivation
~/.claude/bin/skill-search         ← Find skills by keyword
```

**Activation flow:**
1. User sends prompt
2. `UserPromptSubmit` hook fires `skill-auto-activate`
3. Keyword match → skill(s) loaded into context
4. Claude responds with skill intelligence active
5. After task: skill deactivated → core-only state restored

---

## Skill Categories

### Core (Always Active)
| Skill | Purpose |
|---|---|
| `caveman` | Compress all output — short, dense, zero filler |
| `optimize-commands` | Multi-LLM burst, code agent routing, report creator |
| `launch-optimized` | DigiMinds master command stack |
| `compress` | Token management + context compression |
| `find-skills` | Skill discovery engine |
| `skill-router` | Route prompts to correct skill |

### Ads & PPC
| Skill | Purpose |
|---|---|
| `ads-strategy` | Full paid media strategy, campaign architecture |
| `ads-copy` | Ad copywriting, RSA/DSA, hooks, CTAs |
| `ads-creative` | Creative briefs, visual direction, UGC scripts |
| `ads-keywords` | Keyword research, match types, negative lists |
| `ads-competitors` | Competitor ad analysis, swipe file |
| `ads-reporting` | Performance analysis, ROAS, attribution |
| `google-ads-campaign` | Google Ads Search deployment |
| `meta-ads-campaign` | Meta Ads deployment |
| `ppc-ultra-command-stack` | ULTRA/STEP/DENSE PPC command suite |

### SEO & GEO (AI Search)
| Skill | Purpose |
|---|---|
| `geo` | AI search visibility (ChatGPT, Perplexity, Gemini) |
| `geo-technical` | Technical SEO, crawlability, Core Web Vitals |
| `geo-content` | E-E-A-T, content depth, topical authority |
| `geo-schema` | Schema markup, JSON-LD, structured data |
| `geo-citability` | AI citation scoring, llms.txt compliance |

### Lead Gen & Outbound
| Skill | Purpose |
|---|---|
| `leads-generator` | Advanced lead generation playbook |
| `leadgen-omnichannel` | Research-driven 360 degree demand gen |
| `outbound-dm-writer` | LinkedIn outbound DM sequences |
| `email-sequence` | Cold email sequence generator |
| `client-hunting-indeed` | Indeed + MCP job board pipeline |
| `job-finder-agent` | Autonomous job search + apply |

### Agency & Client
| Skill | Purpose |
|---|---|
| `agency` | Full agency operations framework |
| `agency-client` | Client onboarding, proposals, reporting |
| `agency-pipeline` | BDM sweeps, lead-to-close workflow |
| `proposal-strategist` | Win-theme proposals, RFP responses |

### Web Design & Dev
| Skill | Purpose |
|---|---|
| `website-builder-setup` | Premium web design stack (uipro + framer-motion) |
| `premium-web-design` | Stitch → Nano Banana → 21st.dev pipeline |
| `frontend-design` | React, Next.js, Tailwind best practices |
| `web-artifacts-builder` | Canvas, SVG, interactive components |
| `vercel-react-best-practices` | Vercel + React performance |

### AI & Automation
| Skill | Purpose |
|---|---|
| `mcp-builder` | Build MCP servers for Claude |
| `mcp-apify-tool-builder` | Apify actor → MCP tool pipeline |
| `apify-actor-development` | Custom Apify actor creation |
| `schedule` | Cron-scheduled remote agents |
| `auto-learn` | Session learning → memory files |

### Reporting & Analytics
| Skill | Purpose |
|---|---|
| `report-creator` | PDF, DOCX, XLSX, LaTeX, PPTX reports |
| `ads-reporting-automation` | Weekly/daily ad performance reports |
| `ppc-reporting-insight-pack` | Cross-channel PPC insight reports |
| `analytics-tracking` | GA4, GTM, Meta Pixel setup + audit |
| `xlsx` | Excel report generation |
| `pdf` | PDF creation and analysis |

---

## Usage

### Auto-activation (fires on every prompt)

```
"Audit my Google Ads account"        → ads-strategy + ads-reporting
"Build a landing page"               → website-builder + premium-web-design
"Find leads on LinkedIn"             → leads-generator + outbound-dm-writer
"Generate a PDF report"              → report-creator + pdf
```

### Manual activation

```bash
~/.claude/bin/skill-on ads-strategy
~/.claude/bin/skill-search "keyword research"
~/.claude/bin/skill-off ads-strategy
```

---

## Skill Archive

Skills cycle: `active → archived → deduplicated → pushed to hmz-skills-archive`

See: [hmz-skills-archive](https://github.com/hmzainjamil/hmz-skills-archive)

---

## Full System

[claude-ai-system](https://github.com/hmzainjamil/claude-ai-system) | [claude-ai-agents](https://github.com/hmzainjamil/claude-ai-agents) | [claude-ai-automations](https://github.com/hmzainjamil/claude-ai-automations)

---

*Auto-updated daily by github-sync — HMZ AI Agency*
