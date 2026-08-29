---
type: Solution
source: 'agent-run:unattended-sweep-2026-08-28'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: who-does-the-work. Position taken: nobody — the waiting step is removed rather than reassigned.**

The observed failure is a firing polling `/tmp/ost-suite-full.txt` for a test run *it had started itself*. The producer knew when it finished; the consumer was reduced to guessing at a file. This candidate says the ambiguity is downstream of a step that should not exist: a process that starts work it owns should be told when that work ends, not left to infer it from an artifact appearing on disk.

Concretely, the loop stops backgrounding a suite and polling for its output file. It either runs the suite in the foreground and reads its exit status directly, or starts it in a form whose completion is reported back — the harness already notifies when work it tracks finishes, and this workspace's own corrections ledger says as much: "To wait for a command you started, use `run_in_background: true`." A wait that never happens cannot expire ambiguously.

**What it gives up, stated plainly.** It only covers waits on work the firing itself started. Three of the waiting cases this repository has already catalogued in `WAITING_CASES` are not that shape — a CI check on a remote server, a task directory owned by another session, a condition on a third party's state. For those there is no producer to make announce anything, and this candidate offers them nothing. It is the strongest answer for the case that actually burned twenty minutes on 2026-08-29 and no answer at all for the majority of catalogued cases.

**Against its siblings.** The other two accept that waiting happens and improve what a give-up tells you. This one denies the premise for the subset where the firing is on both ends of the transaction. If it works, the sibling improvements still matter for the remaining cases — these are complementary rather than exclusive, and a reader should not treat picking one as retiring the others.

**Sharpest risk:** feasibility — whether the loop's actual waits are mostly self-started work or mostly foreign state. That is a census over the corpus, and it is cheap.

Ideated by an unattended pass on 2026-08-28 against the assigned dimension. **Not blind:** this surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author — the condition the blind-ideation rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.
