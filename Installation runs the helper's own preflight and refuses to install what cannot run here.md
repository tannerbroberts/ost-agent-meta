---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A helper's declared requirements stay true as the helper changes]]

A helper declares what it needs — this interpreter at this version, these commands present — and installing it checks those needs against the machine it is being installed on. A helper that cannot run here does not get installed, and the refusal names exactly what is missing and what version was found instead.

The failure being prevented is a silent bet: the script was written against bash 4, installed on a machine shipping bash 3.2, and nothing between those two moments compared them. Install time is the natural place for that comparison, because it is the last moment when the machine and the requirements are both in view.

**Compared to the alternatives.** Catches the problem at the earliest point where it is knowable, and produces a refusal a person can act on rather than a runtime error mentioning a builtin they have never heard of. It only covers requirements someone remembered to declare, and an undeclared dependency passes install and fails exactly as before.

**What would make this the wrong pick.** Requirement declarations rot. A script that grows a `mapfile` six months after its manifest was written will install cleanly and fail at line 21, which is the original problem with an extra file to maintain.

## Definition of done

"Write manifests for the existing helpers and check whether they catch the failures already seen"

```
npx vitest run test/runner/helper-manifest-coverage.test.ts
```

Green means every helper carries a manifest that declares `mapfile`, and no manifest omits more than one command its script actually invokes. It is red today because no helper carries a manifest at all.

**The omission diff is the honest measure and should be weighted above the catch.** A manifest covers only what someone remembered to declare, and a script that grows a dependency after its manifest was written installs cleanly and fails at run time exactly as before. Asserting the declared set against what the script genuinely uses is the only clause here that a careless author can fail; the `mapfile` catch is nearly free once manifests exist at all.

**What green does NOT settle, and it is a bias in the sample rather than a gap in the check.** Manifests written now, by someone who knows this class of problem exists, are more careful than manifests written routinely six months from now. Green measures the manifests this project happens to have; it says nothing about the discipline holding, and the discipline is the actual mechanism.

## History
- 2026-08-05 unlinked "Write manifests for the existing helpers and check whether they catch the failures already seen" — moved under "A helper's declared requirements stay true as the helper changes" — the belief this test measures now has a node of its own
