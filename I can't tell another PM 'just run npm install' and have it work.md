---
type: Opportunity
status: unvalidated
source: 'human:conversation:2026-07-25'
created: '2026-07-25'
evidence: assertion
---
#Opportunity #evidence/assertion
[[npm setup wizard that scaffolds the vault first and asks for a key last]]

**The need (prospective user's voice, founder-stated):** "I heard about this from another PM. I don't want to read docs, clone repos, or wire up an agent — I want to run one command and have the thing set itself up. If setup takes more than 'Do you have npm? Just run npm install ost-agent', I'm out."

**Reframed from:** the founder's input was solution-shaped (an npm package whose install runs a setup wizard). The underlying need is a hand-off-able, brain-dead setup path: the product must be recommendable in one sentence, with everything after that sentence handled by the product itself.

**Founder constraints attached to this need (design intent, not evidence):**
- The OST-Agent software should be totally isolated from development work — setting it up must not entangle with the user's dev environment or repo.
- Vault scaffolding needs no AI at all; intelligence enters only after setup.
- A credential is asked for during the setup phase, not before — and no-API-key users (see 'Don't want to buy a second AI credential just to try it') must have a drop-in path.

**Contrast with neighbors:** 'No one outside my own network could discover this product exists' is about DISCOVERY — hearing the name at all. This node is about the minute after discovery: the distance from hearing the name to a working vault. 'Don't want to buy a second AI credential just to try it' is the credential slice of that distance; this node is the whole distance.

**Rung honesty:** founder theory about what prospective users need — assertion. No outside PM has actually been handed the one-liner yet; that hand-off is this node's natural first test.

**Litmus (more than one way?):** yes — npm postinstall wizard, an npx one-shot command, a hosted "create your vault" web flow, a Claude Code plugin that scaffolds on first run.
