# Team log — what's landing in the system

Newest first. Written for **David, Karlen and Ethon** to read, not for git. Every push adds an
entry here. If something below affects how you work, it says so.

This is the one authored file in `inbox/` — everything else here is dropped, never edited.

---

## 2026-08-01 · First app repo is live — interview-copilot

**https://github.com/appydave-hackerthons/interview-copilot** — public.

Ethan's idea from the lineage-one interview, now a real repo. Seeded with a README; no code yet.

> A dashboard where a team of AI agents co-pilot a live interview — surfacing questions to ask and
> biases to avoid, so the interviewee opens up.

**Ethan** = `gee842` on GitHub (resolved from his email). Invited with **write access** — the
invite is pending until he accepts it from his email.

### New — app dossiers, for Karlen's presentations

`docs/apps/` — one file per micro-app, same shape every time. This is the presentation source: when
you need to talk about any app in the portfolio, it's all in one place.

Each dossier carries: name · one line · the problem · who it's for · what it does · **tech stack** ·
**why this stack** · status · links · lineage · owner.

**Why the fixed shape:** five apps described five different ways can't be presented as a portfolio —
the audience spends attention re-learning the format instead of hearing the content. It also makes
gaps *visible*: an empty section is a question to go and ask, not something that quietly never gets
written.

**The rule that matters: never invent the stack.** `interview-copilot` has "— pending" under both
tech stack and why-this-stack, because the repo holds a README and nothing else. A guessed stack is
a guaranteed wrong answer in a Q&A. It gets filled from the manifest when Ethan pushes.

---

## 2026-08-01 · Logo decided — design system now the full reference

`claude.ai/code/artifact/601c7895-b9f7-443a-b68b-c373ba223692` — updated in place, same link.

**David picked both lockups.** The dark chip is now **primary**; the light-safe two-tone is the
**fallback** for places a dark element would be wrong — inside a light card, a dense header, or a
page that already spent its one dark beat.

The design system page grew into a proper reference — ten sections now:

- Every colour, as swatches **and** as a copy-paste `:root` block (all sixteen tokens)
- **Contrast pairings**, each shown at real weight rather than described
- Both logo lockups at two sizes, on two grounds, with the three "never do this" rules
- Pipeline state, evidence provenance, typography specimens, and the shipping rules

The rule underneath the logo fix, worth knowing before you build anything: **gold and yellow are
the two lightest tokens in the palette and only work on dark grounds.** The brand's "never on
white" line really means *needs a dark ground*.

---

## 2026-08-01 · Logo — four options, needs a decision

`claude.ai/code/artifact/9de1421b-167d-45f9-8556-d3a8f5046868`

The AppyDave logo on the design-system page was wrong twice: it used amber where the spec says
yellow, and it sat gold-and-yellow on a cream ground. Those are the two lightest tokens in the
palette and the contrast table only ever pairs them with brown or dark surfaces — so it washed out.

Four options, all keeping the two-tone split the brand requires. **Option 01, the dark chip, is
the recommendation** — it is exactly the spec on the ground the spec intends.

David to pick; it then goes into `DESIGN.md` and both existing artifacts.

---

## 2026-08-01 · Design system, and a rule about sharing visual work

**Two shareable links now exist.** Both are private until someone hits share.

| | Link |
|---|---|
| System views — the loop, control plane, build order, lineage one | `claude.ai/code/artifact/00f219bf-ac4c-4799-94fb-e70d39acacd5` |
| **Design system** (new) | `claude.ai/code/artifact/601c7895-b9f7-443a-b68b-c373ba223692` |

### New — the design system

`DESIGN.md` at the repo root is now the canonical token file, with the visual version published
at the link above. It is a **projection of AppyDave, not a new brand** — every colour and typeface
is inherited unchanged.

What it settles, so nobody has to re-decide it mid-build:

- The twelve-colour palette, and the four status colours for pipeline state
- **Evidence provenance** — *said* renders solid and full-contrast, *inferred* renders outlined and
  muted. Inference is always quieter than evidence. This is the one piece unique to this project
- Four typefaces, one job each. Roboto Mono carries every lineage code, capture code and filename
- Yellow is reserved for the human decision gate. Nothing else

**If you build a participant app:** inherit colour and type, let the scaffold own layout — and if
the participant has their own brand, theirs wins. Say so in the handover rather than overriding
them quietly.

### New rule — visual work ships as an Artifact

A local `.html` file is invisible to everyone but the machine it sits on. Anything visual gets
published as an Artifact so the team can actually see it.

**Publishing is not sharing.** Artifacts start private; sharing is a deliberate step from the
page's share menu, and it's the author's job to remember. Now written into `DESIGN.md` §5.

### New — lineage one's discovery record

`docs/lineage-1.md`, from the live interview. Evolving.

- **Ethon** is building an always-listening **interviewer co-pilot** — surfaces live data and
  clarifying questions to the interviewer mid-conversation. The problem: *people don't know what
  they want*, and not every interviewer can extract it
- **Karlen** owns downstream — document frictions, find patterns, generate ideas by method, and
  define what a good idea actually is, judged against the hackathon themes plus the 20-point
  criteria

**Two things we need and don't have:** the **20-point criteria** and the **hackathon themes**.
Both were referenced as if they exist. Everything downstream of idea selection depends on them —
worth chasing early.

Also flagged: the co-pilot only pays off *while interviews are still happening*. Built mid-event
it arrives too late to help this event. That's a real build-order decision.

---

## 2026-08-01 · Inbox opened

`inbox/` is the drop folder for everything arriving during the event.

```
inbox/
├── captains-log/          conversations streaming out of Captain's Log
└── dev-logs/
    ├── appydave/          David — Claude Code / Angel Eye
    └── ethon/             Ethon — Codex
```

**Folders belong to people, not tools** — so they stay put if either of you switches.

**Filename:** `<date>-<lineage>-<source>-<slug>.<ext>` — lowercase, dashes, date first so a plain
listing sorts chronologically.

```
2026-08-14-cm4s-l2-claude-build-run-1.jsonl
2026-08-14-cm4s-l3-codex-first-pass.md
```

The lineage segment does the work: `ls *cm4s-l3*` returns one participant's whole trail across
every source and both builders.

- Never rename or edit a dropped file — derived work goes in `docs/`
- Unsure of the lineage? Use `cm4s-x` and drop it anyway. Misfiled beats lost
- Over ~10 MB doesn't belong in git — drop a pointer file instead

---

## 2026-08-01 · Plugin research — we are not stubbing twenty skills

Full reasoning in `docs/plugin-plan.md`. Short version: four independent sources say build the
distribution envelope now and let the pilot decide what goes inside it.

- The brain's own plugin strategy: *a plugin can ship with exactly one skill* — single-skill stops
  you over-building a suite before the extra skills are proven
- Skill listings have a **~1% context budget**. Past it, descriptions silently drop and skills go
  invisible to auto-routing — they still run when named, but the model stops choosing them
- AppyTron and AppySentinel both state, independently: *recipes are byproducts of pilots, not
  speculative features*

A live example sits in David's own catalog: the `appydave` plugin carries **97 skills**. The
healthy siblings are 3–11.

**Still open:** the marketplace name. Proposed `cm4s@appydave-hackerthons`, in a repo separate from
`appydave-plugins` — because Karlen and Ethon need write access to hackathon skills without
getting access to 97 internal ones.

---

## 2026-08-01 · Lineage tagging — the original plan didn't work

`docs/tag-convention.md`. **Tags cannot be set when a capture is created.** The create endpoint
takes no tags field, and the enricher drops any tag not already in the ontology.

So lineage separation runs on two things we *do* control:

1. **A spoken slate** at the top of every recording — *"Chiang Mai 4 Seas. Lineage two. Participant
   Ethon. Interview one."* It reaches the transcript, then the synopsis, and is findable by keyword.
   Say it **identically every time** — improvising is what breaks it
2. **A title convention** for captures we author: `CM4S-L2 · factsheet`

Verified live. Still open: adding `cm4s` to the capture ontology, which would give real tags
instead of only keyword matches.

---

## 2026-08-01 · Repo opened, gates checked

`github.com/appydave-hackerthons/08-2026-chiangmai-4seas` — **private**.

Three pre-work gates were checked against running systems:

| Gate | Result |
|---|---|
| Captain's Log | **Cleared** — live, tools confirmed, transcripts and search all work |
| Angel Eye | **Blocked** — no MCP server exists yet. The HTTP API does list sessions per project |
| AppyTron | **Already done** — the recon the plan asked for already exists as `CONTEXT.md` |

On Angel Eye: the missing cross-session index is **not** on our critical path. We control project
names, so each lineage already knows its own sessions — a thin wrapper is enough.
