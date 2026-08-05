---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** The channel, not the content.

**The assumption under test.** That `npm postinstall` is a viable wizard channel at all. The node names this itself as the assumption still worth testing and records the current answer as *no* — but is equally explicit that the answer "was gathered from the npm ecosystem's own conventions rather than from a user." That is a reasoned belief about a mechanical fact, and mechanical facts are cheap to measure. Measuring it either retires the founder's original vision honestly or revives it.

**Why it still matters after the redesign.** The shipped form is `npx ost-agent init` plus a session that knows to run it, and the promise one PM gives another was specifically *"just run npm install ost-agent, it'll set everything up for you."* If postinstall genuinely cannot speak on most machines, that promise can never be kept and should stop being quoted as the target experience. If it can speak on most machines, the redesign gave up something real and the trade deserves re-examination.

**The test (ten environments, an afternoon, no product change).** Publish a throwaway package whose `postinstall` does one thing: record whether it ran, whether `process.stdout.isTTY` was true, and whether stdin was readable. Install it on ten stock setups spanning the realistic spread — macOS and Linux; npm, pnpm and yarn; a plain terminal, a CI runner, a Docker build, and at least one setup with `ignore-scripts=true` set (which is the default in some corporate configs and in pnpm for dependencies). Record three outcomes per environment: **script ran with a usable TTY**, **script ran with no TTY**, **script never ran**.

**Pre-committed threshold.** **7 of 10 or more reach "ran with a usable TTY"** and the postinstall wizard is viable, the current design position is overturned, and the founder's original one-liner becomes reachable. **Fewer than 7** and the design position is confirmed by measurement rather than by convention: the node's Issues section should record it, the `npx ost-agent init` form becomes the settled answer, and the PM-to-PM promise gets rewritten to match what actually works.

**Explicitly out of scope.** Whether a stranger gets to a working vault — that is "Does a first-run branch actually get a stranger to a working vault", it needs a person, and it stays blocked on the release credential. This test asks only whether the channel can carry a wizard, and needs no stranger at all.

**Who runs it.** A human, or an attended session with publish rights. Note the dependency the node already carries: publishing anything is blocked on "Every run ends blocked on a credential only I hold".
