# ADR-004: Local On-Device Storage

> **Status:** `TBD` — pending team decision (SRS-mandated requirement)
> **Date:** `[TBD]`
> **Decision Maker:** Team
> **Supersedes:** None
> **Superseded by:** None

## Context

The SRS mandates offline expense entry and synchronization. `SRS Requirement` (Offline + sync)

This requires local on-device storage that can:
- Store expense entries created offline.
- Survive app kill and device reboot.
- Be queried by the UI (for offline view of transactions, budgets, savings goals, etc.).
- Be synchronized to the server when connectivity returns. `SRS Requirement`

## SRS constraint

- The system shall allow users to create expense entries while offline. `SRS Requirement`
- The system shall synchronize offline entries when connectivity returns. `SRS Requirement`
- The SRS does **not** specify the local storage technology. This is a `Team Technical Decision`. The SRS does not mandate Hive, Isar, Drift, or any specific library.

## Options considered

**`[TBD — team to document options considered.]`**

Candidate options (pending team decision — **none assumed**):
- Hive
- Isar
- Drift (SQLite)
- Other

## Decision

**`TBD`** — team decides on Day 1.

## Reason

**`[TBD — pending decision.]`**

## Consequences

**`[TBD — pending decision.]`**

## References

- `../architecture/DATABASE_DESIGN.md` → *Physical Storage Mapping*
- `../architecture/ARCHITECTURE.md` → *Data Source Layer*
- `../product/REQUIREMENTS.md` → FR-OFF-01 (offline expense entry — `SRS Requirement`)

---

**Last updated:** Source-accuracy audit
**Owner:** Team — pending Day 1 decision
