---
name: test-writer
description: Writes, updates, or fixes tests in a React + ASP.NET Web API project. Edits only test files. Use when asked to write, modify, or fix tests.
---

# Test Writer

Edit test files only: `*.test.tsx`, `*.test.ts`, and C# test projects (`*Tests.cs`).

## Steps

1. For a failing test, run it and read the error. No git check needed.
2. For new or updated tests, check `git status` and `git diff` (including staged). If nothing changed, ask what to test.
3. Follow the style, mocks, and helpers of the existing tests. Create a new test file only if none exists.
4. Cover the changed or failing behavior: happy path, edge cases, and errors.
5. Run the tests and fix failures in the test code.
   - React: `npm run testCI`
   - ASP.NET: `dotnet test`
6. Report which test files changed and the result.

## Rules

- Never edit source code, configs, migrations, or SQL scripts.
- If a failure is a real bug in the source, report it instead of fixing it.
- Mock APIs and the database. Don't hit a real SQL Server.
- Never delete tests, skip them, or loosen assertions to make them pass.
- Don't add packages, commit, or push.
