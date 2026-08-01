# reports — pipeline output

Reports produced by `interview-copilot`. One interview in, one evidence-backed report out.

Two files per report:

| | |
|---|---|
| `.mhtml` | **The verbatim archive** — exactly what the app rendered, styling intact. Never edit it |
| `.md` | A text extraction for reading, grepping and diffing in git. Derived, regenerable |

Filename follows the repo convention: `<date>-<lineage>-report-<nnn>-<slug>`.

## Reading them

The structure the app produces, in order: summary · top pain points · key facts & behaviours ·
verbatim quotes · **unanswered questions** · opportunity hypothesis · least-effort next step.

Two of those sections carry more weight than the rest:

- **Unanswered questions** — what the interview did *not* establish. This is the follow-up list,
  and it's the section most likely to be skipped and most likely to matter.
- **Opportunity hypothesis** — the app labels it *"Inference — validate before treating as fact"*.
  Respect that label. It is a hypothesis with evidence behind it, not a decision.

## Rule

**A report is evidence, not a decision.** It feeds the judging stage; it doesn't replace it.
Nothing gets built because a report suggested it — a human still picks.

## The JSON is the real interface

Each report also exports as JSON — that is the **machine-readable handoff** into the next funnel
stage, and the format worth designing against. The HTML is for humans; the JSON is for the
pipeline.

```
summary               str
top_pains             [str]     — the friction, ranked
key_facts             [str]     — what was actually established
quotes                [str]     — verbatim, for the story
unanswered_questions  [str]     — the follow-up list
opportunity           str       — labelled inference, not fact
next_step             str       — one validation test
score                 int       — percent of coverage criteria met
coverage              [{label, complete}]
engine / report_id / session_id / created_at
```

**`key_facts` and `quotes` map cleanly onto the fact-sheet stage of the funnel; `top_pains` and
`opportunity` map onto op-cards.** That is the join we need — it means Ethan's app output can feed
the judging stage without a translation layer.

## The six coverage criteria

The bar the app holds an interview to. `score` is just the percentage of these met.

1. Captured one recent participation decision and desired outcome
2. Uncovered why the experience mattered
3. Assessed how well the participant can access that outcome now
4. Made the expected-versus-actual participation gap explicit
5. Identified where access breaks and the current workaround
6. Captured the consequence, priority, and who else is excluded

**These are effectively an interview rubric already** — worth comparing against Karlen's script and
against whatever Hacker Fund's 20-point criteria turn out to be.
