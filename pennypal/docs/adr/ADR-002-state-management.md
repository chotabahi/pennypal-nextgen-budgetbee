# ADR-002: State Management Library

> **Status:** `TBD` — pending team decision
> **Date:** `[TBD]`
> **Decision Maker:** Team
> **Supersedes:** None
> **Superseded by:** None

## Context

PennyPal has multiple SRS-mandated feature areas (Dashboard, Income/Expenses, Budgets, Savings Goals, Learning Content, AI Chatbot, Notifications, Reports, Feedback, Support, Offline Sync) that need to share state. `SRS Requirement` (features)

The state management library must hold UI state, allow widgets to read it reactively, allow widgets to dispatch actions, support dependency injection, support async state, and be familiar to all team members.

## SRS constraint

The SRS does **not** specify a state management library. This is a `Team Technical Decision`. The SRS does not mandate Riverpod, Bloc, Provider, or any specific library.

## Options considered

**`[TBD — team to document options considered.]`**

Candidate options (pending team decision — **none assumed**):
- Riverpod
- Bloc / Cubit
- Provider
- Other

## Decision

**`TBD`** — team decides on Day 1.

## Reason

**`[TBD — pending decision.]`**

## Consequences

**`[TBD — pending decision.]`**

## References

- `../architecture/ARCHITECTURE.md` → *State Management Layer*
- `../architecture/TECHNICAL_DESIGN.md` → *Module Boundaries*

---

**Last updated:** Source-accuracy audit
**Owner:** Team — pending Day 1 decision
