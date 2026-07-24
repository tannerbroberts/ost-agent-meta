---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
---
#AssumptionTest #unvalidated #feasibility

**Assumption under test (feasibility):** The agent will actually file friction events under load, rather than pushing through silently and reporting a clean run.

**Proposed test:** Add the instruction and the filing affordance, run five ordinary passes, and count. Separately, have a human read the transcripts of those same five passes and count the friction moments that went unfiled.

**Size:** five passes of normal operation; the comparison is the whole cost.

**Pre-committed threshold:** ≥1 event filed per pass AND ≥70% of the events specific enough for a human to act on AND the unfiled-to-filed ratio below 2:1. A high miss rate means self-reporting is a supplement, not a channel.

**Decides:** whether self-reporting can stand alone or must be paired with retrospective harvesting.

Proposed by the agent — a human performs the transcript comparison; the agent must not score its own reporting rate. No results recorded here.
