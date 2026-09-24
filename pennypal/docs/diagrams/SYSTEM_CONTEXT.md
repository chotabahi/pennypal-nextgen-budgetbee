# System Context Diagram

> **Authority:** SRS user roles (Student, Admin) and SRS-mandated features. This is a C4 Level 1 (System Context) diagram.

---

## Diagram

```mermaid
flowchart TD
    Student["👤 Student<br/>(SRS-mandated role)"]
    Admin["👤 Admin<br/>(SRS-mandated role)"]
    PennyPal["💳 PennyPal System<br/>(Multi-platform personal finance app)"]
    LLM["🤖 External LLM API<br/>(provider TBD per ADR-008 — SRS does not mandate)"]
    Email["📧 Email Service<br/>(for support / notifications; TBD)"]
    Push["📲 Push Notification Service<br/>(TBD per team decision)"]

    Student -->|uses| PennyPal
    Admin -->|manages content, feedback, support, users| PennyPal
    PennyPal -->|sends chatbot queries| LLM
    LLM -->|returns basic financial guidance (supporting aid, not substitute)| PennyPal
    PennyPal -->|sends support / notification emails| Email
    Email -->|delivers| Student
    PennyPal -->|sends notifications| Push
    Push -->|delivers| Student

    style Student fill:#D1E4FF,color:#1A1F2C,stroke:#1F6FEB
    style Admin fill:#D1E4FF,color:#1A1F2C,stroke:#1F6FEB
    style PennyPal fill:#B8E5D9,color:#1A1F2C,stroke:#0E7C66
    style LLM fill:#F5F6F8,color:#1A1F2C,stroke:#D0D5DD
    style Email fill:#F5F6F8,color:#1A1F2C,stroke:#D0D5DD
    style Push fill:#F5F6F8,color:#1A1F2C,stroke:#D0D5DD
```

---

## Description

### Central system: PennyPal

PennyPal is a multi-platform personal finance application for students. `SRS Requirement` (Project scope)

### External actors

| Actor | Description | Tag | SRS section |
|-------|-------------|-----|-------------|
| Student | Primary user; uses all Student-facing features. | `SRS Requirement` | User roles |
| Admin | Secondary user; manages learning content, reviews feedback, handles support queries, manages users. | `SRS Requirement` | User roles |

### External systems

| System | Purpose | Tag | SRS section |
|--------|---------|-----|-------------|
| LLM API | Powers the AI chatbot (F-11). Provider TBD per ADR-008. The SRS does not mandate a specific LLM provider. | `SRS Requirement` (chatbot is mandated); `TBD` (provider) | AI chatbot |
| Email Service | For support / notification emails. Specific service TBD. | `Assumption` — pending SRS verification | Notifications / Contact support |
| Push Notification Service | Delivers push notifications (F-12). Service TBD. | `TBD` | Notifications |

### Key data flows

1. Student uses PennyPal (Dashboard, Income/Expenses, Budgets, Savings, Learning Content, AI Chatbot, Reports, etc.). `SRS Requirement`
2. Admin manages content, reviews feedback, handles support queries. `SRS Requirement` (Admin role)
3. PennyPal calls the LLM API for chatbot queries. `SRS Requirement` (AI chatbot); specific provider `TBD`.
4. PennyPal sends emails / push notifications for relevant events. `SRS Requirement` (Notifications)

### SRS AI restriction (preserved)

The AI chatbot provides **basic financial guidance as supporting aid, not a substitute** for professional advice. `SRS Requirement` (Responsible AI usage)

---

## Out of Scope (Assumption)

- Bank APIs (Plaid, Yodlee, open banking): Not in SRS. `Assumption`
- Payment gateways (Stripe, PayPal): Not in SRS. `Assumption`
- Currency exchange rate APIs: Not in SRS. `Assumption`

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — SRS-mandated actors and features depicted; specific external providers labelled TBD
