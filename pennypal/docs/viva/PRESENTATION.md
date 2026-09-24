# Presentation

> **Authority:** SRS-mandated submission deliverables (MP4 demonstration) and SRS-derived user flows. This document defines the demo script, slide outline, and talking points for the presentation.

The SRS mandates an MP4 demonstration as a submission deliverable. `SRS Requirement` The presentation may include a live demo plus the MP4 as backup.

**Critical distinction:** Specific demo script, slide outline, and talking points are `Team Technical Decision` or `Derived Design`. SRS-mandated elements (features, deliverables, AI restriction) are tagged `SRS Requirement`.

---

## 1. Presentation Goals

**Tag:** `Team Technical Decision`.

- Show, don't tell.
- Demonstrate SRS-mandated features (F-01 through F-14).
- Be ready for the viva.
- Stay within time.
- **Demonstrate meaningful understanding of AI-assisted work** (`SRS Requirement` — Responsible AI usage).

---

## 2. Presentation Format

### 2.1 SRS-mandated format

**`Assumption`** — pending SRS / competition rules verification. The SRS mandates an MP4 demonstration but does not specify live presentation format.

### 2.2 Team-decided format

**Tag:** `Team Technical Decision` — `TBD`.

| Segment | Duration | Owner |
|---------|----------|-------|
| Intro | `[TBD]` | `[TBD]` |
| Live demo | `[TBD]` | `[TBD]` |
| Architecture highlights | `[TBD]` | `[TBD]` |
| Closing | `[TBD]` | `[TBD]` |
| Q&A | `[TBD]` | All |

---

## 3. Slide Outline

> **Note:** Slides depend on the SRS-mandated features and the team's chosen demo subset. Until the demo subset is decided, the slide outline is `TBD`.

### Slide 1: Title

- Project name: PennyPal.
- Project description: Multi-platform personal finance application for students. `SRS Requirement`
- Team member names.
- Competition / course.

### Slide 2: Problem & Solution

**`SRS Requirement`** — project scope.

- Problem: Students need a tool to manage personal finance. `Assumption` — pending SRS verification.
- Solution: PennyPal — a multi-platform personal finance app with 14 SRS-mandated features. `SRS Requirement`

### Slide 3: Live Demo

(Screen mirrors the demo device. No slide content.)

### Slide 4: Architecture

**`TBD`** — pending `ARCHITECTURE.md` completion and ADR decisions.

### Slide 5: SRS-Mandated Submission Deliverables

**`SRS Requirement`**:

- Credentials.
- APK.
- Source code.
- README.
- MP4 demonstration.

### Slide 6: Responsible AI Usage

**`SRS Requirement`** (Responsible AI usage):
- AI is supporting aid, not a substitute.
- The team demonstrates meaningful understanding and modification of AI-assisted work.
- AI-generated documentation is not automatically acceptable; team review is mandatory.

### Slide 7: Closing

- Summary.
- Repo link.
- "We'd love to take your questions."

---

## 4. Live Demo Script

> **Note:** The demo script selects a subset of SRS-mandated user flows to demonstrate. Specific script is `Team Technical Decision`.

**`TBD`** — pending team decision on demo subset.

Suggested SRS-mandated flows for the demo (pending team decision):
- UF-01 Login (Student).
- UF-02 Dashboard.
- UF-03 Add Income/Expense.
- UF-14 Offline Expense + Sync.
- UF-11 AI Chatbot (basic guidance, supporting aid).
- UF-06 Budget.
- UF-07 Savings Goal.

### Demo Setup

**Tag:** `Team Technical Decision` — `TBD`.

### Demo Script

**`TBD`** — pending team decision on demo subset.

---

## 5. Architecture Segment Script

**`TBD`** — pending `ARCHITECTURE.md` completion and ADR decisions.

Key SRS-derived points to cover:
- Cross-platform compatibility. `SRS Requirement`
- Role-based access (Student / Admin). `SRS Requirement`
- Offline expense entry and synchronization. `SRS Requirement`
- AI chatbot (basic guidance, supporting aid). `SRS Requirement`
- Security and privacy. `SRS Requirement`
- Responsible AI usage. `SRS Requirement`

---

## 6. Closing Script

**`TBD`**.

---

## 7. Q&A Strategy

**Tag:** `Team Technical Decision` — `TBD`.

- Routing.
- Citing the docs (`SRS Requirement`, `Derived Design`, `Team Technical Decision`, `TBD`, ADR-XXX).
- What if no one knows (be honest).
- Time management.
- **Demonstrate understanding of AI-assisted work** (`SRS Requirement`).

---

## 8. MP4 Demonstration (SRS-Mandated)

**`SRS Requirement`** — the SRS mandates an MP4 demonstration as a submission deliverable.

### 8.1 Recording approach

**Tag:** `Team Technical Decision` — `TBD`.

### 8.2 Content

The MP4 should demonstrate the SRS-mandated features. `SRS Requirement` Suggested content (pending team decision):
- App launch and login.
- Dashboard.
- Add income/expense (online and offline).
- Budgets and savings goals.
- AI chatbot (basic guidance, supporting aid).
- Reports.
- (Optional) Admin features.

### 8.3 Format

**Tag:** `Team Technical Decision` — `TBD`.

| Attribute | Value | Tag |
|-----------|-------|-----|
| Resolution | `[TBD]` | `Team Technical Decision` |
| Duration | `[TBD]` | `Team Technical Decision` |
| File size | `[TBD]` | `Team Technical Decision` |
| Voice-over | `[TBD]` | `Team Technical Decision` |

---

## 9. Speaker Notes Per Team Member

**Tag:** `Team Technical Decision` — `TBD`.

---

## 10. Slide Design Notes

**Tag:** `Team Technical Decision` — `TBD`.

---

## 11. Pre-Demo Checklist

**`TBD`** — pending SRS-derived features and submission requirements.

Must include (SRS-mandated):
- [ ] APK installed on demo device. `SRS Requirement`
- [ ] MP4 recorded and available as backup. `SRS Requirement`
- [ ] Credentials prepared. `SRS Requirement`
- [ ] Source code repository public. `SRS Requirement`
- [ ] README complete. `SRS Requirement`

---

## 12. Post-Demo Actions

**Tag:** `Team Technical Decision` — `TBD`.

---

## 13. What This Document Does NOT Cover

- **Viva question bank** → `VIVA_PREPARATION.md`
- **Submission requirements** → `SUBMISSION_REQUIREMENTS.md`
- **Demo flows (in detail)** → `../design/USER_FLOWS.md`

---

## Team Action: Filling In This File

1. Verify SRS-mandated presentation format (Section 2.1).
2. Wait for SRS-derived user flows to be confirmed.
3. Write the demo script (select subset of SRS-mandated flows).
4. Wait for `ARCHITECTURE.md` and ADRs to be complete.
5. Write the architecture segment script.
6. Record the MP4 demonstration (`SRS Requirement`).
7. Decide on Q&A strategy, speaker notes, slide design.
8. **Preserve the SRS AI restriction** — the presentation must reflect the team's understanding, not raw AI output.
9. Update the file status from `Audited` to `Team-Reviewed`.

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending team decisions on demo subset and ADR completion; SRS AI restriction preserved
