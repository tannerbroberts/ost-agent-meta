---
type: Solution
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: what it measures — the kind of spec, classified before anyone runs it.** Two specs can both be `npx vitest run <file>` and mean opposite things by their red. A *permit* spec asserts behaviour that does not exist yet; red means "not built", green means "built". A *replay* spec runs recorded data through existing code against a pre-committed bar; red means "the hypothesis lost", and there is nothing to build that would turn it green without loosening the bar — which the builder in the observed case correctly refused to do. The loop treats every instrument as the first kind. This candidate lets an instrument declare itself the second (`instrument-kind: replay`, or inferred from the spec importing a recorded-sessions fixture), and `verify` files a replay red as `**refuted**` rather than `**red**` — an observation that is a finding, and that `buildable` does not read as a permit.

**The idea.** `src/ost/instrument.ts` already files three observation kinds and keeps `no-spec` out of the permit path precisely because "both look like exit 1 and only one of them is a test". A fourth kind follows the same reasoning: a replay red and a permit red both look like exit 1, and only one of them is a definition of done. Classification, not judgement — the spec's own imports say which it is.

**Against its siblings.** The only candidate that fixes the *vocabulary* rather than adding a counter ("After two builds…") or a channel ("The builder files…"). It also helps discovery at write time: a pass proposing a replay-style test knows, when it sets the instrument, that it is commissioning a measurement, not a build — and can say so in the test's prose.

**Where it fails, stated so it can be judged.** Classification from imports is a heuristic and a spec can be both (set up a fixture, replay it, assert a new code path). A replay spec that is red because the *replay harness* is unbuilt — the first firing on #130 built `STOP_COUNT_RULE` before the replay could run — is a permit red until the harness exists and a finding red after; one spec, two phases, and the classifier has to know which phase it is in.

**Cost.** One observation kind, one frontmatter field or import heuristic, and a `buildable` that reads `refuted` as not-a-permit.
