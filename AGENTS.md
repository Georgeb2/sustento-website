# AGENTS.md — Sustento Website

Guidance for AI agents (and humans) editing this repo. The goal: keep every change **on-brand** with Sustento's voice, palette, and positioning.

This is a **static marketing site** — no build step, framework, or package manager. Edit files directly; open them in a browser to preview.

### Site structure

| Path | Purpose |
|------|---------|
| `index.html` | Primary marketing homepage |
| `styles.css` | Shared design system (CSS custom properties + components) |
| `industries/<slug>/index.html` | Vertical / industry sub-sites |

**Live industry pages today:**
- `/industries/buildings-facilities/`
- `/industries/hospitality/`
- `/industries/municipal/`

**Still homepage-only** (no dedicated page yet): Fleet Management, Food & Beverage, Marine.

Asset and stylesheet links on subpages must use **site-root paths** (`/styles.css`, `/logo.png`, `/#features`) so they resolve correctly when served from Netlify or similar.

### Adding a new vertical

1. Create `industries/<slug>/index.html` following an existing industry page (nav → breadcrumb/hero → industry features → resources → CTA → footer).
2. Rewrite features and hero copy in that industry’s maintenance terminology.
3. Scaffold three resource cards (Demo, Comparison, White paper) with `mailto:info@sustentosoftware.com` and a clear subject line until real assets exist.
4. Link the vertical from homepage chips, industry cards, and footers (main + sibling industry pages).
5. Document the new slug in this file.

### Resource cards

Use `.resources` / `.resource-card` / `.resource-type`. Prefer real demo URLs or PDF `href`s when available; until then use mailto CTAs (“Request a demo”, “Request the comparison”, “Request the white paper”). Do not invent competitor names or claim downloadable assets that do not exist.

---

## What Sustento is (positioning)

Sustento is a **modern CMMS** (Computerized Maintenance Management System) — vertical SaaS for maintenance teams.

- **Category:** CMMS / maintenance management software.
- **Buyer:** maintenance supervisors, facility managers, operations leads.
- **Core jobs:** work orders, asset management, preventive maintenance, checklists, team management, guest request portals, reporting, audit log.
- **The wedge:** "modern alternative to legacy/desktop tools" — fast, simple, no spreadsheets. The product "gets out of your way."
- **Verticals we speak to** (keep terminology adaptable per industry): Buildings & Facilities, Fleet Management, Hospitality, Food & Beverage, Marine, Municipal.
- **Primary CTA:** "Request early access" → `mailto:info@sustentosoftware.com`. The product is pre-launch / not yet open for self-serve trials, so do **not** add "start free trial" / "no credit card" signup CTAs. "Sign in" still points existing users to `https://www.sustentocmms.com`.
- **Contact:** `info@sustentosoftware.com` (sales/pricing), `hello@sustentosoftware.com` (general). Legal entity: **Sustento Software**.

When adding copy, anchor it to a concrete maintenance outcome (less downtime, never miss a service interval, full audit trail) rather than generic SaaS fluff.

---

## Tone of voice

- **Confident and plain-spoken.** Short sentences. Active voice. No jargon for jargon's sake.
- **Benefit-first, outcome-driven.** Lead with what the team gets ("Create your first work order in under 60 seconds"), not feature lists.
- **Practical, not hypey.** Avoid superlatives and buzzwords ("revolutionary", "AI-powered", "world-class"). We earn trust by being specific.
- **Respect the operator's time.** Copy mirrors the product promise: get out of the way.
- **US English spelling** throughout — e.g. "finalizing", "organizations", not UK variants ("finalising", "organisations").
- Sentence case for most UI; Title Case is fine for short labels/badges. Use the em dash (—) as a connector, consistent with existing copy.

---

## Brand palette

The palette lives in `:root` in `styles.css`. **Reuse the existing custom properties** instead of hardcoding hex values. When a needed shade isn't tokenized (many accent shades are currently inline), match the values below exactly.

### Core brand (primary)

| Token        | Hex       | Use |
|--------------|-----------|-----|
| `--blue`     | `#2563eb` | Primary brand color: primary buttons, links, badges, accents |
| `--blue-dk`  | `#1d4ed8` | Primary hover / pressed state |
| `--blue-lt`  | `#eff6ff` | Tinted backgrounds, badge fills, outline-button hover |

**Brand gradient** (hero highlight + CTA section): `linear-gradient(135deg, #2563eb 0%, #7c3aed 100%)` for text; the CTA band uses `linear-gradient(135deg, #1e40af 0%, #4f46e5 100%)`. Purple (`#7c3aed` / indigo `#4f46e5`) is the **secondary accent** — use it sparingly, mainly in gradients.

### Neutrals (grays)

| Token        | Hex       |
|--------------|-----------|
| `--gray-50`  | `#f9fafb` |
| `--gray-100` | `#f3f4f6` |
| `--gray-200` | `#e5e7eb` |
| `--gray-400` | `#9ca3af` |
| `--gray-600` | `#4b5563` |
| `--gray-500` | `#6b7280` |
| `--gray-700` | `#374151` (default body text) |
| `--gray-900` | `#111827` (headings, dark footer bg) |

All gray steps above are defined in `:root` — use the token, don't hardcode the hex.

### Functional accent colors (status, feature icons, stat cards)

These are semantic, low-saturation pairings (tint background + saturated foreground). Keep them consistent for meaning:

- **Blue** (info / default): bg `#eff6ff` / `#dbeafe`, fg `#2563eb` / `#1d4ed8`
- **Green** (success / assets / "open" PM): bg `#f0fdf4`, fg `#16a34a`; check icons use `#16a34a`
- **Purple** (PM / assigned): bg `#faf5ff` / `#ede9fe`, fg `#7c3aed` / `#6d28d9`
- **Amber/Yellow** (overdue / warning): bg `#fffbeb` / `#fef9c3`, fg `#d97706` / `#854d0e`
- **Red** (urgent / errors): bg `#fef2f2` / `#fee2e2`, fg `#dc2626`
- **Orange** (high priority): bg `#ffedd5`, fg `#c2410c`
- **Teal** (`#0d9488`), **Indigo** (`#4f46e5`), **Gray** (neutral) — additional feature-icon accents

Don't introduce new hues outside this set. If a new accent is truly needed, extend the system deliberately and document it here.

### Surfaces & depth

- Page background: `#fff`; alternating sections use `--gray-50`.
- Radius: `--radius: 12px` (cards), buttons use `8px` (`10px` for `.btn-lg`), pills use `100px`.
- Shadows: `--shadow-sm`, `--shadow`, `--shadow-lg` — use these tokens, don't roll new box-shadows.
- The dark app-preview sidebar uses `#1e3a6e` (deep navy) — part of the product UI illustration.

---

## Typography

- **Font:** `Inter` (Google Fonts), with `system-ui, sans-serif` fallback. Don't swap the typeface.
- **Weights in use:** 400, 500, 600, 700, 800. Headings are 800 with tight tracking (`letter-spacing: -.02em`).
- **Scale:** fluid via `clamp()` for hero/section headings. Body is 16px / line-height 1.6.
- Headings use `--gray-900`; body uses `--gray-700`/`--gray-600`; muted/meta uses `--gray-400`.

---

## Components & conventions

- **Buttons:** `.btn` + a variant (`.btn-primary`, `.btn-secondary`, `.btn-outline`, `.btn-white`), optional `.btn-lg` / `.btn-full`. Primary = brand blue. `.btn-white` is for the dark CTA band.
- **Layout:** wrap content in `.container` (max-width 1120px, 24px gutters). Sections use `.section-header` for centered title + subtitle.
- **Cards:** `.feature-card`, `.industry-card`, `.pricing-card`, `.resource-card` share the white / `--gray-200` border / `--radius` pattern. Feature icons are 44px rounded tiles with a colored accent class. Linked industry cards use `a.industry-card`.
- **Industry pages:** `.page-hero` (left-aligned hero), `.breadcrumb`, `.resources` / `.resources-grid` / `.resource-type` for vertical resource sections.
- **Icons:** inline SVGs, 24×24 viewBox, `stroke="currentColor"`, `stroke-width="2"` (Heroicons-style outline). Match this style for any new icon; color comes from the parent `.feature-icon.<accent>`.
- **Responsive:** breakpoints at `768px` and `480px`. Test mobile — the nav collapses to a hamburger (`#mobileToggle` / `#mobileNav`) and the preview sidebar hides.
- **JS:** one small inline script for the mobile nav (repeated per page). Keep it dependency-free and minimal; no frameworks.

---

## When editing, do

- Reuse CSS variables and existing component classes; keep styling in `styles.css` and avoid inline `style=` attributes in HTML.
- Keep copy specific, benefit-led, and aligned to the maintenance/CMMS domain and the six verticals.
- Preserve the calm, professional, blue-forward look. Purple is an accent, never the lead.
- Keep accessibility intact: real `alt` text, sufficient contrast, semantic headings, `aria-label`s on icon-only controls.
- Match existing spelling/voice in the file you're editing.

## When editing, don't

- Don't add frameworks, build steps, trackers, or heavy dependencies to this static site.
- Don't introduce off-palette colors, a new typeface, or hypey/buzzword copy.
- Don't change CTAs/links/contact emails without reason — primary CTA is early access via `mailto:info@sustentosoftware.com`; Sign in still points to `www.sustentocmms.com`.
- Don't hardcode hex values that already have a token.
