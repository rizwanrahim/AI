# Project Instructions

## Testing
- Do NOT run or fix test cases unless I explicitly ask for it.
- When fixing a bug, only touch the code needed for that fix.

## Scope of changes
- Only modify the specific file/function/feature mentioned in my request.
- Don't refactor, reformat, or rename things unless asked.

## Build / Lint
- Don't auto-run build, lint, or format commands by default.
- EXCEPTION: If any .cs (C#) file is created or modified, automatically run the build after the change.
- EXCEPTION: If any React file (.jsx, .tsx, .js, .ts inside components/ or similar) is created or modified, automatically run both lint and build check after the change.
- For all other file types (e.g. .py, .md, .json, config files), do NOT run build/lint unless I explicitly ask.

## Response Style
- After completing a task, do NOT explain what you did in detail.
- Just reply with a short confirmation like "Done" or "Task completed" + filename(s) changed, unless I ask for an explanation.
- Do NOT repeat/restate the code you wrote or the request I gave you.
- Do NOT summarize changes line-by-line — one short sentence max.
- Only give a detailed explanation if I explicitly ask "explain" or "why".
- Skip preambles like "Sure, I can help with that" or "Here's what I'll do" — just do the task.

## Communication
- If my request is ambiguous, ask before assuming scope.
