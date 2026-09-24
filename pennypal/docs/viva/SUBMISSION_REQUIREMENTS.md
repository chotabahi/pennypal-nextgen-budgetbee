# Submission Requirements

> **Authority:** SRS-mandated submission deliverables. This document defines what gets submitted, in what format, by when, and to whom.

The SRS mandates the following submission deliverables: `SRS Requirement` (Submission)
- Credentials
- APK
- Source code
- README
- MP4 demonstration

**Critical distinction:** The 5 deliverables above are `SRS-mandated deliverables`. Additional items the team may prepare are `Team preparation items` or `Optional enhancement`. The documentation does not add mandatory submission items that are not supported by the SRS, and does not remove SRS-mandated deliverables.

---

## 1. Submission Package Overview

### 1.1 SRS-mandated submission items

**`SRS Requirement`** — the SRS mandates the following deliverables:

| Item | Format | Delivery | Owner | SRS section | Classification |
|------|--------|----------|-------|-------------|----------------|
| Credentials | Document (e.g., Markdown / text file). | Submission package. | `[TBD]` | Submission | `SRS-mandated deliverable` |
| APK | `.apk` (Android Package). | Submission package. | `[TBD]` | Submission | `SRS-mandated deliverable` |
| Source code | Git repository. | Public repo URL. | `[TBD]` | Submission | `SRS-mandated deliverable` |
| README | Markdown file at repository root. | In the repository. | `[TBD]` | Submission | `SRS-mandated deliverable` |
| MP4 demonstration | `.mp4` video file. | Submission package. | `[TBD]` | Submission | `SRS-mandated deliverable` |

### 1.2 Team preparation items (not SRS-mandated)

**Tag:** `Team preparation item`.

| Item | Format | Purpose | Tag |
|------|--------|---------|-----|
| Presentation slides (if applicable) | PDF / PPTX | Live demo support. | `Team preparation item` |
| Demo device (backup) | Physical device | Demo fallback. | `Team preparation item` |
| Printed one-page summary (optional) | PDF | Judge handout. | `Team preparation item` |

### 1.3 Optional enhancements (not SRS-mandated, not required)

**Tag:** `Optional enhancement`.

| Item | Format | Purpose | Tag |
|------|--------|---------|-----|
| Backup MP4 on USB | MP4 on USB stick | Fallback if submission package fails. | `Optional enhancement` |
| Live web build (if applicable) | URL | Additional demo surface. | `Optional enhancement` |

---

## 2. Item Details

### 2.1 Credentials (SRS-mandated)

**`SRS Requirement`** — the SRS mandates credentials as a submission deliverable.

**Classification:** `SRS-mandated deliverable`.

**Format:** Document (e.g., `CREDENTIALS.md` in the repository, or a text file in the submission package). `Team Technical Decision` (specific format).

**Contents:**
- Demo Student account credentials (email / password or other auth method per ADR-006). `SRS Requirement`
- Demo Admin account credentials. `SRS Requirement`
- Any other credentials needed to evaluate the submission (e.g., backend URL). `Team preparation item`

> **Note:** Real production credentials must NOT be included. Only demo / test credentials. `Team Technical Decision`

**Placeholder template:**
```
# PennyPal — Demo Credentials

## Student Account
- Email: [demo-student@example.com]
- Password: [TBD — set during build]

## Admin Account
- Email: [demo-admin@example.com]
- Password: [TBD — set during build]

## Backend
- API URL: [TBD — set during deployment]
```

### 2.2 APK (SRS-mandated)

**`SRS Requirement`** — the SRS mandates an APK as a submission deliverable.

**Classification:** `SRS-mandated deliverable`.

**Format:** `.apk` (Android Package). `SRS Requirement`

**Build process:** See `../process/DEPLOYMENT.md` → Section 3.1.

**Verification:**
- [ ] APK installs on a fresh Android device.
- [ ] App launches without errors.
- [ ] All SRS-mandated features accessible (or honestly documented as not implemented in `LIMITATIONS.md`).

**Distribution:**
- [ ] APK included in the submission package.
- [ ] APK file naming convention: `Team Technical Decision` — `TBD`.

### 2.3 Source code (SRS-mandated)

**`SRS Requirement`** — the SRS mandates source code as a submission deliverable.

**Classification:** `SRS-mandated deliverable`.

**Format:** Git repository. `SRS Requirement`

**Contents:**
- Application source code. `SRS Requirement`
- Backend source code (if applicable). `Assumption` — pending team decision.
- This documentation set (`docs/`). `Team preparation item`
- `README.md` at repository root. `SRS Requirement`
- `.env.example` (no real secrets). `Team Technical Decision`
- Lint rules, CI/CD workflows. `Team Technical Decision`

**Verification:**
- [ ] Repository is public (or accessible to judges). `SRS Requirement`
- [ ] `README.md` renders correctly. `SRS Requirement`
- [ ] Mermaid diagrams in `docs/diagrams/` render on GitHub.
- [ ] No secrets in git history.
- [ ] Commit history is clean.

### 2.4 README (SRS-mandated)

**`SRS Requirement`** — the SRS mandates a README as a submission deliverable.

**Classification:** `SRS-mandated deliverable`.

**Format:** Markdown file at the repository root. `SRS Requirement`

**Contents:**
- Project name and description. `SRS Requirement` (project scope)
- Setup instructions. `Team Technical Decision`
- Link to documentation (`docs/`). `Team preparation item`
- SRS-mandated features list. `SRS Requirement`
- Submission deliverables list. `SRS Requirement`

The repository's `README.md` is the project's `README.md` (the one in this documentation set's parent directory). `Team Technical Decision`

### 2.5 MP4 Demonstration (SRS-mandated)

**`SRS Requirement`** — the SRS mandates an MP4 demonstration as a submission deliverable.

**Classification:** `SRS-mandated deliverable`.

**Format:** `.mp4` video file. `SRS Requirement`

**Content:**
- Demonstration of SRS-mandated features (F-01 through F-14). `SRS Requirement`
- Specific demo script: `Team Technical Decision` — `TBD` (see `PRESENTATION.md`).

**Recording approach:** `Team Technical Decision` — `TBD`.

**Distribution:**
- [ ] MP4 included in the submission package.
- [ ] MP4 file size and duration: `Team Technical Decision` — `TBD`.

---

## 3. Submission Channels

### 3.1 SRS-mandated channels

**`Assumption`** — pending SRS / competition rules verification. The SRS mandates the deliverables but does not specify the submission channel.

### 3.2 Team-decided channels

**Tag:** `Team Technical Decision` — `TBD`.

Candidate channels:
- Email.
- Online form.
- In-person (USB stick).
- GitHub release.

---

## 4. Submission Checklist

The checklist covers all SRS-mandated deliverables:

### Morning (before build)

- [ ] All code merged to main.
- [ ] Lint passes.
- [ ] Tests pass (`SRS Requirement` — testing is mandated).
- [ ] Version bumped.
- [ ] `.env` set to production.
- [ ] All `Assumption` items in documentation reviewed.
- [ ] No secrets in git history.

### Build

- [ ] APK built and verified. `SRS Requirement`
- [ ] Backend deployed (if applicable).
- [ ] MP4 demonstration recorded. `SRS Requirement`

### Verify

- [ ] APK installs and runs on a fresh device. `SRS Requirement`
- [ ] All SRS-mandated features accessible (or honestly documented in `LIMITATIONS.md`). `SRS Requirement`
- [ ] Source code repository is public. `SRS Requirement`
- [ ] README is complete and accurate. `SRS Requirement`
- [ ] Credentials document is prepared. `SRS Requirement`
- [ ] MP4 plays correctly and demonstrates SRS-mandated features. `SRS Requirement`

### Submit

- [ ] All 5 SRS-mandated deliverables included in the submission package:
  - [ ] Credentials. `SRS Requirement`
  - [ ] APK. `SRS Requirement`
  - [ ] Source code (public repo URL). `SRS Requirement`
  - [ ] README (in the repo). `SRS Requirement`
  - [ ] MP4 demonstration. `SRS Requirement`
- [ ] Submission sent via the SRS-mandated channel (or team-decided channel if SRS is silent). `Assumption` / `Team Technical Decision`

---

## 5. Failure Scenarios

**Tag:** `Team Technical Decision` — `TBD`.

| Scenario | Mitigation | Tag |
|----------|------------|-----|
| APK won't build on submission day | Use the most recent stable APK; document any missing features in `LIMITATIONS.md`. | `Team Technical Decision` |
| Backend deployment fails | Demo with local mock; document honestly. | `Team Technical Decision` |
| Demo device crashes | Use MP4 demonstration as backup. `SRS Requirement` (MP4 is mandated). | `SRS Requirement` / `Team Technical Decision` |
| Network fails during demo | The app is offline-capable (`SRS Requirement` — offline expense entry); demo the offline features. | `SRS Requirement` |
| Judge asks a question no one can answer | Honest answer: "We didn't consider that. We would treat it as future work." | `Team Technical Decision` |

---

## 6. Submission File Naming Convention

**Tag:** `Team Technical Decision` — `TBD`.

Suggested convention:
- `PennyPal-v1.0.0.apk`
- `PennyPal-v1.0.0-demo.mp4`
- `PennyPal-v1.0.0-credentials.md`
- `PennyPal-v1.0.0-source.zip` (optional; the GitHub repo is preferred)

---

## 7. Post-Submission Actions

**Tag:** `Team Technical Decision` — `TBD`.

- [ ] Keep the backend running until judges confirm evaluation is complete.
- [ ] Monitor for issues.
- [ ] Respond to judge questions within `[TBD]` hours.
- [ ] Update `docs/process/daily-notes.md` with the final status.

---

## 8. Responsible AI Usage (SRS-mandated — must be preserved)

Per the SRS, the team must:
- Demonstrate meaningful understanding and modification of AI-assisted work. `SRS Requirement`
- Be able to explain architecture, requirements, design, and implementation during judging. `SRS Requirement`
- Not accept AI-generated documentation verbatim; team review is mandatory. `SRS Requirement`

The submission must reflect the team's understanding, not raw AI output. The team must be prepared to defend every aspect of the submission during the viva.

---

## 9. What This Document Does NOT Cover

- **Presentation script** → `PRESENTATION.md`
- **Viva question bank** → `VIVA_PREPARATION.md`
- **Build process** → `../process/DEPLOYMENT.md`
- **Project plan** → `../process/PROJECT_PLAN.md` (Team Project Plan)

---

## Team Action: Filling In This File

1. The 5 SRS-mandated deliverables (Section 1.1) are confirmed.
2. Decide on team preparation items (Section 1.2) and optional enhancements (Section 1.3). Tag appropriately.
3. Decide on submission channels (Section 3.2). Tag `Team Technical Decision`.
4. Decide on failure scenarios and file naming.
5. **Do not include real production credentials in the credentials document.** Only demo / test credentials.
6. **Preserve the SRS AI restriction** — the submission must reflect the team's understanding, not raw AI output.
7. Update the file status from `Audited` to `SRS-Complete` (for SRS-derived) or `Team-Reviewed` (for team-decided).

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending team decisions on submission channels and additional items; SRS-mandated deliverables (5) confirmed; SRS AI restriction preserved
