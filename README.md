# claude-ai-skills
Blockchain-gated Claude Code skill ecosystem — 13 always-on core skills + 100+ domain skills loaded only when needed, zero context bloat.

![core](https://img.shields.io/badge/core_skills-13_always_on-blue?style=flat&labelColor=555) ![archive](https://img.shields.io/badge/archive-100%2B_dormant-gray?style=flat&labelColor=555) ![manifest](https://img.shields.io/badge/manifest-blockchain_gated-orange?style=flat&labelColor=555) ![activation](https://img.shields.io/badge/activation-auto_%2B_on_demand-green?style=flat&labelColor=555)

[Concepts](#-concepts) · [Hot](#-hot) · [Architecture](#️-architecture) · [Tips](#-tips-and-tricks-24) · [Replaced](#️-startups--businesses) · [Stars](#star-history)

---

## 🧠 CONCEPTS

| Feature | Location | Description |
|---------|----------|-------------|
| [**Core Skills (13)**](skills-active/) | `~/.claude/skills/` | Always-on: `caveman` `compress` `context-compression` `compact-guard` `skill-router` `find-skills` `launch-optimized` `summarize` + 5 more — load at session start, never unload |
| [**Skills Archive (100+)**](skills-archive/) | `~/.claude/skills-archive/` | Dormant domain skills — `ads-strategy` `geo` `legal` `all-agents` `apify-*` `market-*` — moved to active on demand |
| [**skill-auto-activate**](automations/bin/skill-auto-activate) | `~/.claude/bin/skill-auto-activate` | UserPromptSubmit hook — keyword-matches every prompt → auto-loads matching domain skills before Claude responds |
| [**Blockchain Manifest**](config/skills-lock.json) | `~/.claude/skills-lock.json` | JSON manifest tracking exactly which skills are active, when loaded, by what trigger — single source of truth |
| [**SKILL.md Format**](skills-active/) | `<skill>/SKILL.md` | Frontmatter: `name` `description` `triggers` `tier` `dependencies` · Body: Purpose, Instructions, Examples, Gotchas |
| [**Skill CLI**](automations/bin/) | `~/.claude/bin/skill-*` | `skill-on` `skill-off` `skill-search` `skill-status` `skill-reset` — full lifecycle management |
| [**Auto-activation Map**](CLAUDE.md) | `CLAUDE.md` | ads/ppc → ads-* skills · seo/geo → geo-* · legal → legal-* · agent → all-agents · apify → apify-* |

### 🔥 Hot

| Feature | Location | Description |
|---------|----------|-------------|
| [**context forking**](skills-active/context-compression/) | `context-compression/SKILL.md` | Skills with `context: fork` run in isolated subagent — main context never sees intermediate tool calls |
| [**shell injection**](skills-active/) | `SKILL.md` | Embed `` !`command` `` in SKILL.md — shell output injected at invocation time, model sees result not script |
| [**progressive disclosure**](skills-archive/) | `skills-archive/<name>/references/` | Skills use `references/` subdirectories — main SKILL.md stays small, deep content loaded on demand |

---

## ⚙️ ARCHITECTURE

```
Every prompt →
  UserPromptSubmit hook
        │
        ▼
  skill-auto-activate
        │
   keyword match?
   ├── YES → skill-on <name> → moves archive→active → updates manifest
   └── NO  → core skills only (zero overhead)

Session context:
  ~/.claude/skills/    ← active skills loaded here
  skills-lock.json     ← manifest: what's active + timestamp

After task:
  skill-off <name> → moves active→archive → updates manifest
```

| Layer | File | Purpose |
|-------|------|---------|
| Core skills | `~/.claude/skills/<name>/SKILL.md` | Always loaded, never unloaded |
| Domain skills | `~/.claude/skills-archive/<name>/SKILL.md` | Load on demand, unload after task |
| Manifest | `~/.claude/skills-lock.json` | Blockchain-style active state tracking |
| Hook | `~/.claude/bin/skill-auto-activate` | Auto-activation on every prompt |
| CLI | `~/.claude/bin/skill-on/off/search/status/reset` | Manual lifecycle management |

---

## 💡 TIPS AND TRICKS (24)

[Core](#tips-core) · [Domain](#tips-domain) · [Format](#tips-format) · [Auto](#tips-auto) · [Perf](#tips-perf) · [Debug](#tips-debug)

<a id="tips-core"></a>■ **Core Skills (4)**

| Tip | Source |
|-----|--------|
| `caveman` compresses all output — saves 30-40% tokens on every response | [caveman SKILL.md](skills-active/) |
| `compact-guard` blocks context dumps before overflow — fires before `/compact` is needed | [compact-guard](skills-active/) |
| `context-compression` and `context-window-management` work together — never disable either | [Core pair](skills-active/) |
| `launch-optimized` runs once at session start — verifies RAM, Ollama, Paperclip, LaunchAgents | [launch-optimized](skills-active/) |

<a id="tips-domain"></a>■ **Domain Skills (5)**

| Tip | Source |
|-----|--------|
| Always `skill-off <name>` after task — loaded domain skills bloat context and slow responses | [Gating rule](CLAUDE.md) |
| Never keep more than 3-4 domain skills active simultaneously | [Performance rule](CLAUDE.md) |
| `skill-search "keyword"` finds the right skill before activating — avoids guessing | [skill-search](automations/bin/) |
| `skill-status` shows manifest: active skills + load timestamps | [skill-status](automations/bin/) |
| New skills go to archive first — test with `skill-on`, promote only if stable | [Dev workflow](skills-archive/) |

<a id="tips-format"></a>■ **SKILL.md Format (5)**

| Tip | Source |
|-----|--------|
| `description` field = auto-match trigger — write for the model: "when should I fire?" | [Thariq](https://x.com/trq212) |
| `triggers` list must be specific — broad keywords fire on wrong prompts | [Thariq](https://x.com/trq212) |
| Build a Gotchas section in every skill — highest-signal content, captures failure patterns | [Thariq](https://x.com/trq212) |
| Don't state the obvious in skills — focus on what pushes Claude out of default behavior | [Thariq](https://x.com/trq212) |
| Include scripts and libraries in `references/` — Claude composes rather than reconstructs | [Thariq](https://x.com/trq212) |

<a id="tips-auto"></a>■ **Auto-Activation (4)**

| Tip | Source |
|-----|--------|
| `skill-auto-activate` fires on every UserPromptSubmit — check `settings.json` hook config | [Hook config](config/) |
| Activation map: `ads\|ppc\|meta\|google ads` → ads-strategy+ads-copy+ads-creative+ads-keywords | [CLAUDE.md](CLAUDE.md) |
| `seo\|geo\|ranking` → geo+geo-technical+geo-content+geo-schema | [CLAUDE.md](CLAUDE.md) |
| `agent\|orchestrate\|multi-agent` → all-agents (full 50-agent roster) | [CLAUDE.md](CLAUDE.md) |

<a id="tips-perf"></a>■ **Performance (3)**

| Tip | Source |
|-----|--------|
| Active skill count < 5 = healthy · 5-8 = degraded · 8+ = reset immediately | [Performance threshold](CLAUDE.md) |
| Long SKILL.md (>500 lines) slows context loading — use `references/` for deep content | [Size limit](CLAUDE.md) |
| Core skills are pre-optimized — touch them only if something is broken | [Design principle](skills-active/) |

<a id="tips-debug"></a>■ **Debug (3)**

| Tip | Source |
|-----|--------|
| Skill not activating → check `triggers` list in frontmatter — add missing keyword | [Debug](automations/bin/) |
| Manifest out of sync → `skill-reset` rebuilds from filesystem | [skill-reset](automations/bin/) |
| Symlink conflict → delete symlink, re-create as directory with `SKILL.md` inside | [Git issue](automations/bin/github-sync) |

---

## ☠️ STARTUPS / BUSINESSES

| Feature | Replaced |
|-|-|
| **Blockchain skill manifest** | [Continue.dev](https://continue.dev), [Cursor Rules](https://cursor.sh) — static, no gating or manifest |
| **Auto-activation by keyword** | Manual `@mention` skill selection, copy-pasting instructions every prompt |
| **On-demand domain loading** | Loading all rules always → context bloat → slower + more expensive |
| **skill-off deactivation** | Forgetting to clear context → degraded performance over long sessions |
| **Progressive disclosure (`references/`)** | Monolithic 2000-line instruction files |
| **shell injection in SKILL.md** | Static snapshots that go stale immediately |

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/claude-ai-skills&type=Date)](https://star-history.com/#hmzainjamil/claude-ai-skills&Date)