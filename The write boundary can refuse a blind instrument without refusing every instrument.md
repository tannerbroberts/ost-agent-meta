---
type: Assumption
source: 'agent-ideation:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[A blind set-instrument call is refused, while a sighted one on the same vault still writes]]

**The belief, stated so it could be false:** the `ost_set_instrument` / `ost_create_node` write boundary can distinguish a pass that could see the repository from one that could not, and refuse only the blind one — without the refusal degenerating into "no instrument may ever be written."

**Why this is a real belief rather than a restatement of the solution.** The solution above proposes gating instrument-writing on repo sight. Its only other assumption, "Operators would rather have honest gaps than guessed commands," is desirability and needs a person. This one is feasibility, and the repository answers it — which matters because the solution's own body concedes the risk in exactly these terms: gating "trades throughput for groundedness at an unknown exchange rate."

**What the code says today (read first-party this pass, with repo sight).** The mechanism already exists and deliberately points the other way:

- `specResolves(repos, target)` in `src/ost/instrument.ts` resolves a named spec against each configured `product.repos` root. It is the set-time half of the `no-spec` rule.
- With `repos` empty it returns `false` for everything, so the boundary **stands down and accepts** the unresolvable path. `test/instruments/spec-path-resolution.test.ts` asserts this as correct behaviour, under the describe block "with no product repo configured, the guard stands down", and states the reasoning in the spec's own header: "With nothing to resolve against the guard would fire on every instrument, and a quality rule would become a total block."
- Sight is nonetheless already *recorded* — `sightCensus()` counts instruments by `sight: grounded | blind | unlabelled`. So the observe-only floor sibling ("An instrument records whether the pass that wrote it could see the repository") is shipped; the ceiling this solution proposes is not.

**So the belief is precisely: is "no repo configured" the same condition as "this author was blind"?** If it is, the shipped stand-down and this solution are in direct contradiction and one of them is wrong. If it is not — if a pass's sight is knowable independently of whether the vault happens to have `product.repos` set — then the refusal can be narrow, and the total-block objection the current spec rests on does not apply to it.

**Risk category:** feasibility. It says nothing about whether operators want the gap (that is the sibling assumption's job) and nothing about the throughput cost of gating.

**If false,** the solution above is not buildable as worded, and the honest fallback is the recorded-sight floor that already ships.
