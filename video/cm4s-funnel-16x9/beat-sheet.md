# cm4s-funnel-16x9 — beat sheet

**The funnel narrowing.** The whiteboard of 2026-08-01, animated. Many opportunity cards go in, a
**human** judges, a handful survive, a few get built. 15.0s · 1920×1080 · 30fps · no audio, no footage
— this is a pure motion-graphics board.

- **Source of the content**: `docs/board-2026-08-01.md` (the photographed whiteboard)
- **Source of the numbers**: `reports/2026-08-01-cm4s-l2-report-001-chiang-mai-lifestyle-v2.json`
  (10 pain points · 24 key facts · 12 unanswered questions) and `story-deck.html` (the 18/20 score,
  criteria Real · New · Good · Feasible)
- **Source of the colour**: `DESIGN.md` → a projection of AppyDave. Nothing here is invented.

## The one editorial argument

A funnel that narrows on its own is a filter. A funnel that narrows *because someone decided* is a
factory. So the yellow — the single reserved colour in the whole system — is spent on one element
and one only: the **JUDGE** gate. And the 13 cards that don't survive **fade to 16%, they never
vanish**: superseded is not deleted, and the board still shows them.

## Beats

| # | Time | What happens | Why | On screen |
|---|---|---|---|---|
| — | 0.0–0.6 | Cream board, header wipes in. Stage rail sits dormant at 22% | Establish the board before anything moves on it | Kicker, title, `CM4S-L2 · 2026-08-01`, six dim stage ordinals |
| 1 | 0.6–2.2 | `01 QUESTIONS` lights. Evidence column counts in: **10 · 24 · 12** | The funnel starts with one real interview, not a prompt. Concrete numbers buy the rest of the claim | Left column: 10 pain points / 24 key facts / 12 open questions. `02 FACT SHEET` lights at 1.5 |
| 2 | 2.2–2.8 | `03 ELABORATIONS` lights; the widening label appears over the empty field | The board's new step — you cannot narrow well from a set that was never wide | Amber `ELABORATIONS →` above the card field |
| 3 | 2.8–4.6 | `04 OP CARDS` lights. **18 cards stagger in**, two rows of nine, left to right | The deliberately wide search space. It should feel like more than you can hold | 9×2 grid of blank linen cards, hairline bracket drawing beneath |
| 4 | 5.4–7.6 | `05 JUDGE` lights. The **yellow gate** wipes across the full width. Criteria land one by one | The turn. This is the human decision gate, and it is the only yellow in the piece | Yellow band: `JUDGE` + `A HUMAN DECIDES` + `REAL · NEW · GOOD · FEASIBLE` chips |
| 5 | 8.0–9.2 | The pass: **13 cards fade to 16%** in place (fast stagger). 5 lift, gain a brown rule and a check | The core point, twice: a person chose, and the losers stay visible. Fading ≠ deleting | Grid splits into faint and solid without changing shape |
| 6 | 9.6–11.6 | Five survivor chips assemble below the gate; **`18/20`** lands on the first; `HOT` pill last | The shortlist, and the one score we actually have. The rest stay unlabelled rather than invented | `PROOFPASS 18/20` + four unlabelled checked chips + `HOT` |
| 7 | 11.8–12.9 | `06 BUILD` lights. Build lane fills, five segments left to right | Where the funnel ends: runnable things, not a backlog | Segmented amber-ruled lane under the shortlist |
| 8 | 13.2–14.2 | Closing line resolves under the board | Names the rule the animation just demonstrated, so it survives the scroll | `SUPERSEDED IS NOT DELETED — THE FADED CARDS STAY ON THE BOARD` |
| — | 14.2–15.0 | Hold on the finished board | Let the whole funnel be read at once in the final frame | Everything, at rest |

## Colour discipline (checked against DESIGN.md §2)

| Element | Token | Why it's allowed |
|---|---|---|
| Stage ordinals `01`–`06` | `--brand-amber` `#c8841a` | A genuine numbered sequence — the one earned case |
| JUDGE gate | `--brand-yellow` `#ffde59` | The human decision gate. Reserved, spent once |
| Cards, surfaces | `--brand-linen` / `--brand-surface` | Neutral field |
| Faded losers | same tokens at 16% opacity | Superseded, not deleted — no new colour |
| Text | `--brand-brown`, `--brand-muted` | Never pure black |

**No logo.** The AppyDave lockup demands yellow for "Dave", and yellow is spent on the gate. A
single-colour logo is a different mark, not a quieter one — so the piece signs off with an Oswald
kicker instead. Deliberate, per §2b.

## Build notes

- **One `.clip` card-host** spans the whole 0–15s and holds the entire board. Everything inside is
  plain DOM animated by GSAP, so `visibility` is never touched on a `.clip` and there is only one
  track — no `overlapping_clips_same_track` surface at all.
- Light-first is pinned (`color-scheme: light`); there is no `prefers-color-scheme` block anywhere.
- Fonts are local woff2 in `public/fonts/`, `@font-face`'d — the renderer's CSP blocks CDNs. Every
  `font-family` lists concrete names, never `var(...)`, because the renderer's resolver does not
  expand CSS custom properties.

## Verify

```bash
cd video/cm4s-funnel-16x9
npx hyperframes lint public
npx hyperframes snapshot public --at 2,5,9,13 --no-end --describe false
```

`2` = evidence only · `5` = the wide field · `9` = judged, losers faded · `13` = built + closing.
