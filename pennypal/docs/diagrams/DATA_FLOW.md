# Data Flow Diagram

> **Authority:** SRS-mandated features. This document shows step-by-step data flows for the most important PennyPal operations, as sequence diagrams.

**Critical distinction:** The flows themselves are `Derived Design` (the team's design to satisfy SRS-mandated capabilities). Specific implementation details (queue, conflict resolution, prompt architecture) are `TBD` pending ADRs. **No specific implementation is invented.**

---

## Data Flow Inventory

| Flow ID | Flow name | Traces to SRS feature | Status |
|---------|-----------|------------------------|--------|
| DF-01 | Add Expense (online) | F-03 Income and expenses | `Audited` |
| DF-02 | Add Expense (offline) + Sync | F-14 Offline + sync | `Audited` |
| DF-03 | AI Chatbot Query | F-11 AI chatbot | `Audited` |
| DF-04 | Admin Manages Learning Content | F-08 Learning content (Admin) | `Audited` |
| DF-05 | Submit Feedback | F-09 Feedback | `Audited` |

---

## DF-01: Add Expense (online)

```mermaid
sequenceDiagram
    autonumber
    actor Student
    participant UI as UI Layer
    participant State as State Layer
    participant App as Application Layer
    participant Repo as TransactionRepository
    participant Local as Local DB
    participant Sync as SyncEngine
    participant API as Server API

    Student->>UI: Tap "Save" on Add Expense
    UI->>State: dispatch save(expense)
    State->>App: AddExpenseUseCase.execute(expense)
    App->>Repo: add(expense)
    Repo->>Local: put(expense)
    Local-->>Repo: saved
    Repo-->>App: Result.success
    App-->>State: Result.success
    State-->>UI: optimistic update (dashboard re-renders)

    Note over Sync,API: Background, sync per ADR-007 (TBD)
    Sync->>API: push (per ADR-007 — TBD)
    API-->>Sync: applied
    Sync->>Local: update sync status
    Sync-->>UI: sync indicator updates
```

**Key points:**
- The UI updates optimistically (SRS-mandated expense recording). `SRS Requirement`
- Sync runs in the background. `SRS Requirement` (sync mandated); specific mechanism `TBD` per ADR-007.

---

## DF-02: Add Expense (offline) + Sync

```mermaid
sequenceDiagram
    autonumber
    actor Student
    participant UI as UI Layer
    participant State as State Layer
    participant Repo as TransactionRepository
    participant Local as Local DB
    participant Sync as SyncEngine
    participant API as Server API

    Note over Student: User is offline
    Student->>UI: Tap "Save"
    UI->>State: dispatch save(expense)
    State->>Repo: add(expense)
    Repo->>Local: put(expense)
    Repo-->>State: Result.success
    State-->>UI: optimistic update (sync indicator shows pending)

    Note over Sync,API: Sync attempts to push, fails (no network)
    Sync->>API: push (per ADR-007 — TBD)
    API--xSync: network error

    Note over Student: User closes app, walks to Wi-Fi
    Note over Sync: Sync triggers on reconnect (per ADR-007 — TBD)
    Sync->>API: push (per ADR-007 — TBD)
    API-->>Sync: applied
    Sync->>Local: update sync status

    Note over Student: User reopens app
    Student->>UI: Open dashboard
    UI->>State: load dashboard
    State-->>UI: dashboard with sync indicator = synced
```

**Key points (SRS-mandated):**
- User can create expense entries while offline. `SRS Requirement`
- Offline entries synchronize when connectivity returns. `SRS Requirement`
- Pending changes survive app kill (per team design in ADR-007). `Team Technical Decision`
- Specific sync mechanism is `TBD` per ADR-007. **No specific algorithm is invented.**

---

## DF-03: AI Chatbot Query

```mermaid
sequenceDiagram
    autonumber
    actor Student
    participant UI as Chat UI
    participant State as ChatNotifier
    participant Repo as ChatRepository
    participant API as Server Chat Proxy
    participant LLM as External LLM (TBD per ADR-008)

    Student->>UI: Type a financial question
    UI->>State: sendMessage(text)
    State->>Repo: send(message)
    Repo->>API: POST /api/chat (message)

    Note over API: Server-side (per ADR-008 — TBD)
    API->>API: authenticate (SRS-mandated)
    API->>API: safety / scope checks (TBD per ADR-008)
    API->>LLM: query (per ADR-008 — TBD)

    LLM-->>API: response (per ADR-008 — TBD)
    API-->>Repo: response
    Repo-->>State: ChatChunk
    State-->>UI: render response
```

**Key points (SRS-mandated):**
- The system provides an AI chatbot. `SRS Requirement`
- The chatbot provides basic financial guidance as supporting aid, not a substitute. `SRS Requirement`
- Specific LLM provider, prompt architecture, safety filtering: `Team Technical Decision` per ADR-008. **No specific design is invented.**

---

## DF-04: Admin Manages Learning Content

```mermaid
sequenceDiagram
    autonumber
    actor Admin
    participant UI as Admin UI
    participant State as State
    participant Repo as LearningContentRepository
    participant API as Server Content Service
    participant DB as Server DB

    Admin->>UI: Create / edit / delete learning content
    UI->>State: dispatch action
    State->>Repo: create/update/delete(content)
    Repo->>API: POST/PUT/DELETE /api/learning
    API->>API: authenticate (Admin role check — SRS-mandated)
    API->>DB: write content
    DB-->>API: saved
    API-->>Repo: success
    Repo-->>State: Result.success
    State-->>UI: confirmation

    Note over Admin: Content is now available to Students
```

**Key points:**
- Admin manages learning content. `SRS Requirement` (Admin role; learning content feature).
- Admin role check enforced server-side. `SRS Requirement`

---

## DF-05: Submit Feedback

```mermaid
sequenceDiagram
    autonumber
    actor Student
    participant UI as Feedback UI
    participant State as State
    participant Repo as FeedbackRepository
    participant API as Server Feedback Service
    participant DB as Server DB

    Student->>UI: Enter feedback text
    UI->>State: submit(text)
    State->>Repo: submit(feedback)
    Repo->>API: POST /api/feedback
    API->>API: authenticate
    API->>DB: save feedback
    DB-->>API: saved
    API-->>Repo: success
    Repo-->>State: Result.success
    State-->>UI: confirmation
```

**Key points (SRS-mandated):**
- The system allows users to submit feedback. `SRS Requirement`

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — flows are `Derived Design`; specific implementation details `TBD` pending ADRs
