---
type: Solution
status: unvalidated
source: 'human:conversation:2026-07-25'
created: '2026-07-25'
evidence: assertion
---
#Solution #evidence/assertion
[[A postinstall step gets to run and speak on a stock setup]]

**Founder's vision (verbatim intent):** the npm package scaffolds the OST vault itself — no AI needed for that — then, during the setup phase and only then, asks for an API key. The new-user experience: get the package name, `npm install`, experience the setup wizard. The promise one PM gives another: "Do you have npm? Just run npm install ost-agent, it'll set everything up for you, ask you for an API key, etc."

**Design constraints (founder, 2026-07-25):**
- OST-Agent software totally isolated from development work — the install must not touch or depend on the user's dev setup.
- A human's interaction with the OST is through an AI agent; the wizard is the one deliberate exception, because it runs before any intelligence is configured.
- If the user has no API key (e.g. they're on a Claude Code subscription plan), the wizard must offer a drop-in path rather than dead-ending — see 'Don't want to buy a second AI credential just to try it' and its 'Ambient session agent drives the append-only tools' solution.

**Key assumptions to surface:** npm postinstall scripts are a viable/trusted wizard channel (many setups disable them — an `npx ost-agent init` style entry may be the honest variant); scaffolding truly needs zero AI; the API-key step is where drop-off concentrates.

## Partially realised, and the part left out was left out on purpose — 2026-07-25 (pass 6)

v0.11.0 implements the *shape* of this solution's second half without the wizard
itself. The credential step now behaves the way this node asks — it names the no-key
drop-in path (the Claude Code plugin, whose MCP server holds no model) rather than
dead-ending, so a subscription-plan user is offered a route instead of a wall. See
[[Don't want to buy a second AI credential just to try it]].

The scaffolding half is *guided* rather than *automated*: the tools now report
`bootstrap: true` with the exact command, and the skill instructs the session to ask
the human for their outcome and run `init` with their words.

**Why the wizard was not built, stated as a design position rather than a backlog
item.** This node's own premise — "vault scaffolding needs no AI at all" — is true of
everything except the Outcome, and the Outcome is not optional. A wizard that prompts
for it on a TTY is fine and `init` already does that; a *postinstall* wizard cannot,
because npm postinstall has no reliable TTY and many setups disable scripts outright.
So the honest form of this solution is `npx ost-agent init` (already the entry point)
plus a session that knows to run it — which is what shipped — rather than
`npm install` doing it silently.

The assumption this node named first is therefore the one still worth testing: **is
npm postinstall a viable wizard channel at all?** The evidence so far says no, and it
was gathered from the npm ecosystem's own conventions rather than from a user.

⚠️ Still unvalidated. No outside operator has run any of this.

## History
- 2026-08-05 unlinked [[Install the package on ten stock setups and see whether postinstall ever gets to speak]] — moved under [[A postinstall step gets to run and speak on a stock setup]] — the belief this test measures now has a node of its own
