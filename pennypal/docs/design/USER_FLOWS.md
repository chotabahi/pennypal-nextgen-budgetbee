# User Flows

> **Authority:** SRS-mandated features (in `REQUIREMENTS.md`). This document captures the **primary user journeys** through PennyPal.

**Critical distinction:** The SRS mandates **capabilities** (e.g., "the system shall allow users to record income and expense entries"). Specific user flows are `Derived Design` (the team's design that satisfies the SRS-mandated capability), unless the SRS explicitly specifies the flow.

Each SRS-mandated feature produces at least one user flow in this document.

---

## 1. Primary User Flows

The SRS mandates the following features, each producing one or more user flows (the flows themselves are `Derived Design`):

| Flow ID | Flow name | Traces to SRS feature | Flow classification | Status |
|---------|-----------|------------------------|----------------------|--------|
| UF-01 | Login / Authentication | F-01 Authentication | `Derived Design` | `Audited` |
| UF-02 | View Dashboard | F-02 Dashboard | `Derived Design` | `Audited` |
| UF-03 | Add Income / Expense | F-03 Income and expenses | `Derived Design` | `Audited` |
| UF-04 | Manage Expense Categories | F-04 Expense categories | `Derived Design` | `Audited` |
| UF-05 | View Transaction History | F-05 Transaction history | `Derived Design` | `Audited` |
| UF-06 | Set / Track Budget | F-06 Budgets | `Derived Design` | `Audited` |
| UF-07 | Set / Track Savings Goal | F-07 Savings goals | `Derived Design` | `Audited` |
| UF-08 | View Learning Content | F-08 Learning content | `Derived Design` | `Audited` |
| UF-09 | Submit Feedback | F-09 Feedback | `Derived Design` | `Audited` |
| UF-10 | Contact Support | F-10 Contact support | `Derived Design` | `Audited` |
| UF-11 | Ask AI Chatbot | F-11 AI chatbot | `Derived Design` | `Audited` |
| UF-12 | View Notifications | F-12 Notifications | `Derived Design` | `Audited` |
| UF-13 | View Reports | F-13 Reports | `Derived Design` | `Audited` |
| UF-14 | Offline Expense Entry and Sync | F-14 Offline + sync | `Derived Design` | `Audited` |
| UF-15 | Admin: Manage Learning Content | F-08 (Admin role — `SRS Requirement`) | `Derived Design` (specific flow) | `Audited` |
| UF-16 | Admin: Review Feedback | F-09 (Admin role — `SRS Requirement`) | `Derived Design` (specific flow) | `Audited` |
| UF-17 | Admin: Handle Support Requests | F-10 (Admin role — `SRS Requirement`) | `Derived Design` (specific flow) | `Audited` |

---

## 2. Flow Specifications

### UF-01: Login / Authentication

**Traces to:** F-01 Authentication. `SRS Requirement`

**Persona:** Student or Admin (per SRS). `SRS Requirement`

**Preconditions:** User has an account. `Derived Design` — pending SRS verification (registration flow).

**Steps:**
1. User opens the app. `Derived Design` (specific step)
2. User enters credentials. `SRS Requirement` (auth is mandated); specific method `TBD` per ADR-006.
3. System validates credentials and determines role (Student or Admin). `SRS Requirement`
4. System redirects to role-appropriate dashboard. `Derived Design` (specific redirect)

**Alternative flows:**
- Invalid credentials: access denied. `SRS Requirement`

**Postconditions (success):** User is authenticated; role is established. `SRS Requirement`

**Postconditions (failure):** User remains unauthenticated. `SRS Requirement`

**Trace:**
- Feature: `../product/FEATURE_SPECIFICATIONS.md → F-01`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-01`.
- Test case: `../process/TESTING.md → TC-AUTH-01` etc.

---

### UF-02: View Dashboard

**Traces to:** F-02 Dashboard. `SRS Requirement`

**Persona:** Student. `SRS Requirement`

**Preconditions:** User is authenticated. `SRS Requirement`

**Steps:**
1. User navigates to the Dashboard. `Derived Design` (specific navigation)
2. System displays an overview of the user's financial position. `SRS Requirement`
3. Specific dashboard contents (balance, recent transactions, budgets, savings): `Derived Design` — pending SRS verification.

**Postconditions (success):** User sees their dashboard. `SRS Requirement`

**Trace:**
- Feature: `../product/FEATURE_SPECIFICATIONS.md → F-02`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-02`.
- Test case: `../process/TESTING.md → TC-DASH-01`.

---

### UF-03: Add Income / Expense

**Traces to:** F-03 Income and expenses. `SRS Requirement`

**Persona:** Student. `SRS Requirement`

**Preconditions:** User is authenticated. `SRS Requirement`

**Steps:**
1. User selects "Add Income" or "Add Expense". `Derived Design` (specific UI)
2. User enters the amount. `SRS Requirement`
3. User enters other fields (date, category, note): `Derived Design` — pending SRS verification.
4. User saves the entry. `SRS Requirement`
5. System records the entry. `SRS Requirement`

**Alternative flows:**
- User is offline: entry is stored locally for later synchronization (see UF-14). `SRS Requirement`

**Postconditions (success):** Entry is recorded. `SRS Requirement`

**Trace:**
- Feature: `../product/FEATURE_SPECIFICATIONS.md → F-03`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-03`.
- Test case: `../process/TESTING.md → TC-IE-01` etc.

---

### UF-04: Manage Expense Categories

**Traces to:** F-04 Expense categories. `SRS Requirement`

**Persona:** Student. `SRS Requirement`

**Preconditions:** User is authenticated. `SRS Requirement`

**Steps:**
1. User assigns a category to an expense. `SRS Requirement`
2. System stores the category assignment. `SRS Requirement`
3. User can view expenses by category: `Derived Design` — pending SRS verification.

**Postconditions (success):** Expense is categorized. `SRS Requirement`

**Trace:**
- Feature: `../product/FEATURE_SPECIFICATIONS.md → F-04`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-04`.
- Test case: `../process/TESTING.md → TC-CAT-01` etc.

---

### UF-05: View Transaction History

**Traces to:** F-05 Transaction history. `SRS Requirement`

**Persona:** Student. `SRS Requirement`

**Preconditions:** User is authenticated. `SRS Requirement`

**Steps:**
1. User navigates to transaction history. `Derived Design` (specific navigation)
2. System displays the user's past transactions. `SRS Requirement`
3. Optional filters (date range, category, type): `Derived Design` — pending SRS verification.

**Postconditions (success):** User sees their transaction history. `SRS Requirement`

**Trace:**
- Feature: `../product/FEATURE_SPECIFICATIONS.md → F-05`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-05`.
- Test case: `../process/TESTING.md → TC-TH-01` etc.

---

### UF-06: Set / Track Budget

**Traces to:** F-06 Budgets. `SRS Requirement`

**Persona:** Student. `SRS Requirement`

**Preconditions:** User is authenticated. `SRS Requirement`

**Steps:**
1. User creates a budget (parameters: `Derived Design` — pending SRS verification). `SRS Requirement`
2. System saves the budget. `SRS Requirement`
3. User can view budget progress. `SRS Requirement`

**Postconditions (success):** Budget is set; progress is tracked. `SRS Requirement`

**Trace:**
- Feature: `../product/FEATURE_SPECIFICATIONS.md → F-06`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-06`.
- Test case: `../process/TESTING.md → TC-BUD-01` etc.

---

### UF-07: Set / Track Savings Goal

**Traces to:** F-07 Savings goals. `SRS Requirement`

**Persona:** Student. `SRS Requirement`

**Preconditions:** User is authenticated. `SRS Requirement`

**Steps:**
1. User creates a savings goal (parameters: `Derived Design` — pending SRS verification). `SRS Requirement`
2. System saves the goal. `SRS Requirement`
3. User can view savings goal progress. `SRS Requirement`

**Postconditions (success):** Goal is set; progress is tracked. `SRS Requirement`

**Trace:**
- Feature: `../product/FEATURE_SPECIFICATIONS.md → F-07`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-07`.
- Test case: `../process/TESTING.md → TC-SG-01` etc.

---

### UF-08: View Learning Content

**Traces to:** F-08 Learning content. `SRS Requirement`

**Persona:** Student. `SRS Requirement`

**Preconditions:** User is authenticated. `SRS Requirement`

**Steps:**
1. User navigates to learning content. `Derived Design` (specific navigation)
2. System displays learning content. `SRS Requirement`
3. Specific content format (articles, videos): `Derived Design` — pending SRS verification.

**Postconditions (success):** User views learning content. `SRS Requirement`

**Trace:**
- Feature: `../product/FEATURE_SPECIFICATIONS.md → F-08`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-08`.
- Test case: `../process/TESTING.md → TC-LC-01` etc.

---

### UF-09: Submit Feedback

**Traces to:** F-09 Feedback. `SRS Requirement`

**Persona:** Student. `SRS Requirement`

**Preconditions:** User is authenticated. `SRS Requirement`

**Steps:**
1. User navigates to feedback. `Derived Design` (specific navigation)
2. User enters feedback text. `SRS Requirement`
3. User submits the feedback. `SRS Requirement`
4. System saves the feedback. `SRS Requirement`

**Postconditions (success):** Feedback is submitted. `SRS Requirement`

**Trace:**
- Feature: `../product/FEATURE_SPECIFICATIONS.md → F-09`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-09`.
- Test case: `../process/TESTING.md → TC-FB-01` etc.

---

### UF-10: Contact Support

**Traces to:** F-10 Contact support. `SRS Requirement`

**Persona:** Student. `SRS Requirement`

**Preconditions:** User is authenticated. `SRS Requirement`

**Steps:**
1. User navigates to contact support. `Derived Design` (specific navigation)
2. User enters a support request. `SRS Requirement`
3. User submits the request. `SRS Requirement`
4. System saves the support request. `SRS Requirement`

**Postconditions (success):** Support request is submitted. `SRS Requirement`

**Trace:**
- Feature: `../product/FEATURE_SPECIFICATIONS.md → F-10`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-10`.
- Test case: `../process/TESTING.md → TC-CS-01` etc.

---

### UF-11: Ask AI Chatbot

**Traces to:** F-11 AI chatbot. `SRS Requirement`

**Persona:** Student. `SRS Requirement`

**Preconditions:** User is authenticated. `SRS Requirement`

**Steps:**
1. User navigates to the AI chatbot. `Derived Design` (specific navigation)
2. User enters a financial question. `SRS Requirement`
3. System sends the question to the chatbot. `SRS Requirement`
4. Chatbot responds with **basic financial guidance as supporting aid** (not a substitute for professional advice). `SRS Requirement`

**Postconditions (success):** User receives a chatbot response. `SRS Requirement`

**Trace:**
- Feature: `../product/FEATURE_SPECIFICATIONS.md → F-11`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-11`.
- Test case: `../process/TESTING.md → TC-AI-01` etc.
- ADR: `ADR-008` (`TBD`).

---

### UF-12: View Notifications

**Traces to:** F-12 Notifications. `SRS Requirement`

**Persona:** Student. `SRS Requirement`

**Preconditions:** User is authenticated. `SRS Requirement`

**Steps:**
1. A notification-triggering event occurs (specific triggers: `Derived Design` — pending SRS verification). `SRS Requirement`
2. System delivers a notification to the user. `SRS Requirement`
3. User views the notification. `SRS Requirement`

**Postconditions (success):** User is notified. `SRS Requirement`

**Trace:**
- Feature: `../product/FEATURE_SPECIFICATIONS.md → F-12`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-12`.
- Test case: `../process/TESTING.md → TC-NOT-01` etc.

---

### UF-13: View Reports

**Traces to:** F-13 Reports. `SRS Requirement`

**Persona:** Student. `SRS Requirement`

**Preconditions:** User is authenticated. `SRS Requirement`

**Steps:**
1. User navigates to reports. `Derived Design` (specific navigation)
2. System displays reports. `SRS Requirement`
3. Specific report types: `Derived Design` — pending SRS verification.

**Postconditions (success):** User views reports. `SRS Requirement`

**Trace:**
- Feature: `../product/FEATURE_SPECIFICATIONS.md → F-13`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-13`.
- Test case: `../process/TESTING.md → TC-REP-01` etc.

---

### UF-14: Offline Expense Entry and Sync

**Traces to:** F-14 Offline expense entry and synchronization. `SRS Requirement`

**Persona:** Student. `SRS Requirement`

**Preconditions:** User is authenticated; user is offline. `SRS Requirement`

**Steps:**
1. User creates an expense entry while offline. `SRS Requirement`
2. System stores the entry locally. `SRS Requirement`
3. Connectivity returns. `SRS Requirement`
4. System synchronizes the local entry to the server. `SRS Requirement`

**Alternative flows:**
- Conflict during sync: `TBD` per `ADR-007`. **Specific conflict resolution not invented.**
- Sync failure: `TBD` per `ADR-007`.

**Postconditions (success):** Local entry is synchronized to the server. `SRS Requirement`

**Trace:**
- Feature: `../product/FEATURE_SPECIFICATIONS.md → F-14`.
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-14` (sync status).
- Test case: `../process/TESTING.md → TC-OFF-01` etc.
- ADR: `ADR-004` (local storage — `TBD`), `ADR-007` (sync strategy — `TBD`).

---

### UF-15: Admin — Manage Learning Content

**Traces to:** F-08 Learning content (Admin role). `SRS Requirement` (Admin role is SRS-mandated; specific Admin functionality is described in SRS where applicable).

**Persona:** Admin. `SRS Requirement`

**Preconditions:** Admin is authenticated. `SRS Requirement`

**Steps:**
1. Admin navigates to content management. `Derived Design` (specific navigation)
2. Admin creates / edits / deletes learning content. `Derived Design` (specific actions) — pending SRS verification of Admin capabilities.
3. System saves changes; content is available to Students. `Derived Design`

**Postconditions (success):** Learning content is updated. `Derived Design`

**Trace:**
- Feature: `../product/FEATURE_SPECIFICATIONS.md → F-08` (Admin sub-feature).
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-15`.
- Test case: `../process/TESTING.md → TC-LC-04` (Admin).

---

### UF-16: Admin — Review Feedback

**Traces to:** F-09 Feedback (Admin role). `SRS Requirement` (Admin role is SRS-mandated).

**Persona:** Admin. `SRS Requirement`

**Preconditions:** Admin is authenticated. `SRS Requirement`

**Steps:**
1. Admin navigates to feedback review. `Derived Design`
2. Admin views submitted feedback. `Derived Design`
3. Admin acts on feedback (respond, archive): `Derived Design` — pending SRS verification.

**Trace:**
- Feature: `../product/FEATURE_SPECIFICATIONS.md → F-09` (Admin sub-feature).
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-16`.
- Test case: `../process/TESTING.md → TC-FB-03` (Admin).

---

### UF-17: Admin — Handle Support Requests

**Traces to:** F-10 Contact support (Admin role). `SRS Requirement` (Admin role is SRS-mandated).

**Persona:** Admin. `SRS Requirement`

**Preconditions:** Admin is authenticated. `SRS Requirement`

**Steps:**
1. Admin navigates to support requests. `Derived Design`
2. Admin views support requests. `Derived Design`
3. Admin responds to / resolves requests: `Derived Design` — pending SRS verification.

**Trace:**
- Feature: `../product/FEATURE_SPECIFICATIONS.md → F-10` (Admin sub-feature).
- Derived design (screen): `../design/UI_UX_DESIGN.md → S-17`.
- Test case: `../process/TESTING.md → TC-CS-03` (Admin).

---

## 3. Error Flows

> **Note:** Error flows are `Derived Design` (derived from SRS-mandated alternative flows) or `Team Technical Decision`. Specific error handling not in SRS is `TBD`.

| Flow ID | Error scenario | Tag | SRS section (if applicable) |
|---------|----------------|-----|------------------------------|
| EF-01 | Invalid credentials at login. | `SRS Requirement` (auth denied) | Authentication |
| EF-02 | Offline expense entry fails to sync. | `TBD` — pending ADR-007. | |
| EF-03 | AI chatbot unavailable. | `TBD` — pending ADR-008. | |
| EF-04 | Notification delivery failure. | `TBD` — pending team decision. | |
| EF-05 | Local DB corruption. | `TBD` — pending team decision. | |

---

## 4. Cross-cutting Behaviours

These behaviours apply across multiple flows. Most are `Team Technical Decision` unless the SRS specifies.

| Behaviour | Decision | Tag | SRS section (if applicable) |
|-----------|----------|-----|------------------------------|
| Sync indicator | `[TBD]` | `Team Technical Decision` | Required by F-14. `SRS Requirement` (sync mandated); indicator design `Team Technical Decision` |
| Loading indicator | `[TBD]` | `Team Technical Decision` | |
| Empty states | `[TBD]` | `Team Technical Decision` | |
| Error states | `[TBD]` | `Team Technical Decision` | |
| Optimistic UI | `[TBD]` | `Team Technical Decision` | |
| Undo toasts | `[TBD]` | `Team Technical Decision` | |

---

## 5. Flow Test Matrix

Each flow must have at least one end-to-end test. The matrix below maps flows to test cases (defined in `../process/TESTING.md`).

| Flow ID | Flow name | Test case | Status |
|---------|-----------|-----------|--------|
| UF-01 | Login | TC-FLOW-01 | `Audited` |
| UF-02 | Dashboard | TC-FLOW-02 | `Audited` |
| UF-03 | Add Income/Expense | TC-FLOW-03 | `Audited` |
| UF-04 | Categories | TC-FLOW-04 | `Audited` |
| UF-05 | History | TC-FLOW-05 | `Audited` |
| UF-06 | Budgets | TC-FLOW-06 | `Audited` |
| UF-07 | Savings | TC-FLOW-07 | `Audited` |
| UF-08 | Learning | TC-FLOW-08 | `Audited` |
| UF-09 | Feedback | TC-FLOW-09 | `Audited` |
| UF-10 | Support | TC-FLOW-10 | `Audited` |
| UF-11 | Chatbot | TC-FLOW-11 | `Audited` |
| UF-12 | Notifications | TC-FLOW-12 | `Audited` |
| UF-13 | Reports | TC-FLOW-13 | `Audited` |
| UF-14 | Offline + Sync | TC-FLOW-14 | `Audited` |
| UF-15 | Admin: Content | TC-FLOW-15 | `Audited` |
| UF-16 | Admin: Feedback | TC-FLOW-16 | `Audited` |
| UF-17 | Admin: Support | TC-FLOW-17 | `Audited` |

---

## 6. Demo Script

> **Tag:** `Team Technical Decision` — `TBD` until the team selects which flows to demo.

The demo script is a `Team Technical Decision` that selects a subset of primary flows to demonstrate. Suggested flows for the demo (pending team decision):
- UF-01 Login
- UF-02 Dashboard
- UF-03 Add Income/Expense
- UF-14 Offline Expense Entry and Sync
- UF-11 Ask AI Chatbot

The exact demo script is finalized on Day 4 once the implementation is stable.

---

## 7. What This Document Does NOT Cover

- **UX philosophy** → `UI_UX_DESIGN.md`
- **Visual design** → `DESIGN_SYSTEM.md`
- **Architecture** → `../architecture/ARCHITECTURE.md`
- **Test case specifications** → `../process/TESTING.md`

---

## Team Action: Verifying This File

1. The 14 SRS-mandated flows (UF-01 through UF-14) trace to SRS-mandated features. The flows themselves are `Derived Design`.
2. The 3 Admin flows (UF-15 through UF-17) trace to SRS-mandated Admin role; specific Admin functionality is `SRS Requirement` where SRS describes it; specific flows are `Derived Design`.
3. Decide error flows and cross-cutting behaviours (Section 3, 4). Tag `Team Technical Decision` or `TBD`.
4. Update the file status from `Audited` to `SRS-Complete`.

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending team verification of `Derived Design` items
