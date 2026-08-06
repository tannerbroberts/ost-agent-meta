---
type: Solution
source: 'TRANSCRIPT:424486ec-3489-4b53-8e2b-012232d221ab'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The run's own journal is enough to tell a stale file from a badly quoted one]]

**Candidate solution (unvalidated).** Every read the run performs is journalled with the file's content hash. When a string replacement then fails, the run re-hashes the file and answers the one question the raw error cannot: did the file change since I read it, or did I quote it wrong? Two causes that produce one identical message become two different reports.

**Approach:** *disambiguate the failure after the fact*, using a record the run already has reason to keep.

**Why this is worth having even though it is the least ambitious of the three.** In the observed session the agent did eventually reach the right diagnosis — "another process is writing to this repo right now (HEAD moved to the PR #22 merge, and ~14 source files have uncommitted changes touched seconds ago)" — but reconstructed it by hand from HEAD and file mtimes, after the fact, and only in that one session. The same failed-match error recurs elsewhere with no diagnosis attached at all. This candidate makes the reconstruction automatic and therefore repeatable; it does not make it earlier.

**Contrast with siblings.** Strictly cheaper and strictly dumber than the drift sentinel: it needs no sampling loop and no background watcher, and it fires only on a failure that has already happened. It is also the only one of the three that helps a reader of the transcript *afterwards*, which matters because this vault's own evidence channel is transcripts — a friction record that says "stale file" is usable signal, and one that says "String to replace not found in file" is not.

**Where it fails.** It is silent about every collision that does not happen to produce a failed write. A file read, moved underneath, and then never edited leaves this mechanism with nothing to say, and the run proceeds on stale content believing it is current.

**Distinct from the harness's own read-before-write guard**, which is recorded separately under "The file changed after I read it, and the failed edit is how I find out". That guard refuses a write when the harness knows the file moved; this classifies a failure the harness has already allowed through, and lives in this product's runner rather than in the host.

⚠️ Unvalidated, and ideated by an agent from its own session record. This grounds usability, not that anyone outside wants it.

## Definition of done

"Change a journalled file underneath a replacement and require the failure to name staleness, not a missing string"

```
npx vitest run test/runner/failed-match-attribution.test.ts
```

Red today because neither the spec nor the read journal it consults exists. Green when all three arms hold — stale-file, bad-quote, and an explicit cannot-say for an unjournalled file. The third arm is the load-bearing one; without it the mechanism passes by always answering "changed".
