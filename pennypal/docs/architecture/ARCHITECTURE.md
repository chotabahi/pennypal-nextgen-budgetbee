# Architecture

> **Authority:** SRS constraints and non-functional requirements. This document defines the **high-level architecture** of PennyPal.

This document is the architectural backbone. Every other technical document elaborates a slice of what is described here.

**Critical distinction:** The SRS mandates **capabilities** (cross-platform compatibility, security, offline sync, AI chatbot, role-based access). Specific architectural style, technology choices, and patterns are `Team Technical Decision` or `TBD` unless the SRS explicitly mandates them. **No specific technology is presented as mandatory unless the SRS says so.**

---

## 1. Architectural Goals

### 1.1 SRS-mandated goals

| Goal | Tag | SRS section |
|------|-----|-------------|
| Cross-platform compatibility — the system shall run on multiple platforms. | `SRS Requirement` | Cross-platform compatibility |
| Security and privacy — the system shall meet SRS-specified security and privacy requirements. | `SRS Requirement` | Security and privacy |
| Offline expense entry and synchronization. | `SRS Requirement` | Offline + sync |
| Role-based access (Student / Admin). | `SRS Requirement` | User roles |
| Database planning (with reference entities). | `SRS Requirement` | Database planning |
| Testing. | `SRS Requirement` | Testing |
| Installation. | `SRS Requirement` | Installation |
| Responsible AI usage (AI is supporting aid; team must demonstrate understanding). | `SRS Requirement` | Responsible AI usage |

### 1.2 Team-decided goals

**Tag:** `Team Technical Decision` — `TBD`.

| Goal | Tag | Rationale |
|------|-----|-----------|
| `[TBD]` | `Team Technical Decision` | Pending team decision. |

Candidate team-decided goals:
- Defensible in viva.
- Testable.
- Simple (smallest structure that meets SRS).
- Performance-target-respecting (targets pending SRS verification).

---

## 2. Architectural Style

### 2.1 SRS-mandated style

**`Assumption`** — the SRS does not appear to mandate a specific architectural style. Pending SRS verification.

### 2.2 Team-decided style

**Tag:** `Team Technical Decision` — `TBD`.

The team decides on the architectural style (layered, feature-first, Clean Architecture, etc.) on Day 1. Once decided, document it here and in ADRs.

A common choice for a multi-platform app is a layered architecture (UI → State → Application → Repository → Data Source) with feature folders inside the layers. The dependency rule: dependencies point inward. **This is a candidate, not a decision.**

---

## 3. The Layers

> **Note:** This section assumes a layered architecture (a `Team Technical Decision` pending). If the team chooses a different style, restructure this section.

| Layer | Responsibility | Tag |
|-------|----------------|-----|
| UI | Render widgets, capture user input. | `Team Technical Decision` (layer design); `SRS Requirement` (screens exist per features) |
| State | Hold UI state, dispatch to application. | `Team Technical Decision` (library TBD per ADR-002) |
| Application | Business logic, use cases. | `Team Technical Decision` |
| Repository | Data contracts, offline-first orchestration. | `Team Technical Decision` |
| Data Source | Talk to local DB / remote API. | `SRS Requirement` (offline entry); `TBD` (specific tech per ADR-004, ADR-005) |

### 3.1 The Dependency Rule

**Tag:** `Team Technical Decision` — `TBD`.

If the team adopts the "dependencies point inward" rule, document it here.

---

## 4. Major Subsystems

The SRS mandates the following subsystems (their existence is `SRS Requirement`; their specific design is `Team Technical Decision` or `TBD`):

| Subsystem | Purpose | SRS section | Tag | Design doc |
|-----------|---------|-------------|-----|------------|
| Authentication subsystem | Authenticate users; distinguish Student/Admin roles. | Authentication / User roles | `SRS Requirement` (existence); `TBD` (specific design per ADR-006) | `TECHNICAL_DESIGN.md`, `SECURITY.md`, `ADR-006` |
| Offline sync subsystem | Allow offline expense entry; synchronize when online. | Offline + sync | `SRS Requirement` (existence); `TBD` (specific design per ADR-007) | `OFFLINE_SYNC_DESIGN.md`, `ADR-004`, `ADR-007` |
| AI chatbot subsystem | Provide basic financial guidance as supporting aid. | AI chatbot | `SRS Requirement` (existence); `TBD` (specific design per ADR-008) | `AI_CHATBOT_DESIGN.md`, `ADR-008` |
| Notifications subsystem | Deliver notifications to users. | Notifications | `SRS Requirement` (existence); `TBD` (specific design) | `TECHNICAL_DESIGN.md` |
| Learning content subsystem | Provide learning content (Student view; Admin management). | Learning content | `SRS Requirement` (existence); `TBD` (specific design) | `TECHNICAL_DESIGN.md`, `DATABASE_DESIGN.md` |
| Reports subsystem | Generate reports. | Reports | `SRS Requirement` (existence); `TBD` (specific design) | `TECHNICAL_DESIGN.md` |
| Feedback / Support subsystem | Allow users to submit feedback and contact support. | Feedback / Contact support | `SRS Requirement` (existence); `TBD` (specific design) | `TECHNICAL_DESIGN.md`, `DATABASE_DESIGN.md` |

---

## 5. Component Diagram (Textual)

**`TBD`** — pending architectural style decision and ADRs. Once decided, a textual component diagram goes here. A rendered version is in `../diagrams/ARCHITECTURE_DIAGRAM.md`.

---

## 6. Data Flow Examples

For each SRS-mandated flow, a data flow example shows how the request moves through the layers.

### DF-1: Add Expense (online)

1. UI: User taps Save on Add Expense. `SRS Requirement` (F-03)
2. State: dispatches to use case. `Team Technical Decision`
3. Application: calls repository. `Team Technical Decision`
4. Repository: writes to local DB. `Team Technical Decision`
5. Sync engine (background): pushes to server. `SRS Requirement` (sync mandated); specific mechanism `TBD` per ADR-007.
6. UI: dashboard updates. `Derived Design`

### DF-2: Add Expense (offline)

1. UI: User taps Save. `SRS Requirement` (F-14)
2. State → Application → Repository → Local DB (entry stored). `SRS Requirement` (offline entry); specific mechanism `TBD`.
3. Sync engine: detects no connectivity; defers. `Team Technical Decision`
4. Connectivity returns: sync engine pushes pending entry. `SRS Requirement` (sync mandated)
5. UI: sync indicator updates. `Derived Design`

For rendered sequence diagrams, see `../diagrams/DATA_FLOW.md`.

---

## 7. Cross-cutting Concerns

For each cross-cutting concern, document the team's approach. All are `Team Technical Decision` unless the SRS specifies.

| Concern | Approach | Tag | SRS section (if applicable) |
|---------|----------|-----|------------------------------|
| Logging | `[TBD]` | `Team Technical Decision` | `SRS Requirement` (security — no PII in logs) |
| Error handling | `[TBD]` | `Team Technical Decision` | |
| Configuration | `[TBD]` | `Team Technical Decision` | |
| Dependency injection | `[TBD]` | `Team Technical Decision` | |
| Internationalization | `[TBD]` | `Team Technical Decision` | |
| Accessibility | `[TBD]` | `Team Technical Decision` | `[SRS Requirement if SRS specifies]` |

---

## 8. Architectural Decisions Summary

The following decisions are detailed in `../adr/`:

| Decision | ADR | Status |
|----------|-----|--------|
| Multi-platform framework | ADR-001 | `TBD` (SRS mandates cross-platform; framework is `Team Technical Decision`) |
| State management library | ADR-002 | `TBD` |
| Navigation approach | ADR-003 | `TBD` |
| Local on-device storage | ADR-004 | `TBD` (required by SRS for offline entry) |
| HTTP client | ADR-005 | `TBD` |
| Authentication strategy | ADR-006 | `TBD` (auth is SRS-mandated; method is `Team Technical Decision`) |
| Offline-first sync strategy | ADR-007 | `TBD` (sync is SRS-mandated; strategy is `Team Technical Decision`) |
| AI chatbot integration | ADR-008 | `TBD` (chatbot is SRS-mandated; approach is `Team Technical Decision`) |

The SRS does **not** mandate specific technologies (no Firebase, Supabase, Node.js, Dio, Hive, Isar, Drift, Riverpod, Bloc, Provider, GoRouter, particular LLM, particular backend language). All such choices are `Team Technical Decision` or `TBD`.

---

## 9. What This Document Does NOT Cover

- **Concrete classes, modules, file structure** → `TECHNICAL_DESIGN.md`
- **Data model** → `DATABASE_DESIGN.md`
- **Sync engine** → `OFFLINE_SYNC_DESIGN.md`
- **Chatbot** → `AI_CHATBOT_DESIGN.md`
- **Security** → `SECURITY.md`
- **Why each decision was made** → `../adr/`

---

## Team Action: Filling In This File

1. Confirm SRS-mandated goals (Section 1.1) against the actual SRS.
2. Decide team-decided goals (Section 1.2) on Day 1. Tag `Team Technical Decision`.
3. Decide architectural style (Section 2) and document the layers (Section 3).
4. Confirm subsystems (Section 4) against the SRS.
5. Decide cross-cutting concerns (Section 7).
6. **Do not present specific technologies as mandatory.** All technology choices are `TBD` until ADRs are decided.
7. Update the file status from `Audited` to `Team-Reviewed`.

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending team decisions on architectural style and ADRs; no technologies presented as mandatory
