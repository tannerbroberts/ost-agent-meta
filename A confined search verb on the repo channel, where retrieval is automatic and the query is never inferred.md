---
type: Solution
source: 'agent-ideation:2026-09-08-unattended-sweep'
created: '2026-09-08'
evidence: assertion
killIf: >-
  Twenty consecutive captured firings record fewer than one guessed-path refusal
  each, so the guessing this verb removes is not actually recurring
killBy: '2026-12-08'
authorship: machine
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: automated-vs-manual. Position taken: the retrieval is automated; the query stays entirely the caller's and is never inferred, expanded, or guessed at.**

`ost_read_repo` grows one more shape beside its listing and its file read: given a literal string, it returns the files and line numbers containing it, confined to `product.repos` exactly as the existing read is, with the same `.ost-agent/` refusal, the same redaction, and a hard cap on matches returned. What is automated is the scan. What is deliberately left manual is everything about intent: no query rewriting, no fuzzy matching, no "did you mean", no ranking by relevance. The caller names a literal string and gets back where it occurs.

**Why the manual half is the point rather than a shortcut.** A surface that infers what the agent meant becomes a second thing to be wrong about, and its errors are silent — a rewritten query that misses is indistinguishable from a string that genuinely is not there, which is exactly the failure mode this need is made of. A literal scan can be wrong only in the way the caller was wrong, and the caller can tell.

**Against its siblings.** Unlike widening the harness grant, this keeps every confinement the read channel already enforces: it cannot leave `product.repos`, cannot open the sidecar, and cannot return unredacted secrets. Unlike adopting an outside indexer, it needs no subprocess, no index to build, and nothing to keep current — the constraint in this product's own CONTRIBUTING.md that no tool shells out stays intact by construction.

**What it costs.** It is the only candidate of the three that is actual product surface: a new verb to specify, refuse correctly, cap, document and keep true. And a linear scan over a repository is not free, so a cap that is too low returns a misleading "no matches" and a cap that is too high puts a scan on a path that has a wall-clock budget.

**What would make this the wrong pick.** If the questions being asked are really about *symbols* — where is this function defined, what calls it — then a literal string scan is a poor instrument for them and the adopted-index sibling is better aimed. The parent node's recorded instances are mixed: `grep -rn "triageLanes" src/cli/` is a symbol question, `grep -n "day(s) ago"` is a string question. Which kind dominates has not been counted, and counting it would separate this candidate from its third sibling more sharply than anything written here.

Ideated by an unattended pass on 2026-09-08 against the assigned dimension. **Not blind:** this surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author — the exact condition the blind-ideation rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.

Unvalidated. A human to review.
