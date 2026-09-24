# Offline & Synchronization Design

> **Authority:** SRS section "Offline expense entry and synchronization". This document is **active** because the SRS mandates offline expense entry and synchronization. `SRS Requirement`

This document defines the offline-first synchronization subsystem of PennyPal.

**Critical distinction:** The SRS mandates **the capability** (offline expense entry + synchronization when online). Specific sync algorithm, conflict resolution, queue architecture, background workers, and database technology are **not** specified by the SRS — they are `Derived Design`, `Team Technical Decision`, or `TBD`. **Nothing is invented.**

---

## 1. Design Goals

### 1.1 SRS-mandated goals

| Goal | Tag | SRS section |
|------|-----|-------------|
| The system shall allow users to create expense entries while offline. | `SRS Requirement` | Offline + sync |
| The system shall synchronize offline entries when connectivity returns. | `SRS Requirement` | Offline + sync |

### 1.2 Team-decided goals

**Tag:** `Team Technical Decision` — `TBD`.

| Goal | Tag | Rationale |
|------|-----|-----------|
| `[TBD]` | `Team Technical Decision` | Pending team adoption. |

Candidate goals (pending team decision):
- Never lose user data.
- UI is always responsive (offline writes return quickly).
- Conflict resolution is deterministic.
- Sync is idempotent.
- Sync is observable.
- Sync is battery-friendly.

---

## 2. Offline-First Pattern

**Tag:** `TBD` (pending ADR-007).

The SRS mandates that users can create expense entries while offline and that those entries synchronize when online. `SRS Requirement`

The specific offline-first pattern (local-first, online-first with cache, etc.) is `TBD` per ADR-007. **No specific pattern is invented here.**

Candidate patterns (pending team decision):
- Local-first: every write goes to local DB first, sync engine pushes when online.
- Online-first with offline cache: writes go to server when online, cached locally when offline.

---

## 3. SyncQueue

> **Note:** A SyncQueue is a `Team Technical Decision` (its design), required by the SRS (its existence is implied by sync). The SRS mandates synchronization; the queue implementation is team-decided. **The SRS does not mandate a queue-based design.**

**Tag:** `Team Technical Decision` — `TBD` (pending ADR-007).

If the team adopts a queue-based design, the queue fields would be:

| Field | Description | Tag |
|-------|-------------|-----|
| `id` | UUID. | `Team Technical Decision` |
| `entityType` | "transaction", etc. | `Team Technical Decision` |
| `entityId` | The ID of the changed entity. | `Team Technical Decision` |
| `operation` | create / update / delete. | `Team Technical Decision` |
| `payload` | Full entity DTO at enqueue time. | `Team Technical Decision` |
| `createdAt` | When the change was made. | `Team Technical Decision` |
| `attempts` | Number of sync attempts. | `Team Technical Decision` |
| `lastError` | Error from last attempt. | `Team Technical Decision` |

---

## 4. Push Protocol

**Tag:** `TBD` (pending backend stack and ADR-007).

The SRS mandates that offline entries synchronize when connectivity returns. `SRS Requirement`

The specific push protocol (endpoint design, request/response shape, batching) is `Team Technical Decision` pending ADR-007 and backend stack decision. **No specific protocol is invented here.**

---

## 5. Pull Protocol

**Tag:** `TBD` (pending backend stack and ADR-007).

The SRS mandates synchronization. `SRS Requirement`

The specific pull protocol is `Team Technical Decision` pending ADR-007 and backend stack decision. **No specific protocol is invented here.**

---

## 6. Conflict Resolution

### 6.1 SRS-mandated conflict resolution

**`Assumption`** — pending SRS verification. The SRS mandates synchronization; specific conflict resolution rules are not stated. **No specific algorithm is invented.**

### 6.2 Team-decided conflict resolution

**Tag:** `TBD` (pending ADR-007).

Candidate strategies (pending team decision — **none assumed**):
- Last-write-wins based on server-received timestamp.
- Field-level merge.
- CRDTs.
- Manual resolution UI.

The team decides in ADR-007. **The documentation does not state a specific strategy until the team decides.**

---

## 7. Sync Engine Lifecycle

**Tag:** `TBD` (pending ADR-007).

The SRS mandates synchronization when online. `SRS Requirement` The specific lifecycle (start, loop, triggers, stop) is `Team Technical Decision` pending ADR-007. **No specific lifecycle is invented.**

---

## 8. Network & Error Handling

**Tag:** `TBD` (pending ADR-007).

The SRS mandates synchronization; specific error handling (retry strategy, backoff, permanent vs transient errors) is `Team Technical Decision` pending ADR-007. **No specific handling is invented.**

---

## 9. Background Sync

**Tag:** `TBD` (pending platform support verification and ADR-007).

The SRS mandates synchronization when online. `SRS Requirement` The specific background sync approach (WorkManager, BGTaskScheduler, etc.) is `Team Technical Decision` pending ADR-007 and platform decisions. **No specific approach is invented.**

---

## 10. Sync State Machine

**Tag:** `TBD` (pending ADR-007).

The SRS mandates synchronization. `SRS Requirement` The specific state machine (Idle → Syncing → Synced / Error) is `Team Technical Decision` pending ADR-007. **No specific state machine is invented.**

---

## 11. UI Surface

### 11.1 Sync indicator

**Tag:** `Team Technical Decision` — `TBD` (pending UI/UX design and ADR-007).

The SRS mandates synchronization; a sync indicator is `Derived Design` (the team's design to make sync observable to the user). Specific indicator design is `Team Technical Decision`.

### 11.2 Sync detail screen (S-14)

**Tag:** `Derived Design` (screen) — `TBD` (specific design).

---

## 12. Testing Strategy

**Tag:** `Team Technical Decision` — `TBD` (pending `../process/TESTING.md`).

Key SRS-derived test scenarios (test cases specified; results `Not Yet Verified`):
- Add expense offline → reconnect → verify sync. `SRS Requirement` (test scenario derived from SRS sync mandate)
- Pending change survives app kill. `Derived Design` — pending team design.
- Conflict scenario → resolution. `Derived Design` — pending team design.

**No test results are fabricated.** All test results are `Not Yet Verified` until tests are actually run.

---

## 13. Viva Defence Summary

> **Note:** Filled in once the sync design is complete. Each question must have an honest, SRS-accurate answer.

**`TBD`** — pending sync design completion.

Key viva points (SRS-accurate):
- The SRS mandates offline expense entry and synchronization when online. `SRS Requirement`
- Specific sync strategy (conflict resolution, idempotency, queue architecture, background workers) is `Team Technical Decision` documented in ADR-007. **No specific strategy is claimed until the team decides.**

---

## 14. What This Document Does NOT Cover

- **Entity definitions** → `DATABASE_DESIGN.md`
- **Why we chose this sync architecture** → ADR-007
- **Security of the sync protocol** → `SECURITY.md`

---

## Team Action: Filling In This File

1. The SRS-mandated goals (Section 1.1) are confirmed.
2. Decide team-decided goals (Section 1.2). Tag `Team Technical Decision`.
3. Wait for ADR-007 (sync strategy) and ADR-004 (local storage) to be decided.
4. Fill in the team-decided sections: SyncQueue, push/pull protocols, conflict resolution, sync engine lifecycle, error handling, background sync, UI surface.
5. **Do not invent specifics.** If a section depends on an undecided ADR, leave as `TBD`.
6. Update the file status from `Audited` to `SRS-Complete` (for SRS-derived parts) or `Team-Reviewed` (for team designs).

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending ADR-004 and ADR-007 decisions; no invented specifics
