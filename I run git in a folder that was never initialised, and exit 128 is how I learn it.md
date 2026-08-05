---
type: Opportunity
source: 'TRANSCRIPT:ac007b7b-ac18-4a19-94f1-cb5f3c93ca42'
created: '2026-08-05'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[One workspace-state probe the run makes before it plans, not one failing command at a time]]
[[The scaffolder writes a manifest of what it did and did not initialise]]

**Customer need (operator's perspective):** "When I start work in a folder, I need to know what that folder already *is* — initialised or not, a repo or a bare directory, tooled or bare — before I run the command that assumes it. Finding out from a `fatal:` is finding out too late."

The pain is distinct from not knowing the *layout*. In every captured instance the files were all present and correctly named: the agent had just listed the directory and could see `index.mjs`, `package.json`, `bin/`, `vaults/`. What was missing was not a path but a **state** — the folder had never been `git init`ed — and nothing in a directory listing distinguishes an initialised repository from a folder that merely looks like a project. So the agent read the layout, concluded the workspace was ready, and learned otherwise from exit code 128.

The same shape covers a missing binary: in one of the captured sessions the very next call after the 128 was `tmux` exiting 127. Both are the same question asked too late — *does this environment actually have the capability I am about to depend on?* — and both are answered only by depending on it and failing.

This matters more for an unattended run than an attended one. A person sees `fatal:` and initialises the repo in a second. A pass that has already committed to a plan built on "this is a repo" has to unwind it, and the recovery is the expensive part.

**Litmus (more than one way to address?):** Yes — a preflight that probes state rather than paths; a scaffolder that leaves a machine-readable manifest of what it initialised; a capability assertion the run declares up front and the runtime answers in one call; recording the state check in the workspace so a later session need not repeat it; making the scaffold step initialise unconditionally so the state is never in question.

_Provenance: TRANSCRIPT:ac007b7b-ac18-4a19-94f1-cb5f3c93ca42 (2026-08-04). Corroborated by three further sessions with the identical exit-128-after-listing shape: TRANSCRIPT:748498c4-31fb-4110-9012-464c441a463f (2026-07-29), TRANSCRIPT:9a406570-323c-453a-b4ca-a29b4aa01f18 (2026-08-04), TRANSCRIPT:35566d8b-a635-49b1-acc8-6bfbeeb134e7 (2026-08-04). Four sessions, three days. Observed behavior — the agent's own mechanically-captured usage; it grounds usability, not desirability, and is not evidence that anyone outside wants this. Unvalidated — for human review._
