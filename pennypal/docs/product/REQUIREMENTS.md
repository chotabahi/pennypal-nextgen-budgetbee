# Requirements

> **Authority:** The PennyPal SRS is the sole authority for requirements. Every requirement in this document is traced to a specific SRS section.

This document is the **canonical list of requirements** for PennyPal. Every feature, architectural decision, test case, and line of code should ultimately trace back to a requirement listed here.

Requirements are organized by SRS section. The SRS section names are taken from the SRS's enumerated feature list. No clause numbers are invented; SRS section headings are cited instead.

---

## Requirement Source Tags

Every requirement row carries one of:

| Tag | Meaning |
|-----|---------|
| `SRS Requirement` | Directly from the SRS, cited by section heading. |
| `Derived Design` | Logically follows from an SRS requirement but not explicitly specified by the SRS. |
| `Team Technical Decision` | A team decision that the SRS does not mandate. |
| `Assumption` | Inferred because the SRS is silent; must be confirmed. |
| `TBD` | Awaiting team decision. |

**No requirement is tagged `SRS Requirement` without being transcribed from the SRS.**

---

## Functional Requirements

### FR-AUTH — Authentication (SRS-mandated)

> **SRS section:** Authentication, User roles. **Tag:** `SRS Requirement` (existence of auth is mandated; specific methods are `TBD`).

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| FR-AUTH-01 | The system shall authenticate users. | `SRS Requirement` | Authentication | `FEATURE_SPECIFICATIONS.md → F-01` |
| FR-AUTH-02 | The system shall distinguish between Student and Admin roles. | `SRS Requirement` | User roles | `FEATURE_SPECIFICATIONS.md → F-01` |
| FR-AUTH-03 | The system shall restrict Admin features to Admin users. | `SRS Requirement` | User roles | `FEATURE_SPECIFICATIONS.md → F-01` |
| FR-AUTH-04 | The system shall restrict Student features to authenticated users. | `SRS Requirement` | Authentication | `FEATURE_SPECIFICATIONS.md → F-01` |
| FR-AUTH-05 | Specific auth method (email/password, biometric, OAuth, etc.) | `TBD` | — | `ADR-006` |

### FR-DASH — Dashboard (SRS-mandated)

> **SRS section:** Dashboard. **Tag:** `SRS Requirement`.

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| FR-DASH-01 | The system shall provide a Dashboard for users. | `SRS Requirement` | Dashboard | `FEATURE_SPECIFICATIONS.md → F-02` |
| FR-DASH-02 | Specific dashboard contents (balance, recent transactions, etc.) | `Derived Design` | Dashboard | `FEATURE_SPECIFICATIONS.md → F-02` |

### FR-IE — Income and Expenses (SRS-mandated)

> **SRS section:** Income and expenses. **Tag:** `SRS Requirement`.

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| FR-IE-01 | The system shall allow users to record income entries. | `SRS Requirement` | Income and expenses | `FEATURE_SPECIFICATIONS.md → F-03` |
| FR-IE-02 | The system shall allow users to record expense entries. | `SRS Requirement` | Income and expenses | `FEATURE_SPECIFICATIONS.md → F-03` |
| FR-IE-03 | Expense entries shall support offline creation (see FR-OFF-01). | `SRS Requirement` | Income and expenses / Offline + sync | `FEATURE_SPECIFICATIONS.md → F-03, F-14` |
| FR-IE-04 | Specific entry fields (date, category, note) | `Derived Design` | Income and expenses | `FEATURE_SPECIFICATIONS.md → F-03` |
| FR-IE-05 | View / edit / delete entries | `Derived Design` | Income and expenses / Transaction history | `FEATURE_SPECIFICATIONS.md → F-03, F-05` |

### FR-CAT — Expense Categories (SRS-mandated)

> **SRS section:** Expense categories. **Tag:** `SRS Requirement`.

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| FR-CAT-01 | The system shall allow expenses to be categorized. | `SRS Requirement` | Expense categories | `FEATURE_SPECIFICATIONS.md → F-04` |
| FR-CAT-02 | The system shall support a set of expense categories. | `SRS Requirement` | Expense categories | `FEATURE_SPECIFICATIONS.md → F-04` |
| FR-CAT-03 | Specific category list (default categories, custom categories) | `Derived Design` | Expense categories | `FEATURE_SPECIFICATIONS.md → F-04` |

### FR-TH — Transaction History (SRS-mandated)

> **SRS section:** Transaction history. **Tag:** `SRS Requirement`.

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| FR-TH-01 | The system shall maintain a transaction history. | `SRS Requirement` | Transaction history | `FEATURE_SPECIFICATIONS.md → F-05` |
| FR-TH-02 | The system shall allow users to view their transaction history. | `SRS Requirement` | Transaction history | `FEATURE_SPECIFICATIONS.md → F-05` |
| FR-TH-03 | Specific history features (filtering, search, date range) | `Derived Design` | Transaction history | `FEATURE_SPECIFICATIONS.md → F-05` |

### FR-BUD — Budgets (SRS-mandated)

> **SRS section:** Budgets. **Tag:** `SRS Requirement`.

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| FR-BUD-01 | The system shall allow users to set budgets. | `SRS Requirement` | Budgets | `FEATURE_SPECIFICATIONS.md → F-06` |
| FR-BUD-02 | The system shall allow users to track budget progress. | `SRS Requirement` | Budgets | `FEATURE_SPECIFICATIONS.md → F-06` |
| FR-BUD-03 | Specific budget features (per-category, monthly, alerts) | `Derived Design` | Budgets | `FEATURE_SPECIFICATIONS.md → F-06` |

### FR-SG — Savings Goals (SRS-mandated)

> **SRS section:** Savings goals. **Tag:** `SRS Requirement`.

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| FR-SG-01 | The system shall allow users to set savings goals. | `SRS Requirement` | Savings goals | `FEATURE_SPECIFICATIONS.md → F-07` |
| FR-SG-02 | The system shall allow users to track savings goal progress. | `SRS Requirement` | Savings goals | `FEATURE_SPECIFICATIONS.md → F-07` |
| FR-SG-03 | Specific savings features (contributions, deadlines, target amounts) | `Derived Design` | Savings goals | `FEATURE_SPECIFICATIONS.md → F-07` |

### FR-LC — Learning Content (SRS-mandated)

> **SRS section:** Learning content. **Tag:** `SRS Requirement`.

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| FR-LC-01 | The system shall provide learning content to users. | `SRS Requirement` | Learning content | `FEATURE_SPECIFICATIONS.md → F-08` |
| FR-LC-02 | The learning content shall be financial-literacy oriented. | `Derived Design` | Learning content | `FEATURE_SPECIFICATIONS.md → F-08` |
| FR-LC-03 | Specific content format (articles, videos, interactive) and management (Admin-curated) | `Derived Design` | Learning content | `FEATURE_SPECIFICATIONS.md → F-08` |

### FR-FB — Feedback (SRS-mandated)

> **SRS section:** Feedback. **Tag:** `SRS Requirement`.

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| FR-FB-01 | The system shall allow users to submit feedback. | `SRS Requirement` | Feedback | `FEATURE_SPECIFICATIONS.md → F-09` |
| FR-FB-02 | Specific feedback handling (Admin review, response) | `Derived Design` | Feedback | `FEATURE_SPECIFICATIONS.md → F-09` |

### FR-CS — Contact Support (SRS-mandated)

> **SRS section:** Contact support. **Tag:** `SRS Requirement`.

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| FR-CS-01 | The system shall allow users to contact support. | `SRS Requirement` | Contact support | `FEATURE_SPECIFICATIONS.md → F-10` |
| FR-CS-02 | Specific support channel (in-app form, email, chat) | `Derived Design` | Contact support | `FEATURE_SPECIFICATIONS.md → F-10` |

### FR-AI — AI Chatbot (SRS-mandated)

> **SRS section:** AI chatbot. **Tag:** `SRS Requirement`.

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| FR-AI-01 | The system shall provide an AI chatbot. | `SRS Requirement` | AI chatbot | `FEATURE_SPECIFICATIONS.md → F-11` |
| FR-AI-02 | The chatbot shall provide basic financial guidance. | `SRS Requirement` | AI chatbot | `FEATURE_SPECIFICATIONS.md → F-11` |
| FR-AI-03 | The chatbot is supporting aid, **not a substitute** for professional advice. | `SRS Requirement` | AI chatbot / Responsible AI usage | `FEATURE_SPECIFICATIONS.md → F-11` |
| FR-AI-04 | Specific chatbot scope (what it can / cannot answer) | `Derived Design` | AI chatbot | `FEATURE_SPECIFICATIONS.md → F-11` |
| FR-AI-05 | LLM provider and integration approach | `TBD` | — | `ADR-008` |

### FR-NOT — Notifications (SRS-mandated)

> **SRS section:** Notifications. **Tag:** `SRS Requirement`.

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| FR-NOT-01 | The system shall provide notifications to users. | `SRS Requirement` | Notifications | `FEATURE_SPECIFICATIONS.md → F-12` |
| FR-NOT-02 | Specific notification triggers (budget alerts, reminders, etc.) | `Derived Design` | Notifications | `FEATURE_SPECIFICATIONS.md → F-12` |
| FR-NOT-03 | Notification delivery mechanism (push, in-app, etc.) | `TBD` | — | Team decision |

### FR-REP — Reports (SRS-mandated)

> **SRS section:** Reports. **Tag:** `SRS Requirement`.

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| FR-REP-01 | The system shall provide reports to users. | `SRS Requirement` | Reports | `FEATURE_SPECIFICATIONS.md → F-13` |
| FR-REP-02 | Specific report types (spending by category, trend, etc.) | `Derived Design` | Reports | `FEATURE_SPECIFICATIONS.md → F-13` |

### FR-OFF — Offline Expense Entry and Synchronization (SRS-mandated)

> **SRS section:** Offline + sync. **Tag:** `SRS Requirement`.

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| FR-OFF-01 | The system shall allow users to create expense entries while offline. | `SRS Requirement` | Offline + sync | `FEATURE_SPECIFICATIONS.md → F-14` |
| FR-OFF-02 | The system shall synchronize offline entries when connectivity returns. | `SRS Requirement` | Offline + sync | `FEATURE_SPECIFICATIONS.md → F-14` |
| FR-OFF-03 | Specific sync strategy (conflict resolution, idempotency) | `TBD` | — | `ADR-007` |
| FR-OFF-04 | Local storage technology | `TBD` | — | `ADR-004` |

---

## Non-Functional Requirements

### NFR-SEC — Security and Privacy (SRS-mandated)

> **SRS section:** Security and privacy. **Tag:** `SRS Requirement` (existence is mandated; specifics are `TBD` or `Derived Design`).

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| NFR-SEC-01 | The system shall meet the SRS's security and privacy requirements. | `SRS Requirement` | Security and privacy | `../architecture/SECURITY.md` |
| NFR-SEC-02 | Specific security controls (encryption, auth, etc.) | `Derived Design` / `TBD` | Security and privacy | `../architecture/SECURITY.md` |

### NFR-CP — Cross-Platform Compatibility (SRS-mandated)

> **SRS section:** Cross-platform compatibility. **Tag:** `SRS Requirement`.

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| NFR-CP-01 | The system shall run on multiple platforms. | `SRS Requirement` | Cross-platform compatibility | `ADR-001` |
| NFR-CP-02 | Specific target platforms (Android, iOS, Web, Desktop) | `Assumption` — pending SRS verification | Cross-platform compatibility | `ADR-001` |

### NFR-PERF — Performance

> **Note:** The SRS may specify performance requirements. Until verified, this section is `Assumption`.

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| NFR-PERF-01 | Specific performance targets | `Assumption` — pending SRS verification | (TBD) | `../process/TESTING.md` |

---

## Constraint Requirements

| Req ID | Constraint | Tag | SRS section | Notes |
|--------|------------|-----|-------------|-------|
| CR-01 | Multi-platform compatibility | `SRS Requirement` | Cross-platform compatibility | See NFR-CP-01. |
| CR-02 | Specific framework (e.g., Flutter) | `TBD` | — | See ADR-001. SRS does not mandate a specific framework. |
| CR-03 | Team size | `Assumption` | — | Pending competition rules. See `../ASSUMPTIONS.md` A3.1. |
| CR-04 | Build window | `Assumption` | — | Pending competition rules. See `../ASSUMPTIONS.md` A3.2. |
| CR-05 | Responsible AI usage | `SRS Requirement` | Responsible AI usage | AI is supporting aid; team must demonstrate understanding. |

---

## Data Requirements

> **SRS section:** Database planning. **Tag:** `SRS Requirement` (the SRS specifies reference entities).

The SRS specifies the following database reference entities (`SRS Requirement`):

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| DR-01 | The system shall plan its database. | `SRS Requirement` | Database planning | `../architecture/DATABASE_DESIGN.md` |
| DR-02 | Database shall include `Users` entity. | `SRS Requirement` | Database planning | `../architecture/DATABASE_DESIGN.md → E-01` |
| DR-03 | Database shall include `UserProfiles` entity. | `SRS Requirement` | Database planning | `../architecture/DATABASE_DESIGN.md → E-02` |
| DR-04 | Database shall include `Transactions` entity. | `SRS Requirement` | Database planning | `../architecture/DATABASE_DESIGN.md → E-03` |
| DR-05 | Database shall include `Categories` entity. | `SRS Requirement` | Database planning | `../architecture/DATABASE_DESIGN.md → E-04` |
| DR-06 | Database shall include `Budgets` entity. | `SRS Requirement` | Database planning | `../architecture/DATABASE_DESIGN.md → E-05` |
| DR-07 | Database shall include `SavingsGoals` entity. | `SRS Requirement` | Database planning | `../architecture/DATABASE_DESIGN.md → E-06` |
| DR-08 | Database shall include `Reports` entity. | `SRS Requirement` | Database planning | `../architecture/DATABASE_DESIGN.md → E-07` |
| DR-09 | Database shall include `LearningContent` entity. | `SRS Requirement` | Database planning | `../architecture/DATABASE_DESIGN.md → E-08` |
| DR-10 | Database shall include `Notifications` entity. | `SRS Requirement` | Database planning | `../architecture/DATABASE_DESIGN.md → E-09` |
| DR-11 | Database shall include `SupportQueries` entity. | `SRS Requirement` | Database planning | `../architecture/DATABASE_DESIGN.md → E-10` |
| DR-12 | Specific entity fields | `Derived Design` / `TBD` | Database planning | `../architecture/DATABASE_DESIGN.md` |

Note: The SRS requires Feedback as a feature (`SRS Requirement`) but does **not** list Feedback as a database reference entity. Any Feedback table in the database design is `Derived Design`. Same for ChatMessage.

---

## Interface Requirements

> **Note:** The SRS may specify interface requirements (APIs, external systems). Pending SRS verification.

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| IR-01 | Specific interface requirements | `Assumption` — pending SRS verification | — | `../architecture/TECHNICAL_DESIGN.md` |

---

## Testing Requirements

> **SRS section:** Testing. **Tag:** `SRS Requirement` (existence is mandated; specific tests are `TBD`).

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| TR-01 | The system shall be tested. | `SRS Requirement` | Testing | `../process/TESTING.md` |
| TR-02 | Specific test strategy and coverage | `Derived Design` / `TBD` | Testing | `../process/TESTING.md` |

---

## Installation Requirements

> **SRS section:** Installation. **Tag:** `SRS Requirement` (existence is mandated; specifics are `TBD`).

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| IR-INST-01 | The system shall be installable. | `SRS Requirement` | Installation | `../process/DEPLOYMENT.md` |
| IR-INST-02 | Specific installation method (APK, app store, etc.) | `Assumption` — pending SRS verification | Installation | `../process/DEPLOYMENT.md` |

---

## Responsible AI Usage Requirements

> **SRS section:** Responsible AI usage. **Tag:** `SRS Requirement`.

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| RA-01 | AI is supporting aid rather than a substitute. | `SRS Requirement` | Responsible AI usage | `../architecture/AI_CHATBOT_DESIGN.md` |
| RA-02 | The project must demonstrate meaningful understanding and modification of AI-assisted work. | `SRS Requirement` | Responsible AI usage | `../viva/VIVA_PREPARATION.md` |
| RA-03 | AI-generated documentation is not automatically acceptable for final submission; team review is mandatory. | `SRS Requirement` | Responsible AI usage | `README.md` |
| RA-04 | The team must be able to explain architecture, requirements, design, and implementation during judging. | `SRS Requirement` | Responsible AI usage | `../viva/VIVA_PREPARATION.md` |

---

## Submission Requirements

> **SRS section:** Submission deliverables. **Tag:** `SRS Requirement`.

| Req ID | Requirement | Tag | SRS section | Trace |
|--------|-------------|-----|-------------|-------|
| SR-01 | The submission shall include Credentials. | `SRS Requirement` | Submission | `../viva/SUBMISSION_REQUIREMENTS.md` |
| SR-02 | The submission shall include an APK. | `SRS Requirement` | Submission | `../viva/SUBMISSION_REQUIREMENTS.md` |
| SR-03 | The submission shall include Source code. | `SRS Requirement` | Submission | `../viva/SUBMISSION_REQUIREMENTS.md` |
| SR-04 | The submission shall include a README. | `SRS Requirement` | Submission | Repository README. |
| SR-05 | The submission shall include an MP4 demonstration. | `SRS Requirement` | Submission | `../viva/SUBMISSION_REQUIREMENTS.md` |

---

## Out of Scope

The SRS does not enumerate explicit out-of-scope items. Inferred out-of-scope items are documented in `../LIMITATIONS.md` → *SRS Scope Limitations* with `Assumption` tags pending team verification.

---

## Traceability

For the full bidirectional traceability matrix (requirement ↔ feature ↔ derived design ↔ technical design ↔ test case), see `TRACEABILITY_MATRIX.md`.

---

## Team Action: Verifying This File

1. Walk each `Assumption` tag against the actual SRS. Replace with `SRS Requirement` if confirmed; replace with the correct value if contradicted.
2. For each `TBD` tag, hold the corresponding ADR discussion on Day 1 and resolve to `Team Technical Decision`.
3. Verify that all SRS-mandated features listed in the SRS are present in this document.
4. Update the file status from `Audited` to `SRS-Complete` once all `Assumption` tags are resolved.

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending team verification of `Assumption` items
