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
