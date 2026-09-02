---
type: Opportunity
source: 'TRANSCRIPT:0e641ade-9c76-40f6-9a60-c6150096e8ac'
created: '2026-09-02'
evidence: observed
authorship: machine
---
#Opportunity #unvalidated #evidence/observed
[[The session declares at call time that a negative exit is the answer it wants]]
[[Demote an errored result to an observation when nothing in it diagnoses the command]]
[[Adopt each tool's published exit-code contract instead of authoring a notion of failure here]]

**The need (operator's voice):** "Half of what my agent does on purpose is ask a question whose answer is 'no' — a grep that finds nothing, an instrument run that comes back red because red is what I sent it to observe. The channel records every one of those as a tool failure. I want the commands that reported a finding separated from the commands that broke, because right now the loop files its own successful measurements as evidence that the product hurts."

## What was observed, first-party, this pass

`TRANSCRIPT:0e641ade-9c76-40f6-9a60-c6150096e8ac` (captured 2026-09-01, mirrored 0d ago) records 5 friction events, of which two are Bash calls whose non-zero exit carried exactly the information the caller asked for:

- **tool_error** (Bash): `Exit code 1 src/security/tools.ts:1480: // earned (see the class doc on 'Vault.setInstrument'), so it must be a src/security/tools.ts:1552: const line = vault.setInstrument(...)` — a search that *found* its matches and printed them, filed as a failure.
- **tool_error** (Bash): `Exit code 1 … Tests 3 failed | 7 passed (10)` — a test run that reported failures. On this product specifically, observing a spec fail is not an accident: an instrument is required to be red, and `ost-agent verify` exists to record that red. The channel files the loop's prescribed measurement as friction.

The remaining three events in that session are the already-mapped "file has not been read yet" class and belong to a different node.

## The mechanism, read first-party from the code

`ost_read_repo` on `src/adapters/transcript.ts` settles it. Inside `extractFriction`, the entire classifier for this kind is:

```
if (block.type === "tool_result" && block.is_error === true) {
  const denied = DENIAL_PATTERNS.some((re) => re.test(body));
  events.push({ kind: denied ? "permission_denied" : "tool_error", ... });
}
```

`is_error` is the host's flag, and the host sets it on any non-zero exit. So the adapter has exactly two categories for an errored result — a human said no, or the tool broke — and no third for *the command ran correctly and its answer was negative*. Nothing downstream can recover the distinction either, because `errorDetail()` keeps the exit-code line and the last error-looking line, and `ERROR_LINE` matches `/no match|failed|not found/i` — the very words a successful negative answer prints.

This is a different defect from the one the sibling beside it found. That node's finding is that `retry` is derived from call *shape* with no reference to outcome. This one is that `tool_error` is derived from an outcome flag with no reference to *intent*. Same channel, opposite halves of the classifier, and a fix to either leaves the other standing.

## Why this is not either sibling

- **"The friction channel fills with my own typos"** names noise made of *mistakes* — a shell-quoting slip, an edit whose search string drifted. Those commands were wrong. These were right, and their answer was wanted. Of that node's four candidates, *recurrence over incidence* ranks this class top rather than dropping it (the loop runs searches and instrument checks on every firing, so this recurs by construction), and *errors the session corrected itself* finds nothing to fold, because nothing was corrected. Only *filter to the product's own surface* would catch these, and it catches them by discarding all Bash friction including the genuine kind — coverage by amputation, not an address.
- **"I can't tell real friction from the loop doing exactly what I told it to do"** names noise made of prescribed *repetition*, filed by the `retry` branch on identical arguments. These are single calls with distinct arguments and would file identically the first time they ever ran.

Torres's test: a classifier that requires a failure diagnostic distinct from the command's own reported finding addresses this node and does nothing for either sibling; each sibling's candidates leave this class filed. Three needs, not three phrasings.

## Litmus test (more than one way to address this?)

Yes, and they trade off: require a stderr diagnostic the command did not itself print as its result before `is_error` counts as friction; recognise measurement-shaped commands (a test runner, a search) and file their non-zero exits as observations rather than errors; have the caller declare in-band that a non-zero exit is the expected answer, so intent is read rather than inferred; or drop Bash from the channel entirely and keep only the product's own tool surface, accepting the loss of genuine shell friction. Passes.

## Why it costs something

The loop's own verification work is the largest generator of this class: every instrument this tree asks a pass to observe is required to be red, and every red is an exit code the channel calls a failure. So the channel's volume rises with exactly the behaviour the product is trying to encourage, and — as the sibling census records — nothing in the tool surface can mark an item considered-and-declined, so each one is read in full and dismissed again on every future firing.

**Evidence rung:** `observed` — a mechanical transcript record of the agent's own session, plus a first-party read of the adapter that produced it. It grounds usability of this product's own feedback loop. It is not outside-user demand data and must not be counted as evidence that anyone wants this.

## For a human to review

Two things. First, whether a negative answer is genuinely *never* friction: a search returning nothing because the agent looked in the wrong place is a real navigation failure wearing this shape, and this node assumes that case is worth trading away. Second, the sample is one session read in full plus the mechanism; the *rate* at which this class occurs across the 567 unmapped records is unmeasured here, and the case for building anything should rest on a count somebody takes rather than on this node's two instances.

_Method: one evidence record read in full through `ost_next_work({evidence})`, one first-party read of `src/adapters/transcript.ts` through `ost_read_repo`, and three neighbouring node bodies read to apply Torres's test. Nothing was executed and no result is recorded — the code is reported as read, not as run._
