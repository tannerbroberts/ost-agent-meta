---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The tools that actually stalled honour the non-interactive convention]]

The run declares itself unattended to everything it invokes — the environment variables, the flags, the config that tell a tool no terminal is watching — and anything that would still prompt is made to exit with an error instead. The run then fails in a way its supervisor can see, rather than hanging in a way nobody can.

Turning a silent stall into a loud failure is the whole gain. A failure is reportable, retryable, and countable; a hang is none of those, and the evidence shows one costing an entire run twice.

**Compared to the alternatives.** Simple, uses mechanisms that already exist in most tools, and it never guesses at an answer on the operator's behalf. It converts the stall into a stop rather than letting the work continue, so a run that hits a prompt still achieves nothing — it just says so promptly.

**What would make this the wrong pick.** It relies on every invoked tool honouring the convention, and the ones that ignore it are exactly the ones that caused the problem. A git that prompts for a reconcile strategy despite a non-interactive environment will hang exactly as before, and the run will now believe it cannot.

## Definition of done

[[Set the non-interactive flags and check whether the tools that stalled actually honour them]]

```
npx vitest run test/runner/non-interactive-honoured.test.ts
```

Green means both situations named in the harvested transcripts — the git that hit divergent branches, the copy that asked to overwrite — fail promptly under every non-interactive signal available, rather than prompting anyway or hanging. It is red today because nothing sets those signals and no harness reproduces either command.

**Why this is the assumption and not a detail.** The solution's premise is that invoked tools honour the convention. The tools that ignore it are exactly the ones that caused the problem in the first place — and the failure mode of getting this wrong is not neutral, it is worse than today: a `git` that prompts despite a non-interactive environment will hang as before, but the run will now believe it cannot hang, and will have stopped watching for it.

**What green does NOT settle.** Two commands are not a tool chain. Any tool added later brings its own behaviour and its own idea of what non-interactive means, so this establishes the convention works for the failures actually observed and makes no claim beyond them. The honest reading of green is "the two known stalls are fixed", not "prompting is solved".

## History
- 2026-08-05 unlinked [[Set the non-interactive flags and check whether the tools that stalled actually honour them]] — moved under [[The tools that actually stalled honour the non-interactive convention]] — the belief this test measures now has a node of its own
