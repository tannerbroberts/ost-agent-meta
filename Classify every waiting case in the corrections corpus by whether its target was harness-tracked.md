---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-28'
created: '2026-08-29'
evidence: assertion
threshold: at least 50% of classified waiting cases target harness-tracked work
instrument: npx vitest run test/loop/wait-target-census.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** This is a count over records already on disk, not a question about anyone's preferences.

**What the spec must assert.** The corpus exists: `src/loop/wait.ts` states its three `WAITING_CASES` are lifted verbatim from `test/fixtures/corrections/<session>*.jsonl`, and that the ledger holds eight sightings of which six are the CI-check case. The spec reads those fixtures, extracts every refused or retried waiting-shaped call, and classifies each by its target into two buckets — **harness-tracked** (work started through a channel the harness reports completion for: a backgrounded tool task, a subagent or workflow run) versus **self-backgrounded** (a shell job, a `gh` poll against a remote, a file-existence condition on something no tool started). It then asserts the harness-tracked share meets the bar above.

**Why it fails against today's code for a reason specific to this question.** No classifier exists. `src/loop/wait.ts` carries `WAITING_CASES` with an `intent` string per case and no notion of what started the work — the module's whole subject is expression cost, not target provenance. So the spec cannot pass until someone writes the classification, and the shape of that classification is decided entirely by this question: change the buckets and the assertion changes.

**Honest disclosure about the red this currently produces.** `test/loop/wait-target-census.test.ts` does not exist, so today the command exits non-zero as `no-spec` — a red that would look identical for any question written on that path, and therefore the weak kind. It is recorded that way rather than dressed up: this surface cannot author spec files. The compensating work is above — the corpus is named, the buckets are defined, and the field that is missing from `WAITING_CASES` is identified — so a builder starts from a definition of done rather than an empty file. Not finished until the spec exists and fails on its assertion.

**Pre-committed reading of the verdict, fixed before the run.** At or above 50%, the assumption is supported and "Delete the wait let harness-tracked work announce its own completion instead of being polled" is the branch's first candidate. Below 50%, it is refuted, that candidate is retired rather than sequenced, and the liveness sibling becomes the default. This is written down now precisely because the available four cases already point below the bar, and a bar chosen after seeing the count is not a bar.

**What a result here does not settle.** Only coverage — what share of waits a notification could reach. It says nothing about whether notifications are better than polls where they do apply, nothing about the mid-flight progress the candidate gives up either way, and nothing about the liveness question its sibling owns. It is also a census of a corpus assembled for a different purpose, so it measures the waits that were *refused and recorded*, which may not be the same population as the waits this loop issues.
