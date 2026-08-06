---
type: AssumptionTest
status: unvalidated
source: 'TRANSCRIPT:8a9777ad-a1ca-47fc-ab8e-3bd4b001a5cd'
created: '2026-08-06'
evidence: observed
threshold: >-
  All four omitted tool grants named, the path-scoped read gap named, and zero
  false gaps against a pattern-granted entry.
instrument: npx vitest run test/runner/grant-preflight.test.ts
---
#AssumptionTest #unvalidated #evidence/observed

**Lane: compute-only.** Nothing here needs a person: the two lists are both files on this machine, and whether one covers the other is a set operation with a definite answer.

Build the resolver against a fixture pair — a skill frontmatter declaring the tools the unattended prompt actually names (`ost_check`, `ost_debt`, `ost_status`, `ost_flag_humans_required`, plus repo reads under a product path), and a settings allowlist that omits four of them, which is the configuration the five recorded sessions were run under. The resolver must return those four by name and must not return a false gap for a tool that is granted under a pattern rather than a literal.

The part that decides whether the parent assumption survives is the path-scoped case. Four of the fifteen recorded denials were `Glob` refused on `/Users/tanner/dev/OST-Agent` — the tool was available and the directory was not. A resolver that reports "Glob: granted" against that fixture has cleared a run that is about to be blocked, which is worse than no preflight, because it converts an unknown into a wrong answer. So the fixture includes a read grant scoped to one directory and a demand to read another, and the resolver is required to report it as a gap.

**Pre-committed bar:** all four missing tool grants named, the path-scoped read gap named, and zero false gaps against the granted-by-pattern entry. Anything less and the preflight cannot be trusted to clear a run, which means the assumption is false in the way that matters and the sibling solution "The run's report leads with what it was refused, so a denied night cannot read as a quiet one" is the one to build.

**What a green run here does not settle.** It answers feasibility only: that the gap is computable from files already on disk. It says nothing about whether stopping the whole pass over one missing optional tool is the behaviour an operator wants — that is the false-stop risk named on the parent solution, it is a desirability question, and it needs an operator, not a spec file. It also says nothing about whether the harness's live grant matches the settings file it read; a resolver that is right about the configuration and wrong about the session is still wrong at 3am.
