# ADR-008: AI Chatbot Integration

> **Status:** `TBD` — pending team decision (SRS-mandated requirement)
> **Date:** `[TBD]`
> **Decision Maker:** Team
> **Supersedes:** None
> **Superseded by:** None

## Context

The SRS mandates an AI chatbot that provides basic financial guidance as supporting aid, not a substitute. `SRS Requirement` (AI chatbot, Responsible AI usage)

## SRS constraint

- The system shall provide an AI chatbot. `SRS Requirement`
- The chatbot shall provide basic financial guidance. `SRS Requirement`
- The chatbot is supporting aid, **not a substitute** for professional advice. `SRS Requirement`
- The project must demonstrate meaningful understanding and modification of AI-assisted work. `SRS Requirement` (Responsible AI usage)
- The SRS does **not** specify the integration approach (server-side proxy, on-device LLM, managed service), the LLM provider, the model name, the prompt architecture, the API provider, token limits, vector database, RAG, or agent framework. These are `Team Technical Decision` or `TBD`.

## Options considered

**`[TBD — team to document options considered.]`**

Candidate options for integration approach (pending team decision — **none assumed**):
- Server-side LLM proxy calling a third-party cloud LLM.
- On-device LLM (via Ollama / llama.cpp).
- Managed chatbot service (Dialogflow, Chatbase).

Candidate options for LLM provider (pending team decision — **none assumed**):
- OpenAI
- Anthropic
- Google
- Local
- Other

## Decision

**`TBD`** — team decides on Day 1.

The team decides:
- Integration approach: `[TBD]`
- LLM provider: `[TBD]`
- Safety filtering: `[TBD]`
- Cost control: `[TBD]`

## Reason

**`[TBD — pending decision.]`**

## Consequences

**`[TBD — pending decision.]`**

## References

- `../architecture/AI_CHATBOT_DESIGN.md` (full design)
- `../architecture/SECURITY.md` → *Secrets Management*
- `../product/REQUIREMENTS.md` → FR-AI-01 through FR-AI-05; RA-01 through RA-04

---

**Last updated:** Source-accuracy audit
**Owner:** Team — pending Day 1 decision
