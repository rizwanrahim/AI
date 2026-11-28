---
name: o-planner
description: Creates an implementation plan for any development work (story, bug, task, feature, refactor, or a plain request) with copy-paste-ready Before/After code per file, explaining what changes and why, and saves it as a markdown file in the Project Plan folder at the workspace root. Use whenever the user asks to plan, scope, break down, or design a change, mentions an Azure DevOps ID (e.g. Story 12424), or says create a plan.
---

# Planner

## Steps

1. **Get the input.** If the user gave an Azure DevOps ID and an Azure DevOps tool is available, fetch it (title, description, acceptance criteria, repro steps). Otherwise use what the user typed. Never invent details.
2. **Read only what you need.** Find the closest existing example and follow its patterns. Open only files you will change or copy from. Copy current code for "Before" blocks from the actual files.
3. **Write the plan** using the format below, directly into the file. Do not draft it in chat first.
4. **Save it** to `Project Plan/<short-kebab-name>.md` in the workspace root (create the folder if missing). Name it after the change, not the ID. Example: "Story 12424 - Create end point to generate user list" becomes `get-user-end-point.md`.
5. **Reply with one line only:** `Plan saved: Project Plan/<file>.md`. No summary, no repeating the plan, no questions unless something blocks you. Do not change source code unless asked.

## Plan format

```
# <Title>

## Input
<Azure DevOps details if any (type, ID, description, acceptance criteria)>
<Everything the user told you, word for word>

## Approach
<2-4 sentences, plus any assumptions>

## Code Changes

### path/to/File.ext (Modified)
What: <what is changing, one line>
Why: <why, one line>
Before:
<exact existing lines with 3-5 lines of context>
After:
<replacement lines, ready to paste>

### path/to/NewFile.ext (New)
What: <what this file does>
Why: <why it is needed>
<full file content>

## Commands
<migrations, installs, config keys, or "None">

## Verification
<how to test it>
```

## Rules

- Input always comes first.
- Every file gets a What and a Why, kept to one line each.
- One section per file, in the order the changes should be applied.
- Code must be complete: include imports, registrations, and tests. No "..." inside changed code.
- Before blocks must match the source exactly.
- Be brief: no filler, no repeated explanations, show only changed lines plus context (not whole files) for modified files.
