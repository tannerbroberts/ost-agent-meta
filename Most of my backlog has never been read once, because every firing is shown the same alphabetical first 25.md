---
type: Opportunity
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
authorship: machine
---
#Opportunity #unvalidated #evidence/assertion
[[An operator-set evidence window in ost.config.yaml, amended by hand like discovery.target]]
[[Order every capped list by least-recently-shown, so the window advances each firing on its own]]
[[Adopt cursor pagination as it already exists, and build only the store that remembers the cursor]]

**The need, in the operator's voice.** "When I pay for a firing, I want it to look at part of my backlog I haven't paid to look at before. If every pass reads the same twenty-five items, the other four hundred are not a backlog — they are a place things go."

## The mechanism, measured off this pass's own `ost_next_work` response

Four of this sweep's lists arrived capped at 25, and every one of them is sorted ascending and truncated at the head. Nothing rotates.

- `unmappedEvidence` — 25 of 419 shown, 394 hidden. The ids run `0095203e`, `00c3120a`, `01e55025`, `022e473f`, `024ceca3`, `030e5db3` … `1515b876`: ascending hex, cut at 25. Nothing beyond `15…` is visible to any firing.
- `solutionsMissingInstruments` — 25 of 63 shown, 38 hidden. The titles run "A background task's own output directory…", "A highlight criteria note…", "A human-edited manifest…", "Append-only…", "Auto-read…", "Axioms elicited…", "Borrow…", "Charge for…" … "Short-lived scoped tokens…": strictly ascending alphabetical, cut at 25. Every entry sorting after "Short-lived…" — the whole S-tail plus T, U, V, W — is invisible.
- `assumptionWork.needsHumans` — 25 of 457 shown, 432 hidden. Same ordering.
- `outstandingAsks` — 25 of 51 shown, 26 hidden. Same ordering.

**Why the window is frozen rather than merely capped.** A cap over a draining queue is harmless: work leaves, the window advances, everything is eventually seen. These queues do not drain. The sibling needs under this same parent establish why — settled work has no way to say it is settled, evidence corroborating an existing opportunity has no way to be marked handled, and a correctly-declined instrument is indistinguishable from an unexamined one. So the head of each list is made of exactly the items that cannot leave, and the cap pins the firing's attention to them permanently.

**The compounding step, and it is the part worth acting on.** Because the window never moves, *every census ever taken of these buckets sampled the same head*. The 2026-08-26 firing read 10 of the 25 shown solutions, found 10 of 10 to be correct declines, and recorded the bucket's yield of real work as zero — a sound reading of what it could see. This firing independently re-read 6 of those same 10 and reached the same verdict, which is the treadmill rather than a replication. Neither firing could reach the 38 entries later in the alphabet, and no firing ever has. The conclusion "this bucket contains no real work" rests on a sample that cannot touch 60% of it, and the same holds for the 94% of evidence and the 95% of human-lane tests no pass has been shown.

**What the surface does and does not claim.** The cap is deliberate and honestly reported: `Truncation` in `src/mcp/next-work.ts` carries `shown`/`total`/`hidden` precisely so "a capped list that reported only what it showed would read as the whole truth — which turns a display limit into an amnesty." That design goal is met; the totals do travel with the sample. What is undocumented anywhere in that module is *which* members the sample is drawn from, and the observed answer is "the same ones, forever." The honesty fix landed on the denominator and not on the selection.

**Litmus — is there more than one way to address it?** Yes, and they disagree about who pays for the coverage: rotate the window by firing so the tail surfaces on a later pass; sort by least-recently-examined instead of by title; drop from the list anything a pass has already dispositioned, so the window advances as a side effect of honest work; sample the window at random; or report the hidden tail's identity cheaply (titles only, no detail) so a pass can at least name what it cannot see. Passes.

**Distinct from its siblings under this parent.** The siblings are about *settled* work reappearing — "Work a previous pass settled comes back on the next list, so I pay to re-decide it", "Work my own governance has already gated still shows as outstanding every pass", "Work I already finished keeps coming back in the queue, so the pass can never say it is done". This is the reverse face: *unexamined* work never appearing at all. Torres's test both ways — rotating the window surfaces the tail but does nothing about settled items recurring within it, and a disposition state stops recurrence but, on a 419-item queue, still leaves 394 items no firing is shown. Two solutions, each serving one and not the other, so these are separate needs.

**Provenance and its limits.** First-party observation of this product's own tool output on 2026-08-27, plus reads of `src/mcp/next-work.ts` and the `test/mcp/` listing via `ost_read_repo`. The ordering claim is read off one response; it is consistent with the 2026-08-26 firing's reported list but has not been confirmed against the selection code itself, which sits past the point where the file read truncated. Nothing was executed and no result is recorded. Floor rung, and this is the agent reporting a defect in the surface that grades it — checkable by anyone re-running the sweep and reading the first characters of each capped list, and it should be checked rather than taken.

## First reads from the hidden tail — the window is frozen, but this slice of what it hides is not different (unattended firing, 2026-08-28)

This node's sharpest claim is epistemic rather than mechanical: every "this bucket holds no real work" verdict was taken over a head the cap pins in place, so it "rests on a sample that cannot touch 60% of it, and the same holds for the 94% of evidence … no pass has been shown." That gap was stated and left open. This firing put three records into it.

**How the tail was reached, since the sweep cannot hand it over.** `ost_next_work` serves ids only for what it shows, so the tail is unaddressable through the sweep alone. But an evidence id is recoverable from the vault's own filenames, and the body is then servable through the blessed channel: `Glob` over `.ost-agent/evidence/TRANSCRIPT_f*.md` returned 23 filenames, and `ost_next_work({evidence: …})` read three of them in full. The `.ost-agent/` sidecar is refused to `ost_read_repo` on purpose — evidence bodies come from one channel — and that boundary is intact here: only filenames came off disk, every body came through the sweep's own reader. **Worth recording as a technique**, because it means the tail is reachable today by any pass willing to spend two calls, without waiting for the rotation this node proposes.

**What was in them.** `f48dc76d` (2026-07-31): a Bash call killed at exit 143 after a two-minute timeout, five polling attempts still pending. `fe671285` (2026-08-06): a module-not-found against `/private/tmp/src/adapters/transcript.js`, then four consecutive `File has not been read yet` refusals. `f9f63ce3` (2026-08-12): the same read-first refusal three more times, a `ScheduleWakeup` rejected for a missing required `prompt`, and a `Monitor` call refused because "this tool's schema was not sent to the API — it was not in the discovered-tool set derived from message history."

**The finding, and it cuts against this node's own worry.** Every one of those needs is already on the tree, most of them several times over: the read-first precondition, module paths composed against a layout nobody checked, a tool refusing a call for a schema the session never held. Three records spanning six weeks and drawn from a region no firing has ever been shown produced **no need that is not already mapped**. So for the evidence bucket specifically, the frozen window is costing far less than its 94%-unseen figure suggests — the hidden records are not different in kind from the visible ones, because the channel filling them is the same loop recording the same frictions.

**What this does not license, stated because the temptation is obvious.** Three of roughly four hundred is a thin sample, chosen by one letter of hex rather than at random, and the fact that its members agree with each other and with the head is weak evidence that all of them do — a homogeneous corpus and an unrepresentative sample look identical at n=3. It says nothing at all about the other three capped lists: `solutionsMissingInstruments`, `assumptionWork.needsHumans` and `outstandingAsks` are populated by different mechanisms, and the 38 solutions after "Short-lived scoped tokens…" remain entirely unexamined by anyone. The narrow claim is that the evidence tail is probably more of the same; the general claim, that the frozen window is cheap, is exactly what has not been shown.

**Consequence for the fix, and it changes the ranking.** If the tail is homogeneous, then rotating the evidence window is worth less than the sibling remedies under this parent — a pass that sees 25 fresh restatements of mapped needs is no better off than one that sees the same 25. The higher-value target is the other three lists, where the hidden entries are individually distinct artefacts rather than repeated recordings of one loop. A human ranking the three candidate solutions here should weigh that: least-recently-shown ordering buys most on `solutionsMissingInstruments`, and close to nothing on `unmappedEvidence`.

_First-party to this firing, 2026-08-28: three evidence bodies read through `ost_next_work({evidence: …})`, filenames enumerated with `Glob` over the vault. Observed behaviour of the agent's own sessions; grounds usability, not demand. Nothing was executed, no result is recorded, and this node's rung is unchanged._
