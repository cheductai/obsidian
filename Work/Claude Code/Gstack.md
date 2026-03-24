# Gstack

> A "software factory" that transforms Claude Code into a virtual engineering team via 28 specialized slash-command skills.

**Author:** [Garry Tan](https://github.com/garrytan) (President & CEO, Y Combinator)
**Repository:** [garrytan/gstack](https://github.com/garrytan/gstack)
**License:** MIT
**Claim:** 600,000+ lines of production code in 60 days (35% tests) at 10,000-20,000 lines/day

---

## What Is Gstack?

Gstack is an open-source skill system for Claude Code that provides a structured sprint cycle: **Think -> Plan -> Build -> Review -> Test -> Ship -> Reflect**. Each skill feeds output into the next stage, ensuring no gaps. It also supports Codex, Gemini CLI, and Cursor.

Unlike [Superpowers](Superpowers/Superpowers%20Overview.md) which triggers skills automatically, gstack uses explicit slash commands — you invoke each skill manually.

---

## Installation

**Requirements:** Claude Code, Git, Bun v1.0+, Node.js (Windows only)

### Global Install
```bash
git clone https://github.com/garrytan/gstack.git ~/.claude/skills/gstack
cd ~/.claude/skills/gstack && ./setup
```

### Per-Project (Team Access)
```bash
cp -Rf ~/.claude/skills/gstack .claude/skills/gstack
rm -rf .claude/skills/gstack/.git
cd .claude/skills/gstack && ./setup
```

### Other Agents
```bash
git clone https://github.com/garrytan/gstack.git .agents/skills/gstack
cd .agents/skills/gstack && ./setup --host codex  # or --host auto
```

---

## Sprint Cycle & All 28 Skills

### Think
| Command | Purpose |
|---------|---------|
| `/office-hours` | YC-style product reframing — six forcing questions, challenges premises, generates 3+ approaches with effort estimates |

### Plan
| Command | Purpose |
|---------|---------|
| `/plan-ceo-review` | CEO perspective: expansion, selective expansion, hold scope, or reduction modes |
| `/plan-eng-review` | Architecture lock-in — ASCII diagrams, data flow, state machines, edge cases, test matrices |
| `/plan-design-review` | Rates design dimensions 0-10, explains what a 10 looks like, AI-slop detection |
| `/design-consultation` | Builds complete design systems from scratch with landscape research and mockups |

### Build
| Command | Purpose |
|---------|---------|
| `/autoplan` | Runs CEO + design + eng review automatically with encoded decision principles |

### Review
| Command | Purpose |
|---------|---------|
| `/review` | Staff-engineer-level review — finds production bugs, auto-fixes obvious issues, flags gaps |
| `/investigate` | Systematic root-cause debugging with hypothesis testing (stops after 3 failed fixes) |
| `/design-review` | Designer-coder hybrid — audits and fixes with atomic commits + before/after screenshots |
| `/codex` | Independent second opinion via OpenAI Codex CLI: review gate, adversarial challenge, or consultation |

### Test
| Command | Purpose |
|---------|---------|
| `/qa` | Opens real browser, tests flows, fixes bugs with atomic commits, generates regression tests |
| `/qa-only` | Pure bug reporting — no code changes |
| `/cso` | Chief Security Officer — OWASP Top 10 + STRIDE threat modeling, 8/10+ confidence gate |

### Ship
| Command | Purpose |
|---------|---------|
| `/ship` | Syncs main, runs tests, audits coverage, pushes, opens PR |
| `/land-and-deploy` | Merges PR, awaits CI/deploy, verifies production health |
| `/canary` | Post-deploy monitoring — console errors, perf regressions, page failures |
| `/benchmark` | Baselines page load times, Core Web Vitals, resource sizes; before/after comparisons |

### Reflect
| Command | Purpose |
|---------|---------|
| `/retro` | Weekly retrospective — per-person breakdowns, shipping streaks, test health trends (`/retro global` spans all projects) |
| `/document-release` | Updates project docs to match shipped changes, catches stale READMEs |

### Utility
| Command | Purpose |
|---------|---------|
| `/browse` | Real Chromium browser with clicks and screenshots (~100ms per command) |
| `/setup-browser-cookies` | Imports cookies from Chrome/Arc/Brave/Edge into headless sessions |
| `/setup-deploy` | One-time deploy configurator — detects platform, prod URL, deploy commands |
| `/careful` | Safety guardrails — warns before `rm -rf`, `DROP TABLE`, force-push, etc. |
| `/freeze` | Locks edits to a single directory |
| `/guard` | Combined `/careful` + `/freeze` for maximum safety |
| `/unfreeze` | Removes freeze boundary |
| `/gstack-upgrade` | Self-updater — detects global vs. vendored install, shows changelog |

---

## Gstack vs Superpowers

| | Gstack | [Superpowers](Superpowers/Superpowers%20Overview.md) |
|---|---|---|
| **Author** | Garry Tan (YC) | Jesse Vincent (Prime Radiant) |
| **Activation** | Manual slash commands | Automatic skill triggering |
| **Focus** | Full sprint cycle (think to reflect) | Development discipline (design to verify) |
| **Browser testing** | Built-in (`/browse`, `/qa`) | Not included |
| **Security audit** | `/cso` (OWASP + STRIDE) | Not included |
| **Deploy pipeline** | `/ship` -> `/land-and-deploy` -> `/canary` | Not included |
| **Multi-agent** | Conductor for parallel sessions | Subagent-driven development |
| **Design system** | `/design-consultation` + `/design-review` | Not included |
| **Can coexist** | Yes | Yes |

Both are MIT-licensed and can be installed side by side.

---

## Privacy

- **Telemetry:** Off by default. Opt-in only.
- **If enabled:** collects skill name, duration, success/fail, version, OS only.
- **Never collected:** code, file paths, repo names, prompts, or any user content.
- Disable: `gstack-config set telemetry off`
- Local dashboard: `gstack-analytics`

---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| Skills not appearing | `cd ~/.claude/skills/gstack && ./setup` |
| `/browse` failures | `cd ~/.claude/skills/gstack && bun install && bun run build` |
| Stale install | `/gstack-upgrade` or set `auto_upgrade: true` in `~/.gstack/config.yaml` |
| Windows issues | Use Git Bash or WSL; Node.js required alongside Bun (Playwright pipe transport bug) |
