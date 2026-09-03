---
type: Solution
source: 'TRANSCRIPT:9c00df65-1c8d-4171-a870-22efc103d834'
created: '2026-09-03'
evidence: assertion
killIf: >-
  A caller hits an unsupported-construct refusal on a surface whose description
  already named that construct as absent.
killBy: '2026-12-01'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A caller reads a tool's stated dialect before composing against it]]

**Variation dimension: bought-vs-built. Position: the dialect definition is adopted from outside, verbatim; the only thing built here is the pointer to it.** The sibling candidates build something — a structured query compiler, a pattern parser. This one builds nothing that can drift, on the argument that the engine's own maintainers already publish an exact syntax reference and any second description of it is a copy that will disagree with the engine before it disagrees with itself.

The tool's description states which engine it is — "patterns are RE2 syntax as implemented by ripgrep; look-around and backreferences are not present" — and links the upstream reference. The caller reads the boundary before composing rather than after failing, which is the thing neither other candidate delivers.

**What is bought, precisely.** The enumeration of what the dialect does and does not contain, maintained by people who change the engine when they change it. What is built here is one sentence and one URL.

**What it gives up.** It is prose, so nothing enforces that it stays true: an engine swap or a version bump can make the description wrong with no test going red, and a description that disagrees with its own validator is a failure mode this tree already holds a separate node about. It also assumes the caller reads the description before composing, which is an assumption about behavior and not a mechanism — and that assumption is the one worth testing first, because if callers do not read it, this candidate delivers nothing at all while costing almost nothing.

**Cheapest of the three by a wide margin**, which is the argument for trying it first even though it is the weakest guarantee.

## Provenance

Ideated by an unattended sweep on 2026-09-03 against the assigned variation dimension `bought-vs-built`. Rests on the parent opportunity's evidence and on nothing else. The upstream reference was not fetched — this pass did not spend a web lookup to confirm the published syntax page still exists, so that is an open check for whoever picks this up.
