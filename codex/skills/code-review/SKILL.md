---
name: code-review
description: Use this skill to review code changes, diffs, pull requests, or recently modified files. Focus on correctness, regressions, type safety, performance, architecture, tests, and maintainability.
---

# Code Review Skill

## Goal

Review code like a senior engineer. Focus on issues that can cause bugs, regressions, poor maintainability, performance problems, or architectural violations.

## Before reviewing

1. Read relevant project instructions if they exist:
   - `AGENTS.md`
   - `.ai/AGENTS.md`
   - `.ai/rules/*`
   - `CLAUDE.md`

2. Inspect the changed files and surrounding code.

3. Understand the purpose of the change before commenting.

## Review checklist

Check for:

- correctness
- possible regressions
- type safety
- edge cases
- async/race-condition issues
- performance problems
- unnecessary rerenders
- accessibility issues
- architecture consistency
- test coverage impact
- backward compatibility
- unnecessary complexity
- unrelated refactoring

## React / TypeScript focus

For React and TypeScript code, pay special attention to:

- incorrect hook dependencies
- excessive local state
- duplicated derived state
- unstable object/function references
- unnecessary `useMemo` / `useCallback`
- missing memoization where rerenders matter
- unsafe `any`
- weak or misleading types
- props/contracts changed without need
- component responsibilities growing too much

## Go focus

For Go code, pay attention to:

- error handling
- context propagation
- package boundaries
- simple interfaces
- unnecessary abstractions
- goroutine leaks
- resource cleanup
- idiomatic naming
- table-driven tests where useful

## Output format

Group findings by severity:

### Critical

Issues that can break production, data flow, purchase flow, security, or major user behavior.

### Major

Likely bugs, regressions, architectural violations, missing tests, or performance problems.

### Minor

Readability, maintainability, naming, small simplifications.

### Positive

Mention strong decisions if relevant.

## Rules

- Do not rewrite the whole solution unless asked.
- Prefer precise comments tied to specific files or code fragments.
- Explain why each issue matters.
- Suggest a minimal fix when possible.
- If there are no serious issues, say so clearly.
