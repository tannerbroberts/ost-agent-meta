---
type: Solution
source: 'TRANSCRIPT:35566d8b-a635-49b1-acc8-6bfbeeb134e7'
created: '2026-08-05'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Check whether initialising only tool-created directories still covers every captured failure]]

Remove the variance rather than detect it. Every folder this tool scaffolds gets `git init` at creation, always, with no flag to skip it — so "is this a repository?" stops being a question anybody has to ask, probe for, or record.

**Nobody pays.** Against [[One workspace-state probe the run makes before it plans, not one failing command at a time]] (the reader pays, every time) and [[The scaffolder writes a manifest of what it did and did not initialise]] (the writer pays once, and readers must still handle absence), this candidate's claim is that the cheapest state check is the one that cannot come out false.

**The case for it is the observed distribution.** All four captured exit-128 sessions were freshly-scaffolded folders, and in each the run's very next act after the failure was to initialise the repository — i.e. the run always wanted a repo, and the only question was who would notice it was missing and when. When every caller wants the same answer, making it unconditional is usually right.

**The case against, which is real and should not be waved past.** Unconditional initialisation is a side effect on the operator's filesystem that they did not ask for, in a product whose whole trust story is that it does not take irreversible actions unprompted — see [[Fear the agent could take a destructive, irreversible action]]. `git init` is close to harmless and is trivially undone, but "close to harmless" is exactly the argument that erodes a boundary, and a scaffolder that initialises a repo inside a directory that is already inside another repository creates a nested repo that is genuinely confusing to unpick.

**So the sharpest version is narrower than the title.** Initialise unconditionally *when scaffolding a new directory this tool created*, and never touch a directory it did not create. That keeps the property — no state question inside our own workspaces — without claiming authority over the operator's disk. Whether that narrower version still covers the observed failures is the thing to check first, and it is cheap to check because the four sessions are on record.

_Agent-ideated, unvalidated — one of three competing candidates under this opportunity, for a human to compare rather than adopt._

## Definition of done

[[Check whether initialising only tool-created directories still covers every captured failure]]

```
npx vitest run test/runner/unconditional-scaffold-init.test.ts
```

Red today: scaffolding does not initialise, and nothing checks whether a scaffold target sits inside an existing working tree. Green when the narrowed rule covers all four captured failures and no target in the record would produce a nested repository.

**What this does not settle, and it may be decisive.** Whether the operator accepts an unrequested write to their disk at all is a consent question, and no coverage count answers it. If the answer is no at any scope, this candidate is dead however green the command comes out.
