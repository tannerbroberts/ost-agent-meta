---
type: Solution
source: 'agent-ideation:2026-09-08-unattended-sweep'
created: '2026-09-08'
evidence: assertion
killIf: >-
  The smallest usable indexer cannot be driven without spawning a subprocess, so
  the adapter turns out to be the whole build and nothing was actually adopted
killBy: '2026-12-08'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A code index exists in library form that answers in-process, so adopting one needs no subprocess]]

**Variation dimension: bought-vs-built. Position taken: the index and its query language are adopted from outside exactly as they are; the only thing built here is the adapter that hands a question to it and shapes the answer.**

Symbol indexing is a solved problem with several mature answers — a tags file, a language server's symbol index, a library-form matcher — and each already defines what a query is, what a result is, and how a definition differs from a reference. This candidate takes one of them whole and writes the smallest possible layer that accepts a question, asks the index, and returns file-and-line confined to `product.repos`. Nothing about the query language is designed here.

**Why adopt rather than build.** The sibling that writes a literal-string scan will meet, in order, every question a search tool eventually gets asked: whole word or substring, case sensitivity, definitions versus references, how to rank, what to do about generated files. Each is a small decision and their sum is a search tool nobody set out to write. An adopted index has already made all of them, and made them the way the ecosystem expects, so an agent that knows the tool already knows this surface.

**The distinguishing capability, which is not speed.** This is the only candidate of the three that can answer *where is this defined* as a different question from *where does this string occur*. The parent node's own recorded errands are split between those two kinds, and the string-scan sibling can only serve one of them.

**What it costs, and the cost is structural rather than incidental.** An index is state: it is built, it goes stale, and something has to decide when to rebuild it. That is a maintenance surface neither sibling has. Worse for this product specifically, most off-the-shelf indexers are programs rather than libraries, and driving a program means spawning one — which this repository's own CONTRIBUTING.md forbids for tools on this surface. So the adoption is only real if a library-form index exists that runs in-process; otherwise what looks like buying is building a subprocess boundary, plus a policy exception, plus the adapter.

**What it gives up.** Weight and time-to-first-answer. The grant sibling ships today and the scan sibling is a bounded piece of work; this one is the largest of the three and the only one that adds a dependency the project must then live with. It earns that only if symbol questions turn out to dominate string questions, which nothing has counted.

Ideated by an unattended pass on 2026-09-08 against the assigned dimension. **Not blind:** this surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author — the exact condition the blind-ideation rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.

Unvalidated. A human to review.
