---
description: Create a pull request with auto-generated description
allowed-tools: Bash(git:*), Bash(gh:*)
---

## Context

Current branch:
!`git branch --show-current`

Commits in this branch:
!`git log main..HEAD --oneline`

Changed files:
!`git diff main --stat`

## Task

1. Push the current branch to origin
2. Create a PR using `gh pr create` with:
   - Clear title summarizing the changes
   - Description with:
     - Summary of what changed
     - Why the change was made
     - How to test it
