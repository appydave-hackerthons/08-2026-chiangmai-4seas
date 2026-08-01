# Coordination Playbook — Nimman Hackathon

This is the playbook for how the three of us (Karlen, Ethan, Dave) coordinate during the hackathon. It answers: who does what, when, how, and what gets shared where.

Read this first if you're joining mid-hackathon.

---

## The team

| Person | Role | What they own |
|--------|------|---------------|
| Karlen | Story creation factory | Ingests everything as it arrives. Weaves the three-layer story arc. Updates `extracted-stuck-points.md` and `demo-script.md` in real time. |
| Ethan | Interview process | Runs 5-min dynamic interviews. Surfaces stuck points, workarounds, smallest steps. Pushes for workaround-rich answers, not surface. |
| Dave | Factory automation experiments | Captures whatever artifact emerges. Could be code, mockup, paper prototype, framework diagram. Whatever the moment calls for. |

---

## The shared workspace

**`~/workspace/nimman-hackathon/`** is the single source of truth. Everyone reads from and writes to the same folder.

When something happens:
1. Person does their work (interview, build, story)
2. Files get written to this folder
3. Git commit + push happens (in background — you don't need to think about it)
4. Team pulls to see updates

If you're not sure where to put a file, ask Karlen.

---

## The clock

| Time | Phase | Who's doing what |
|------|-------|------------------|
| 1:30–2:00 | Interviews 1–2 | Ethan interviews, Karlen captures |
| 2:00–2:30 | Interviews 3–4 | Ethan interviews, Karlen captures |
| 2:30–3:00 | Interview 5 + capture | Ethan interviews, Karlen weaves |
| 3:00–3:30 | Synthesis + ideation | Whole team in `extracted-stuck-points.md` |
| 3:30 | Decision moment | Karlen writes to `decision.md` |
| 3:30–4:30 | Build | Dave captures the artifact |
| 4:30–5:00 | Demo polish + run | Whole team |

Adjust as needed. The clock is a guide, not a prison.

---

## Where to put what

| File | When | Who | Why |
|------|------|-----|-----|
| `interviews/interview-NN.md` | After each interview | Ethan | Raw transcript |
| `interviews/extracted-stuck-points.md` | After each interview | Karlen | Pattern matching, story input |
| `decision.md` | At decision moment (~3:30) | Karlen | What we're demoing + why |
| `demo-script.md` | Continuously | Karlen | Three-layer arc, fill placeholders |
| `artifacts/sketch-NN.md` | As ideas emerge | Dave | Visual artifacts |
| `artifacts/README.md` | After decision | Karlen | What we built, why |
| `factory/README.md` | End of hackathon | Karlen | How to run this again |

---

## How to write a file for the team

**Don't think about git.** Just write the file. The git push happens in the background.

If you write a file in the wrong place, Karlen moves it (and tells you where it landed).

If you want to capture a quick thought that doesn't fit a template, drop it in `interviews/extracted-stuck-points.md` under the right person — Karlen will triage.

---

## How interviews flow

**Ethan runs them. Karlen listens and captures.**

Per-interview loop:

1. **Ethan** interviews one person (5 min, dynamic, see `interview-script.md`)
2. **Ethan** writes transcript to `interviews/interview-NN.md` immediately after
3. **Karlen** extracts:
   - Stuck point (one sentence)
   - Smallest step (verbatim)
   - Best quote (verbatim, with emotion)
   - Workaround (what they're already doing)
4. **Karlen** writes to `interviews/extracted-stuck-points.md`
5. **Karlen** captures one story beat (a moment that lands) for `demo-script.md`

If Ethan and Karlen are in the same room, this can be verbal ("write this down: '...'"). If remote, Ethan texts/voice-notes the raw transcript fast.

---

## How ideation flows

After 5 interviews, ~3:00pm:

1. **Karlen** reads `extracted-stuck-points.md`, names the dominant stuck (what 3+ share) and the outlier stuck
2. **Whole team** ideates 15-25 micro app ideas (~15 min)
3. **Karlen** picks the strongest 2-3 ideas that fit the story
4. **Whole team** decides what to demo
5. **Karlen** writes decision to `decision.md`
6. **Dave** starts building

---

## How demo prep flows

1. **Karlen** fills placeholders in `demo-script.md` (Layer 1 / 2 / 3)
2. **Dave** finishes artifact
3. **Whole team** dry-runs the three-layer arc
4. **Karlen** writes the closer (Layer 3 punchline)

---

## What to do if something's stuck

| Stuck on | Ask |
|----------|-----|
| How to phrase a question | Karlen — has the prompt bank in `interview-script.md` |
| Where to put a file | Karlen — has the file map above |
| What artifact to demo | Karlen — owns the decision |
| Demo won't fit in 10 min | Karlen — owns the script, will trim |
| Code won't compile / mockup broken | Dave — owns the build |
| Interview won't go deep | Ethan — owns the interview, but Karlen can suggest a workaround thread |
| Story is unclear | Whole team in `demo-script.md` |

---

## The git situation

The team repo is `https://github.com/appydave-hackerthons/08-2026-chiangmai-4seas`.

If push is blocked (403 / access denied):
- Karlen sorts it out with Dave
- Files still get committed locally — nothing is lost
- One push ships everything once access is granted

**You don't need to know any of this.** Just write files. Karlen (via me) handles the git.

---

## The three-layer story (what we're aiming for)

Every demo hits:

1. **What we built** — the artifact, demo it working
2. **How it meets the needs** — the people, the stuck points, the value
3. **How we built it** — the factory, the method, the roles

Layer 3 wins hackathons. Always have the factory in the story.

---

## TL;DR

- **Ethan:** interview, capture transcript, push for workaround-rich
- **Karlen:** ingest everything, weave the story, update placeholders in real time
- **Dave:** wait for the decision, then build whatever was chosen
- **Files:** write to `~/workspace/nimman-hackathon/`, don't think about git
- **Coordination:** ask Karlen when in doubt