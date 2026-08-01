# Recon — the three AppyDave scaffolds

Verified 2026-08-01 against the repos on this machine. Purpose: decide what the hackathon builds
on, and retire the "AppyTron recon" pre-work item from the plan.

## Verdict first

**All three are strongly documented — recon was easy, and one of them was already done.**

| | Agent-facing docs | Verdict |
|---|---|---|
| **AppyTron** | `CONTEXT.md` 205 · README 47 · 7 docs · no `CLAUDE.md` | The plan's "AppyTron recon" **already exists** as `CONTEXT.md` |
| **AppyStack** | `CLAUDE.md` 98 · README 262 · `docs/architecture.md` **1,187** · 65 docs · KDD library | Deepest documentation of the three |
| **AppySentinel** | `CLAUDE.md` 162 · `CONTEXT.md` 247 · README 246 · `DEVELOPMENT.md` · `context.globs.json` · 16 docs | Best agent setup; holds the MCP pattern we need |

Three peers, one job each: **AppyStack builds web viewers, AppySentinel builds headless
observers, AppyTron builds desktop consoles.** They share `@appydave/core` (Tier 1).

---

## 1 · AppyTron — the hackathon build stack

`~/dev/ad/apps/appytron` · github.com/appydave/appytron · last commit 2026-07-19

Electron desktop scaffold. `template/` is the product; `create-appytron` copies it.

- **Stack** — electron-vite (main/preload/renderer) + electron-builder, React 18 + Vite + Tailwind 3
  + Zustand, `@appydave/core`, macOS-first with GitHub-Releases auto-update.
- **The pattern** — every app's `src/main/index.ts` drives one `createConsole({ name, registerIpc,
  onReady })`. The IPC contract lives in exactly one file, `src/shared/ipc.ts`.
- **Scaffold** — `npx create-appytron my-app`.
- **Verify healthy** — `bun run test` in appydave-foundation (33), then `npm test && npm run
  typecheck && npm run build` in `template/`, then `npm test` in `create-appytron`.
- **Gotcha that will bite** — the preload is `index.mjs`, not `.js`. Loading `.js` fails silently,
  `window.appytron` is never defined, and the UI just sits on "loading…" with dead buttons.
- **Recipes** — markdown capability descriptions at `.claude/skills/recipe/references/*.md`.
  Shipped: `wrap-cli` (the signature move) and `landing-page`.

**Conclusion: the pre-hackathon "AppyTron recon skill" is unnecessary.** `CONTEXT.md` §10 is
literally addressed to an agent building an app on AppyTron. Point build sessions at it.

Only real gap: no `CLAUDE.md`, which is the file a Claude Code session reads first. Cheap fix.

---

## 2 · AppyStack — web viewers

`~/dev/ad/apps/appystack` · last commit 2026-07-22

Not an application — a config package plus an architecture hub for the RVETS stack (React, Vite,
Express, TypeScript, Socket.io). Consumed by FliGen, FliHub, FliDeck, Storyline.

- **Scaffold** — `npx create-appystack@latest my-app --scope @myorg --port 5500`.
- **Ports** — client `5X00`, server `5X01`. Registry at
  `~/dev/ad/brains/brand-dave/app-port-registry.md`; client apps use 6000–6999.
- **Hard rules** — ESLint 9 flat config only (legacy `.eslintrc.*` is silently ignored);
  TailwindCSS v4 syntax (`@import "tailwindcss"`, not v3 `@tailwind`); npm workspaces with a
  client/server/shared three-package layout.
- **KDD library** at `docs/kdd/` — consult before touching env config, ports, the upgrade tool or
  dependency bumps. Those areas have bitten before and a `.claude/rules/` gate surfaces the entry.

**Relevance to the hackathon:** this is the fallback if a participant's app is better as a web app
than a desktop one, and it is what the portfolio site should be built on.

---

## 3 · AppySentinel — headless observers, and the MCP pattern

`~/dev/ad/apps/appysentinel` · last commit 2026-07-20

Boilerplate for always-on local data coordinators. Matters here for one reason: **it owns the
documented MCP-binding pattern** the Angel Eye work needs.

- **Access zone** — the interface layer, split three ways: *Bindings* (thin MCP / HTTP / CLI
  adapters that own no logic), *Query* (pure reads returning `QueryResult<T>` with freshness
  metadata), *Command* (stateless writes that control the Sentinel itself, never the observed
  system). CQRS-lite, communicating through the filesystem.
- **`mcp-binding` (pattern A3) is PoC-validated and locked** — 2026-04-27. Read-only layer over a
  snapshot store: `collector → sentinel-latest.json → MCP binding → agents`. Data-age is a
  first-class field on every response. Tool granularity is summary + detail + domain-specific.
  One command-like tool (`trigger_collect`) is acceptable. Full spec lives at
  `appyradar-sentinal-safe/docs/mcp-surface.md`.
- **`docs/forensic-angeleye.md`** — 1,014 lines, dated 2026-04-25, a full architectural forensic of
  Angel Eye written to extract patterns for AppySentinel. Read this before building the wrapper.

### Correction to AppySentinel's own docs

`CONTEXT.md` §5 states that `packages/template/.claude/skills/configure-sentinel/SKILL.md` is "a
placeholder… deliberately deferred for v1". **It is now 454 lines.** That snapshot is dated
2026-04-28 and has drifted. Worth regenerating.

---

## What this means for the plan

1. **Retire the AppyTron recon item.** It exists. Add a `CLAUDE.md` instead.
2. **The Angel Eye wrapper has a documented pattern and a prior forensic** — it is not
   greenfield work.
3. **Three scaffolds, three shapes.** Desktop console → AppyTron. Web app or portfolio site →
   AppyStack. Anything always-on and observing → AppySentinel. Pick per participant rather than
   forcing everything through AppyTron.
