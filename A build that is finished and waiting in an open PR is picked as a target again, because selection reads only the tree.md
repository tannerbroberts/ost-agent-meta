---
type: Opportunity
source: >-
  INBOX:2026-08-20-build-loop-stuck-every-run-records-the-tool-surface-it-actually-had.md
created: '2026-08-20'
evidence: assertion
authorship: machine
---
#Opportunity #unvalidated #evidence/assertion
[[Target selection skips any solution that an open branch or PR on the product repo already names]]
[[The ship step merges its own green, mergeable PR instead of leaving it for a human]]
[[A work claim released by the merge, not by the clock]]

**The need (operator's voice):** "The work is done. It is sitting in a green, mergeable PR. And the loop keeps spending firings re-discovering that, because the only thing it reads before choosing a target is the tree, and the tree does not change until the PR merges."

**Why this is a child of its parent and not the parent restated.** The parent's originating observation is two *concurrent* passes building the same thing, with `git push --ff-only` as the only detector, firing after the cost was paid. Here nothing is concurrent: the first build is finished, visible, and named by a branch (`run-tool-surface`, PR #181), and a firing hours or days later still selects the same solution. Torres's test separates them — "release a work claim on merge rather than on a clock" or "skip any target an open PR names" addresses this case and does nothing for two passes starting inside the same hour; "push early so rejection arrives in minutes" shrinks the parent's window and does nothing here, because there is no rejection to arrive (the second firing builds nothing and the PR is untouched). Subset by mechanism, so it hangs beneath.

**What was observed.** `INBOX:2026-08-20-build-loop-stuck-every-run-records-the-tool-surface-it-actually-had.md` (automated build note; an exit code the loop watched): the build loop selected "Every run records the tool surface it actually had", found it already complete on branch `run-tool-surface` (PR #181 — tsc clean, vitest green, CI green, mergeable, unmerged), re-verified rather than duplicated, and then could not ship because the re-verification left the working tree dirty. The loop's own report: "this loop can re-fire a cleared node before its prior build has merged." A third firing the same day (`TRANSCRIPT:97af8252-5994-4c67-98fe-5fd6650aaaad`) selected it again and improvised the missing ship step by hand. The same shape recurs for PR #130 across at least nine transcript sessions, each re-selecting "Ask the open question first, and offer options only once the frame is agreed", each re-finding the open PR, each reporting "already built" — one firing per rediscovery.

**Where the gap is in the code, read this pass via `ost_read_repo`.** `examples/automation/build-pass.sh` chooses its target from `ost-agent buildable` and `ost-agent gate`, both computed over the vault; nothing in the preflight consults the product checkout's branches or the forge's open PRs. `src/loop/claim.ts` does hold a work claim that outlives a session, but it is released by `DEFAULT_CLAIM_TTL_HOURS = 8` and nothing else — a PR that sits unmerged for a day outlives the claim that covered it, and the module's own header says the liveness half is "inherited and not fixed here".

**Litmus test (more than one way?):** Yes — consult branch/PR state at selection time; release claims on merge rather than by clock; let the loop finish the job by merging its own green PR; or shrink the cost of a re-selection to a single `gh pr view` instead of a firing. Distinct mechanisms with different risks. Passes.

**What it costs.** Twelve or more firings across two targets, each a full selection plus a model call, spent confirming that finished work is finished. The rate matters more than the count: with one hourly loop and one finished-but-unmerged PR, every firing until the merge is one of these.

**Provenance and rung.** Source is an automated build note on the inbox channel, which the ladder caps at `assertion` (the tool refused `observed` for it this pass — correctly, since an inbox file is a report of a measurement, not the recording). The transcript records named above are recordings and a human may re-source or promote from them; this node does not claim the rung they would support.

## A third detector, observed 2026-08-28: the collision surfaced as a failed branch create

New evidence captured by this pass's own `ost_ingest_inbox` run, not previously on the tree. `TRANSCRIPT:62625424-f497-4be3-a0c0-7a7b0d3e5cac` (unattended firing, 2026-08-28T07:04Z, 4 friction events) records, as its first event: `tool_error` (Bash), exit code 128, `fatal: a branch named 'wait-primitive-affordance' already exists`.

**Why this is worth a section rather than a tally mark.** Every instance already on this node was detected by a firing *reading* state — the loop found PR #181 already green, or re-found PR #130 open, and reported "already built". Here nothing was read. The firing selected its target, got as far as `git checkout -b`, and learned the work was already claimed only because git refused to make the branch a second time. The branch name is the tell: `wait-primitive-affordance` matches the solution "Monitor accepts a vetted until-loop primitive instead of raw shell polling", which sits in today's `solutionsMissingInstruments` — so the re-selection happened against a target whose prior build never merged, exactly the shape this node describes.

**What it adds to the argument.** The node's litmus test already lists "consult branch/PR state at selection time" as a candidate mechanism. This record is the cheapest possible evidence for that candidate and against the others: the collision was detectable from the product checkout's own local refs, with no forge call, no claim TTL, and no merge. `src/loop/claim.ts`'s 8-hour TTL did not cover it and could not have — the branch outlived the claim. A `git rev-parse --verify` at selection would have cost microseconds and saved the firing.

**What it does not establish.** One record. It does not say how often branch-create collisions happen relative to the PR rediscoveries already counted here, and this pass did not run git or read the product's ref list — the branch's existence is asserted by the recorded exit code, not observed by this pass. It also does not show what the firing did next; the remaining three events in that record are two `File has not been read yet` errors and a retry against `docs/reference/v1-readiness.md`, which belong to a different need.

**Rung unchanged.** The record is a transcript, which is a recording rather than a report, and would support `observed` on a node sourced to it. This node stays at `assertion` because its own source is an inbox build note; a human re-sourcing it to the transcript records named here could raise it.

_First-party to this firing, 2026-08-28: `ost_ingest_inbox` captured the record, and it was read in full via `ost_next_work({evidence})`. Nothing was executed and no result is recorded._
