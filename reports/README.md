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
