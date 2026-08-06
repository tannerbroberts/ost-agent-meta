---
type: Opportunity
source: 'TRANSCRIPT:748498c4-31fb-4110-9012-464c441a463f'
created: '2026-08-06'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[The run is handed the workspace layout at startup, before it composes anything]]

Observed across sessions: `sed: src/cli/index.ts: No such file or directory`, `ls: test/adapters/transcript-model-reader.test.ts: No such file or directory`, `(eval):1: no matches found: test/tmp*`, and a `git` invocation returning exit 128 from a directory holding only `bin/` and `vaults/`. In each case the command was well-formed and addressed a file the agent believed existed.

This is the failure mode an invented instrument produces: the command fails, but it fails because nothing is at the path, which is the weakest reason a command can fail and tells a builder only "create this file". The need is for the agent to know the shape of the thing it is addressing before it composes a command against it.
