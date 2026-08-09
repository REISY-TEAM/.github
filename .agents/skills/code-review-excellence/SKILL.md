---
name: code-review-excellence
description: REISY organization code review and security auditing standards.
---

# Code Review Excellence Skill

## Rules & Checklists
1. Check for complete PR contract headings (`## What`, `## Why`, `## How tested`, `## Risk / rollback`, `## Screenshots / artifacts`).
2. Verify that `.feature` files exist for `feature/` or `fix/` branches.
3. Ensure no hardcoded tokens (`ghp_`, `figd_`), credentials, or SSH keys are in the diff.
4. Verify unit tests exist for all new code logic.
