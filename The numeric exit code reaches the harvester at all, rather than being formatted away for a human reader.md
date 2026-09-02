---
type: Assumption
source: 'agent-ideation:2026-09-02-unattended-sweep'
created: '2026-09-02'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[A friction event from a Bash result carries the exit code as a number and names the tool that returned it]]

**Category: feasibility.**

The belief, stated so it could be false: the exit code an adopted contract is looked up by can be recovered from what the adapter actually receives.

**Why it could be false, concretely, and it is closer to false than the other two assumptions on this branch.** `FrictionEvent` has no exit-code field, `resultText()` returns a flat string, and nothing in `extractFriction` parses a number out of it. The code appears only as the prose `Exit code 1` at the head of a body the host formatted for a person to read — an incidental rendering, not an interface. Three ways that breaks the candidate above: the host stops printing the line, or prints it differently for a different tool; a command that was piped or chained reports the exit of the last stage while the contract being looked up belongs to the first; or the invoked tool cannot be identified from the recorded command string well enough to select a row in the table at all, which is a second parse of prose stacked on the first.

**What this assumption is really testing, said plainly.** Whether adopting somebody else's contract is cheap. Its whole appeal over the two siblings is that the discrimination is bought rather than built — but if the input the contract needs must itself be reconstructed by a home-grown parser over human-readable text, most of the cost comes back, and the candidate's advantage is smaller than its own body claims.
