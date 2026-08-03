---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-25-friction-run-p2-p5-requires-an-api-credential-even-when-a.md'
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Ask the host for the credential it already holds, instead of asking the operator for a second one]]
[[Detect the authentication that already exists and say exactly which one will be used]]

The blocking case is narrower than not wanting to buy a key: an authenticated agent session was driving the run, with a live model connection right there, and the path still refused to start because it looked for a separate API credential and found none — no environment variable, no CLI, an empty keychain entry.

The work was possible the whole time; it was reachable only by routing around the intended path through the ambient tool surface. So the cost is not the price of a key, it is that the obvious way in is closed to the person who already has everything they need, and the way that works is not the documented one.

**The need:** I want the run to use the authentication I am already holding, instead of asking me to acquire a second one to do what this session can already do.

More than one way to address this: inherit the host session's authentication, delegate model calls back to the driving agent, detect the ambient path and prefer it automatically, or fail with a message that names the ambient route rather than the missing variable.

## Provenance

Distilled from `INBOX:2026-07-25-friction-run-p2-p5-requires-an-api-credential-even-when-a.md` — filed by the twenty-passes ambient driver after the SDK could not resolve an authentication method while an authenticated session was active.

## History
- 2026-08-02 evidence: stated → assertion — Demoted from 'stated' for consistency: rests on an inbox friction note, and the inbox channel's earned ceiling is 'assertion'.

## Issues
- 2026-08-02 Two conflicts, both flagged by the pass that created it, 2026-08-02. First, the Outcome's ledger for the twenty-passes run (2026-07-25) records this exact source as "MAPPED: appended as first observed instance under 'Don't want to buy a second AI credential just to try it'" — which is this node's parent, so the evidence is already represented there. Second and more important, that parent row is placed in the sequenced-after-demand group by the human-authorized prioritization of 2026-07-24, with the instruction to hold until external returning operators exceed zero. Adding structure beneath a held row is work the human sequenced away from, and this pass did it without seeing the sequence. Recommend archiving unless the demand gate has since opened.
- 2026-08-03 2026-08-03, unattended sweep — declined to ideate here, deliberately, honouring the hold rather than the counter. `ost_next_work` reports this row as under-served (0 of 3 solutions). It is not ideated because the note above is correct and the gate it names is still shut: this node's parent, "Don't want to buy a second AI credential just to try it", is placed in the sequenced-after-demand group by the human-authorized prioritization of 2026-07-24 recorded on the root Outcome, with the instruction to hold until external returning operators exceed zero. Nothing in this pass's evidence shows that condition met — the twenty-two transcripts and three usage traces read this pass are all the agent's own dogfooding, which by their own stated evidence class grounds usability and never demand. Adding three solutions beneath a held row would spend the pass's ideation on structure the human sequenced away from, and would do it invisibly, since the under-served counter cannot see a gate. The prior recommendation stands unchanged and is not this pass's to execute: archive unless the demand gate has since opened, or fold into the parent. A human should also note that this row will keep being reported outstanding on every future pass until the gated rows carry a status the sweep honours — that is the standing decision already recorded three times at the root, and this annotation is a fourth instance of the same cost.
