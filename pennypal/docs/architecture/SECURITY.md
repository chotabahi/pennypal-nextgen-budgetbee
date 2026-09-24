# Security

> **Authority:** SRS security and privacy requirements. This document defines the **security architecture** of PennyPal.

This document is the defensive reference for the viva. Every security control must trace to either an SRS requirement (`SRS Requirement`) or a `Team Technical Decision`.

**Critical distinction:** The SRS mandates security and privacy. Specific controls (encryption algorithms, auth methods, transport protocols) are `Team Technical Decision` or `TBD` unless the SRS explicitly specifies them. **No specific technology is presented as mandatory.**

---

## 1. Security Principles

### 1.1 SRS-mandated principles

| Principle | Tag | SRS section |
|-----------|-----|-------------|
| The system shall meet the SRS's security and privacy requirements. | `SRS Requirement` | Security and privacy |
| The system shall authenticate users (Student / Admin). | `SRS Requirement` | Authentication / User roles |
| The system shall restrict Admin features to Admin users. | `SRS Requirement` | Authentication / User roles |

### 1.2 Team-decided principles

**Tag:** `Team Technical Decision` — `TBD`.

| Principle | Tag | Rationale |
|-----------|-----|-----------|
| `[TBD]` | `Team Technical Decision` | Pending team decision. |

Candidate principles (pending team decision):
- Defence in depth.
- Least privilege.
- Fail secure.
- No security through obscurity.
- Honest about residual risk.

---

## 2. Threat Model

> **Note:** The threat model is `Team Technical Decision` unless the SRS specifies threats. The team identifies threats using STRIDE or another methodology once the SRS-derived features are confirmed.

For each threat category (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege), document:

| Threat | Vectors | Controls | Residual risk | Tag |
|--------|---------|----------|---------------|-----|
| Spoofing | Stolen credentials, MITM. | Auth (`SRS Requirement`); transport security (`Team Technical Decision`). | `[TBD]` | `SRS Requirement` (auth); `Team Technical Decision` (other) |
| Elevation of Privilege | Student attempts Admin actions. | Role checks (`SRS Requirement`). | `[TBD]` | `SRS Requirement` |
| Information Disclosure | Unauthorized data access. | Auth + role checks (`SRS Requirement`). | `[TBD]` | `SRS Requirement` |
| Tampering | Local DB modification, in-transit tampering. | Transport security; local DB encryption (pending ADR-004). | `[TBD]` | `Team Technical Decision` |
| Repudiation | User denies action. | Audit log (`Derived Design` — pending team decision). | `[TBD]` | `Derived Design` |
| Denial of Service | API flooding, LLM budget exhaustion (if applicable). | Rate limiting (`Team Technical Decision`); LLM budget cap (if applicable, `Team Technical Decision`). | `[TBD]` | `Team Technical Decision` |

---

## 3. Authentication

### 3.1 SRS-mandated auth requirements

| Requirement | Tag | SRS section |
|-------------|-----|-------------|
| The system shall authenticate users. | `SRS Requirement` | Authentication |
| The system shall distinguish Student and Admin roles. | `SRS Requirement` | User roles |
| Admin features shall be restricted to Admin users. | `SRS Requirement` | User roles |
| Student features shall be restricted to authenticated users. | `SRS Requirement` | Authentication |

### 3.2 Auth strategy

**Tag:** `TBD` (pending ADR-006).

The auth method (email/password, biometric, OAuth, etc.) and token strategy (JWT, session cookies, OAuth) are team decisions documented in `ADR-006`. **No specific method is assumed.**

---

## 4. Authorization

### 4.1 SRS-mandated authz requirements

| Requirement | Tag | SRS section |
|-------------|-----|-------------|
| Role-based access (Student / Admin). | `SRS Requirement` | User roles |
| Admin features restricted to Admin. | `SRS Requirement` | User roles |

### 4.2 Access rules

| Resource | Read | Write | Delete | SRS section / tag |
|----------|------|-------|--------|-------------------|
| Own User profile | Self | Self | Self (account deletion) | `SRS Requirement` (auth); `Derived Design` (specific rules) |
| Other Users | Admin (user management) | Admin | Admin | `SRS Requirement` (Admin role); `Derived Design` (specific rules) |
| Own Transactions | Self | Self | Self | `SRS Requirement`; `Derived Design` |
| Own Budgets | Self | Self | Self | `SRS Requirement`; `Derived Design` |
| Own SavingsGoals | Self | Self | Self | `SRS Requirement`; `Derived Design` |
| Own Feedback | Self (submit); Admin (review) | Self (submit); Admin (respond) | Admin | `SRS Requirement`; `Derived Design` |
| Own SupportQueries | Self (submit); Admin (handle) | Self (submit); Admin (respond) | Admin | `SRS Requirement`; `Derived Design` |
| Own ChatMessages | Self | Self (delete own history) | Self | `SRS Requirement`; `Derived Design` |
| Own Notifications | Self | Self (mark read) | Self | `SRS Requirement`; `Derived Design` |
| LearningContent | Student (view); Admin (manage) | Admin | Admin | `SRS Requirement` |
| Reports | Self (view) | — | — | `SRS Requirement`; `Derived Design` |

### 4.3 Server-side enforcement

**Tag:** `Team Technical Decision` — all authz must be enforced server-side. Document the enforcement approach here once the backend is designed.

---

## 5. Transport Security

### 5.1 SRS-mandated transport security

**`Assumption`** — pending SRS verification. The SRS mandates security and privacy; specific transport requirements (TLS version, HSTS) are likely `Team Technical Decision`.

### 5.2 Team-decided transport security

**Tag:** `Team Technical Decision` — `TBD`.

Candidate: TLS 1.2+ everywhere; HSTS on the server. **No specific protocol is assumed.**

---

## 6. Data-at-Rest Security

### 6.1 SRS-mandated at-rest security

**`Assumption`** — pending SRS verification. The SRS mandates security and privacy; specific at-rest encryption requirements are likely `Team Technical Decision`.

### 6.2 Local DB encryption

**Tag:** `TBD` (pending ADR-004).

The SRS mandates offline expense entry, so the local DB must store user data. `SRS Requirement` Whether the DB is encrypted is a `Team Technical Decision` pending ADR-004.

### 6.3 Server DB encryption

**Tag:** `TBD` (pending backend stack decision).

---

## 7. Input Validation

### 7.1 SRS-mandated validation

**`Assumption`** — pending SRS verification.

### 7.2 Validation approach

**Tag:** `Team Technical Decision` — `TBD`.

- Client-side validation: `[TBD]`
- Server-side validation: `[TBD]`
- SQL/NoSQL injection prevention: `[TBD]`
- XSS prevention: `[TBD]`

---

## 8. Secrets Management

**Tag:** `Team Technical Decision` — `TBD`.

For each secret type (LLM API key, JWT signing secret, DB password, etc.), document where it's stored and how it's accessed. No real secrets are listed here — this is a structural description only.

| Secret | Storage | Access | Tag |
|--------|---------|--------|-----|
| `[TBD]` | `[TBD]` | `[TBD]` | `Team Technical Decision` |

---

## 9. Residual Risk

> **Note:** Honest documentation of what is and isn't defended. The team does not claim production-grade security.

| Risk | Reason | Tag |
|------|--------|-----|
| No penetration test | Out of scope for a competition. | `Assumption` |
| `[TBD]` | `[TBD]` | `[TBD]` |

---

## 10. OWASP Mobile Top 10 Self-Review

> **Tag:** `Team Technical Decision` — `TBD`.

If the team performs a self-review against the OWASP Mobile Top 10, document the results here. This is a `Team Technical Decision`, not an SRS mandate. **No results are fabricated.**

| OWASP Category | Control | Status |
|----------------|---------|--------|
| M1: Improper Credential Usage | `[TBD]` | `TBD` |
| M2: Insecure Communication | `[TBD]` | `TBD` |
| ... | ... | ... |

---

## 11. Privacy & Compliance

### 11.1 SRS-mandated privacy requirements

| Requirement | Tag | SRS section |
|-------------|-----|-------------|
| The system shall meet the SRS's privacy requirements. | `SRS Requirement` | Security and privacy |

### 11.2 Compliance posture

**Tag:** `Team Technical Decision` — `TBD`.

---

## 12. Viva Defence Summary

> **Note:** This section is filled in once the security design is complete. Each question must have an honest, SRS-accurate answer.

**`TBD`** — pending security design completion.

Key viva points (SRS-accurate):
- The SRS mandates security and privacy requirements. `SRS Requirement`
- The SRS mandates authentication with Student/Admin roles. `SRS Requirement`
- Specific security controls (encryption, transport, auth method) are `Team Technical Decision` documented in ADRs. **No specific controls are claimed until the team decides.**

---

## 13. What This Document Does NOT Cover

- **Why we chose this auth strategy** → ADR-006
- **Sync engine security** → `OFFLINE_SYNC_DESIGN.md`
- **Chatbot safety** → `AI_CHATBOT_DESIGN.md`
- **Deployment security** → `../process/DEPLOYMENT.md`

---

## Team Action: Filling In This File

1. Confirm SRS-mandated security and privacy requirements (Section 1.1, 3.1, 4.1, 11.1).
2. Identify security principles the team adopts beyond the SRS. Tag `Team Technical Decision`.
3. Build the threat model once the SRS-derived features are confirmed.
4. Wait for ADR-006 (auth) and the backend stack decision to fill in auth, authz, and at-rest security.
5. **Do not fabricate security properties.** If a control is not implemented, say so.
6. **No security test results are fabricated.** All test results are `Not Yet Verified`.
7. Update the file status from `Audited` to `SRS-Complete` (for SRS-derived parts) or `Team-Reviewed` (for team-decided parts).

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending ADR-006 and team decisions on security specifics; no fabricated results
