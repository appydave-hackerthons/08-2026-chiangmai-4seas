# Agent registry

Standing agents the hackathon system can call on. Each entry: who it is, what it owns, what it
can do for CM4S, and how to reach it. An agent introduces itself by adding a row here **and** by
authoring a `CM4S-L1 · agent · <name>` capture in Captain's Log, so it is discoverable both in
the document area and in the evidence stream the system listens to.

| Agent | Owns | Reach it via |
|---|---|---|
| **captain-swag** | Captain's Log (repo + MCP surface) | blackboard channel `cl-orchestrator-coherence`, or a session in `~/dev/ad/apps/captains-log` |

## captain-swag — Captain's Log orchestrator

Introduced 2026-08-01 · capture **B344** (`q: "CM4S"` finds it — that capture is also the first
live end-to-end proof of `capture_create`).

- **What it is**: the Swagger orchestrator session that owns Captain's Log on the M4 mini. It
  specs, delegates to worker agents, gates their evidence, and keeps the CL board
  (`docs/tickets/BOARD.md`) and blackboard channel coherent. It does not do build labor itself —
  it routes it.
- **What it can do for CM4S**: operate and *extend* the upstream evidence source. The MCP surface
  on `:7101/mcp` exposes **8 tools** as of `c2436ba` (2026-08-01): `captures_search`,
  `capture_get`, `captures_stats`, `capture_set_state`, `capture_add_note`, **`capture_create`**
  (new — fact sheets / opportunity cards / selection records can now be authored over MCP, not
  just REST), `composer_describe`, `composer_invoke`. Missing capabilities (participant/entity
  fields, new filters, ontology terms) are ticketed on the CL board on request — file the ask via
  the channel rather than editing the CL repo from a hackathon session.
- **Constraints it is the authority on** (see `tag-convention.md` for the working conventions):
  no participant/entity fields in the record contract; tags are enricher-produced and
  ontology-gated, never caller-set; `q` searches title + synopsis + tags; the `cm4s` ontology
  term is an **open decision at David** and interacts with CL's open T39 ontology rework (the
  `project` area currently has zero curated terms — `cm4s` would be its first).
