---
type: Solution
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: automated-vs-manual. Position taken: extraction is automated, the equivalence judgement is deliberately manual.**

The harvester computes and stores a signature for every friction event as it captures it — cheap, mechanical, no judgement. What is never automatic is the collapse. The operator is shown signatures ranked by frequency and marks which ones are *the same problem*; the queue folds only what they have marked, and an unmarked signature stays individually listed forever.

**Why the manual half is the point rather than a shortcut.** Whether two errors are one problem is not a string-distance question. `Cannot find module './src/security/tools.js'` and `Cannot find module './scripts/provenance-census.js'` share almost no text and are one problem — a command run against an unbuilt or wrongly-rooted checkout. `HTTP 503 from api.github.com` and `permission not granted for ost_check` are textually unlike and also unlike each other, and one of them is not a product defect at all. Any normalizer aggressive enough to merge the first pair will merge the second, and any normalizer safe enough to keep the second pair apart will leave the first pair as two. The equivalence relation is domain knowledge, and it lives in the person who knows what the build loop does.

**Against its siblings.** Unlike the read-time grouping, this leaves a durable record of what was judged equivalent, so a wrong merge is visible and correctable instead of silently repeated every pass. Unlike widening the age-out predicate, it never collapses anything on a rule the operator did not author, so a novel problem cannot be buried by a mechanism nobody inspected.

**What it costs, and this is its sharpest risk.** It asks a specific person for recurring input, and this project's own tree already records that artifacts asking for recurring founder input are the ones that go unmaintained — there is a live assumption elsewhere on exactly that question ("The founder will actually maintain a highlight criteria note over time"), and a sibling branch proposes reading amendment counts out of the vault's git log to settle that class of belief cheaply. A stale signature list fails in the safe direction, though, which is the one real advantage it has over the age-out route: unmarked signatures stay listed, so neglect produces today's noisy queue rather than a quietly buried finding.

**What would make this the wrong pick.** If the signatures turn out to be few and stable — and the 6-record sample that produced this opportunity suggests roughly five modes — then asking a person to curate five entries is ceremony around a hard-coded list. It is the right pick only if the set is large enough to need judgement and slow-changing enough that someone will keep up.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author, because this surface holds no grant to run independent parallel ideators. That is the condition blind ideation exists to prevent; discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-08-30; a human to review.
