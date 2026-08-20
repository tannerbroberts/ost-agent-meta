---
type: Solution
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The per-target attempt count survives between firings and is consulted when a target is selected]]

**Variation dimension: automated versus manual — a count, with no judgement anywhere in it.** The loop already knows how many consecutive firings have built against a target with its node unchanged — that is the number in the "has not shipped after 2 attempt(s) in a row" note. This candidate makes that count *do* something: on the second assertion-red after a build (not a `no-spec`, not a compile failure — `src/ost/instrument.ts` already keeps those apart), the loop writes a `disputed` marker into its own state, excludes the target from `buildable` on every later firing until the node's file hash changes, and says so in the report. Discovery, reading the tree, sees a target the loop has stood down from and can propose `deferred` or a reframing.

**The idea.** Two builds that both end on the same failing assertion, with nothing about the definition changed in between, is a repeatable measurement whatever it means: either the idea is wrong or the definition is. Neither is a reason for a third model call. The marker is in loop state, not in the tree, so no tree invariant moves — it is the same shape as the firing lock and the cadence stamp.

**Against its siblings.** Trusts nobody: not the builder's account ("The builder files a structured disconfirmation…") and not a classification of the spec ("Replay-style instruments are a distinct kind…"). It is also the only one that would have stopped the third firing on PR #171 — the 2026-08-19 re-refutation happened *after* two identical notes and after a human had already set the solution `deferred`, which suggests the count is either not persisted across firings or not consulted by selection.

**Where it fails, stated so it can be judged.** It cannot tell a refuted idea from a badly built one; it can only say "stop spending here". A solution that genuinely needs three attempts is stood down after two. And it depends on the per-target count surviving between firings, which the existing note mechanism appears not to guarantee.

**Cost.** A state file keyed by target and node hash, one filter in the preflight, one sentence in the report.

## Definition of done

"Replaying the PR #130 sequence, the preflight refuses the third selection of a twice-red unchanged target"

    npx vitest run test/loop/disputed-target-exclusion.test.ts

No-spec red as of 2026-08-20: the spec is unwritten. Once written it fails genuinely — `build-pass.sh`'s preflight reads no per-target history, and the recorded third selection of 2026-08-19 is the observation the spec encodes. Green settles that exclusion is feasible; the number two, and what the disputed marker means to discovery, stay open.
