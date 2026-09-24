# Database Design

> **Authority:** SRS data requirements (in `REQUIREMENTS.md`). This document defines the **logical data model** for PennyPal — entities, fields, relationships, indexes, constraints.

This document is **storage-agnostic** at the logical level. The chosen physical storage is `TBD` (pending ADR-004 for local, pending backend stack decision for server).

**Critical distinction:** The SRS specifies **10 database reference entities**. These are tagged `SRS Requirement`. Other entities (e.g., Feedback, ChatMessage, SyncQueue) are **not** in the SRS reference list — they are tagged `Derived Design` or `Team Technical Decision`. Specific entity fields not in the SRS are tagged `Derived Design` or `TBD`.

---

## 1. Design Principles

### 1.1 SRS-mandated principles

| Principle | Tag | SRS section |
|-----------|-----|-------------|
| The system shall plan its database. | `SRS Requirement` | Database planning |
| The database shall include the SRS reference entities. | `SRS Requirement` | Database planning |

### 1.2 Team-decided principles

**Tag:** `Team Technical Decision` — `TBD`.

| Principle | Tag | Rationale |
|-----------|-----|-----------|
| `[TBD]` | `Team Technical Decision` | `[TBD]` |

Candidate principles (pending team decision):
- Soft deletes only.
- UUIDs for primary keys.
- Integer minor units for monetary amounts.
- Optimistic concurrency (required for offline sync — `SRS Requirement`).
- No SQL injection / parameterized queries only.

---

## 2. Entity Relationship Overview

The SRS specifies the following **10 reference entities** (`SRS Requirement`):

```
USERS ──┬── TRANSACTIONS ──── CATEGORIES
        │        │
        │        └── (offline sync status)
        │
        ├── USERPROFILES
        ├── BUDGETS
        ├── SAVINGSGOALS
        ├── REPORTS
        ├── LEARNINGCONTENT
        ├── NOTIFICATIONS
        └── SUPPORTQUERIES
```

For a rendered ER diagram, see `../diagrams/ER_DIAGRAM.md`.

---

## 3. SRS Reference Entities (10 — `SRS Requirement`)

> **Note:** These 10 entities are explicitly listed in the SRS as database reference entities. Field specifics not in the SRS are tagged `Derived Design` or `TBD`.

### E-01: Users

**Traces to:** SRS section "Database planning". `SRS Requirement`

| Field | Type | Constraints | Notes | Tag |
|-------|------|-------------|-------|-----|
| `id` | `[TBD]` | PK | `[TBD]` | `Derived Design` / `TBD` |
| `email` | string | unique, not null | `[TBD]` | `Derived Design` |
| `role` | enum (Student, Admin) | not null | Distinguishes roles per SRS. | `SRS Requirement` (User roles) |
| `passwordHash` | string | not null (server only) | `[TBD]` | `Derived Design` |
| Other fields | `[TBD]` | | Pending SRS verification of attribute list. | `TBD` |

**Relationships:**
- Has many Transactions. `SRS Requirement` (implied by feature)
- Has one UserProfile. `SRS Requirement`
- Has many Budgets, SavingsGoals, Reports, Notifications, SupportQueries. `SRS Requirement` (implied)
- Has access to LearningContent. `SRS Requirement`

---

### E-02: UserProfiles

**Traces to:** SRS section "Database planning". `SRS Requirement`

| Field | Type | Constraints | Notes | Tag |
|-------|------|-------------|-------|-----|
| `id` | `[TBD]` | PK | | `Derived Design` / `TBD` |
| `userId` | UUID | FK → Users, not null | | `SRS Requirement` (implied) |
| Other profile fields (name, avatar, etc.) | `[TBD]` | | Pending SRS verification of attribute list. | `TBD` |

> **Note:** The SRS distinguishes Users from UserProfiles as separate reference entities. The exact division of fields between them is `Derived Design` / `TBD` pending SRS attribute specification.

---

### E-03: Transactions

**Traces to:** SRS section "Database planning", "Income and expenses", "Transaction history", "Offline + sync". `SRS Requirement`

| Field | Type | Constraints | Notes | Tag |
|-------|------|-------------|-------|-----|
| `id` | `[TBD]` | PK | | `Derived Design` / `TBD` |
| `userId` | UUID | FK → Users | | `SRS Requirement` (implied) |
| `type` | enum (income, expense) | not null | | `SRS Requirement` (Income and expenses) |
| `amount` | `[TBD]` | >0 | | `SRS Requirement` |
| `date` | datetime | not null | | `Derived Design` |
| `categoryId` | UUID | FK → Categories | For expenses. | `SRS Requirement` (Expense categories) |
| `note` | string | optional | | `Derived Design` |
| Other fields | `[TBD]` | | Pending SRS verification of attribute list. | `TBD` |
| Sync-related fields (e.g., syncStatus, serverUpdatedAt) | `[TBD]` | | Required for offline sync (`SRS Requirement`). Specific field design `TBD` per ADR-007. | `SRS Requirement` (sync mandated); `TBD` (field design) |

---

### E-04: Categories

**Traces to:** SRS section "Database planning", "Expense categories". `SRS Requirement`

| Field | Type | Constraints | Notes | Tag |
|-------|------|-------------|-------|-----|
| `id` | `[TBD]` | PK | | `Derived Design` / `TBD` |
| `name` | string | not null | | `SRS Requirement` |
| Other fields (icon, isSystem, etc.) | `[TBD]` | | Pending SRS verification. | `TBD` |

---

### E-05: Budgets

**Traces to:** SRS section "Database planning", "Budgets". `SRS Requirement`

| Field | Type | Constraints | Notes | Tag |
|-------|------|-------------|-------|-----|
| `id` | `[TBD]` | PK | | `Derived Design` / `TBD` |
| `userId` | UUID | FK → Users | | `SRS Requirement` (implied) |
| `amount` | `[TBD]` | >0 | | `SRS Requirement` |
| Other fields (period, category, etc.) | `[TBD]` | | Pending SRS verification of attribute list. | `TBD` |

---

### E-06: SavingsGoals

**Traces to:** SRS section "Database planning", "Savings goals". `SRS Requirement`

| Field | Type | Constraints | Notes | Tag |
|-------|------|-------------|-------|-----|
| `id` | `[TBD]` | PK | | `Derived Design` / `TBD` |
| `userId` | UUID | FK → Users | | `SRS Requirement` (implied) |
| `targetAmount` | `[TBD]` | >0 | | `SRS Requirement` |
| `currentAmount` | `[TBD]` | ≥0 | | `SRS Requirement` |
| Other fields (deadline, name, etc.) | `[TBD]` | | Pending SRS verification of attribute list. | `TBD` |

---

### E-07: Reports

**Traces to:** SRS section "Database planning", "Reports". `SRS Requirement`

| Field | Type | Constraints | Notes | Tag |
|-------|------|-------------|-------|-----|
| `id` | `[TBD]` | PK | | `Derived Design` / `TBD` |
| `userId` | UUID | FK → Users | | `SRS Requirement` (implied) |
| Other fields (report type, period, generated data, etc.) | `[TBD]` | | Pending SRS verification of attribute list. | `TBD` |

> **Note:** The SRS lists Reports as both a feature and a database reference entity. The exact structure (e.g., whether Reports stores generated report data or report metadata) is `TBD` pending SRS attribute specification.

---

### E-08: LearningContent

**Traces to:** SRS section "Database planning", "Learning content". `SRS Requirement`

| Field | Type | Constraints | Notes | Tag |
|-------|------|-------------|-------|-----|
| `id` | `[TBD]` | PK | | `Derived Design` / `TBD` |
| `title` | string | not null | | `Derived Design` |
| `body` / `content` | `[TBD]` | not null | Format TBD (article, video, etc.). | `Derived Design` |
| Other fields (createdBy, createdAt, etc.) | `[TBD]` | | Pending SRS verification. | `TBD` |

---

### E-09: Notifications

**Traces to:** SRS section "Database planning", "Notifications". `SRS Requirement`

| Field | Type | Constraints | Notes | Tag |
|-------|------|-------------|-------|-----|
| `id` | `[TBD]` | PK | | `Derived Design` / `TBD` |
| `userId` | UUID | FK → Users | | `SRS Requirement` (implied) |
| `body` | string | not null | | `Derived Design` |
| Other fields (type, isRead, createdAt, etc.) | `[TBD]` | | Pending SRS verification. | `TBD` |

---

### E-10: SupportQueries

**Traces to:** SRS section "Database planning", "Contact support". `SRS Requirement`

| Field | Type | Constraints | Notes | Tag |
|-------|------|-------------|-------|-----|
| `id` | `[TBD]` | PK | | `Derived Design` / `TBD` |
| `userId` | UUID | FK → Users | | `SRS Requirement` (implied) |
| `body` | string | not null | | `SRS Requirement` |
| Other fields (subject, status, createdAt, handledBy, etc.) | `[TBD]` | | Pending SRS verification. | `TBD` |

> **Note:** The SRS uses the name `SupportQueries` (not "SupportRequest"). This document uses the SRS name.

---

## 4. Non-SRS Entities (Derived Design / Team Technical Decision)

> **Note:** The SRS does **not** list the following entities as database reference entities. They are included here because the SRS-mandated features imply a need for storage, but they are tagged `Derived Design` (the SRS mandates the feature but not the database entity) or `Team Technical Decision` (the team adds the entity for implementation).

### E-11: Feedback (Derived Design)

**Traces to:** SRS section "Feedback" (feature is `SRS Requirement`; database entity is **not** in SRS reference list).

**Tag:** `Derived Design` — the SRS mandates the Feedback feature but does not list a Feedback database entity. The team derives a Feedback table to store submitted feedback.

| Field | Type | Constraints | Notes | Tag |
|-------|------|-------------|-------|-----|
| `id` | `[TBD]` | PK | | `Derived Design` |
| `userId` | UUID | FK → Users | | `Derived Design` |
| `text` | string | not null | | `SRS Requirement` (feedback text) |
| Other fields | `[TBD]` | | | `Derived Design` |

---

### E-12: ChatMessage (Derived Design)

**Traces to:** SRS section "AI chatbot" (feature is `SRS Requirement`; database entity is **not** in SRS reference list).

**Tag:** `Derived Design` — the SRS mandates the AI chatbot feature but does not list a ChatMessage database entity. The team derives a ChatMessage table to store chat history.

| Field | Type | Constraints | Notes | Tag |
|-------|------|-------------|-------|-----|
| `id` | `[TBD]` | PK | | `Derived Design` |
| `userId` | UUID | FK → Users | | `Derived Design` |
| `role` | enum (user, assistant) | not null | | `Derived Design` |
| `content` | string | not null | | `Derived Design` |
| Other fields | `[TBD]` | | | `Derived Design` |

---

### E-13: SyncQueue (Team Technical Decision)

**Traces to:** SRS section "Offline + sync" (sync is `SRS Requirement`; specific queue entity is team-decided).

**Tag:** `Team Technical Decision` — the SRS mandates offline expense entry and synchronization. A SyncQueue entity is a team-decided implementation approach (pending ADR-007). The SRS does not mandate a queue-based design.

| Field | Type | Constraints | Notes | Tag |
|-------|------|-------------|-------|-----|
| `id` | `[TBD]` | PK | | `Team Technical Decision` |
| `entityType` | string | not null | | `Team Technical Decision` |
| `entityId` | UUID | not null | | `Team Technical Decision` |
| `operation` | enum (create, update, delete) | not null | | `Team Technical Decision` |
| `payload` | string (JSON) | not null | | `Team Technical Decision` |
| `createdAt` | datetime | not null | | `Team Technical Decision` |
| `attempts` | int | default 0 | | `Team Technical Decision` |

---

### E-14: ConflictLog (Team Technical Decision)

**Traces to:** SRS section "Offline + sync" (sync is `SRS Requirement`; specific conflict log entity is team-decided).

**Tag:** `Team Technical Decision` — may be used for sync conflict tracking. Specific design is team-decided (pending ADR-007). The SRS does not mandate a conflict log.

| Field | Type | Constraints | Notes | Tag |
|-------|------|-------------|-------|-----|
| `id` | `[TBD]` | PK | | `Team Technical Decision` |
| Other fields | `[TBD]` | | | `Team Technical Decision` |

---

## 5. Relationships Summary

### SRS-mandated relationships (implied by SRS reference entities and features)

| From | To | Type | Notes | Tag |
|------|----|------|-------|-----|
| Users | UserProfiles | 1:1 | | `SRS Requirement` |
| Users | Transactions | 1:N | | `SRS Requirement` |
| Users | Budgets | 1:N | | `SRS Requirement` |
| Users | SavingsGoals | 1:N | | `SRS Requirement` |
| Users | Reports | 1:N | | `SRS Requirement` |
| Users | Notifications | 1:N | | `SRS Requirement` |
| Users | SupportQueries | 1:N | | `SRS Requirement` |
| Users | LearningContent | N:M (access) | Admin manages; Student views. | `SRS Requirement` |
| Categories | Transactions | 1:N | | `SRS Requirement` |

### Derived relationships

| From | To | Type | Notes | Tag |
|------|----|------|-------|-----|
| Users | Feedback | 1:N | Feedback feature is `SRS Requirement`; entity is `Derived Design`. | `Derived Design` |
| Users | ChatMessage | 1:N | Chatbot feature is `SRS Requirement`; entity is `Derived Design`. | `Derived Design` |
| Categories | Budgets | 1:N | If budgets are per-category. | `Derived Design` |

---

## 6. Indexing Strategy

**Tag:** `Team Technical Decision` — `TBD`.

Indexes are chosen based on query patterns. Likely indexes (pending team decision):
- `Transactions.userId`, `Transactions.date`
- `Budgets.userId`
- `SavingsGoals.userId`
- `Notifications.userId`, `Notifications.isRead`
- `SupportQueries.userId`, `SupportQueries.status`

---

## 7. Migration Strategy

**Tag:** `Team Technical Decision` — `TBD`.

For the competition, only one schema version exists (v1), so no migrations are typically needed.

---

## 8. Physical Storage Mapping

### 8.1 Local on-device storage

**Tag:** `TBD` (pending ADR-004).

The SRS mandates offline expense entry, so local storage is required. `SRS Requirement` Specific technology (Hive / Isar / Drift / other) is `TBD` per ADR-004.

### 8.2 Server-side storage

**Tag:** `TBD` (pending backend stack decision).

The SRS does not mandate a specific server database technology. Candidates (MongoDB, PostgreSQL, Firestore, other) are `TBD`.

---

## 9. Data Volume Estimates

**Tag:** `Assumption` — speculative, not from SRS.

| Entity | Per user | Notes | Tag |
|--------|----------|-------|-----|
| `[TBD]` | `[TBD]` | Estimates. | `Assumption` |

---

## 10. Privacy & Data Retention

> **Tag:** `SRS Requirement` (security and privacy are mandated) or `Team Technical Decision`.

| Data category | Retention | Tag | SRS section |
|---------------|-----------|-----|-------------|
| Active user data | `[TBD]` | `SRS Requirement` (security and privacy mandated); specifics `TBD` | Security and privacy |
| Soft-deleted data | `[TBD]` | `Team Technical Decision` | |
| Logs | `[TBD]` | `Team Technical Decision` | |

See `SECURITY.md` for the full privacy and security posture.

---

## 11. What This Document Does NOT Cover

- **Sync engine** → `OFFLINE_SYNC_DESIGN.md`
- **Security (encryption, access control)** → `SECURITY.md`
- **Why a storage library was chosen** → ADR-004
- **Concrete query examples** → `TECHNICAL_DESIGN.md` and feature specs
- **ER diagram (rendered)** → `../diagrams/ER_DIAGRAM.md`

---

## Team Action: Filling In This File

1. Verify each SRS reference entity (E-01 through E-10) matches the SRS exactly. The 10 entities are: Users, UserProfiles, Transactions, Categories, Budgets, SavingsGoals, Reports, LearningContent, Notifications, SupportQueries. `SRS Requirement`
2. Verify entity field lists against the SRS attribute specifications. Replace `TBD` fields with `SRS Requirement` where the SRS specifies attributes.
3. Confirm non-SRS entities (E-11 through E-14) are correctly tagged `Derived Design` or `Team Technical Decision`.
4. Decide team-decided principles (Section 1.2). Tag `Team Technical Decision`.
5. Wait for ADR-004 (local storage) and backend stack decision to fill in physical storage mapping.
6. Update the file status from `Audited` to `SRS-Complete` (for SRS-derived parts) or `Team-Reviewed` (for team designs).

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending team decisions on physical storage and field specifics
