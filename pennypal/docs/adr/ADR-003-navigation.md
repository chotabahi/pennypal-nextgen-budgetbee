# ADR-003: Navigation Approach

> **Status:** `TBD` — pending team decision
> **Date:** `[TBD]`
> **Decision Maker:** Team
> **Supersedes:** None
> **Superseded by:** None

## Context

PennyPal has 19 screens (per `../design/UI_UX_DESIGN.md` → *Screen Inventory*) covering all SRS-mandated features plus Student/Admin role-based access. `SRS Requirement` (features, roles)

The navigation approach must support named routes, redirects (auth-gating per SRS), testability, and work across all target platforms.

## SRS constraint

- The SRS mandates authentication (`SRS Requirement`) — auth-gating is required.
- The SRS mandates role-based access (Student/Admin) (`SRS Requirement`) — role-based redirects required.
- The SRS does **not** specify a navigation library. This is a `Team Technical Decision`. The SRS does not mandate GoRouter, auto_route, or any specific library.

## Options considered

**`[TBD — team to document options considered.]`**

Candidate options (pending team decision — **none assumed**):
- GoRouter
- auto_route
- Beamer
- Navigator 1.0 (imperative) — not recommended for 19+ screens

## Decision

**`TBD`** — team decides on Day 1.

## Reason

**`[TBD — pending decision.]`**

## Consequences

**`[TBD — pending decision.]`**

## References

- `../architecture/TECHNICAL_DESIGN.md` → *Project Structure*
- `../design/UI_UX_DESIGN.md` → *Navigation Model*

---

**Last updated:** Source-accuracy audit
**Owner:** Team — pending Day 1 decision
