---
type: Assumption
source: >-
  INBOX:friction/2026-08-10-friction-pr-80-shipped-a-pass-claims-the-work-item-before.md
created: '2026-08-10'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Count how many registered subcommands need an allowlist entry before the list stops meaning anything]]

**The belief, stated so it can be false.** Most registered subcommands are reached by an automation script, and the ones that are not form a short list with an obvious shared reason — they are the human's commands (`init`, `set-outcome`, `promote`, `result`, `retract`, `lane --set`). If that is right, the allowlist is a readable statement about the product's shape and a new entry on it is conspicuous.

It is false if the split runs the other way. If most subcommands have no script caller, the allowlist is most of the CLI, a new line on it means nothing, and the rule degrades into a registration ritual that the next `claim`-shaped command passes by being added to the list without thought.

**Category:** feasibility, with a usability edge — the rule's whole force comes from the exemption being noticeable, which is a property of how long the list is.

**What makes this measurable rather than a matter of taste.** The ratio is a fact about the repository as it stands today. Nobody has counted it: `build-pass.sh` names eight subcommands, `autonomous-pass.sh` names others, and the registry in `src/cli/` names all of them, but the intersection has never been taken.
