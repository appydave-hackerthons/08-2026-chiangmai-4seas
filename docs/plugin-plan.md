# The plugin — findings from the brain, and what to actually build

Researched 2026-08-01 across `brains/anthropic-claude/claude-code/plugins/`,
`brains/anthropic-claude/skills/` and `brains/prompt-patterns/`.

## Headline: build the repo, don't stub twenty skills

Four independent sources say the same thing, and none of them were written about this project.

| Source | What it says |
|---|---|
| `plugins/strategy-and-best-practices.md` §1 | *"A plugin can ship with exactly ONE skill… single-skill stops you over-building a speculative 'suite' before the extra skills are proven."* ChernyWorthy shipped with one skill after four unproven siblings were rejected. |
| Same doc §3 | Skill listings have a **~1% context budget**. Past it descriptions silently drop and skills go **invisible to auto-routing** — they still run when named, but the model stops choosing them. |
| AppyTron `CONTEXT.md` §5 / AppySentinel `CONTEXT.md` §6 | *"Recipes are byproducts of pilots, not speculative features."* Both scaffolds state it independently. |
| This project's plan of record, step 4→5 | Pilot lineage one by hand, **then** extract skills from steps that demonstrably worked. |

There is also a live worked example of the failure in David's own catalog: the `appydave`
plugin carries **97 skills**. The brain's budget doc flags a 91-skill plugin as running ~8×
over, with several skills already name-only. The healthy siblings — `sesh` 11, `brand-dave` 11,
`overwatch` 4, `captains-log` 3 — are the shape to copy.

**So: build the distribution envelope now (it is genuinely blocking — the team can't share
anything without it), and let the pilot decide what goes inside.**

## Why a separate repo is right

`appydave-plugins` is David's *private* internal marketplace. Karlen and Ethon need write access
to hackathon skills, and shouldn't get access to 97 internal skills to obtain it. Marketplace
source types include `github`, so a separate repo is a first-class citizen — it can stand alone
or be listed from another catalog later.

## Structure (matching the house pattern)

```
<repo>/
├── .claude-plugin/
│   └── marketplace.json          the catalog — name is the @namespace
├── cm4s/                         the plugin (install unit)
│   ├── .claude-plugin/
│   │   └── plugin.json           MUST carry an explicit version
│   └── skills/
│       └── <skill-name>/SKILL.md
└── docs/
    └── catalogue.md              the skill manifest — a TABLE, not 20 stubs
```

Mechanics that bite, from `strategy-and-best-practices.md` §5:

- **Set `version` in every `plugin.json`.** Omit it and you get SHA versioning — every commit
  bumps every plugin.
- **Use explicit `"source": "./cm4s"`** in the marketplace entry. The bare-name
  `metadata.pluginRoot` shorthand fails `claude plugin validate` on the current CLI.
- Don't set `version` in both `plugin.json` and the marketplace entry — `plugin.json` wins.
- Omit manifest keys you don't need. `skills` **adds** to the default scan, but `commands`,
  `agents` and `outputStyles` **replace** it — a manifest key plus a folder silently drops the
  folder.
- Install syntax is `<plugin>@<marketplace-name>`. Avoid the single-plugin-marketplace
  anti-pattern (`foo@foo`) — one marketplace, many plugins, the brand is the `@`.

## How to write the skills when the pilot earns them

From `prompt-patterns/context-engineering-deltas-claude-5.md` — six reversals against
pre-Claude-5 habits. The ones that apply here:

1. **Rules → judgment.** Replace a prohibition with a reference point. "Match the surrounding
   code" beats a list of bans — unbounded in expression, tightly bounded in outcome.
2. **Examples → interface design.** Examples of *mechanics* now constrain the exploration space.
   Spend the effort on expressive parameters instead; an enum is documentation at zero token cost.
   (Examples of *taste* and communication style still work.)
3. **Progressive disclosure — a tree, not an index.** The "central repository of every practice"
   is explicitly named as a myth, and it's what produces the 900-line SKILL.md.
4. **One canonical statement, at the layer that owns it.** Don't duplicate an instruction for
   reliability, and don't position it late for recency — both tactics are dead.
5. **Skills should encode *our* opinions,** not general practice the model already has.

The cost of getting this wrong is a **reasoning tax**, not a wrong answer: contradictory guidance
across CLAUDE.md → rules → skill → prompt makes the model adjudicate a fight we started.

## The catalogue

The source plan §15 asks for a manifest with, per skill: name, single responsibility, inputs,
outputs, prerequisites, phase, mandatory/optional, next skill, validation, failure behaviour.

**That is a table in `docs/catalogue.md`, not twenty `SKILL.md` files.** It costs nothing, puts
no false pressure on interfaces that haven't met a real input yet, and is the artifact the
orchestration layer reads to decide what runs next. Stubs get created as the pilot earns them.

## Open decision

Repo name and marketplace name. Proposed:

- repo `appydave-hackerthons/cm4s-plugin`
- marketplace `name: "cm4s"`, plugin `name: "cm4s"` → installs as `cm4s@cm4s`

…which trips the single-plugin-marketplace anti-pattern. Better: marketplace
`name: "appydave-hackerthons"` so future events add plugins alongside → installs as
`cm4s@appydave-hackerthons`. **Awaiting a go.**
