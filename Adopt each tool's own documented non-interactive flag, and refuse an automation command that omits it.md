---
type: Solution
status: unvalidated
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: bought vs built — the answers are adopted from outside as they are, and only the enforcement is built here.** Every tool that prompts already ships the flag that stops it: `cp -f`, `rm -f`, `git -c advice.*=false`, `npm --yes`, `gh --yes`. Nothing here invents a mechanism or a policy language. What is built is one preflight check over `examples/automation/*.sh`: a command whose executable is on a known-prompting list and which carries none of that tool's documented non-interactive flags is refused before the firing starts, with the flag named in the refusal.

**Why this shape.** It puts the fix where the defect was authored rather than where it fired. The founding evidence is a `cp` in an automation script that nobody wrote `-f` on; the sibling that removes the TTY and the sibling that shims the prompt both let that script stay wrong and catch it at runtime. This one makes it un-writable, and the refusal teaches the flag rather than hiding the need for it. It is also the only candidate whose behaviour is documented by someone other than us — the semantics of `-f` are the vendor's, so there is no second definition of "yes" to keep correct.

**What it gives up.** It only ever covers tools someone put on the list, so it is the narrowest of the three and the one most likely to be silently incomplete — precisely the failure mode the no-TTY sibling avoids by construction. It also cannot help a prompt from a tool the agent invokes ad hoc mid-run rather than from a checked-in script, which is a large share of what an unattended firing actually runs.

**Cost.** A per-tool flag table and a preflight pass over the automation scripts. Smallest of the three to build, largest to keep current.

⚠️ Unvalidated. Agent-ideated from one recorded session (`005ca37f`, `overwrite src/cli/index.ts? (y/n [n]) not overwritten`).
