# Design System

> **Authority:** SRS visual / accessibility requirements (if any). This document defines the **visual language** of PennyPal — colors, typography, spacing, components, states.

The visual design system is primarily a **team decision** (`Team Technical Decision`), except where the SRS specifies visual or accessibility requirements. SRS-mandated visual requirements are tagged `SRS Requirement`.

---

## 1. Design Tokens

**Tag:** `Team Technical Decision` — `TBD`.

The team decides whether to use a token-based design system. If yes, the token categories (Color, Spacing, Radius, Typography, Duration, Elevation) are listed here.

| Category | Examples | Tag |
|----------|----------|-----|
| Color | `[TBD]` | `Team Technical Decision` |
| Spacing | `[TBD]` | `Team Technical Decision` |
| Radius | `[TBD]` | `Team Technical Decision` |
| Typography | `[TBD]` | `Team Technical Decision` |
| Duration | `[TBD]` | `Team Technical Decision` |
| Elevation | `[TBD]` | `Team Technical Decision` |

---

## 2. Color Palette

### 2.1 SRS-mandated colors

**`Assumption`** — pending SRS verification. If the SRS specifies brand colors, paste them here with `SRS Requirement` tags.

### 2.2 Team-decided palette

**Tag:** `Team Technical Decision` — `TBD`.

If the team adopts a palette, list it here (light + dark). If the SRS specifies accessibility requirements (e.g., "the app shall meet WCAG 2.1 AA contrast"), tag those `SRS Requirement` and ensure the palette satisfies them.

| Token | Hex (light) | Hex (dark) | Usage | Tag |
|-------|-------------|------------|-------|-----|
| `primary` | `[TBD]` | `[TBD]` | `[TBD]` | `Team Technical Decision` |
| `surface` | `[TBD]` | `[TBD]` | `[TBD]` | `Team Technical Decision` |
| `income` | `[TBD]` | `[TBD]` | Income indicators (F-03). | `Team Technical Decision` |
| `expense` | `[TBD]` | `[TBD]` | Expense indicators (F-03). | `Team Technical Decision` |
| `budget.under` | `[TBD]` | `[TBD]` | Budget progress (F-06). | `Team Technical Decision` |
| `budget.over` | `[TBD]` | `[TBD]` | Budget over-limit (F-06). | `Team Technical Decision` |
| `sync.synced` | `[TBD]` | `[TBD]` | Sync status (F-14). | `Team Technical Decision` |
| `sync.pending` | `[TBD]` | `[TBD]` | Sync pending (F-14). | `Team Technical Decision` |

### 2.3 Accessibility (contrast)

**`Assumption`** — pending SRS verification. If the SRS mandates WCAG 2.1 AA or AAA, document the contrast ratios and verify the palette meets them.

---

## 3. Typography

### 3.1 Typeface

**Tag:** `Team Technical Decision` — `TBD`.

If the team selects a typeface, document it here. If the SRS specifies a typeface, paste it with `SRS Requirement`.

### 3.2 Type scale

**Tag:** `Team Technical Decision` — `TBD`.

| Token | Size / Weight / Line height | Usage | Tag |
|-------|------------------------------|-------|-----|
| `displayLarge` | `[TBD]` | Dashboard balance (F-02). | `Team Technical Decision` |
| `headlineLarge` | `[TBD]` | Screen titles. | `Team Technical Decision` |
| ... | ... | ... | ... |

---

## 4. Spacing Scale

**Tag:** `Team Technical Decision` — `TBD`.

| Token | Value | Usage |
|-------|-------|-------|
| `spacing.4` | `[TBD]` | `[TBD]` |
| ... | ... | ... |

---

## 5. Border Radius

**Tag:** `Team Technical Decision` — `TBD`.

| Token | Value | Usage |
|-------|-------|-------|
| `radius.sm` | `[TBD]` | `[TBD]` |
| ... | ... | ... |

---

## 6. Elevation

**Tag:** `Team Technical Decision` — `TBD`.

| Token | Box shadow | Usage |
|-------|------------|-------|
| `elevation.1` | `[TBD]` | `[TBD]` |
| ... | ... | ... |

---

## 7. Components

For each component the team adopts, document its variants, when to use, and style. All components are `Team Technical Decision` unless the SRS specifies (rare).

| Component | Variants | Tag | Used in (SRS feature) |
|-----------|----------|-----|------------------------|
| Button | `[TBD]` | `Team Technical Decision` | All screens. |
| Input | `[TBD]` | `Team Technical Decision` | Login, Add Income/Expense, Feedback, Contact Support. |
| Card | `[TBD]` | `Team Technical Decision` | Dashboard, Budgets, Savings Goals, Learning Content. |
| Progress | `[TBD]` | `Team Technical Decision` | Budget progress (F-06), Savings progress (F-07), Sync status (F-14). |
| Chip | `[TBD]` | `Team Technical Decision` | Expense categories (F-04), Notification badges (F-12). |
| List | `[TBD]` | `Team Technical Decision` | Transaction history (F-05), Notifications (F-12), Learning content (F-08). |
| Sheet / Dialog | `[TBD]` | `Team Technical Decision` | Add Income/Expense (F-03), Confirmations. |
| Navigation | `[TBD]` | `Team Technical Decision` | All screens. |
| Empty state | `[TBD]` | `Team Technical Decision` | All list screens. |
| Error state | `[TBD]` | `Team Technical Decision` | All screens. |
| Chat bubble | `[TBD]` | `Team Technical Decision` | AI Chatbot (F-11). |

---

## 8. Iconography

**Tag:** `Team Technical Decision` — `TBD`.

If the team selects an icon set (e.g., Material Symbols, Cupertino icons), document it here. If the SRS specifies icons (rare), paste with `SRS Requirement`.

---

## 9. State Matrix

For each primary component, the design system specifies how it looks in each state (default, hover, pressed, disabled, loading, error). All states are `Team Technical Decision` unless the SRS specifies.

| Component | Default | Hover | Pressed | Disabled | Loading | Error |
|-----------|---------|-------|---------|----------|---------|-------|
| Button | `[TBD]` | `[TBD]` | `[TBD]` | `[TBD]` | `[TBD]` | `[TBD]` |
| Input | `[TBD]` | `[TBD]` | N/A | `[TBD]` | N/A | `[TBD]` |
| Card | `[TBD]` | `[TBD]` | N/A | N/A | `[TBD]` | N/A |
| Sync indicator | `[TBD]` | N/A | N/A | N/A | `[TBD]` | `[TBD]` |
| ... | ... | ... | ... | ... | ... | ... |

---

## 10. Dark Mode

**`Assumption`** — pending SRS verification. If the SRS specifies dark mode support, paste it here with `SRS Requirement` tag. Otherwise mark as `Team Technical Decision` / `TBD`.

If the SRS mandates dark mode, document the dark palette per token. If the SRS is silent, the team decides.

---

## 11. Asset Management

**Tag:** `Team Technical Decision` — `TBD`.

If the team adopts asset organization conventions (icons, illustrations, fonts, images), document them here.

---

## 12. Token Implementation

> **Note:** This section describes the implementation approach in prose. Per the task constraints, no Dart source code is included.

**Tag:** `Team Technical Decision` — `TBD`.

The team decides how tokens are implemented (e.g., a `theme/tokens.dart` file with classes for each token category). The implementation approach is documented here once decided.

---

## 13. What This Document Does NOT Cover

- **UX flows** → `UI_UX_DESIGN.md`
- **Step-by-step user journeys** → `USER_FLOWS.md`
- **Architecture of the theme system** → `../architecture/TECHNICAL_DESIGN.md`
- **Accessibility audit results** → `../process/TESTING.md`

---

## Team Action: Filling In This File

1. Check the SRS for any visual / accessibility requirements. Paste them with `SRS Requirement` tags.
2. For each token category, decide as a team and tag `Team Technical Decision`.
3. For each component, decide variants and styles. Tag `Team Technical Decision`.
4. Verify the palette meets any SRS-mandated contrast requirements.
5. Update the file status from `SRS-Derived` to `Team-Reviewed`.

---

**Last updated:** SRS-derived content generation
**Maintained by:** Team
**Status:** `SRS-Derived` — pending team decisions on visual design
