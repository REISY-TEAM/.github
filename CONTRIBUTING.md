# Contributing to REISY repositories

Thank you for contributing to REISY. This document defines the default contribution rules for repositories in the REISY organization.

Individual repositories may add extra instructions when needed, but they should not weaken these shared rules.

## Contribution scope

Prefer small, focused changes. A good pull request should have one purpose and should be reviewable without requiring the reviewer to understand unrelated changes.

Large pull requests are allowed only when the work cannot be split safely. In that case, the PR description must include a clear large PR justification.

## Branch naming

Use one of these branch prefixes:

```text
feature/
fix/
analysis/
refactor/
chore/
docs/
```

Examples:

```text
feature/trip-scoring-v1
fix/provider-timeout-handling
analysis/hotel-api-comparison
refactor/search-orchestrator-cache
chore/update-ci-caller
docs/provider-integration-notes
```

## Pull request expectations

Every pull request should:

- Use the organization PR template.
- Explain what changed and why.
- Describe how the change was tested.
- Mention risks, rollback notes, skipped checks, generated artifacts, or external dependencies.
- Keep placeholder comments out of the final PR body.
- Have all required checklist boxes checked before review.
- Avoid self-merge unless the repository has an explicitly approved emergency process.

## Review expectations

Reviewers should check:

- The change matches the stated scope.
- The PR description is complete.
- Tests and validation are appropriate for the changed files.
- New behavior is understandable and maintainable.
- Secrets, private data, generated noise, and unrelated files are not included.

Authors should respond to review comments clearly and update the PR description when the scope changes.

## Testing and CI

Each repository should define its own language-specific validation through reusable workflows.

Recommended split:

```text
REISY-TEAM/.github       -> contribution and PR governance
REISY-TEAM/ci-python     -> Python lint, typecheck, tests, packaging
REISY-TEAM/ci-node       -> JavaScript/TypeScript lint, typecheck, tests, builds
REISY-TEAM/ci-docker     -> Docker build, smoke tests, image publishing
```

Do not put language-specific CI implementation into this governance repository.

## AI and agent-assisted contributions

AI-assisted contributions are welcome when they are transparent and reviewable.

Agent or AI-assisted PRs must:

- Keep the change small and scoped.
- Follow the same PR template and checklist rules as human PRs.
- State what was tested and what was not tested.
- Avoid claiming that checks passed unless they were actually run.
- Avoid modifying governance files, CI files, or security files unless the task explicitly requires it.
- Never include secrets, tokens, private user data, proprietary provider credentials, or raw production data.

## REISY product principles

REISY should act as a travel decision and intelligence layer, not as a thin wrapper around many raw provider APIs.

Provider integrations should usually follow this pattern:

```text
provider adapter -> normalized object -> deduplication -> scoring -> explanation
```

Important rules:

- The AI layer should not directly call all external APIs.
- Backend orchestration should control provider calls, cache usage, field selection, and rate limits.
- Store provider provenance and timestamps for offers, prices, policies, ratings, and photos.
- Use official APIs, partner feeds, or approved affiliate flows for core inventory.
- Respect provider terms for caching, attribution, display, photos, reviews, and data use.
- Apply GDPR and privacy-by-design principles to user preferences and sensitive travel data.

## Security and privacy

Do not open public issues or pull requests containing:

- API keys, tokens, passwords, cookies, or private credentials.
- Personal documents, passport data, visa data, health information, or precise private location data.
- Provider partner credentials, contracts, unpublished pricing, or private commercial terms.
- Production database dumps or customer data.

Report security issues privately according to `SECURITY.md`.
