# REISY organization governance

This repository contains the default community health files, contribution guidelines, pull request templates, and language-independent PR governance workflows for REISY repositories.

It is intentionally small. It defines the shared contribution contract for the organization. It does not contain Python, JavaScript, TypeScript, Docker, deployment, or product-specific CI implementation.

## What belongs here

- Organization-wide contribution guidelines.
- Pull request template and PR quality expectations.
- Security, support, and code of conduct documents.
- Reusable PR metadata validation that is not tied to one programming language.
- Workflow templates that product repositories can opt into.

## What does not belong here

- Python linting, typing, packaging, or testing logic.
- JavaScript or TypeScript linting, testing, or build logic.
- Docker image build and deploy logic.
- Application-specific architecture decisions.
- Secrets, API keys, provider credentials, or production configuration.

Language-specific CI should live in separate reusable workflow repositories, for example:

```text
REISY-TEAM/ci-python
REISY-TEAM/ci-node
REISY-TEAM/ci-docker
REISY-TEAM/repo-template-base
```

Downstream repositories should keep thin workflow files that call those reusable workflows instead of copying large CI implementations.

## Recommended downstream structure

A normal REISY product repository should usually contain only small workflow caller files:

```text
.github/workflows/
  pr-contract.yml
  python-ci.yml
  node-ci.yml
  docker-ci.yml
```

The PR contract belongs to this governance layer because it checks repository-agnostic rules: PR title, PR body, checklist, branch name, and large PR justification.

## REISY engineering principles

REISY is a travel intelligence layer. Provider APIs should be accessed through controlled backend adapters, normalized data models, deduplication, scoring, and explanation layers. The AI layer should not call every provider API directly.

Core product rules:

- Normalize provider data before showing or scoring it.
- Preserve provider provenance, timestamps, terms, and identifiers.
- Deduplicate before ranking or explaining.
- Control API cost through caching, field masks, provider budgets, and shortlists.
- Do not build core travel inventory on scraping.
- Treat user preferences, location, dietary, mobility, passport, visa, and health-related data with care and data minimization.

## Repository owners

Governance files should be reviewed by maintainers before changes are merged. Update `CODEOWNERS` when the organization has a stable maintainer team slug.
