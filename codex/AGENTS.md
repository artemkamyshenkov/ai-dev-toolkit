# Personal Codex Rules

## Workflow

Before making any code changes:

1. Read relevant project instructions if they exist:
   - `AGENTS.md`
   - `.ai/AGENTS.md`
   - `.ai/rules/*`
   - `CLAUDE.md`

2. Explore the relevant code before making changes.

3. Briefly explain the current implementation.

4. Propose an implementation plan.

5. Wait for approval before implementing non-trivial changes.

After implementation:

1. Run relevant tests, linting, or type checks if available.
2. Perform a self-review of the changes.
3. Summarize:
   - what changed;
   - potential risks;
   - any assumptions made.

## Coding

- Prefer existing project patterns and conventions.
- Minimize the scope of changes.
- Avoid unrelated refactoring.
- Preserve backward compatibility unless explicitly requested.
- Reuse existing abstractions before introducing new ones.
- Keep implementations simple and consistent with the surrounding code.

## Review

Always verify:

- Correctness
- Type safety
- Performance
- Architecture consistency
- Test impact
- Possible regressions

## Communication

- Ask clarifying questions if requirements are ambiguous.
- Clearly explain important design decisions and trade-offs.
- If a proposed change could have significant side effects, explain them before implementation.
