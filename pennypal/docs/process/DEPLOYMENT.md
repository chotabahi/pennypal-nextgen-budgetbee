# Deployment

> **Authority:** SRS-mandated submission deliverables and cross-platform compatibility. This document is the release runbook.

The SRS mandates the following submission deliverables: `SRS Requirement` (Submission)
- Credentials
- APK
- Source code
- README
- MP4 demonstration

The SRS also mandates cross-platform compatibility `SRS Requirement` and installation. `SRS Requirement`

**Critical distinction:** The SRS mandates the deliverables and cross-platform compatibility. Specific build process, backend stack, CI/CD provider, and signing approach are `Team Technical Decision` or `TBD` pending ADRs. **No specific technology is presented as mandatory.**

---

## 1. Build Targets

### 1.1 SRS-mandated platforms

**`SRS Requirement`** — cross-platform compatibility is mandated. Specific target platforms are `Assumption` pending SRS verification.

| Platform | Priority | Format | Distribution | SRS section / tag |
|----------|----------|--------|--------------|-------------------|
| Android | Must Have (APK is SRS-mandated) | APK | Direct install / app store | `SRS Requirement` |
| iOS | `[TBD]` | IPA (if target) | TestFlight / app store | `Assumption` — pending SRS verification |
| Web | `[TBD]` | Web build | Web host | `Assumption` — pending SRS verification |
| Desktop | `[TBD]` | Desktop binaries | Direct download | `Assumption` — pending SRS verification |

### 1.2 Team-decided additional platforms

**Tag:** `Team Technical Decision` — `TBD`.

---

## 2. Pre-Build Checklist

**`TBD`** — pending ADR decisions.

- [ ] Code merged to main.
- [ ] Lint passes.
- [ ] Tests pass (`SRS Requirement` — testing is mandated).
- [ ] Version bumped.
- [ ] `.env` set to production.
- [ ] Signing keys available.

---

## 3. Building Each Target

### 3.1 Android APK (SRS-mandated)

**`SRS Requirement`** — APK is a mandated submission deliverable.

Build process: `TBD` — pending ADR-001 (framework decision). The SRS does not mandate a specific framework.

Verification:
- [ ] APK installs on a fresh Android device.
- [ ] App launches without errors.
- [ ] All SRS-mandated features accessible (or honestly documented as not implemented in `LIMITATIONS.md`).

Distribution:
- [ ] APK uploaded to the submission package.

### 3.2 iOS IPA (if target)

**`Assumption`** — pending SRS verification. Build process `TBD`.

### 3.3 Web bundle (if target)

**`Assumption`** — pending SRS verification. Build process `TBD`.

### 3.4 Desktop binaries (if target)

**`Assumption`** — pending SRS verification. Build process `TBD`.

---

## 4. Backend Deployment

> **Note:** Applicable if the SRS implies a backend (it does — for sync, chatbot, Admin features). `SRS Requirement`

### 4.1 Prerequisites

**`TBD`** — pending backend stack decision. The SRS does not mandate a specific backend stack.

### 4.2 Build the container

**`TBD`** — pending backend stack decision.

### 4.3 Deploy to the server

**`TBD`** — pending backend stack decision.

### 4.4 Verify the deployment

**`TBD`** — pending backend stack decision.

### 4.5 Rollback

**`TBD`** — pending backend stack decision.

---

## 5. CI/CD Pipeline

**`TBD`** — pending `DEVELOPMENT_WORKFLOW.md` CI/CD section and platform list. The SRS does not mandate a specific CI/CD provider.

---

## 6. Signing & Secrets

### 6.1 Android signing

**Tag:** `Team Technical Decision` — `TBD`.

### 6.2 iOS signing

**Tag:** `Team Technical Decision` — `TBD`.

### 6.3 Server secrets

**Tag:** `Team Technical Decision` — `TBD`.

> **Note:** No real secrets are documented here. This section describes the secret management approach only.

---

## 7. Environments

**Tag:** `Team Technical Decision` — `TBD`.

| Env | Backend URL | Purpose | Tag |
|-----|-------------|---------|-----|
| `development` | `[TBD]` | Local dev. | `Team Technical Decision` |
| `staging` | `[TBD]` | Pre-production. | `Team Technical Decision` |
| `production` | `[TBD]` | Submission. | `Team Technical Decision` |

---

## 8. SRS-Mandated Submission Deliverables

The SRS mandates the following deliverables. The release runbook must produce all of them.

| Deliverable | Build process | Tag | Status |
|-------------|---------------|-----|--------|
| Credentials | Document demo/test credentials for judges. | `SRS Requirement` | `TBD` |
| APK | Build per Section 3.1. | `SRS Requirement` | `TBD` |
| Source code | Push to Git repository. | `SRS Requirement` | `TBD` |
| README | Committed to repository root. | `SRS Requirement` | `TBD` |
| MP4 demonstration | Record from running app. | `SRS Requirement` | `TBD` |

---

## 9. Release Runbook (Submission Day)

**`TBD`** — pending SRS-derived submission requirements. See `../viva/SUBMISSION_REQUIREMENTS.md`.

The runbook must produce all SRS-mandated deliverables (Section 8).

---

## 10. Monitoring

**Tag:** `Team Technical Decision` — `TBD`.

---

## 11. What This Document Does NOT Cover

- **Deployment topology** → `../diagrams/DEPLOYMENT.md`
- **CI/CD details** → `DEVELOPMENT_WORKFLOW.md`
- **Project plan** → `PROJECT_PLAN.md` (Team Project Plan)
- **Security of the deployment** → `../architecture/SECURITY.md`

---

## Team Action: Filling In This File

1. Verify SRS-mandated platforms (Section 1.1).
2. Decide on additional platforms (`Team Technical Decision`).
3. Wait for ADR-001 (framework) and backend stack decision to be decided.
4. Fill in build commands, deployment steps, signing, and environments.
5. Ensure the release runbook produces all SRS-mandated deliverables (Section 8).
6. **Do not present specific technologies as mandatory.** All technology choices are `TBD` until ADRs are decided.
7. Update the file status from `Audited` to `Team-Reviewed`.

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — pending ADR decisions and build process definition; no technologies presented as mandatory
