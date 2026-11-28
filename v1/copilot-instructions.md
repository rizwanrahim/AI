# Project Instructions

## Testing
- Do not run or fix tests unless explicitly asked.

## Scope
- Only touch the file/function mentioned in the request. No unrelated refactors, renames, or formatting.
- If a request is ambiguous, ask before assuming scope.

## Build / Lint (workflow convenience, not for every change)
- Default: don't run build/lint/format.
- If a .cs file is touched → run build.
- If a React file is touched (src/components/**, src/pages/**) → run lint + build.
- On failure: fix only errors caused by this change, re-run once to confirm. If unclear/unrelated, stop and report instead of guessing.

## Response Style (output token savings)
- No preambles ("Sure, I can help...").
- No restating the request or the code just written.
- No step-by-step explanation of changes — one line max, e.g. "Done — fixed null check in auth.ts".
- Full explanation only if I ask "explain" or "why".
