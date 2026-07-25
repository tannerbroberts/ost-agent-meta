---
type: Opportunity
status: unvalidated
source: >-
  founder-directive:2026-07-24 — compute-only actionability, stated in session
  as first operator
created: '2026-07-25'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Triage every assumption test by the human-minutes it actually needs, and let compute run the zero-minute lane]]
[[Weekly ten-minute docket - every pending decision arrives prepared as one yes or no]]
[[Scheduled ambient passes that page the operator only at hard gates]]

**The need (operator's voice):** "I'm a working man, husband, and father of three, soon to be four. I prioritize my family, but there's no excuses that build new products. The output from my OST needs to be actionable by me pointing my Claude subscription's token generation power at the problem. I need better bootstrappability from the agent with less involvement from me."

**Why it matters:** This is the first opportunity in this vault sourced from a real operator describing their own binding constraint in actual use. The constraint is structural, not motivational: the current critical path (cold-offer test) budgets ~4 operator-hours; the test backlog assumes a human with afternoons. If solutions are only actionable by a human with hours, this tree steers work that will never happen — for this operator and plausibly for the entire solo-founder segment.

**The honest floor (recorded at birth):** compute cannot absorb four things — the operator's identity in outreach (consent), money, validation authority (the proposer must never dispose), and the goal itself. The need is therefore precisely: human involvement measured in MINUTES at decision-shaped moments, never in hours at work-shaped ones. "Zero" is not on the table; "minutes" is the spec.

**Rung honesty:** assertion — the operator is also the founder, so this is a claim from inside the building. It carries unusual weight anyway: it is a first-person account of a verifiable constraint (time scarcity), not a theory about other people's needs. First non-founder confirmation would come from any outside operator citing the same constraint.

**Litmus (more than one way?):** yes — compute-runnable test triage, prepared decision dockets, exception-paged autonomous loops, delegation protocols are all distinct answers.

## Issues
- 2026-07-25 Cross-branch: this need REFRAMES the cold-offer critical path rather than replacing it — outreach identity/consent stays human, but compute compresses the operator's share from ~4 hours to ~45 minutes (sourcing sweep, all 20 personalization drafts, tracking, reply filing, verdict prep are all compute). Also gates 'Scheduled ambient passes…' behind the exit-0 fix tracked under 'A failed pass reports success, so my automation can't tell'.

## Observed instance — 2026-07-25 autonomous loop, and exactly where it hit the wall

One unattended run took both products from tree to shipped code with **zero operator minutes**: read both vaults, picked each tree's stated next build, wrote tests first, implemented, ran the suites, and pushed. Concretely — `ost-agent` v0.5.0 (the exit-code/status fix) and `tetrix-game-monorepo` `8e6d50c` (the anonymous-funnel instrument that unblocks four assumption tests). This is the strongest observed evidence yet for this need's central claim: compute can absorb the *work* shape.

**Then it hit the honest floor recorded at this node's birth, precisely where predicted.** `npm publish` needs a credential the loop does not have and should not have (`npm whoami` → `ENEEDAUTH`, no `NPM_TOKEN`). RELEASING.md's alternate path — publish a GitHub Release, which fires the publish workflow — was also unavailable, because the environment's git proxy rejected the tag push, so the tag that workflow keys on never reached the remote. **The release commit is on `main`; the package is not on npm.** Filed as `INBOX:2026-07-25-friction-npm-publish-cannot-complete-in-the-unattended-lo.md`.

**Why this sharpens the need rather than just confirming it.** The floor said compute cannot absorb identity, money, validation authority, or the goal. This adds a fifth, and it is not one of those four: **the credential that makes work public.** Publishing is not a decision — nobody is weighing anything, and there is nothing for the operator to judge. It is a one-minute mechanical act that only a credential-holder can perform. The spec "minutes at decision-shaped moments" does not cover it; this is a minute at a *permission*-shaped moment, and a pipeline that hands off decisions cleanly will still stall here.

**What that implies for the candidates below.** [[Weekly ten-minute docket - every pending decision arrives prepared as one yes or no]] is built for decisions and would carry this badly — "run `npm publish`" is not a yes/no with evidence behind it. Either the docket grows a distinct *pending permissions* lane (chores, not judgements), or credential-holding steps are pushed out of the loop's path entirely (an automation token in CI, triggered by something compute can reach). A human should pick; the agent should not quietly acquire publish rights, and did not.
