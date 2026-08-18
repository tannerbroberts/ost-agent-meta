---
type: Solution
source: 'TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2'
created: '2026-08-18'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A build step is reliably available in the environment that resolves a git merge on an unattended firing]]

Keep dist/ost-agent.mjs checked in, but register a custom git merge driver (via .gitattributes) for that path that runs the build from the merged source instead of attempting a textual three-way merge. A conflict on the compiled output is resolved by regenerating it, never by reconciling two versions of generated code by hand or aborting the firing.

**Compared to the alternatives.** Keeps today's checked-in-artifact model (whatever currently depends on dist/ being present in a plain checkout keeps working) while still removing the conflict; costs the one-time work of writing and testing the merge driver, and still requires a working build step to be available at merge time, which an unattended firing may not always have.

## Issues
- 2026-08-17 Assumption surfaced ("A build step is reliably available in the environment that resolves a git merge on an unattended firing") but its test is not created: this is a feasibility question about the actual firing environment/toolchain, and this unattended sweep holds no `ost_read_repo` grant. Needs an attended pass with repo sight to write the spec-file instrument.
