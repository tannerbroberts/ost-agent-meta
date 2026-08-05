---
type: Opportunity
status: unvalidated
source: 'agent-run:autonomous-loop-2026-07-25-pass5'
created: '2026-07-25'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Flag a threshold that is still an instruction to choose one]]
[[Refuse to record a result against a threshold that was never fixed]]
[[Make the threshold a field the node carries, not a sentence in its prose]]

**The need (operator's voice):** *"Every one of my assumption tests has a
pre-commitment section, so the tree looks rigorous. Then I go to run one and the
pre-commitment says 'fix the minimum number before starting'. Nobody fixed it. So
whatever comes out, I can read as a pass — and I will, because I want to build the
thing."*

**How this surfaced, with numbers.** v0.9.0's threshold extractor was run over both
live vaults before it shipped. It is a mechanical reading of what is actually in the
node bodies:

| | assumption tests | threshold extractable | contains a number or a bound |
|---|---|---|---|
| ost-agent-meta | 77 | 65 | 57 |
| tetrix-ost | 27 | 27 | **4** |

`tetrix-ost` is the sharp case: **21 of 27** of its extractable pre-commitments open
with *Fix…*, *Decide…*, *Choose…* — they are instructions to pre-commit, standing in
where a pre-commitment should be. This vault is in much better shape (57 of 65 carry
a number or a bound), which is itself informative: the same agent wrote both, and the
difference is that this tree's tests were mostly drafted alongside a specific
disconfirmer while the sibling's were drafted in bulk during ideation.

**Why it matters more than it looks.** The believability ladder, the evidence-debt
gate, and v0.8.0's coverage field are all machinery for making a claim refutable. All
of it sits on top of a threshold that a human wrote before looking. If that threshold
is "decide a threshold", the whole stack is enforcing paperwork around a bar that
does not exist — and the failure is invisible, because every mechanical check passes.
`debt` counts the pair; `gate` clears on any recorded result; nothing has ever asked
whether the thing pre-committed to was a commitment.

**Litmus test (more than one way to address it):** flag the unfixed ones, refuse a
result against one, move the threshold out of prose into a field the tool can require
at creation, or leave it entirely to review. Passes.

**Caveat for a human, and it is a real one.** The distinction between "a threshold"
and "an instruction to set one" is fuzzy, and the cheap mechanical version of this
(does the sentence start with an imperative verb) will be wrong at the edges. A rule
that nags about well-written thresholds gets turned off, and then the genuinely empty
ones come back with it. Whatever gets built here should be a *report* before it is
ever a *refusal* — which is the order [[Flag a threshold that is still an instruction to choose one]]
and [[Refuse to record a result against a threshold that was never fixed]] are
deliberately proposed in.

**Provenance:** agent-origin — a fact about two vaults inside this building,
mechanically checked, not a sentence from any user. It sits at the `assertion` floor
for the same reason everything else does, and it is another instance of the hole
[[A Context node type for evidence that is true, useful, and not a customer need]]
describes: verified fact about our own system, weighted like founder theory.

## History
- 2026-08-05 unlinked [[Do named unfixed thresholds actually get fixed]] — not a parent-child relation the OST hierarchy supports — every tree walk counted it as structure, so a cross-reference read as a child
