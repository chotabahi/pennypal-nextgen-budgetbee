# Feature Specifications

> **Authority:** SRS functional requirements (in `REQUIREMENTS.md`). This document specifies **how each SRS-mandated feature behaves**.

This document is the **behavioural contract** for every SRS-mandated PennyPal feature.

Each feature spec follows a template. SRS-mandated behaviour is tagged `SRS Requirement`. Specific UI/UX details (screens, flows, components) not in the SRS are tagged `Derived Design`. Specific technology choices are tagged `Team Technical Decision` or `TBD`. Implementation status is `Required by SRS` / `Planned` / `In Development` / `Implemented` / `Tested` / `Verified` / `Not Yet Verified`.

---

## Feature Inventory

The SRS mandates the following 14 user-facing features. Detailed specs follow.

| Feature ID | Feature name | Tag | SRS section |
|------------|--------------|-----|-------------|
| F-01 | Authentication | `SRS Requirement` | Authentication |
| F-02 | Dashboard | `SRS Requirement` | Dashboard |
| F-03 | Income and expenses | `SRS Requirement` | Income and expenses |
| F-04 | Expense categories | `SRS Requirement` | Expense categories |
| F-05 | Transaction history | `SRS Requirement` | Transaction history |
| F-06 | Budgets | `SRS Requirement` | Budgets |
| F-07 | Savings goals | `SRS Requirement` | Savings goals |
| F-08 | Learning content | `SRS Requirement` | Learning content |
| F-09 | Feedback | `SRS Requirement` | Feedback |
| F-10 | Contact support | `SRS Requirement` | Contact support |
| F-11 | AI chatbot (basic guidance; supporting aid) | `SRS Requirement` | AI chatbot |
| F-12 | Notifications | `SRS Requirement` | Notifications |
| F-13 | Reports | `SRS Requirement` | Reports |
| F-14 | Offline expense entry and synchronization | `SRS Requirement` | Offline + sync |

---

## F-01: Authentication

**Traces to:** SRS section "Authentication" and "User roles". `SRS Requirement`

**Overview:**
The SRS mandates that the system shall authenticate users and shall distinguish between Student and Admin roles. `SRS Requirement`

**User stories:**
- As a Student, I want to log in so that I can access my financial data. `Derived Design` (specific story derived from SRS auth requirement)
- As an Admin, I want to log in so that I can access Admin features. `Derived Design`
- As an unauthenticated user, I want to register so that I can become a Student. `Derived Design` — pending SRS verification of registration flow

**Inputs:**
- Authentication credentials (specific method TBD per ADR-006). `TBD`

**Outputs / states:**
- Success: User is authenticated and redirected to their role-appropriate dashboard. `Derived Design` (specific redirect)
- Failure: User remains unauthenticated; error displayed. `Derived Design`

**Business rules:**
- The system shall distinguish between Student and Admin roles. `SRS Requirement`
- Admin features shall be restricted to Admin users. `SRS Requirement`
- Student features shall be restricted to authenticated users. `SRS Requirement`

**Acceptance criteria:**
- Given valid Student credentials, when the user authenticates, then they can access Student features. `SRS Requirement`
- Given valid Admin credentials, when the user authenticates, then they can access Admin features. `SRS Requirement`
- Given invalid credentials, when the user attempts to authenticate, then access is denied. `SRS Requirement`

**Implementation status:** `Required by SRS` — `Not Yet Verified`

**Trace:**
- Requirements: `FR-AUTH-01` through `FR-AUTH-04`.
- Derived design (user flow): `../design/USER_FLOWS.md → UF-01` (login flow).
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-01` (login screen).
- Test case: `../process/TESTING.md → TC-AUTH-01` etc.
- ADR: `ADR-006` (auth strategy — `TBD`).

---

## F-02: Dashboard

**Traces to:** SRS section "Dashboard". `SRS Requirement`

**Overview:**
The SRS mandates that the system shall provide a Dashboard for users. `SRS Requirement`

**User stories:**
- As a Student, I want to see a dashboard so that I have an overview of my financial position. `Derived Design`

**Inputs:**
- None (autonomous view). `Derived Design`

**Outputs / states:**
- Dashboard displays an overview of the user's financial position. `SRS Requirement`
- Specific dashboard contents (balance, recent transactions, budget progress, savings goal progress): `Derived Design` — pending SRS verification.

**Acceptance criteria:**
- Given an authenticated user, when they navigate to the Dashboard, then an overview of their financial position is displayed. `SRS Requirement`

**Implementation status:** `Required by SRS` — `Not Yet Verified`

**Trace:**
- Requirements: `FR-DASH-01`, `FR-DASH-02`.
- Derived design (flow): `../design/USER_FLOWS.md → UF-02`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-02`.
- Test case: `../process/TESTING.md → TC-DASH-01` etc.

---

## F-03: Income and Expenses

**Traces to:** SRS section "Income and expenses". `SRS Requirement`

**Overview:**
The SRS mandates that the system shall allow users to record income and expense entries. `SRS Requirement`

**User stories:**
- As a Student, I want to record an income entry so that my balance reflects it. `Derived Design`
- As a Student, I want to record an expense entry so that my balance reflects it. `Derived Design`
- As a Student, I want to record an expense entry while offline so that I can log it when I have no connectivity. `SRS Requirement` (cross-reference F-14)

**Inputs:**
- Amount. `SRS Requirement`
- Type (income or expense). `SRS Requirement`
- Other fields (date, category, note): `Derived Design` — pending SRS verification.

**Outputs / states:**
- Entry is recorded; balance updates. `Derived Design` (specific update behaviour)
- Offline entry is queued for synchronization (see F-14). `SRS Requirement`

**Business rules:**
- Income entries increase the user's balance. `Derived Design` — pending SRS verification.
- Expense entries decrease the user's balance. `Derived Design` — pending SRS verification.

**Acceptance criteria:**
- Given an authenticated user, when they record an income entry, then it is saved. `SRS Requirement`
- Given an authenticated user, when they record an expense entry, then it is saved. `SRS Requirement`
- Given an authenticated user offline, when they record an expense entry, then it is saved locally for later synchronization. `SRS Requirement`

**Implementation status:** `Required by SRS` — `Not Yet Verified`

**Trace:**
- Requirements: `FR-IE-01` through `FR-IE-05`.
- Derived design (flow): `../design/USER_FLOWS.md → UF-03`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-03`.
- Test case: `../process/TESTING.md → TC-IE-01` etc.

---

## F-04: Expense Categories

**Traces to:** SRS section "Expense categories". `SRS Requirement`

**Overview:**
The SRS mandates that expenses shall be categorized. `SRS Requirement`

**User stories:**
- As a Student, I want to categorize my expenses so that I can see spending by category. `Derived Design`

**Inputs:**
- Category assignment per expense. `SRS Requirement`

**Outputs / states:**
- Expenses are categorized. `SRS Requirement`
- Default category list: `Derived Design` — pending SRS verification.
- Custom category creation: `Derived Design` — pending SRS verification.

**Acceptance criteria:**
- Given an expense entry, when the user assigns a category, then the expense is categorized. `SRS Requirement`

**Implementation status:** `Required by SRS` — `Not Yet Verified`

**Trace:**
- Requirements: `FR-CAT-01` through `FR-CAT-03`.
- Derived design (flow): `../design/USER_FLOWS.md → UF-04`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-04`.
- Test case: `../process/TESTING.md → TC-CAT-01` etc.

---

## F-05: Transaction History

**Traces to:** SRS section "Transaction history". `SRS Requirement`

**Overview:**
The SRS mandates that the system shall maintain a transaction history and allow users to view it. `SRS Requirement`

**User stories:**
- As a Student, I want to view my transaction history so that I can review past activity. `Derived Design`

**Inputs:**
- Optional filters (date range, category, type): `Derived Design` — pending SRS verification.

**Outputs / states:**
- Transaction history is displayed. `SRS Requirement`

**Acceptance criteria:**
- Given an authenticated user, when they navigate to transaction history, then their past transactions are displayed. `SRS Requirement`

**Implementation status:** `Required by SRS` — `Not Yet Verified`

**Trace:**
- Requirements: `FR-TH-01` through `FR-TH-03`.
- Derived design (flow): `../design/USER_FLOWS.md → UF-05`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-05`.
- Test case: `../process/TESTING.md → TC-TH-01` etc.

---

## F-06: Budgets

**Traces to:** SRS section "Budgets". `SRS Requirement`

**Overview:**
The SRS mandates that the system shall allow users to set and track budgets. `SRS Requirement`

**User stories:**
- As a Student, I want to set a budget so that I can control my spending. `Derived Design`
- As a Student, I want to track budget progress so that I know if I'm on track. `Derived Design`

**Inputs:**
- Budget parameters (amount, period, category): `Derived Design` — pending SRS verification.

**Outputs / states:**
- Budget is set; progress is tracked. `SRS Requirement`

**Acceptance criteria:**
- Given an authenticated user, when they set a budget, then it is saved. `SRS Requirement`
- Given an existing budget, when the user views it, then the current progress is displayed. `SRS Requirement`

**Implementation status:** `Required by SRS` — `Not Yet Verified`

**Trace:**
- Requirements: `FR-BUD-01` through `FR-BUD-03`.
- Derived design (flow): `../design/USER_FLOWS.md → UF-06`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-06`.
- Test case: `../process/TESTING.md → TC-BUD-01` etc.

---

## F-07: Savings Goals

**Traces to:** SRS section "Savings goals". `SRS Requirement`

**Overview:**
The SRS mandates that the system shall allow users to set and track savings goals. `SRS Requirement`

**User stories:**
- As a Student, I want to set a savings goal so that I can work toward a target. `Derived Design`
- As a Student, I want to track savings goal progress so that I know how close I am. `Derived Design`

**Inputs:**
- Goal parameters (target amount, deadline, name): `Derived Design` — pending SRS verification.

**Outputs / states:**
- Goal is set; progress is tracked. `SRS Requirement`

**Acceptance criteria:**
- Given an authenticated user, when they set a savings goal, then it is saved. `SRS Requirement`
- Given an existing savings goal, when the user views it, then the current progress is displayed. `SRS Requirement`

**Implementation status:** `Required by SRS` — `Not Yet Verified`

**Trace:**
- Requirements: `FR-SG-01` through `FR-SG-03`.
- Derived design (flow): `../design/USER_FLOWS.md → UF-07`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-07`.
- Test case: `../process/TESTING.md → TC-SG-01` etc.

---

## F-08: Learning Content

**Traces to:** SRS section "Learning content". `SRS Requirement`

**Overview:**
The SRS mandates that the system shall provide learning content to users. `SRS Requirement`

**User stories:**
- As a Student, I want to access learning content so that I can improve my financial literacy. `Derived Design`
- As an Admin, I want to manage learning content so that Students have access to current material. `Derived Design` — pending SRS verification.

**Inputs:**
- Content format (articles, videos, interactive): `Derived Design` — pending SRS verification.

**Outputs / states:**
- Learning content is displayed to Students. `SRS Requirement`
- Admin can manage content: `Derived Design` — pending SRS verification.

**Acceptance criteria:**
- Given an authenticated Student, when they navigate to learning content, then content is displayed. `SRS Requirement`

**Implementation status:** `Required by SRS` — `Not Yet Verified`

**Trace:**
- Requirements: `FR-LC-01` through `FR-LC-03`.
- Derived design (flow): `../design/USER_FLOWS.md → UF-08`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-08`.
- Test case: `../process/TESTING.md → TC-LC-01` etc.

---

## F-09: Feedback

**Traces to:** SRS section "Feedback". `SRS Requirement`

**Overview:**
The SRS mandates that the system shall allow users to submit feedback. `SRS Requirement`

**User stories:**
- As a Student, I want to submit feedback so that I can share my experience. `Derived Design`
- As an Admin, I want to review feedback so that I can act on it. `Derived Design` — pending SRS verification.

**Inputs:**
- Feedback text. `SRS Requirement`
- Other fields (rating, category): `Derived Design` — pending SRS verification.

**Outputs / states:**
- Feedback is submitted. `SRS Requirement`

**Acceptance criteria:**
- Given an authenticated user, when they submit feedback, then it is saved. `SRS Requirement`

**Implementation status:** `Required by SRS` — `Not Yet Verified`

**Trace:**
- Requirements: `FR-FB-01`, `FR-FB-02`.
- Derived design (flow): `../design/USER_FLOWS.md → UF-09`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-09`.
- Test case: `../process/TESTING.md → TC-FB-01` etc.

---

## F-10: Contact Support

**Traces to:** SRS section "Contact support". `SRS Requirement`

**Overview:**
The SRS mandates that the system shall allow users to contact support. `SRS Requirement`

**User stories:**
- As a Student, I want to contact support so that I can get help with issues. `Derived Design`

**Inputs:**
- Support request text. `SRS Requirement`
- Other fields (subject, category): `Derived Design` — pending SRS verification.

**Outputs / states:**
- Support request is submitted. `SRS Requirement`

**Acceptance criteria:**
- Given an authenticated user, when they submit a support request, then it is saved. `SRS Requirement`

**Implementation status:** `Required by SRS` — `Not Yet Verified`

**Trace:**
- Requirements: `FR-CS-01`, `FR-CS-02`.
- Derived design (flow): `../design/USER_FLOWS.md → UF-10`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-10`.
- Test case: `../process/TESTING.md → TC-CS-01` etc.

---

## F-11: AI Chatbot

**Traces to:** SRS section "AI chatbot" and "Responsible AI usage". `SRS Requirement`

**Overview:**
The SRS mandates that the system shall provide an AI chatbot that provides **basic financial guidance as supporting aid, not a substitute** for professional advice. `SRS Requirement`

**User stories:**
- As a Student, I want to ask the AI chatbot a financial question so that I get basic guidance. `Derived Design`

**Inputs:**
- User's question (text). `SRS Requirement`
- Chat history (for context): `Derived Design` — pending SRS verification.

**Outputs / states:**
- Chatbot responds with basic financial guidance. `SRS Requirement`
- Specific response format (citations, suggestions): `Derived Design` — pending SRS verification.

**Business rules:**
- The chatbot shall provide basic financial guidance. `SRS Requirement`
- The chatbot is supporting aid, **not a substitute** for professional advice. `SRS Requirement`
- The team must demonstrate meaningful understanding and modification of AI-assisted work. `SRS Requirement` (Responsible AI usage)
- Specific safety / scope rules (e.g., refusing regulated advice): `Derived Design` / `TBD` — pending team design.

**Acceptance criteria:**
- Given an authenticated user, when they ask the chatbot a question, then the chatbot responds with basic guidance. `SRS Requirement`

**Implementation status:** `Required by SRS` — `Not Yet Verified`

**Trace:**
- Requirements: `FR-AI-01` through `FR-AI-04`; RA-01 through RA-04.
- Derived design (flow): `../design/USER_FLOWS.md → UF-11`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-11`.
- Test case: `../process/TESTING.md → TC-AI-01` etc.
- ADR: `ADR-008` (chatbot integration — `TBD`).

---

## F-12: Notifications

**Traces to:** SRS section "Notifications". `SRS Requirement`

**Overview:**
The SRS mandates that the system shall provide notifications to users. `SRS Requirement`

**User stories:**
- As a Student, I want to receive notifications so that I am informed of relevant events. `Derived Design`

**Inputs:**
- Notification triggers (budget alerts, reminders): `Derived Design` — pending SRS verification.

**Outputs / states:**
- Notifications are delivered to the user. `SRS Requirement`
- Delivery mechanism (push, in-app): `TBD` per team decision.

**Acceptance criteria:**
- Given a notification-triggering event, when it occurs, then the user is notified. `SRS Requirement`

**Implementation status:** `Required by SRS` — `Not Yet Verified`

**Trace:**
- Requirements: `FR-NOT-01`, `FR-NOT-02`.
- Derived design (flow): `../design/USER_FLOWS.md → UF-12`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-12`.
- Test case: `../process/TESTING.md → TC-NOT-01` etc.

---

## F-13: Reports

**Traces to:** SRS section "Reports". `SRS Requirement`

**Overview:**
The SRS mandates that the system shall provide reports to users. `SRS Requirement`

**User stories:**
- As a Student, I want to view reports so that I can analyze my spending. `Derived Design`

**Inputs:**
- Report parameters (period, type): `Derived Design` — pending SRS verification.

**Outputs / states:**
- Reports are displayed. `SRS Requirement`
- Specific report types: `Derived Design` — pending SRS verification.

**Acceptance criteria:**
- Given an authenticated user, when they navigate to reports, then reports are displayed. `SRS Requirement`

**Implementation status:** `Required by SRS` — `Not Yet Verified`

**Trace:**
- Requirements: `FR-REP-01`, `FR-REP-02`.
- Derived design (flow): `../design/USER_FLOWS.md → UF-13`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-13`.
- Test case: `../process/TESTING.md → TC-REP-01` etc.

---

## F-14: Offline Expense Entry and Synchronization

**Traces to:** SRS section "Offline expense entry and synchronization". `SRS Requirement`

**Overview:**
The SRS mandates that the system shall allow users to create expense entries while offline, and shall synchronize offline entries when connectivity returns. `SRS Requirement`

**User stories:**
- As a Student, I want to record an expense while offline so that I can log it immediately. `Derived Design`
- As a Student, I want my offline expenses to synchronize automatically so that my data is consistent across devices. `Derived Design`

**Inputs:**
- Expense entry (per F-03). `SRS Requirement`

**Outputs / states:**
- Offline entry is stored locally. `SRS Requirement`
- When connectivity returns, the entry is synchronized to the server. `SRS Requirement`
- Sync status is visible to the user: `Derived Design` — pending team design.

**Business rules:**
- Offline entries must not be lost if the app is killed or the device reboots. `Derived Design` — pending team design (see `ADR-007`).
- Synchronization must be idempotent: `Derived Design` — pending team design (see `ADR-007`).
- Conflict resolution strategy: `TBD` per `ADR-007`.
- Specific sync algorithm (last-write-wins, CRDTs, etc.): `TBD` per `ADR-007`. **Not invented.**

**Acceptance criteria:**
- Given an authenticated user offline, when they record an expense entry, then it is stored locally. `SRS Requirement`
- Given a locally-stored offline entry, when connectivity returns, then the entry is synchronized to the server. `SRS Requirement`

**Implementation status:** `Required by SRS` — `Not Yet Verified`

**Trace:**
- Requirements: `FR-OFF-01` through `FR-OFF-04`.
- Derived design (flow): `../design/USER_FLOWS.md → UF-14`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-14` (sync status indicator).
- Test case: `../process/TESTING.md → TC-OFF-01` etc.
- ADR: `ADR-004` (local storage — `TBD`), `ADR-007` (sync strategy — `TBD`).

---

## Tagging Rules Recap

- **SRS-derived content** (feature existence, role behaviour, acceptance criteria from SRS): tag `SRS Requirement`.
- **Specific UI/UX details** (screens, flows, components, fields not in SRS): tag `Derived Design`.
- **Concrete implementation choices** (specific widgets, libraries): tag `Implementation Detail` (only when verified from source code) or `Team Technical Decision`.
- **Inferred content** (specific input fields, edge cases not in SRS): tag `Assumption`.
- **Open questions**: tag `TBD`.

---

## Team Action: Verifying This File

1. Walk each `Derived Design` tag against the actual SRS. If the SRS explicitly specifies the design, replace with `SRS Requirement`.
2. Walk each `Assumption` tag against the actual SRS. Replace with `SRS Requirement` if confirmed; replace with the correct value if contradicted.
3. For each `TBD` tag, hold the corresponding ADR discussion and resolve to `Team Technical Decision`.
4. Verify that all SRS-mandated features are covered.
5. Update implementation status (currently `Not Yet Verified`) only when actual status is known.
6. Update the file status from `Audited` to `SRS-Complete`.

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending team verification of `Derived Design` and `Assumption` items
