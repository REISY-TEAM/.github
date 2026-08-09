# REISY-TEAM Agent Directives & AI/CD Specification

Welcome, Agent. This repository is part of the **REISY-TEAM** organization and follows strict AI-Driven Continuous Development (AI/CD) standards.

---

## 1. Non-Negotiable Governance Rules

1. **Branch Naming:** All work must occur on branches starting with:
   - `feature/`
   - `fix/`
   - `refactor/`
   - `chore/`
   - `docs/`
   - `analysis/`
   *Never push directly to `main`.*

2. **BDD Specification Requirement:**
   - Every `feature/` or `fix/` branch **MUST** include or update at least one `.feature` Gherkin spec file inside `features/`.
   - PRs lacking `.feature` updates will automatically fail CI.

3. **PR Description Contract:**
   - Every PR body **MUST** contain these exact sections:
     - `## What`
     - `## Why`
     - `## How tested`
     - `## Risk / rollback`
     - `## Screenshots / artifacts`
   - If changed lines > 400 or changed files > 15, you **MUST** fill out `## Large PR justification`.

4. **Secrets & Security:**
   - Never commit private keys, API tokens (`ghp_`, `figd_`), passwords, or raw customer data.

---

## 2. Verification & Fast-Lane Loop

Before opening a PR or claiming work is complete, you MUST run the local verification suite:

* **React Native Repositories:**
  ```bash
  npm test
  npx prettier --check .
  ```
* **Java Repositories:**
  ```bash
  mvn clean test
  ./mvnw spotless:check
  ```
* **Python Repositories:**
  ```bash
  uv run pytest -m "not slow"
  uv run ruff check .
  ```

---

## 3. Skill & Pattern Hierarchy

Agents operating in REISY-TEAM repositories should load and apply the following procedural skills:

| Domain | Skill Name | Usage Trigger |
| :--- | :--- | :--- |
| **Governance & PRs** | `code-review-excellence` | Reviewing PRs, security auditing, or checking diffs |
| **BDD & Testing** | `bdd-gherkin-workflow` | Writing or updating `.feature` scenario files |
| **CI/CD & Pipelines** | `deployment-pipeline-design` | Modifying GitHub Actions or pre-commit hooks |
| **Python Stack** | `async-python-patterns` | Writing Python async code, FastAPI endpoints, or data processing |
| **React Native Stack** | `react-native-navigation` | Building mobile components, navigation, or state management |
| **Java Stack** | `spring-boot-architecture` | Building Spring Boot microservices, JPA entities, or REST APIs |

---

## 4. Heavy & Advanced Workflows

Heavy checks (mutation testing, slow-lane regression, performance benchmarks) do **NOT** run automatically on PRs. Execute them on demand using:

```bash
# Pre-commit manual stage
pre-commit run --hook-stage manual --all-files

# GitHub Actions manual execution
gh workflow run ci-mutation-testing.yml --ref main
```
