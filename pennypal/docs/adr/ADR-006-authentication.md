# ADR-006: Authentication Strategy

> **Status:** `TBD` — pending team decision (SRS-mandated requirement)
> **Date:** `[TBD]`
> **Decision Maker:** Team
> **Supersedes:** None
> **Superseded by:** None

## Context

The SRS mandates authentication and distinguishes between Student and Admin roles. `SRS Requirement` (Authentication, User roles)

## SRS constraint

- The system shall authenticate users. `SRS Requirement`
- The system shall distinguish Student and Admin roles. `SRS Requirement`
- Admin features shall be restricted to Admin users. `SRS Requirement`
- Student features shall be restricted to authenticated users. `SRS Requirement`
- The SRS does **not** specify the auth method (email/password, biometric, OAuth, social, etc.) or the token strategy (JWT, session cookies, OAuth). These are `Team Technical Decision`.

## Options considered

**`[TBD — team to document options considered.]`**

Candidate options for auth method (pending team decision — **none assumed**):
- Email/password
- Biometric
- OAuth / social login
- Other

Candidate options for token strategy (pending team decision — **none assumed**):
- JWT
- Session cookies
- OAuth
- Other

## Decision

**`TBD`** — team decides on Day 1.

The team decides:
- Auth method: `[TBD]`
- Token strategy: `[TBD]`
- Token storage: `[TBD]` (secure storage is recommended `Team Technical Decision`)

## Reason

**`[TBD — pending decision.]`**

## Consequences

**`[TBD — pending decision.]`**

## References

- `../architecture/SECURITY.md` → *Authentication*
- `../architecture/TECHNICAL_DESIGN.md` → *Backend Design*
- `../product/REQUIREMENTS.md` → FR-AUTH-01 through FR-AUTH-05

---

**Last updated:** Source-accuracy audit
**Owner:** Team — pending Day 1 decision
