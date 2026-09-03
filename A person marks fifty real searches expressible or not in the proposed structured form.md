---
type: AssumptionTest
source: 'TRANSCRIPT:9c00df65-1c8d-4171-a870-22efc103d834'
created: '2026-09-03'
evidence: assertion
lane: humans-required
threshold: 'at least 40 of 50 expressible, and at least 15 of the 20 marked exploratory'
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

Take fifty search invocations from real captured sessions, strip them of their results, and have a person who did not design the structured form decide for each one whether it could have been asked in that form without an escape hatch to a raw pattern. Mark each expressible / not-expressible / unclear, and separately mark whether the search was one where the caller already knew what they were looking for.

The second mark is what makes this worth a person's afternoon rather than a count: the assumption is not "most searches are expressible" but "the searches that matter are", and only a reader can tell an exploratory search from a confirmatory one.

**Lane: humans-required.**

**What this does NOT settle.** Nothing about whether the compiler can be built, whether it is fast, or whether anyone would prefer it to a raw pattern once both exist. It answers expressive coverage only, and a supported verdict here leaves feasibility and preference exactly where they were.

A person outside the building is the measurement here: A person must read each search and judge expressibility and intent; no exit code distinguishes an exploratory search from a confirmatory one, and the designer of the form cannot be the judge of it.
