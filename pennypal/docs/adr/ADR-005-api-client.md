# ADR-005: HTTP Client and API Layer

> **Status:** `TBD` — pending team decision and backend stack
> **Date:** `[TBD]`
> **Decision Maker:** Team
> **Supersedes:** None
> **Superseded by:** None

## Context

The SRS mandates features that imply a backend (authentication, synchronization, AI chatbot, Admin-managed learning content, feedback/support review). `SRS Requirement`

The client needs an HTTP client to talk to the backend. The client must support interceptors (for auth token injection), streaming (potentially for the chatbot), cancellation, file upload/download (if SRS mandates), and work across all platforms (per SRS cross-platform requirement). `SRS Requirement`

## SRS constraint

- The SRS mandates authentication (`SRS Requirement`) — auth interceptor required.
- The SRS mandates synchronization (`SRS Requirement`) — sync API calls required.
- The SRS mandates an AI chatbot (`SRS Requirement`) — chat API calls required.
- The SRS mandates cross-platform compatibility (`SRS Requirement`) — HTTP client must work on all target platforms.
- The SRS does **not** specify the HTTP client. This is a `Team Technical Decision`. The SRS does not mandate Dio, http, Retrofit, or any specific library.

## Options considered

**`[TBD — team to document options considered.]`**

Candidate options (pending team decision — **none assumed**):
- Dio
- http package
- Retrofit
- Other

## Decision

**`TBD`** — team decides on Day 1.

## Reason

**`[TBD — pending decision.]`**

## Consequences

**`[TBD — pending decision.]`**

## References

- `../architecture/TECHNICAL_DESIGN.md` → *Data Source Layer*
- `../architecture/SECURITY.md` → *Transport Security*

---

**Last updated:** Source-accuracy audit
**Owner:** Team — pending Day 1 decision
