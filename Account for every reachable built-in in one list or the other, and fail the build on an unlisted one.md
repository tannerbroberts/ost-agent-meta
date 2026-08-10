---
type: Solution
source: 'agent-ideation:2026-08-10-unattended-sweep'
created: '2026-08-10'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** Neither the grant nor the deny list is the proof. The proof is that the two together are *exhaustive*: take the set of built-in tools the host can actually hand this pass, and require every member to appear in `OST_TOOLS` (granted, deliberately) or `DENIED_TOOLS` (refused, deliberately). A built-in in neither list is not a judgement call about whether it is dangerous — it is a capability nobody decided about, and the build fails naming it. That converts "no hijackable capability exists" from a claim about our own code into an accounting identity over the host's surface.

**Why now: this is not hypothetical, it was observed this firing.** `examples/automation/autonomous-pass.sh` denies `Bash,BashOutput,KillShell,Edit,Write,NotebookEdit,Task,Skill,WebFetch,WebSearch` and grants sixteen `ost_*` MCP tools. `Read`, `Glob` and `Grep` appear in neither list, and the 2026-08-10 unattended sweep used all three — it read node files out of the vault directly, globbed the vault root, and grepped the whole vault. Two documents say that should not have been possible:

- `ost.config.yaml`'s `loop:` comment: the firing runs "with only the ost-agent MCP tools granted and every file/shell/network built-in denied." File reads were not denied.
- the script's own comment: "under `-p` a tool outside --allowedTools is denied rather than prompted." Read was outside `--allowedTools` and was not denied; it was path-scoped instead. A read of the *product* directory was refused for want of a path permission, while reads of the vault went through unremarked.

Neither document is lying on purpose. `DENIED_TOOLS` names "every built-in that can write a file, run a command, delegate, or reach the network", and `Read`/`Glob`/`Grep` do none of those, so they fall out of that criterion correctly and out of the accounting silently. That is the shape of the gap: the deny list was written from a *predicate*, and a predicate cannot report the cases it does not cover.

**Why this belongs under this opportunity.** The operator wants proof that no hijackable capability *exists*, not an argument that the ones we thought of are off. `docs/reference/v1-readiness.md` criterion P10 says exactly this is still open — "nothing yet enumerates the whole surface" — and this is the cheapest mechanism that closes it, because the enumeration already half-exists: `test/release/examples-allowlist.test.ts` extracts both lists from the script and pins their membership and disjointness. It checks the two lists against each other. It never asks what is in neither.

**How it compares to its siblings.**
- "Allowlist Tool Runner registers only OST tools" governs what our MCP server registers. It says nothing about the built-ins the host grants alongside it, which is where the three unaccounted tools live — so it would have been green through this whole observation.
- "Published capability manifest with signed build" is an attestation of what we believe we expose; it inherits whatever the belief got wrong. This produces the belief instead of publishing it, and fails when the world adds a capability we have not ruled on. A new Claude Code built-in ships and the build goes red until somebody decides — which is the property the other two lack.

**Where this fails, stated so it can be judged rather than assumed.** It needs a committed list of the host's built-ins to compare against, and that list goes stale the moment the host ships a tool — so the mechanism is only as exhaustive as its own manifest, which is the same class of problem one level up. It also cannot say a granted tool is *safe*, only that somebody decided; and it says nothing about capability reachable through a granted tool's arguments rather than through a tool name. The `Skill`/`SlashCommand` rename recorded in the script is the precedent that argues for it anyway: a deny rule naming a retired tool was inert for four days while the capability it existed to refuse moved to a name nothing denied, and the warning that reported the hole was read as noise about a stale name.

⚠️ Unvalidated. Agent-ideated on the strength of a hole the agent found by using three tools it was not knowingly granted, which is a reason to trust the observation and discount the conviction.
