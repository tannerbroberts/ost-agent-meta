---
type: Solution
source: 'CONVO:2026-08-11 operator session'
created: '2026-08-11'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**Mechanism:** a human-set target (a `target:` field in `ost.config.yaml`, or `ost-agent target <opportunity title>` on the CLI — human-set to honor the MUST NOT at `ruleset.ts:142` against auto-selecting a target opportunity). `ost_next_work` gains a `scope` parameter that filters every bucket to the target opportunity's subtree, plus the evidence records whose best-match candidate lands there; `/ost-pass` reads the target and works that branch until its buckets are empty before touching anything else. When no target is set, today's whole-tree sweep is the unchanged fallback. Render the ruleset's `cadence` block (which already prescribes "select a single target opportunity at a time") into SKILL.md so the running agent finally sees it.

**Why this shape:** it matches Torres's prioritize-then-ignore-other-branches procedure exactly, gives the operator the one-branch mental model they asked for, and keeps target selection a human act — the agent's added power is only the discipline to stay inside the choice.

**Precedent in-repo:** the build loop already has per-item focus (`src/loop/claim.ts` — a pass claims the one briefing item it is building). This is the discovery-side equivalent, one level up.
