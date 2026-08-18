---
type: Solution
source: 'TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2'
created: '2026-08-18'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Every current consumer of the checked-in dist file can be changed to build it locally instead]]
[[Nothing outside the build loop depends on dist being present in the committed tree between firings]]

Remove dist/ost-agent.mjs (and any other compiled artifact) from version control and .gitignore it; have each firing run the build step to produce it locally before use. Two branches can no longer conflict over a file neither of them hand-edits, because it is never checked in on either.

**Compared to the alternatives.** Eliminates the conflict class entirely rather than managing it, at the cost of every firing paying a build step it currently gets for free from git. Requires whatever consumes dist/ (a published package, a deploy step) to build it from source at that point instead, which may be a larger change than it looks.

## Issues
- 2026-08-17 Assumption surfaced ("Every current consumer of the checked-in dist/ file can be changed to build it locally instead") but its test is not created: answering it requires an inventory of every consumer of dist/ in the repository, and this unattended sweep holds no `ost_read_repo` grant. Needs an attended pass with repo sight to write the spec-file instrument.
