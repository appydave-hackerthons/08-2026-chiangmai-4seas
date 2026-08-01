# interview-copilot

**Last assessed:** 2026-08-01, commit `e621b69` — MVP shipped, stack now known.

## Name

`interview-copilot`. Spoken as "the interview co-pilot".

## One line

Ethan's own: *"Local-first AI research partner for live interviews."*

Fuller: a dashboard where specialist agent lenses read a live interview transcript and quietly
place useful next moves beside the interviewer — without interrupting the conversation.

## The problem

> **Said (Ethan):** People don't know what they want. A good interviewer can extract needs out of
> people, or get them to realise problems they have — but not everyone has that skill.

From his MVP contract: *"The memorable moment is not a chatbot response. It is watching the
interview turn into a living evidence base in real time."*

## Who it's for

The **interviewer**. The interviewee never sees it.

## What it does

Five **specialist lenses** read a shared evidence pool:

| Lens | Watches for |
|---|---|
| **Clarification** | Missing frequency, cost, recency, concrete examples |
| **Opportunity** | Repeated work, paid workarounds, urgency, unmet need |
| **Bias guard** | Leading questions, premature solutioning |
| **Memory** | Connects or challenges statements already in the pool |
| **Research** | What needs external validation — *must not invent sources* |

Flow: pick a template → transcript arrives by microphone or typing → facts, pains, quotes,
workflows, tools and questions get extracted → lenses suggest → the interviewer pins, promotes,
dismisses or expands → ends with an evidence-backed report and a least-effort next step.

## Tech stack

| Layer | Choice |
|---|---|
| **Backend** | Python ≥3.11 · FastAPI · uvicorn · pydantic v2 · httpx · python-multipart |
| **Packaging** | `uv` (uv.lock committed) · hatchling build backend |
| **Frontend** | React 19 · TypeScript 5.9 · Vite 7 · lucide-react |
| **Styling** | Plain CSS — one 245-line `styles.css`, no framework |
| **Agent runtime** | **opencode**, model `openai/gpt-5.6-sol` |
| **Tests** | pytest + pytest-asyncio, `asyncio_mode = auto` |
| **Tasks** | Makefile — `install · backend · frontend · dev · build · start · test · check` |

Modules: `app.py` (FastAPI) · `models.py` (pydantic) · `opencode_runtime.py` · `fallback.py` ·
`transcription.py`. Frontend: `SetupScreen · TranscriptPanel · EvidencePanel · ActivityPanel ·
ReportView`.

## Why this stack

Partly stated, partly inferred — **ask Ethan to confirm the inferred rows before they go on a slide.**

- **Every agent tool disabled** in `opencode.json` — bash, edit, write, read, grep, glob, webfetch,
  websearch, task, all `false`. The lenses reason over the transcript and can touch nothing else.
  For a tool that listens to a stranger's interview, that is a deliberate and good call. *(Read from
  config; rationale not stated.)*
- **One bounded model call per cycle, not five.** *Stated:* the lenses share a single call while
  keeping explicit agent attribution — *"avoiding the latency and cost of five independent calls.
  The contract can later fan out without changing the frontend or evidence model."*
- **`fallback.py` (195 lines)** — the app still works when opencode isn't available. Sensible for a
  demo that must not die on stage. *(Inferred.)*
- **Local-first** — his own framing in the package description. No hosted dependency.
- React 19 + Vite 7 + plain CSS, no UI framework — *inferred:* fast to build, nothing to fight.

## Status

**MVP shipped** 2026-08-01. ~4,500 lines. Backend, frontend, tests and a Makefile all present.
Not yet run or reviewed by us.

## Links

- Repo — https://github.com/appydave-hackerthons/interview-copilot (public)
- MVP contract — `docs/MVP.md` in the repo
- Deployed / demo — *pending*

## Lineage

`CM4S-L1` — the team's own lineage. Ethan's idea, from the 2026-08-01 interview
([`../lineage-1.md`](../lineage-1.md)).

**For a presentation:** this app is *recursive* — a tool that improves the very process that
produced it. That's the closed loop the demonstration wants, happening naturally.

## Owner

**Ethan Ooi** (`gee842`) — build lead.

## What his MVP doc settles that our plan hadn't

His **evidence rules** arrive independently at the discipline we wrote into `DESIGN.md`:

> *"Agent suggestions are not facts until pinned, and remain labelled as agent material after
> pinning."*
> *"External claims require a real URL; absent web retrieval, the research lens should propose a
> search rather than fabricate a result."*
> *"Confidence communicates extraction certainty, not objective truth."*

That is our said-versus-inferred split, and evidence-before-invention, written by someone who
hadn't read our docs. Two independent arrivals at the same rule is the strongest signal we have
that it's the right one.

## Correction to an earlier note

The seed README I wrote proposed **separate agents per concern**, reasoning that one model asked
to do three jobs does the easiest and drops the rest. Ethan's design keeps **per-lens attribution
while sharing one call**, with fan-out available later behind an unchanged contract. That's the
better MVP answer — it buys the attribution without paying five times for it. My note was wrong;
his design stands.

## Open questions

- **Microphone or typed transcript** — both are in the flow; which is the demo path?
- `transcription.py` exists — what does it use, and does it handle non-English?
- Does anything connect to Captain's Log yet, or is the evidence pool self-contained?
- What is the "least-effort next step" the report ends on — and could it hand straight into the
  fact-sheet stage of our funnel?
