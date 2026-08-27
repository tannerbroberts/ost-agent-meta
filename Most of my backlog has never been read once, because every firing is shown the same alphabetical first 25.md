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
