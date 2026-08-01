# Lineage tagging — finding and proposed convention

Investigated 2026-08-01 against the running Captain's Log and its source.

## The premise of step 1 is wrong

The plan says *"tags must be applied at capture time"*. **Tags cannot be set at capture time.**
There is no path — MCP or HTTP — that accepts them.

`CreateCaptureBody` (`server/src/routes/captures.ts:317`) accepts exactly five fields:

```
text        required
title       optional
createdAt   optional
externalId  optional
source      optional, must be the literal 'api'
```

No `tags`. Tags are **produced** by the enrich step, not supplied to it — `POST /api/captures`
runs resolve → clean → enrich → code → index synchronously and *returns* `{ code, sourceId,
signal, tags }`.

Two further constraints found in `server/src/enrich/index.ts`:

- **Tags are enforced against the ontology.** Each model-proposed tag is normalised (alias →
  canonical) and kept only if approved. Off-ontology tags are **dropped** from the record and
  pushed to a suggestion queue. So an invented tag like `cm4s-p1` would silently vanish.
- The enrich prompt does permit product / brand / project / person names, but enforcement still
  applies afterwards. Permission in the prompt is not survival in the record.

Also: `capture_create` is **not exposed** in this session's MCP surface — 7 tools are available,
not the 8 previously reported. The HTTP endpoint exists; the MCP tool is not reachable from here.

> **Superseded 2026-08-01 (captain-swag):** `capture_create` shipped to the MCP surface that same
> morning (`c2436ba` in captains-log). The 7-tool reading was a connection made before the server
> picked the change up — new connections see 8 tools. Proven live end-to-end: capture **B344**
> (`CM4S-L1 · agent · captain-swag`) was created over MCP and round-trips via `q: "CM4S"`. The
> step-1 done-condition is now achievable except the find-by-*tag* leg, which still waits on the
> `cm4s` ontology decision below.

## What does work

Verified live: `captures_search` with `q: "hackathon"` returned B343 — last night's conversation —
matching on **synopsis**, which the enricher writes from the transcript. `q` covers title,
synopsis and tags.

That gives two mechanisms we actually control:

### 1 · Spoken slate — the primary mechanism

For Plaud / Omi recordings we control neither title nor tags, but we do control **what is said**.
Open every recording with a slate, exactly as film does:

> "Chiang Mai 4 Seas. Lineage two. Participant Ethon. Interview one."

It lands in the transcript, the enricher carries it into the synopsis, and `q: "lineage two"` or
`q: "4 seas"` finds it. Costs three seconds per recording and needs no code change.

**Say it clearly and identically every time.** The mechanism is exact-ish string matching against
a machine transcription — improvised phrasing is what breaks it.

### 2 · Title convention — for captures we author

Where we create captures over the API (fact sheets, opportunity cards, selection records), `title`
*is* caller-settable. Use:

```
CM4S-L2 · interview · Ethon
CM4S-L2 · factsheet
CM4S-L2 · opportunity · 03
CM4S-L2 · selection
```

`q: "CM4S-L2"` then returns that lineage's whole artifact trail.

## Vocabulary

| Axis | Values |
|---|---|
| Event | `CM4S` — Chiang Mai 4 Seasons, Aug 2026 |
| Lineage | `L1` David + Karlen + Ethon · `L2`–`L5` participants |
| Stage | `interview` · `factsheet` · `opportunity` · `selection` · `requirements` · `build` · `product` |

Lineage, not participant name, is the primary key — names are transcribed unreliably (the corpus
already contains "Carlin" for Karlen).

## Open decision — needs David

To get real *tags* rather than only `q` matches, `cm4s` must be added to the capture ontology at
`~/.config/appydave/capture-ontology.json` (912 terms, 11 areas). The natural shape:

```json
{ "canonical": "cm4s",
  "aliases": ["chiangmai-4seas", "chiang-mai-4-seasons", "4seas"],
  "type": "topic",
  "area": "project" }
```

plus `cm4s` appended to the `project` area's `topics` list, and optionally `karlen` / `ethon` as
`person` terms.

**Not done — this is a global config other systems read.** Awaiting a go.

Without it the slate + title convention still works; we just search by `q` rather than filter by
`tag`, which is a smaller, slower handle but sufficient for five lineages.

## Status against the step-1 done-condition

The stated condition was: create a test capture, find it by tag, retrieve it by `capture_get`.

- Find by tag — **not achievable** as specified; tags are not settable and `cm4s` is not in the
  ontology.
- Create a test capture — **not achievable from here**; `capture_create` is not in the MCP surface.
- `q` round-trip — **verified** on real data (B343).
