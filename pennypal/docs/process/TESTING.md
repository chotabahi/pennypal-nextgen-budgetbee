# Testing

> **Authority:** SRS-mandated testing requirements. `SRS Requirement` (Testing) This document defines the test strategy.

The SRS mandates that the system shall be tested. `SRS Requirement` Test cases trace to SRS-mandated requirements (in `REQUIREMENTS.md`).

**Critical distinctions (per audit):**
- **Test Requirement** — what the SRS mandates be tested. `SRS Requirement`
- **Test Case** — a specific test defined in this document. `Derived Design` / `Team Technical Decision`.
- **Test Procedure** — how to run the test. `Team Technical Decision` / `TBD`.
- **Expected Result** — what should happen if the system is correct. `Derived Design` / `SRS Requirement` (where the SRS specifies).
- **Actual Result** — what actually happened when the test was run. **`Not Yet Verified`** at documentation generation time. **Never fabricated.**
- **Test Evidence** — logs, screenshots, etc. **None at documentation generation time.** **Never fabricated.**

**Never convert a planned test into a completed test.** Never write "all tests passed" unless actual evidence exists. Never invent performance measurements, security test results, or screenshots.

---

## 1. Testing Principles

**Tag:** `Team Technical Decision` — `TBD`.

Candidate principles (pending team decision):
- Test the behaviour, not the implementation.
- Tests are first-class citizens.
- Fast tests win.
- Isolate failures.
- Honest about coverage.
- Never fabricate test results.

---

## 2. Test Pyramid

**Tag:** `Team Technical Decision` — `TBD`.

| Layer | Scope | Tools | Speed | Target | Tag |
|-------|-------|-------|-------|--------|-----|
| Unit | `[TBD]` | `[TBD]` | `[TBD]` | `[TBD]` | `Team Technical Decision` |
| Integration | `[TBD]` | `[TBD]` | `[TBD]` | `[TBD]` | `Team Technical Decision` |
| Widget | `[TBD]` | `[TBD]` | `[TBD]` | `[TBD]` | `Team Technical Decision` |
| E2E | `[TBD]` | `[TBD]` | `[TBD]` | `[TBD]` | `Team Technical Decision` |

---

## 3. Test Case Inventory

> **Note:** Each test case traces to an SRS-mandated requirement (via `TRACEABILITY_MATRIX.md`). Test cases are specified; **actual results are `Not Yet Verified`** until tests are actually run.

### Test case ID convention

Test case IDs follow `TC-<AREA>-<NN>` (e.g., `TC-AUTH-01`). Areas correspond to SRS feature groups.

### Test case table

| ID | Description | Traces to requirement | Type | Expected result | Actual result | Status |
|----|-------------|------------------------|------|-----------------|----------------|--------|
| TC-AUTH-01 | Login with valid Student credentials → access Student features. | FR-AUTH-01, FR-AUTH-02, FR-AUTH-04 | `[TBD]` | Student can access Student features. | `Not Yet Verified` | `Audited` |
| TC-AUTH-02 | Login with valid Admin credentials → access Admin features. | FR-AUTH-01, FR-AUTH-02, FR-AUTH-03 | `[TBD]` | Admin can access Admin features. | `Not Yet Verified` | `Audited` |
| TC-AUTH-03 | Student attempts Admin feature → access denied. | FR-AUTH-03 | `[TBD]` | Access denied. | `Not Yet Verified` | `Audited` |
| TC-AUTH-04 | Unauthenticated user attempts protected feature → access denied. | FR-AUTH-04 | `[TBD]` | Access denied. | `Not Yet Verified` | `Audited` |
| TC-AUTH-05 | Specific auth method tests. | FR-AUTH-05 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `TBD` (pending ADR-006) |
| TC-DASH-01 | Authenticated user views Dashboard. | FR-DASH-01 | `[TBD]` | Dashboard displayed. | `Not Yet Verified` | `Audited` |
| TC-DASH-02 | Dashboard contents. | FR-DASH-02 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `Audited` |
| TC-IE-01 | Record income entry. | FR-IE-01 | `[TBD]` | Income entry saved. | `Not Yet Verified` | `Audited` |
| TC-IE-02 | Record expense entry. | FR-IE-02 | `[TBD]` | Expense entry saved. | `Not Yet Verified` | `Audited` |
| TC-IE-03 | Offline expense creation. | FR-IE-03, FR-OFF-01 | `[TBD]` | Entry stored locally. | `Not Yet Verified` | `Audited` |
| TC-IE-04 | Specific entry fields. | FR-IE-04 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `Audited` |
| TC-IE-05 | View / edit / delete entries. | FR-IE-05 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `Audited` |
| TC-CAT-01 | Categorize an expense. | FR-CAT-01 | `[TBD]` | Expense categorized. | `Not Yet Verified` | `Audited` |
| TC-CAT-02 | View expense categories. | FR-CAT-02 | `[TBD]` | Categories displayed. | `Not Yet Verified` | `Audited` |
| TC-CAT-03 | Specific category list. | FR-CAT-03 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `Audited` |
| TC-TH-01 | View transaction history. | FR-TH-01, FR-TH-02 | `[TBD]` | History displayed. | `Not Yet Verified` | `Audited` |
| TC-TH-02 | Specific history features. | FR-TH-03 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `Audited` |
| TC-BUD-01 | Set a budget. | FR-BUD-01 | `[TBD]` | Budget saved. | `Not Yet Verified` | `Audited` |
| TC-BUD-02 | Track budget progress. | FR-BUD-02 | `[TBD]` | Progress displayed. | `Not Yet Verified` | `Audited` |
| TC-BUD-03 | Specific budget features. | FR-BUD-03 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `Audited` |
| TC-SG-01 | Set a savings goal. | FR-SG-01 | `[TBD]` | Goal saved. | `Not Yet Verified` | `Audited` |
| TC-SG-02 | Track savings goal progress. | FR-SG-02 | `[TBD]` | Progress displayed. | `Not Yet Verified` | `Audited` |
| TC-SG-03 | Specific savings features. | FR-SG-03 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `Audited` |
| TC-LC-01 | View learning content. | FR-LC-01 | `[TBD]` | Content displayed. | `Not Yet Verified` | `Audited` |
| TC-LC-02 | Financial-literacy oriented. | FR-LC-02 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `Audited` |
| TC-LC-03 | Specific content format. | FR-LC-03 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `Audited` |
| TC-LC-04 | Admin: manage learning content. | FR-LC-01 (Admin) | `[TBD]` | Content managed. | `Not Yet Verified` | `Audited` |
| TC-FB-01 | Submit feedback. | FR-FB-01 | `[TBD]` | Feedback saved. | `Not Yet Verified` | `Audited` |
| TC-FB-02 | Specific feedback handling. | FR-FB-02 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `Audited` |
| TC-FB-03 | Admin: review feedback. | FR-FB-01 (Admin) | `[TBD]` | Feedback reviewed. | `Not Yet Verified` | `Audited` |
| TC-CS-01 | Submit support query. | FR-CS-01 | `[TBD]` | Query saved. | `Not Yet Verified` | `Audited` |
| TC-CS-02 | Specific support channel. | FR-CS-02 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `Audited` |
| TC-CS-03 | Admin: handle support queries. | FR-CS-01 (Admin) | `[TBD]` | Queries handled. | `Not Yet Verified` | `Audited` |
| TC-AI-01 | Ask chatbot a question → response. | FR-AI-01, FR-AI-02 | `[TBD]` | Chatbot responds with basic guidance. | `Not Yet Verified` | `Audited` |
| TC-AI-02 | Chatbot provides basic financial guidance. | FR-AI-02 | `[TBD]` | Basic guidance provided. | `Not Yet Verified` | `Audited` |
| TC-AI-03 | Chatbot is supporting aid, not substitute. | FR-AI-03 | `[TBD]` | Chatbot does not present as substitute. | `Not Yet Verified` | `Audited` |
| TC-AI-04 | Specific chatbot scope. | FR-AI-04 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `Audited` |
| TC-AI-05 | LLM provider / integration. | FR-AI-05 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `TBD` (pending ADR-008) |
| TC-NOT-01 | Receive notification. | FR-NOT-01 | `[TBD]` | Notification received. | `Not Yet Verified` | `Audited` |
| TC-NOT-02 | Specific notification triggers. | FR-NOT-02 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `Audited` |
| TC-NOT-03 | Notification delivery mechanism. | FR-NOT-03 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `TBD` |
| TC-REP-01 | View reports. | FR-REP-01 | `[TBD]` | Reports displayed. | `Not Yet Verified` | `Audited` |
| TC-REP-02 | Specific report types. | FR-REP-02 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `Audited` |
| TC-OFF-01 | Offline expense entry. | FR-OFF-01 | `[TBD]` | Entry stored locally. | `Not Yet Verified` | `Audited` |
| TC-OFF-02 | Sync when online. | FR-OFF-02 | `[TBD]` | Entry synchronized. | `Not Yet Verified` | `Audited` |
| TC-OFF-03 | Specific sync strategy. | FR-OFF-03 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `TBD` (pending ADR-007) |
| TC-OFF-04 | Local storage. | FR-OFF-04 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `TBD` (pending ADR-004) |
| TC-SEC-01 | Meet SRS security and privacy requirements. | NFR-SEC-01 | `[TBD]` | SRS security requirements met. | `Not Yet Verified` | `Audited` |
| TC-SEC-02 | Specific security controls. | NFR-SEC-02 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `Audited` |
| TC-CP-01 | Run on multiple platforms. | NFR-CP-01 | `[TBD]` | App runs on multiple platforms. | `Not Yet Verified` | `Audited` |
| TC-CP-02 | Specific target platforms. | NFR-CP-02 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `Audited` |
| TC-PERF-01 | Specific performance targets. | NFR-PERF-01 | `[TBD]` | `[TBD]` | `Not Yet Verified` | `Audited` |
| TC-DATA-01 | Database planning. | DR-01 | `[TBD]` | Database planned. | `Not Yet Verified` | `Audited` |
| TC-DATA-02 through TC-DATA-12 | SRS reference entities (Users, UserProfiles, Transactions, Categories, Budgets, SavingsGoals, Reports, LearningContent, Notifications, SupportQueries, fields). | DR-02 through DR-12 | `[TBD]` | Entities present. | `Not Yet Verified` | `Audited` |

### Flow tests

| ID | Description | Traces to flow | Expected result | Actual result | Status |
|----|-------------|----------------|-----------------|----------------|--------|
| TC-FLOW-01 | UF-01: Login. | UF-01 | User logs in. | `Not Yet Verified` | `Audited` |
| TC-FLOW-02 | UF-02: Dashboard. | UF-02 | Dashboard displayed. | `Not Yet Verified` | `Audited` |
| TC-FLOW-03 | UF-03: Add Income/Expense. | UF-03 | Entry saved. | `Not Yet Verified` | `Audited` |
| TC-FLOW-04 | UF-04: Categories. | UF-04 | Expense categorized. | `Not Yet Verified` | `Audited` |
| TC-FLOW-05 | UF-05: History. | UF-05 | History displayed. | `Not Yet Verified` | `Audited` |
| TC-FLOW-06 | UF-06: Budgets. | UF-06 | Budget saved. | `Not Yet Verified` | `Audited` |
| TC-FLOW-07 | UF-07: Savings. | UF-07 | Goal saved. | `Not Yet Verified` | `Audited` |
| TC-FLOW-08 | UF-08: Learning. | UF-08 | Content displayed. | `Not Yet Verified` | `Audited` |
| TC-FLOW-09 | UF-09: Feedback. | UF-09 | Feedback saved. | `Not Yet Verified` | `Audited` |
| TC-FLOW-10 | UF-10: Support. | UF-10 | Query saved. | `Not Yet Verified` | `Audited` |
| TC-FLOW-11 | UF-11: Chatbot. | UF-11 | Chatbot responds. | `Not Yet Verified` | `Audited` |
| TC-FLOW-12 | UF-12: Notifications. | UF-12 | Notification received. | `Not Yet Verified` | `Audited` |
| TC-FLOW-13 | UF-13: Reports. | UF-13 | Reports displayed. | `Not Yet Verified` | `Audited` |
| TC-FLOW-14 | UF-14: Offline + Sync. | UF-14 | Entry synced. | `Not Yet Verified` | `Audited` |
| TC-FLOW-15 | UF-15: Admin Content. | UF-15 | Content managed. | `Not Yet Verified` | `Audited` |
| TC-FLOW-16 | UF-16: Admin Feedback. | UF-16 | Feedback reviewed. | `Not Yet Verified` | `Audited` |
| TC-FLOW-17 | UF-17: Admin Support. | UF-17 | Queries handled. | `Not Yet Verified` | `Audited` |

---

## 4. Test File Organization

**Tag:** `Team Technical Decision` — `TBD`.

---

## 5. Mocking Strategy

**Tag:** `Team Technical Decision` — `TBD`.

---

## 6. Test Data

### 6.1 Fixtures

**Tag:** `Team Technical Decision` — `TBD`.

### 6.2 Builders

**Tag:** `Team Technical Decision` — `TBD`.

### 6.3 Seeded demo data

**Tag:** `Team Technical Decision` — `TBD`.

---

## 7. Test Execution

### 7.1 Local

**Tag:** `Team Technical Decision` — `TBD`.

### 7.2 CI

**Tag:** `Team Technical Decision` — `TBD`.

The SRS mandates testing; CI should run tests. `SRS Requirement`

### 7.3 Manual tests

**Tag:** `Team Technical Decision` — `TBD`.

---

## 8. Bug Tracking

**Tag:** `Team Technical Decision` — `TBD`.

---

## 9. Coverage Targets

**Tag:** `Team Technical Decision` — `TBD`.

| Layer | Target | Tag |
|-------|--------|-----|
| `[TBD]` | `[TBD]` | `Team Technical Decision` |

> **Note:** Coverage targets are aspirational, not SRS-mandated (unless the SRS specifies). **No coverage numbers are fabricated.**

---

## 10. Test Results Log

> **Note:** This section is intentionally empty. Test results are recorded only after tests are actually run. **No fabricated results.**

**At documentation generation time:** No test results exist. All actual results are `Not Yet Verified`.

The team should maintain a separate test-results log (e.g., `test-results.md` in this directory or in CI artifacts) and update it as tests are run. **Never write "all tests passed" without actual evidence.**

### 10.1 What is NOT recorded here

- **No fabricated pass/fail status.** All entries are `Not Yet Verified` until tests are actually run.
- **No fabricated performance measurements.** Performance is recorded only after measurement.
- **No fabricated security test results.** Security tests are recorded only after they are actually run.
- **No screenshots.** Screenshots are evidence; none exist at documentation generation time.

---

## 11. What This Document Does NOT Cover

- **Traceability** → `../product/TRACEABILITY_MATRIX.md`
- **Engineering process** → `DEVELOPMENT_WORKFLOW.md`
- **Project plan** → `PROJECT_PLAN.md`
- **Viva questions about testing** → `../viva/VIVA_PREPARATION.md`

---

## Team Action: Filling In This File

1. Test cases (Section 3) are SRS-derived. Verify against the actual SRS.
2. Decide on testing principles, pyramid, file organization, mocking, fixtures, CI, coverage targets (`Team Technical Decision`).
3. **Do not fabricate test results.** Update Section 10 only after tests are actually run. Use accurate status values: `Not Yet Verified`, `Passed`, `Failed`, `Blocked`, `Skipped`.
4. **Never write "all tests passed" without actual evidence.**
5. Update the file status from `Audited` to `SRS-Complete` (for test cases) or `Team-Reviewed` (for process).

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending team decisions on testing process; all actual results `Not Yet Verified`; no fabricated results
