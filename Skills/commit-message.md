---
name: commit-message
description: Generates concise, single-paragraph Git commit messages with standardized past-tense action prefixes. Use when asked to write, draft, or format a commit message for code changes.
---

# Commit Message Rules

Generate a Git commit message summarizing the staged or provided code changes by strictly adhering to the following constraints:

1. **Format:** Output ONLY a single line or a single continuous paragraph.
2. **No Formatting Breaks:** Do NOT use line breaks, newlines, bullet points, numbered lists, or markdown headers inside the message.
3. **Mandatory Prefix:** Begin the message with a lowercase past-tense action prefix from the allowed list below, followed by a colon and a single space (`<prefix>: <summary>`).
4. **Clarity & Brevity:** Keep the description direct, specific, and focused on *what* changed and *why*. Do not include conversational filler before or after the commit message.

## Allowed Prefixes

Use the most accurate past-tense verb for the primary change:

- `added:` — new files, features, components, endpoints, or tests
- `updated:` — enhancements, modifications, or configuration changes to existing behavior
- `fixed:` — bug fixes, error handling, or edge-case corrections
- `refactored:` — code restructuring without changing external behavior
- `resolved:` — merge conflicts, review comments, or tracked issue resolutions
- `removed:` — deletion of unused files, dead code, or dependencies

## Examples

- `added: style.css file to align the main container in the center.`
- `fixed: null reference exception in user authentication middleware when token header is missing.`
- `refactored: SQL query builder logic into a dedicated repository helper and updated unit tests to match the new signature.`
- `resolved: PR review feedback by adding input validation on the payload DTO and handling timeout errors.`
