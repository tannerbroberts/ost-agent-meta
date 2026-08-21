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

## Repo sight this pass — two consumers found, and the cost is larger than the body implied (unattended sweep, 2026-08-21)

The Issues note above deferred this solution's test because answering it needs an inventory of every consumer of `dist/`, and that sweep held no `ost_read_repo` grant. This pass held one. Two consumers are confirmed in committed code, and both would break as written:

- `examples/automation/build-pass.sh` — `CLI="$OST_AGENT_DIR/dist/ost-agent.mjs"`, invoked for six CLI calls per firing (`build-check`, `gate`, `buildable`, `verify`, `check`, `debt`), with no `npm ci`, no `npm install` and no `npm run bundle` anywhere in the script.
- `examples/automation/github-workflow.yml` — checks OST-Agent out with `actions/checkout@v4` and points its MCP config at `node "$SRC/dist/ost-agent.mjs" mcp`. The job installs Node and Claude Code and never installs this project's dependencies or builds it. On a fresh runner the bundle arrives from git and from nothing else.

Not checked, and named so this is not read as complete: `examples/automation/autonomous-pass.sh` (20KB, could not be read whole on this surface) and any consumer outside the repository.

**This sharpens the trade rather than settling it.** The body already said conversion "may be a larger change than it looks"; the read says what the change actually is. Both confirmed consumers can be converted — a `npm ci && npm run bundle` step in each — but that step lands on the critical path of every six-hourly CI run and every hourly firing, on a runner that currently installs nothing from this project. Against the merge-driver sibling, which keeps the bundle committed and pays only when a conflict occurs, this candidate pays on every firing whether or not anything conflicted. That is the comparison a human should make, and it now rests on read code rather than on either candidate's self-description.

## Definition of done

"Every invocation of the committed bundle is preceded by a build step, and a new consumer without one fails the census"

```
npx vitest run test/release/dist-consumer-inventory.test.ts
```

Named in plain quoted text rather than as a `[[wikilink]]`: that test's one backlink belongs to its parent assumption, and a second link anywhere in the vault fails `check`'s single-backlink rule.

The test is a census rather than two assertions precisely because the inventory above is partial — finishing it is the spec's first job — and it plants a consumer with no build step to prove the census can still fail. It settles feasibility only: a complete, converted inventory says nothing about whether the per-firing build cost is worth paying, which stays a human's call.

_Source: this pass's `ost_read_repo` reads of examples/automation/build-pass.sh, examples/automation/github-workflow.yml and .gitignore. First-party read of committed code; grounds feasibility, not demand. No command executed, no result recorded, rung unchanged._
