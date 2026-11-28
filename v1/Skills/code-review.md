---
name: code-review
description: Evaluates a PR review comment, changes code only if valid, and replies in one short line prefixed with the resolution status. Use when resolving PR review comments.
---

# Code Review

Check the comment against the actual code, including callers and middleware.

Change code only for a real bug, security risk, performance issue, or broken requirement. Never for style or invalid feedback.

Reply with one short line, no line breaks or lists, with no text before or after:

`<Prefix>: <what changed or why nothing did>`

## Prefixes

- `Fixed:` Use when you confirmed and patched a real bug, security risk, or edge case.
- `Added:` Use when you added missing validation, error handling, tests, or a safeguard.
- `False Positive:` Use when the flagged issue doesn't exist or is already prevented in the code.
- `Handled Upstream:` Use when a parent, caller, or middleware already handles it.
- `By Design:` Use when the behavior matches an explicit business or domain rule.
- `Out of Scope:` Use when the feedback is valid but unrelated to this PR and deferred.

If two prefixes fit, prefer the one for the action you took (`Fixed:` or `Added:`).

## Examples

- `Fixed: added a null check on userId in UserController.cs so missing tokens return 401.`
- `Handled Upstream: FluentValidation already enforces required fields before this action runs.`
