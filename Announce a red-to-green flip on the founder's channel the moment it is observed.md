---
type: Solution
source: 'INBOX:2026-08-11-observed-build-loop-reports-not-merged-on-merged-prs.md'
created: '2026-08-11'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Highlight interrupts keep their signal — the founder keeps reading them rather than tuning them out]]
[[Every build that lands is announceable, including one whose only prior observation was no-spec]]

When a post-build observation records an instrument going from red to green, send one short push message to a channel the founder already watches, at the moment the flip is recorded — the event, the solution it clears, and where the observation lives.

**Against the alternatives beside it:** this is the immediate, event-granular end of the spectrum. It needs no curation artifact and no digest cadence, and it surfaces the win while the context is fresh. Its risk is the known one recorded for block notifications — interrupts that arrive too often stop being read — and red-to-green flips are rarer than blocks, which is the reason to believe the risk is smaller here. It cannot surface opportunity-kill highlights, because those events do not occur without a human today.

## Definition of done

"A green arriving after a no-spec-only history announces, and a repeat green announces nothing"

```
npx vitest run test/telemetry/build-landed-announcement.test.ts
```

Red today because nothing routes an observed transition to a channel and the spec is unwritten; green when it does and the no-spec-then-green case fires. Written blind of an existing spec, so its first observation files as `no-spec`; the bar above carries a builder.

**One correction to this node's framing, from committed code read this pass.** The detection half already exists: `verifyInstrument` returns `transitioned: true` on a green run of an already-red test. What does not exist is any consumer of it — so the build is smaller than "detect and announce", it is "announce".

**And one defect this node's title would have shipped.** Announcing on `transitioned` alone is silent for a test whose only prior observation was `no-spec`, because `observedRed` deliberately does not match that marker. Since very nearly every instrument on this tree is of that kind, "red-to-green flip" is the wrong event to key on; the event is *a build landing*. The title is left as the author wrote it, but a builder should read the assumption beneath before implementing the title literally.

**This command settles feasibility only.** Whether the founder keeps reading the interrupts is the sibling assumption and stays a person's answer over time.
