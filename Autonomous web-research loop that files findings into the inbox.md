---
type: Solution
status: unvalidated
source: 'human:conversation:2026-07-25'
created: '2026-07-25'
evidence: assertion
---
#Solution #evidence/assertion
[[An autonomous web loop finds things that bear on assumptions the tree actually holds open]]

**Founder's vision:** OST-Agent runs a research loop autonomously, dropping information into its own inbox from the most recent findings it can access on the web. The inbox is already the tree's evidence intake, so research lands in the same channel every other source uses and gets mapped by the normal pass — no new pipeline.

**Shape:** a recurring loop that (1) derives research questions from the tree's current opportunities and open assumptions, (2) searches the web for the freshest relevant findings, (3) files each finding as an inbox note with provenance (URL, date, what question it bears on), (4) lets the existing mapping pass pull them into the tree.

**Key assumptions to surface:** web findings can honestly land above the assertion rung (a cited external source is still not observed customer behavior — rung labeling must resist inflation); the loop can stay relevant to the tree rather than drifting into generic reading; inbox volume stays below what mapping passes can digest; running unattended web research is compatible with the operator's trust constraints ('I can't leave the process running unattended without worrying').

## Definition of done

[[Blind-rate ten dry-run web findings for whether they bear on an open assumption]]

`npx vitest run test/web/research-loop-provenance.test.ts`

The spec asserts the first of the four assumptions this node lists, which is also the only one a machine can hold: every filed finding carries URL, retrieval date and the open assumption it was derived from, and enters at the `assertion` rung **regardless of the host's earned standing**. The node's own words are that "rung labeling must resist inflation", and a loop that could promote what it fetched would be the single most damaging thing to build here. Red today because nothing files findings on a schedule — web reads are operator-initiated and budgeted.

**What a green here does not settle — three of the four assumptions, by the node's own list.** Whether the loop stays relevant to the tree rather than drifting into generic reading is exactly what the blind-rating measures, and no spec can judge relevance. Whether inbox volume stays below what mapping passes can digest is an empirical rate question. And whether running unattended web research is compatible with the operator's trust constraints is a person's judgement — the tree already carries "I can't leave the process running unattended without worrying" as a live need, and a loop that reaches the open internet on its own schedule is squarely inside it.

## History
- 2026-08-05 unlinked [[Blind-rate ten dry-run web findings for whether they bear on an open assumption]] — moved under [[An autonomous web loop finds things that bear on assumptions the tree actually holds open]] — the belief this test measures now has a node of its own
