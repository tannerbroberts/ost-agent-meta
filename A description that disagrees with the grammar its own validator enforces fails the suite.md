---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
threshold: >-
  every example command quoted in a tool description parses, and at least 1
  seeded mismatch fails the suite
instrument: npx vitest run test/mcp/description-grammar-parity.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility. Small and fast: it reads two artefacts already in the repository and compares them.**

Take every command-shaped example quoted in an `ost_*` tool description and run it through `parseInstrument` from `src/knowledge/instruments.ts`. Each must come back as an instrument rather than a rejection. Then seed the mismatch deliberately — a description quoting a form the validator does not accept, such as one carrying a `-t` filter — and assert the check fails on it, so the parity test cannot pass vacuously.

The positive control is the part worth insisting on. A parity check that finds nothing looks identical to one with nothing to find, and this vault has already been bitten by that shape: `test/ost/vault-write-guard.test.ts` carries an explicit "the guard cannot pass vacuously" block for the same reason, and the `no-spec` classification exists because a red that every question would produce distinguishes none of them.

**Why it is red today.** No such check exists — nothing in the suite reads a tool description at all, so no artefact today asserts the two agree. It goes green when the parity check is written and the descriptions are made to satisfy it.

**Honest labelling of how red it is.** `test/mcp/description-grammar-parity.test.ts` does not exist, so the first run is filed `no-spec` rather than a true red, and would fail identically for any question written on that path. `test/mcp/` is a real, populated directory, and the threshold above is a bound bar with a positive control in it — the two properties this vault's own 2026-08-09 and 2026-08-21 findings identify as what separates a weak red a builder can act on from one they cannot. The stronger form, naming an assertion inside an existing spec, is not expressible: the instrument grammar accepts a bare `npx vitest run <path>.test.ts` and rejects a `-t` filter as shell punctuation.

**A note on what this test is an instance of.** The candidate it serves proposes publishing a grammar; this test's own instrument was constrained by that same grammar being unpublished and discovered by refusal. That is not irony worth much, but it is one more first-party sighting of the refusal class the parent opportunity is about, and it happened during the pass that wrote this node.

**What a green does not settle.** Whether publishing the grammar stops the refusal — that depends on a session reading the description before composing, which is a usability question about the reader and needs a separate test. It also covers only grammars statable in advance, so it says nothing about the state-dependent refusals (the humans-required lane) that this candidate admits it cannot reach.

## Instrument Log
- 2026-08-27 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-28 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-31 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/mcp/description-grammar-parity.test.ts` — test/mcp/description-grammar-parity.test.ts does not exist — no spec was collected, so nothing was measured

## 2026-09-08 — the seeded mismatch is now an observed specimen, and it is not in a tool description

Kept short. Two findings, and the second widens what this test has to read.

**1. The positive control this node proposes to synthesise has occurred for real.** The body above says to seed the mismatch deliberately — "a description quoting a form the validator does not accept, such as one carrying a `-t` filter" — and treat it as the control that stops the parity check passing vacuously. `USAGE:2026-09-08`, captured at this pass's own ingest, records a live `ost_set_instrument` call refused for exactly that shape: setting `npx vitest run test/ost/pending-ask-queue.test.ts -t "a test born humans-required at creation is in the queue with a non-null age"` on the test "A test born humans-required at creation is in the queue with a non-null age", rejected with "contains shell punctuation. Instruments are run as argv wi…". It was one of only 3 failed calls in 451. So the control has a real specimen rather than an invented one, and whoever writes the spec can use it verbatim.

**2. The artefact that disagrees with the validator is the unattended pass prompt, not a tool description — and this test currently would not read it.** The refusal above is not an agent improvising. `.claude/commands/ost-pass.md` — the file `examples/automation/autonomous-pass.sh` strips of frontmatter and hands over verbatim as the firing's prompt — instructs the pass, in its `solutionsMissingInstruments` step, to prefer precisely that form. Its worked contrast names `npx vitest run test/foo/bar.test.ts` against a missing file as the WEAK kind, and `vitest run test/git/conflict-guard.test.ts -t "refuses a write whose base hash drifted from the last read"` as the STRONG kind a builder can act on. Meanwhile `ost_set_instrument`'s own description says "Nothing else is accepted — no shell punctuation, no arbitrary command." So the pass is instructed to compose the one form its writing tool refuses, and is told the form it CAN compose is the weak one.

**Why this changes the test rather than merely illustrating it.** As worded, this node reads "every command-shaped example quoted in an `ost_*` tool description". On the evidence above the tool descriptions are consistent with the validator — `ost_set_instrument` quotes a bare `npx vitest run test/git/conflict-guard.test.ts` and states the no-punctuation rule outright. The disagreement lives one artefact over, in the prompt and the ruleset that generates the skill, which no spec in the suite reads either. A parity check scoped to tool descriptions would go green and leave the observed refusal untouched. The threshold should extend to command-shaped examples quoted in `.claude/commands/ost-pass.md` and `src/knowledge/ruleset.ts`, or the check will pass while the defect that produced this specimen stands.

**The consequence for this node's own 68 no-spec runs, which is the uncomfortable part.** This node's Instrument Log carries 68 consecutive `no-spec` entries from 2026-08-27 to 2026-09-02, and the body already concedes that "the stronger form, naming an assertion inside an existing spec, is not expressible" under the grammar. Put beside finding 2, that is a closed loop worth stating once: the grammar admits only a bare spec path, so the only red an agent can author is a missing-file red; the pass prompt calls that red weak and asks for the assertion-level form; and the assertion-level form is refused. The rollup's observation that 260 of 266 recorded reds read "No test files found" is not 260 lazy authors — it is the single form the tool accepts. Whoever picks up the parity check should decide whether the repair is publishing the grammar or widening it, because publishing it alone leaves every future instrument no-spec by construction.

**Limits.** The `.claude/commands/ost-pass.md` quotations are read from this firing's own delivered prompt text, which `autonomous-pass.sh` was read first-party this pass and confirmed to assemble from that file by `awk` on its frontmatter — not from an `ost_read_repo` read of the file itself, so the wording is this pass's received copy rather than the file on disk (16,432 bytes, `wouldTruncate: false`, so it is readable by a pass that wants to confirm). `src/ost/instrument.ts` probes at 29,758 bytes with `wouldTruncate: true` and could not be served whole, so the refusal rule is taken from the tool description and the observed refusal text together, not from the parser. Nothing was executed, no instrument was set or replaced, no rung moved, no status changed, no node created. This node's threshold and instrument stand unchanged.

_Method: this pass's own `ost_ingest_inbox`, the body served by `ost_next_work({evidence: "USAGE:2026-09-08"})`, and first-party `ost_read_repo` reads of `examples/automation/autonomous-pass.sh` and two probes. Observed behaviour of this product's own tool surface; it grounds feasibility, not desirability._
