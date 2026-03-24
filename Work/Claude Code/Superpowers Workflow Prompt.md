Complete Superpowers Workflow Prompt                                                                                                                                                                                                     
                  
  I need you to implement [TASK DESCRIPTION].                                                                                                                                                                                              
                  
  Follow the full Superpowers workflow:

  1. **Brainstorm** (`/superpowers:brainstorming`)
     - Explore my intent and clarify requirements
     - Ask questions before assuming
     - Identify edge cases, constraints, and design options
     - Reach alignment before moving forward

  2. **Write a Plan** (`/superpowers:writing-plans`)
     - Break the task into discrete, ordered steps
     - Identify critical files and architectural trade-offs
     - Produce a concrete implementation plan I can review

  3. **Set Up Isolation** (`/superpowers:using-git-worktrees`)
     - Create an isolated git worktree for the feature branch
     - Keep main workspace clean

  4. **Execute the Plan** (`/superpowers:executing-plans` or `/superpowers:subagent-driven-development`)
     - For independent tasks: dispatch parallel agents
       (`/superpowers:dispatching-parallel-agents`)
     - For sequential tasks: execute step-by-step with review checkpoints
     - Use TDD throughout (`/superpowers:test-driven-development`):
       a. Write a failing test
       b. Write minimal code to pass it
       c. Refactor
       d. Repeat

  5. **Debug Issues** (`/superpowers:systematic-debugging`)
     - If any test fails or unexpected behavior occurs:
       a. Reproduce the issue
       b. Form hypotheses
       c. Test hypotheses systematically
       d. Fix root cause, not symptoms

  6. **Simplify** (`/simplify`)
     - Review all changed code for reuse, quality, and efficiency
     - Fix any issues found

  7. **Verify Before Claiming Done** (`/superpowers:verification-before-completion`)
     - Run ALL tests and verification commands
     - Confirm output with evidence — no assumptions
     - Never say "done" without proof

  8. **Request Code Review** (`/superpowers:requesting-code-review`)
     - Review work against original requirements
     - Check for missed edge cases, security issues, quality

  9. **Finish the Branch** (`/superpowers:finishing-a-development-branch`)
     - Present options: merge, PR, or cleanup
     - Follow my preference for integration

  Throughout this process:
  - Ask before assuming
  - User instructions override skill defaults
  - Evidence before assertions
  - Simple solutions over clever ones

  ---
  Condensed Version (Copy-Paste Ready)

  Implement [TASK]. Use the full Superpowers workflow:
  brainstorm → plan → worktree → TDD + execute → debug if needed →
  simplify → verify with evidence → code review → finish branch.
  Ask me questions at each checkpoint before proceeding.

  ---
  When to Skip Steps

  ┌──────────────────────────────────┬───────────────────────────────┐
  │            Situation             │             Skip              │
  ├──────────────────────────────────┼───────────────────────────────┤
  │ Tiny bug fix                     │ Brainstorm, plan, worktree    │
  ├──────────────────────────────────┼───────────────────────────────┤
  │ Well-defined spec already exists │ Brainstorm                    │
  ├──────────────────────────────────┼───────────────────────────────┤
  │ Already on a feature branch      │ Worktree setup                │
  ├──────────────────────────────────┼───────────────────────────────┤
  │ Single-file change               │ Parallel agents               │
  ├──────────────────────────────────┼───────────────────────────────┤
  │ No tests in project              │ TDD (but suggest adding them) │
  └──────────────────────────────────┴───────────────────────────────┘