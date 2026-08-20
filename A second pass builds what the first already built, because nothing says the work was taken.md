---
type: Opportunity
source: 'agent-run:autonomous-loop-2026-08-07'
created: '2026-08-07'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[A pass claims the work item before it starts, and the claim outlives the session]]
[[Scan for prior art at the start of a build, not at the push]]
[[Accept the collision and shrink it, by pushing early so rejection arrives in minutes]]
[[A build that is finished and waiting in an open PR is picked as a target again, because selection reads only the tree]]

**The need (operator's voice).** "I paid for eight hours of compute and got a commit I had to delete. Another run had already built the same thing six hours earlier, and nothing told either of them."

**Why this is its own need and not a restatement of its parent.** The parent, "Two agents sharing my vault can trample each other", holds two children and both are about *writes* colliding — a merge conflict committed into a source file, and two runs writing the vault with nothing arbitrating. This is not a write collision. The parent's own body says so, in the section recording the 2026-07-26 sighting: neither pass wrote the vault while building, git would have serialised them cleanly, and no vault lease would have helped. What collided was **the decision about what to work on**. Both passes read one briefing paragraph that names work and has no way to say the work has been taken, and both acted on it.

**What was observed, with times.** A loop iteration cloned the product repo clean at 00:47Z, read the standing briefing, and built the named feature: a migration, a derived experiment arm, a per-arm admin read, 28 new tests, four e2e tests green against real Chromium and real Postgres. It committed at 08:46Z. At 08:47Z the push was rejected — a commit pushed at 02:56Z by a different session was the same feature: same migration number, same column name, same hash function, same default-off knob. One 4-assertion test file was salvageable. Everything else was discarded.

**The part that makes this worth a node of its own.** The only detector in the system is `git push --ff-only`, it fires after all the cost has been paid, and it fired here only because the two implementations happened to touch overlapping files. **Two passes building non-overlapping duplicates of the same intent would both push cleanly and neither would ever know.** The observed cost is therefore a floor, not an estimate — it is what this failure costs when it is caught.

**Litmus — more than one way to address it?** Yes, and the three are genuinely different in kind: claim the work before starting so a second pass sees it is taken; scan for prior art at the start rather than discovering it at the push; or accept that collisions happen and shrink the window so a wasted pass costs minutes instead of hours.

**Why it was invisible until now.** This need has lived as prose inside its parent since 2026-07-26 and has never had a node. The parent reads as fully served — two children, three solutions under each — so every sweep that counts subtrees would mark it done. It surfaced only because a pass went looking for parents carrying needs their children do not hold, which the assumption "Most opportunities the sweep calls underserved are categories whose children are already served" had named as its own biggest unanswered question.

⚠️ Unvalidated. Distilled by an unattended pass from its parent's recorded observation. The rung is `assertion`, not `observed`: the collision itself was observed first-hand by the pass that wasted the work, but this node's source is that node's prose rather than a transcript recording, and the claim that operators other than this one would hit it is grounded in nothing at all — n=1, and the 1 is this building's own loop.

## Corroboration — the finished-but-unmerged variant, seen ten times (unattended sweep, 2026-08-20)

`INBOX:2026-08-20-build-loop-stuck-every-run-records-the-tool-surface-it-actually-had.md`: the build loop selected "Every run records the tool surface it actually had" as a target, and the firing found the work already complete on branch `run-tool-surface` (PR #181 — tsc clean, vitest green, CI green, mergeable, unmerged), built by an earlier firing the same day. It re-verified rather than duplicate it, then could not ship because the re-verification left uncommitted changes and the ship step refuses a dirty tree. The loop filed this as "failed to ship 2 firings in a row" and will keep passing over the target. The report's own words: "this loop can re-fire a cleared node before its prior build has merged."

The same shape recurs across the transcript channel for PR #130: at least nine sessions (`TRANSCRIPT:0095203e-ab42-4179-a53e-a2d4d6dd6032`, `00c3120a-411d-4c42-ba04-aaf9c43aadd7`, `339f1021-5bf7-4779-b9f4-4ad2f911fed0`, `41c3be96-84ed-453c-89c9-d349e7dc5e4b`, `4c23e06e-330b-4e33-80d0-b301e6e05d42`, `5e2d1a9a-df73-4cee-a511-cab7abedccc9`, `a0a90eab-13db-49b5-a7e9-309584d8cb26`, `a6906de8-c76c-4799-8e85-085026f24616`, `c22f7f1d-e799-452a-b1a4-8602163042e8`) each re-selected "Ask the open question first, and offer options only once the frame is agreed", each re-found the open PR, each reported "already built" — one firing spent per rediscovery.

**What this adds to the node.** The originating observation was two concurrent passes building the same thing, with the detector firing at push. Here the first build is *finished* and *visible* as an open PR, and the loop still cannot see that the work was taken, because the only state target selection reads is the tree, and the tree changes only when the PR merges and the instrument goes green. An open PR is a claim on the work that nothing in selection consults. Of the three candidate directions beneath this node, "Scan for prior art at the start of a build" is the one these firings performed by hand — it saved the build but not the firing. Whoever builds any of the three should note that "taken" has to include an unmerged branch or PR naming the target, not only a merge.

**Smaller fact, for a human:** the 2026-08-20 firing was blocked from shipping by changes its *own* re-verification left in the working tree. Nearest existing home is "A run's own leftovers break the next run's setup, so the loop fails before it starts"; recorded here instead because this time the leftovers broke the same run. One instance; no node.

_Sources: the INBOX note (automated; an exit code the loop watched) and nine transcript records (observed behaviour of the product's own agent). Grounds usability and the loop's mechanics, not demand. Rung unchanged._

## Third firing on the same finished PR, and this one reached for the merge itself (unattended sweep, 2026-08-20, later)

`TRANSCRIPT:97af8252-5994-4c67-98fe-5fd6650aaaad` (2026-08-20 18:55Z): a third build firing selected "Every run records the tool surface it actually had", found PR #181 already implemented and green, and — per its own report — "moved its branch into the main checkout and merged origin/main" into it rather than re-verifying and standing down as the second firing had. Three firings on one finished build, each spending its selection on the same target, and the third escalating from re-verify to merge-by-hand is a new fact: when target selection cannot see an open PR as "taken", the firings do not merely repeat, they start to improvise the missing ship step. The session's only friction event was the build loop's usual Write on its own `last-report.txt`, already counted on "The session tries to write a file before it has read it this run…".

_Source: `TRANSCRIPT:97af8252-5994-4c67-98fe-5fd6650aaaad` — observed behaviour of the product's own agent; the report text is the agent's own account, the re-selection is the recorded fact. Grounds the loop's mechanics, not demand. Rung unchanged._
