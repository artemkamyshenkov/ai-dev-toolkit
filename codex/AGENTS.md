# Personal Codex Rules

## Workflow

- Before editing code, read relevant project instructions (`AGENTS.md`,
  `.ai/AGENTS.md`, `.ai/rules/*`, and `CLAUDE.md`) and explore the affected code.
- For non-trivial changes, briefly explain the current behavior,
  scope, and proposed plan, then obtain approval once.
- If the user has already approved the plan, proceed with implementation,
  relevant checks, and fixes within that scope without asking again.
- Ask again only when new information requires a material change to the
  approved scope, externally visible behavior, compatibility, or risk.
  Routine implementation choices and changes to shared modules within
  the approved scope do not require additional approval.
- Follow existing patterns and abstractions, keep changes focused, and avoid
  unrelated refactoring. Preserve backward compatibility unless requested otherwise.
- After implementation, run relevant tests, linting, or type checks and review
  the diff for correctness and regressions.
- Summarize changes, verification results, and any material risks or assumptions.

## Communication

- Clarify ambiguous requirements and explain important design trade-offs.
- Explain significant side effects before implementation.

## Superpowers

Use Superpowers skills only when I explicitly request Superpowers
or name a specific Superpowers skill.

Do not activate using-superpowers automatically at conversation start.
A task matching a Superpowers skill description is not sufficient.

Requesting one skill authorizes that skill only. Do not expand it into
the full Superpowers workflow unless I explicitly request that workflow.

## Corporate Resources: MCP-First Routing

Use the corresponding corporate MCP whenever the user provides or references
one of these URLs:

- `https://kibana.logs.tutu.ru/app/` and its descendants: use `observability-mcp`.
- `https://dom.tutu.ru/pages` and its descendants: use `confluence-mcp`.
- `https://hq.tutu.ru/browse` and its descendants: use `jira-mcp`.
- `https://stash.tutu.ru/projects` and its descendants: use `bitbucket-mcp`.

For these corporate resources:

1. Use the mapped MCP before answering or asking the user to provide the
   resource contents.
2. Do not use browser automation, web search, `curl`, or direct browser login
   to read the resource when the mapped MCP can access it.
3. A referenced URL authorizes read-only retrieval through the mapped MCP. Do
   not create, edit, comment, transition, merge, or otherwise mutate corporate
   data unless the user explicitly requests that action.
4. Follow cross-links through the corresponding MCP. For example, resolve a
   Jira link from Confluence with `jira-mcp`, and a Bitbucket link from Jira
   with `bitbucket-mcp`.
5. If authorization is missing or expired, first inspect the mapped MCP's
   available authentication or connection guidance and attempt its supported,
   non-destructive authentication or reconnection flow. An MCP-provided auth
   flow may open a browser when required, but do not open the corporate
   resource URL itself as an authentication workaround.
6. Never invent credentials, expose stored tokens, or ask the user to paste a
   secret into chat. If MCP authentication requires user interaction, fails,
   or cannot be completed with the available tools, report the exact blocker
   and tell the user what action is required.
7. If the mapped MCP is unavailable, say so explicitly instead of silently
   falling back to another access method.

