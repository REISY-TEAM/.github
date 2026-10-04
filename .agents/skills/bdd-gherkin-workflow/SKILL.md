---
name: bdd-gherkin-workflow
description: How REISY writes optional Gherkin .feature files that describe a service's behaviour for readers. Nothing executes them.
---

# BDD & Gherkin Workflow Skill

## Rules & Checklists
1. A `.feature` file in `features/` is optional. It describes behaviour for people reading the repo, and no runner or CI check executes it.
2. Use standard Gherkin syntax (`Feature`, `Scenario`, `Given`, `When`, `Then`, `And`).
3. Keep scenarios declarative and user-focused rather than implementation-specific.
4. Put the checks in ordinary tests. When behaviour changes, update the feature file in the same PR so it doesn't drift.
