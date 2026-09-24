# UI / UX Design

> **Authority:** SRS user roles (Student, Admin) and SRS-mandated features. This document defines **how users move through PennyPal** and **how the interface is structured**.

This document captures the UX philosophy, information architecture, screen inventory, navigation model, and interaction patterns.

**Critical distinction:** The SRS mandates **capabilities** (e.g., "the system shall allow users to record income and expense entries"). Specific screens, flows, and UI elements are `Derived Design` (the team's design that satisfies the SRS-mandated capability), unless the SRS explicitly names them.

---

## 1. UX Philosophy

> **Tag:** `Team Technical Decision` — UX principles are team decisions, not SRS-derived. The SRS may mandate specific UX requirements; those are tagged `SRS Requirement`.

**`TBD`** — team to decide on Day 1.

Candidate principles (pending team decision):
- Offline-first (supports SRS-mandated offline expense entry).
- Insight over data.
- Honest about scope.
- Speed is a feature.

| Principle | Tag | Rationale |
|-----------|-----|-----------|
| `[TBD]` | `Team Technical Decision` | `[TBD]` |

If the SRS specifies UX principles or usability requirements, paste them here with `SRS Requirement` tags.

---

## 2. Information Architecture

### 2.1 SRS-mandated roles

The SRS specifies two user roles: **Student** and **Admin**. Both are SRS-explicit. `SRS Requirement`

The SRS describes functionality for both Student and Admin roles. The information architecture must distinguish between Student-facing and Admin-facing screens:

- **Student-facing** (per SRS feature list): Dashboard, Income/Expenses, Expense Categories, Transaction History, Budgets, Savings Goals, Learning Content, AI Chatbot, Notifications, Reports, Feedback, Contact Support, plus authentication and offline entry. `SRS Requirement`
- **Admin-facing** (per SRS — Admin role exists and SRS describes Admin functionality): The SRS describes Admin functionality (e.g., managing learning content, reviewing feedback, handling support queries, managing users) where applicable. Specific Admin screens are `Derived Design`.

### 2.2 Top-level navigation

**`TBD`** — pending team decision on navigation approach (ADR-003). The team decides whether to use a bottom nav, side rail, drawer, or other pattern. Tag `Team Technical Decision`.

### 2.3 Screen hierarchy

The screen hierarchy follows from the SRS-mandated features. Each SRS feature produces at least one screen (`Derived Design`).

---

## 3. Screen Inventory

> **Note:** Specific screens are `Derived Design` unless the SRS explicitly names them. The SRS mandates the underlying capabilities; the team designs the screens.

| Screen ID | Screen name | Traces to SRS feature | Screen classification | Status |
|-----------|-------------|------------------------|------------------------|--------|
| S-01 | Login / Authentication | F-01 Authentication | `Derived Design` | `Audited` |
| S-02 | Dashboard | F-02 Dashboard | `Derived Design` | `Audited` |
| S-03 | Add Income / Expense | F-03 Income and expenses | `Derived Design` | `Audited` |
| S-04 | Expense Categories (view/manage) | F-04 Expense categories | `Derived Design` | `Audited` |
| S-05 | Transaction History | F-05 Transaction history | `Derived Design` | `Audited` |
| S-06 | Budgets (view/set) | F-06 Budgets | `Derived Design` | `Audited` |
| S-07 | Savings Goals (view/set) | F-07 Savings goals | `Derived Design` | `Audited` |
| S-08 | Learning Content | F-08 Learning content | `Derived Design` | `Audited` |
| S-09 | Feedback (submit) | F-09 Feedback | `Derived Design` | `Audited` |
| S-10 | Contact Support | F-10 Contact support | `Derived Design` | `Audited` |
| S-11 | AI Chatbot | F-11 AI chatbot | `Derived Design` | `Audited` |
| S-12 | Notifications | F-12 Notifications | `Derived Design` | `Audited` |
| S-13 | Reports | F-13 Reports | `Derived Design` | `Audited` |
| S-14 | Sync Status (offline indicator) | F-14 Offline + sync | `Derived Design` | `Audited` |
| S-15 | Admin: Learning Content Management | F-08 (Admin role — `SRS Requirement`) | `Derived Design` (specific screen) | `Audited` |
| S-16 | Admin: Feedback Review | F-09 (Admin role — `SRS Requirement`) | `Derived Design` (specific screen) | `Audited` |
| S-17 | Admin: Support Request Handling | F-10 (Admin role — `SRS Requirement`) | `Derived Design` (specific screen) | `Audited` |
| S-18 | Admin: User Management | Authentication (Admin role — `SRS Requirement`) | `Derived Design` (specific screen) | `Audited` |
| S-19 | Settings / Profile | (implied by auth) | `Derived Design` | `Audited` |

**Total: 19 screens** (all `Derived Design` — the SRS mandates the capabilities; the screens are the team's design).

### Screen classification recap

- **SRS-Explicit Screen**: A screen the SRS explicitly names. (None currently identified — the SRS does not appear to name specific screens. Pending team verification.)
- **Derived Design**: A screen the team designs to satisfy an SRS-mandated capability. (All 19 screens above.)
- **Team Technical Decision**: A screen the team adds that is not directly traceable to an SRS requirement (e.g., Settings). (S-19 is borderline; tagged `Derived Design` because it's implied by auth.)

---

## 4. Navigation Model

### 4.1 Navigation approach

**Tag:** `TBD` — pending ADR-003.

The navigation library (GoRouter, auto_route, etc.) is a team decision documented in `ADR-003`. Until ADR-003 is decided, this section is `TBD`.

### 4.2 Route table

**`TBD`** — pending screen inventory finalization and ADR-003 decision.

| Route path | Screen | Notes | Tag |
|------------|--------|-------|-----|
| `/login` | S-01 | Auth-gate. | `Derived Design` (route) |
| `/` | S-02 | Dashboard (Student) or Admin dashboard. | `Derived Design` |
| `/transactions/new` | S-03 | Add income/expense. | `Derived Design` |
| `/categories` | S-04 | Expense categories. | `Derived Design` |
| `/transactions` | S-05 | Transaction history. | `Derived Design` |
| `/budgets` | S-06 | Budgets. | `Derived Design` |
| `/savings` | S-07 | Savings goals. | `Derived Design` |
| `/learn` | S-08 | Learning content. | `Derived Design` |
| `/feedback` | S-09 | Feedback. | `Derived Design` |
| `/support` | S-10 | Contact support. | `Derived Design` |
| `/assistant` | S-11 | AI chatbot. | `Derived Design` |
| `/notifications` | S-12 | Notifications. | `Derived Design` |
| `/reports` | S-13 | Reports. | `Derived Design` |
| `/sync` | S-14 | Sync status. | `Derived Design` |
| `/admin/content` | S-15 | Admin: content management. | `Derived Design` |
| `/admin/feedback` | S-16 | Admin: feedback review. | `Derived Design` |
| `/admin/support` | S-17 | Admin: support handling. | `Derived Design` |
| `/admin/users` | S-18 | Admin: user management. | `Derived Design` |
| `/settings` | S-19 | Settings / profile. | `Derived Design` |

Routes themselves are `Derived Design` (the team's design). Auth-gating is `SRS Requirement` (auth is mandated); specific redirect rules are `Team Technical Decision`.

### 4.3 Redirect rules

**`SRS Requirement`** — authentication is SRS-mandated.

- Unauthenticated user hitting any protected route → redirect to `/login`. `SRS Requirement` (auth is mandated); redirect rule is `Team Technical Decision`.
- Student hitting any `/admin/*` route → redirect to `/` with an "access denied" message. `SRS Requirement` (role-based access is mandated); specific behaviour is `Team Technical Decision`.

---

## 5. Interaction Patterns

> **Tag:** `Team Technical Decision` — interaction patterns are team decisions, except where the SRS specifies.

For each interaction pattern, document the team's approach:

| Pattern | Decision | Tag | SRS section (if applicable) |
|---------|----------|-----|------------------------------|
| Optimistic UI | `[TBD]` | `Team Technical Decision` | |
| Skeleton loaders | `[TBD]` | `Team Technical Decision` | |
| Pull-to-refresh | `[TBD]` | `Team Technical Decision` | |
| Empty states | `[TBD]` | `Team Technical Decision` | |
| Error states | `[TBD]` | `Team Technical Decision` | |
| Confirmation dialogs | `[TBD]` | `Team Technical Decision` | |
| Undo toasts | `[TBD]` | `Team Technical Decision` | |
| Inline validation | `[TBD]` | `Team Technical Decision` | |
| Sync indicator | `[TBD]` | `Team Technical Decision` | Required by F-14 (offline + sync). `SRS Requirement` (sync mandated); indicator design `Team Technical Decision` |
| Accessibility | `[TBD]` | `Team Technical Decision` | `[SRS Requirement if SRS specifies]` |

---

## 6. Responsive Design

### 6.1 SRS-mandated platforms

**`SRS Requirement`** — the SRS specifies cross-platform compatibility. The exact target platforms are `Assumption` pending SRS verification.

### 6.2 Breakpoints

**Tag:** `Team Technical Decision` — `TBD`.

If the team adopts specific breakpoints (e.g., 360 dp, 600 dp, 840 dp, 1200 dp), list them here. If the SRS specifies breakpoints, paste them with `SRS Requirement`.

---

## 7. Animation & Motion

**Tag:** `Team Technical Decision` — `TBD`.

If the team adopts motion principles (durations, easing, stagger), list them here. If the SRS specifies motion requirements, paste them with `SRS Requirement`.

---

## 8. Content & Tone

**Tag:** `Team Technical Decision` — `TBD`.

If the team adopts content / tone guidelines, list them here. If the SRS specifies content guidelines (e.g., language), paste them with `SRS Requirement`.

---

## 9. Onboarding

**`Assumption`** — pending SRS verification. If the SRS specifies onboarding requirements, paste them with `SRS Requirement` tag. Otherwise mark as `Team Technical Decision` / `TBD`.

---

## 10. What This Document Does NOT Cover

- **Visual design** (colors, typography, components) → `DESIGN_SYSTEM.md`
- **Step-by-step user flows** → `USER_FLOWS.md`
- **Architecture** → `../architecture/ARCHITECTURE.md`
- **Concrete widget structure** → `../architecture/TECHNICAL_DESIGN.md`

---

## Team Action: Filling In This File

1. The screen inventory (Section 3) is `Derived Design` — the team's design to satisfy SRS-mandated capabilities. Verify the SRS doesn't explicitly name any screens; if it does, upgrade those to `SRS-Explicit Screen`.
2. Admin screens (S-15 through S-18) are `Derived Design` for the specific screens, but the underlying Admin capabilities are `SRS Requirement` (the SRS describes Admin functionality).
3. Decide navigation approach (ADR-003) and fill in Section 4.
4. Decide interaction patterns, breakpoints, motion, content tone (Section 5–8). Tag `Team Technical Decision`.
5. Update the file status from `Audited` to `Team-Reviewed`.

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending team decisions on UI/UX specifics
