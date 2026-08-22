---
type: Solution
source: 'agent-ideated:2026-08-17-unattended-sweep'
created: '2026-08-17'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A single fixed per-run friction-count threshold separates sessions worth the operator's attention from ordinary recoverable noise]]
[[A candidate threshold's would-have-fired verdict is computable from friction records already stored]]

Most runs recover from a couple of retries without it meaning anything; the interesting case is the run that fought through nine. Rather than reporting every run's count, only surface a message when one run's tool_error/retry count crosses a pre-set bar — the operator hears about the outlier and nothing else.

**Compared to the alternatives.** Unlike a per-run summary, this respects attention: silence is the normal case, and a message means something actually happened. Unlike a trend view, it catches a single bad run immediately rather than waiting for a pattern to accumulate.

**What would make this the wrong pick.** The threshold is a guess with no data behind it yet — set too low and it is noise again, set too high and the run that quietly degraded over time never crosses it in any single session. It also can't see a slow drift: ten runs at just-under-threshold friction look identical to ten clean ones.

## Definition of done

"Every stored friction record is labelled fired or not-fired at each candidate bar, with none left unlabelled"

```
npx vitest run test/friction/threshold-sweep.test.ts
```

Red today because nothing sweeps candidate bars over stored records and the spec is unwritten; green when the sweep exists and reports its own denominator. Written blind of an existing spec, so its first observation files as `no-spec`; the bar above is what carries a builder.

**Order of work, which this node did not previously state.** This command is a *prerequisite* for the human study, not an alternative to it. The sibling assumption's test — "Show the operator a handful of recorded sessions and the threshold's would-have-fired verdict, and ask which they'd have wanted alerted" — cannot be assembled until something computes those verdicts. That ask has been sitting in `outstandingAsks` unanswerable for want of a mechanism nobody had named.

**This command settles feasibility only.** A green says the verdicts can be produced. It says nothing about whether any single bar is the right one, which is exactly the guess this candidate's own prose flags as having no data behind it.
