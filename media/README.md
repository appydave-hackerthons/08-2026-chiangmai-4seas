# media — the b-roll catalogue

Images we can cut into video: app screenshots, UI states, whiteboards, diagrams, moments from the
event. **B-roll you can't find is b-roll you don't have** — the describing is the point, not the
storing.

```
media/
├── README.md        ← the schema
├── catalog.md       one entry per image, described
└── images/          the files
```

## Modelled on what already works

Beauty & Joy solved this at `~/dev/ad/joy/joy-footage/` — `catalog.json` (73 clips, schema v3) plus
`describes/clip-describes.md`. That describe file is the part worth copying: each clip gets
**Setting · Subject & framing · Movement · Audio/content · Usability**, and the *usability* verdict
is what makes it searchable months later. "Excellent b-roll — two great beats in one clip" is a
sentence you can act on. A filename is not.

## Filename

Same convention as `inbox/`, so one rule covers the whole repo:

```
<date>-<lineage>-<source>-<slug>.<ext>
2026-08-14-cm4s-l2-screenshot-dashboard-empty.png
2026-08-14-cm4s-x-whiteboard-funnel.jpg
```

`cm4s-x` when it belongs to no single lineage.

## Every image gets an entry in `catalog.md`

```markdown
## 2026-08-14-cm4s-l2-screenshot-dashboard-empty.png

**Tags:** `screenshot` `ui` `empty-state` `cm4s-l2` `interview-copilot`

**What it shows:** The interview-copilot dashboard before a session starts — three empty agent
panels down the right, a dead transcript pane on the left, one "start listening" control.

**Composition:** Full-window screenshot, 16:9, light UI on cream. Dense in the right third,
generous empty space centre-left — text can sit over the middle without covering anything.

**Usability:** Good establishing shot for "before". Pairs with a populated shot for a
before/after cut. Weak on its own — nothing is happening in it.

**Caveats:** Shows a placeholder participant name; blur before publishing.
```

**Usability and caveats are the load-bearing fields.** Anyone can see what's in an image. What you
can't recover later is *whether it was any good and what would stop you using it.*

## Tag vocabulary

Keep it small, add deliberately.

| Axis | Values |
|---|---|
| Kind | `screenshot` · `whiteboard` · `diagram` · `photo` · `ui` · `terminal` |
| Use | `establishing` · `detail` · `before` · `after` · `hero` · `filler` |
| State | `empty-state` · `populated` · `error` · `success` |
| Lineage | `cm4s-l1` … `cm4s-l5` · `cm4s-x` |
| App | the repo name, e.g. `interview-copilot` |

## Rules

- **Describe on arrival, not later.** An undescribed backlog never gets described — and by then
  nobody remembers what they were looking at.
- **Never invent what an image shows.** If it hasn't been looked at, it has no entry yet.
- **Flag anything needing a blur before it ships** — participant names, faces, API keys in a
  terminal. That's what `Caveats` is for, and it's cheaper here than in a render.
- Screenshots go in at full resolution; the cut can crop, it can't add pixels back.

## The tool split, borrowed from `joy-video`

Two different questions need two different tools, and conflating them is a known failure:

- **Where things are** (safe zones, where text can sit) → geometry. Deterministic.
- **What it shows** (semantic description, the entry above) → a vision model.

Joy's skill is blunt about it: *a VLM is the wrong tool for coordinates — it describes, it doesn't
give reliable pixel rectangles.* Same applies to screenshots.

→ Pipeline recon: [`../docs/video-pipeline.md`](../docs/video-pipeline.md)
