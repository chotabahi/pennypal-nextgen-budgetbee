# Project Plan (Team Project Plan)

> **Authority:** SRS-mandated features and submission deliverables. **The schedule itself is a `Team Project Plan`, not SRS-mandated.** `Team Technical Decision`

This document is the day-by-day execution plan. Every morning, the team opens this document and follows the day's checklist.

**Critical distinction:** The SRS mandates features and deliverables. The SRS does **not** mandate a specific schedule (e.g., 5 days). The schedule below is a `Team Project Plan` — a project-management proposal by the team. `Team Technical Decision`

---

## Guiding Principle

**Tag:** `Team Technical Decision`.

> Build fewer features, but make every feature feel finished.

The SRS mandates 14 features (F-01 through F-14) plus 5 submission deliverables. `SRS Requirement` The team's job is to deliver all of them, polished.

---

## SRS-Mandated Constraints

| Constraint | Value | SRS section / tag |
|------------|-------|-------------------|
| SRS-mandated features | 14 (F-01 through F-14) | `SRS Requirement` |
| Submission deliverables | Credentials, APK, Source code, README, MP4 | `SRS Requirement` |
| Cross-platform compatibility | Yes | `SRS Requirement` |
| Testing | Yes | `SRS Requirement` |
| Installation | Yes | `SRS Requirement` |
| Responsible AI usage | AI is supporting aid; team must demonstrate understanding | `SRS Requirement` |
| Timeline | `[TBD]` | `Assumption` — pending competition rules; **the 5-day schedule below is a `Team Project Plan`, not SRS-mandated.** |
| Team size | `[TBD]` | `Assumption` — pending competition rules |

---

## Day 0 — Pre-Build

**Goal:** Set up the foundation so Day 1 can start coding immediately.

### Checklist

- [ ] All team members have read `README.md` and `DOCUMENTATION_INDEX.md`.
- [ ] All team members have read `docs/product/PRODUCT_OVERVIEW.md` and `docs/product/REQUIREMENTS.md`.
- [ ] All team members have read `docs/architecture/ARCHITECTURE.md` and all ADRs.
- [ ] Team has walked `docs/ASSUMPTIONS.md` and verified items against the SRS.
- [ ] Team has decided on all `TBD` ADRs that can be decided pre-build:
  - ADR-001 (framework)
  - ADR-002 (state management)
  - ADR-003 (navigation)
  - ADR-004 (local storage)
  - ADR-005 (HTTP client)
  - ADR-006 (auth strategy)
  - ADR-007 (sync strategy)
  - ADR-008 (chatbot integration)
- [ ] Repositories created; branch protection configured.
- [ ] `.env.example` files committed.
- [ ] Framework / SDK installed on every team member's machine.
- [ ] Backend stack decided.
- [ ] LLM provider decided (per ADR-008).
- [ ] Communication channel created.
- [ ] Working hours agreed (see `TEAM_WORKFLOW.md`).

### Exit Criteria

- All team members can run the (empty) app locally.
- All team members can run the (empty) backend locally (if applicable).
- Team chat is active; standup time for Day 1 is agreed.

---

## Day 1 — Plan + Design

**Goal:** Decide what to build and how it looks. Do NOT spend Day 1 immediately coding.

### Morning: Requirements + Architecture

- [ ] Walk `docs/product/REQUIREMENTS.md` against the SRS. Update tags (`Assumption` → `SRS Requirement` or `Team Technical Decision`).
- [ ] Finalize feature priorities for the 14 SRS-mandated features.
- [ ] Finalize architecture decisions (all 8 ADRs).
- [ ] Set up the project skeleton.

### Afternoon: UI/UX Design

- [ ] Design the design system (colors, typography, spacing, components).
- [ ] Design the primary screens (S-01 through S-19 per `UI_UX_DESIGN.md`).
- [ ] End-of-day briefing.

### Exit Criteria

- [ ] `REQUIREMENTS.md` is `SRS-Complete` (all `Assumption` items resolved).
- [ ] `DESIGN_SYSTEM.md` is `Team-Reviewed`.
- [ ] `USER_FLOWS.md` has flows for all SRS-mandated use cases (UF-01 through UF-14).
- [ ] Project skeleton compiles and runs.
- [ ] All team members can explain the architecture and design system.

---

## Day 2 — Core Development

**Goal:** Build the foundation and the core SRS-mandated features. End of Day 2: app is navigable end-to-end.

### Morning: Foundation

- [ ] Theme system.
- [ ] Navigation (per ADR-003).
- [ ] Reusable components from design system.

### Afternoon: Core Features

- [ ] F-01 Authentication (Student / Admin roles).
- [ ] F-02 Dashboard.
- [ ] F-03 Income and expenses.
- [ ] End-of-day briefing.

### Exit Criteria

- [ ] App launches, shows login.
- [ ] User can authenticate (Student or Admin).
- [ ] Dashboard renders.
- [ ] User can add income/expense entries.
- [ ] App builds for primary platforms.

---

## Day 3 — Functionality + Backend

**Goal:** Connect to backend. Implement remaining SRS-mandated features.

### Morning: Backend

- [ ] Backend skeleton.
- [ ] Auth endpoints (Student / Admin roles).
- [ ] Sync endpoints (push / pull).

### Afternoon: Features

- [ ] F-04 Expense categories.
- [ ] F-05 Transaction history.
- [ ] F-06 Budgets.
- [ ] F-07 Savings goals.
- [ ] F-14 Offline expense entry and synchronization (per ADR-007).
- [ ] End-of-day briefing.

### Exit Criteria

- [ ] All SRS-mandated features functionally working (rough edges OK).
- [ ] Offline expense entry works; sync works.

---

## Day 4 — Polish + Remaining Features + Testing

**Goal:** Implement remaining SRS-mandated features, fix bugs, polish UX, write tests.

### Morning: Remaining Features

- [ ] F-08 Learning content.
- [ ] F-09 Feedback.
- [ ] F-10 Contact support.
- [ ] F-11 AI chatbot (per ADR-008) — **basic guidance, supporting aid only.**
- [ ] F-12 Notifications.
- [ ] F-13 Reports.
- [ ] Admin features (UF-15, UF-16, UF-17) — `SRS Requirement` (Admin role is SRS-mandated).

### Afternoon: Testing + UX Polish

- [ ] Write tests for every SRS-mandated requirement (per `TESTING.md`).
- [ ] UX polish (animations, states, responsive).
- [ ] Security self-review (per `SECURITY.md`).
- [ ] Smoke test: run the demo script.
- [ ] End-of-day briefing.

### Exit Criteria

- [ ] All 14 SRS-mandated features functionally working.
- [ ] All blocker and high-severity bugs fixed.
- [ ] Test suite passes (`SRS Requirement` — testing is mandated).
- [ ] App builds without errors.
- [ ] Demo script runs without errors.

---

## Day 5 — Freeze + Demo + Submission

**Goal:** Feature freeze, final testing, build SRS-mandated deliverables, demo to judges, viva.

### Morning: Freeze + Build

- [ ] Feature freeze.
- [ ] Final code review.
- [ ] Bump version, tag release.
- [ ] CI builds APK.
- [ ] Record MP4 demonstration (`SRS Requirement`).
- [ ] Prepare Credentials (`SRS Requirement`).
- [ ] Finalize README (`SRS Requirement`).

### Afternoon: Verify + Practice

- [ ] Verify APK on demo device.
- [ ] Make repo public (`SRS Requirement` — source code is a mandated deliverable).
- [ ] Practice the demo.
- [ ] Verify viva prep.

### Pre-Demo

- [ ] Final smoke test.
- [ ] Demo device setup.
- [ ] Team huddle.

### Demo + Viva

- [ ] Demo runs (or fallback to MP4 — `SRS Requirement`).
- [ ] Viva questions answered per `VIVA_PREPARATION.md`.
- [ ] **Team demonstrates meaningful understanding and modification of AI-assisted work** (`SRS Requirement` — Responsible AI usage).
- [ ] Submission per `SUBMISSION_REQUIREMENTS.md`:
  - [ ] Credentials submitted. `SRS Requirement`
  - [ ] APK submitted. `SRS Requirement`
  - [ ] Source code submitted. `SRS Requirement`
  - [ ] README submitted. `SRS Requirement`
  - [ ] MP4 demonstration submitted. `SRS Requirement`

### Post-Demo

- [ ] Debrief.
- [ ] Celebrate.

---

## Risk Buffers

**Tag:** `Team Technical Decision` — `TBD`.

If the team falls behind, cut features aggressively. **However**, SRS-mandated features cannot be cut without honesty in `LIMITATIONS.md`. Ship something polished, not everything broken.

---

## What This Document Does NOT Cover

- **Engineering process** → `DEVELOPMENT_WORKFLOW.md`
- **Team roles and schedule** → `TEAM_WORKFLOW.md`
- **Test strategy** → `TESTING.md`
- **Deployment runbook** → `DEPLOYMENT.md`
- **Viva question bank** → `../viva/VIVA_PREPARATION.md`
- **Presentation script** → `../viva/PRESENTATION.md`
- **Submission requirements** → `../viva/SUBMISSION_REQUIREMENTS.md`

---

## Team Action: Filling In This File

1. **The 5-day schedule is a `Team Project Plan`, not SRS-mandated.** Adjust the day count to match the actual competition timeline.
2. Verify SRS-mandated timeline and team size (Assumption — pending competition rules).
3. The 14 SRS-mandated features must all be addressed by the end of the plan.
4. The 5 SRS-mandated deliverables must all be produced by submission.
5. **Do not claim work is completed unless actually completed.** Update implementation status honestly.
6. Update the file status from `Audited` to `Team-Reviewed`.

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — `Team Project Plan` (not SRS-mandated schedule); pending team verification of timeline and team size
