---
type: Opportunity
source: 'TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2'
created: '2026-08-18'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Stop committing the compiled dist file to source control; build it fresh at each firing]]
[[Give dist a git merge driver that rebuilds it instead of diffing it]]
[[Have each firing build and commit dist on its own branch only, never on the shared trunk mid-flight]]

An unattended firing switching branches and auto-merging hit "CONFLICT (content): Merge conflict in dist/ost-agent.mjs" — a compiled artifact, not hand-written source, colliding between two concurrent branches. Nobody is present to resolve a merge conflict on an unattended firing, so the run either stalls or has to work around an artifact conflict it did not cause and cannot meaningfully "resolve" by editing by hand.

Observed in TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2.

## Issues
- 2026-08-17 shared-extent flag vs "The session tries to write a file before it has read it this run, and the guard fails the turn instead of reading first" adjudicated by Torres's interventional test: DISTINCT, keep as siblings, do not merge. Both cite TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2 only because one session hit both frictions. Removing the dist/ file from version control (or a merge driver for it) does nothing about write-before-read ordering, and an auto-read-before-write fix does nothing about a merge conflict on a compiled artifact. Shared provenance, separate needs.

## A related but distinct git-collision shape, observed once (unattended sweep, 2026-08-18)

`TRANSCRIPT:fb366858-3f64-4cc1-ad74-6e00d208d697` shows a different concurrent-firing git collision in the same family: `git checkout -b rename-topology-detect` failed with exit 128, "a branch named 'rename-topology-detect' already exists" — a leftover branch from a prior firing colliding with a new one attempting the same name, plus a separate "ambiguous argument" error resolving a ref. Not the same mechanism as this node's dist merge conflict (that is a content collision on a shared trunk merge; this is a naming collision on branch creation), and it is a single instance rather than an established pattern, so no new node was created. Flagged here as the nearest existing home rather than left uncited, since both describe concurrent unattended firings stepping on each other's git state.
