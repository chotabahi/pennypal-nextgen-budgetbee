# Technical Design

> **Authority:** Architecture from `ARCHITECTURE.md`. ADRs from `../adr/`. This document defines the **concrete technical design** of PennyPal.

This document is the engineer's view. It translates the abstract architecture into concrete packages, classes, and interfaces. It cannot be completed until the architectural decisions (ADRs) are made.

**Critical distinction:** Specific technologies, packages, endpoints, and DTO fields are `Team Technical Decision` or `TBD` until ADRs are decided. **No specific technology is presented as mandatory.** No APIs, packages, or fields are invented.

---

## 1. Project Structure

> **Tag:** `Team Technical Decision` — `TBD` (pending ADR-001 through ADR-006).

The folder structure depends on the chosen architectural style, state management library, navigation approach, local storage, and HTTP client. Once those ADRs are decided, the folder structure is documented here.

```
[TBD — insert folder tree once ADRs are decided. Tag as Team Technical Decision.]
```

---

## 2. Module Boundaries

> **Tag:** `Team Technical Decision` — `TBD`.

For each module, document its contents, dependencies, and dependents. Module existence is `SRS Requirement` (derived from SRS-mandated features); specific module design is `Team Technical Decision`.

| Module | Contents | Depends on | Depended on by | Tag |
|--------|----------|------------|-----------------|-----|
| Auth module | Login, registration, role checks (Student/Admin). | Domain, Data | UI (login screen) | `SRS Requirement` (auth mandated); `Team Technical Decision` (module design) |
| Dashboard module | Dashboard view (F-02). | Domain, Data | UI | `SRS Requirement`; `Team Technical Decision` |
| Transactions module | Add/edit/view income & expense (F-03, F-05). | Domain, Data | UI, Sync | `SRS Requirement`; `Team Technical Decision` |
| Categories module | Expense categories (F-04). | Domain, Data | UI, Transactions | `SRS Requirement`; `Team Technical Decision` |
| Budgets module | Set/track budgets (F-06). | Domain, Data | UI, Dashboard | `SRS Requirement`; `Team Technical Decision` |
| Savings module | Set/track savings goals (F-07). | Domain, Data | UI, Dashboard | `SRS Requirement`; `Team Technical Decision` |
| Learning module | View/manage learning content (F-08). | Domain, Data | UI | `SRS Requirement`; `Team Technical Decision` |
| Feedback module | Submit/review feedback (F-09). | Domain, Data | UI | `SRS Requirement`; `Team Technical Decision` |
| Support module | Submit/handle support queries (F-10). | Domain, Data | UI | `SRS Requirement`; `Team Technical Decision` |
| Chatbot module | AI chatbot (F-11). | Domain, Data | UI | `SRS Requirement`; `Team Technical Decision` |
| Notifications module | Display notifications (F-12). | Domain, Data | UI | `SRS Requirement`; `Team Technical Decision` |
| Reports module | Generate reports (F-13). | Domain, Data | UI | `SRS Requirement`; `Team Technical Decision` |
| Sync module | Offline entry + synchronization (F-14). | Domain, Data | All write modules | `SRS Requirement`; `Team Technical Decision` |
| Admin module | Admin-only screens (content, feedback, support, users). | All modules | UI | `SRS Requirement` (Admin role); `Team Technical Decision` (specific design) |

---

## 3. Key Interfaces

> **Tag:** `Team Technical Decision` — `TBD`.

For each SRS-mandated feature, the corresponding repository / service interface is documented. Specific method signatures are `TBD` until ADRs are decided.

| Interface | Methods (prose description) | Traces to SRS feature | Tag |
|-----------|------------------------------|------------------------|-----|
| `AuthRepository` | `login`, `logout`, `currentRole`, `watchSession`. | F-01 Authentication | `SRS Requirement` (interface exists); `TBD` (specific method signatures) |
| `TransactionRepository` | `addIncome`, `addExpense`, `getRecent`, `getHistory`, `search`. | F-03, F-05 | `SRS Requirement`; `TBD` |
| `CategoryRepository` | `getAll`, `assign`, `create`. | F-04 | `SRS Requirement`; `TBD` |
| `BudgetRepository` | `create`, `getProgress`, `getAll`. | F-06 | `SRS Requirement`; `TBD` |
| `SavingsGoalRepository` | `create`, `getProgress`, `contribute`. | F-07 | `SRS Requirement`; `TBD` |
| `LearningContentRepository` | `getAll`, `getById`, `create` (Admin), `update` (Admin). | F-08 | `SRS Requirement`; `TBD` |
| `FeedbackRepository` | `submit`, `getAll` (Admin). | F-09 | `SRS Requirement`; `TBD` |
| `SupportQueryRepository` | `submit`, `getAll` (Admin). | F-10 | `SRS Requirement`; `TBD` |
| `ChatRepository` | `send`, `getHistory`. | F-11 | `SRS Requirement`; `TBD` |
| `NotificationRepository` | `getAll`, `markRead`. | F-12 | `SRS Requirement`; `TBD` |
| `ReportsRepository` | `generate` (params TBD). | F-13 | `SRS Requirement`; `TBD` |
| `SyncEngine` | `start`, `stop`, `syncNow`, `watchState`. | F-14 | `SRS Requirement`; `TBD` |

---

## 4. Backend Design

### 4.1 SRS-mandated backend requirements

**`Assumption`** — pending SRS verification. The SRS implies a backend (for sync, AI chatbot, Admin features), but does not explicitly mandate a backend stack.

### 4.2 Backend stack

**Tag:** `TBD` — team decision.

The SRS does **not** mandate a specific backend stack. Candidates (Node.js + Express, Firebase, Supabase, custom, etc.) are `TBD`. **No specific stack is assumed.**

### 4.3 API endpoints

> **Note:** API endpoints are documented here only when they trace to an SRS requirement. Specific endpoint design is `Team Technical Decision` pending backend stack. **No specific endpoints are invented.**

| Endpoint (proposed) | Method | Purpose | Traces to SRS feature | Tag |
|----------|--------|---------|------------------------|-----|
| `/api/auth/login` | POST | User login. | F-01 | `SRS Requirement` (auth mandated); `Team Technical Decision` (endpoint design) |
| `/api/auth/register` | POST | User registration. | F-01 | `Derived Design` — pending SRS verification |
| `/api/transactions` | POST | Add income/expense. | F-03 | `SRS Requirement`; `Team Technical Decision` |
| `/api/transactions` | GET | Get transaction history. | F-05 | `SRS Requirement`; `Team Technical Decision` |
| `/api/categories` | GET | Get categories. | F-04 | `SRS Requirement`; `Team Technical Decision` |
| `/api/budgets` | POST/GET | Set/get budgets. | F-06 | `SRS Requirement`; `Team Technical Decision` |
| `/api/savings` | POST/GET | Set/get savings goals. | F-07 | `SRS Requirement`; `Team Technical Decision` |
| `/api/learning` | GET | Get learning content. | F-08 | `SRS Requirement`; `Team Technical Decision` |
| `/api/learning` | POST/PUT/DELETE | Manage learning content (Admin). | F-08 (Admin) | `SRS Requirement` (Admin role); `Team Technical Decision` |
| `/api/feedback` | POST/GET | Submit/get feedback. | F-09 | `SRS Requirement`; `Team Technical Decision` |
| `/api/support` | POST/GET | Submit/get support queries. | F-10 | `SRS Requirement`; `Team Technical Decision` |
| `/api/chat` | POST | Send chatbot message. | F-11 | `SRS Requirement`; `Team Technical Decision` |
| `/api/notifications` | GET | Get notifications. | F-12 | `SRS Requirement`; `Team Technical Decision` |
| `/api/reports` | GET | Get reports. | F-13 | `SRS Requirement`; `Team Technical Decision` |
| `/api/sync/push` | POST | Push pending changes. | F-14 | `SRS Requirement` (sync mandated); `Team Technical Decision` |
| `/api/sync/pull` | POST | Pull server-side changes. | F-14 | `SRS Requirement` (sync mandated); `Team Technical Decision` |

The exact endpoint design (request/response shape, status codes) is `TBD` pending backend stack and team decision. **No specific endpoint design is invented.**

---

## 5. Data Transfer Objects (DTOs)

> **Tag:** `Team Technical Decision` — `TBD` (pending data model from `DATABASE_DESIGN.md`).

For each SRS-specified entity, document the DTO that mirrors its storage format. DTOs depend on the data model. **No specific DTO fields are invented.**

| DTO | Fields (summary) | Traces to SRS entity | Tag |
|-----|------------------|----------------------|-----|
| `UserDTO` | id, email, role (Student/Admin), ... | Users (SRS reference entity) | `SRS Requirement`; `TBD` (fields) |
| `UserProfileDTO` | userId, ... | UserProfiles (SRS reference entity) | `SRS Requirement`; `TBD` |
| `TransactionDTO` | id, type (income/expense), amount, ... | Transactions (SRS reference entity) | `SRS Requirement`; `TBD` |
| `CategoryDTO` | id, name, ... | Categories (SRS reference entity) | `SRS Requirement`; `TBD` |
| `BudgetDTO` | id, target, ... | Budgets (SRS reference entity) | `SRS Requirement`; `TBD` |
| `SavingsGoalDTO` | id, target, ... | SavingsGoals (SRS reference entity) | `SRS Requirement`; `TBD` |
| `ReportDTO` | id, type, ... | Reports (SRS reference entity) | `SRS Requirement`; `TBD` |
| `LearningContentDTO` | id, title, ... | LearningContent (SRS reference entity) | `SRS Requirement`; `TBD` |
| `NotificationDTO` | id, type, ... | Notifications (SRS reference entity) | `SRS Requirement`; `TBD` |
| `SupportQueryDTO` | id, subject, body, ... | SupportQueries (SRS reference entity) | `SRS Requirement`; `TBD` |
| `FeedbackDTO` | id, userId, text, ... | Feedback (`Derived Design` — not in SRS reference list) | `Derived Design`; `TBD` |
| `ChatMessageDTO` | id, userId, role, content, ... | ChatMessage (`Derived Design` — not in SRS reference list) | `Derived Design`; `TBD` |

---

## 6. Configuration

### 6.1 Environment variables

**`TBD`** — pending backend stack and feature decisions.

| Variable | Purpose | Tag |
|----------|---------|-----|
| `API_BASE_URL` | Backend API URL. | `Team Technical Decision` |
| `[TBD]` | `[TBD]` | `Team Technical Decision` |

### 6.2 Feature flags

**`TBD`** — pending feature decisions.

| Flag | Default | Effect | Tag |
|------|---------|--------|-----|
| `[TBD]` | `[TBD]` | `[TBD]` | `Team Technical Decision` |

---

## 7. Build & Dependency Strategy

### 7.1 Framework version

**Tag:** `Team Technical Decision` — `TBD` (pending ADR-001).

### 7.2 Key dependencies

> **Note:** Dependencies are listed here only after the corresponding ADR is decided. **Do not invent dependencies.**

| Package | Purpose | ADR | Tag |
|---------|---------|-----|-----|
| `[TBD]` | `[TBD]` | `ADR-XXX` | `Team Technical Decision` |

### 7.3 Dependency rules

**Tag:** `Team Technical Decision` — `TBD`.

---

## 8. Performance Strategy

> **Tag:** `Team Technical Decision` — `TBD`, except where the SRS specifies performance requirements.

| Technique | Approach | Tag | SRS section (if applicable) |
|-----------|----------|-----|------------------------------|
| Lazy loading | `[TBD]` | `Team Technical Decision` | `[SRS Requirement if specified]` |
| Indexing | `[TBD]` | `Team Technical Decision` | |
| Caching | `[TBD]` | `Team Technical Decision` | |
| Background work | `[TBD]` | `Team Technical Decision` | `SRS Requirement` (offline sync requires background work) |

---

## 9. Future Integrations (Out of Scope)

> **Tag:** `Assumption` — speculative; not implemented; not in SRS.

| Integration | Purpose | Tag |
|-------------|---------|-----|
| Bank APIs | Automatic transaction import. | `Assumption` (speculative, not in SRS) |
| Currency exchange rate API | Auto FX rates. | `Assumption` |

---

## 10. What This Document Does NOT Cover

- **High-level architecture** → `ARCHITECTURE.md`
- **Data model** → `DATABASE_DESIGN.md`
- **Security** → `SECURITY.md`
- **Why each technology was chosen** → `../adr/`
- **How the team builds and deploys** → `../process/DEPLOYMENT.md`

---

## Team Action: Filling In This File

1. Wait for ADR-001 through ADR-006 to be decided (Day 1).
2. Confirm SRS-mandated features in the module list (Section 2).
3. Fill in interface signatures (Section 3) once ADRs are decided.
4. Decide backend stack (Section 4.2) and fill in endpoint design.
5. Decide DTOs (Section 5) based on `DATABASE_DESIGN.md`.
6. **Do not invent specifics.** If a section depends on an undecided ADR, leave as `TBD`.
7. Update the file status from `Audited` to `Team-Reviewed`.

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending ADR decisions; no invented specifics
