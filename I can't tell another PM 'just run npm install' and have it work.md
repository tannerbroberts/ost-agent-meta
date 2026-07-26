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

## Supporting evidence — the hand-off this node predicted now has a named participant (2026-07-25, human:conversation)

The founder, same day this node was created: "I actually have lined up another person to try this out, but I won't give the cold-offer a shot unless I can say, 'Just install ost-agent, setup runs itself.'" This node's one-liner is now the explicit launch gate for the first external trial — see the matching annotation on [[Cold-offer test - will outside teams hand over real discovery work]].

## Supporting evidence — fresh-user simulation, observed (2026-07-25 pass, run minutes after v0.9.0 finally reached npm)

An agent session simulated the cold path from an empty directory. What already holds: `npx -y ost-agent@latest` resolves (first time ever — the publish landed today), `init` is a true one-shot with no AI and no key (scaffolds vault + git + outcome node, prompts for the mandate on a TTY), `P1_ingest`/`status`/`check` run fully offline, and the plugin path is live end-to-end (`/plugin marketplace add tannerbroberts/OST-Agent` → `/plugin install` wires skill + commands + MCP; the repo is public; the MCP server needs no API key). What breaks the one-liner, observed:
1. **Nothing runs `init` for you.** After plugin install, a session in an empty folder has the tools and the skill but no vault — the skill and MCP layer contain no first-run/no-vault handling at all (grep confirms zero matches for init/scaffold in the shipped skill). The person must know to run `init` with an outcome. This is the single seam between today and "setup runs itself."
2. **The credential wall fails ugly.** `run P2_map` without a key dies with the raw SDK message "Could not resolve authentication method. Expected either apiKey or authToken…" — not actionable for a PM, and it doesn't mention that the no-key MCP path exists (see [[Don't want to buy a second AI credential just to try it]]).
