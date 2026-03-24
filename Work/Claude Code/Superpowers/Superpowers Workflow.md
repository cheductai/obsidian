# Superpowers Workflow

> The end-to-end development workflow powered by [[Superpowers Overview|Superpowers]]. Each step maps to a composable skill that activates automatically.

---

## The Full Workflow

### 1. Brainstorm

**Skill:** `brainstorming`
**Trigger:** Before any code is written

The agent does not jump into code. It steps back and:

- Explores your intent and clarifies requirements
- Asks targeted questions before making assumptions
- Identifies edge cases, constraints, and design options
- Presents the design in short, reviewable sections
- Saves a design document once you approve

> **Checkpoint:** Review and approve the design before moving on.

---

### 2. Set Up Isolation

**Skill:** `using-git-worktrees`
**Trigger:** After design approval

- Creates an isolated git worktree on a new branch
- Runs project setup commands
- Verifies a clean test baseline
- Keeps your main workspace untouched

---

### 3. Write a Plan

**Skill:** `writing-plans`
**Trigger:** After design approval

- Breaks work into bite-sized tasks (2-5 minutes each)
- Every task includes exact file paths, complete code, and verification steps
- Produces a concrete implementation plan you can review and edit

> **Checkpoint:** Review and approve the plan before execution begins.

---

### 4. Execute the Plan

**Skill:** `executing-plans` or `subagent-driven-development`
**Trigger:** After plan approval

Two execution modes:

| Mode | Best For |
| ---- | -------- |
| `executing-plans` | Sequential tasks with human checkpoints between batches |
| `subagent-driven-development` | Fast autonomous iteration with two-stage review (spec compliance, then code quality) |

For independent tasks, use `dispatching-parallel-agents` to run multiple subagents concurrently.

**TDD is enforced throughout** (`test-driven-development`):

1. Write a failing test (RED)
2. Write minimal code to pass it (GREEN)
3. Refactor
4. Commit
5. Repeat

> If code is written before its test, the code gets deleted.

---

### 5. Debug Issues

**Skill:** `systematic-debugging`
**Trigger:** When a test fails or unexpected behavior occurs

Four-phase process:

1. **Reproduce** - Confirm the failure is consistent
2. **Hypothesize** - Form ranked hypotheses about root cause
3. **Test** - Systematically validate or eliminate each hypothesis
4. **Fix** - Address the root cause, not the symptom

Includes techniques: root-cause-tracing, defense-in-depth, condition-based-waiting.

---

### 6. Simplify

**Skill:** `/simplify`
**Trigger:** After implementation

- Reviews all changed code for reuse, quality, and efficiency
- Reduces unnecessary complexity
- Fixes any issues found

---

### 7. Verify Before Completion

**Skill:** `verification-before-completion`
**Trigger:** Before claiming anything is done

- Runs ALL tests and verification commands
- Confirms output with evidence - no assumptions
- Never says "done" without proof

---

### 8. Request Code Review

**Skill:** `requesting-code-review`
**Trigger:** After verification passes

- Reviews work against the original requirements
- Checks for missed edge cases, security issues, quality gaps
- Reports issues by severity (critical issues block progress)

---

### 9. Finish the Branch

**Skill:** `finishing-a-development-branch`
**Trigger:** When all tasks are complete and reviewed

- Verifies all tests pass
- Presents options: merge, create PR, keep branch, or discard
- Cleans up the worktree

> **Checkpoint:** Choose your preferred integration method.

---

## Guiding Principles

Throughout the entire workflow:

- **Ask before assuming** - The agent checks in at each milestone
- **User instructions override skill defaults** - You're always in control
- **Evidence before assertions** - No guessing, only proof
- **Simple over clever** - The simplest solution that works

---

## When to Skip Steps

| Situation | Skip |
| --------- | ---- |
| Tiny bug fix | Brainstorm, Plan, Worktree |
| Well-defined spec already exists | Brainstorm |
| Already on a feature branch | Worktree setup |
| Single-file change | Parallel agents |
| No tests in project | TDD *(but suggest adding them)* |

---

## Workflow Diagram

```
Brainstorm ─> Worktree ─> Plan ─> Execute (TDD) ─> Debug (if needed)
                                       │
                                       v
                          Simplify ─> Verify ─> Code Review ─> Finish Branch
```

---

## Related Notes

- [[Superpowers Overview]] - Installation, skills reference, and philosophy
- [[Superpowers Prompts]] - Ready-to-use prompts for common tasks
