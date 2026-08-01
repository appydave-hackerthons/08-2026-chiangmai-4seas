# inbox — the temporal stream

Data arriving continuously during the event. Drop files here; don't edit them in place.

**`inbox/` is not `raw/`.** `raw/` holds stable source material for the plan — read once,
rarely changes. `inbox/` is a feed: it accumulates all day, gets consumed, and its contents are
evidence rather than instruction.

```
inbox/
├── captains-log/          conversations streaming out of Captain's Log
└── dev-logs/
    ├── appydave/          David — Claude Code sessions / Angel Eye exports
    └── ethon/             Ethon — Codex sessions
```

One folder per builder. The tool that produced the log doesn't matter — Claude, Codex, whatever
comes next — the folder is owned by the **person**, because that's what stays stable.

## Filename convention

```
<date>-<lineage>-<source>-<slug>.<ext>
```

All lowercase, dash-separated, **date first** so a plain directory listing sorts chronologically —
which is the only ordering temporal data actually wants.

| Segment | Values | Notes |
|---|---|---|
| `date` | `2026-08-14` | ISO, always four-digit year |
| `lineage` | `cm4s-l1` … `cm4s-l5` | `l1` is David + Karlen + Ethon. Use `cm4s-x` if it belongs to no lineage |
| `source` | `claude` · `codex` · `angeleye` · `plaud` · `omi` · `note` | what produced it |
| `slug` | short, dashed | what it is — a session id fragment, a topic, a run number |

Worked examples:

```
inbox/dev-logs/appydave/2026-08-14-cm4s-l2-claude-build-run-1.jsonl
inbox/dev-logs/appydave/2026-08-14-cm4s-l2-angeleye-session-3f9a.json
inbox/dev-logs/ethon/2026-08-14-cm4s-l3-codex-first-pass.md
inbox/captains-log/2026-08-14-cm4s-l3-plaud-b351-interview.md
```

The lineage segment is what makes a flat drop folder queryable — `ls *cm4s-l3*` returns one
participant's whole trail across every source. It matches the slate and title convention in
[`../docs/tag-convention.md`](../docs/tag-convention.md); keep the two in step.

## Rules

- **Never rename or edit a dropped file.** Derived work goes in `docs/`, not here. The value of
  an inbox is that it's a faithful record of what arrived.
- **Unsure of the lineage? Use `cm4s-x` and drop it anyway.** A misfiled log beats a lost one.
- **Anything over ~10 MB doesn't belong in git** — leave it on the machine that made it and drop a
  short pointer file here instead. Session logs are usually small; Angel Eye archives are not.
- Subfolders by date (`2026-08-14/`) are fine once a day gets busy — the filename convention
  doesn't change.
