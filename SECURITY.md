# Security policy

REISY takes security and privacy seriously. Please report security issues privately and responsibly.

## Supported scope

This policy applies to active repositories in the `REISY-TEAM` organization unless a repository has a more specific security policy.

## Reporting a vulnerability

Do not open a public GitHub issue for a vulnerability.

Use one of these private channels instead:

1. GitHub private vulnerability reporting, if enabled for the affected repository.
2. A private message to the repository maintainers or organization owners.
3. A private security contact documented in the affected repository, if one exists.

Include as much detail as possible:

- Affected repository and branch or release.
- A clear description of the issue.
- Steps to reproduce, proof of concept, or affected endpoint.
- Potential impact.
- Suggested mitigation, if known.

## What not to share publicly

Do not post any of the following in issues, PRs, comments, screenshots, logs, or artifacts:

- API keys, OAuth tokens, passwords, cookies, session IDs, signing secrets, or private certificates.
- Provider credentials for travel APIs, maps APIs, payment systems, or partner dashboards.
- Customer data, production database exports, support logs, analytics exports, or private trip data.
- Passport, visa, health, dietary, exact location, or other sensitive personal information.
- Private commercial terms, unpublished provider pricing, or partner contracts.

## Maintainer response expectations

Maintainers should acknowledge valid private reports, assess impact, plan a fix, and coordinate disclosure timing when necessary.

Security fixes should be reviewed with extra care and should not expose exploit details in public PR text before mitigation is available.

## Dependency and secret hygiene

Repositories should use appropriate dependency checks, secret scanning, minimal permissions for GitHub Actions, and least-privilege provider credentials.

GitHub Actions workflows should not expose secrets to untrusted pull request code. Workflows using `pull_request_target` must not check out or execute untrusted code unless the risk is explicitly understood and controlled.
