---
type: Solution
source: 'TRANSCRIPT:081b644b-e90a-472e-9b3d-15562a030a94'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** The operator names surfaces in `ost.config.yaml` — `unattended`, `attended`, `ci` — and each pins the tool set that surface is meant to have. A pass runs under exactly one named profile, and the profile is the contract, so what the agent may do stops depending on which client happened to launch it.

**Why this shape.** The tree already relies on surfaces differing deliberately: outward sensing is on the attended path and off the unattended one, and that is a design decision, not an accident. What is missing is anywhere that decision is written down. Today it lives in prose in a prompt, which is why the unattended sweep of 2026-08-06 was told to flag human-required tests as a legitimate outcome and then found the flagging tool absent — the instructions and the grants were authored in different places and disagreed.

**How it differs from its siblings.** The only one that treats surface variation as intended and configurable rather than as a fault to detect. A preflight check ("A pass declares the tools it needs before it starts") asks whether the tools are there; this says which ones ought to be, and gives the preflight check something to check against.

**Where it fails.** It is a second place for the truth to live. If the profile says a surface has a tool and the host does not grant it, the config is now confidently wrong, which is worse than silent — and nothing here reconciles the two without the preflight sibling.

⚠️ Unvalidated. Agent-ideated.
