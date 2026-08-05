---
type: Opportunity
status: unvalidated
source: 'human:conversation:2026-07-25'
created: '2026-07-25'
evidence: assertion
---
#Opportunity #evidence/assertion
[[npm setup wizard that scaffolds the vault first and asks for a key last]]
[[A first-run branch that walks a stranger to a vault in one question]]
[[Ship a starter vault whose outcome is a placeholder the human must replace]]

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

The founder, same day this node was created: "I actually have lined up another person to try this out, but I won't give the cold-offer a shot unless I can say, 'Just install ost-agent, setup runs itself.'" This node's one-liner is now the explicit launch gate for the first external trial — see the matching annotation on "Cold-offer test - will outside teams hand over real discovery work".

## Supporting evidence — fresh-user simulation, observed (2026-07-25 pass, run minutes after v0.9.0 finally reached npm)

An agent session simulated the cold path from an empty directory. What already holds: `npx -y ost-agent@latest` resolves (first time ever — the publish landed today), `init` is a true one-shot with no AI and no key (scaffolds vault + git + outcome node, prompts for the mandate on a TTY), `P1_ingest`/`status`/`check` run fully offline, and the plugin path is live end-to-end (`/plugin marketplace add tannerbroberts/OST-Agent` → `/plugin install` wires skill + commands + MCP; the repo is public; the MCP server needs no API key). What breaks the one-liner, observed:
1. **Nothing runs `init` for you.** After plugin install, a session in an empty folder has the tools and the skill but no vault — the skill and MCP layer contain no first-run/no-vault handling at all (grep confirms zero matches for init/scaffold in the shipped skill). The person must know to run `init` with an outcome. This is the single seam between today and "setup runs itself."
2. **The credential wall fails ugly.** `run P2_map` without a key dies with the raw SDK message "Could not resolve authentication method. Expected either apiKey or authToken…" — not actionable for a PM, and it doesn't mention that the no-key MCP path exists (see "Don't want to buy a second AI credential just to try it").

## Seam 2 closed, seam 1 half closed — 2026-07-25 (autonomous loop, pass 6)

`OST-Agent` v0.11.0 (`86b6ff4` on `main`) is aimed at exactly the two observations
above, and the honest accounting is that it closes one and halves the other.

**The credential wall (observation 2) is closed.** `run P2_map` without a key no
longer dies with the SDK's *"Could not resolve authentication method. Expected either
apiKey or authToken to be set."* It now names the variable to set **and** the two-line
plugin install that needs no key at all, plus the commands that already work without
one (`init`, `status`, `check`, `debt`, `lanes`, `result`). The second half is the
part that mattered: the old message did not merely fail to help, it implied a
credential was the only way in, which is false — this product's MCP server holds no
model. Only model-driven processes are gated, derived from the process's own tool
allowlist and proved by running every model-free process against a driver that throws
if anyone calls it, so `P1_ingest` and `P5_hygiene` keep working with no credential.

*This vault produced the last instance of the old wall itself*: `ost-agent status`
against `ost-agent-meta` still leads with `⚠ Last run FAILED — P2_map` carrying that
exact SDK sentence, from 2026-07-25T02:00. That journal line is what the fix was
written against.

**"Nothing runs `init` for you" (observation 1) is half closed, and the half that
remains is the half that matters for the launch bar.** `ost-agent mcp` used to
*refuse to start* outside a vault — and the plugin points its server at
`${CLAUDE_PROJECT_DIR}`, so the very first session after `/plugin install` showed a
first-time operator an MCP server that failed to connect: no cause, no fix, the least
actionable signal available. It now starts, serves the identical tool surface, and
`ost_next_work` — where every pass already begins — returns
`{ bootstrap: true, reason, vault, message, nextStep }` instead of an error. The
generated skill carries a matching first-run branch, so the reasoning session knows
to ask the human for the outcome and run `init` with their words.

**What is still true: nothing runs `init` for you.** A session now *tells* you the
command and *asks* you for the one input it needs. It does not scaffold on your
behalf, and this is deliberate rather than unfinished: the input `init` requires is
the Outcome, which is the single human-set mandate the whole tree hangs from. An
agent that scaffolded a vault around a placeholder to keep making progress would have
quietly chosen the thing every node below it ladders up to.

**So: does this clear the founder's launch bar?** *"Just install ost-agent, setup runs
itself"* is not yet literally true and cannot be made literally true without the agent
inventing an outcome. What is now true is: *"install the plugin, and the session will
walk you through setting it up — it needs one sentence from you."* Whether that is
close enough to hand to the warm n=1 prospect is the founder's call, and it is a
smaller call than it was this morning. **No outside PM has been handed either
sentence.** This node's rung is unchanged at `assertion`, and the hand-off it predicts
remains its natural first test.

## Issues
- 2026-07-26 undefined
- 2026-07-26 **Hygiene — a destroyed annotation, flagged not repaired (2026-07-26).** One or more lines in this node read `- <date> undefined`. That is not a note anybody wrote: `ost_annotate` was called with `note` instead of its declared `issue` field, nothing validated the call, and the literal string "undefined" was appended in place of the content. The original text was never written anywhere and is unrecoverable. Fourteen such lines exist across the two live vaults, written by several passes over three days. The cause is closed in ost-agent v0.17.0, which refuses a tool call that does not match the schema the tool itself declares. **Left in place deliberately:** this vault is append-only, and rewriting history to hide a bad write is exactly the action this product refuses — including when the product is the one that made it. Full account: "A tool call I got slightly wrong destroyed the note I was filing".
