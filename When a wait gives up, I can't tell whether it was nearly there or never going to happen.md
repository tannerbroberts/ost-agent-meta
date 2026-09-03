---
type: Opportunity
source: 'TRANSCRIPT:cf2cef94-0aee-4647-80e0-9d64dbe0e18d'
created: '2026-08-29'
evidence: observed
authorship: machine
---
#Opportunity #unvalidated #evidence/observed
[[Remove the wait have the work the firing started announce its own completion]]
[[The wait reports expiry as its own outcome, and says whether the condition was moving]]
[[Adopt timeout(1)'s settled expiry convention instead of inventing a private one]]

**The need (operator's voice):** "My unattended run waited, gave up, and told me the same thing it would have told me if the thing I was waiting for were never going to happen. So it waited again. Twenty minutes of a firing I am paying for went into learning nothing."

**What was observed.** `TRANSCRIPT:cf2cef94-0aee-4647-80e0-9d64dbe0e18d`, an unattended firing captured 2026-08-29 (mirrored 0d ago), produced 9 friction events. Four of them are the same line:

- `Exit code 1 … await: gave up after 300s; the condition still exits 1.` ×4
- plus two `retry` events re-issuing the identical wait — `await 'grep -qE "Test Files.*\(" /tmp/ost-suite-full.txt'` and the same against `/tmp/ost-suite-quiet.txt`, each carrying `timeout: 600000`.

The session was waiting for its own test suite to finish writing a results file. It gave up, re-issued the same wait unchanged, and gave up again. Two conditions, four expiries, roughly twenty minutes.

**The mechanism, read first-party out of the code rather than inferred.** `renderWaitShim` in `src/loop/wait.ts` ends its loop with `exit "$rc"`, and its own doc comment states the design: "The exit status is the condition's own, and giving up says so on stderr rather than looking like success." So an expiry and a condition that is simply false exit identically. `DEFAULT_FOR_SECONDS` is 300 and is applied when the caller names no third argument — which none of the observed calls did, so the wait gave up at half the 600s the caller had allotted the Bash call, on a bound the call site never mentions. `test/loop/wait-primitive-affordance.test.ts` pins the current behaviour explicitly: `run(["exit 3", "1", "2"])` asserts `status` is `3`, the condition's own code.

**Why it matters.** The give-up carries no evidence of progress. Nothing in it says whether the condition's output changed between the first attempt and the sixtieth, so the caller cannot distinguish "the suite was three seconds from finishing" from "the file will never exist". Re-issuing the identical wait is the rational move under that ambiguity, and it is also the expensive one — and it happens with nobody watching, which is the condition under which a wrong guess costs a whole firing rather than a shrug.

**Distinct from its neighbours, by Torres's test.** Against "One red run is all I get, and nothing in it separates noise from a real break": a solution that makes a wait report whether its condition moved between attempts addresses this node and does nothing for a flaky perf gate, and re-run-and-compare addresses that sibling and nothing here. Against "A refusal names a field that was fine, so the retry fixes the wrong thing": that node is about a message that misdirects a retry with wrong information; this is about a message that cannot direct one at all, plus a bound the caller did not choose. Both pass.

**Litmus test (more than one way to address?):** Yes — give expiry a reserved exit status distinct from any condition's, the way `timeout(1)` uses 124; report the attempt count, elapsed time and whether the condition's output changed; make the bound explicit at the call site or inherit the caller's own timeout instead of defaulting under it; block on the job's exit rather than polling for its artifact. Real trade-offs between them. Passes.

**Evidence rung:** `observed` — the source is a mechanical capture of the agent's own session, not a recalled account. It observes this product's own runs rather than an outside user, so it grounds usability and says nothing about whether anyone else wants this.

_Source: `TRANSCRIPT:cf2cef94-0aee-4647-80e0-9d64dbe0e18d` via `ost_next_work`, plus first-party reads of `src/loop/wait.ts`, `test/loop/wait-primitive-affordance.test.ts` and `examples/automation/build-pass.sh` through `ost_read_repo`. No test was run and no result is recorded._

## 2026-09-02 — a second independent instance, and its producer is the other kind

Kept short deliberately; this node's neighbours already record that long appends are the ratchet.

**The pattern recurred, four days later and unchanged.** `TRANSCRIPT:33913791-83fb-4d6c-9b03-47e96fbb292b` (captured 2026-09-03T02:32Z, mirrored 0d ago) produced 13 friction events, four of them the identical line this node was opened on: `Exit code 1 await: gave up after 300s; the condition still exits 1.` One `retry` event re-issues the same wait. So the behaviour this node describes is not a single bad session — it has now been mechanically captured twice, in unrelated firings, at four expiries each.

**The part that is new, and it is about a sibling's premise rather than this node's.** The cited record on this node (`cf2cef94`) was waiting on `/tmp/ost-suite-full.txt` — a file the session's own foreground shell command was writing, i.e. a shell-backgrounded producer. This record waits on `grep -q "^exit=" /private/tmp/claude-501/-Users-tanner-ost-agent-meta/33913791-83fb-4d6c-9b03-47e96fbb292b/tasks/ba73258n2.output` — the harness's own per-task output path, i.e. **a harness-tracked producer**. The two recorded instances of this failure therefore sit on opposite sides of the distinction the assumptions "Most of what this loop waits on is work the harness tracks, not shell-backgrounded jobs it started itself" and "Most of the waits this loop actually performs are on work the firing itself started" turn on, and which the tests "Classify every waiting case in the corpus by whether its target was harness-tracked" and "Census every blocked wait in the corpus and count how many had a producer the same firing started" propose to count.

**Why that is worth one line to whoever runs that census.** The solution "Delete the wait let harness-tracked work announce its own completion instead of being polled" only reaches waits whose producer the harness tracks. On the two instances on record the split is one and one, so nothing here says which way the corpus leans — but it does establish that both kinds occur, which means a census that finds only one kind has probably mis-classified rather than found a clean answer. n=2 is a shape, not a rate, and it is offered as the former.

**One figure in the record is truncated and is therefore not claimed.** The retry event's Bash arguments show `"timeout":90…` cut off mid-number, so this record neither confirms nor contradicts this node's existing finding that the wait gave up at half the timeout the caller had allotted. Reading a bound off a truncated integer would be inventing it. Whoever wants that figure should take it from the raw transcript rather than from this record.

_Source: `TRANSCRIPT:33913791-83fb-4d6c-9b03-47e96fbb292b` via `ost_next_work({evidence})`, read in full. Observed behavior, captured mechanically from the agent's own session — it grounds usability, not desirability, and adds no outside voice. The harness-tracked classification is read off the output path's shape, not from harness source, which this surface cannot see. Nothing executed, no test run, no result recorded, no rung moved (this node already rests on `observed` and n=2 does not move it)._

## 2026-09-03 — n=2 becomes a corpus rate, and the classification census this node calls for is only half-answerable from evidence records

Kept short, per this node's convention. Two findings: the rate this node explicitly declines to claim, and a methodological limit on the census it points a future pass at.

**The rate. 22 records of 635, or 3.5%.** The section above ends "n=2 is a shape, not a rate, and it is offered as the former." A grep for `await: gave up after` across every `TRANSCRIPT_*.md` in this vault returns **22 distinct records**. So the pattern is not two unlucky firings: roughly one session in twenty-nine hits this, and because the two cited records carry four expiries each, the event count is a multiple of the record count. That is small in share and expensive per instance — this node's own arithmetic puts a four-expiry session at roughly twenty minutes of paid firing spent learning nothing.

**Sizing, offered rather than acted on.** Against the corpus's largest signatures — read-before-write at 285 records, permission denial at 143 — this is a minor one by frequency. It is also the only one of the five where the cost per occurrence is measured in wall-clock minutes of unattended compute rather than one wasted call, so record share understates it. Which of those matters more is the operator's call and this pass does not make it.

**The census, partially run, and the reason it cannot be finished from here.** This node points a future pass at "Classify every waiting case in the corpus by whether its target was harness-tracked". That classification needs the *wait command*, and the corpus preserves it unevenly: a `retry` event carries the Bash arguments including the command text, while a `tool_error` event carries only the message `await: gave up after 300s; the condition still exits 1`, which names no target. **Only 13 of the 635 records preserve an `await '…'` command at all**, against 22 that record an expiry. So a census run over evidence records can classify at most ~59% of the instances it can count, and the missing 41% are missing structurally rather than by sampling.

**What the classifiable 13 split into.** 2 target the harness's per-task output path (`/private/tmp/claude-501/…/tasks/…`) — `2a530e09` and `33913791`. 4 target a shell-backgrounded artifact under `/tmp/ost-…` — `4972fdeb`, `98a40050`, `cf2cef94`, `acba7e27`. The remaining 7 wait on other conditions. So on visible targets the split runs 4 shell-backgrounded to 2 harness-tracked, which is the same "both kinds occur" shape the section above established at 1 and 1, now at 4 and 2. It still does not settle which way the corpus leans, and n=6 on a 41%-blind sample is not a rate. It does sharpen the warning already recorded: a census reporting a clean one-sided answer has probably mis-classified, and it should state how many instances it could not see the target for.

**One incidental confirmation, since it happened while running the above.** The attempt to exclude the harness path with a negative look-ahead was refused by ripgrep — "look-around, including look-ahead and look-behind, is not supported" — which is the same refusal already mapped on this tree and already counted among the corpus's repeating signatures. Recorded here only because it occurred in this pass's own work; no node changed for it.

**Limits.** The 22 counts records containing the expiry string anywhere, so a record quoting it inside a retry payload counts alongside one recording it as a tool error — the same inflation hazard the evidence-census node flags for its own record-level counts. The 13/2/4 split is read off path *shape*, not from harness source, which this surface cannot see; a harness-tracked producer writing somewhere else would be mis-filed. Nothing was executed, no test run, no result recorded, no rung moved — this node already rests on `observed` and a corpus count of its own signature does not move it.

_Method: four `Grep` counts over every `TRANSCRIPT_*.md` in this vault's evidence folder. Observed behaviour of this product's own agent, captured mechanically — it grounds usability, not desirability. The records counted stay listed as unmapped; counting them does not map them._

## Corroboration — two give-ups back to back in one session (unattended sweep, 2026-09-03)

`TRANSCRIPT:fb9ff385-b77f-4210-a84a-b64a8f04be6b` recorded `await: gave up after 300s; the condition still exits 1` **twice within the same session**, alongside two `File has not been read yet` errors from `Edit` and `Write`.

**The one thing here that is not already on this node.** Every instance cited above is a give-up in a different session. This record is two in one, which is the shape this node's claim predicts but had not yet observed: a run that cannot tell "nearly there" from "never going to happen" has no basis for choosing a different budget the second time, so it spends the identical 300s again. The two give-ups are indistinguishable from each other in the record, exactly as each is indistinguishable from a success that needed 301s.

**What it does not establish.** Whether the two waits were on the same condition — the friction record carries the message and not the command, so a repeat of one wait and two unrelated waits look the same here. That distinction is the whole of this node's need, and this record demonstrates the gap rather than closing it.

_Source: `TRANSCRIPT:fb9ff385-b77f-4210-a84a-b64a8f04be6b` — observed behavior, captured mechanically from the agent's own transcript. Grounds usability, not desirability. The two `File has not been read yet` errors in the same record belong to "The file changed after I read it, and the failed edit is how I find out" and are noted here only because they share the session, not because this node claims them._
