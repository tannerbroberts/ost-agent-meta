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

## The census, updated by a sighted pass — 2026-08-10 (not a recorded result)

**This node's premise no longer describes this surface, and the outcome did not change.** The 2026-08-10 unattended sweep had `ost_read_repo` and read `examples/automation/autonomous-pass.sh` and `test/` in full. It wrote **zero** instruments for the 58 queue entries anyway. That is the single most useful thing this pass can report about this node: repo sight was the stated blocker for six passes, it has now been granted to an unattended firing, and the queue did not move. The exchange rate this node called unknown has one data point, and it is not the one the node predicted.

**Two rows classified by opening the test rather than reading its title**, which is the method the earlier census admits it lacked:

- *"Take up independent work while a check is outstanding"* — its test is "Count how much post-handoff work in past sessions would have survived a failing check", tagged `#desirability`, threshold "at least half the work identifiable as independent would have survived a failing verdict untouched, across at least five recorded waits including two that failed." The replay is over a corpus that exists, so it looks mechanical — but the quantity being counted is *which steps genuinely did not depend on a pending verdict*, and that is a judgement per step. A spec asserting a share would be asserting the labelling somebody chose. Class: `people`, and instrumenting it would launder a judgement into an exit code.
- *"The tally is kept and the second occurrence is met with the count, not the correction"* — its test's threshold is two clauses: "the counter fires by the second occurrence in both replays" (mechanical, against a corpus that exists) **and** "3 of 5 live sessions change approach rather than retrying" (people). The node's own prose says exactly this. An instrument settles the first clause and cannot touch the second, so the exit code would clear a gate on half a bar. Per the ruleset's own rule, the repair is to split the test, which is a structural change to somebody else's node and not an unattended pass's call. Class: split — and the class set in "What is in the 33 queue entries no tool has ever listed" has no row for it, which is itself worth knowing.

**What that suggests about the remaining rows, stated as an expectation and not a measurement.** The queue's alphabetical head is disproportionately commercial and the unlisted tail disproportionately mechanical-looking — but both rows opened above *looked* mechanical from their titles and neither was. Two of two is not a rate; it is a warning that title-proxy classification of this queue reads high.

**What this does not settle.** Whether a *sighted* pass could write good instruments for the rows that are genuinely mechanical — it found none in the two it opened, having spent its reads on enumeration instead. And nothing about the sibling proposals here: this is one firing's experience, not a comparison between them.

## Repo sight is not one capability, and a pass can hold part of it — 2026-08-10, later firing (not a recorded result)

**No test was run.** This is one firing reporting the shape of its own grant, because the section above rests on a claim about exactly that and the claim is narrower than it reads.

**What the section above asserts.** That "the 2026-08-10 unattended sweep had `ost_read_repo`", read `examples/automation/autonomous-pass.sh` and `test/` in full, and wrote zero instruments anyway — offered as the decisive data point that "repo sight was the stated blocker for six passes, it has now been granted to an unattended firing, and the queue did not move."

**What this firing observed, which qualifies it.** This vault's transcript channel captured that sweep's own session record this pass, as `TRANSCRIPT:79a96b5a-9874-4507-9175-b285b601eb24`, and its three friction events include one `tool_error`: a `Glob` against `/Users/tanner/dev/OST-Agent` refused with *"Claude requested permissions to read from /Users/tanner/dev/OST-Agent, but you haven't granted it yet."* This firing then hit the identical refusal on the identical path.

Both facts can hold at once, and that is the finding: **`ost_read_repo` and the built-in file tools are separate grants over the same directory.** A pass can read the product through the metered MCP surface while being refused the same bytes through `Glob`, and it discovers which by attempting one. So "the sweep held repo sight" is true of one path and false of another, and a node reasoning about whether blindness is the blocker should not treat repo sight as a single switch. That is this node's own subject — it proposes gating instrument-writing on a capability — and a capability that comes in separable pieces is one a gate has to name precisely or will check the wrong half.

**This firing's brief disagreed with itself about the same grant**, which is worth recording beside the above. One paragraph told it three read-only senses were now on the surface and named `ost_read_repo` among them; a later paragraph told it the unattended sweep holds no outward-sensing grant on purpose and named the same three tools as attended-path only. The firing followed the prohibition and did not attempt the tool, so it cannot report whether the grant was live — only that the instruction was ambiguous and it resolved the ambiguity conservatively. For a human: the two paragraphs want reconciling, and until they are, each unattended firing spends reasoning deciding which sentence governs.

**Zero instruments again, and this time for a reason worth separating from blindness.** The queue stood at 58 — unmoved from the previous firing. This pass wrote none, and not because it could not see the repository: it declined because an instrument written without reading the code can only name a spec path that does not exist, and the ruleset's own measurement is that such a run is filed `no-spec`, mints no permit, and is indistinguishable from every other unwritten question — 260 of this tree's 266 recorded reds are "No test files found". Writing 58 more would move the queue to zero while adding 58 commands that measure nothing, which is precisely the failure this node names: *"those can be 'cleared' by any pass willing to write a plausible sentence… so the queue would report progress precisely as the tree filled with commands that measure nothing."* The queue's counter cannot tell the two apart, so the counter is not the thing to optimise.

**What this does not settle.** Whether `ost_read_repo` was in fact live on either firing — neither attempted it under a brief that forbade it, and the earlier one's claim to have used it is its own report. Whether the separable-grant finding generalises beyond this machine's permission model. And nothing about the sibling proposals, which remain uncompared.

_Method: this firing's own tool results, plus a full read of `TRANSCRIPT:79a96b5a-9874-4507-9175-b285b601eb24` through `ost_next_work`. Agent self-observation — it grounds feasibility, not demand. No command executed, no result recorded, no rung changed._

## The head is now closed too, so the whole queue is classified — 2026-08-10, later firing (not a recorded result)

**No test was run.** This is the missing half of a count this node has carried four times. The tail was closed on the unknown "What is in the 33 queue entries no tool has ever listed" at `mechanical` = 0 of 33. The head — the 25 the tool prints — had never been finished: 25 classified by subject on 2026-08-09, 12 opened on 2026-08-10, **13 never opened by anybody**. Those 13 are now classified.

**The whole 58-entry queue contains zero entries asking for a spec file.**

| | people | elapsed-time | shipped | no-command | premise-superseded | split | **mechanical** |
|---|---|---|---|---|---|---|---|
| head (25) | 15 | 3 | 5 | 1 | 1 | 0 | **0** |
| tail (33) | 25 | 4 | 2 | 0 | 0 | 2 | **0** |
| **58** | **40** | **7** | **7** | **1** | **1** | **2** | **0** |

**The shipped class is verified rather than inferred, and it is bigger in the head than any pass has recorded.** One grep for `status: shipped` across the vault returns ten solutions; **five of the ten are in the visible 25** — "Refuse a proving command whose exit code cannot report failure", "Refuse a wiki-link that contains a newline", "Refuse a write whose content is empty or literally undefined", "Post-session transcript harvester", and "A result must state what it did not cover". The other five are absent from the queue for the ordinary reason: their tests carry instruments. So `status: shipped` does not exclude a solution from this bucket, and the 2026-08-05 repair that set the first of those to `shipped` has now failed to remove it on six consecutive passes.

**The strongest mechanical-looking entry in the head was opened and is not mechanical.** "Settle the standing answers once, in committed configuration the run inherits" proposes committed configuration — a schema change, mechanical by subject. Its only test, "Settle the known prompts as config and count how many new ones appear in a month", has the threshold *"At most 2 previously unseen prompts stop a run in the month"* and the design *"run normally for a month and count how many previously unseen prompts stop a run."* Class `elapsed-time`. That is the third consecutive time the title-proxy method has read a queue entry as mechanical and the test has said otherwise, and it is now 3 for 3 in the optimistic direction.

**An independent derivation of the uninstrumented set, which agrees.** Two multiline greps over frontmatter — tests whose last key is a plain scalar, and tests whose last key is a `threshold:` block — return 35 and 25 files, **60 tests carrying no `instrument:`**. Against the arithmetic total of 73 (351 tests minus 278 with instruments), 13 tests have a frontmatter shape neither pattern catches and were not enumerated here. So this is a floor of 60 of 73, not a complete census of tests — but every one of the 60 was classified, and none is mechanical.

**What this changes for the instruction.** Every prior pass framed the blocker as capability: repo sight, then built-in file access. Both have now been held by a firing, and the count did not move, because the queue's composition is the constraint. The bucket's instruction — "declare an `instrument:` (one spec file that fails today and passes when the solution is built)" — is not merely hard to satisfy on most entries; on this measurement it is satisfiable on **none of the 58**. A pass that reports progress against it is writing commands that measure nothing. The repair belongs entirely to the queue's derivation and not to any solution beneath it.

**What this does not settle.** Twenty-three of the tail's 33 and roughly half of the head's 25 rest on their test's *title*; the two `split` rows already prove a threshold can hide a clause a title does not show, so `mechanical` = 0 is a measurement with a known blind spot rather than a proof. The 13 unenumerated tests are unclassified. Nothing here says whether any of these tests is well designed, and nothing was executed.

_Method: `Read`/`Glob`/`Grep` over this vault, plus `ost_read_repo` reads of `test/`, `test/ost/` and `test/ost/instrument.test.ts` in the product. First-party throughout; no command executed, no result recorded, no rung changed._

## The queue grew 58 → 67, and the nine new entries do not change the zero — 2026-08-10, eighth firing (not a recorded result)

**No test was run.** The complete census above closed the 58-entry queue at `mechanical` = 0. This firing found the queue at 67 and classified the growth rather than re-counting the whole.

**The new entries are the 2026-08-10 founder-theory batch.** A vault grep for the `goal-acquisition`/`axioms` tags returns the whole family: six new solutions (the proof lane, the autonomy ledger, three axiom-register variants, and unattended feasibility tests) under two new opportunities, with four assumption tests beneath them. Every one of the four tests was read or frontmatter-checked this firing: **all four already carry `lane: humans-required`**, set at creation — "Present the founder three derivations…" names the founder as irreducibly the measurement, and the other three ("Import ten doctrine axioms…", "Seed five axiom asks…", "Hold one 30-minute axiom-writing session…") name the founder or the ask-queue's human. The two solutions read in full ("A proof lane where derivations from declared axioms count as evidence", "An autonomy ledger that widens permission as staked claims survive their instruments") each rest on an assumption whose title names a person's willingness. Class: `people`, all of them.

**So the composition finding extends to the 67.** The nine new entries are correctly-laned human-required work listed as instrument debt — the exact defect the 2026-08-07 Issues entry on this node recorded on the day it was created, now reproduced at batch scale: a test created with `humansRequired` still surfaces its solution in `solutionsMissingInstruments` on the next sweep. This firing held repo sight (`ost_read_repo` answered on this surface for the first time — root and `test/` were listed) and wrote zero instruments, because there is still nothing in the queue an instrument can settle. The blocker was never sight; it is the queue's derivation, and the repair still belongs to "Work I already finished keeps coming back in the queue, so the pass can never say it is done" and to excluding humans-required-laned tests from the bucket.

**What this does not settle.** The tail's unlisted 42 were not re-enumerated; this classifies the family the growth came from, verified by frontmatter on the four tests, not every hidden entry individually. And nothing about whether any of the four human studies is well designed.

_Method: `Grep`/`Read` over this vault's own files plus full `ost_read_tree` reads of two new solutions and one new test; `ost_read_repo` root and `test/` listings. First-party; no command executed, no result recorded, no rung changed._

## The growth 67 → 70 is the highlight family, and the zero holds — 2026-08-11, unattended sweep (not a recorded result)

**No test was run.** `solutionsMissingInstruments` stood at 70 this firing, up three from the closed census at 67. The three new entries are the 2026-08-11 highlight family: "A highlight criteria note the founder edits and the loop reads before deciding what to surface", "A highlights digest distilled from what vault history already records", and "Announce a red-to-green flip on the founder's channel the moment it is observed".

**All three tests carry `lane: humans-required`, set at creation and read from frontmatter this firing.** "Seed a one-line criteria note and see whether the founder edits it within two weeks", "Hand the founder a digest built from last month's history and ask what it missed", and "Send flip announcements for two weeks and count which ones the founder reacts to" each name the founder as irreducibly the measurement — his edits, his named misses, his reactions. Class: `people`, all three. `mechanical` remains **0 of 70**.

**Repo sight was live on this surface and it changed nothing, again.** This firing probed `ost_read_repo` before touching the queue and it answered — `test/` listed in full on the first call. Zero instruments were written, for the composition reason the census already established, not for blindness: the queue still contains nothing an exit code can settle, and the batch-scale defect recorded on 2026-08-10 — a test created `humansRequired` still surfaces its solution in this bucket on the next sweep — has now reproduced on a third consecutive family.

**What this does not settle.** Whether the highlight family's three human studies are well designed, and nothing about the queue's unlisted tail, which was not re-enumerated.

_Method: frontmatter reads of the three new tests and their solutions in this vault; `ost_read_repo` listing of `test/`. First-party; no command executed, no result recorded, no rung changed._
