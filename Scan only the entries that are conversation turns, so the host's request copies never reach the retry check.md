---
type: Solution
source: 'agent-ideation:2026-10-17-unattended-sweep'
created: '2026-10-17'
evidence: assertion
killIf: >-
  A re-harvest of sessions 8275c757 and a6cedf56 with the filter in place still
  files a retry whose id appeared earlier in the session, or files fewer
  tool_error events than it did before
killBy: '2027-04-17'
authorship: machine
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: who-does-the-work. Position taken: the harvester does all of it, at read time, and nobody downstream has to discount anything.**

`extractFriction` reads `message.content` from every line of the session file, whatever the line's `type`. This candidate makes it read only lines whose `type` is `assistant` or `user`, the two that are conversation turns. The host's `api-request-blob` lines, and any other bookkeeping line, are skipped before any block is looked at. The second copy of a parallel call never reaches the retry check, so no record files it and no reader or pass ever sees it.

**Why this position and not another.** The work lands on the one component that already knows the session file's shape. A reader, a later pass or a config file would each have to learn the same fact again, every time.

**What it deliberately gives up.** It depends on a list of entry types this product maintains. If the host ever writes a third copy of a turn inside a turn-typed line, or renames its turn types, the filter is wrong and nothing says so. The bought-vs-built sibling avoids exactly that dependency, and that is the comparison to make.

**What it does not touch.** Prescribed repeats are real turns, so they still file. That stays the parent's problem. It also cannot fix records already on disk: evidence is append-only, and the 1,082 unmapped records keep whatever retries they were filed with.

**Cheapest form.** One guard at the top of the per-line loop in `src/adapters/transcript.ts`, plus fixtures in the spec that give the two copies their real entry types.

**Honest note on how this was ideated.** All three candidates under this opportunity were written in one context by one author, one after another. This surface cannot run independent blind ideators, so discount their apparent distinctness.

Unvalidated. Agent-ideated 2026-10-17; for a human to review.
