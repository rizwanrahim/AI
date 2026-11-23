---
name: cherry-pick-pr
description: Cherry-picks only the actual changes of a PR into the current branch. Use when the user gives a PR number or URL and wants its changes copied here.
---

# Cherry-Pick PR

Copy only the PR's own changes into the current branch. Skip merge commits and unrelated history.

## Steps

1. Get the PR number from the user's message or URL.
2. Run `git status`. If the working tree is dirty, stop and ask the user to commit or stash.
3. Fetch the PR without creating a branch: `git fetch origin pull/{number}/head`
4. List only the PR's own commits: `git log --no-merges --reverse --format=%H origin/{base}..FETCH_HEAD` where `{base}` is the PR's target branch.
5. Cherry-pick them in order onto the current branch: `git cherry-pick {sha1} {sha2} ...`
6. If the PR was squash-merged, cherry-pick the single squash commit from the base branch instead.
7. Report which commits were applied.

## Conflicts

- Resolve only conflicts in files the PR touched. Keep both sides' intent.
- If a conflict is unclear, stop and ask the user. Never guess.
- Use `git cherry-pick --abort` to roll back if the user asks.

## Rules

- Stay on the current branch. Never switch, create, or delete branches.
- Never cherry-pick merge commits or commits that came from merging the base branch into the PR.
- Don't push, amend, or rebase unless asked.
- Don't change anything outside the PR's diff.
