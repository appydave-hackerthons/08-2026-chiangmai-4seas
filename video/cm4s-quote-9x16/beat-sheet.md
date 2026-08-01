# cm4s-quote-9x16 — "One quote, held"

**Format** 1080×1920 · 30fps · **15.0s** · no footage, no voiceover — kinetic type only
**Source of truth (words)** `reports/2026-08-01-cm4s-l2-report-001-chiang-mai-lifestyle-v2.json` → `quotes[]`
**Source of truth (look)** `DESIGN.md` — a projection of AppyDave. No invented colours.

## The thesis

She said one line twice. That repetition is the whole edit — not a graphic decision, a
transcript fact. The piece does exactly one thing: let the first saying land plain, then
let the second one land harder, then show what it cost her and what she does about it now.

Everything technical in the demo comes after this. So this opens on a person, and nothing
in it may look like a system.

## Verbatim lines used — all four are `quotes[]` entries, unedited

| # | Line | Why this one |
|---|------|--------------|
| Q1 | "I don't want to waste my time. I don't want to waste my time." | The repetition. Two sentences, one line — the JSON itself preserves the doubling |
| Q2 | "But it's kind of like, it's not look like what they said." | The friction, in her grammar. Promotion vs reality, no paraphrase available that lands better |
| Q3 | "So I just let somebody else go there first." | The workaround she built — a person, not a product. Hands off to whatever the demo shows next |

Her English is non-native. Nothing was tidied. `it's not look like` stays.

## Beat sheet

| ~time | On screen | Move | Motivation |
|---|---|---|---|
| 0.0–0.6 | (nothing) | Cream frame, gold hairline draws L→R, 0→300px | A breath before a person speaks. An empty first half-second buys attention that a text-on-frame-1 open spends |
| 0.6–4.2 | **"I don't want to waste my time."** — Roboto 400, 78px, brown | Fades up + rises 18px, then holds still for 3.2s | The first saying is unemphatic — she says it in passing. 400 weight, no colour, no motion after arrival. 3.6s = well over the 3s readable floor |
| 4.2–8.4 | Second saying appears **below** — Roboto 700, 96px, brown. First saying **dims to `--brand-muted`** | Line 2 fades up over 0.55s; line 1 crossfades to muted at the same instant | The edit's one real move. The second saying is not a new line, it's the same line — so it can't arrive as a new idea. It arrives *bigger and heavier* while the first recedes. Nothing else happens on screen for four seconds |
| 7.5–8.4 | `PARTICIPANT 001 · CHIANG MAI` — Oswald 600, 26px, muted, above the gold rule | Fades in only, no movement | Attribution lands *after* the words, never before. Naming the source first makes it a case study; naming it last leaves it a person |
| **8.4** | — | **Hard cut to dark `#25201e`** — no fade, one frame | The only dark beat in the piece. A cut, not a transition: the disappointment was abrupt for her too |
| 8.5–11.9 | **"But it's kind of like, it's not look like what they said."** — Roboto 400, 64px, cream on dark | Fades up 0.4s, holds 3.0s, cuts out | 3.4s for 12 words. The friction the first quote maps to: the Facebook promotion promised Japanese culture and delivered a food festival |
| **11.9** | — | **Hard cut back to cream** | Symmetry with 8.4. The dark beat is a guest and it leaves the way it arrived |
| 12.0–15.0 | **"So I just let somebody else go there first."** — Roboto 700, 86px, brown | Fades up + rises, holds 3.0s to the last frame | What she built: not an app — a friend who goes first and reports back on LINE. This is the line the rest of the demo answers |
| 13.7–15.0 | `AppyDave` lockup, bottom-left, 44px Bebas Neue — **"Appy" `#342d2d`, "Dave" `#c8841a`** | Fades in under the closing quote, no motion | Brand last and small. **Light-safe two-tone fallback, not the dark chip** — DESIGN.md §2b: the dark chip is wrong on a page that already spent its dark element, and this piece spent it at 8.4 |

## Restraint ledger — what was deliberately left out

- **No colour emphasis on "waste my time."** Yellow is reserved for the human gate; amber is for
  sequences. Emphasis is carried by **weight and size only**. A highlighted phrase would have read
  as a pull-quote graphic, which is the thing this piece is counter-programming.
- **No quote marks, no attribution card, no photo, no b-roll, no counter, no rule under the closing
  line.** Four text moments in fifteen seconds.
- **Two dark beats were considered and cut** — the friction and the close both wanted it. One is
  the rule and one is also better: a second dark frame would make the first one decorative.
- **Q3 held at 3.0s, not trimmed to 2.4s to fit the logo earlier.** Below 3s a phrase flashes.
  The logo waited instead.

## Safe-zone / legibility check

No face in frame, so no `cards_below_y` constraint. The type constraints that replace it:

- Text block left-aligned in a 888px column, 96px page margins — no glyph within 96px of an edge
- Every quote wraps naturally (`max-width`), **no `<br>` in body text** (core rule 6)
- Smallest type on screen is 26px Oswald 600 (attribution) — reads at 1080 wide
- Contrast: `#342d2d` on `#faf5ec` ≈ 13:1 · `#faf5ec` on `#25201e` ≈ 14:1

## Snapshot expectations (`--at 2,5,9,13`)

| t | should show |
|---|---|
| 2 | First saying alone, cream, gold rule. No second line yet |
| 5 | Both sayings — first muted, second brown and heavy. The repetition, mid-land |
| 9 | Dark frame, friction quote in cream |
| 13 | Cream, closing quote. Logo not yet in (arrives 13.7) — an empty lower-left here is correct |
