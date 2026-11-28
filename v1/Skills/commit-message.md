---
name: commit-message
description: Writes a one-line Git commit message with a lowercase past-tense prefix. Use when asked to write or format a commit message.
---

# Commit Message

Summarize the changes as one line, no line breaks or lists, with no text before or after:

`<prefix>: <what changed and why>`

If a commit has several changes, pick the prefix for the main one.

## Prefixes

- `added:` Use when you create something new: files, features, endpoints, components, or tests.
- `updated:` Use when you change or improve something that already exists, including config changes.
- `fixed:` Use when you correct a bug, error, or edge case.
- `refactored:` Use when you restructure code and behavior stays the same.
- `resolved:` Use when you settle a merge conflict, address review comments, or close a tracked issue.
- `removed:` Use when you delete files, dead code, or dependencies.

## Example

`fixed: null reference in auth middleware when the token header is missing.`
