# Video & animation — what Beauty & Joy already solved

Recon 2026-08-01. Purpose: reuse Joy's working video pipeline for CM4S overlays, sequences and
b-roll instead of rediscovering it.

## The headline finding inverts the request

You asked for the **Remotion** videos, not the Remotion-hyperframes ones. The Remotion project
exists — `~/dev/ad/joy/joy-videos` — and it is **archived**. Its own `DEPRECATED.md` (2026-07-23)
says, verbatim: *do not render from it, do not copy its colours, do not start new video work here.*

Why it died is the useful part:

> **Its palettes were invented.** `JoyJuiceIntro.tsx` and `NailPromotion.tsx` use `#1a6b3a`,
> `#e8c96e`, `#f5e642` — green/yellow that match **neither** brand's DESIGN.md, neither website,
> and nothing else in the hub. They were not derived from anything; they were picked.

And the lesson it draws:

> `composition-patterns.md` opens by naming its authority — *"Source of truth: AppyDave `brand`
> skill → `references/beauty-and-joy/DESIGN.md`"* — and copies six values out of it. That is the
> only design artifact in this hub wired that way, and it produced the only visual output anyone is
> happy with. **Name your source or don't ship.**

That is the same rule `DESIGN.md` in this repo already follows — *a projection of AppyDave, not a
new brand; where they disagree, AppyDave wins.* Independent arrival, same conclusion.

**So: the live pipeline is HyperFrames, and that is what we copy.**

## Where it lives

| What | Path |
|---|---|
| The skill (system of record) | `~/dev/ad/joy/.claude/skills/joy-video/` |
| Footage + catalogue | `~/dev/ad/joy/joy-footage/` |
| Master project ★ | `joy-footage/hf-recut/videos/joy0039-editorial-9x16` |
| Archived Remotion | `~/dev/ad/joy/joy-videos` — **do not use** |

## The skill architecture — this is the transferable part

`joy-video` wraps HeyGen's `hyperframes` CLI but **owns** everything the generic tool doesn't know.
Its stated principle: *"HeyGen is a tool we rent; this skill is our system of record. If hyperframes
changes, fix it here — don't relearn."*

Four ledgers, each with one job, and a routing rule for what goes where:

| Ledger | Holds | Route here when |
|---|---|---|
| `SKILL.md` | The durable law — folder conventions, the make-a-cut sequence | A rule becomes permanent |
| `LEARNINGS.md` | Technical gotchas — render, tooling, fonts | You hit a tooling fact worth keeping |
| `references/editorial-craft.md` | General craft any editor would use | It's technique, not tooling |
| `references/composition-patterns.md` | Brand tokens + copy-paste blocks per beat | It stops us re-deriving a value |
| `editorial-preferences.md` | David's personal taste, learned from his reactions to real cuts | He reacts to a specific cut |

> *"Knowledge that isn't committed here is lost at session end. These ledgers are the mechanism
> that stops us relearning every session."*

**This is the shape our own skills should take when the pilot earns them** — not one fat SKILL.md,
but a law file plus routed ledgers.

## The token bridge — what to adapt for AppyDave

Joy's compositions bake six values into every `:root`, copied from the brand DESIGN.md and *named*
as such. The CM4S equivalent, drawn from our own `DESIGN.md`:

```css
:root {
  /* Source of truth: CM4S DESIGN.md → a projection of AppyDave.
     Do not invent values here. If a colour is missing, the design is wrong. */
  --bg:       #faf5ec;  /* warm cream page */
  --text:     #342d2d;  /* warm brown ink — never pure black */
  --accent-0: #ccba9d;  /* gold — rules, kickers */
  --accent-1: #ffde59;  /* yellow — the signature accent, sparingly */
  --accent-2: #c8841a;  /* amber — sequences, numbers */
  --muted:    #7a6e5e;  /* secondary labels */
  --dark:     #25201e;  /* the one dark beat — end-cards, logo chip */
}
```

Joy's concepts vary **accents, not structure** — `editorial` = gold+pink, `warmgold` = gold+bronze,
`bold` = solid chips. Same discipline available to us: the skin stays constant, the device rotates.

Fonts: **local woff2 in `public/fonts/`, `@font-face`'d** — the renderer's CSP blocks CDNs, exactly
like the artifact CSP. The `grab()` helper in `composition-patterns.md` pulls latin subsets; it's
the same technique already used for our artifacts. One gotcha: body `font-family` must list
**concrete names**, not `var(--font-family)` — the renderer's font resolver doesn't expand CSS vars.

## Render gotchas that will bite us too

- **Paint z-order is DOM order, not `data-track-index`.** Order: `bg-video → b-roll → cards → PiP`
- B-roll needs a **unique `data-track-index`** or lint errors, but still paints by DOM order
- **Never animate `visibility` on `.clip` elements** — animate `opacity` / `scale` only
- Re-encode sources with dense keyframes (`-g 30 -keyint_min 30`) or frames freeze on seek
- Pinned baseline: **hyperframes v0.7.26**, Node ≥22, ffmpeg 8, `PRODUCER_BROWSER_GPU_MODE=hardware`

## Two tools, two jobs — don't conflate them

A recut needs to know **where** things are and **what** is happening. Joy's skill is explicit that
these are different problems:

- **Positional** (face boxes, safe zones) → **Apple Vision** via `scripts/facedetect.swift`.
  Deterministic pixel rectangles, instant, no pip deps. *A VLM is the wrong tool — it describes, it
  doesn't give reliable coordinates.*
- **Semantic** (what's in the shot, style) → **qwen-video** (local Qwen3-VL). Use it to *motivate*
  a cutaway, never to place a card.

For us the equivalent split is: screenshot geometry (where the UI chrome is) versus what the screen
is showing. Same rule — don't ask a VLM for coordinates.

## Beat sheet before render — the discipline worth stealing

> *"Draft a beat sheet FIRST, review with David, THEN render — and PERSIST it. Renders cost
> minutes; the table costs seconds and is where the editorial decisions get made."*

The persisted `beat-sheet.md` is the **re-runnable recipe** — change the table, re-render, no
re-deriving. It and `source-analysis.json` stay in git; `output.mp4` and fonts stay out.

## What to do next

1. **Don't build a video skill yet** — same pilot-first rule as everywhere else here. Wait until we
   have a real overlay to make
2. When we do, **copy the master project folder**, don't rebuild
3. Adapt `composition-patterns.md` with the token block above, and **name the source in line one**
4. The image catalogue (below) is the prerequisite — b-roll you can't find is b-roll you don't have

→ Image/b-roll catalogue: [`../media/README.md`](../media/README.md)
