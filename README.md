# Claude AI Skills

A curated collection of Claude Code skill folders. Each top-level skill folder contains a `SKILL.md`; some include supporting scripts, data, or references. At the `main` tree checked for this update on 2026-10-02, 45 top-level folders contained `SKILL.md`. That is a repository snapshot count, not a runtime discovery or activation count.

## Scope and status

| Item | Evidence |
|---|---|
| Content | Skill instructions, with selected helper files |
| Expected format | Claude Code-oriented `SKILL.md` files; inspect each skill for its own requirements |
| Runtime | Not included or verified by this repository |
| Install/setup | No repository-wide installer or package manifest was found in the inspected tree |
| Validation | No tests or runtime checks were run for this documentation change |

## Browse the collection

- [Skill router](skill-router/SKILL.md): prompts for task context and recommends relevant skills
- [UI/UX Pro Max](ui-ux-pro-max/SKILL.md): design guidance with searchable data and scripts
- [Compress](compress/SKILL.md): skill instructions; helper CLI source is under `compress/scripts/`
- [All Agents](all-agents/SKILL.md): orchestration guidance. Its setup document contains historical counts and integrations; verify those separately before relying on them
- Other top-level folders group skills for web design, marketing, lead research, document creation, agent workflows, context management, and related tasks

Read a skill's `SKILL.md` and any linked references before using it. Folder presence alone does not mean Claude Code has loaded or activated a skill.

## Use

1. Select a skill that matches the task.
2. Read its instructions and check linked files, prerequisites, external services, and commands.
3. Use it through a Claude Code workflow that supports the skill format, following the current Claude Code documentation.
4. Verify results in the target environment. This repository does not claim automatic routing, model selection, cost savings, or successful execution.

No bulk installer is provided. Copy only reviewed skill folders into the location supported by your Claude Code setup. Back up existing files first; avoid copying secrets, local configuration, or unrelated data.

## Security and provenance

Skills may recommend third-party services or actions. Review instructions before use, especially where a skill handles credentials, user data, network requests, file changes, or external actions. Keep credentials outside the repository.

Some skills describe external projects, integrations, or performance figures. Treat such claims as skill-authored guidance until verified from a current authoritative source. Preserve attribution and license terms when adapting content.

## Maintenance

When a skill changes, update its own instructions and links in the same change. Record tested commands only after running them, with the environment and date. Regenerate this snapshot count from the Git tree when updating the README.
