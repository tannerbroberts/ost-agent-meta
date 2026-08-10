---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Operators would rather have honest gaps than guessed commands]]
[[What is in the 33 queue entries no tool has ever listed]]

**The idea.** Instrument-writing is gated on repo sight. A surface without it gets the refusal instead of the write, and the test is routed to a named lane — work waiting on an attended pass — rather than being cleared blind.

**Why this shape.** It is the only candidate that makes the guarantee unconditional. The other two produce a tree in which some instruments are grounded and some are not, and rely on a downstream reader caring about the difference. This produces a tree in which every instrument was written by something that had read the code, and the price of that is paid visibly, as a backlog with a name on it.

It also answers a question the other two dodge: what a blind pass should *do* with `solutionsMissingInstruments`. Under the siblings, the answer is "write instruments anyway, marked or checked". Under this one, the answer is "nothing, and say so", which is what the last three passes have done by hand each time and had to re-reason from scratch.

**How it compares to its siblings.**
- "An instrument records whether the pass that wrote it could see the repository" is the observe-only floor; this is the ceiling. Both could ship, in that order.
- "An instrument naming a spec path that does not exist is refused" catches the weak artefact even from a sighted author, which this does not — a pass with repo sight can still write a lazy path under this rule.

**Where it fails, stated so it can be judged.** This trades throughput for groundedness, and the exchange rate is unknown. 61 solutions currently wait on an instrument; under this rule an unattended fleet contributes zero of them, and whether an operator prefers 61 honest gaps to 61 guessed commands is a question about what they want, not about the code. That is the assumption beneath this node and it is not one a spec can settle.

The blunter risk: gating on capability means the capability becomes the thing to acquire, and the cheapest way to acquire it is to widen a grant. A rule that makes blindness expensive is a rule that argues for handing an unattended loop repository access, which is a different safety conversation entirely and should be had deliberately rather than as a consequence.

**Cost.** A capability check and a lane. Small to build, large to live with.

⚠️ Unvalidated. Agent-ideated.

## Definition of done

"Five operators choose between sixty-one weak instruments and sixty-one blanks"

There is deliberately **no command** here. This solution's risk is not mechanical — it trades throughput for groundedness, and whether that trade is wanted is a preference the repository cannot hold. The test names five operators who run an unattended agent overnight and pay for the compute, and it is created human-required rather than left as prose nobody is assigned to.

A builder should not start this one until that result exists: building it and being wrong costs the whole unattended instrument backlog.

## Issues
- 2026-08-07 2026-08-07 A human-required test still reads as instrument debt — observed on this node, minutes after it was created, and it is a defect in the queue rather than in this node.

This solution's only assumption test is "Five operators choose between sixty-one weak instruments and sixty-one blanks", created with `humansRequired` because the measurement is an operator's preference and no command can hold one. That is the correct, sanctioned outcome for a test of this kind. The very next `ost_next_work` call listed this solution in `solutionsMissingInstruments` — the bucket whose instruction is "declare an `instrument:` (one spec file that fails today and passes when the solution is built)".

So the queue is asking for a command that should never exist. A pass that complies writes a spec for a question about human preference, which is the laundering the human-required lane was built to prevent; a pass that declines leaves the entry outstanding and meets it again next pass. Neither is a good outcome and the surface offers no third one, since `ost_flag_humans_required` is withheld here and would in any case refuse a test whose lane is already declared.

Scope, measured rather than guessed: `solutionsMissingInstruments` went from 61 to 62 across this pass, and this node is the increment. The other 61 have not been checked for the same shape, so the true size of the miscount is unknown and is worth counting before anything is built.

This is a sibling of "The queue sends me to ideate under a heading that already has thirty solutions under it" — same family, different bucket: the queue reports a gap that is not a gap and instructs the wrong work. It is filed here as an annotation rather than as a new Opportunity because whether it is a distinct need or a second instance of that one is a judgement about the opportunity space, and an unattended pass that has already created four opportunities today should not also decide that. For a human: if it is distinct, it wants a node of its own under the same bucket; if it is the same need, that node's three candidate solutions should each be checked for whether they cover this case, and none of them currently does.
- 2026-08-09 2026-08-09 Read the census appended to this node today together with the older one on "Filter the queue on shipped and count what is still unsatisfiable", not as a second opinion on it. That test node carries a 2026-08-06 hand count of the same queue, and it is the more complete of the two on the shipped class: it identifies five shipped solutions in the visible 25 and bounds the whole-queue contamination at ten nodes by grepping every `status:` in the vault. Today's count verified only three of that five from frontmatter and did not check the other two, so where the numbers differ the older one is better evidenced and today's is the subset. Same tree, same method, same agent lineage, three days apart — so the agreement between them is persistence, not corroboration, and nobody should count it as two independent measurements of the queue's composition. What today's adds that the older does not: a classification of all 25 visible titles into three classes rather than an inspection of 11, giving the "at most 7 of 25 are what the bucket is actually for" figure, and confirmation that the defect survives across passes — the queue moved 63 → 62 in three days while the shipped entries stayed in it. What both share, and it is the load-bearing weakness of each: the 37 unlisted entries were never classified by either, both read titles as a proxy for the majority class, and neither could open the repository. A human wanting the real number should run the instrument already declared on that test node — `npx vitest run test/ost/instrument-queue-excludes-shipped.test.ts`, logged red on 2026-08-06 for "No test files found" — rather than commission a third hand count.

## The count this node asked for — 25 of 62 classified (unattended sweep, 2026-08-09)

**Not a recorded result.** No test was run. This answers the open question in the Issues section above — *"The other 61 have not been checked for the same shape, so the true size of the miscount is unknown and is worth counting before anything is built"* — on the part of the bucket a capped tool call will show.

`solutionsMissingInstruments` was 62 this pass and `ost_next_work` lists 25 of them. Those 25 were classified by what their test could possibly measure. **At most 7 of 25 are asking for the thing the bucket says it is asking for.**

| Class | n | What an instrument would be |
|---|---|---|
| Already shipped — verified from frontmatter | 3 | Impossible: green on arrival, so it cannot fail and measures nothing |
| No command by design — verified by reading the node | 1 | The laundering the human-required lane exists to prevent |
| Human preference, demand, or pricing by nature — judged from the solution's subject | 14 | A spec standing in for a person's answer |
| Plausibly mechanical — the bucket's actual target | 7 | A real spec, if the repository could be read |

**The three shipped ones are verified, not inferred**, because that class is the sharpest: `Refuse a wiki-link that contains a newline`, `Post-session transcript harvester` and `Refuse a write whose content is empty or literally undefined` all carry `status: shipped` in their own frontmatter and all three were still listed. The first of those was set to `shipped` by the 2026-08-05 sweep *specifically because* an instrument was impossible for it, with that reasoning written into its History. Setting the status did not remove it from the bucket. So the one repair a previous pass identified and performed correctly does not work, and the node it was performed on came back the next pass and the pass after.

**The 14 are a judgement and should be read as one.** They were classified by subject rather than by opening each node — solutions about what to charge, how to position against funded competitors, whether to run a concierge cohort, whether to publish a side-by-side diff as the pitch. Titles like *Charge per assumption test designed and run to a pre-committed threshold* and *Instrumented public trial with a willingness-to-pay probe* name a measurement that is an operator's or a buyer's, and no exit code holds one. The two nodes in this class that *were* read in full — this node and "The instrument-writing step declares repo sight required and skips itself rather than inventing paths" — both say in their own bodies that they deliberately carry no command. That is a 2-for-2 confirmation rate on the subset that was checked, which is why the class is stated as a finding rather than a guess, and it is still 14 titles read as titles.

**What the number changes.** This node's Issues section framed the miscount as an increment of one and called the true size unknown. On this sample the bucket is not mostly correct with a defect at the edge — **roughly three quarters of it is asking for commands that should not be written**, and a pass that complies produces exactly the artefact this solution exists to prevent, at scale, from the top of the queue. The instruction to work this bucket is therefore not merely unachievable without repo sight; it is pointed at the wrong 18 of every 25 items even with it.

**And the two failure modes compound in the worst direction.** Repo blindness blocks the 7 that are real. Nothing blocks the 18 that are not — those can be "cleared" by any pass willing to write a plausible sentence, and each clearing removes a solution from the bucket, so the queue would report progress precisely as the tree filled with commands that measure nothing. The bucket's counter cannot distinguish the two, which is the same shape as the under-served counter measured this pass on "An opportunity counts as served when its subtree has solutions, not only its direct children" — a queue reporting a gap that is not a gap and instructing the wrong work.

**What this does NOT settle.** The remaining 37 of 62 were not listed by the tool and were not classified; the true proportion across the whole bucket is still unmeasured, and a capped list is not a random sample — it is alphabetical, which is not a reason to think it is unrepresentative but is not a reason to think it is representative either. It also says nothing about whether the 7 mechanical ones are well-specified, only that a command is the right kind of answer for them.

_Method: the 25 titles returned by `ost_next_work`, classified by subject; the shipped class confirmed by reading `status:` from each node's frontmatter; two of the no-command class confirmed by reading the full nodes. Agent self-observation of this vault — it grounds feasibility, not demand. No test was run, no result recorded, and this node's rung is unchanged._

## The census re-done by opening the tests instead of reading the titles — 2026-08-10

**Not a recorded result, and not an independent measurement.** The 2026-08-09 census on this node classified 25 queue entries by the solution's subject and flagged its own weakest point: *"they were classified by subject rather than by opening each node… it is still 14 titles read as titles."* This pass opened twelve of the twenty-five and, for each, read **the assumption test beneath it** rather than the solution — because what an instrument can measure is a property of the test, not of the solution's topic.

**Twelve opened, and none of them wants a mechanical instrument.**

| Class | n | What the test beneath actually asks for |
|---|---|---|
| Already shipped, `status: shipped` read from frontmatter | 3 | Nothing red is possible; the behaviour exists |
| No command by design, stated in the node's own body | 1 | This node |
| A person is the measurement | 5 | Ten buyers, ten practitioners, five operators, two practitioners, operators' felt value |
| **Elapsed calendar time is the measurement** | 2 | "Count previously unseen prompts over a month"; "two unattended weeks — count pages, grind, money" |
| Premise superseded by the product | 1 | "Can a full pass be done with no delete or edit tool" — answered no by building the tools |

**The elapsed-time class is new and the earlier census had no slot for it.** Its three classes were shipped, no-command-by-design, and human preference. A test whose method is *run normally for four weeks and count what stops you* is none of those: nobody is being asked anything, no preference is being elicited, and the product is not finished-and-shipped. It is a question that only calendar time can answer, and it is as unreachable by a spec file as an interview is — for a different reason, which is why it deserves its own name. Two of twelve is a small sample, but it is a class that will never shrink to zero, because a product whose whole claim is about unattended operation over time will keep generating tests shaped like that.

**Where this agrees with the earlier census and where it goes further.** It agrees on the headline — the bucket is mostly not asking for what it says it is asking for — and on the shipped count of three, verified the same way. It goes further in one respect that matters: the earlier census read fourteen titles and *inferred* they were human-preference; opening the tests confirms the inference for the five checked and, more usefully, shows the inference was made at the wrong level. "Nested sub-outcomes between the distant goal and the opportunity space" is a **mechanical** solution — it proposes a schema change — and would be classed as plausibly-instrumentable by subject. Its only test asks whether two practitioners place the same opportunity under the same sub-outcome. Classifying by the solution's topic gets that one wrong in the optimistic direction, which means the earlier estimate of seven plausibly-mechanical entries is an upper bound rather than a centre.

**The consequence for this pass, stated plainly.** This sweep held repo sight — the capability every prior pass recorded as the thing blocking the mechanical remainder — and wrote **zero instruments**, because among the twelve entries it opened there was no test a command could settle. That is a stronger version of the same finding the last three passes reported: the blocker was named as blindness, and with the blindness removed the queue did not yield. Whatever is wrong with `solutionsMissingInstruments` is not repo access.

**What this does not settle.** Thirteen of the twenty-five visible entries were not opened, and the thirty-three the tool does not list have now gone four passes without being classified by anybody. The upper bound of seven is not disproved — only shown to be measured at the wrong level. And nothing here says whether the escape this node proposes is one an operator would want, which is still what its own human-required test is for.

_Method: full reads of twelve node files and their assumption tests in this vault, plus `ost_read_repo` listings of the product suite, 2026-08-10. First-party reads of this vault and of committed code; no command executed, no result recorded, no rung changed._
