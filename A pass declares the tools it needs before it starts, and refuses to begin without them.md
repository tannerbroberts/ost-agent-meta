---
type: Solution
source: 'TRANSCRIPT:081b644b-e90a-472e-9b3d-15562a030a94'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A pass can know which tools it needs before it makes its first call]]

**The idea.** A pass names its required tool set as a precondition and checks it against what is actually callable before the first unit of work. A missing tool stops the pass at second zero, with the name of what is absent, rather than surfacing forty calls in as a denial the agent then works around.

**Why this shape.** Observed first-party on 2026-08-06: an unattended sweep instructed to flag human-only tests found `ost_flag_humans_required` was not granted on that surface, discovered at the moment it tried to use it. The same sweep found `Bash` absent and `ost_read_repo` ungranted. Each was a mid-pass discovery, and each silently changed what the pass could deliver — the sweep continued and produced a smaller result that looks from the outside like a complete one.

**How it differs from its siblings.** This one fails loudly and early, and buys nothing else. It does not record the gap for later ("Every refusal a surface returns is recorded as tree evidence") and it does not let the operator pin an intended surface ("One surface profile per pass, pinned in config"). It is the cheapest of the three and the only one that prevents a degraded pass rather than explaining one afterwards.

**Where it fails.** A pass that legitimately adapts to a smaller surface — an unattended sweep that genuinely should not hold repo sight — would be refused by a naive requirement list. The precondition has to distinguish *needed* from *would use*, and getting that split wrong makes the check either useless or an obstacle.

⚠️ Unvalidated. Agent-ideated, from friction the ideating agent hit in the same pass.

## Definition of done

"Declare a required tool set and check a pass refuses before doing any work"

```
npx vitest run test/mcp/preflight-required-tools.test.ts
```

Named in plain text rather than linked: the test is already wikilinked by its parent assumption, and a title is linked exactly once in the vault.

## Issues
- 2026-08-23 2026-08-23 unattended sweep, repo sight held — the gap this solution's own implementation names is now observed firing, first-party. `src/mcp/required-tools.ts` ships a `LIVE_SURFACE_CAVEAT` printed on every verdict, cleared or refused: "NOT checked: whether the surface this run actually fires with is the list handed in here — a precondition right about the declaration and wrong about the session is still wrong at 3am." This firing is an instance of exactly that. The declared surface cleared, and the session was nonetheless refused `Glob` on `/Users/tanner/dev/OST-Agent` at the moment it reached for it — one call spent, mid-pass, in the shape this solution exists to prevent. `TRANSCRIPT:d2c8dbf0-41f7-4517-bc57-88924f735441` (2026-08-23) records an unattended firing hitting the identical refusal on `/Users/tanner/dev/OST-Agent/src/ost`, so it is not particular to this session. Note the asymmetry that makes it survive the preflight: `ost_read_repo` was granted and carried this pass's whole repo sight, so the pass was not blind and did not narrow — the check would have cleared on the ost_* family and been right, while the built-in file tools were refused and nothing compared them against anything. What this does NOT establish: whether the live surface is knowable to a preflight at all. `beginPass` is handed `available` by its caller, and whether the harness can hand it what the session will actually accept is a question about the harness, not this repository — the same routing correction already recorded on "Auto-read a file before the first write or edit to it in a session, instead of erroring". Recorded as an observation, not a request; the design call is a human's. Related and already updated with the scope limit: "The same agent has a different tool surface on every surface I run it on".
