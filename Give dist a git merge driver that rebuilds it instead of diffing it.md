---
type: Solution
source: 'TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2'
created: '2026-08-18'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Keep dist/ost-agent.mjs checked in, but register a custom git merge driver (via .gitattributes) for that path that runs the build from the merged source instead of attempting a textual three-way merge. A conflict on the compiled output is resolved by regenerating it, never by reconciling two versions of generated code by hand or aborting the firing.

**Compared to the alternatives.** Keeps today's checked-in-artifact model (whatever currently depends on dist/ being present in a plain checkout keeps working) while still removing the conflict; costs the one-time work of writing and testing the merge driver, and still requires a working build step to be available at merge time, which an unattended firing may not always have.
