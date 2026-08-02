---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-22-agent-as-driver.md'
created: '2026-07-25'
evidence: assertion
---
#Opportunity #ported-from-ost-agent-vault #evidence/assertion
[[Ambient session agent drives the append-only tools]]
[[Bundled local model for zero-credential trial]]
[[Optional bring-your-own-key, off by default]]
[[The credential I am already authenticated with can't be used by the tool asking for one]]

**Customer need (operator's perspective):** "I don't want to provision, pay for, and manage a second API credential just to try or run this tool. The friction and cost of a separate AI key puts me off before I've even started."

The pain is adoption friction and duplicated cost: the operator often already has an intelligent agent running in their session, and being asked to buy/manage another credential to unlock the same reasoning is a barrier to trying and to running consistently.

**Litmus (more than one way to address?):** Yes — the underlying need (get value without a second credential) could be met by letting the ambient agent drive, bundling access, a free tier, BYO-key optional, etc. Not a single-solution disguise.

_Provenance: INBOX:2026-07-22-agent-as-driver.md (design review conversation, 2026-07-22). The evidence names one solution (ambient agent as driver); reframed here to the underlying need. Distilled by autonomous OST pass; unvalidated — for human review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Issues
- 2026-07-25 Design decision (ambient-agent driver) reverse-engineered into a need — the node's own body concedes the evidence names one solution. Sequenced-after-demand (2026-07-24 review).

## Supporting evidence — observed live (2026-07-25)

`INBOX:2026-07-25-friction-run-p2-p5-requires-an-api-credential-even-when-a.md`: an authenticated ambient Claude Code session attempted `run P2_map` on this vault and hit the SDK credential wall (no key, no ant CLI, empty keychain) — while itself being a fully authenticated agent. The pass was completed via the ambient tool-surface path instead, which is this opportunity's thesis working as designed. First observed-rung instance under this node; the need itself remains founder-stated.

## Evidence (mapped 2026-07-25)

`INBOX:2026-07-25-friction-run-p2-p5-requires-an-api-credential-even-when-a.md` — direct live instance: `run P2-P5` demanded an ANTHROPIC_API_KEY while an authenticated Claude Code session was RIGHT THERE driving it; the driver had to fall back to the ambient tool-surface path. The product's own runner reproduces the second-credential wall this need describes.

## Founder confirmation (2026-07-25, human:conversation)

The founder restated this need unprompted while describing the setup vision: "If a user doesn't have an API key, because they prefer to use something like a Claude Code subscription plan, then I'd also like to be able to easily drop in to serve them as well." Two implications for this node: (1) the no-key path is now an explicit requirement of the planned npm setup wizard (see 'npm setup wizard that scaffolds the vault first and asks for a key last'), not just an adoption nicety; (2) subscription-plan users are named as a concrete persona for this need. Rung unchanged — still founder-stated (assertion), but the need has been independently re-stated twice from inside the building.

## The wall now names this path instead of hiding it — 2026-07-25 (pass 6)

v0.11.0 (`86b6ff4`): the credential failure this node's evidence recorded no longer
reports the SDK's *"Could not resolve authentication method"*. It reports the variable
to set **and** this node's own answer — that the MCP server holds no model and needs
no key, reachable in two lines via the Claude Code plugin — plus the commands that
already work without a credential.

**Why this matters more than a better error message.** The old wall did not merely
fail to help. It stated, in effect, that a credential was required, which is false
for this product and had been false since the MCP surface existed. A
subscription-plan user who hit it learned the opposite of the truth and had no reason
to look further. The observed instance under this node — an authenticated Claude Code
session hitting the wall *while itself being the credential* — is exactly the person
the old message misinformed.

Rung unchanged: still `assertion`. Nobody outside this building has hit either
message. What changed is that the product now argues for its own no-key path at the
moment someone is deciding whether to give up.
