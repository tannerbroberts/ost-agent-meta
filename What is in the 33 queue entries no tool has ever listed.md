---
type: Unknown
source: 'agent-ideation:2026-08-10-unattended-sweep'
created: '2026-08-10'
evidence: assertion
---
#Unknown #unvalidated #evidence/assertion

`solutionsMissingInstruments` holds 58 entries and `ost_next_work` prints 25 of them, alphabetically. The same 25 have appeared on every sweep since 2026-08-06. Four passes have now classified some part of the visible head — 25 by subject on 2026-08-09, 12 by opening their tests on 2026-08-10 — and **not one of them has ever seen the other 33**. Every claim this tree makes about the queue's composition is a claim about its alphabetical head, extrapolated.

That is the darkness. It is not "we have not got round to it": no surface available to a sweep can enumerate them. The tool caps at 25 by design, and the derivation that produces the list — a solution none of whose assumption tests carries an `instrument:` — is not something the vault's own files answer in one read, because it needs two hops through the wikilink graph, from solution to assumption to test.

## Format

A table of 33 rows. Each row: the solution's title, its `status:`, and one class from the set the head has already produced —

- `shipped` — the behaviour exists, so no command can be red
- `no-command-by-design` — the node's own body says an instrument would be laundering
- `people` — a person outside the building is the measurement
- `elapsed-time` — only running for weeks or months answers it
- `premise-superseded` — the product has answered the question by moving on
- `mechanical` — a spec file could settle it, and the bucket is right about this one

The count of `mechanical` rows is the answer this unknown exists to produce. Anything else it turns up is a bonus.

## Methodology

Two routes, and the first is cheap enough to try first.

*From the vault.* Enumerate every `type: Solution` file, follow its `[[…]]` child edges to the assumptions beneath it, follow those to the assumption tests, and select the solutions where no test carries an `instrument:` field. This is a whole-vault read plus two hops and needs no repository access. It reproduces the tool's own derivation, so it also serves as a check on it — a disagreement between the two lists would itself be worth knowing.

*From the tool.* Raise or page the 25-item cap on `solutionsMissingInstruments`. That is a product change and belongs to whoever owns the response-size budget; the vault route does not wait on it.

Either route produces the titles. Classifying each still needs the node opened and its test read, which is what the 2026-08-10 pass did for twelve and is the expensive half — roughly one full read per row.

## Rationale

**What it darkens.** "A pass that cannot see the repository cannot set an instrument at all" carries this tree's census of the instrument queue, and that census states its own limit in its own words: the unlisted entries "were never classified by either, both read titles as a proxy for the majority class". It also darkens the assumption "Every solution in the current backlog has an existing spec that could go red for it", whose threshold is stated over 61 backlog solutions and cannot be evaluated against a backlog nobody can list.

**What would change if it were answered.** The estimate of how much of the queue is genuinely mechanical is currently an upper bound of seven, derived from the head and shown on 2026-08-10 to be measured at the wrong level. If the 33 are mostly mechanical, the queue is roughly right and repo sight was the blocker after all — which the 2026-08-10 sweep's zero instruments argues against, but only over the head. If the 33 look like the head, the bucket is mostly asking for commands that should not be written, and the repair is to the queue rather than to any solution beneath it. Those two answers point at different builds, and nothing currently distinguishes them.

**Why it is worth naming rather than absorbing.** Four consecutive passes have each re-derived "I can only see 25" and moved on. Written down, the gap is costable — 33 reads — instead of being rediscovered every sweep at the price of the rediscovery.

## Enumeration — 2026-08-10, Methodology route 1 executed (no Answer yet)

**Not the Answer.** The Format wants 33 rows each carrying a class, and this pass resolved the *titles* rather than the classes. `## Answer` stays unwritten on purpose. What follows is the enumeration half, done, plus the arithmetic that shows it is not a guess.

**The surface that made it possible.** This sweep was granted `Read`, `Glob` and `Grep` over the vault directory — three built-ins the automation script grants no one deliberately, recorded separately under "Account for every reachable built-in in one list or the other, and fail the build on an unlisted one". Four earlier passes reported this route unavailable and were wrong about their own surface: the whole-vault read the Methodology asks for was reachable the entire time. That is the cheaper finding of the two.

### A derivation that removes most of the cost

`ost_next_work` emits `solutionsMissingInstruments` **alphabetically**, and caps at 25. Confirmed against this firing's own output: the 25 run "A pass that cannot see the repository…" → "Ship a starter vault whose outcome is a placeholder the human must replace" in strict alphabetical order. Therefore the 33 unlisted entries are not a random tail — they are **exactly the queue members that sort after "Ship a starter vault…"**. No enumeration is needed to know where they live.

Filtering the vault's 336 `type: Solution` files to titles sorting after that point leaves **66 candidates**, of which 33 are in the queue. The search space is halved by an observation about sort order, costing one grep.

### The 73 uninstrumented tests, derived exactly

- 351 files carry `type: AssumptionTest`.
- 278 files carry an `instrument:` field.
- Sequentially diffing the two listings (identical traversal order, so the diff is a single walk) yields **73** tests with no instrument.
- **Arithmetic check: 351 − 278 = 73, and the walk independently produced 73.** The two agree, which is the check the Methodology hoped for — the vault route reproduces the tool's own derivation rather than a second opinion about it.

Twenty-eight of the 73 sit scattered through the listing:

Five operators choose between sixty-one weak instruments and sixty-one blanks · Five-minute orientation task on a static mock · Blind-rate ten instruments for groundedness and compare against whether their pass had repo sight · Show five operators a pass's dismissed-work list and ask whether they would have let it stand · Test can a full pass be done with no delete or edit tool · Hand-compute unblock counts and see if the operator's pick changes · Test can teams define a real-world outcome signal for the gate · Run the refusals section for two weeks and count the mornings it changes anything · Ask ten practitioners whether their own discipline has ever failed them, before naming any mechanism · Ask ten PMs to recount the last time they were asked how they knew, and what they showed · Ask ten buyers what happened the last time a tool they relied on shut down · Ask ten buyers to split a test's price between designing it and running it · Do two practitioners place the same opportunity under the same sub-outcome · Does a route view change which work a builder picks up first · Sweep both vault histories for writes that landed as undefined or empty · Show the operator ten forks already taken and count the reversals and the minutes · Show readers a degraded run report and see whether they notice · Judge the eighteen reopened items — were they genuinely finished · Install the package on ten stock setups and see whether postinstall ever gets to speak · Does the side-by-side change what a reviewer does about a threshold · Does a placeholder outcome get replaced, or does it become the tree's real root · Do the shipped sweeps actually find a planted instance · Do named unfixed thresholds actually get fixed · Cold-offer test - will outside teams hand over real discovery work · Ask five prospective operators whether they would let their vault report outward · Ask five operators whether they would let a stated default stand while they are away · Replay the three recorded failed runs through the journal-alert rule on paper · Apply the escalating message to the five-failure session and check where it would have fired

The remaining 45 are one contiguous run at the end of the listing: Deliver three free trees… · Publish six pieces over six weeks… · Rewrite the shortest helper against the bundled runtime… · Settle the known prompts as config… · Have authors nominate a riskiest assumption… · Check what would actually have to be redacted… · Withhold the agent's answer on ten forks… · Queue forty drafts for approval… · Give a cold session only the tree… · Interview ten solo builders… · Sell one engagement… · Offer a maintained tree at a stated monthly price… · Run the checks over three hand-built vaults… · Have a second person run the hand arm… · Run one small corpus through both… · Pitch the refusals to ten prospects… · Follow a candidate source list for a month… · Group the harvested tool errors by hand… · Set up one scheduled export… · Count how many of the operator's real experiment sources can push anywhere at all · Replay ten past runs and count how many needed a scope nobody would have predicted · Have five authors preview a write… · Hand-label the gated rows… · Count how much post-handoff work… · Would an operator accept the agent living inside the vault it maintains · Hand a reader five run records… · Does the guard catch real laundering without refusing honest commands · Does showing the whole sentence change what a reader does with a paste-ready command · Does refusing a newline inside a wiki-link catch breaks nothing else catches · Pre-order probe - will anyone pay before the map proves itself · Does a forced uncovered field change what a second reader believes · Two unattended weeks - count pages, grind, and money burned · Time one real week of decisions through the docket from a phone · Five-second status glance test after a failed run · Diff three past sessions' claims against their traces by hand · Two-week recruiting test for interview supply · Would operators accept unattended self-modification · Unprompted-fear interviews about leaving it running · Test humans can promote while the agent is blocked from validating · Test does the weekly digest make operators willing to walk away · Test do operators get value with remote push off · One re-synthesis pass with human accept-reject · Hand-distil three past sessions · Can a builder work from the map without ideating · Backdated half-life comparison for staleness flags

### What the head hides, which is the part worth acting on

The alphabetical head is **not** a representative sample, and the tree's existing census — which extrapolated from it — is skewed by that. Roughly half the visible 25 are commercial: pricing, positioning, cold offers, interview supply. In the 66-candidate tail that proportion collapses; the tail is dominated by product mechanisms — leases, watchdogs, typechecks, schema validation, workspace reconciliation, queue behaviour. So the honest expectation reverses: the existing upper bound of seven `mechanical` rows was measured on the least mechanical half of the queue.

That does **not** license raising the estimate. Every attempt this pass made to place a specific tail solution in the queue by matching a test to it by subject was wrong often enough to distrust: three checks that looked certain (a starter-vault sibling, an unrun-test accounting solution, an actor-partition solution) turned out to have an *instrumented* test after the edge map was read, so they are not queue members at all. Title-proxy matching fails in exactly the direction that would inflate a mechanical count.

### What remains, priced

The two-hop edge map for every tail-named file is now read, so solution → assumption is settled for all 66 candidates. What is still owed per row is one hop: the assumption's own test, for assumptions whose titles fall outside the S–Z listing. That is roughly **30 single-file reads of about 12 lines each** — a tenth of the "one full read per row" this node originally priced, because the classification only needs the test's title and threshold, not the solution's prose.

A pass with `Bash` closes the whole thing in one command instead, and should: the derivation above is a shell one-liner over the vault, and re-deriving it by hand cost this firing six tool calls plus a careful manual diff.
