# Assumptions

> **Authority:** This document records every working assumption made because the SRS is silent on a point. Each assumption is explicit and must be confirmed by the team.

This file records every assumption. Each assumption is explicit and must be confirmed.

If an assumption is **confirmed by the SRS**, replace it with `SRS Requirement` and cite the SRS section.
If an assumption **logically follows from an SRS requirement**, replace it with `Derived Design`.
If an assumption is a **team choice**, replace it with `Team Technical Decision`.
If the SRS is **silent** on a point, leave it as `Assumption` or `TBD`.

---

## A1. SRS-Derived Scope (Confirmed — these are `SRS Requirement`, not assumptions)

These items are confirmed SRS requirements:

| ID | Item | Tag | SRS section |
|----|------|-----|-------------|
| A1.1 | Project scope: multi-platform personal finance application for students. | `SRS Requirement` | Project scope |
| A1.2 | User roles: Student and Admin (both SRS-explicit). | `SRS Requirement` | User roles |
| A1.3 | Authentication is required. | `SRS Requirement` | Authentication |
| A1.4 | Dashboard feature. | `SRS Requirement` | Dashboard |
| A1.5 | Income and expenses feature. | `SRS Requirement` | Income and expenses |
| A1.6 | Expense categories feature. | `SRS Requirement` | Expense categories |
| A1.7 | Transaction history feature. | `SRS Requirement` | Transaction history |
| A1.8 | Budgets feature. | `SRS Requirement` | Budgets |
| A1.9 | Savings goals feature. | `SRS Requirement` | Savings goals |
| A1.10 | Learning content feature. | `SRS Requirement` | Learning content |
| A1.11 | Feedback feature. | `SRS Requirement` | Feedback |
| A1.12 | Contact support feature. | `SRS Requirement` | Contact support |
| A1.13 | AI chatbot feature (basic financial guidance; **supporting aid only, not a substitute**). | `SRS Requirement` | AI chatbot |
| A1.14 | Notifications feature. | `SRS Requirement` | Notifications |
| A1.15 | Reports feature. | `SRS Requirement` | Reports |
| A1.16 | Offline expense entry and synchronization. | `SRS Requirement` | Offline + sync |
| A1.17 | Security and privacy requirements. | `SRS Requirement` | Security and privacy |
| A1.18 | Database planning requirements. | `SRS Requirement` | Database planning |
| A1.19 | Cross-platform compatibility. | `SRS Requirement` | Cross-platform compatibility |
| A1.20 | Testing requirements. | `SRS Requirement` | Testing |
| A1.21 | Installation requirements. | `SRS Requirement` | Installation |

### A1.R — Responsible AI Usage (SRS-mandated)

| ID | Item | Tag | SRS section |
|----|------|-----|-------------|
| A1.R1 | AI is supporting aid rather than a substitute. | `SRS Requirement` | Responsible AI usage |
| A1.R2 | The project must demonstrate meaningful understanding and modification of AI-assisted work. | `SRS Requirement` | Responsible AI usage |
| A1.R3 | AI-generated documentation is not automatically acceptable for final submission; team review is mandatory. | `SRS Requirement` | Responsible AI usage |
| A1.R4 | The team must be able to explain architecture, requirements, design, and implementation during judging. | `SRS Requirement` | Responsible AI usage |

### A1.D — SRS Database Reference Entities (Confirmed — these are `SRS Requirement`)

The SRS specifies the following database reference entities:

| ID | Entity | Tag | SRS section |
|----|--------|-----|-------------|
| A1.D1 | Users | `SRS Requirement` | Database planning |
| A1.D2 | UserProfiles | `SRS Requirement` | Database planning |
| A1.D3 | Transactions | `SRS Requirement` | Database planning |
| A1.D4 | Categories | `SRS Requirement` | Database planning |
| A1.D5 | Budgets | `SRS Requirement` | Database planning |
| A1.D6 | SavingsGoals | `SRS Requirement` | Database planning |
| A1.D7 | Reports | `SRS Requirement` | Database planning |
| A1.D8 | LearningContent | `SRS Requirement` | Database planning |
| A1.D9 | Notifications | `SRS Requirement` | Database planning |
| A1.D10 | SupportQueries | `SRS Requirement` | Database planning |

Note: The SRS requires Feedback as a feature (`SRS Requirement`) but does **not** list Feedback as a database reference entity. Any Feedback table in the database design is therefore `Derived Design`, not `SRS Requirement`. Same for chat messages (the SRS mandates the chatbot feature but does not list a ChatMessage entity).

### A1.S — SRS-Mandated Submission Deliverables

| ID | Deliverable | Tag | SRS section |
|----|-------------|-----|-------------|
| A1.S1 | Credentials (demo/test) | `SRS Requirement` | Submission |
| A1.S2 | APK | `SRS Requirement` | Submission |
| A1.S3 | Source code | `SRS Requirement` | Submission |
| A1.S4 | README | `SRS Requirement` | Submission |
| A1.S5 | MP4 demonstration video | `SRS Requirement` | Submission |

---

## A2. Architectural Choices (Open — Pending ADRs)

The SRS mandates the **existence** of capabilities (offline sync, AI chatbot, auth) but does not mandate specific implementation technologies. The following are open team decisions:

| ID | Item | Tag | Resolution |
|----|------|-----|------------|
| A2.1 | State management library (Riverpod / Bloc / Provider / etc.) | `TBD` | ADR-002 |
| A2.2 | Navigation library (GoRouter / auto_route / etc.) | `TBD` | ADR-003 |
| A2.3 | Local on-device storage (Hive / Isar / Drift / etc.) | `TBD` | ADR-004 — required for SRS-mandated offline entry |
| A2.4 | HTTP client (Dio / http / etc.) | `TBD` | ADR-005 |
| A2.5 | Auth strategy specifics (email/password, biometric, OAuth, etc.) | `TBD` | ADR-006 — auth is `SRS Requirement`; method is `Team Technical Decision` |
| A2.6 | Sync strategy (last-write-wins, CRDTs, etc.) | `TBD` | ADR-007 — sync is `SRS Requirement`; strategy is `Team Technical Decision` |
| A2.7 | Chatbot integration approach (server-side proxy, on-device, etc.) | `TBD` | ADR-008 — chatbot is `SRS Requirement`; approach is `Team Technical Decision` |
| A2.8 | Backend stack (Node.js, Firebase, Supabase, custom, etc.) | `TBD` | Team decision — SRS does not mandate |
| A2.9 | LLM provider (OpenAI, Anthropic, Google, local, etc.) | `TBD` | Team decision — SRS does not mandate |
| A2.10 | Push notification service (FCM, APNs, etc.) | `TBD` | Team decision — SRS does not mandate |
| A2.11 | CI/CD provider (GitHub Actions, etc.) | `TBD` | Team decision — SRS does not mandate |
| A2.12 | Framework (Flutter, React Native, native, etc.) | `TBD` | ADR-001 — SRS mandates cross-platform; framework is `Team Technical Decision` |

---

## A3. Process Assumptions (Open — Not SRS-Specified)

The SRS does not specify team size or build window. These are team / competition constraints:

| ID | Item | Tag | Resolution |
|----|------|-----|------------|
| A3.1 | Team size | `Assumption` | Confirm against competition rules. |
| A3.2 | Build window duration | `Assumption` | Confirm against competition rules. |
| A3.3 | Submission deadline | `Assumption` | Confirm against competition rules. |
| A3.4 | Presentation / viva format | `Assumption` | Confirm against competition rules. |
| A3.5 | Five-day project schedule | `Assumption` / `Team Technical Decision` | The schedule in `PROJECT_PLAN.md` is a `Team Project Plan`, not SRS-mandated. |

---

## A4. Implementation Status Assumptions

The SRS describes the **required** system. Implementation status is tracked separately and is **not assumed**:

| ID | Item | Tag | Resolution |
|----|------|-----|------------|
| A4.1 | No SRS-mandated feature is assumed implemented. | `Assumption` | Implementation status tracked in `LIMITATIONS.md` → *Unimplemented Features*. Status per feature: `Required by SRS`, `Planned`, `In Development`, `Implemented`, `Tested`, `Verified`, or `Not Yet Verified`. |
| A4.2 | No test results are assumed. | `Assumption` | Test cases are specified in `process/TESTING.md`; results recorded only after tests are actually run. Current status: `Not Yet Verified`. |
| A4.3 | No performance numbers are assumed. | `Assumption` | Performance targets may be `SRS Requirement`; measured values recorded only after measurement. |
| A4.4 | No screenshots exist. | `Assumption` | The MP4 demo is the SRS-mandated visual deliverable. |
| A4.5 | No credentials are documented with real values. | `Assumption` | Only a placeholder template; real values supplied at submission time. |

---

## A5. Derived Design Items (Logically Follow from SRS — Not Assumptions)

These items are `Derived Design` (they follow from SRS requirements but the SRS does not specify the exact design):

| ID | Item | Tag | Derived from SRS requirement |
|----|------|-----|-------------------------------|
| A5.1 | Specific screens (Login, Dashboard, Add Income/Expense, etc.) | `Derived Design` | SRS-mandated features imply screens, but SRS does not name specific screens. |
| A5.2 | Specific user flows | `Derived Design` | SRS-mandated capabilities imply flows, but SRS does not specify flows. |
| A5.3 | Feedback table in database | `Derived Design` | SRS mandates Feedback feature; database entity not in SRS reference list. |
| A5.4 | ChatMessage table in database | `Derived Design` | SRS mandates AI chatbot feature; database entity not in SRS reference list. |
| A5.5 | SyncQueue table in database | `Team Technical Decision` | Required for offline sync implementation; specific design is team-decided. |
| A5.6 | ConflictLog table in database | `Team Technical Decision` | May be used for sync conflict tracking; specific design is team-decided. |
| A5.7 | Specific sync algorithm (last-write-wins, etc.) | `TBD` | SRS mandates sync; algorithm is `Team Technical Decision` per ADR-007. |
| A5.8 | Specific chatbot prompt architecture | `TBD` | SRS mandates chatbot; prompt design is `Team Technical Decision` per ADR-008. |
| A5.9 | Specific UI components (buttons, cards, etc.) | `Team Technical Decision` | Visual design is team-decided. |
| A5.10 | Specific color palette | `Team Technical Decision` | Visual design is team-decided. |

---

## Verification Checklist (for the team)

Walk this checklist on Day 0 / Day 1 morning:

- [ ] Confirm all items in Section A1 are accurately transcribed from the SRS.
- [ ] Confirm Responsible AI Usage items (Section A1.R) are accurately transcribed.
- [ ] Confirm SRS database reference entities (Section A1.D) — verify the 10 entities match the SRS exactly.
- [ ] Confirm SRS-mandated submission deliverables (Section A1.S).
- [ ] For each item in Section A2, hold the ADR discussion and resolve to `Team Technical Decision`.
- [ ] Confirm items in Section A3 against the competition rules.
- [ ] Throughout the build, update `LIMITATIONS.md` → *Unimplemented Features* as features are completed.
- [ ] Verify Section A5 items are correctly tagged as `Derived Design` or `Team Technical Decision`.

Once ADRs are decided, propagate the chosen technologies into:
- `architecture/ARCHITECTURE.md`
- `architecture/TECHNICAL_DESIGN.md`
- `architecture/DATABASE_DESIGN.md`
- `architecture/SECURITY.md`
- `architecture/OFFLINE_SYNC_DESIGN.md`
- `architecture/AI_CHATBOT_DESIGN.md`
- All ADRs in `adr/`

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending team verification of `Assumption` and `TBD` items
