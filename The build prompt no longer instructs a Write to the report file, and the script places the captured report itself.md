---
type: AssumptionTest
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
threshold: >-
  Both assertions in test/automation/build-pass-report-channel.test.ts pass: (1)
  the heredoc prompt in examples/automation/build-pass.sh — the text between
  `cat >"$PROMPT_FILE" <<PROMPT` and the closing `PROMPT` line — contains no
  instruction to Write `$REPORT`; (2) the executable (non-comment) lines capture
  the output of `claude -p "$(cat "$PROMPT_FILE")"` and write it to `$REPORT`
  themselves.
instrument: npx vitest run test/automation/build-pass-report-channel.test.ts
sight: grounded
---
#AssumptionTest #feasibility #build-loop #unvalidated #evidence/assertion

**Lane: compute-only.** A spec over one shell script settles it; nobody outside the building is the measurement.

**What the spec must assert, stated so the next reader does not inherit a blank file.** Following the pattern `test/automation/build-pass-reports.test.ts` already uses (read `build-pass.sh`, strip comment lines, regex the code):

1. Slice the prompt heredoc — from `cat >"$PROMPT_FILE" <<PROMPT` to the `\nPROMPT\n` terminator — and expect it **not** to match an instruction to Write the report path (today that slice tells the model to Write `$REPORT`, and the existing spec's test "the model's own report gets the prefix too — it Writes the file itself" documents that fact in its comment).
2. Expect the executable lines to route `claude -p "$(cat "$PROMPT_FILE")"` output into `$REPORT` (a redirect or a capture-then-`report`), which today they do not.

**Why it is red today, honestly classified.** The spec file does not exist, so today's red is `no-spec` — it would fail identically for any question written on this path and grants no build permit. It becomes a real red the moment the spec above is written: assertion (1) fails against the current prompt text and assertion (2) fails against the current script. A pass on this surface can name the mechanism but cannot leave the spec behind; the deliverable is the failing spec, not this filename.

**What a green does NOT settle.** That the 94 refused turns mattered to anyone (desirability — nobody has said so); that capturing stdout yields a clean report rather than one with tool noise in it (the assumption's own second failure mode, which needs a run of the loop, not a spec); and nothing about the 66 source-file instances of the guard, which this solution does not touch.
