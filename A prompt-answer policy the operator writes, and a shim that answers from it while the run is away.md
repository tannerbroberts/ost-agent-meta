---
type: Solution
status: unvalidated
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A prompt the policy does not cover stops the run and is recorded, rather than being guessed]]

**Variation dimension: automated vs manual — the answering is automated, the policy stays deliberately manual.** The operator writes, once and by hand, which questions a firing may answer for itself and what the answer is: overwrite an existing file, yes; delete anything, never, fail the run instead; push to a remote, never. A shim wraps the prompting call, matches the question against that policy, and supplies the answer. A question the policy does not cover is not guessed — the run stops and records the exact prompt text for the operator, joining the same `outstandingAsks` queue every other human question sits on.

**Why this shape.** It is the only candidate that lets the run get the work *done* rather than merely fail legibly. The sibling that removes the TTY converts a silent no into a loud no; this one turns it into the yes the operator would have given, which is what the founding evidence actually needed — the file was supposed to be overwritten. It also keeps the consent where the product already keeps consent: a human states a standing rule in advance, and compute acts inside it. That is the same shape as the lane labels and `ost-agent promote`.

**What it gives up.** It is a list, and lists go stale — a prompt phrased differently next release falls through to the stop path, so the maintenance cost is real and recurring. More seriously, it is the candidate that hands an unattended run a standing yes, which is a widening of what compute may do without a person, and that is a trust decision rather than a convenience one. The sibling candidates deliberately do not ask for it.

**Cost.** A policy file format, a matcher, a shim on the invocation path, and a new failure class for uncovered prompts. The largest of the three.

⚠️ Unvalidated. Agent-ideated from one recorded session (`005ca37f`, `overwrite src/cli/index.ts? (y/n [n]) not overwritten`).
