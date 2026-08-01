# cm4s-evidence-16x9 — beat sheet

**Idea 1 — "The evidence base forming."** The product demo. Ethan's framing: *"The memorable moment
is not a chatbot response. It is watching the interview turn into a living evidence base in real
time."*

| | |
|---|---|
| Canvas | 1920 × 1080, 30 fps, **15.0 s** |
| Concept | screen-recording of the CM4S console — no camera, no talking head, no audio |
| Source data | `reports/2026-08-01-cm4s-l2-report-001-chiang-mai-lifestyle-v2.json` |
| Palette | CM4S `DESIGN.md` → a projection of AppyDave. Cream `#faf5ec`, brown `#342d2d`, gold, yellow, amber, muted. **Nothing invented.** |
| Type | Bebas Neue (logo only) · Oswald (labels, uppercase) · Roboto (body) · Roboto Mono (data, timestamps) |

## The compression

20 minutes of real interview → 9.8 seconds of screen time. The header clock is the honest scale
marker: it runs `00:00 → 20:00` while the two feeds fill. Everything on screen is real data.

## Known limitation, designed around

`source_turn_ids` is **empty on all 45 evidence items**. There is no way to draw a line from a card
back to the turn that produced it, so **no such line is drawn**. Cards land *while* the transcript
advances — adjacency in time, never a claimed causal link. The one lineage claim the data *does*
support is `source`: `transcript` (verbatim) vs `agent` (synthesised), and that ships as the
SAID / INFERRED provenance pill from `DESIGN.md` §2.

## Layout

```
┌ header ────────────────────────────────────────────────── 00:00 / 20:00 ┐
│ [AppyDave chip]  CM4S-L2 · REPORT 001 · CHIANG MAI LIFESTYLE            │
├── gold progress rule (0 → 100% across the run) ─────────────────────────┤
│ TRANSCRIPT (720)  │ EVIDENCE BASE (620)   │ COVERAGE (388)              │
│ 157 turns         │ 45 items              │ 6 phases                    │
│ turns stream in,  │ cards materialise,    │ ordinals 01–06 amber        │
│ list scrolls up   │ stack scrolls up      │ bars fill green as met      │
│                   │                       │ ── 4 of 6 · score 67        │
└─────────────────────────────────────────────────────────────────────────┘
```

## Beats

| Time | What happens | Why | On screen |
|---|---|---|---|
| **0.0–0.9** | Cream canvas. Header rule draws left→right. Logo chip fades in. Three panel columns fade up **empty**. | Establish the surface as a *tool*, not a slide. Empty is the point — the value is what fills it. | Chip · `CM4S-L2 · REPORT 001 · CHIANG MAI LIFESTYLE` · clock `00:00 / 20:00` |
| **0.9–1.6** | Column headers land staggered: TRANSCRIPT / EVIDENCE BASE / COVERAGE. Counters read `0`, `0 / 45`, `0 of 6`. | Name the three things before they move, so the eye knows where to look for the next 10 s. | Oswald caps + gold hairlines; six coverage rows sit pending (`--st-pending`) |
| **1.6–11.4** | **THE RUN.** Clock counts `00:00 → 20:00`; gold progress rule fills. 15 real transcript turns stream into the left column, the stack translating up as it overflows. 10 real evidence cards materialise on the right in waves (scale 0.94→1, `back.out(1.4)`). The `n / 45` counter climbs. Four of the six coverage bars sweep to complete. | The whole video. Left is *input*, right is *what the system made of it*, centre column is the transformation happening at interview speed. Nothing here is a mock — every string is from the JSON. | See card order below |
| **11.4–12.5** | **LAND.** Last card settles. Coverage summary pops to **4 of 6**; the two unmet phases stay visibly open in `--st-pending`. Score chip counts to **67** and holds. | The honest ending. A demo that lands on 6/6 is a mock; landing on 4/6 with two named gaps is the product telling the truth about its own coverage. | `4 of 6 phases` · `SCORE 67` · rows 01 and 06 still hollow |
| **12.5–15.0** | **CLAIM.** A cream veil at 0.92 fades over the console — the finished evidence base ghosts through it. Headline + subline rise; the AppyDave dark chip sits under them. | Say the thesis once, over the proof, not instead of it. | *"20 minutes of interview. 45 pieces of evidence."* / *"Built while the conversation was still happening."* |

## Card order — real items, real arc

Adjacent to the transcript in time only. Provenance pill from `source`.

| # | at | id | type | provenance | copy (verbatim, trimmed where marked ⋯) |
|---|---|---|---|---|---|
| 1 | 2.5 | `quote-01` | QUOTE | SAID | "It makes me more relaxed and also for praying. And also I love to take a picture." |
| 2 | 3.3 | `fact-01` | FACT | INFERRED | The participant visits Chiang Mai temples for relaxation, prayer, and photography. |
| 3 | 4.3 | `quote-03` | QUOTE | SAID | "But it's kind of like, it's not look like what they said." |
| 4 | 5.1 | `pain-02` | PAIN | INFERRED | The Japanese festival's performances felt contemporary rather than representative ⋯ |
| 5 | 6.1 | `quote-04` | QUOTE | SAID | "I feel that I shouldn't waste my time to be here." |
| 6 | 6.9 | `fact-14` | FACT | INFERRED | They will not attend when the promotional post or image appears AI-generated. |
| 7 | 7.9 | `quote-05` | QUOTE | SAID | "So I just let somebody else go there first." |
| 8 | 8.7 | `pain-07` | PAIN | INFERRED | The participant relies on a friend to assume the risk of attending first ⋯ |
| 9 | 9.6 | `fact-12` | FACT | INFERRED | Does not attend many events, describes themselves as selective ⋯ |
| 10 | 10.5 | `insight-01` | INSIGHT | INFERRED | ⋯ may value a lightweight credibility layer showing recent, real attendee evidence. |

Arc: **the thing that works** (temples) → **the thing that broke** (festival) → **the distrust** →
**the workaround** (send a friend) → **the opportunity**. That is the interview's actual shape, not
an imposed one.

## Coverage rows — verbatim from `coverage[]`, ordinals from `template.phases`

| # | phase | met | fills at |
|---|---|---|---|
| 01 | Recent context & desired outcome | **no** | — stays pending |
| 02 | Underlying why | yes | 3.6 |
| 03 | Current reality | yes | 5.4 |
| 04 | Expectation gap | yes | 7.2 |
| 05 | Friction & attempts | yes | 9.0 |
| 06 | Consequence & priority | **no** | — stays pending |

Complete = `--st-complete` `#22c55e`. Pending = `--st-pending` `#b8a070`, hollow track. Per
`DESIGN.md`, state reads by **shape as well as hue** — a filled bar versus an empty one.

## Rules honoured

- **Light-first.** `color-scheme: light` pinned. No `prefers-color-scheme: dark`, no `data-theme`.
- **One dark element.** The AppyDave logo chip `#25201e`, and nothing else.
- **Yellow is reserved.** `--brand-yellow` appears twice only: the "Dave" half of the wordmark, and
  the score chip's underline — the closest thing here to a human decision gate.
- **Amber only for the six phase ordinals.** Never a button, never a fill.
- **No invented colours.** Every hex traces to `DESIGN.md` §1 or §2.
- Fonts are local woff2, `@font-face`'d — the renderer's CSP blocks CDNs. Body `font-family` lists
  concrete names, never `var()`.
- Paint order is DOM order. Clip elements animate `opacity` / `scale` only — never `visibility`.
- All twelve palette tokens defined in `:root` even where unused; an undefined custom property
  renders as invisible text.

## Not in this cut

- **No audio.** Silent by design — this plays in a room, on a loop, behind a person talking.
- **No cursor, no fake clicks.** Nobody is driving it; the system is doing the work.
- **No causal lines** between transcript and evidence. See the limitation above.
