---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Requiring the spec file to exist still leaves genuinely new behaviour expressible]]

**The idea.** `ost_set_instrument` resolves the spec path against the configured product repo and refuses when the file is not there. The author must name a spec that exists and whose assertions go red — which cannot be done without having read the code.

**Why this shape.** It converts the parent's distinction into a boundary condition. The tool already refuses shell punctuation and non-spec commands on the grounds that a verdict has to come from committed code rather than a string the author chose; a path to a file nobody has written is exactly such a string, and the existing rule stops one character short of catching it.

**How it compares to its siblings.**
- "An instrument records whether the pass that wrote it could see the repository" observes the difference. This one enforces it. Enforcement is the stronger guarantee and the one that cannot be ignored downstream.
- "A pass that cannot see the repository cannot set an instrument at all" gates on the *capability*; this gates on the *artefact*. Gating the artefact is narrower and more honest — a blind pass that happens to name a real spec correctly is not doing anything wrong, and capability-gating would still stop it.

**Where it fails, stated so it can be judged.** Some legitimate instruments genuinely need a new spec file. Behaviour that no existing spec touches has no existing home, and forcing the author into an unrelated file to get a red is worse than a clean new path. So the refusal needs an escape, and every escape is a hole: whatever form it takes will become the default the moment the backlog is large, which it is.

It is also unbuildable where the parent's observation was made. This pass had no configured `product.repos` at all, so the resolution step has nothing to resolve against, and the refusal would fire on every instrument rather than on the weak ones — turning a quality rule into a total block. That dependency is the assumption beneath this node.

**Cost.** Path resolution, a configured repo it can rely on, an escape hatch, and fixtures for both directions.

⚠️ Unvalidated. Agent-ideated.
