# PennyPal — Documentation System

> **Project:** PennyPal — Multi-Platform App Computing project
> **Authority:** The PennyPal Software Requirements Specification (SRS) is the primary and authoritative source. Statements in this documentation are classified by their relationship to the SRS.
> **Status:** Audited — pending team verification of `Assumption` and `TBD` items.

> **Important (per SRS):** AI is supporting aid rather than a substitute. The project must demonstrate meaningful understanding and modification of AI-assisted work. The team must be able to explain the architecture, requirements, design, and implementation during judging. AI-generated documentation is not automatically acceptable for final submission; the team must review and understand it. `SRS Requirement` (Responsible AI usage)

---

## What is PennyPal?

PennyPal is a multi-platform personal finance application aimed at students. `SRS Requirement` (Project scope)

The SRS specifies the following feature areas (each tag is `SRS Requirement` unless noted):

- **Project scope** — multi-platform personal finance application for students.
- **User roles** — Student and Admin. Both are SRS-explicit.
- **Authentication** — login/registration with role-based access.
- **Dashboard** — overview of the user's financial position.
- **Income and expenses** — record and manage income and expense entries.
- **Expense categories** — categorize expenses.
- **Transaction history** — view past transactions.
- **Budgets** — set and track budgets.
- **Savings goals** — set and track savings goals.
- **Learning content** — educational financial-literacy content for users.
- **Feedback** — users can submit feedback.
- **Contact support** — users can contact support.
- **AI chatbot** — an AI assistant that provides basic financial guidance. **Per SRS: supporting aid only, not a substitute; the team must demonstrate meaningful understanding and modification of AI-assisted work.**
- **Notifications** — push/in-app notifications.
- **Reports** — financial reports and analytics.
- **Offline expense entry and synchronization** — users can add expenses offline; data syncs when connectivity returns.
- **Security and privacy** — the SRS specifies security and privacy requirements.
- **Database planning** — the SRS specifies database reference entities and attributes.
- **Cross-platform compatibility** — the application must run on multiple platforms.
- **Testing** — the SRS specifies testing requirements.
- **Installation** — the SRS specifies installation requirements.

### Submission Deliverables (SRS-mandated)

The SRS mandates the following deliverables as part of the submission:

- **Credentials** — demo/test credentials documented for judges. `SRS Requirement`
- **APK** — a buildable Android Package. `SRS Requirement`
- **Source code** — the complete source code repository. `SRS Requirement`
- **README** — a README file documenting the project. `SRS Requirement`
- **MP4 demonstration** — a video demonstration of the application. `SRS Requirement`

---

## Tag Scheme (Used Throughout)

Every statement in this documentation is tagged with exactly one of:

| Tag | Meaning |
|-----|---------|
| **`SRS Requirement`** | The SRS explicitly states the requirement. Where possible, the relevant SRS section heading is cited. No clause numbers are invented. |
| **`Derived Design`** | Logically follows from an SRS requirement but the SRS does not explicitly specify this exact design (e.g., a specific screen, flow, or component that satisfies an SRS-mandated capability). |
| **`Team Technical Decision`** | A technical or design decision selected by the team where the SRS does not mandate the choice (e.g., state management library, color palette, navigation package, HTTP client, local database library). |
| **`Implementation Detail`** | A concrete implementation choice actually confirmed from the project source code. **Not written as a fact unless verified from the actual project.** |
| **`Assumption`** | Inferred because the SRS does not specify it and the team has not yet decided it. Not used where a clear SRS requirement exists. |
| **`TBD`** | A decision genuinely remains open. |

If a statement has no tag, it is structural / navigational text (e.g., "see also", "this section covers").

### Critical distinction

- An **SRS Requirement** is what the SRS explicitly states.
- A **Derived Design** is what the team designs to satisfy an SRS requirement.

Example:
- `SRS Requirement`: Users can create monthly budgets.
- `Derived Design`: The application provides a Budget screen containing the monthly budget controls.

The documentation does **not** claim the SRS mandates a specific screen layout, component, or technology unless the SRS actually says so.

---

## What This Documentation Does NOT Contain

To avoid fabrication, the following are **not present** until confirmed:

- **Test results** — test cases are specified; pass/fail status is recorded only after tests are actually run. Status: `Not Yet Verified` at documentation generation time.
- **Performance numbers** — performance targets may be SRS-mandated; measured values are recorded only after measurement.
- **Screenshots** — none. The MP4 demo is the SRS-mandated visual deliverable.
- **Credentials** — SRS-mandated as a submission deliverable; only a placeholder template is documented, real values supplied at submission time.
- **Implementation status** — features are documented as `Required by SRS` and tracked as `Planned` / `In Development` / `Implemented` / `Tested` / `Verified` only when the corresponding status is actually known. Otherwise `TBD` or `Not Yet Verified`.
- **Technology choices** — the SRS does **not** mandate specific technologies (no Firebase, Supabase, Node.js, Dio, Hive, Isar, Drift, Riverpod, Bloc, Provider, GoRouter, particular LLM, particular backend language). All such choices are `Team Technical Decision` or `TBD` until the team decides via ADRs.

---

## Repository Layout

```
pennypal/
├── README.md                              ← you are here
├── DOCUMENTATION_INDEX.md                 ← master navigation
├── docs/
│   ├── product/                           ← what we are building
│   │   ├── PRODUCT_OVERVIEW.md
│   │   ├── REQUIREMENTS.md
│   │   ├── FEATURE_SPECIFICATIONS.md
│   │   └── TRACEABILITY_MATRIX.md
│   ├── design/                            ← UX and visual
│   │   ├── UI_UX_DESIGN.md
│   │   ├── DESIGN_SYSTEM.md
│   │   └── USER_FLOWS.md
│   ├── architecture/                      ← how it is structured
│   │   ├── ARCHITECTURE.md
│   │   ├── TECHNICAL_DESIGN.md
│   │   ├── DATABASE_DESIGN.md
│   │   ├── SECURITY.md
│   │   ├── OFFLINE_SYNC_DESIGN.md
│   │   └── AI_CHATBOT_DESIGN.md
│   ├── adr/                               ← Architecture Decision Records
│   │   ├── ADR-001-flutter-multiplatform.md
│   │   ├── ADR-002-state-management.md
│   │   ├── ADR-003-navigation.md
│   │   ├── ADR-004-local-storage.md
│   │   ├── ADR-005-api-client.md
│   │   ├── ADR-006-authentication.md
│   │   ├── ADR-007-offline-sync.md
│   │   └── ADR-008-ai-chatbot.md
│   ├── diagrams/                          ← Mermaid diagrams
│   │   ├── DIAGRAMS_INDEX.md
│   │   ├── SYSTEM_CONTEXT.md
│   │   ├── ARCHITECTURE_DIAGRAM.md
│   │   ├── DATA_FLOW.md
│   │   ├── ER_DIAGRAM.md
│   │   ├── USER_FLOW.md
│   │   └── DEPLOYMENT.md
│   ├── process/                           ← how the team operates
│   │   ├── DEVELOPMENT_WORKFLOW.md
│   │   ├── TEAM_WORKFLOW.md
│   │   ├── TESTING.md
│   │   ├── DEPLOYMENT.md
│   │   └── PROJECT_PLAN.md
│   ├── viva/                              ← judge / viva defence
│   │   ├── VIVA_PREPARATION.md
│   │   ├── PRESENTATION.md
│   │   └── SUBMISSION_REQUIREMENTS.md
│   ├── ASSUMPTIONS.md                     ← all assumptions, explicit
│   └── LIMITATIONS.md                     ← known limitations, explicit
```

---

## Reading Order

1. `README.md` (this file).
2. `docs/product/PRODUCT_OVERVIEW.md` — SRS-derived product definition.
3. `docs/product/REQUIREMENTS.md` — SRS-derived requirements list.
4. `docs/product/TRACEABILITY_MATRIX.md` — requirement → feature → derived design → technical design → test case.
5. `docs/architecture/ARCHITECTURE.md`.
6. All ADRs in `docs/adr/`.
7. `docs/process/PROJECT_PLAN.md` (Team Project Plan — not SRS-mandated schedule).
8. `docs/viva/VIVA_PREPARATION.md`.

---

## Status Legend

| Status | Meaning |
|--------|---------|
| `Audited` | Documentation has been audited against the available SRS source material. `Assumption` and `TBD` items may still be pending final team verification against the authoritative SRS. |
| `Team-Reviewed` | Team has walked the file and confirmed tags are accurate. |
| `Final` | Reviewed and frozen for submission. |

Every file in this repository currently has status `Audited`.

---

## Verification Scope

The SRS-derived portions of this documentation were validated against the available SRS source material. Remaining `Assumption` items require final team verification against the authoritative SRS. This documentation does not claim 100% SRS compliance. Within the material reviewed, there are 0 known unresolved conflicts.

---

## Responsible AI Usage Reminder

Per the SRS, AI is supporting aid rather than a substitute. The team must:

- Review and understand every line of this documentation. `SRS Requirement`
- Be able to explain the architecture, requirements, design, and implementation during judging. `SRS Requirement`
- Demonstrate meaningful modification of AI-assisted work (not accept AI output verbatim). `SRS Requirement`

AI-generated documentation is **not** automatically acceptable for final submission. The team's review and understanding is mandatory.

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team (all members; see `docs/process/TEAM_WORKFLOW.md`)
**Status:** `Audited` — pending team verification of `Assumption` and `TBD` items
