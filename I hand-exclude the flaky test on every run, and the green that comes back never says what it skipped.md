---
type: Opportunity
source: 'TRANSCRIPT:785ea509-96b9-4225-b45a-babd5321aafc'
created: '2026-08-05'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed

**Customer need (operator's perspective):** "When I have to work around a test I know is flaky, I need the workaround to be on the record. A suite that came back green while one file was excluded by hand is not the same result as a suite that came back green, and right now nothing I can read afterwards tells the two apart."

This is downstream of flake attribution, not the same need. Attribution asks *why did this fail* — a busy machine or a real regression. This asks what happens **after** the operator has already answered that and decided to keep moving: the only tool available is to retype the exclusion into every subsequent invocation. In the captured session the agent issued the full suite four times, three of them carrying `--exclude "test/mcp/wall-clock-budget.test.ts"` typed out by hand, and the passing result it finally reported carried no trace of the exclusion. The next reader — a later pass, a gate, a person — sees a green suite and a covered file that was never run.

Two things go wrong and they compound. The exclusion is **manual**, so it has to be remembered on every invocation and is silently dropped the moment someone forgets. And it is **invisible**, so the result overstates its own coverage. That second one is the same defect the tree already names one level up in "A sweep that cannot read its subject reports a clean result" — a clean result that was clean because nothing looked.

**Litmus (more than one way to address?):** Yes — a quarantine list committed to the repo so the exclusion is declared once rather than retyped; a runner that reports skipped-by-quarantine alongside passed and failed; a green result that carries its own exclusion set so a gate can refuse to read it as full coverage; retry-with-attribution so the flaky file need not be excluded at all; expiring quarantine entries so a workaround cannot become permanent by inattention.

_Provenance: TRANSCRIPT:785ea509-96b9-4225-b45a-babd5321aafc (2026-08-04) — four full-suite invocations, three carrying a hand-typed exclusion of the same file. Corroborated by two friction notes already in this vault naming that same test flaking: `.ost-agent/friction/2026-08-01-friction-wall-clock-budget-test-flaked-once` and `-a-second-time-2280`. Observed behavior — mechanically captured from the agent's own session; it grounds usability, not desirability. Unvalidated — for human review._
