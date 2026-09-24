# Viva Preparation

> **Authority:** SRS requirements. This document is the **question bank with model answers** for the technical viva.

This document is the team's defence reference for the viva. Every team member must read it in full before the viva. Every model answer must be **SRS-accurate** — no invented answers.

The viva strategy: **no invented answers**. If a judge asks a question not in this bank, the honest answer is: "We didn't explicitly consider that. We would treat it as future work."

**Critical distinction:** Questions are separated into:
- **General Flutter/Dart knowledge** — not project-specific; team should be able to answer from general knowledge.
- **SRS-based PennyPal questions** — project-specific; answers must be supported by the SRS or actual implementation.
- **Architecture / Database / AI / Offline-sync / Testing / Security questions** — project-specific; answers distinguish `SRS Requirement` from `Derived Design` / `Team Technical Decision` / `TBD`.

Project-specific answers must be supported by the SRS or the actual implementation. **If the implementation is not yet known, answer from the SRS requirement and clearly distinguish planned design from implemented behavior.**

---

## 1. Viva Strategy

**Tag:** `Team Technical Decision`.

- One person answers first; others add.
- Cite the documentation (`SRS Requirement`, `Derived Design`, `Team Technical Decision`, `TBD`, ADR-XXX, etc.).
- Be honest about scope (see `LIMITATIONS.md`).
- Be honest about implementation status (see `LIMITATIONS.md` → *Unimplemented Features*).
- Don't bluff. "We didn't consider that" is better than a made-up answer.
- Time management.

### 1.1 Responsible AI usage (SRS-mandated — must be demonstrated)

The SRS mandates that the team must:
- Demonstrate meaningful understanding and modification of AI-assisted work. `SRS Requirement`
- Be able to explain architecture, requirements, design, and implementation during judging. `SRS Requirement`

The team must be prepared to explain **every** part of the project, including parts that were AI-assisted. AI-generated documentation is not automatically acceptable; the team's understanding is mandatory.

---

## 2. Question Bank

> **Note:** Each question's model answer must be SRS-accurate. Model answers cite SRS sections where applicable. Implementation-specific answers are `TBD` until ADRs are decided and implementation is verified.

### 2.1 SRS-Based PennyPal Questions

For each SRS-mandated feature, the viva may ask: "How did you implement requirement `<FR-XX>`?" The model answer cites the SRS section, points to the feature spec, and explains the implementation (distinguishing `SRS Requirement` from `Derived Design` and `TBD`).

| Q ID | Question | Model answer | SRS section | Status |
|------|----------|--------------|-------------|--------|
| Q-SRS-01 | How did you implement authentication? | The SRS mandates authentication with Student and Admin roles. See `FEATURE_SPECIFICATIONS.md → F-01`. Specific auth method is `TBD` per ADR-006. | Authentication, User roles | `Audited` |
| Q-SRS-02 | How does the Dashboard work? | The SRS mandates a Dashboard. See `FEATURE_SPECIFICATIONS.md → F-02`. Specific contents are `Derived Design` pending SRS verification. | Dashboard | `Audited` |
| Q-SRS-03 | How do users record income and expenses? | The SRS mandates income and expense entry. See `FEATURE_SPECIFICATIONS.md → F-03`. | Income and expenses | `Audited` |
| Q-SRS-04 | How are expenses categorized? | The SRS mandates expense categories. See `FEATURE_SPECIFICATIONS.md → F-04`. | Expense categories | `Audited` |
| Q-SRS-05 | How is transaction history maintained? | The SRS mandates transaction history. See `FEATURE_SPECIFICATIONS.md → F-05`. | Transaction history | `Audited` |
| Q-SRS-06 | How do budgets work? | The SRS mandates budgets. See `FEATURE_SPECIFICATIONS.md → F-06`. | Budgets | `Audited` |
| Q-SRS-07 | How do savings goals work? | The SRS mandates savings goals. See `FEATURE_SPECIFICATIONS.md → F-07`. | Savings goals | `Audited` |
| Q-SRS-08 | What is the learning content feature? | The SRS mandates learning content. See `FEATURE_SPECIFICATIONS.md → F-08`. Specific format is `Derived Design`. | Learning content | `Audited` |
| Q-SRS-09 | How does feedback work? | The SRS mandates feedback submission. See `FEATURE_SPECIFICATIONS.md → F-09`. Note: the SRS does **not** list Feedback as a database reference entity; the Feedback table is `Derived Design`. | Feedback | `Audited` |
| Q-SRS-10 | How does contact support work? | The SRS mandates contact support. See `FEATURE_SPECIFICATIONS.md → F-10`. The SRS lists `SupportQueries` as a database reference entity. | Contact support | `Audited` |
| Q-SRS-11 | How does the AI chatbot work? | The SRS mandates an AI chatbot for **basic financial guidance as supporting aid, not a substitute**. See `FEATURE_SPECIFICATIONS.md → F-11` and `AI_CHATBOT_DESIGN.md`. Specific integration is `TBD` per ADR-008. | AI chatbot | `Audited` |
| Q-SRS-12 | How do notifications work? | The SRS mandates notifications. See `FEATURE_SPECIFICATIONS.md → F-12`. Specific triggers are `Derived Design`. | Notifications | `Audited` |
| Q-SRS-13 | How do reports work? | The SRS mandates reports. See `FEATURE_SPECIFICATIONS.md → F-13`. The SRS lists `Reports` as both a feature and a database reference entity. | Reports | `Audited` |
| Q-SRS-14 | How does offline expense entry and synchronization work? | The SRS mandates offline expense entry and synchronization. See `FEATURE_SPECIFICATIONS.md → F-14` and `OFFLINE_SYNC_DESIGN.md`. Specific strategy is `TBD` per ADR-007. **No specific algorithm is claimed.** | Offline + sync | `Audited` |
| Q-SRS-15 | How do you handle Student vs Admin roles? | The SRS mandates Student and Admin roles. Admin features are restricted to Admin users. See `FEATURE_SPECIFICATIONS.md → F-01` and `SECURITY.md`. | User roles | `Audited` |
| Q-SRS-16 | How do you ensure security and privacy? | The SRS mandates security and privacy requirements. See `SECURITY.md`. Specific controls are `Derived Design` / `TBD` pending SRS verification. | Security and privacy | `Audited` |
| Q-SRS-17 | How is the database planned? | The SRS mandates database planning with 10 reference entities: Users, UserProfiles, Transactions, Categories, Budgets, SavingsGoals, Reports, LearningContent, Notifications, SupportQueries. See `DATABASE_DESIGN.md`. Non-SRS entities (Feedback, ChatMessage, SyncQueue) are tagged `Derived Design` or `Team Technical Decision`. | Database planning | `Audited` |
| Q-SRS-18 | How is cross-platform compatibility achieved? | The SRS mandates cross-platform compatibility. See `ADR-001`. Specific framework is `TBD` (SRS does not mandate a specific framework). | Cross-platform | `Audited` |
| Q-SRS-19 | How is the system tested? | The SRS mandates testing. See `TESTING.md`. Test cases are specified; **no test results are fabricated** — all actual results are `Not Yet Verified` until tests are actually run. | Testing | `Audited` |
| Q-SRS-20 | How is the system installed? | The SRS mandates installation. See `DEPLOYMENT.md`. | Installation | `Audited` |
| Q-SRS-21 | What are the submission deliverables? | The SRS mandates: Credentials, APK, Source code, README, MP4. See `SUBMISSION_REQUIREMENTS.md`. | Submission | `Audited` |
| Q-SRS-22 | Is the AI chatbot a substitute for professional advice? | **No.** The SRS specifies the chatbot is supporting aid, **not a substitute**. `SRS Requirement` (Responsible AI usage) | AI chatbot / Responsible AI usage | `Audited` |
| Q-SRS-23 | How did the team ensure meaningful understanding of AI-assisted work? | The SRS mandates that the team demonstrate meaningful understanding and modification of AI-assisted work. The team reviews and understands all documentation and code; AI output is not accepted verbatim. `SRS Requirement` (Responsible AI usage) | Responsible AI usage | `Audited` |

### 2.2 Architecture / ADR Questions

| Q ID | Question | Model answer | Tag | Status |
|------|----------|--------------|-----|--------|
| Q-ARCH-01 | Why did you choose this architecture? | `[TBD — pending ARCHITECTURE.md completion]` | `Team Technical Decision` | `TBD` |
| Q-ARCH-02 | Why did you choose this state management library? | `[TBD — pending ADR-002]` The SRS does not mandate a specific library. | `Team Technical Decision` | `TBD` |
| Q-ARCH-03 | Why this navigation approach? | `[TBD — pending ADR-003]` The SRS does not mandate a specific library. | `Team Technical Decision` | `TBD` |
| Q-ARCH-04 | Why this local storage? | `[TBD — pending ADR-004]` The SRS mandates offline entry; specific storage is `Team Technical Decision`. | `SRS Requirement` (offline); `TBD` (storage) | `TBD` |
| Q-ARCH-05 | Why this HTTP client? | `[TBD — pending ADR-005]` The SRS does not mandate a specific client. | `Team Technical Decision` | `TBD` |
| Q-ARCH-06 | Why this auth strategy? | The SRS mandates auth (Student/Admin roles). Specific method is `TBD` per ADR-006. | `SRS Requirement` (auth); `TBD` (method) | `TBD` |
| Q-ARCH-07 | Why this sync strategy? | The SRS mandates offline expense entry and synchronization. Specific strategy is `TBD` per ADR-007. **No specific algorithm is claimed.** | `SRS Requirement` (sync); `TBD` (strategy) | `TBD` |
| Q-ARCH-08 | Why this chatbot integration? | The SRS mandates an AI chatbot for basic guidance as supporting aid. Specific integration is `TBD` per ADR-008. The SRS does not mandate a specific LLM provider, prompt architecture, RAG, or agent framework. | `SRS Requirement` (chatbot); `TBD` (integration) | `TBD` |

### 2.3 Database Questions

| Q ID | Question | Model answer | Tag | Status |
|------|----------|--------------|-----|--------|
| Q-DB-01 | What database entities does the SRS specify? | The SRS specifies 10 reference entities: Users, UserProfiles, Transactions, Categories, Budgets, SavingsGoals, Reports, LearningContent, Notifications, SupportQueries. See `DATABASE_DESIGN.md` and `ER_DIAGRAM.md`. | `SRS Requirement` | `Audited` |
| Q-DB-02 | Why is there a Feedback table if the SRS doesn't list it as a reference entity? | The SRS mandates the Feedback feature but does not list Feedback as a database reference entity. The Feedback table is `Derived Design` — the team's design to store submitted feedback. | `SRS Requirement` (feature); `Derived Design` (table) | `Audited` |
| Q-DB-03 | Why is there a ChatMessage table? | Same as Q-DB-02 — the SRS mandates the AI chatbot feature but does not list ChatMessage as a database reference entity. The table is `Derived Design`. | `SRS Requirement` (feature); `Derived Design` (table) | `Audited` |
| Q-DB-04 | What specific database technology are you using? | `[TBD — pending ADR-004 (local) and backend stack decision (server)]` The SRS does not mandate a specific technology. | `TBD` | `TBD` |
| Q-DB-05 | What are the specific fields of each entity? | `[TBD — pending SRS attribute verification]` The SRS specifies the 10 reference entities; specific attribute lists are pending SRS verification. | `TBD` | `TBD` |

### 2.4 AI Chatbot Questions

| Q ID | Question | Model answer | Tag | Status |
|------|----------|--------------|-----|--------|
| Q-AI-01 | How does the chatbot work? | The SRS mandates an AI chatbot for basic financial guidance as supporting aid, not a substitute. See `AI_CHATBOT_DESIGN.md`. Specific integration is `TBD` per ADR-008. | `SRS Requirement`; `TBD` | `Audited` |
| Q-AI-02 | Is the chatbot a substitute for professional advice? | **No.** The SRS specifies the chatbot is supporting aid, **not a substitute**. `SRS Requirement` (Responsible AI usage) | `SRS Requirement` | `Audited` |
| Q-AI-03 | What LLM provider are you using? | `[TBD — pending ADR-008]` The SRS does not mandate a specific LLM provider. | `TBD` | `TBD` |
| Q-AI-04 | How do you prevent hallucination? | `[TBD — pending ADR-008 and team design]` The SRS does not specify a hallucination mitigation approach. | `TBD` | `TBD` |
| Q-AI-05 | How do you prevent regulated advice? | The SRS specifies the chatbot is supporting aid, not a substitute. Specific safety filtering is `TBD` per ADR-008. | `SRS Requirement` (restriction); `TBD` (filtering) | `Audited` |
| Q-AI-06 | What if the LLM is down? | `[TBD — pending ADR-008]` | `TBD` | `TBD` |
| Q-AI-07 | How do you control cost? | `[TBD — pending ADR-008 and team design]` The SRS does not specify cost controls. | `TBD` | `TBD` |
| Q-AI-08 | How did the team ensure understanding of AI-assisted work? | The SRS mandates that the team demonstrate meaningful understanding and modification of AI-assisted work. The team reviews and understands all chatbot design and implementation. `SRS Requirement` (Responsible AI usage) | `SRS Requirement` | `Audited` |
| Q-AI-09 | Do you use RAG / vector database / agent framework? | `[TBD — pending ADR-008]` The SRS does not specify RAG, vector database, or agent framework. None are assumed. | `TBD` | `TBD` |

### 2.5 Offline / Sync Questions

| Q ID | Question | Model answer | Tag | Status |
|------|----------|--------------|-----|--------|
| Q-OFF-01 | How does offline mode work? | The SRS mandates offline expense entry. The local DB stores entries while offline; sync engine pushes when online. See `OFFLINE_SYNC_DESIGN.md`. Specific implementation is `TBD` per ADR-007. **No specific algorithm is claimed.** | `SRS Requirement`; `TBD` | `Audited` |
| Q-OFF-02 | What happens if sync fails? | `[TBD — pending ADR-007]` The SRS mandates sync; specific failure handling is `Team Technical Decision`. | `SRS Requirement` (sync); `TBD` (handling) | `TBD` |
| Q-OFF-03 | How are conflicts resolved? | `[TBD — pending ADR-007]` The SRS does not specify a conflict resolution strategy. **No specific strategy is claimed.** | `TBD` | `TBD` |
| Q-OFF-04 | How is sync idempotent? | `[TBD — pending ADR-007]` The SRS mandates sync; idempotency mechanism is `Team Technical Decision`. | `SRS Requirement` (sync); `TBD` (mechanism) | `TBD` |

### 2.6 Testing Questions

| Q ID | Question | Model answer | Tag | Status |
|------|----------|--------------|-----|--------|
| Q-TEST-01 | How is the system tested? | The SRS mandates testing. See `TESTING.md`. Test cases are specified. | `SRS Requirement` | `Audited` |
| Q-TEST-02 | Have all tests passed? | **No test results are claimed.** All actual results are `Not Yet Verified` until tests are actually run. We do not fabricate test results. | `Not Yet Verified` | `Audited` |
| Q-TEST-03 | What is the test coverage? | `[TBD — pending measurement]` Coverage targets are `Team Technical Decision`; measured coverage is recorded only after measurement. **No fabricated numbers.** | `TBD` | `TBD` |

### 2.7 Security Questions

| Q ID | Question | Model answer | Tag | Status |
|------|----------|--------------|-----|--------|
| Q-SEC-01 | Where do you store tokens? | `[TBD — pending SECURITY.md and ADR-006 completion]` The SRS mandates security; specific storage is `Team Technical Decision`. | `SRS Requirement` (security); `TBD` (storage) | `TBD` |
| Q-SEC-02 | How do you protect sensitive information? | The SRS mandates security and privacy. See `SECURITY.md`. Specific controls are `Derived Design` / `TBD`. | `SRS Requirement`; `TBD` | `Audited` |
| Q-SEC-03 | Why shouldn't secrets be hardcoded? | `[TBD]` General security principle. | `Team Technical Decision` | `TBD` |
| Q-SEC-04 | How are passwords stored? | `[TBD — pending ADR-006]` The SRS mandates security; specific hashing is `Team Technical Decision`. | `SRS Requirement` (security); `TBD` (method) | `TBD` |
| Q-SEC-05 | How do you prevent one user from reading another's data? | The SRS mandates role-based access (Student/Admin). Server-side enforcement. See `SECURITY.md`. | `SRS Requirement`; `Team Technical Decision` (enforcement) | `Audited` |

### 2.8 Performance Questions

| Q ID | Question | Model answer | Tag | Status |
|------|----------|--------------|-----|--------|
| Q-PERF-01 | How do you ensure the app is fast? | `[TBD]` Performance targets may be SRS-mandated; specific optimizations are `Team Technical Decision`. **No fabricated performance numbers.** | `TBD` | `TBD` |
| Q-PERF-02 | What are the measured performance numbers? | **None claimed.** Performance is recorded only after measurement. `Not Yet Verified` | `Not Yet Verified` | `Audited` |

### 2.9 General Flutter / Dart Questions (NOT project-specific)

> **Note:** These are general technical knowledge questions, not PennyPal-specific. The team should be able to answer from general Flutter/Dart knowledge. Tag as `Team Technical Decision` (the team's understanding). **These are not SRS-based.**

| Q ID | Question | Model answer | Status |
|------|----------|--------------|--------|
| Q-FLUT-01 | What is a widget? | `[TBD — team to fill in from general Flutter knowledge]` | `TBD` |
| Q-FLUT-02 | StatelessWidget vs StatefulWidget? | `[TBD]` | `TBD` |
| Q-FLUT-03 | What happens when setState() is called? | `[TBD]` | `TBD` |
| Q-FLUT-04 | What is BuildContext? | `[TBD]` | `TBD` |
| Q-FLUT-05 | Why use keys? | `[TBD]` | `TBD` |
| Q-FLUT-06 | What causes unnecessary rebuilds? | `[TBD]` | `TBD` |
| Q-DART-01 | What is null safety? | `[TBD]` | `TBD` |
| Q-DART-02 | Difference between final and const? | `[TBD]` | `TBD` |
| Q-DART-03 | What is a Future? | `[TBD]` | `TBD` |
| Q-DART-04 | What does async/await do? | `[TBD]` | `TBD` |
| Q-DART-05 | Difference between List, Set, and Map? | `[TBD]` | `TBD` |

### 2.10 Project-Specific Questions

| Q ID | Question | Model answer | Tag | Status |
|------|----------|--------------|-----|--------|
| Q-PROJ-01 | Show me where X happens in your code. | `[TBD — pending code implementation]` | (depends on X) | `TBD` |
| Q-PROJ-02 | Why did you build this feature? | Cite `SRS Requirement` and SRS section. | `SRS Requirement` | `Audited` |
| Q-PROJ-03 | What would you do differently with more time? | `[TBD — pending LIMITATIONS.md completion]` | `Team Technical Decision` | `TBD` |
| Q-PROJ-04 | What was the hardest part? | `[TBD]` | `Team Technical Decision` | `TBD` |
| Q-PROJ-05 | How did the team divide the work? | `[TBD — pending TEAM_WORKFLOW.md completion]` | `Team Technical Decision` | `TBD` |
| Q-PROJ-06 | Which SRS features are not yet implemented? | See `LIMITATIONS.md → Unimplemented Features` for an honest status. At submission, this list must be accurate. **Status is only set to a value when actually known.** | `SRS Requirement`; `Not Yet Verified` | `Audited` |
| Q-PROJ-07 | Did you understand and modify the AI-assisted work, or accept it verbatim? | The SRS mandates meaningful understanding and modification. The team reviews, understands, and modifies all AI-assisted work. `SRS Requirement` (Responsible AI usage) | `SRS Requirement` | `Audited` |

### 2.11 Behavioral Questions

| Q ID | Question | Model answer | Tag | Status |
|------|----------|--------------|-----|--------|
| Q-BEH-01 | What did you learn from this project? | `[TBD]` | `Team Technical Decision` | `TBD` |
| Q-BEH-02 | What would you do differently? | `[TBD]` | `Team Technical Decision` | `TBD` |
| Q-BEH-03 | How did you handle disagreements? | `[TBD]` | `Team Technical Decision` | `TBD` |

---

## 3. Question Bank Summary

| Area | Questions | Status |
|------|-----------|--------|
| SRS-based PennyPal questions | 23 | `Audited` (SRS-accurate) |
| Architecture / ADR | 8 | `TBD` (pending ADRs) |
| Database | 5 | `Audited` / `TBD` |
| AI Chatbot | 9 | `Audited` / `TBD` |
| Offline / Sync | 4 | `Audited` / `TBD` |
| Testing | 3 | `Audited` (no fabricated results) |
| Security | 5 | `Audited` / `TBD` |
| Performance | 2 | `Audited` (no fabricated numbers) |
| General Flutter / Dart (NOT project-specific) | 11 | `TBD` (team to fill in) |
| Project-specific | 7 | `Audited` / `TBD` |
| Behavioral | 3 | `TBD` |
| **Total** | **80** | |

---

## 4. Final Viva Tips

**Tag:** `Team Technical Decision`.

1. Breathe.
2. Cite the docs (`SRS Requirement`, `Derived Design`, `Team Technical Decision`, `TBD`, ADR-XXX, etc.).
3. Be honest about what's not implemented (see `LIMITATIONS.md`).
4. Be honest about test results — no fabricated "all tests passed".
5. Be honest about performance — no fabricated numbers.
6. Tag-team.
7. Slow down.
8. **Demonstrate meaningful understanding of AI-assisted work** (`SRS Requirement` — Responsible AI usage).
9. Have fun.

---

## Team Action: Filling In This File

1. The 23 SRS-based questions (Q-SRS-01 through Q-SRS-23) are SRS-accurate.
2. Wait for ADRs to be decided. Fill in architecture question model answers.
3. Fill in Flutter / Dart, security, performance, project, and behavioral questions.
4. **Do not invent model answers.** If an answer depends on an unimplemented feature or undecided ADR, mark `TBD` and say so honestly in the viva.
5. **Do not claim test results, performance numbers, or implementation status that is not actually known.**
6. Update the file status from `Audited` to `SRS-Complete` (for SRS-derived) or `Team-Reviewed` (for team-decided).

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending ADR decisions and team fill-in for non-SRS questions; no fabricated results; SRS AI restriction preserved
