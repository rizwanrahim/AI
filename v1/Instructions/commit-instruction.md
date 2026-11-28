# Commit Message Instructions

Follow these rules strictly when generating a commit message:

## Format

<prefix>: <short description>


- **Single line only.** No multi-line messages, no bullet points, no body/footer.
- Keep the description short and clear — ideally under 72 characters total.
- **Use smallcase (lowercase) for everything** — prefix and description — except proper nouns, file names, class names, or acronyms (e.g., `spread.ts`, `API`, `JSON`).
- No trailing period.

## Prefixes

Choose the prefix that best matches the *intent* of the change (always lowercase):

| Prefix    | Use when...                                              |
|-----------|-----------------------------------------------------------|
| `add`     | Introducing new functionality, files, or features          |
| `update`  | Modifying existing functionality or content without fixing a bug |
| `fixed`   | Resolving a bug, error, or unintended behavior              |
| `delete`  | Removing code, files, or features                           |
| `refactor`| Restructuring code without changing external behavior      |
| `docs`    | Documentation-only changes                                  |
| `style`   | Formatting, whitespace, or styling changes (no logic change)|
| `test`    | Adding or updating tests                                     |
| `chore`   | Maintenance tasks (configs, dependencies, tooling)          |

## Description Guidance

- Explain **what** changed and, briefly, **why**, if relevant.
- Reference the affected file or module when it adds clarity (e.g., `spread.ts`).
- Avoid vague messages like "fix bug" or "update code" — be specific.
- Keep everything lowercase.

## Examples

- `fixed: the null reference error in spread.ts file`
- `add: dark mode toggle to settings panel`
- `update: validation logic in login form`
- `delete: unused helper functions from utils.ts`
- `refactor: simplify date formatting in invoice.ts`

## What to Avoid

- Do not generate multiple lines, paragraphs, or commit bodies.
- Do not capitalize the first letter of the description.
- Do not use vague prefixes like `fix` alone without a clear target.
- Do not include ticket numbers or issue references unless explicitly requested.
- Do not add trailing punctuation.
