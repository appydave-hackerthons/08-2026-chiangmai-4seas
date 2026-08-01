# interview-copilot

**Last assessed:** 2026-08-01 — repo seeded, no code yet.

## Name

`interview-copilot`. Spoken as "the interview co-pilot".

## One line

A dashboard where a team of AI agents co-pilot a live interview — surfacing questions to ask and
biases to avoid, so the interviewee opens up.

## The problem

> **Said (Ethan):** People don't know what they want. A good interviewer can extract needs out of
> people, or get them to realise problems they have — but not everyone has that skill.

Interview quality is the upstream constraint on the whole hackathon system. Thin evidence produces
weak opportunity cards, and no amount of downstream scoring recovers it. The plan's own diagnostic
rule points here: *if the cards are weak, fix the questions before touching the ranking.*

## Who it's for

The **interviewer** — Karlen at this event, and anyone conducting discovery interviews after it.
Not the interviewee; they never see it.

## What it does

Three things, live, while the interviewer is still talking:

1. **Questions to ask next** — the follow-up that opens a door the interviewer didn't see
2. **Biases to avoid** — leading the witness, accepting the first answer, treating a proposed
   solution as if it were the underlying problem
3. **Supporting information** — relevant data surfaced while the topic is still on the table

The interviewer stays in charge throughout. The agents never address the interviewee.

## Tech stack

— **pending.** Repo contains a README only as of 2026-08-01. Do not guess this; fill it from the
manifest once Ethan pushes.

## Why this stack

— **pending.** Ask Ethan directly. This is the section that gets asked about in Q&A, and a reason
invented after the fact will not survive follow-up.

## Status

**Not started.** Repo created 2026-08-01 so work could begin; Ethan invited with write access the
same day.

## Links

- Repo — https://github.com/appydave-hackerthons/interview-copilot (public)
- Deployed — *pending*
- Demo / screenshots — *pending*

## Lineage

`CM4S-L1` — the team's own lineage (David, Karlen, Ethan).

Traces to the live interview on 2026-08-01, recorded in [`../lineage-1.md`](../lineage-1.md).
Ethan's own idea, described in his own words during that interview.

**Note for a presentation:** this app is *recursive* — it is a tool that improves the very process
that produced it. That is the closed loop the demonstration arc wants to show, happening naturally
rather than being staged.

## Owner

**Ethan** (`gee842`) — build lead.

## Open questions

Unanswered as of 2026-08-01. Each changes the build:

- **Live audio, or reading a transcript as it lands?** Sets the whole architecture, and decides
  whether it plugs into the Captain's Log ingestion path
- Are suggestions private to the interviewer, or visible in the room? A participant-visible prompt
  changes the interview dynamic
- Does the interviewer pick from options, or does it push one at a time? And what happens when a
  suggestion is bad?
- What does it do when it has nothing useful to add — stay silent, or is silence a failure state?

## Design note — inference, not Ethan's words

The README proposes **a team of agents rather than one**: separate watchers for the unasked
question, for bias, and for facts. The reasoning is that one model asked to do all three tends to
do the easiest and quietly drop the others.

Ethan said "agents, as a team", so the team framing is his. **The one-agent-per-concern rationale
is mine** — his repo, his call to keep or discard.
