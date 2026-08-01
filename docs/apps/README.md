# App dossiers — one bucket of knowledge per micro-app

One file per app, named after its repo. **This is Karlen's presentation source** — when he needs
to talk about any app in the portfolio, everything he needs is in one file, in the same shape
every time.

```
docs/apps/
├── README.md              ← you are here (the schema)
└── <repo-name>.md         one per app
```

## Why a fixed shape

Five apps described five different ways can't be presented as a portfolio — the audience spends
their attention re-learning the format instead of hearing the content. A fixed shape also means a
gap is **visible**: an empty "why this stack" section is a question to go and ask, not something
that quietly never gets written.

## The schema

Every dossier carries these, in this order. Keep a heading even when the answer is *not yet known* —
write `— pending` under it rather than deleting it.

| Section | What goes in it |
|---|---|
| **Name** | The repo name, and the spoken name if they differ |
| **One line** | What it does, in a sentence a stranger understands. No jargon |
| **The problem** | What's broken without it. Trace to interview evidence where it exists |
| **Who it's for** | The actual person or role, not "users" |
| **What it does** | The two or three things it actually does. Not a feature list |
| **Tech stack** | Every significant choice — language, framework, scaffold, services |
| **Why this stack** | **The one people forget.** Why each choice, in one line. A stack without reasons can't be defended in a Q&A |
| **Status** | Honest. "Nothing built yet" is a legitimate answer |
| **Links** | Repo, deployed app, demo video, screenshots |
| **Lineage** | Which lineage (`CM4S-L1`…`L5`), whose idea, and the evidence it traces back to |
| **Owner** | Who builds it. Who to ask |

## Rules

- **Never invent the stack.** If the repo is empty or unread, write `— pending` and say when it
  was last checked. A guessed stack in a presentation is a guaranteed wrong answer on stage.
- **Mark evidence.** Same rule as everywhere else here — what a person *said* is separate from
  what we inferred. Karlen needs to know which is which before he puts it on a slide.
- **Update after each assessment pass**, and stamp the date. A dossier nobody re-reads goes stale
  silently.
- **Write for someone with no context.** A judge, an audience member, a participant seeing their
  own app described back to them.

## Assessment pass

When a repo comes back with real code in it, the pass is:

1. Read the manifest — `package.json`, `Cargo.toml`, `pyproject.toml`, whatever it uses
2. Read the README and any `CLAUDE.md` / `CONTEXT.md` the builder left
3. Skim entry points and the directory shape — enough to name the architecture, not to review it
4. Fill **Tech stack** from what's there, and **Why this stack** from what the builder said. If
   they never said, that's a question for them, not a blank to fill in with a plausible reason
5. Update **Status** and stamp the date
