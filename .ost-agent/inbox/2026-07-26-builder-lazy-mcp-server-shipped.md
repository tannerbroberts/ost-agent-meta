# Builder note — the lazy MCP server is implemented and committed (not yet released)

Source: builder session, 2026-07-26, repo `~/dev/OST-Agent`, commit `3b9cc5e` on `main` (local; 2 commits ahead of origin, unpublished).

What was observed, not asserted: HEAD carried `test/mcp/setup-mode.test.ts` — five tests
specifying `createLazyOstMcpServer`, committed with no implementation. 5 of 468 tests red.
This was the remaining machinery behind the first-run seam tracked on
[[I can't tell another PM 'just run npm install' and have it work]]: the plugin auto-starts
`ost-agent mcp` against `${CLAUDE_PROJECT_DIR}`, so the server itself must survive the
minute before a vault exists.

Shipped (verified by running the suite, not by agent self-report — 472/472 across 65 files,
tsc clean, generated skill drift-free):

- The server now comes up against a bare directory, lists the full 13-tool surface, and
  answers pre-init calls with the setup guidance from `src/mcp/setup.ts` (exact dir, exact
  init command, outcome-is-human-set, no-API-key). `ost_next_work` keeps its
  `bootstrap: true` contract. First call after `init` hits the real tools — no reconnect.
- Adversarial review (3 lenses, every finding independently verified) confirmed 7 defects
  in the first implementation; all fixed with regression tests: probing wrote directories
  to disk (`Vault`'s constructor `mkdirSync` — a typo'd `OST_VAULT` conjured the path
  chain); a broken `ost.config.yaml` turned every request into a raw JSON-RPC -32603; an
  enabled adapter's missing env vars blocked all tools; and a vault missing only its
  Outcome was told `init` — which would have silently discarded the human's outcome —
  instead of `set-outcome`.

What this does NOT change: the rung of the gate node stays `assertion`. No outside PM has
been handed the one-liner. And the plugin invokes `ost-agent@latest`, so no consumer sees
any of this until `npm publish` runs — which is blocked on the credential only the founder
holds (the standing instance of [[Every run ends blocked on a credential only I hold]]).
The warm n=1 hand-off test ([[Does a first-run branch actually get a stranger to a working
vault]]) is now unblocked on the build side pending that release.

## Correction — 2026-07-26 evening, after rebase onto origin/main

The shas above are stale: the autonomous loop released its own v0.18.0 ("the schema
checked the call, and nothing checked the value") to npm while this work sat unpushed —
two release trains, one version counter, no coordination. The local release was rebased
and renumbered: feature is now `822d5bb`, release `a10e75f` = **v0.19.0** (tag local,
push pending). 493/493 tests on the merged tree. The near-collision itself is friction
evidence: nothing in the release path checks the registry or origin/main before choosing
the next version number.
