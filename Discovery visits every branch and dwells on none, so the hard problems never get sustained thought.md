---
type: Opportunity
source: 'CONVO:2026-08-11 operator session'
created: '2026-08-11'
evidence: stated
---
#Opportunity #unvalidated #evidence/stated
[[A discovery firing scoped to one human-chosen target branch, worked to done before the sweep widens]]
[[Buckets ordered by branch, so consecutive firings finish a region before sampling the next]]

**The need (operator's voice, 2026-08-11):** "Does the discovery phase work with one branch at a time? I'd prefer that, so more mental space can be reserved for problem solving, and so we avoid distractions during discovery."

**What is true today (measured, not assumed):** The unattended discovery pass is a whole-tree sweep. `/ost-pass` (`.claude/commands/ost-pass.md:12-24`) loops bucket-by-bucket — unmappedEvidence → underservedOpportunities → … — and every bucket spans the entire tree. `ost_next_work` (`src/mcp/next-work.ts`) has no branch/scope/target parameter, no ranking of any kind: lists are emitted in tree-walk (effectively alphabetical) order and display-capped at 25, so a firing sees the alphabetically-first slice of every bucket, from anywhere in the tree. The live log shows fourteen consecutive passes re-deriving the same global queue ("Evidence queue (124)…") without finishing any region of it.

**The method itself agrees with the operator.** Teresa Torres's own procedure is branch-at-a-time on both sides: structure "each branch one at a time" (producttalk.org/opportunity-solution-trees), and prioritize top-down — assess top-level opportunities, pick one, then "ignore the other branches of the tree" and recurse until a leaf-sized target; ideation is then scoped strictly to that one target (producttalk.org/prioritize-opportunities). The repo's own ruleset says the same — `ruleset.ts:79` ("Target one opportunity at a time (a WIP limit) and go deep"), `:104` (row-by-row, pick the top branch) — and the strongest statement, `ruleset.ts:115` "select a single target opportunity at a time", sits in the `cadence` block that `scripts/gen-skill.ts` never renders into SKILL.md, so the one rule prescribing focus never reaches the running agent.

**The constraint any fix must respect:** `ruleset.ts:142` (MUST NOT): "Auto-select a target opportunity or declare a winning solution." Target selection is a human decision. Branch-scoped discovery therefore needs a human-set target (or an explicitly audited selection rule), not agent whim — which is also what the operator is asking for.

**Litmus (more than one way to address it):** yes — a human-set target field the pass reads; a `scope` parameter on ost_next_work; rendering the cadence block into SKILL.md; a WIP-limit rule enforced by the sweep; rollup-driven branch nomination with human confirmation. A real opportunity, not a solution in disguise.
