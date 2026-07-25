---
type: Solution
status: unvalidated
source: 'human:conversation:2026-07-25'
created: '2026-07-25'
evidence: assertion
---
#Solution #evidence/assertion

**Founder's vision (verbatim intent):** the npm package scaffolds the OST vault itself — no AI needed for that — then, during the setup phase and only then, asks for an API key. The new-user experience: get the package name, `npm install`, experience the setup wizard. The promise one PM gives another: "Do you have npm? Just run npm install ost-agent, it'll set everything up for you, ask you for an API key, etc."

**Design constraints (founder, 2026-07-25):**
- OST-Agent software totally isolated from development work — the install must not touch or depend on the user's dev setup.
- A human's interaction with the OST is through an AI agent; the wizard is the one deliberate exception, because it runs before any intelligence is configured.
- If the user has no API key (e.g. they're on a Claude Code subscription plan), the wizard must offer a drop-in path rather than dead-ending — see 'Don't want to buy a second AI credential just to try it' and its 'Ambient session agent drives the append-only tools' solution.

**Key assumptions to surface:** npm postinstall scripts are a viable/trusted wizard channel (many setups disable them — an `npx ost-agent init` style entry may be the honest variant); scaffolding truly needs zero AI; the API-key step is where drop-off concentrates.
