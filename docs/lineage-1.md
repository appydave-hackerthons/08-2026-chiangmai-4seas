# Lineage 1 — David, Karlen, Ethon

**Evolving document.** The team's own discovery record — lineage one being interviewed by the
system it is building. Appended to as the interview continues; nothing here is final.

Evidence is marked. **Said** is what a person actually stated. **Inferred** is synthesis — mine,
not theirs. The plan's "evidence before invention" rule applies to the team's own lineage first.

Started 2026-08-01 · interview conducted by David, relayed live.

---

## Ethon — the interviewer co-pilot

### Said

An **always-listening co-pilot for the interviewer**. While an interview is running, it surfaces
two things:

1. **Useful information from the internet** — data relevant to what's being discussed.
2. **Clarifying questions**, proposed by the AI, for the interviewer to ask next.

**The problem it solves:** *people don't know what they want.* A good interviewer can extract
needs out of people, or get them to realise they have a problem they hadn't named. But that skill
isn't universal — not everyone has it. A co-pilot could surface better needs to send down the
pipeline later.

### Inferred

This is aimed squarely at the weakest link in the whole system. The source plan already names
interview quality as the primary risk and states the diagnostic rule: *if the opportunity cards
come out weak, inspect the interview questions before touching the scoring.* Ethon's co-pilot is
a direct intervention on exactly that failure point.

It is also **recursive in a way that matters for the demo** — the tool improves the process that
produced it. That is the closed loop the demonstration arc is trying to show, occurring naturally
rather than being staged.

**The timing tension worth naming early:** a tool that improves interviews only pays off while
interviews are still being conducted. Built mid-event, it arrives after its own usefulness has
passed. Built as lineage one's north-star artifact — first, before participant interviews begin —
it compounds across every remaining lineage. The build order is the whole value here.

---

## Karlen — downstream of the interview

### Said

Once there are good questions and a working process for surfacing people's frictions and pain
points, the next problems are:

- **Document** all of the frictions and pain points captured.
- **Find patterns** within them.
- **Generate ideas** from those patterns — which needs a defined process or method, not intuition.
- **Define what a good idea actually is.**

A good idea has to satisfy two things:

1. The **themes of the hackathon** itself.
2. The **20-point criteria**.

Together those become the criteria set for deciding which ideas are higher priority, which are
worth building, and which are not.

### Inferred

This is the opportunity-selection funnel from the source plan, arrived at independently — which is
a good sign the plan is describing something real rather than something invented.

The sharpest thing in Karlen's answer is **"define what is in fact a good idea."** The plan
proposes a dozen ranking dimensions but never fixes a bar. Karlen is asking for the bar, and he is
right that it must come from outside the system: the hackathon's own themes and the 20-point
criteria are **external rubrics**, not something the AI should be allowed to infer. That maps
exactly to the plan's rule that a weighted score organises attention but must not make the
decision.

It also sits squarely in Karlen's owned territory — interviews, customer journey, lean canvas,
marketing — so the criteria set is his to define, and the build side consumes it.

---

## Two halves of one spine

```
Ethon                                    Karlen
better evidence IN          ─────▶       better judgement ON IT
────────────────────                     ──────────────────────
co-pilot surfaces                        document frictions
  · live data                            find patterns
  · clarifying questions                 generate ideas by method
                                         judge against an external bar
                                           · hackathon themes
                                           · 20-point criteria
```

Neither half is useful alone. A co-pilot that surfaces richer needs into a pipeline with no
defined bar just produces more unranked ideas. A rigorous criteria set applied to thin interview
evidence ranks noise precisely. **They have to land together**, and they are owned by different
people — which makes the handoff between them the thing most likely to break.

---

## Unknowns — do not invent these

| Unknown | Who owns it | Why it matters |
|---|---|---|
| **The 20-point criteria** — referenced as if it exists; contents not stated | Karlen / Hacker Fund | It is half the definition of "good idea". Everything downstream of selection depends on it |
| **The hackathon themes** — not yet stated | Hacker Fund | The other half. An idea can be excellent and still fail the theme test |
| Whether the co-pilot is lineage one's north-star artifact or a later build | David + Ethon | Determines whether it helps this event or only the next one |
| What "always listening" means technically — live audio, or reading the transcript stream | Ethon | Changes the build entirely, and touches the Captain's Log ingestion path |
| Whether the co-pilot's suggested questions are shown to the interviewer only, or to the room | Ethon | A participant-visible prompt changes the interview dynamic |

---

## Questions to ask next

Short list, ordered by what unblocks the most.

**For Ethon**
1. Does the co-pilot listen to live audio, or read a transcript as it lands? That one answer sets
   the whole architecture.
2. Interviewer sees the suggestions privately, or does the participant see them too?
3. When it surfaces a clarifying question, does the interviewer choose from options, or does it
   push one at a time? What happens when its suggestion is bad?
4. What does it do when it has nothing useful to add — stay silent, or is silence a failure state?

**For Karlen**
5. Can we see the 20-point criteria, and are the hackathon themes published anywhere yet?
6. Of the twenty points, which are **disqualifying** — a zero that kills an idea regardless of the
   rest — versus merely weighted?
7. Are ideas judged individually, or against each other? Ranking a set and scoring one idea are
   different instruments.

**For both**
8. If the co-pilot works and the criteria are sharp, but a participant's best idea is still too
   large to build in a day — what happens to it? Does the system say so out loud, or quietly pick
   the second-best?
