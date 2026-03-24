# Superpowers Prompts

> Ready-to-use prompts for common development tasks using [[Superpowers Overview|Superpowers]]. Copy, customize the `[BRACKETED]` sections, and paste.

---

## Full Workflow Prompt

The all-in-one prompt that invokes the complete [[Superpowers Workflow]].

```
Implement [TASK DESCRIPTION].

Use the full Superpowers workflow:
brainstorm → plan → worktree → TDD + execute → debug if needed →
simplify → verify with evidence → code review → finish branch.

Ask me questions at each checkpoint before proceeding.
```

---

## Feature Development

### New Feature (Full Process)

```
I need to build [FEATURE DESCRIPTION].

Here's what I know so far:
- [REQUIREMENT 1]
- [REQUIREMENT 2]
- [CONSTRAINT OR CONTEXT]

Start with brainstorming to refine the design with me, then follow
the full Superpowers workflow through to a finished branch.
```

### Add Feature to Existing Module

```
I want to add [FEATURE] to [MODULE/FILE].

Current behavior: [WHAT IT DOES NOW]
Desired behavior: [WHAT IT SHOULD DO]

Brainstorm the approach, then plan and execute with TDD.
Keep changes minimal and focused on this module.
```

---

## Bug Fixing

### Systematic Bug Fix

```
There's a bug: [DESCRIBE THE BUG].

Steps to reproduce:
1. [STEP 1]
2. [STEP 2]
3. [STEP 3]

Expected: [EXPECTED BEHAVIOR]
Actual: [ACTUAL BEHAVIOR]

Use systematic-debugging to find and fix the root cause.
Write a regression test before applying the fix.
```

### Production Incident

```
We have a production issue: [DESCRIBE INCIDENT].

Symptoms: [WHAT'S HAPPENING]
Impact: [WHO/WHAT IS AFFECTED]
When it started: [TIMELINE]

Use systematic-debugging. Prioritize understanding the root cause
before attempting any fix. Show evidence at each step.
```

---

## Refactoring

### Code Refactoring

```
I need to refactor [FILE/MODULE/COMPONENT].

Problems with current code:
- [ISSUE 1]
- [ISSUE 2]

Goals:
- [GOAL 1]
- [GOAL 2]

Plan the refactoring in small, safe steps. Every step must keep
tests green. Use a worktree so we can abort cleanly if needed.
```

### Extract and Restructure

```
I want to extract [FUNCTIONALITY] from [CURRENT LOCATION] into
[NEW LOCATION/MODULE].

Reason: [WHY THIS RESTRUCTURING IS NEEDED]

Plan this carefully — identify all callers and dependencies first.
Each step should be a working commit with passing tests.
```

---

## Testing

### Add Test Coverage

```
[FILE/MODULE] has insufficient test coverage.

Key behaviors to test:
- [BEHAVIOR 1]
- [BEHAVIOR 2]
- [EDGE CASE]

Write tests using TDD methodology. Focus on behavior, not
implementation details. No mocking unless absolutely necessary.
```

### Fix Flaky Tests

```
These tests are flaky: [TEST NAMES/FILES].

They fail approximately [FREQUENCY] of the time.
Suspected cause: [YOUR HYPOTHESIS, IF ANY]

Use systematic-debugging to identify the root cause of the
flakiness, then fix it. Verify the fix by running the tests
multiple times.
```

---

## Code Review

### Review a Branch

```
Review the changes on branch [BRANCH NAME] against [BASE BRANCH].

Focus on:
- Correctness and edge cases
- Test coverage
- Security implications
- Code clarity and maintainability

Use the requesting-code-review skill. Report issues by severity.
```

### Review Before Merge

```
I'm about to merge [BRANCH/PR]. Do a final review:

1. Run all tests and verify they pass
2. Check for any TODO/FIXME/HACK left behind
3. Verify the changes match the original requirements: [REQUIREMENTS]
4. Flag anything that concerns you

Use verification-before-completion. Show evidence, not assertions.
```

---

## Planning & Design

### Architecture Discussion

```
I'm considering [ARCHITECTURAL CHANGE/DECISION].

Context:
- [CURRENT STATE]
- [CONSTRAINTS]
- [GOALS]

Let's brainstorm. Explore the trade-offs with me — don't just
pick an approach. I want to understand the options before deciding.
```

### Sprint Planning Breakdown

```
I need to break down this work into implementable tasks:

[FEATURE/EPIC DESCRIPTION]

Acceptance criteria:
- [CRITERION 1]
- [CRITERION 2]

Use writing-plans to create a detailed plan with tasks that are
2-5 minutes each. Include file paths, verification steps, and
dependencies between tasks.
```

---

## Quick Operations

### Quick Fix (Skip Brainstorm/Plan)

```
Quick fix: [DESCRIBE THE CHANGE].

This is small and well-defined — skip brainstorming and planning.
Write a test, make the fix, verify, and commit.
```

### Explore and Explain

```
I need to understand how [COMPONENT/FEATURE] works.

Walk me through:
- The entry points
- The main code paths
- How data flows through the system
- Any non-obvious behavior or gotchas

Don't change any code. Just explain.
```

### Parallel Task Execution

```
I need these independent changes done:

1. [TASK 1]
2. [TASK 2]
3. [TASK 3]

These are independent — use dispatching-parallel-agents to run
them concurrently. Each task should follow TDD and be verified
independently before completion.
```

---

## Tips for Writing Effective Prompts

1. **Be specific about what you want** - "Add pagination to the users API" beats "improve the API"
2. **State constraints upfront** - Performance requirements, backward compatibility, etc.
3. **Provide reproduction steps for bugs** - The more detail, the faster the fix
4. **Say what to skip** - If you know the design, say "skip brainstorming"
5. **Mention checkpoints** - "Ask me before executing" keeps you in the loop
6. **Reference the skill directly** - When you want a specific behavior, name the skill

---

## Related Notes

- [[Superpowers Overview]] - Installation, skills reference, and philosophy
- [[Superpowers Workflow]] - The end-to-end development workflow
