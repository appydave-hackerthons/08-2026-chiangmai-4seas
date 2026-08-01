# video — four 15-second pieces

Built by parallel agents from real report-001 data. **Nothing has been rendered** — beat sheets
and frames only, so the edit gets reviewed before minutes are spent.

| Folder | Idea | Format | Frames |
|---|---|---|---|
| `cm4s-quote-9x16` | One quote, held — the human open | 9:16 | 4 |
| `cm4s-funnel-16x9` | The funnel narrowing — the factory | 16:9 | 4 |
| `cm4s-evidence-16x9` | The evidence base forming — the product | 16:9 | 2 |
| `narration/` | Scripts + Kokoro audio for all four, incl. the report idea | — | 4 wav |

Each project holds `beat-sheet.md` (the reviewable recipe — edit the table, re-render, no
re-deriving) and `public/index.html`. Contact sheets are at
`<project>/public/snapshots/contact-sheet.jpg`.

## To render one

```bash
cd video/<project>
npx hyperframes lint public
PRODUCER_BROWSER_GPU_MODE=hardware npx hyperframes render public -o output.mp4 --fps 30
```

`output.mp4`, fonts and vendor files stay out of git. `beat-sheet.md` stays in — it's the recipe.
