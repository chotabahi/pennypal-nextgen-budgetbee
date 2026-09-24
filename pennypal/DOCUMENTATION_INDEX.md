# Documentation Index

Master navigation for the PennyPal documentation system. Every file is listed here with its purpose and current status.

All files have been audited against the available SRS source material. The SRS-derived portions were validated against the available SRS source material; remaining `Assumption` items require final team verification against the authoritative SRS. This documentation does not claim 100% SRS compliance. Within the material reviewed, there are 0 known unresolved conflicts.

---

## Tag Scheme

| Tag | Meaning |
|-----|---------|
| `SRS Requirement` | Explicitly stated by the SRS. |
| `Derived Design` | Logically follows from an SRS requirement but not explicitly specified by the SRS. |
| `Team Technical Decision` | Team choice where the SRS does not mandate. |
| `Implementation Detail` | Confirmed from project source code. |
| `Assumption` | Inferred because SRS is silent; team has not decided. |
| `TBD` | Genuinely unresolved. |

---

## 1. Product Documentation

| Document | What it answers | Status |
|----------|-----------------|--------|
| [PRODUCT_OVERVIEW.md](product/PRODUCT_OVERVIEW.md) | What is PennyPal? Who uses it? What problem does it solve? | `Audited` |
| [REQUIREMENTS.md](product/REQUIREMENTS.md) | The canonical list of SRS-mandated functional and non-functional requirements. | `Audited` |
| [FEATURE_SPECIFICATIONS.md](product/FEATURE_SPECIFICATIONS.md) | Behaviour of every SRS-mandated feature; specific UI details tagged `Derived Design`. | `Audited` |
| [TRACEABILITY_MATRIX.md](product/TRACEABILITY_MATRIX.md) | SRS requirement → feature → derived design → technical design → test case. | `Audited` |

## 2. Design Documentation

| Document | What it answers | Status |
|----------|-----------------|--------|
| [UI_UX_DESIGN.md](design/UI_UX_DESIGN.md) | UX philosophy, information architecture, screen inventory. Screens are `Derived Design` unless SRS names them. | `Audited` |
| [DESIGN_SYSTEM.md](design/DESIGN_SYSTEM.md) | Colors, typography, spacing, components, states. All `Team Technical Decision` or `TBD`. | `Audited` |
| [USER_FLOWS.md](design/USER_FLOWS.md) | User journeys. Flows are `Derived Design` (SRS mandates capability, not specific flow). | `Audited` |

## 3. Architecture Documentation

| Document | What it answers | Status |
|----------|-----------------|--------|
| [ARCHITECTURE.md](architecture/ARCHITECTURE.md) | High-level architecture. SRS mandates capabilities; style is `Team Technical Decision`. | `Audited` |
| [TECHNICAL_DESIGN.md](architecture/TECHNICAL_DESIGN.md) | Concrete technical design. Pending ADR decisions; specific tech `TBD`. | `Audited` |
| [DATABASE_DESIGN.md](architecture/DATABASE_DESIGN.md) | SRS reference entities (Users, UserProfiles, Transactions, Categories, Budgets, SavingsGoals, Reports, LearningContent, Notifications, SupportQueries); non-SRS entities tagged `Derived Design`. | `Audited` |
| [SECURITY.md](architecture/SECURITY.md) | SRS-mandated security/privacy requirements; specific controls `Team Technical Decision` or `TBD`. | `Audited` |
| [OFFLINE_SYNC_DESIGN.md](architecture/OFFLINE_SYNC_DESIGN.md) | SRS mandates offline entry + sync; specific algorithm/architecture `Derived Design` or `TBD`. | `Audited` |
| [AI_CHATBOT_DESIGN.md](architecture/AI_CHATBOT_DESIGN.md) | SRS mandates basic AI guidance; specific LLM/prompt/RAG `TBD`. Preserves SRS restriction: AI is supporting aid. | `Audited` |

## 4. Architecture Decision Records (ADRs)

Each ADR documents a technical choice the SRS does not mandate. All are `TBD` until the team decides. Each ADR follows the structure: Context → SRS constraint (if applicable) → Options considered → Decision → Reason → Consequences → Status.

| ADR | Decision | Status |
|-----|----------|--------|
| [ADR-001](adr/ADR-001-flutter-multiplatform.md) | Multi-platform framework. SRS mandates cross-platform; framework is `Team Technical Decision`. | `TBD` |
| [ADR-002](adr/ADR-002-state-management.md) | State management library. | `TBD` |
| [ADR-003](adr/ADR-003-navigation.md) | Navigation approach. | `TBD` |
| [ADR-004](adr/ADR-004-local-storage.md) | Local on-device storage (required for SRS-mandated offline entry). | `TBD` |
| [ADR-005](adr/ADR-005-api-client.md) | HTTP client. | `TBD` |
| [ADR-006](adr/ADR-006-authentication.md) | Auth method (SRS mandates auth; method is `Team Technical Decision`). | `TBD` |
| [ADR-007](adr/ADR-007-offline-sync.md) | Sync strategy (SRS mandates sync; strategy is `Team Technical Decision`). | `TBD` |
| [ADR-008](adr/ADR-008-ai-chatbot.md) | Chatbot integration (SRS mandates chatbot; approach is `Team Technical Decision`). | `TBD` |

## 5. Diagrams

All diagrams are Mermaid source. Diagrams that depict SRS-mandated structure use SRS entity names; diagrams that depict team-decided technology label those elements as `TBD` or `Team Technical Decision`.

| Diagram | Shows | Status |
|---------|-------|--------|
| [DIAGRAMS_INDEX.md](diagrams/DIAGRAMS_INDEX.md) | Index of all diagrams. | `Audited` |
| [SYSTEM_CONTEXT.md](diagrams/SYSTEM_CONTEXT.md) | PennyPal in its environment (Student, Admin, AI supporting aid). | `Audited` |
| [ARCHITECTURE_DIAGRAM.md](diagrams/ARCHITECTURE_DIAGRAM.md) | Internal layering. Specific tech labelled `TBD`. | `Audited` |
| [DATA_FLOW.md](diagrams/DATA_FLOW.md) | How data flows. Flow specifics are `Derived Design`. | `Audited` |
| [ER_DIAGRAM.md](diagrams/ER_DIAGRAM.md) | SRS reference entities (10) + team-added entities (labelled `Derived Design`). | `Audited` |
| [USER_FLOW.md](diagrams/USER_FLOW.md) | User journeys. Flows are `Derived Design`. | `Audited` |
| [DEPLOYMENT.md](diagrams/DEPLOYMENT.md) | Deployment topology. Specific tech `TBD`. | `Audited` |

## 6. Process Documentation

| Document | What it answers | Status |
|----------|-----------------|--------|
| [DEVELOPMENT_WORKFLOW.md](process/DEVELOPMENT_WORKFLOW.md) | Git, PRs, code review. `Team Technical Decision`. | `Audited` |
| [TEAM_WORKFLOW.md](process/TEAM_WORKFLOW.md) | Roles, schedule. `Team Technical Decision`. | `Audited` |
| [TESTING.md](process/TESTING.md) | Test cases. No fabricated results; all actual results `Not Yet Verified`. | `Audited` |
| [DEPLOYMENT.md](process/DEPLOYMENT.md) | Build SRS-mandated deliverables. Specific build process `TBD` pending ADRs. | `Audited` |
| [PROJECT_PLAN.md](process/PROJECT_PLAN.md) | **Team Project Plan** (not SRS-mandated schedule). | `Audited` |

## 7. Viva & Submission Documentation

| Document | What it answers | Status |
|----------|-----------------|--------|
| [VIVA_PREPARATION.md](viva/VIVA_PREPARATION.md) | Question bank. General Flutter/Dart separated from SRS-based. Preserves AI understanding requirement. | `Audited` |
| [PRESENTATION.md](viva/PRESENTATION.md) | Demo script, slide outline. | `Audited` |
| [SUBMISSION_REQUIREMENTS.md](viva/SUBMISSION_REQUIREMENTS.md) | SRS-mandated deliverables: Credentials, APK, Source code, README, MP4. | `Audited` |

## 8. Project-Wide References

| Document | What it answers | Status |
|----------|-----------------|--------|
| [ASSUMPTIONS.md](ASSUMPTIONS.md) | All working assumptions, explicit. | `Audited` |
| [LIMITATIONS.md](LIMITATIONS.md) | Known limitations; unimplemented features list. | `Audited` |

---

## Reading Order

### For the team (Day 0 / Day 1 morning)

1. `README.md` (5 min).
2. `docs/product/PRODUCT_OVERVIEW.md`.
3. `docs/product/REQUIREMENTS.md`.
4. `docs/product/TRACEABILITY_MATRIX.md`.
5. `docs/architecture/ARCHITECTURE.md`.
6. All ADRs in `docs/adr/`.
7. `docs/process/PROJECT_PLAN.md` (Team Project Plan).
8. `docs/viva/VIVA_PREPARATION.md`.

### For judges

1. `README.md`.
2. `docs/product/PRODUCT_OVERVIEW.md`.
3. `docs/product/TRACEABILITY_MATRIX.md`.
4. `docs/architecture/ARCHITECTURE.md`.
5. Sample 2–3 ADRs.
6. `docs/viva/SUBMISSION_REQUIREMENTS.md`.

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending team verification of `Assumption` and `TBD` items
