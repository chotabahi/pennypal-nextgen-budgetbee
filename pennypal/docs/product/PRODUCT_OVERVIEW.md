# Product Overview

> **Authority:** The PennyPal SRS is the sole authority for product definition. This document transcribes the SRS's product-level statements.

This document defines **what PennyPal is, who uses it, what problem it solves, and why it exists**. Every product-level statement is traced to an SRS section.

---

## 1. What is PennyPal?

PennyPal is a **multi-platform personal finance application aimed at students**. `SRS Requirement` (Project scope)

The SRS specifies that PennyPal must include the following feature areas. Each tag is `SRS Requirement` unless noted:

1. Authentication
2. Dashboard
3. Income and expenses
4. Expense categories
5. Transaction history
6. Budgets
7. Savings goals
8. Learning content
9. Feedback
10. Contact support
11. AI chatbot (basic financial guidance; **supporting aid only, not a substitute**)
12. Notifications
13. Reports
14. Offline expense entry and synchronization

The SRS also specifies the following project-level requirements:

- User roles: Student and Admin. `SRS Requirement`
- Database planning (with reference entities). `SRS Requirement`
- Security and privacy. `SRS Requirement`
- Cross-platform compatibility. `SRS Requirement`
- Testing. `SRS Requirement`
- Installation. `SRS Requirement`
- Responsible AI usage (AI is supporting aid; team must demonstrate meaningful understanding and modification). `SRS Requirement`

### 1.1 Project name

**PennyPal** — `SRS Requirement` (per SRS document title).

### 1.2 Project category

Multi-Platform App Computing. `SRS Requirement`

### 1.3 Project type

The SRS specifies this as a Multi-Platform App Computing project. The exact academic / competition context (course, competition) is `Assumption` pending team verification.

---

## 2. Who uses PennyPal?

### 2.1 User classes / actors

The SRS specifies two user roles. Both are SRS-explicit (not assumed):

| User role | Tag | SRS section |
|-----------|-----|-------------|
| **Student** | `SRS Requirement` | User roles |
| **Admin** | `SRS Requirement` | User roles |

The SRS describes functionality for both Student and Admin roles. Specific Admin capabilities (e.g., managing learning content, reviewing feedback, handling support queries, managing users) are `SRS Requirement` where the SRS describes them; specific Admin screens are `Derived Design`.

### 2.2 Primary vs secondary users

The SRS does not explicitly distinguish primary vs secondary users. `Assumption` — pending team verification. The team's working assumption is that **Student** is the primary user (the app is aimed at students per the project scope) and **Admin** is a secondary user (manages content, users, or system configuration).

---

## 3. What problem does PennyPal solve?

### 3.1 Problem statement

The SRS specifies that PennyPal is a multi-platform personal finance application for students. `SRS Requirement` (Project scope)

The SRS does not provide an explicit "problem statement" section. The problem PennyPal solves is therefore inferred from its feature set: **students need a tool to track income and expenses, set budgets, work toward savings goals, learn financial literacy, and get AI-assisted basic financial guidance — all working offline so they can use it anywhere.** `Assumption` — pending team verification against the SRS.

### 3.2 Project objectives

**`SRS Requirement`** — the SRS's project objectives are inferred from its feature list. The objectives are:

- Provide students with a tool to record and manage income and expenses.
- Allow students to categorize expenses for better insight.
- Allow students to view transaction history.
- Allow students to set and track budgets.
- Allow students to set and track savings goals.
- Provide financial-literacy learning content.
- Provide an AI chatbot for **basic financial guidance as supporting aid** (not a substitute for professional advice).
- Allow offline expense entry with synchronization when online.
- Provide reports for spending analysis.
- Provide notifications for relevant events.
- Allow users to submit feedback and contact support.
- Provide an Admin role for management.
- Ensure security and privacy of user data.
- Ensure cross-platform compatibility.

### 3.3 Target outcomes

**`TBD`** — the SRS does not explicitly enumerate target outcomes. The team should derive them from the project objectives above.

---

## 4. Scope

### 4.1 In scope

The following feature areas are in scope per the SRS (`SRS Requirement`):

| Feature area | SRS section |
|--------------|-------------|
| Authentication | Authentication |
| User roles (Student, Admin) | User roles |
| Dashboard | Dashboard |
| Income and expenses | Income and expenses |
| Expense categories | Expense categories |
| Transaction history | Transaction history |
| Budgets | Budgets |
| Savings goals | Savings goals |
| Learning content | Learning content |
| Feedback | Feedback |
| Contact support | Contact support |
| AI chatbot (basic guidance; supporting aid) | AI chatbot |
| Notifications | Notifications |
| Reports | Reports |
| Offline expense entry and synchronization | Offline + sync |

The SRS also specifies these project-level requirements as in scope (`SRS Requirement`):

| Requirement | SRS section |
|--------------|-------------|
| Database planning (with reference entities) | Database planning |
| Security and privacy | Security and privacy |
| Cross-platform compatibility | Cross-platform compatibility |
| Testing | Testing |
| Installation | Installation |
| Responsible AI usage | Responsible AI usage |

### 4.2 Out of scope

The SRS does not enumerate explicit out-of-scope items. Inferred out-of-scope items are documented in `../LIMITATIONS.md` → *SRS Scope Limitations* with `Assumption` tags pending team verification.

---

## 5. Product Principles

> **Note:** Product principles are team decisions, not SRS-derived. Tag each as `Team Technical Decision`.

| Principle | Tag | Rationale |
|-----------|-----|-----------|
| `[TBD — team to decide on Day 1]` | `Team Technical Decision` | `[TBD]` |

Candidate principles (pending team decision):
- Offline-first (supports the SRS-mandated offline expense entry).
- Insight over data.
- Every number is sourced (especially for the AI chatbot).
- Honest about scope.
- Speed is a feature.

---

## 6. High-Level Feature Inventory

The SRS-mandated features are listed below. The count of **14** user-facing features is derived by counting SRS-mandated capabilities (excluding cross-cutting requirements like security, database planning, cross-platform, testing, installation, and responsible AI usage, which are project-level requirements rather than features).

| Feature ID | Feature name | Tag | SRS section |
|------------|--------------|-----|-------------|
| F-01 | Authentication | `SRS Requirement` | Authentication |
| F-02 | Dashboard | `SRS Requirement` | Dashboard |
| F-03 | Income and expenses | `SRS Requirement` | Income and expenses |
| F-04 | Expense categories | `SRS Requirement` | Expense categories |
| F-05 | Transaction history | `SRS Requirement` | Transaction history |
| F-06 | Budgets | `SRS Requirement` | Budgets |
| F-07 | Savings goals | `SRS Requirement` | Savings goals |
| F-08 | Learning content | `SRS Requirement` | Learning content |
| F-09 | Feedback | `SRS Requirement` | Feedback |
| F-10 | Contact support | `SRS Requirement` | Contact support |
| F-11 | AI chatbot (basic guidance; supporting aid) | `SRS Requirement` | AI chatbot |
| F-12 | Notifications | `SRS Requirement` | Notifications |
| F-13 | Reports | `SRS Requirement` | Reports |
| F-14 | Offline expense entry and synchronization | `SRS Requirement` | Offline + sync |

The exact priority (Must / Should / Could, or High / Medium / Low) for each feature is `TBD` pending team verification against the SRS.

### Cross-cutting requirements (not counted as features)

These SRS-mandated requirements apply across all features:

| Requirement | SRS section | Tag |
|--------------|-------------|-----|
| User roles (Student, Admin) | User roles | `SRS Requirement` |
| Security and privacy | Security and privacy | `SRS Requirement` |
| Database planning | Database planning | `SRS Requirement` |
| Cross-platform compatibility | Cross-platform compatibility | `SRS Requirement` |
| Testing | Testing | `SRS Requirement` |
| Installation | Installation | `SRS Requirement` |
| Responsible AI usage | Responsible AI usage | `SRS Requirement` |

---

## 7. Submission Deliverables (SRS-Mandated)

The SRS mandates the following deliverables as part of the submission (`SRS Requirement`):

| Deliverable | SRS section | Notes |
|-------------|-------------|-------|
| Credentials (demo/test) | Submission | Documented in `../viva/SUBMISSION_REQUIREMENTS.md`. |
| APK | Submission | Build process in `../process/DEPLOYMENT.md`. |
| Source code | Submission | Hosted in a Git repository. |
| README | Submission | The repository's README file. |
| MP4 demonstration video | Submission | Recorded demo of the application. |

---

## 8. Relationship to the Rest of the Documentation

| If you want to know... | Read this |
|------------------------|-----------|
| The full list of requirements, traced to the SRS | `REQUIREMENTS.md` |
| How each feature behaves in detail | `FEATURE_SPECIFICATIONS.md` |
| How requirements trace to features, derived designs, technical design, tests | `TRACEABILITY_MATRIX.md` |
| How the UI is structured | `../design/UI_UX_DESIGN.md` |
| How the system is architected | `../architecture/ARCHITECTURE.md` |
| Why each technical decision was made | `../adr/` |
| What assumptions were made | `../ASSUMPTIONS.md` |
| What is intentionally out of scope or not yet implemented | `../LIMITATIONS.md` |
| How the team operates | `../process/PROJECT_PLAN.md` (Team Project Plan) |

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending team verification of `Assumption` items
