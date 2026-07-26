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
- Against [[Ship a starter vault whose outcome is a placeholder the human must
  replace]]: that one buys a literal one-liner by letting a machine write the mandate
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
