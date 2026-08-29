---
type: AssumptionTest
created: '2026-07-27'
evidence: assertion
instrument: npx vitest run test/loop/laundering-guard-false-positives.test.ts
sight: grounded
---
#AssumptionTest #evidence/assertion

**The two assumptions, and the second is the risky one.**

1. That an unguarded shell pipeline is a real and recurring way for a proving command to hide failure. **This one is already settled** -- it was observed in production use before the guard existed, which is why the guard exists.
2. That refusing it does not refuse commands whose exit codes were honest. **This is the assumption that can still be wrong**, and it is the one that would do damage: a guard that fires on legitimate invocations teaches people to stop wrapping commands in `loop step` at all, which loses the whole record rather than one step of it.

**How assumption 2 gets tested.** Not by more unit tests -- those only re-assert what the author already believed. By reading `runs.jsonl` across the next several firings and across both vaults, and counting refusals:

- how many `loop step` invocations were refused
- for each, whether the refusal was correct (the pipeline really could have hidden a failure) or a false positive (the exit code was already honest)

**Pre-committed threshold, fixed before the test runs.** Over the next **10 firings**: if **any** refusal turns out to be a false positive -- a command whose exit code could already report failure -- the detector is too broad and must be narrowed before it costs anyone a record. If there are **zero refusals at all** across 10 firings, that is not a pass either: it means nobody writes pipelines and the guard is dead weight sitting in the hot path, which should be recorded honestly rather than counted as success. **Between 1 and 10 correct refusals with no false positives** is the outcome that would justify it.

**What it cannot tell anyone.** Whether the *fix* people reach for is the right one. Someone told to add `set -o pipefail` might instead drop `loop step` and run the command bare, which satisfies the guard by escaping it. That behaviour is invisible to `runs.jsonl` by construction -- the step simply never appears -- and only a human reading a firing's transcript would catch it.

**Lane: compute-only** (prose, not a label; a human runs `ost-agent lane` to make it one). It reads health records this loop already writes and needs no participant.

## History
- 2026-08-29 instrument: (none) → npx vitest run test/loop/laundering-guard-false-positives.test.ts [sight: grounded] — Reads the loop's own runs.jsonl across the recorded firings, selects every `loop step` invocation the pipeline guard refused, and asserts this node's two pre-committed edges: at least 1 refusal exists (the node fixes zero refusals as a failure meaning the guard is dead weight in the hot path, not as a pass), and zero of those refusals are false positives — a refused command whose exit code could already report failure. It fails today because nothing in the suite reads runs.jsonl for guard refusals at all. Labelled honestly: test/loop/laundering-guard-false-positives.test.ts does not exist yet, so the first run files as no-spec rather than a true red; once the spec exists it can fail on either edge for a reason specific to this question, because both edges are counts over a corpus already on disk. The node's own prose already declares Lane: compute-only and names runs.jsonl as the artefact, so this gives an existing question a runnable form rather than inventing a new one.
