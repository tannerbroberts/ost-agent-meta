---
type: Solution
status: unvalidated
source: 'agent-ideation:autonomous-loop-2026-07-25-pass5'
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Check whether the threshold field gets a bound or just the same wrapped prose]]

**The idea.** An assumption test carries its threshold as frontmatter — a named field
set when the node is created — instead of a bold lead-in somewhere in the body. The
tool then reads it rather than finds it, and a test created without one is visibly
incomplete from the moment it exists.

**Approach.** `ost_create_node` takes the threshold for an AssumptionTest; the
extractor keeps working for every node written before the field existed, exactly the
way v0.8.0's coverage check treats older results as unbounded rather than as errors.

**How it differs from its siblings.** The other two treat the prose as given and get
better at reading it. This one changes what a node *is*, so the question stops being
askable. It is the only one that fixes the cause rather than the symptom — and the
only one that touches the append-only substrate, which is why it is the most
expensive and the most likely to be wrong.

**Why it might be wrong.** Prose is doing real work in these nodes. The best
thresholds in this vault carry their reasoning inline — *">= 2 incidents beyond the
known one, else defer (this solution already ranks itself last among its siblings and
questions its own existence)"* is a threshold and an argument in one sentence, and a
field would either truncate it or become a paragraph in a different place. There is a
real chance this trades a readable tree for a parseable one, which is the wrong
direction for an artefact whose whole purpose is to be read by a person.

**Also worth naming:** the extractor found 65 of 77 thresholds in this vault and 27
of 27 in the sibling, against prose that was never written for it. That is a decent
argument that reading is working well enough and the cause does not need fixing.

**Size:** days, not an afternoon — a schema change, a tool-surface change, a
migration story for 104 existing tests, and a docs change.

⚠️ Unvalidated. Proposed by an agent, and proposed as the *least* likely of the three
to be right — recorded so the option is on the table rather than because it is
recommended.

## Issues
- 2026-08-01 SHIPPED 2026-08-01 (sixteenth pass), scoped to the additive half only.
  [tannerbroberts/OST-Agent#29](https://github.com/tannerbroberts/OST-Agent/pull/29),
  merged to `main` as `4edcc6c`; on the `Unreleased` line in `CHANGELOG.md`, not yet
  published to npm. `ost_create_node` accepts `threshold` for a new AssumptionTest
  (refused for any other layer); `askedOf` reads it first and falls back to the
  existing prose scan when it is absent — none of the 91 tests already in this vault
  changed classification. The migration this node's own Size line named ("days, not
  an afternoon... a migration story for 104 existing tests") was **not built and is
  not needed**: the Approach section's own fallback design makes it optional, not a
  precondition, and building it anyway would have been the destructive, expensive
  half this node itself flagged as "the most likely to be wrong." **The "why it might
  be wrong" risk stands, unaddressed by choice:** a field cannot carry inline
  reasoning the way *">= 2 incidents beyond the known one, else defer"* does, and
  nothing in this build stops a future test from truncating a real argument into a
  bare bound. The field is optional precisely so a test whose threshold needs
  argument, not just a number, can keep using prose. Follow-on, not yet run: does a
  test written with the field actually avoid the line-wrap misread in practice, or
  does whoever fills it in just re-paste the same hard-wrapped prose into the field.

## Definition of done

[[Check whether the threshold field gets a bound or just the same wrapped prose]]

```
npx vitest run test/ost/threshold-field-bound.test.ts
```

Green means a threshold field parses to an actual bound — a comparator and a number — so a test carrying one can come out a failure. This is the mechanism behind the tree's own standing complaint that nothing can fail. It does not settle whether the bound anyone writes is the *right* bound, and moving prose into a field does not make a badly chosen number good.
