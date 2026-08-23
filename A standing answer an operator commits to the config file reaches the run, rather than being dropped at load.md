---
type: Assumption
source: 'REPO:OST-Agent/src/config/schema.ts'
created: '2026-08-23'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Three committed standing answers survive config load and are readable by the run]]

**The belief, stated so it could be false:** when an operator writes a standing answer into `ost.config.yaml` — how to reconcile divergent branches, whether to overwrite on copy, which editor never opens — the config layer carries it to the run. If that is false, the solution above does not merely underperform; it fails silently, which is worse than not shipping it.

**It is false today, read first-party from source this pass.** `ConfigSchema` in `src/config/schema.ts` declares `outcome`, `outcomeTitle`, `remote`, `adapters`, `processes`, `web`, `product`, `discovery`, `evidence` and `loop`. There is no key for any prompt the evidence beneath this branch actually recorded a run stopping on. And the schema's own comment on `ProcessSchema` states the consequence: it "uses Zod's default object behaviour, which strips undeclared keys instead of failing." So an operator who commits `prompts:` or `git: { reconcile: rebase }` gets no error, no warning, and no effect — the key is discarded between the file and the run.

**Why that is the load-bearing half of this solution and not a detail.** The sibling candidates in this set stop the run cleanly when a prompt arrives. This one's whole claim over them is that the run *continues*, because the answer was settled in advance. That claim rests entirely on the answer surviving the trip from file to run, and nothing in the product carries it today. The solution's own prose asserts the opposite in passing — "a divergent-branch reconcile policy and a file-overwrite default are both one-line settings" — which is true of the tools being driven and not of this config.

**What this is not.** It says nothing about whether pre-answering is wise; the solution's own "what would make this the wrong pick" paragraph holds that risk, and it is a person's judgement. This is the feasibility half only: whether there is anywhere to write the answer at all.

_Method: first-party `ost_read_repo` of `src/config/schema.ts`, read to the `defaultConfigYaml` scaffold. Nothing executed. Rung stays at the `assertion` floor._
