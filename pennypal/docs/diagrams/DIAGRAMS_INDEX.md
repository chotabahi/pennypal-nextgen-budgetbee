# Diagrams Index

> **Authority:** SRS-mandated features and roles.

All diagrams use Mermaid syntax and render natively on GitHub.

**Audit note:** All diagrams have been audited. Diagrams distinguish `SRS Requirement` (SRS-mandated) from `Derived Design` (team's design) and `TBD` (pending team decision). No speculative technologies are presented as mandatory.

---

## Diagram Inventory

| Diagram | File | Type | Shows | Status |
|---------|------|------|-------|--------|
| System Context | [SYSTEM_CONTEXT.md](SYSTEM_CONTEXT.md) | C4 Level 1 | PennyPal in its environment (Student, Admin, AI supporting aid). | `Audited` |
| Architecture | [ARCHITECTURE_DIAGRAM.md](ARCHITECTURE_DIAGRAM.md) | C4 Level 2 | Internal layering. Specific tech labelled `TBD`. | `Audited` |
| Data Flow | [DATA_FLOW.md](DATA_FLOW.md) | Sequence | How data flows. Flow specifics are `Derived Design`. | `Audited` |
| ER Diagram | [ER_DIAGRAM.md](ER_DIAGRAM.md) | ER | SRS reference entities (10) + team-added entities (labelled `Derived Design` / `Team Technical Decision`). | `Audited` |
| User Flow | [USER_FLOW.md](USER_FLOW.md) | Flowchart | User journeys. Flows are `Derived Design`. | `Audited` |
| Deployment | [DEPLOYMENT.md](DEPLOYMENT.md) | Deployment | Deployment topology. Specific tech `TBD`. | `Audited` |

---

## How to View

- **On GitHub:** Mermaid renders automatically in `.md` files.
- **In VS Code:** Install "Markdown Preview Mermaid Support".
- **Standalone:** Paste Mermaid code into [mermaid.live](https://mermaid.live).

---

## Diagram Conventions

- All nodes and edges have labels.
- Colors (where Mermaid supports styling): green = SRS-mandated, blue = actor, red = error, grey = external / TBD.
- Each diagram includes a "See also" section linking to related documents.
- SRS-mandated elements are tagged `SRS Requirement` in node labels where applicable.
- Speculative technologies are labelled `TBD` or `Team Technical Decision` — never presented as mandatory.

---

## Diagram Maintenance

- Each diagram has an owner (same as the document it appears in).
- Diagrams must be updated when the underlying architecture changes.
- Out-of-date diagrams are treated as bugs.

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited`
