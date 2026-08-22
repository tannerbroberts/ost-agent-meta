---
type: Solution
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A stored expression can reproduce what the hand-written censuses counted, without quietly narrowing it]]

**Variation dimension: automated vs manual — the counting is automated and the judgement is left manual, and the split is drawn between them rather than around the whole task.** A node stops quoting a number in prose and instead carries the expression that produces it: the record set, the pattern counted, and the bar. Anything that renders the node runs the expression and prints the current value beside the bar — "91 across 29 sessions; bar is at most 1 per session; **breached**." The prose keeps every word of the argument about what the number *means*, which is the part no expression holds.

This is the same posture the rollup already takes and the same one the codebase argues for in `src/eval/rollup.ts`: every figure derived from what nodes carry, nothing a pass typed about its own work. This extends that from tree-shape figures to the evidence-corpus figures the censuses are made of.

**Compared to its siblings.** The only candidate where a stale number is structurally impossible rather than caught after the fact — there is no stored number to go stale, because the number is computed at read time. It is also the only one that makes past censuses cheaper rather than more expensive: five dated sections on one node collapse into one expression plus the five arguments, which is the accumulation problem that node has already been asked twice to stop.

**What it deliberately gives up.** History. A computed value shows what is true now and forgets that the count was 83 last week, which is precisely the trend the operator reads these censuses for. Keeping both means keeping a stored series after all, and then the question of what re-takes *that* comes back in a smaller form.

**What would make this the wrong pick.** It needs an expression language, and the honest version of that requirement is uncomfortable: the four censuses on the originating node are hand-written greps with hand-chosen splits, and at least one of them ("the two classes sum to 125 rather than 127; the residue is other denial shapes not broken out") admits its own pattern is a floor. An expression language rich enough to express what those greps actually did is a substantial build, and one too poor to express them would silently narrow what gets measured — a number that is always current and quietly counts the wrong thing is worse than a stale one somebody knows to distrust.

⚠️ Unvalidated. Agent-ideated from one recorded session.
