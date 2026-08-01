# CM4S — DESIGN.md

Design system for everything built at Chiang Mai 4 Seasons, August 2026 — the artifacts, the
portfolio, and the participant micro-apps.

**This is a projection of AppyDave, not a new brand.** It inherits every token from
`brand-dave:brand` → `references/appydave/DESIGN.md` unchanged, and adds only the semantic
assignments this project needs. Where the two disagree, **AppyDave wins.**

---

## 1 · Inherited palette — fixed, do not extend

| Token | Hex | Role |
|---|---|---|
| `--brand-brown` | `#342d2d` | Primary dark — text, headings, structure |
| `--brand-gold` | `#ccba9d` | Warm secondary — "Appy" in logo, borders |
| `--brand-yellow` | `#ffde59` | Primary CTA — "Dave" in logo, attention |
| `--brand-amber` | `#c8841a` | Numbered sequences, one-off accents |
| `--brand-muted` | `#7a6e5e` | Supporting body text, secondary labels |
| `--brand-near-white` | `#faf5ec` | Primary page background |
| `--brand-surface` | `#f0ebe4` | Secondary surface, section alternates |
| `--brand-linen` | `#e8e0d4` | Tertiary warm surface, cards |
| `--brand-border` | `#d4cdc4` | Dividers, rules, table borders |
| `--brand-chrome` | `#1a1515` | Dark chrome — never pure black |
| `--brand-dark-surface` | `#25201e` | Dark contrast beats only |
| `--brand-blue` | `#2E91FC` | Links and small elements only, never a fill |

Define **all twelve** in every stylesheet. An undefined custom property renders as invisible text.

## 2 · Semantic assignments — this project's own

Status colours come from AppyDave's `brand-style-guide.md`. Nothing below is invented.

### Pipeline state — the control plane

| State | Token | Hex |
|---|---|---|
| Complete | `--st-complete` | `#22c55e` |
| In progress | `--st-active` | `#16a34a` |
| Blocked | `--st-error` | `#dc2626` |
| Not started | `--st-pending` | `#b8a070` |

Complete and in-progress are both green and adjacent. **Encode in-progress as a half-filled bar**
so state reads by shape as well as hue — colour alone is not sufficient here.

### Evidence provenance — the one thing unique to this project

The system distinguishes what a participant said from what the AI synthesised. That distinction is
load-bearing, so it gets a visual form:

| Kind | Treatment |
|---|---|
| **Said** — the participant's own words | Solid pill, `--brand-brown` background, cream text. Body text at full contrast |
| **Inferred** — AI synthesis | Outline pill, `--brand-border` hairline, `--brand-muted` text. Body text muted |

Inference is *quieter* than evidence. Never render a synthesis at the same weight as a quote.

### Phase sequence

`--brand-amber` for the six phase ordinals `01`–`06`. This is a genuine sequence, which is the
only case where numbered markers are earned. Never amber as a button.

### The human gate

`--brand-yellow` is **reserved** — the human decision gate and the active tab underline. Nothing
else. If yellow appears three times on a page, two of them are wrong.

## 3 · Typography

| Font | Role |
|---|---|
| **Bebas Neue** | The AppyDave logo only. Never headings, never navigation |
| **Oswald** 400–700 | All headings, tabs, labels, category headers — uppercase always |
| **Roboto** 400–700 | Body, paragraphs, table cells |
| **Roboto Mono** 400 | Data, identifiers, filenames, lineage codes, timestamps |

Roboto Mono carries every `CM4S-L2`, capture code, and filename — machine-readable strings look
machine-readable.

## 4 · Rules that have already been broken once

Each of these cost a rebuild. They are not stylistic preferences.

- **Light-first for every viewer.** Pin `color-scheme: light`. **No `prefers-color-scheme: dark`
  block, no `data-theme` override, ever.** AppyDave is light-first regardless of the reader's OS
  theme. "Dark as accent" means a dark *element* inside a light page — never a repainted canvas.
- **Embed fonts as base64 data URIs.** The artifact CSP blocks font CDNs, so a
  `fonts.googleapis.com` link fails silently into an arbitrary fallback. Latin subsets of all four
  faces total ~260 KB — acceptable.
- **Invent no colours.** If a hue seems needed that isn't in §1 or §2, the design is wrong, not the
  palette.
- **One dark element per page, at most.** A single `--brand-dark-surface` beat is a guest.
- **The logo is two-tone** — "Appy" gold, "Dave" yellow — and never sits on white.

## 5 · Visual output is an Artifact, not a file

Any visual deliverable ships as a published Artifact so the team can see it. A local `.html` file
is invisible to everyone but the machine it sits on.

Artifacts are **private by default** — publishing does not share. Sharing is a deliberate step
from the page's share menu, and it is the author's job to remember it.

Keep a redeployed artifact on its original URL and favicon; a changed icon reads as a different
page to anyone who bookmarked it.

## 6 · Participant micro-apps

Apps built for participants inherit §1 and §3. They are AppyTron desktop consoles or AppyStack web
apps, so also read that scaffold's own conventions — this file governs colour and type, not layout.

Two judgement calls for a one-day build:

- **Coherence beats expression.** Five apps that look like one family read as a system. Five that
  each express themselves read as five hackathon projects.
- **A participant's own brand, if they have one, wins over this file** — the app is theirs. Say so
  in the handover rather than quietly overriding it.

---

**Base**: AppyDave · `~/dev/ad/appydave-plugins/brand-dave/skills/brand/references/appydave/`
**Applies to**: `docs/system-views.html`, `docs/design-system.html`, the portfolio, participant apps
**Created**: 2026-08-01
