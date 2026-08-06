---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A shipped solution's claim is settleable by running one named spec]]

**The idea.** A solution that ships does not leave the queue — it moves to a different one. `solutionsMissingInstruments` keeps only the unbuilt; shipped solutions with no recorded run appear under a separate heading that asks for the thing a shipped solution can actually supply: a command that passes now, run once, with its exit code recorded as an observation.

**Why this one.** The red-now rule is a rule about *unbuilt* behaviour, and the tool currently applies it to every solution because it has only one queue. But the question "does the shipped thing actually do what the node claimed?" is a real question that the tree cannot presently ask at all — and it is the question that would have settled this pass's central uncertainty, where five shipped nodes were taken at their prose's word because the repository could not be read. A green run of a named spec is evidence the mechanism exists; a status field is a claim that it does.

**How it compares to its siblings.**
- "Drop shipped solutions from the instrument queue" makes the noise go away and collects nothing. That is the right trade if the operator's complaint is purely about the queue draining. This one treats the same nodes as an untapped source of the strongest evidence rung the tree can reach mechanically, and it is the only one of the three that would raise a node above `assertion`.
- "Refuse an instrument that passes on arrival" already has to execute the command, which is most of this solution's machinery — if that one ships, this one becomes cheap, and the two are more complementary than competing.

**Where this fails, stated so it can be judged rather than assumed.** It doubles the queue surface: two lists, two rules about which commands are legal, and a pass that must not confuse them — and the tool's own history says structural rules here get duplicated across a checker and a reporter and then disagree (recorded on "Refuse a wiki-link that contains a newline", where the same link scan lived in three places). It also asks for a green command, which is the exact shape the tool currently refuses at `ost_set_instrument`, so the refusal has to learn a second case and could start accepting green instruments for unbuilt work. Worst case it makes the very confusion it is trying to fix.

**Cost.** A second queue in `computeNextWork`, a second acceptance rule at the write boundary, and a way to record a green run distinctly from a red one. Meaningfully more than its cheapest sibling.

⚠️ Unvalidated. No human has said they want more evidence from shipped work rather than less noise, and those are different products.

## Definition of done

"Require a shipped solution to be asked for an observation and not for a red command"

```
npx vitest run test/ost/shipped-observation-queue.test.ts
```

Red today: there is one queue and one acceptance rule, and no path by which a green command is accepted for anything. Green when the two queues separate cleanly AND the write boundary still refuses a green instrument for unshipped work — that last assertion is the abandon condition, not a detail.

The test title is quoted rather than linked because it is already wikilinked once by its parent Assumption, and a second link would fail `check`'s single-backlink rule.
