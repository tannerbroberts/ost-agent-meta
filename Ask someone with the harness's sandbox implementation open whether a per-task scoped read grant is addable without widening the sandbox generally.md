---
type: AssumptionTest
source: 'TRANSCRIPT:0f28d01f-35fa-49f0-b085-89170e306ef8'
created: '2026-08-18'
evidence: assertion
lane: humans-required
---
#AssumptionTest #unvalidated #evidence/assertion

Threshold: a clear yes/no on whether the working-directory restriction is implemented as a single session-wide allowlist or something a per-task declaration could extend. Same reason as its sibling test: the restriction lives in the harness, not in a repository this tree can read or run a spec against.

A person outside the building is the measurement here: The harness maintainer is irreducibly the measurement — the sandbox's read-scoping rules live in Claude Code's own implementation, not in a repository or vault this tree can inspect or test.

## Pre-committed threshold

**Pre-committed threshold:** the answer names which of exactly 2 shapes the working-directory restriction actually has — a single session-wide allowlist, or a structure a per-task declaration could extend — with at least 1 pointer into the sandbox implementation. A yes counts as support only if it also states whether the per-task grant would be scoped to that task alone rather than persisting for the session. "Don't know" and "probably extensible" are inconclusive, not support.

This paragraph adds no new question. It restates the bar the node's own first sentence already carries, in the bold pre-commitment form `askedOf` (`src/eval/coverage.ts`) reads — this node has no `threshold:` frontmatter field, so the prose scan classifies it, and a bare `Threshold:` line matches no lead-in and reads as `absent`.

The scoped-to-that-task clause is stated in advance because the two answers differ in what they cost: a grant that persists for the session is a general widening wearing a per-task name, which is the outcome the question exists to avoid.

What clearing this bar does not settle: whether a scoped grant is one the operator would enable. Feasibility in the harness and willingness to turn it on are separate, and only the first is asked here.

_Added by the 2026-08-22 unattended sweep. Correctly humans-required — the restriction lives in the harness, not in any repository this tree can read. No lane changed, no result recorded, no instrument set._
