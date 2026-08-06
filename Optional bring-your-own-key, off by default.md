---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-agent-as-driver.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[A user can complete a first run without ever supplying a key]]

**Candidate solution (unvalidated).** Default operation requires no key (ambient agent). Power users who want fully headless scheduled runs may optionally supply their own API key — strictly opt-in, never required to try or to run interactively.

**Approach:** *make the credential optional and additive*, not a gate to entry.

**Contrast with siblings:** unlike ambient-only it enables unattended cron for those who want it; unlike a bundled model it defers to the user's chosen provider/quality.

_Addresses: "Don't want to buy a second AI credential just to try it". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Test can users complete first run without providing a key" — moved under "A user can complete a first run without ever supplying a key" — the belief this test measures now has a node of its own

## Issues
- 2026-08-05 Deliberately not instrumented by the 2026-08-05 unattended pass, because the honest command would already be green. This solution's test is "Test can users complete first run without providing a key", and the product's own documentation states that setup "needs no model and no API key, and neither does anything else here — `status`, `check`, `debt`, `lanes`, `result`, and every tool on this surface are deterministic. This project calls no model at all: the server holds none, and the connected session supplies every bit of the reasoning." If that is accurate, a spec asserting that init, a sweep and a check all succeed with every API-key variable unset passes against today's code — and an instrument that cannot fail measures nothing and hands a builder no definition of done. Two things a human should decide. First, whether the test is already answered by construction, in which case it should be recorded as such via `ost-agent result` rather than left open — it has been sitting unrun since 2026-07-25 for a property the product may have had the whole time. Second, whether the solution's real content is the OTHER half of its title, "optional bring-your-own-key": if a BYOK path is intended to exist at all, then the instrumentable claim is that it is off by default and that no outward call happens until a key is deliberately supplied, and that spec WOULD be red today. This pass could not tell the two apart without reading the repository, which it holds no grant to do.

## Definition of done

"Test can users complete first run without providing a key"

```
npx vitest run test/cli/first-run-without-key.test.ts
```

Red today for an observed reason rather than a missing file: this vault's friction record of 2026-07-25 — "run P2-P5 requires an API credential even when an authenticated ambient agent is the one driving" — records the Anthropic SDK failing to resolve any authentication method while an authenticated session was available, with the run proceeding only via the ambient tool-surface workaround. The keyless default path is therefore known to be incomplete at P2-P5, and the spec fails on exactly that.

Green when init, set-outcome, ingest and the maintenance passes all complete with no credential in the environment. That settles the mechanical half of the claim only — whether anything in the default path *demands* a key. Whether a stranger experiences that path as complete is usability, and stays with a person.

The test title is quoted rather than linked because it is already wikilinked once by its parent Assumption, and a second link would fail `check`'s single-backlink rule.
