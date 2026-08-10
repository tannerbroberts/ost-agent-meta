---
type: Assumption
source: >-
  INBOX:friction/2026-08-10-friction-pr-80-shipped-a-pass-claims-the-work-item-before.md
created: '2026-08-10'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it can be false.** A census built from static reads of this repository classifies entry points accurately enough that its output is worth an operator's attention — specifically, it names `claim` and does not name the eight subcommands `build-pass.sh` actually shells out to.

It could easily be false. The callers in this repository are heterogeneous: `build-pass.sh` reaches the CLI through `node "$CLI" <subcommand>` string interpolation, the MCP tools are registered into a table by name, and the skill file names tools in prose. A walk that only reads TypeScript imports sees none of those and would report the entire CLI as unreached — a census with a 100% false-positive rate, which is not a weaker version of the useful thing, it is noise.

**Category:** feasibility.

**Why it is the riskiest belief under this solution.** The solution's value proposition is that a number exists to read. If the number is wrong in the direction of accusing live code, nobody reads the second report, and the census has cost a module and bought nothing. Whether unreached code is *common* is the interesting question, and this belief is upstream of even being able to ask it.
