---
name: code-review
description: Evaluates PR code review feedback, applies targeted code fixes only when genuinely required, and generates a single-paragraph reply prefixed with the resolution status. Use when resolving code review comments or auditing PR feedback.
---

# Code Review Rules

Evaluate the reported code review comment against the codebase and respond by strictly adhering to the following constraints:

- Change Only When Required: Modify code ONLY if the review comment identifies a genuine bug, security risk, performance issue, or broken requirement. Do NOT alter working code for subjective style preferences or invalid feedback.
- Mandatory Prefix: Begin the reply with an exact prefix from the allowed list below, followed by a colon and a single space (`<Prefix>: <explanation>`).
- Format: Output ONLY a single line or a single continuous paragraph.
- No Formatting Breaks: Do NOT use line breaks, newlines, bullet points, numbered lists, or markdown headers inside the reply.
- Clarity & Brevity: State clearly what was changed or why no code change was needed. Do not include conversational filler before or after the reply.

## Allowed Prefixes

Use the exact prefix matching the action taken:

- `Fixed:` — a valid bug, security risk, or edge case was confirmed and patched
- `Added:` — missing validation, error handling, test coverage, or safeguard was added as requested
- `False Positive:` — the flagged issue does not exist or is already prevented elsewhere in the code
- `Handled Upstream:` — validation, sanitization, or error handling already occurs in a parent component, middleware, or caller
- `By Design:` — the current behavior matches explicit business rules or domain requirements
- `Out of Scope:` — valid suggestion, but unrelated to the current story/PR and deferred to a separate task

## Examples

- `Fixed: added a null check on the userId claim in UserController.cs before parsing so missing tokens return a 401 Unauthorized response instead of throwing a NullReferenceException.`
- `Added: unit test coverage in OrderServiceTests.cs for empty cart submissions and discount boundary validation.`
- `False Positive: the SQL query already uses parameterized Dapper bindings via @OrderId, so it is protected against SQL injection and no code changes are needed.`
- `Handled Upstream: payload schema and required field checks are already enforced by the FluentValidation filter before reaching this controller action.`
- `By Design: soft-deleted records are intentionally excluded at the repository query layer to satisfy the audit retention requirement.`
- `Out of Scope: refactoring the shared grid column builder is a valid improvement, and it will be tracked separately to keep this bugfix PR minimal.`
