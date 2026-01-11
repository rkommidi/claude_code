---
description: Stage all changes and create a commit with a generated message
allowed-tools: Bash(git add:*), Bash(git status:*), Bash(git diff:*), Bash(git commit:*)
---

## Context

Current changes:
!`git diff --stat`

Staged files:
!`git status --short`

## Task

1. Review the changes above
2. Stage all modified files with `git add -A`
3. Generate a concise commit message following conventional commits:
   - feat: new feature
   - fix: bug fix
   - refactor: code restructuring
   - docs: documentation
   - test: adding tests
4. Create the commit
