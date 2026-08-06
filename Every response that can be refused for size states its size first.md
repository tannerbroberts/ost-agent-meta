---
type: Solution
source: 'TRANSCRIPT:28d14def-76a2-4bbb-bd55-6f9b80c8ca8c'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A response cannot be sized more cheaply than it can be produced, so stating the size first buys nothing]]

**The idea.** Any call that can be refused for exceeding a response limit can first be asked what it would cost. A cheap probe returns the count or byte size the full call would produce, so a caller chooses a narrower call instead of discovering the cap by hitting it.

**Why this shape.** Two independent sightings of the same wall from opposite directions: `ost_read_tree` returning 134,240 characters and being refused for it, with the size discoverable only by asking; and session `28d14def` having a Read refused at 73,874 tokens against a 25,000 cap. In both there was a cheaper call available to a caller who knew the size in advance, and in both the only way to learn the size was to spend the turn.

**How it differs from its siblings.** The narrowest of the three and the only one that survives the objection to the other two. A manifest can state that a cap exists but not whether this particular call is over it — the number is a property of the data, not of the rule — and a cap cannot be auto-satisfied, because shrinking a response means deciding what the caller does not get to see. Disclosure is the only remedy that leaves the choice with the caller.

**Trade-off.** It adds a call to the common path: a careful caller now probes before reading, which costs a turn to save a turn and is a net loss whenever the response would have fit. That is avoidable if the size travels on responses the caller already makes rather than on a separate probe, which is the version worth building if the assumption beneath this holds.

**Where this fails.** It helps only where the caller has a narrower call to fall back on. A read of one large file has no smaller form, so the probe converts a refusal into a forewarned refusal and saves nothing but the surprise.

⚠️ Unvalidated. Agent-originated, first-party observation of this product's own surface.
