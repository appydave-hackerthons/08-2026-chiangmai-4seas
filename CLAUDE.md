# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Status: greenfield

The repo is empty as of 2026-08-01. There is no code, no build, no tests yet — so there are no
commands or architecture to document. **Fill this in as the stack lands**, don't invent it.

## What this is

Hackathon project for **Hacker Fund**, Chiang Mai, August 2026 (`08-2026-chaingmai-4seas`).
Lives under `~/dev/ad/apps/appydave-hackerthons/` — the hackathon folder, separate from the
`/apps/` micro-app family in the parent monorepo `CLAUDE.md`.

Scope, problem statement, and stack are **not yet decided**. More detail is coming from David —
until then, ask rather than assume.

## `raw/` — unprocessed intake

`raw/` holds material pasted in from the clipboard (briefs, notes, specs, transcripts) before it's
been turned into anything. Treat it as **input, not source of truth** — read it, distil it, but
don't let it drift into being the documentation.

Use the `clipboard` skill for the paste → file step; it infers filenames from headings.

## People

| Who | Contact |
|---|---|
| Karlen | karlenchang@gmail.com |
| David Cruwys (AppyDave) | david@ideasmen.com.au |

David also mentioned a possible `@appydave.com` address — unconfirmed, verify before using it.

## Conventions

Inherits the monorepo rules from `~/dev/ad/CLAUDE.md` and `~/dev/.ai-conventions.md`:

- **kebab-case** for markdown filenames (`my-file.md`, never uppercase)
- Language-specific casing for code (snake_case in Ruby, etc.)

## When the project takes shape

Replace the "Status" section above with, at minimum:

- Build / dev / test commands, including how to run a **single** test
- The big-picture architecture — the parts you'd only understand after reading several files
- Anything a hackathon judge or a second contributor would trip over (env vars, external services,
  demo setup)
