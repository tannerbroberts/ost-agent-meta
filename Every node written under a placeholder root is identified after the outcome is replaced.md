---
type: AssumptionTest
source: 'REPO:OST-Agent/src/ost/node.ts'
created: '2026-08-23'
evidence: assertion
threshold: >-
  at least 5 of 5 nodes written under a placeholder root are identified as such
  after set-outcome, and 0 of 5 nodes written afterwards are misidentified;
  today 0 of 5 are identified
instrument: npx vitest run test/ost/placeholder-provenance.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Pre-committed threshold:** scaffold a vault with a placeholder root, write 5 nodes under it, run `set-outcome` with a real mandate on the same calendar day, write 5 more, then ask the tree which 5 were provisional. **At least 5 of 5 placeholder-era nodes must be identified, and 0 of 5 later nodes may be misidentified. Today 0 of 5 are identified**, because `OstNode` carries no field recording the mandate in force and `serialize` drops any key not on its enumerated list.

**Why the same-day construction is the whole design of this test, and not an awkward detail.** A date-based partition against the root's history would pass a lazily-built version of this spec — write the placeholder nodes in January, replace in March — while failing the case the solution is actually trying to create, which is a stranger scaffolding and replacing within one sitting. `created` holds `YYYY-MM-DD` with no time, so a same-day replacement makes every node on that date ambiguous. Forcing both cohorts onto one day means a builder cannot satisfy this by reading dates; they have to record the thing itself.

**Why this is red today for a reason specific to this test.** The assertion is not that a file exists or a command runs. It is a two-sided count over a constructed vault: 5 identified and 0 misidentified. A builder who stamps every node would pass the first half and fail the second; one who stamps nothing fails the first. Change the question and both numbers change with it.

**What a green here does NOT settle.** Only that the damage from a placeholder is *visible*. It says nothing about whether a loudly-marked placeholder actually gets replaced — the sibling assumption's question, and a person's — and nothing about whether shipping a placeholder root is wise at all. This solution's central objection stands untouched by any exit code: the Outcome is the one thing the agent may not invent, and a placeholder is an invention wearing a disclaimer. A green here makes that invention auditable, not acceptable.

**Why a new spec path.** `test/ost/` holds 47 specs, none of which reads mandate provenance, because no such field exists. Naming an existing green spec would meet `verifyInstrument`'s first-run-green refusal and could never produce an observation.

_Grounded in first-party `ost_read_repo` reads of `src/ost/node.ts` and `src/ost/frontmatter.ts` and a listing of `test/ost/`. Nothing executed. Rung stays at the `assertion` floor._
