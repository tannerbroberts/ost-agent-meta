---
type: Opportunity
status: unvalidated
source: 'TRANSCRIPT:005ca37f-b0fc-4ddf-b8b6-971bc90384e1'
created: '2026-08-22'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Run every unattended firing with no controlling terminal, so prompting tools take their non-interactive branch]]
[[A prompt-answer policy the operator writes, and a shim that answers from it while the run is away]]
[[Adopt each tool's own documented non-interactive flag, and refuse an automation command that omits it]]

**The need (customer's voice):** "When I am not at the keyboard, a step that pauses to ask me something is a step that silently does nothing. I need the run to either not be asked, or to answer for itself under a rule I set beforehand — not to stall on a question I will read hours later."

**Why it matters:** An interactive prompt is the one failure that does not look like a failure. The command exits, the transcript records a non-zero code with a fragment of a question in it, and the work it was supposed to do simply never happened. Unlike a crash there is no stack trace and unlike a denial there is no permission to grant — the run was asked for consent and the absence of a person was read as "no".

**Observed instance:** session `005ca37f-b0fc-4ddf-b8b6-971bc90384e1`, an unattended firing with nobody watching, recorded `Exit code 1 overwrite src/cli/index.ts? (y/n [n]) not overwritten`. A copy silently defaulted to no. The run continued as though the file had been written.

**Litmus test:** More than one way to address it — pass non-interactive flags at every call site, run the whole firing with no TTY so prompting tools take their non-interactive path, wrap the tools that prompt in a shim that answers from a stated default, detect the prompt pattern in the output and surface it as a distinct failure class rather than a generic exit 1. Passes.

**What separates it from its siblings:** "The unattended run is scoped for tools nobody granted it" is about a *permission* nobody granted — the fix is a grant, and the denial is legible as a denial. This one is about a *question* nobody answered — there is no grant to give, the tool was working exactly as designed, and the failure is indistinguishable from ordinary command failure. A shim that answers prompts from a stated default addresses this and does nothing for the permission need; a broader tool grant addresses that and does nothing for this.

**Provenance caveat:** Grounded in the agent's own recorded session, so it evidences usability of this runtime — not that anybody outside the building wants it fixed.
