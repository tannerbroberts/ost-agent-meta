---
type: Solution
status: unvalidated
source: 'agent-run:autonomous-loop-2026-07-25-pass6'
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Does a first-run branch actually get a stranger to a working vault]]

**The idea.** Setup is not a wizard the package runs; it is a conversation the session
already knows how to have. The tool layer reports "there is no vault here, and here is
the command", the skill carries a first-run branch, and the operator answers exactly
one question — *what outcome do you want this tree to serve?* — in their own words.
Everything else is scaffolding that needs no model and no key.

**Partially shipped in v0.11.0**, which is why this node exists as a candidate rather
than a wish: the bootstrap signal (`ost_next_work` → `bootstrap: true`) and the skill
branch are live. What is *not* built is the deliberate front door — a `/ost-setup`
command, or an equivalent affordance that a person who has just installed a plugin
would actually find without knowing to ask for an OST.

**How it compares to its siblings.**
- Against [[npm setup wizard that scaffolds the vault first and asks for a key last]]:
  the wizard's premise is that `npm install` does the work. npm postinstall has no
  reliable TTY and is disabled outright in many setups, so the wizard's honest form is
  `npx ost-agent init` anyway. This solution accepts that and moves the guidance into
  the layer that *does* have a conversation.
- Against [[Ship a starter vault whose outcome is a placeholder the human must replace]]: that one buys a literal one-liner by letting a machine write the mandate
  first. This one refuses to, and pays for the refusal with one question.

**The cost, stated plainly.** The founder's launch sentence is *"setup runs itself."*
This solution cannot make that literally true. What it delivers is *"install it, and
it walks you through — it needs one sentence from you."* If that gap is what keeps the
warm prospect from being contacted, this solution has not cleared the bar and the
sibling below is the one to weigh.

**The assumption it rests on:** that a person who installs a plugin will encounter the
first-run branch at all, rather than opening a session, seeing nothing happen, and
closing it. Nothing in the current design makes the branch discoverable to someone who
does not already ask for discovery work.

⚠️ Unvalidated. Proposed by the agent that shipped half of it, which is a reason to
discount its confidence that the shipped half is the useful half.

## What was built, 2026-07-26 (autonomous loop, pass 7) — the other half

`OST-Agent` v0.12.0 (`d3efbbd` on `main`). This node has carried, since it was written,
the sentence that named its own gap: *"What is not built is the deliberate front door — a
`/ost-setup` command, or an equivalent affordance that a person who has just installed a
plugin would actually find without knowing to ask for an OST."* That is now built.

**What `/ost-setup` does.** Calls `ost_next_work`. On `no-vault` it asks the one question
it is not allowed to answer — *what outcome do you want this tree to serve?* — reads the
human's sentence back verbatim, and runs `ost-agent init <folder> --outcome "<their
words>"`. On `no-outcome` it does the same through `set-outcome`. On a folder that is
already a vault it reports the outcome and node counts, points at `/ost-status`, and
**stops**: it does not re-initialise over a live tree or touch an Outcome someone already
chose.

**It is generated, not written.** `scripts/gen-skill.ts` renders it from
`OST_RULESET.firstRun` — the same source `SKILL.md` renders from — and the drift test
fails on either being stale. Two hand-maintained copies of the one branch that must never
invent the outcome would drift, and the drift would be silent. A new ruleset rule states
the point out loud, so it reaches both brains: *reporting first run is not the same as
being findable; if a human seems to be starting from nothing, say `/ost-setup` rather than
waiting to be asked.* Both bootstrap messages now name the command too, so a person who
arrives through the tool layer and one who arrives through the menu land in the same place.

**Its shell allowance is four named commands, not a shell.** `Bash(ost-agent init:*)`,
`Bash(ost-agent set-outcome:*)` and their `npx` forms, with a test asserting the shape of
every grant. A bare `Bash` here would hand a shell to the one product whose promise is
that it holds no tool capable of a destructive action, and that promise is worth more than
the convenience.

351 tests across 53 files, `tsc` clean.

**What this does NOT settle, and it is the whole point of the node.** Whether a person who
installs a plugin encounters the branch *at all* is still the assumption underneath this,
and it is still untested — see [[Does a first-run branch actually get a stranger to a working vault]]. A name in the slash-command menu is a better bet than nothing, and it is
still a bet, made by the party that wants it to work.

**And it is not reachable by the person it was built for.** The plugin's MCP server runs
`npx -y ost-agent@latest mcp`, which resolves to **0.9.0** — three releases behind, and the
version that refuses to start outside a vault. Until someone runs `npm publish`, a stranger
installing this plugin gets the failure v0.11.0 removed and never reaches the door v0.12.0
added.

## Issues
- 2026-08-05 2026-08-05 Left un-instrumented deliberately, and the reason is the node's own text rather than a shortage of ideas. Its only test, "Does a first-run branch actually get a stranger to a working vault", pre-commits a threshold that is irreducibly about a person: a warm participant reaching a committed root Outcome in their own words within 30 minutes, zero questions asked, with any clarifying question counting as a refutation rather than a narrow pass. No exit code observes that. The test also states "Lane: deliberately unset — it needs a real outside person; classifying it is a human's call", so this sweep did not flag it either; saying nothing here means only that no marker was found, never that it is safe to automate. What I did instead was follow the node's closing paragraph, which names a real and currently-true blocker: the plugin's MCP server runs `npx -y ost-agent@latest mcp`, resolving to 0.9.0 — the release that refuses to start outside a vault — so the door v0.12.0 built is not reachable by the person it was built for. That is a mechanical claim and it now has a home: an instrument asserting every registry manifest's documented install command resolves to a version that starts outside a vault is attached to [[Be found through the agent ecosystem's own directories rather than through product channels]], where the install path is the load-bearing claim rather than an aside. Worth a human's attention as sequencing rather than as a defect: the 30-minute stranger test cannot be run at all until the package is published, so the test that would produce this vault's first external-operator evidence of any kind is blocked behind an `npm publish` that no node currently owns. Three passes have now recorded that dependency without anyone clearing it.
