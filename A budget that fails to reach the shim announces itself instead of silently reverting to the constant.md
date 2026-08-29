---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: feasibility**, and it is the belief that decides whether this candidate is an improvement or a better-hidden version of the same defect.

**The belief, stated so it can be false:** when the budget does not reach the shim — the export missing, misspelled, empty, or non-numeric — the wait says so, rather than falling back to 300 and behaving exactly as it does today.

**Why this is the load-bearing belief and not a detail.** The defect being fixed is a number the composer never saw deciding when their wait stopped. A fallback that is silent reproduces that defect precisely, with one difference that makes it worse: today the constant is at least discoverable in `src/loop/wait.ts` as `DEFAULT_FOR_SECONDS = 300`, whereas a mechanism believed to be carrying the caller's 400 while actually using 300 is a defect nobody will look for. The observed session re-issued the same wait three times; a composer in that position who believed their budget was being honoured would keep re-issuing.

**What makes it genuinely uncertain.** Shell default-substitution is silent by construction — `${AWAIT_LIMIT:-300}` is exactly the idiom that swallows the distinction, and it is also the shortest and most natural way to write this. Announcing requires a deliberate extra branch in a script whose stated design value, in the module's own prose, is being self-contained and minimal. So the cheap implementation and the correct one differ, which is the condition under which an assumption is worth writing down.

**Non-numeric is the case most likely to be missed.** POSIX `sh` arithmetic on a non-numeric value does not reliably error; a bound that evaluates to zero would make the wait give up before its first sleep, which reads to a composer as the condition being instantly false.

**What it does not settle.** Whether the export can be plumbed from the harness at all — that is a separate question about what the firing's wrapper can see — and nothing whatsoever about whether the composer's own number is a good one.
