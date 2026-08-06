---
type: Solution
source: 'agent-ideation:2026-08-06-unattended-sweep'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Forcing a look before every path costs more turns than the wrong guesses did]]

**The idea.** A command that takes a path is refused unless that path has already appeared in this session — in a listing, a search result, or a prior read. The run must look before it addresses. The refusal is cheap, immediate, and names the looking that would satisfy it.

**Why this shape.** The parent's census is a list of first-contact guesses, and a guess is exactly what this makes impossible. It also converts an expensive failure into a cheap one: `sed` against a missing file costs a turn and returns a message about that one path, whereas a listing costs a turn and returns the whole directory, so the run that was forced to look is better off than the run that was allowed to guess and happened to be right.

**How it differs from its siblings.** It is the pull form, and it is the only one of the three that scales to a workspace nobody inventoried — it never needs to know the layout in advance, because it makes the run acquire the part it actually needs. Its startup-manifest sibling pays a fixed cost for a description that may not cover the path in question; this pays a variable cost that always covers it.

**Where it fails, stated so it can be judged.** It is the read-before-write handshake generalised, which means it inherits that handshake's entire recorded cost — this vault's own corpus records roughly twenty collisions with read-before-write across eleven sessions, making it the most frequent friction event the product has ever observed about itself. Proposing the same mechanism over a wider surface is proposing more of the thing that hurts most, and that should be argued rather than assumed. It is also wrong for the legitimate case of creating a file that does not exist yet, and needs an exemption there — which is precisely the seam through which the guard gets routinely bypassed.

**A limit worth stating.** Like its sibling, it does not address the failure this pass actually hit: a path that exists and cannot be read for want of a grant. Looking first returns a permission denial rather than a listing, and the run is exactly where it started.

**Cost.** Session-scoped path bookkeeping plus a refusal path. Cheap to build, and the expensive part is the friction it deliberately introduces.

⚠️ Unvalidated. Agent-ideated from the agent's own transcripts — usability evidence, not evidence that anyone wants this.

## Definition of done

"Replay the corpus to count how many correct path guesses the guard would have taxed"

```
npx vitest run test/friction/path-guess-hit-rate.test.ts
```

Green means wrong first-contact path guesses are at least 1 in 5 of all first-contact path-taking calls. Below that the guard costs more turns than it saves and this solution should be dropped in favour of "A path failure answers with the layout it was addressed against, not with the path that was missing".

One trap the spec must avoid, or the number is meaningless: the friction adapter records failures only, so a test reading the distilled friction records would see no successful guesses, compute a hit rate of 100%, and pass resoundingly while measuring nothing. It must read raw session transcripts and fail loudly if handed the friction records instead.

Named in plain text rather than linked: the test's one wikilink is held by its parent assumption, "Forcing a look before every path costs more turns than the wrong guesses did".
