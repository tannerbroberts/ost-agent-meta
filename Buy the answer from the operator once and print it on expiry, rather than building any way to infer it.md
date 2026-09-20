---
type: Solution
source: 'agent-ideation:2026-08-29-unattended-sweep'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[An expiry note the operator writes once stays true long enough to be worth trusting]]

**Variation dimension: bought-vs-built. Position taken: nothing is built here; the missing knowledge is bought from the person once and replayed forever.**

The operator records, once, in the same hand-edited config that already carries `discovery.target`, what an expiry on this machine means and what to do about it — for example: "the full suite takes 6-9 minutes here; if a wait on it expires at 300s, do not re-wait, start it in the background and come back." On expiry the helper prints that sentence verbatim next to the condition that failed. No gradient is computed, no state is kept between calls, no cooperation is asked of the subject process.

**Why buying beats building for this particular gap.** The thing the expired session actually lacked was not telemetry — it was local knowledge that a full suite on this machine outruns a 300s ceiling. That knowledge already exists, in one head, and is stable for months. Every other candidate spends engineering to re-derive at runtime something a person could have written down in one line. This position takes the founder's own recorded preference for hand-edited operator files — the same shape as `discovery.target` and `evidence.ageOutDays` — and extends it one field.

**Against its siblings.** It is by far the cheapest and the only one that works identically for local, remote and queued subjects, because it makes no observation at all. It is also the only one that cannot adapt: it says the same sentence on the first expiry and the fifth, so it does not fix the re-issue loop, only makes each expiry less confusing. The heartbeat and budget-escalation candidates both act; this one only informs.

**What would make this the wrong pick, stated plainly.** It is a recurring-input artifact, and this project's own tree already records that such artifacts are the ones that go unmaintained — there is a live assumption elsewhere on exactly that question, about a highlight criteria note. A stale expiry note fails in the dangerous direction: it confidently tells a future session to do the wrong thing, which is worse than the current silence. It is the right pick only if the note is short enough to stay true across machine and suite changes.

**No instrument, and the reason differs from its siblings'.** The other two candidates are unreachable because the helper is not in this repository. This one is unreachable because its load-bearing claim is about whether one person writes and maintains one sentence — a viability question about a human, not about code. Either way there is no spec in this product's `test/` that could go red for it.

Unvalidated. Agent-ideated on 2026-08-29; a human to review.

## Definition of done — and it is not a command

"Ask the operator to write the expiry note now, then check ninety days later whether it is still true"

There is deliberately no instrument. The bar is: the note is still accurate at 90 days with no more than one edit in between. There is nothing to execute — writing the note *is* shipping this candidate in its minimal form, and the only measurement is whether one person's written advice survives ninety days.

The test title is quoted rather than wikilinked on purpose: its one backlink belongs to its parent assumption.

**Sequencing:** this is the only one of the three candidates whose test and whose build are the same act, which makes it the natural first move regardless of how the other two are ranked. Its feasibility half needs no test at all — `ost.config.yaml` already carries hand-edited operator fields the tooling reads and never writes, verified with repo sight on 2026-08-29.

## 2026-09-20 — this node's own reason stands; the premise it states about its siblings does not

Three lines. Nothing here bears on whether this candidate is right.

**The sentence being corrected.** This node states: "**No instrument, and the reason differs from its siblings'.** The other two candidates are unreachable because the helper is not in this repository." The second clause is false. Read first-party this pass via `ost_read_repo`, `src/loop/wait.ts` authors the `await` helper in full — `renderWaitShim()` emits the entire POSIX `sh` script, `ost-agent wait-shim` prints it, and `examples/automation/build-pass.sh` installs it onto `PATH` — and `test/loop/wait-primitive-affordance.test.ts` installs and executes it, asserting its exit statuses and its `gave up after` stderr line. Both sibling candidates are corrected on their own nodes this pass.

**What survives untouched, which is this node's actual argument.** Its own reason for having no instrument is unaffected and remains sound: the load-bearing claim here is whether one person writes and maintains one sentence, which is a viability question about a human and not about code. No exit code reaches it, and no spec in this repository could. The contrast the sentence was drawing is what fails — the siblings are not unreachable, so this node is not the only one of the three whose bar needs a person; it is the only one whose bar needs a person *for that reason*.

**Limits.** Source read, not run; nothing executed, no result recorded. Whether the siblings' feasibility halves are worth instrumenting is argued on those nodes, not here. No rung moved, no instrument set, no status changed, no node created. `ost_check` is withheld on this surface, so this write is unverified by the invariant checker by design.

_Method: first-party `ost_read_repo` full reads of `src/loop/wait.ts` and `test/loop/wait-primitive-affordance.test.ts`._
