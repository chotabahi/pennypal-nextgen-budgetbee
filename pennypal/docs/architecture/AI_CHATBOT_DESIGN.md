# AI Chatbot Design

> **Authority:** SRS section "AI chatbot" and "Responsible AI usage". This document is **active** because the SRS mandates an AI chatbot. `SRS Requirement`

This document defines the AI chatbot subsystem of PennyPal.

**Critical distinction:** The SRS mandates **the capability** (an AI chatbot that provides basic financial guidance as supporting aid, not a substitute). Specific LLM provider, model name, prompt architecture, API provider, token limits, vector database, RAG, and agent framework are **not** specified by the SRS — they are `Team Technical Decision` or `TBD`. **Nothing is invented.**

**SRS restriction (must be preserved):** AI is supporting aid rather than a substitute. The project must demonstrate meaningful understanding and modification of AI-assisted work. `SRS Requirement` (Responsible AI usage)

---

## 1. Design Goals

### 1.1 SRS-mandated goals

| Goal | Tag | SRS section |
|------|-----|-------------|
| The system shall provide an AI chatbot. | `SRS Requirement` | AI chatbot |
| The chatbot shall provide basic financial guidance. | `SRS Requirement` | AI chatbot |
| The chatbot is supporting aid, **not a substitute** for professional advice. | `SRS Requirement` | AI chatbot / Responsible AI usage |
| The project must demonstrate meaningful understanding and modification of AI-assisted work. | `SRS Requirement` | Responsible AI usage |
| AI-generated documentation is not automatically acceptable for final submission; team review is mandatory. | `SRS Requirement` | Responsible AI usage |
| The team must be able to explain architecture, requirements, design, and implementation during judging. | `SRS Requirement` | Responsible AI usage |

### 1.2 Team-decided goals

**Tag:** `Team Technical Decision` — `TBD`.

| Goal | Tag | Rationale |
|------|-----|-----------|
| `[TBD]` | `Team Technical Decision` | Pending team adoption. |

Candidate goals (pending team decision):
- Cite sources for numeric answers (if applicable).
- Refuse regulated financial advice (if applicable).
- Cost-capped.
- Fast enough to feel responsive.
- No PII in prompts.

---

## 2. Architecture

**Tag:** `TBD` (pending ADR-008).

The SRS mandates the existence of the chatbot; the integration approach is `Team Technical Decision`.

Candidate architectures (pending team decision — **none assumed**):
- Server-side LLM proxy calling a third-party cloud LLM.
- On-device LLM (via Ollama / llama.cpp).
- Managed chatbot service (Dialogflow, Chatbase).

**The documentation does not state a specific architecture until the team decides via ADR-008.**

---

## 3. Prompt Design

### 3.1 SRS-mandated chatbot behaviour

| Behaviour | Tag | SRS section |
|-----------|-----|-------------|
| The chatbot shall provide basic financial guidance. | `SRS Requirement` | AI chatbot |
| The chatbot is supporting aid, not a substitute. | `SRS Requirement` | AI chatbot / Responsible AI usage |

### 3.2 System prompt

**Tag:** `Team Technical Decision` — `TBD`.

The system prompt is designed by the team. It is documented here once ADR-008 is decided. **No specific prompt architecture is invented.**

### 3.3 User context

**Tag:** `Team Technical Decision` — `TBD`.

The user context (what data the chatbot receives) is designed by the team. **No specific context design is invented.**

### 3.4 What the documentation does NOT claim

The SRS does **not** specify:
- LLM provider. `TBD`
- Model name. `TBD`
- Prompt architecture. `TBD`
- API provider. `TBD`
- Token limits. `TBD`
- Vector database. `TBD`
- RAG (Retrieval-Augmented Generation). `TBD`
- Agent framework. `TBD`

These are `Team Technical Decision` or `TBD` until the team decides via ADR-008. **None are assumed.**

---

## 4. Safety Filtering

### 4.1 SRS-mandated safety requirements

**`SRS Requirement`** — the chatbot is supporting aid, not a substitute. `SRS Requirement` (Responsible AI usage)

The SRS restriction implies the chatbot should not present itself as a substitute for professional advice. Specific safety filter implementation is `Team Technical Decision`.

### 4.2 Safety filter implementation

**Tag:** `Team Technical Decision` — `TBD`.

Candidate layers (pending team decision — **none assumed**):
- Regex filter on user input.
- LLM-based classifier on user input.
- Output filter on LLM response.

**The documentation does not state specific safety filters until the team decides.**

---

## 5. Context Management

**Tag:** `Team Technical Decision` — `TBD`.

- Number of chat turns kept as context: `[TBD]`.
- Context truncation behaviour: `[TBD]`.

---

## 6. Cost Control

**Tag:** `Team Technical Decision` — `TBD`.

- Rate limit: `[TBD]` (if any).
- Budget cap: `[TBD]` (if any).
- Model choice: `[TBD]` (pending LLM provider decision — `TBD` per ADR-008).

---

## 7. Failure Modes

**Tag:** `Team Technical Decision` — `TBD`.

Candidate failure modes (pending team decision — **none assumed**):
- LLM unavailable: graceful degradation.
- LLM slow: timeout + retry.
- Invalid response: retry.
- Hallucinated numbers: mitigation `TBD`.
- Budget exhausted: graceful degradation.
- Rate limit hit: user told when to retry.
- Network error: user told chatbot requires internet.

---

## 8. Data Flow

**`TBD`** — pending SRS-derived chatbot behaviour and ADR-008.

High-level (SRS-derived):
1. User enters a question. `SRS Requirement`
2. System sends the question to the chatbot. `SRS Requirement`
3. Chatbot responds with **basic financial guidance as supporting aid** (not a substitute). `SRS Requirement`

Specific data flow (prompt construction, LLM call, streaming, citation) is `Team Technical Decision` pending ADR-008. **No specific flow is invented.**

---

## 9. Logging & Observability

**Tag:** `Team Technical Decision` — `TBD`.

- What is logged: `[TBD]` (no PII per SRS security requirement).
- Log retention: `[TBD]`.

---

## 10. Testing Strategy

**Tag:** `Team Technical Decision` — `TBD` (pending `../process/TESTING.md`).

Key SRS-derived test scenarios (test cases specified; results `Not Yet Verified`):
- User asks a financial question → chatbot responds with basic guidance. `SRS Requirement`
- Chatbot does not present itself as a substitute for professional advice. `SRS Requirement`
- Specific safety / scope tests: `Derived Design` — pending SRS verification.

**No test results are fabricated.** All test results are `Not Yet Verified` until tests are actually run.

---

## 11. Responsible AI Usage (SRS-mandated — must be preserved)

The SRS mandates the following responsible AI usage requirements. These must be preserved throughout the project:

| Requirement | Tag | SRS section |
|-------------|-----|-------------|
| AI is supporting aid rather than a substitute. | `SRS Requirement` | Responsible AI usage |
| The project must demonstrate meaningful understanding and modification of AI-assisted work. | `SRS Requirement` | Responsible AI usage |
| AI-generated documentation is not automatically acceptable for final submission; team review is mandatory. | `SRS Requirement` | Responsible AI usage |
| The team must be able to explain architecture, requirements, design, and implementation during judging. | `SRS Requirement` | Responsible AI usage |

### 11.1 Team responsibilities

The team must:
- Review and understand the chatbot's design and implementation. `SRS Requirement`
- Be able to explain the chatbot's behaviour, scope, and limitations during judging. `SRS Requirement`
- Demonstrate meaningful modification of any AI-assisted chatbot code or design (not accept AI output verbatim). `SRS Requirement`
- Be honest about the chatbot's capabilities — it is basic financial guidance, supporting aid only. `SRS Requirement`

---

## 12. Viva Defence Summary

> **Note:** Filled in once the chatbot design is complete. Each question must have an honest, SRS-accurate answer.

**`TBD`** — pending chatbot design completion.

Key viva points (SRS-accurate):
- The SRS mandates an AI chatbot that provides basic financial guidance as supporting aid, not a substitute. `SRS Requirement`
- LLM provider and integration approach are `Team Technical Decision` documented in ADR-008. **No specific provider or approach is claimed until the team decides.**
- The team must demonstrate meaningful understanding and modification of AI-assisted work. `SRS Requirement`

---

## 13. What This Document Does NOT Cover

- **Why we chose an LLM-based chatbot** → ADR-008
- **Chat UI design** → `../design/UI_UX_DESIGN.md`
- **Security of the chat API** → `SECURITY.md`

---

## Team Action: Filling In This File

1. The SRS-mandated goals (Section 1.1) and Responsible AI Usage requirements (Section 11) are confirmed.
2. Decide team-decided goals (Section 1.2). Tag `Team Technical Decision`.
3. Wait for ADR-008 (chatbot integration) and LLM provider decision.
4. Fill in the team-decided sections: architecture, prompt design, safety filtering, context management, cost control, failure modes, logging, testing.
5. **Do not invent specifics.** If a section depends on an undecided ADR, leave as `TBD`.
6. **Preserve the SRS AI restriction throughout** — the chatbot is supporting aid, not a substitute; the team must demonstrate understanding and modification.
7. Update the file status from `Audited` to `SRS-Complete` (for SRS-derived parts) or `Team-Reviewed` (for team designs).

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending ADR-008 and LLM provider decision; no invented specifics; SRS AI restriction preserved
