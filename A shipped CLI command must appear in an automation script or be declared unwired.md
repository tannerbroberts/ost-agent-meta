---
type: Solution
source: >-
  INBOX:friction/2026-08-10-friction-pr-80-shipped-a-pass-claims-the-work-item-before.md
created: '2026-08-10'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** Narrow the claim to the one surface where reachability is cheap to decide. Every subcommand the CLI registers is either named by a script under `examples/automation/`, or listed in an explicit `unwired` allowlist with a one-line reason. A spec walks both lists and fails on any command in neither. Adding a command therefore forces one of two sentences: which loop runs it, or why nothing does.

**Why this shape.** It targets exactly the observed failure. `ost-agent claim` shipped with a green spec and no caller; `build-pass.sh` names eight other subcommands and not that one. This rule would have gone red on the same PR, before the friction filing existed, and it needs no static analysis to do it — the automation scripts are text and the command registry is a list.

**The allowlist is the load-bearing part, not a loophole.** Some commands are genuinely operator-facing and correctly have no script caller: `init`, `set-outcome`, `promote`, `result`, `retract`, `lane --set`. A rule that refused those would be wrong, and a rule with an unexplained escape hatch would be ignored. Making the exemption cost one sentence is what keeps the list readable as a statement about the product rather than as suppression.

**Contrast with siblings.** The caller census reports across the whole exported surface and blocks nothing; this covers only CLI subcommands and blocks. It is the cheaper and more certain of the two and the one that generalises least — nothing it does helps with an unreached MCP tool or an unreached module.

**Where it fails.** It checks that a name appears in a script, which is not the same as that line executing. A subcommand mentioned in a comment, in a dead branch, or behind an env flag nobody sets would pass. It would have caught `claim` because `claim` appears nowhere at all, and it would not catch the next instance if that one is mentioned once and never run.

**Cost.** Very small — one spec and one allowlist file.

⚠️ Unvalidated. Agent-ideated.
