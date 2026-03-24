# Superpowers Overview

> A complete software development workflow for coding agents, built on composable "skills" that activate automatically.

**Author:** [Jesse Vincent](https://blog.fsck.com) / [Prime Radiant](https://primeradiant.com)
**Repository:** [obra/superpowers](https://github.com/obra/superpowers)
**License:** MIT
**Community:** [Discord](https://discord.gg/Jd8Vphy9jq)

---

## What Is Superpowers?

Superpowers is a plugin system that transforms how coding agents approach software development. Instead of jumping straight into writing code, the agent follows a structured process:

1. **Understands intent** - Asks what you're really trying to do
2. **Designs first** - Presents the design in digestible chunks for validation
3. **Plans meticulously** - Creates implementation plans clear enough for execution
4. **Executes with discipline** - Uses subagent-driven development with two-stage review
5. **Verifies with evidence** - Never claims "done" without proof

The skills trigger automatically - you don't invoke them manually. Your coding agent just has Superpowers.

---

## Core Philosophy

| Principle                  | Description                                |
| -------------------------- | ------------------------------------------ |
| **Test-Driven Development**| Write tests first, always                  |
| **Systematic over Ad-hoc** | Process over guessing                      |
| **Complexity Reduction**   | Simplicity as the primary goal             |
| **Evidence over Claims**   | Verify before declaring success            |
| **YAGNI**                  | You Aren't Gonna Need It                   |
| **DRY**                    | Don't Repeat Yourself                      |

---

## Installation

### Claude Code (Official Marketplace)

```bash
/plugin install superpowers@claude-plugins-official
```

### Claude Code (Community Marketplace)

```bash
/plugin marketplace add obra/superpowers-marketplace
/plugin install superpowers@superpowers-marketplace
```

### Cursor

```text
/add-plugin superpowers
```

Or search for "superpowers" in the plugin marketplace.

### Gemini CLI

```bash
gemini extensions install https://github.com/obra/superpowers
```

### Codex / OpenCode

Tell the agent:

```
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.codex/INSTALL.md
```

*(Replace `.codex` with `.opencode` for OpenCode.)*

### Verify Installation

Start a new session and ask for something like "help me plan this feature" or "let's debug this issue." The agent should automatically invoke the relevant skill.

### Updating

```bash
/plugin update superpowers
```

---

## Skills Library

### Testing

| Skill | Purpose |
| ----- | ------- |
| `test-driven-development` | RED-GREEN-REFACTOR cycle with anti-patterns reference |

### Debugging

| Skill | Purpose |
| ----- | ------- |
| `systematic-debugging` | 4-phase root cause process (root-cause-tracing, defense-in-depth, condition-based-waiting) |
| `verification-before-completion` | Ensure the fix is real before closing |

### Collaboration

| Skill                            | Purpose                                   |
| -------------------------------- | ----------------------------------------- |
| `brainstorming`                  | Socratic design refinement                |
| `writing-plans`                  | Detailed, step-level implementation plans |
| `executing-plans`                | Batch execution with human checkpoints    |
| `dispatching-parallel-agents`    | Concurrent subagent workflows             |
| `subagent-driven-development`    | Fast iteration with two-stage review      |
| `requesting-code-review`         | Pre-review checklist                      |
| `receiving-code-review`          | Responding to feedback                    |
| `using-git-worktrees`            | Parallel development branches             |
| `finishing-a-development-branch` | Merge/PR decision workflow                |

### Meta

| Skill | Purpose |
| ----- | ------- |
| `writing-skills` | Create new skills following best practices |
| `using-superpowers` | Introduction to the skills system |

---

## Related Notes

- [[Superpowers Workflow]] - The end-to-end development workflow
- [[Superpowers Prompts]] - Ready-to-use prompts for common tasks
- [[Command Slash]] - Slash command reference
