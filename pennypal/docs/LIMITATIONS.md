# Limitations

> **Authority:** SRS scope (in `product/REQUIREMENTS.md`). Team decisions. This document captures known limitations of PennyPal — things the application does not do, does poorly, or does only under specific conditions.

Every limitation is traceable to either:
- An SRS scope boundary (`SRS Requirement` — the SRS explicitly says PennyPal does NOT do X).
- A team decision based on the build constraint (`Team Technical Decision`).
- A `Derived Design` limitation (follows from SRS but not specified).
- An honest acknowledgment of an unimplemented feature (`Assumption` — not yet implemented).

Do not fabricate limitations. If something is genuinely out of scope per the SRS, document it. If something is in scope but not yet implemented, say so honestly.

---

## 1. SRS Scope Limitations

> **Note:** Limitations in this section are derived from the SRS's scope statement.

The SRS lists the following feature areas as in scope: `SRS Requirement` (Project scope, all feature areas listed in `REQUIREMENTS.md`).

The SRS does **not** enumerate explicit out-of-scope items. The following are therefore inferred as out-of-scope based on the absence from the SRS feature list, tagged `Assumption` pending team confirmation:

| Out-of-scope item | Reason | Tag |
|--------------------|--------|-----|
| Real-money movement (bank integration, P2P transfers, bill pay) | Not in SRS feature list. | `Assumption` |
| Investment / stock / crypto tracking | Not in SRS feature list. | `Assumption` |
| Tax reporting | Not in SRS feature list. | `Assumption` |
| Regulated financial advice | Not in SRS feature list (the chatbot is `SRS Requirement` but bounded by what the SRS specifies — basic financial guidance, supporting aid only). | `Assumption` |
| Multi-tenant / enterprise features (SSO, RBAC beyond Student/Admin) | SRS specifies only Student and Admin roles. | `SRS Requirement` (scope boundary) |
| Localization beyond the SRS-specified language | Not in SRS feature list. | `Assumption` |

The team should walk this list against the actual SRS on Day 1 and update tags accordingly.

---

## 2. Team-Imposed Limitations

> **Note:** Limitations in this section are team decisions based on the build constraint (time, team size, complexity). All are `Team Technical Decision` once decided; until then, `TBD`.

| Limitation | Reason | Tag |
|------------|--------|-----|
| `[TBD — team to enumerate on Day 1]` | Build constraint. | `TBD` |

Candidate team-imposed limitations (pending team decision):
- No real bank integration (out of scope per A1 above).
- No automatic currency exchange rate feed (manual entry only).
- No PDF generation on-device (CSV export only, if reports are exported).
- No multi-region deployment.
- No formal penetration test.
- No bug bounty programme.

---

## 3. Unimplemented Features

> **Note:** This section honestly acknowledges SRS-mandated features that are not yet implemented. Update throughout the build. At submission time, any SRS-mandated feature still listed here is a known gap.

At documentation generation time, **all SRS-mandated features are not yet implemented**. The implementation status will be updated as the build progresses.

Status values used: `Required by SRS`, `Planned`, `In Development`, `Implemented`, `Tested`, `Verified`, `Not Yet Verified`.

| SRS-mandated feature | SRS section | Implementation status | Notes |
|----------------------|-------------|------------------------|-------|
| Authentication (Student / Admin roles) | Authentication / User roles | `Required by SRS` — `Not Yet Verified` | Status to be updated during build. |
| Dashboard | Dashboard | `Required by SRS` — `Not Yet Verified` | |
| Income and expenses | Income and expenses | `Required by SRS` — `Not Yet Verified` | |
| Expense categories | Expense categories | `Required by SRS` — `Not Yet Verified` | |
| Transaction history | Transaction history | `Required by SRS` — `Not Yet Verified` | |
| Budgets | Budgets | `Required by SRS` — `Not Yet Verified` | |
| Savings goals | Savings goals | `Required by SRS` — `Not Yet Verified` | |
| Learning content | Learning content | `Required by SRS` — `Not Yet Verified` | |
| Feedback | Feedback | `Required by SRS` — `Not Yet Verified` | |
| Contact support | Contact support | `Required by SRS` — `Not Yet Verified` | |
| AI chatbot (basic guidance; supporting aid) | AI chatbot | `Required by SRS` — `Not Yet Verified` | |
| Notifications | Notifications | `Required by SRS` — `Not Yet Verified` | |
| Reports | Reports | `Required by SRS` — `Not Yet Verified` | |
| Offline expense entry and synchronization | Offline + sync | `Required by SRS` — `Not Yet Verified` | |
| Security and privacy controls | Security and privacy | `Required by SRS` — `Not Yet Verified` | |
| Cross-platform compatibility | Cross-platform | `Required by SRS` — `Not Yet Verified` | |
| Responsible AI usage (team understanding + modification) | Responsible AI usage | `Required by SRS` — `Not Yet Verified` | Team must demonstrate understanding during judging. |

The team updates the third column to `Planned`, `In Development`, `Implemented`, `Tested`, or `Verified` as the build progresses. **Status is only set to a value when actually known.** At submission, the column must be accurate.

---

## 4. Platform Limitations

### 4.1 SRS-mandated platforms

**`SRS Requirement`** — the SRS specifies cross-platform compatibility. The exact target platforms are `Assumption` pending team verification against the SRS.

| Platform | Priority | SRS clause / tag | Notes |
|----------|----------|-------------------|-------|
| `[TBD — verify against SRS]` | `[TBD]` | `SRS Requirement` (cross-platform compatibility) | |

### 4.2 Platform-specific limitations

**`TBD`** — pending SRS platform list and team verification. Once the target platforms are confirmed, document any platform-specific limitations (e.g., "Web build does not support biometric login") with `Team Technical Decision` tags.

---

## 5. Performance Limitations

> **Note:** Performance targets may be SRS-mandated (in `REQUIREMENTS.md` → Non-Functional Requirements). Measured performance is recorded only after measurement. **No fabricated performance numbers.**

**`TBD`** — pending SRS performance requirements and actual measurement.

| Performance target | SRS-mandated? | Measured value | Status |
|--------------------|---------------|----------------|--------|
| `[TBD]` | `[TBD]` | `Not Yet Verified` | `TBD` |

---

## 6. Security Limitations

> **Note:** Honest acknowledgment that the app's security is not production-grade. The SRS mandates security and privacy requirements; their implementation status is tracked here.

| Limitation | Reason | Tag |
|------------|--------|-----|
| No penetration test | Out of scope for a competition. | `Team Technical Decision` |
| No end-to-end encryption (if SRS does not mandate) | Server must read user data for sync and chatbot. | `Assumption` — pending SRS verification |
| No hardware security module (HSM) | Consumer app; uses platform secure storage. | `Team Technical Decision` |
| No bug bounty programme | Out of scope for a competition. | `Team Technical Decision` |
| No formal incident response plan | Team commits to a 72-hour initial response window during competition. | `Team Technical Decision` |
| Security test results | Not Yet Verified — no test results fabricated. | `Not Yet Verified` |

---

## 7. AI Chatbot Limitations

> **Note:** SRS-mandated chatbot (see `architecture/AI_CHATBOT_DESIGN.md`). The SRS specifies the chatbot provides **basic financial guidance as supporting aid, not a substitute**. Limitations here are honest acknowledgments of what the chatbot cannot do.

| Limitation | Reason | Tag |
|------------|--------|-----|
| Chatbot is supporting aid, not a substitute for professional advice | SRS restriction. | `SRS Requirement` |
| Chatbot provides basic financial guidance only | SRS restriction. | `SRS Requirement` |
| Specific LLM provider / model | Not specified by SRS; team decides via ADR-008. | `TBD` |
| No real-time data awareness (chatbot receives snapshot) | `Derived Design` — pending team design | `Derived Design` |
| No multi-turn reasoning beyond context window | `Derived Design` — limited by LLM token budget | `Derived Design` |
| No support for images or voice | `TBD` — pending team decision | `TBD` |
| Hallucination risk | LLM may produce incorrect numbers. Mitigation `TBD` per ADR-008. | `TBD` |
| Latency on first message | LLM call latency. `TBD` per ADR-008. | `TBD` |

---

## 8. Operational Limitations

**`Team Technical Decision`** / **`TBD`** — pending backend stack decision.

| Limitation | Reason | Tag |
|------------|--------|-----|
| No 24/7 uptime guarantee | Single-region deployment (`Assumption`). | `Team Technical Decision` |
| No multi-region deployment | Simplicity and budget (`Assumption`). | `Team Technical Decision` |
| No automated rollback | Manual rollback (`Assumption`). | `Team Technical Decision` |
| LLM API cost ceiling | Fixed budget for the competition (`Assumption`). | `Team Technical Decision` |

---

## 9. Documentation Limitations

### 9.1 SRS verification status

**`Audited`** — SRS-mandated content has been transcribed and audited. Technical implementation choices remain `TBD` until ADRs are decided. `Assumption` items remain pending team verification.

### 9.2 No fabricated implementation results

This documentation does **not** claim any implementation results (test pass/fail, performance numbers, screenshots, credentials, security test results). All such results are `Not Yet Verified` until the implementation actually produces them.

### 9.3 No live architecture diagrams

Diagrams in `docs/diagrams/` are Mermaid source — they render on GitHub but are not auto-generated from the codebase. If the code drifts from the diagrams, the diagrams must be updated manually.

### 9.4 AI-assisted documentation

Per SRS, this documentation was AI-assisted and is **not** automatically acceptable for final submission. The team must review, understand, and meaningfully modify it before submission. `SRS Requirement` (Responsible AI usage)

---

## 10. Competition-Specific Limitations

**`Team Technical Decision`** / **`Assumption`**.

| Limitation | Reason | Tag |
|------------|--------|-----|
| No post-competition maintenance commitment | Competition submission. | `Team Technical Decision` |
| Demo data dependency | Demo may rely on seeded data. | `Team Technical Decision` |
| No localization beyond SRS-specified language | Out of scope. | `Assumption` |
| Five-day schedule is a Team Project Plan, not SRS-mandated | Schedule is team-proposed. | `Team Technical Decision` |

---

## 11. How to Use This Document in the Viva

If a judge asks "why doesn't PennyPal do X?":
1. Check this file first.
2. If the limitation is listed here, cite it: "We considered X, and we made a deliberate scope decision. The reasoning is in `LIMITATIONS.md` section N."
3. If the limitation is not listed, the honest answer is: "That's a fair question. We didn't explicitly consider X. We would treat it as future work."

Do not invent justifications on the spot. Judges can tell.

---

## Team Action: Maintaining This File

1. On Day 1, walk Section 1 (SRS scope) against the actual SRS and confirm tags.
2. On Day 1, decide Section 2 (team-imposed limitations) and tag `Team Technical Decision`.
3. **Throughout the build**, update Section 3 (Unimplemented Features) as features are completed. Use accurate status values: `Required by SRS`, `Planned`, `In Development`, `Implemented`, `Tested`, `Verified`, `Not Yet Verified`.
4. On Day 4, walk Section 3 and ensure it accurately reflects the implementation status.
5. At submission, Section 3 must be accurate — any SRS-mandated feature still listed as `Not Yet Verified` is a known gap that the team must be honest about in the viva.

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending team decisions and implementation progress
