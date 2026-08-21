---
type: AssumptionTest
source: 'agent-ideated:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
threshold: >-
  2 assertions pass in one spec: (1) the build-pass invocation's permission
  flags exclude `examples/automation/**` from Write and Edit, and (2) the same
  invocation still grants Write on at least 1 non-automation path. Both must
  pass; 1 of 2 is a fail.
instrument: npx vitest run test/automation/build-pass-write-scope.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

The assumption above says the permission boundary can be drawn to exclude the automation-script paths *without* blocking the build work that never touches them. Both halves are readable off the invocation, so this is settled by a spec file rather than by anyone's afternoon.

**What the spec must assert.** Two assertions, and the second is what stops a blanket deny from satisfying it. `test/automation/build-pass-reports.test.ts` already establishes the technique — it reads `examples/automation/build-pass.sh` as text and asserts against its source seven times over (heredoc construct, report strings, lineage ordering). The new spec does the same read and checks: (1) the `--allowedTools`/`--disallowedTools` flags scope Write and Edit so `examples/automation/**` is excluded; (2) the same invocation still grants Write for ordinary source paths. A script that simply dropped Write would pass (1) and fail (2), which is the intent this test protects.

**The absent mechanism, named from the code.** Read this pass with `ost_read_repo`: both `build-pass.sh` and `autonomous-pass.sh` scope tool access through `claude -p`'s `--allowedTools`/`--disallowedTools`, and both do it at whole-tool-name granularity only — `Bash,BashOutput,KillShell,Edit,Write,…` — with no path-scoped form anywhere in either file. So the behaviour this spec would assert is absent from the code, not merely untested.

**Honest about what kind of red this is.** The spec file does not exist yet, so the first observation will file as `no-spec`, not `red` — it will mint no build permit and this test is not finished until someone writes the spec and an assertion in it fails. That is not a choice made here: `src/knowledge/instruments.ts` admits exactly one instrument form, `npx vitest run <one-spec-path>`, with shell punctuation refused, so a `-t` filter naming the missing assertion inside the existing spec file is not expressible. An agent that cannot author files cannot reach a non-vacuous red under that grammar. See the finding recorded on "A pass that cannot see the repository cannot set an instrument at all".

**What a green here would NOT settle.** It proves the flags can be written and that the loop still functions with them — feasibility only. It says nothing about whether a real build task will one day legitimately need to edit an automation script; that is the sibling assumption's question and is already out with the operator. It also cannot prove Claude Code's permission layer *honours* a path-scoped Write rule at runtime, because the spec reads the invocation, not the enforcement. If the CLI turns out not to support the finer grain, this test goes red meaning "the mechanism is unavailable" rather than "the script is wrong", and a result recorded against it should say which.

**Grounding.** First-party observation from this pass's own `ost_read_repo` reads, corroborating the same finding recorded on the parent solution by the 2026-08-18 sweep.
