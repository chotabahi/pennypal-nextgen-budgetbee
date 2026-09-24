# User Flow Diagram

> **Authority:** SRS-mandated features and use cases. This document shows the primary user flows as flowcharts. For detailed step-by-step descriptions, see `../design/USER_FLOWS.md`.

**Critical distinction:** The flows themselves are `Derived Design` (the team's design to satisfy SRS-mandated capabilities). Specific UI steps are `Derived Design`. SRS-mandated capabilities are tagged `SRS Requirement`.

---

## Flow Inventory

| Flow ID | Flow name | Traces to SRS feature | Status |
|---------|-----------|------------------------|--------|
| UF-01 | Login | F-01 Authentication | `Audited` |
| UF-02 | Dashboard | F-02 Dashboard | `Audited` |
| UF-03 | Add Income/Expense | F-03 Income and expenses | `Audited` |
| UF-06 | Budget | F-06 Budgets | `Audited` |
| UF-07 | Savings Goal | F-07 Savings goals | `Audited` |
| UF-08 | Learning Content | F-08 Learning content | `Audited` |
| UF-11 | AI Chatbot | F-11 AI chatbot | `Audited` |
| UF-14 | Offline Expense + Sync | F-14 Offline + sync | `Audited` |

---

## UF-01: Login (Student / Admin)

```mermaid
flowchart TD
    Start([App Open]) --> Login[Login Screen — Derived Design]
    Login -->|Enter credentials| Submit[Submit]
    Submit --> AuthCheck{Auth OK? — SRS Requirement}
    AuthCheck -->|No| ShowErr[Show Error — Derived Design]
    ShowErr --> Login
    AuthCheck -->|Yes| RoleCheck{Role? — SRS Requirement}
    RoleCheck -->|Student| StudentDashboard[Student Dashboard — Derived Design]
    RoleCheck -->|Admin| AdminDashboard[Admin Dashboard — Derived Design]

    style Start fill:#B8E5D9
    style StudentDashboard fill:#B8E5D9
    style AdminDashboard fill:#B8E5D9
```

`SRS Requirement` — authentication and role-based access are SRS-mandated. Specific screens are `Derived Design`.

---

## UF-02: Dashboard

```mermaid
flowchart TD
    Login[After Login] --> Dashboard[Dashboard — Derived Design]
    Dashboard --> ViewOverview[View financial overview — SRS Requirement]
    Dashboard --> NavigateTo{Navigate to? — Derived Design}
    NavigateTo -->|Transactions| TxnList[Transaction History — Derived Design]
    NavigateTo -->|Add| AddTxn[Add Income/Expense — Derived Design]
    NavigateTo -->|Budgets| Budgets[Budgets — Derived Design]
    NavigateTo -->|Savings| Savings[Savings Goals — Derived Design]
    NavigateTo -->|Learning| Learning[Learning Content — Derived Design]
    NavigateTo -->|Assistant| Chatbot[AI Chatbot — Derived Design]
    NavigateTo -->|Reports| Reports[Reports — Derived Design]

    style Dashboard fill:#B8E5D9
```

`SRS Requirement` — Dashboard is SRS-mandated. Specific contents are `Derived Design`.

---

## UF-03: Add Income/Expense

```mermaid
flowchart TD
    Dashboard[Dashboard] -->|Tap Add| AddForm[Add Income/Expense Form — Derived Design]
    AddForm -->|Select type| Type{Type? — SRS Requirement}
    Type -->|Income| IncomeForm[Income entry — Derived Design]
    Type -->|Expense| ExpenseForm[Expense entry — Derived Design]
    IncomeForm --> EnterAmount[Enter amount — SRS Requirement]
    ExpenseForm --> EnterAmount
    ExpenseForm --> SelectCategory[Select category — SRS Requirement]
    EnterAmount --> Save[Save — SRS Requirement]
    SelectCategory --> Save
    Save --> RecordEntry[Entry recorded — SRS Requirement]

    style Save fill:#B8E5D9
    style RecordEntry fill:#B8E5D9
```

`SRS Requirement` — income and expense entry is SRS-mandated. Specific form is `Derived Design`.

---

## UF-06: Budget

```mermaid
flowchart TD
    Dashboard[Dashboard] -->|Navigate to Budgets| BudgetList[Budget List — Derived Design]
    BudgetList -->|Tap Create| CreateBudget[Create Budget Form — Derived Design]
    CreateBudget --> EnterDetails[Enter amount, period — SRS Requirement]
    EnterDetails --> Save[Save — SRS Requirement]
    Save --> BudgetList
    BudgetList -->|Tap existing| BudgetDetail[Budget Detail — Derived Design]
    BudgetDetail --> ViewProgress[View progress — SRS Requirement]

    style Save fill:#B8E5D9
```

`SRS Requirement` — budgets are SRS-mandated.

---

## UF-07: Savings Goal

```mermaid
flowchart TD
    Dashboard[Dashboard] -->|Navigate to Savings| SavingsList[Savings Goals List — Derived Design]
    SavingsList -->|Tap Create| CreateGoal[Create Goal Form — Derived Design]
    CreateGoal --> EnterDetails[Enter target — SRS Requirement]
    EnterDetails --> Save[Save — SRS Requirement]
    Save --> SavingsList
    SavingsList -->|Tap existing| GoalDetail[Goal Detail — Derived Design]
    GoalDetail --> ViewProgress[View progress — SRS Requirement]

    style Save fill:#B8E5D9
```

`SRS Requirement` — savings goals are SRS-mandated.

---

## UF-08: Learning Content

```mermaid
flowchart TD
    Dashboard[Dashboard] -->|Navigate to Learning| ContentList[Learning Content List — Derived Design]
    ContentList -->|Tap item| ContentDetail[Content Detail — Derived Design]
    ContentDetail -->|Read / watch| FinishContent[Finish]
    FinishContent --> ContentList

    style ContentList fill:#B8E5D9
```

`SRS Requirement` — learning content is SRS-mandated.

---

## UF-11: AI Chatbot

```mermaid
flowchart TD
    Dashboard[Dashboard] -->|Tap Assistant| ChatScreen[Chat Screen — Derived Design]
    ChatScreen -->|Type question| SendMessage[Send — SRS Requirement]
    SendMessage --> ServerCall[Server-side processing — TBD per ADR-008]
    ServerCall --> SafetyCheck{Within scope? — SRS Requirement (supporting aid only)}
    SafetyCheck -->|No — regulated advice| SafetyMsg[Decline; suggest professional — SRS Requirement]
    SafetyCheck -->|Yes — basic guidance| StreamResponse[Provide basic guidance — SRS Requirement]
    StreamResponse --> ShowResponse[Show response — Derived Design]
    ShowResponse --> ChatScreen

    style SendMessage fill:#B8E5D9
    style SafetyMsg fill:#FFCDD2
```

`SRS Requirement` — AI chatbot is SRS-mandated; it provides basic financial guidance as supporting aid, not a substitute. Specific integration is `TBD` per ADR-008.

---

## UF-14: Offline Expense + Sync

```mermaid
flowchart TD
    Offline[User is offline] --> AddExpense[Add Expense — SRS Requirement]
    AddExpense --> SaveLocal[Save to Local DB — SRS Requirement]
    SaveLocal --> UpdateUI[Optimistic UI Update — Derived Design]
    UpdateUI --> WaitForNet{Network?}
    WaitForNet -->|No| Wait[Wait]
    Wait --> WaitForNet
    WaitForNet -->|Yes| SyncStart[Sync Engine pushes — SRS Requirement]
    SyncStart --> SyncOK{Sync OK?}
    SyncOK -->|Yes| Synced[Synced — SRS Requirement]
    SyncOK -->|No, retry| SyncStart

    style Offline fill:#FFE0B2
    style UpdateUI fill:#FFE0B2
    style Synced fill:#B8E5D9
```

`SRS Requirement` — offline expense entry and synchronization are SRS-mandated. Specific sync mechanism is `TBD` per ADR-007.

---

## Combined Primary Flow Map

```mermaid
flowchart LR
    Auth[Login — SRS Requirement] --> Dashboard[Dashboard — SRS Requirement]
    Dashboard --> Txns[Transactions — SRS Requirement]
    Dashboard --> Budgets[Budgets — SRS Requirement]
    Dashboard --> Savings[Savings — SRS Requirement]
    Dashboard --> Learning[Learning — SRS Requirement]
    Dashboard --> Assistant[AI Assistant — SRS Requirement]
    Dashboard --> Reports[Reports — SRS Requirement]
    Dashboard --> Feedback[Feedback — SRS Requirement]
    Dashboard --> Support[Support — SRS Requirement]
    Dashboard --> Notifications[Notifications — SRS Requirement]

    Txns --> AddTxn[Add Income/Expense — SRS Requirement]
    AddTxn --> SyncBackground[Background Sync — SRS Requirement]
    SyncBackground --> Dashboard

    Assistant --> AskQ[Ask Question — SRS Requirement]
    AskQ --> ShowResp[Show Basic Guidance — SRS Requirement (supporting aid)]

    Admin[Admin Login — SRS Requirement] --> AdminPanel[Admin Panel — Derived Design]
    AdminPanel --> ContentMgmt[Content Mgmt — SRS Requirement]
    AdminPanel --> FeedbackReview[Feedback Review — SRS Requirement]
    AdminPanel --> SupportHandling[Support Handling — SRS Requirement]
    AdminPanel --> UserMgmt[User Mgmt — SRS Requirement]

    style Auth fill:#D1E4FF
    style Admin fill:#D1E4FF
    style Dashboard fill:#B8E5D9
    style SyncBackground fill:#FFE0B2
```

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — flows are `Derived Design`; SRS-mandated capabilities tagged `SRS Requirement`
