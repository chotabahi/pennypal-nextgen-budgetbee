# Deployment Diagram

> **Authority:** SRS-mandated cross-platform compatibility and submission deliverables (APK, source code, README, MP4).

**Critical distinction:** The SRS mandates cross-platform compatibility and the APK / source code / README / MP4 deliverables. Specific deployment topology, backend stack, CI/CD provider, and external services are `Team Technical Decision` or `TBD`. **No specific technology is presented as mandatory.**

---

## Diagram

```mermaid
flowchart TD
    subgraph UserDevices["User Devices (SRS-mandated cross-platform)"]
        AndroidPhone["📱 Android (APK — SRS-mandated deliverable)"]
        OtherPlatforms["💻 Other platforms (TBD per SRS verification)"]
    end

    subgraph Cloud["Cloud (stack TBD — Team Technical Decision)"]
        LoadBalancer["Load Balancer (TBD)"]
        BackendServer["Backend Server<br/>(stack TBD — SRS does not mandate)"]
        ServerDB[("Database<br/>(stack TBD — SRS reference entities)")]
        SecretManager["Secret Manager (TBD)"]
    end

    subgraph External["External"]
        LLM["LLM API<br/>(provider TBD per ADR-008 — SRS does not mandate)"]
        EmailSvc["Email Service (TBD)"]
        PushSvc["Push Service (TBD)"]
    end

    subgraph CICD["CI/CD (provider TBD)"]
        Repo["Git Repository<br/>(source code — SRS-mandated deliverable)"]
        Actions["CI/CD Pipeline (TBD)"]
        Registry["Container Registry (TBD)"]
    end

    AndroidPhone -->|HTTPS| LoadBalancer
    OtherPlatforms -->|HTTPS| LoadBalancer

    LoadBalancer --> BackendServer
    BackendServer --> ServerDB
    BackendServer --> SecretManager
    BackendServer -->|HTTPS| LLM
    BackendServer -->|HTTPS| EmailSvc
    BackendServer -->|HTTPS| PushSvc

    Repo --> Actions
    Actions -->|build + push| Registry
    Actions -->|deploy| BackendServer
    Actions -->|build APK| AndroidPhone

    style UserDevices fill:#D1E4FF,color:#1A1F2C,stroke:#1F6FEB
    style Cloud fill:#E8F5E9,color:#1A1F2C,stroke:#0E7C66
    style External fill:#F5F6F8,color:#1A1F2C,stroke:#D0D5DD
    style CICD fill:#FFF3E0,color:#1A1F2C,stroke:#ED6C02
```

---

## Component Descriptions

### User Devices

**`SRS Requirement`** — cross-platform compatibility is mandated.

| Platform | Distribution | SRS section / tag |
|----------|--------------|-------------------|
| Android | APK (`SRS Requirement` — APK is a mandated deliverable) | `SRS Requirement` |
| Other platforms (iOS, Web, Desktop) | `[TBD]` | `Assumption` — pending SRS verification |

### Cloud

**Tag:** `TBD` — pending backend stack decision. The SRS does not mandate a specific cloud provider or backend stack.

| Component | Tech | Tag |
|-----------|------|-----|
| Load Balancer | `[TBD]` | `Team Technical Decision` |
| Backend Server | `[TBD]` | `Team Technical Decision` |
| Database | `[TBD]` (SRS reference entities are `SRS Requirement`; specific DB tech is `TBD`) | `SRS Requirement` (entities); `TBD` (tech) |
| Secret Manager | `[TBD]` | `Team Technical Decision` |

### External Services

| Service | Purpose | Tag |
|---------|---------|-----|
| LLM API | Powers the AI chatbot (F-11). Provider TBD per ADR-008. | `SRS Requirement` (chatbot); `TBD` (provider) |
| Email Service | For support / notification emails. | `Assumption` — pending SRS verification |
| Push Service | For push notifications (F-12). | `TBD` |

### CI/CD

| Component | Purpose | Tag |
|-----------|---------|-----|
| Git Repository | Hosts source code (`SRS Requirement` — source code is a mandated deliverable). | `SRS Requirement` |
| CI/CD Pipeline | Builds APK, runs tests, deploys backend. | `Team Technical Decision` |
| Container Registry | Hosts backend container image. | `Team Technical Decision` |

---

## Environments

**Tag:** `Team Technical Decision` — `TBD`.

| Env | Backend URL | Purpose | Tag |
|-----|-------------|---------|-----|
| `development` | `[TBD]` | Local dev. | `Team Technical Decision` |
| `staging` | `[TBD]` | Pre-production. | `Team Technical Decision` |
| `production` | `[TBD]` | Submission. | `Team Technical Decision` |

---

## Build & Release Process

The SRS mandates the following deliverables. The release runbook must produce all of them.

| Deliverable | Build process | Tag |
|-------------|---------------|-----|
| APK | Built from source; signed. | `SRS Requirement` |
| Source code | Pushed to Git repository. | `SRS Requirement` |
| README | Committed to repository root. | `SRS Requirement` |
| MP4 demonstration | Recorded from running app. | `SRS Requirement` |
| Credentials | Documented for judges. | `SRS Requirement` |

Detailed build process: `../process/DEPLOYMENT.md`.

---

## Security Notes

**`TBD`** — pending `../architecture/SECURITY.md` completion.

---

## Limitations

**`TBD`** — pending architectural decisions. See `../LIMITATIONS.md`.

---

**Last updated:** Source-accuracy audit
**Maintained by:** Team
**Status:** `Audited` — SRS-mandated deliverables depicted; specific technologies labelled TBD
