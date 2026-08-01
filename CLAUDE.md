# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Status: pre-planning

No application code yet. The repo currently holds source material, a recon, and a visual artifact.
**Fill this in as the stack lands** — don't invent commands or architecture that don't exist.

## What this is

Hackathon project for **Hacker Fund**, Chiang Mai (4 Seasons), August 2026.

The system listens to human and machine traces, discovers opportunities inside them, and turns
selected opportunities into working micro-apps. Two evidence sources with different jobs:

- **Captain's Log** — upstream, human traces (Plaud / Omi / Whisper). What might be worth building.
- **Angel Eye** — downstream, machine traces (Claude Code / Codex sessions). What actually happened
  during the build.

Six phases: Discover → Evaluate → Define → Build → Analyse → Productise. A **human decision gate**
sits between Evaluate and Define — the system never goes from interview straight to build.

Repo: `github.com/appydave-hackerthons/08-2026-chiangmai-4seas` (private).
Local folder is `08-2026-chaingmai-4seas` — note the transposition; the repo name is corrected.

## Team

Three people. Lineage one is the team itself; four participant lineages follow.

| Who | Owns | Contact |
|---|---|---|
| **David Cruwys** | Building the AI applications | david@ideasmen.com.au |
| **Karlen** | Interviews, interview questions, customer journey, lean canvas, marketing presentation | karlenchang@gmail.com |
| **Ethon** | Building the AI applications | — |

David and Ethon take **parallel paths** on the build side and deliberately do things their own way,
then compare where they converge.

> Spelling: **Karlen**. The source doc in `raw/` says "Carlan" throughout — that's the transcript's
> error, left verbatim because `raw/` is unprocessed intake. Use Karlen everywhere else.

## Gate status — verified 2026-08-01

| Gate | State | Detail |
|---|---|---|
| Captain's Log MCP | **Cleared, one gap** | Live on :7101, **8 tools since 2026-08-01 (`c2436ba`): `capture_create` is now on the MCP surface** (earlier 7-tool reading was a pre-T40 connection — reconnect to see it; proven live by capture B344). No participant/entity field. **Tags are not settable at capture time** and off-ontology tags are dropped — lineage separation runs on a spoken slate + title convention instead. See `docs/tag-convention.md`. CL-side asks route via `docs/agents.md` → captain-swag. |
| Angel Eye MCP | **Blocked** | No MCP server exists. HTTP API lists sessions by project and returns per-session events. Missing: cross-session query, and decisions (notes 0/2083). |
| AppyTron recon | **Already done** | `~/dev/ad/apps/appytron/CONTEXT.md` is the recon. See `docs/recon.md`. |

For the hackathon specifically, the Angel Eye cross-session index is **not** on the critical path —
we control project names, so each lineage knows its own sessions. The thin MCP wrapper alone
unblocks phase 05.

## Layout

```
raw/    unprocessed intake — verbatim, read it, don't treat it as truth
docs/   recon.md (the three scaffolds) · system-views.html (the artifact)
```

`docs/system-views.html` is published as an artifact and **must be kept current** — republish it
whenever the team, gates, or plan change.

## Conventions

- Inherits `~/dev/ad/CLAUDE.md` and `~/dev/.ai-conventions.md` — **kebab-case** markdown filenames.
- Any HTML/visual output uses the **AppyDave brand**: load the `brand-dave:brand` skill *and* read
  `references/appydave/DESIGN.md` and `context-guide.md`. Non-negotiables that have already been got
  wrong once: light-first for every viewer (`color-scheme: light`, no `prefers-color-scheme: dark`
  block), real Oswald/Roboto/Bebas embedded as data URIs since the artifact CSP blocks font CDNs,
  and no invented colours — status colours come from `brand-style-guide.md`.
