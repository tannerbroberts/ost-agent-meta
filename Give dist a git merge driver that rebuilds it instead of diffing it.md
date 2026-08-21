---
type: Solution
source: 'TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2'
created: '2026-08-18'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A build step is reliably available in the environment that resolves a git merge on an unattended firing]]
[[A git merge driver can deterministically rebuild dist from source instead of needing a content-level diff merge]]

Keep dist/ost-agent.mjs checked in, but register a custom git merge driver (via .gitattributes) for that path that runs the build from the merged source instead of attempting a textual three-way merge. A conflict on the compiled output is resolved by regenerating it, never by reconciling two versions of generated code by hand or aborting the firing.

**Compared to the alternatives.** Keeps today's checked-in-artifact model (whatever currently depends on dist/ being present in a plain checkout keeps working) while still removing the conflict; costs the one-time work of writing and testing the merge driver, and still requires a working build step to be available at merge time, which an unattended firing may not always have.

## Issues
- 2026-08-17 Assumption surfaced ("A build step is reliably available in the environment that resolves a git merge on an unattended firing") but its test is not created: this is a feasibility question about the actual firing environment/toolchain, and this unattended sweep holds no `ost_read_repo` grant. Needs an attended pass with repo sight to write the spec-file instrument.

## Repo sight this pass — the premise holds, and the 2026-08-17 blocker is discharged (unattended sweep, 2026-08-21)

The Issues note above records that an assumption was surfaced here but its test was never written, because that sweep held no `ost_read_repo` grant. This pass held one.

**The premise is confirmed.** This solution depends on `dist/ost-agent.mjs` being a checked-in artifact. `.gitignore` carries `dist/*` followed by `!dist/ost-agent.mjs`, with a comment explaining that the non-wholesale form was chosen deliberately — "git cannot re-include a file whose parent directory is excluded wholesale, so a plain `dist/` would make the negation below a no-op and silently break the ability to commit the bundle." So the bundle is tracked on purpose, and the conflict this solution addresses is a real consequence of a decision somebody made rather than an accident of tooling.

**And there is a live consumer, which raises the stakes on the alternatives.** `examples/automation/build-pass.sh` runs `node "$OST_AGENT_DIR/dist/ost-agent.mjs"` for six CLI calls per firing — `build-check`, `gate`, `buildable`, `verify`, `check`, `debt` — and has no build step of its own. Any sibling candidate that untracks dist, or that leaves it unbuilt mid-merge, breaks the loop doing the building. That is an argument in this candidate's favour that its body did not previously make: keeping the artifact committed is not just backwards compatibility, it is a requirement of the automation already running.

**The gap this pass also found.** The assumption "A build step is reliably available in the environment that resolves a git merge on an unattended firing" carried no test at all — invisible to `ost_next_work`, which checks that solutions have assumptions but not that assumptions have tests. One is now proposed beneath it, and it deliberately tests the failure mode rather than surveying environments, because `build-pass.sh` contains no `npm ci` and no `npm run bundle`: the committed automation assumes a prebuilt bundle and never guarantees the toolchain that makes one.

## Definition of done

"A merge driver invoked without the build toolchain fails loudly instead of writing a half-built dist"

```
npx vitest run test/git/dist-merge-driver-toolchain.test.ts
```

Named in plain quoted text rather than as a `[[wikilink]]`: that test's one backlink belongs to its parent assumption, and a second link anywhere in the vault fails `check`'s single-backlink rule.

This is one of two beliefs beneath this solution and it is the *safety* one — it says a driver that cannot build must refuse rather than commit a partial bundle. The other, determinism, is carried by "Have someone with the build scripts open confirm the dist build is deterministic enough to run inside a git merge step", which this pass annotated with what the repository says: the bundle command has no non-deterministic input, and the two residual risks are the caret range on esbuild and whether the merge context installs with `npm ci`. Neither test speaks to whether anyone wants a merge driver.

_Source: this pass's `ost_read_repo` reads of .gitignore, package.json and examples/automation/build-pass.sh. First-party read of committed code; grounds feasibility, not demand. No command executed, no result recorded, rung unchanged._
