---
type: AssumptionTest
source: 'TRANSCRIPT:748498c4-31fb-4110-9012-464c441a463f'
created: '2026-08-06'
evidence: assertion
threshold: >-
  Wrong first-contact path guesses are at least 1 in 5 of all first-contact
  path-taking calls in the corpus. Below that ratio the guard costs more turns
  than it saves and the solution is refuted in favour of its cheaper sibling.
instrument: npx vitest run test/friction/path-guess-hit-rate.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** A replay over transcripts already on disk. Nobody is asked anything.

**What it does.** Walk the corpus and identify every path-taking call whose path had not appeared earlier in that same session — the calls this guard would have blocked. Split them by whether they succeeded or failed. The ratio is the answer: failures are turns the guard saves, successes are turns it costs.

**Why it is red today.** Nothing in the product replays a transcript for first-contact path analysis; the friction adapter records failures only, so the successful calls this test needs are not currently extracted at all. That absence is itself part of the finding — the corpus is biased toward failure by construction, and a test that only sees friction events would compute a hit rate of zero and look like a resounding pass. The spec must read raw session transcripts rather than the distilled friction records, and it should fail loudly if handed the latter.

**What a green does NOT settle.** Whether the turns are equally expensive. A listing that returns a whole directory may be worth more than the failure it replaced, which would justify the guard even at a poor ratio — this test counts turns and cannot weigh them.
