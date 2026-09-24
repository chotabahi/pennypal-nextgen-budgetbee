# Development Workflow

> **Authority:** Team decisions on engineering process. The SRS mandates testing (`SRS Requirement`) and installation (`SRS Requirement`); the workflow is `Team Technical Decision`.

This document defines how the team writes, reviews, and merges code.

---

## 1. Repository Setup

### 1.1 Repositories

**Tag:** `Team Technical Decision` — `TBD`.

| Repo | Contents | Visibility | Tag |
|------|----------|------------|-----|
| `[TBD]` | Source code (SRS-mandated deliverable). | `[TBD]` | `SRS Requirement` (source code); `Team Technical Decision` (repo structure) |

The SRS mandates that the submission includes source code. `SRS Requirement`

### 1.2 Branch protection

**Tag:** `Team Technical Decision` — `TBD`.

### 1.3 Branch naming

**Tag:** `Team Technical Decision` — `TBD`.

### 1.4 Commit conventions

**Tag:** `Team Technical Decision` — `TBD`.

### 1.5 PR template

**Tag:** `Team Technical Decision` — `TBD`.

---

## 2. Git Workflow

**Tag:** `Team Technical Decision` — `TBD`.

The team decides on trunk-based vs. GitFlow, rebase vs. merge, squash vs. merge commit.

---

## 3. Code Review

### 3.1 Reviewer assignment

**Tag:** `Team Technical Decision` — `TBD`.

### 3.2 Review checklist

**Tag:** `Team Technical Decision` — `TBD`.

### 3.3 Definition of Done

**Tag:** `Team Technical Decision` — `TBD`.

The SRS mandates testing; the definition of done must include tests passing. `SRS Requirement`

---

## 4. Coding Standards

### 4.1 Lint rules

**Tag:** `Team Technical Decision` — `TBD`.

### 4.2 Formatting

**Tag:** `Team Technical Decision` — `TBD` (typically `dart format` with default settings — pending ADR-001 framework decision).

### 4.3 Naming conventions

**Tag:** `Team Technical Decision` — `TBD`.

### 4.4 File organization

**Tag:** `Team Technical Decision` — `TBD` (depends on architectural style chosen in `ARCHITECTURE.md`).

### 4.5 Comment policy

**Tag:** `Team Technical Decision` — `TBD`.

---

## 5. CI/CD

### 5.1 Workflows

**Tag:** `Team Technical Decision` — `TBD`.

The SRS mandates testing; CI should run tests. `SRS Requirement`

### 5.2 Secrets

**Tag:** `Team Technical Decision` — `TBD`.

### 5.3 Failure handling

**Tag:** `Team Technical Decision` — `TBD`.

---

## 6. Dependency Management

**Tag:** `Team Technical Decision` — `TBD`.

Dependencies are decided via ADRs (state management: ADR-002; navigation: ADR-003; storage: ADR-004; HTTP: ADR-005; etc.). The SRS does not mandate specific technologies.

---

## 7. Local Development Setup

### 7.1 Prerequisites

**Tag:** `Team Technical Decision` — `TBD` (depends on ADRs).

### 7.2 First-time setup

**`TBD`** — pending ADR decisions.

### 7.3 Daily workflow

**`TBD`** — pending workflow decisions.

---

## 8. Logging & Debugging

**Tag:** `Team Technical Decision` — `TBD`.

The SRS mandates security and privacy; logs must not contain PII. `SRS Requirement`

---

## 9. Hotfix Process

**Tag:** `Team Technical Decision` — `TBD`.

---

## 10. Responsible AI Usage (SRS-mandated)

Per the SRS, AI is supporting aid rather than a substitute. The team must:
- Review and understand all AI-assisted code and documentation. `SRS Requirement`
- Demonstrate meaningful modification of AI-assisted work (not accept AI output verbatim). `SRS Requirement`
- Be able to explain the codebase during judging. `SRS Requirement`

---

## 11. What This Document Does NOT Cover

- **Team roles and daily schedule** → `TEAM_WORKFLOW.md`
- **Test strategy** → `TESTING.md`
- **Deployment details** → `DEPLOYMENT.md`
- **Project plan** → `PROJECT_PLAN.md` (Team Project Plan)

---

## Team Action: Filling In This File

1. Decide on each `Team Technical Decision` on Day 0 / Day 1.
2. Document the decision and rationale.
3. **Preserve the SRS AI restriction** — the team must review and understand all AI-assisted code.
4. Update the file status from `Audited` to `Team-Reviewed`.

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending team decisions on engineering process; SRS AI restriction preserved
