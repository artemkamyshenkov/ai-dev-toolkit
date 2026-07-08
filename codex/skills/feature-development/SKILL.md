---
name: feature-development
description: Use this skill when implementing a new feature, changing existing behavior, extending UI/backend logic, or modifying product functionality. The skill guides the agent through investigation, planning, implementation, verification, and summary.
---

---

# Feature Development Skill

## Goal

Implement features like a senior engineer: understand the existing system first, minimize risk, follow project conventions, and make focused changes.

This skill is not for code review only. Use it when code needs to be changed.

## Core principles

- Understand before changing.
- Prefer existing patterns over new abstractions.
- Keep changes minimal and task-focused.
- Avoid unrelated refactoring.
- Preserve backward compatibility unless explicitly requested.
- Make behavior changes explicit.
- Verify changes with tests, linting, or type checks when possible.
- Be honest about assumptions, uncertainty, and risks.

## Before implementation

1. Read relevant project instructions if they exist:
   - `AGENTS.md`
   - `.ai/AGENTS.md`
   - `.ai/rules/*`
   - `CLAUDE.md`

2. Explore the relevant code:
   - find the current implementation;
   - find similar features;
   - inspect nearby tests;
   - identify shared utilities, hooks, selectors, services, or helpers.

3. Explain the current behavior briefly.

4. Identify affected areas:
   - UI;
   - state management;
   - API/data layer;
   - types/contracts;
   - tests;
   - shared modules;
   - product-specific modules.

5. Propose a plan before making non-trivial changes.

6. Wait for approval before implementation if:
   - the change affects architecture;
   - the change touches shared modules;
   - the change may affect several product flows;
   - the task requirements are ambiguous;
   - the implementation requires choosing between multiple approaches.

## Implementation rules

When implementing:

- Follow the nearest existing code style.
- Reuse existing abstractions before creating new ones.
- Prefer small, readable changes.
- Avoid large rewrites.
- Avoid speculative generalization.
- Do not change public contracts unless required.
- Do not introduce new dependencies unless explicitly justified.
- Do not silently change behavior outside the requested scope.
- Keep naming consistent with the surrounding code.
- Update tests when behavior changes.
- Add tests for important edge cases when practical.

## React / TypeScript focus

For React and TypeScript projects, pay attention to:

- component responsibility boundaries;
- unnecessary local state;
- duplicated derived state;
- unstable object/function references;
- incorrect hook dependencies;
- unnecessary rerenders;
- excessive `useMemo` / `useCallback`;
- missing memoization where rerenders matter;
- weak types or unsafe `any`;
- changed props/contracts;
- accessibility;
- loading, empty, and error states.

Prefer derived values over duplicated state.

Prefer clear types over clever generic abstractions.

## Backend / Go focus

For Go or backend work, pay attention to:

- error handling;
- context propagation;
- package boundaries;
- simple interfaces;
- resource cleanup;
- goroutine leaks;
- request validation;
- database migrations;
- observability;
- table-driven tests where useful.

Prefer straightforward, idiomatic code over complex abstractions.

## Verification

After implementation:

1. Run the most relevant available checks:
   - tests;
   - lint;
   - typecheck;
   - build;
   - targeted package checks.

2. If checks cannot be run, explain why.

3. Perform a self-review:
   - correctness;
   - regressions;
   - type safety;
   - performance;
   - architecture consistency;
   - test coverage;
   - edge cases.

## Output format

Before implementation, respond with:

### Current implementation

Briefly explain how the relevant code works now.

### Plan

List the implementation steps.

### Risks / assumptions

Mention important risks, assumptions, or unclear requirements.

After implementation, respond with:

### Changed

Summarize what changed.

### Verification

List checks that were run and their results.

### Risks

Mention remaining risks or assumptions.

### Notes

Mention anything the user should know before committing.

## Rules

- Do not implement before understanding the existing code.
- Do not skip investigation unless the task is trivial.
- Do not produce broad refactors unless explicitly requested.
- Do not hide uncertainty.
- Do not claim tests passed if they were not run.
- If the requested change is risky, say so before changing code.
- If a smaller safe change is possible, prefer it.
