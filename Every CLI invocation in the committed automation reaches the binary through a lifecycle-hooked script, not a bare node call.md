---
type: AssumptionTest
source: 'agent-ideation:2026-09-02-unattended-sweep'
created: '2026-09-02'
evidence: assertion
threshold: >-
  Zero bare `node .../ost-agent.mjs` invocations remain across every file in
  examples/automation/, and at least 1 lifecycle hook is asserted present in
  package.json.
instrument: npx vitest run test/automation/cli-invocations-are-hooked.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

Scan every file under `examples/automation/` for invocations of the CLI binary and assert that none of them is a bare `node` call — each reaches the binary through a script the package manager runs, so a `prepare`/`pre*` hook is on its path. Assert separately that such a hook exists in `package.json`, since routing the calls buys nothing if there is no hook at the other end.

**Why this red is specific to this question rather than generic.** It fails today for a reason nobody has to take on faith: `examples/automation/build-pass.sh` contains six `node "$OST_AGENT_DIR/dist/ost-agent.mjs"` invocations — `build-check`, `gate`, `buildable`, `verify`, `check` and `debt` — and no `npm ci` or `npm run bundle` anywhere. Read first-party this pass with `ost_read_repo`. Change the question and this command stops being red for the same reason; that is the property the sweep asks for and it is present here.

**Pre-committed bar, fixed before anything runs.** Zero bare invocations across every file in `examples/automation/` — currently three files: `autonomous-pass.sh`, `build-pass.sh`, `github-workflow.yml` — and at least one lifecycle hook asserted present. Six known failures to zero; a partial routing that leaves one bare call is a fail, because one unhooked entrypoint is exactly the silent-bypass failure the parent assumption is about.

**Instrument honesty, stated rather than hidden.** `test/automation/cli-invocations-are-hooked.test.ts` does not exist yet, so the first run of this command will be filed `no-spec` — the weakest reason a command can fail, and it grants no build permit. That is a grammar limit, not a choice: `ost_set_instrument` accepts only a bare `npx vitest run <path>.test.ts` and refuses a `-t` filter, so an assertion-level red inside an existing spec cannot be expressed on this surface at all. Two things make it as strong as the grammar allows — the path sits in `test/automation/`, an existing directory, so the builder inherits its neighbours' conventions rather than making a structural decision; and the bar above names the exact six invocations and the exact three files, which is what a builder actually works from. Once the spec exists it will be red on an assertion about real committed shell, not about a missing file.

**What a green here does not settle.** It proves the automation is routed and a hook exists. It does not prove the hook *fires* in the operator's real firing environment, does not prove the rebuild it triggers succeeds when the toolchain is absent — that is the question "A merge driver invoked without the build toolchain fails loudly instead of writing a half-built dist" already carries — and says nothing about desirability or viability. It also cannot see an invocation typed by hand outside the repository, which is the parent assumption's open edge.

⚠️ Proposed only — the agent does not run tests or record results.
