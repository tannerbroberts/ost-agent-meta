---
type: Solution
source: 'TRANSCRIPT:9c00df65-1c8d-4171-a870-22efc103d834'
created: '2026-09-03'
evidence: assertion
killIf: >-
  Patterns in real use carry only one unsupported construct each, so naming them
  all at once saves no call over naming the first.
killBy: '2026-12-01'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Every construct this engine lacks can be located in a submitted pattern before the pattern is run]]

**Variation dimension: automated-vs-manual. Position: detection fully automated, repair deliberately left manual.** The sibling candidates either remove the pattern surface or hand the caller a document to read; this one keeps the raw pattern and keeps the human decision, automating only the part a machine is strictly better at — enumerating which constructs in a submitted pattern this engine does not implement.

A pre-flight parse walks the submitted pattern and returns, in a single refusal, every construct the engine lacks: `look-ahead at offset 4`, `named group at offset 19`, `possessive quantifier at offset 31`. The caller learns the whole edge from one rejected call instead of one construct per call, which is the specific cost the evidence records — the refusal states the boundary one construct at a time, so learning where the edge is costs as many calls as the pattern has unsupported pieces.

**What stays manual, and why.** The refusal may suggest a supported rewrite where an obvious one exists, but it never substitutes one and runs it. A silently narrowed search returns a result set the caller will read as an answer to the question they asked, and it was not. Choosing to accept a narrower search is a judgement about whether the difference matters for this question, and only the caller holds that.

**What it does not do.** It does not tell the caller the dialect before they compose — they still pay one failed call. It reduces that cost from N calls to one; it does not remove it. The candidate that removes it entirely is the bought-vs-built sibling, which publishes the dialect up front and pays for it in staleness instead.

## Provenance

Ideated by an unattended sweep on 2026-09-03 against the assigned variation dimension `automated-vs-manual`. Rests on the parent opportunity's evidence — six sessions recording the same one-construct-at-a-time refusal — and on nothing else.
