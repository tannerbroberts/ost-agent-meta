---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** A replacement records the command it displaced alongside the observation that command had earned. If the original command is later set again, the observation it held is re-associated rather than gone.

**Why this shape.** It is the only candidate that addresses the damage that has already been done. On 2026-08-07 a good instrument was replaced and then restored one call later — the string came back and the permit did not, and no call on that surface could bring it back. Prevention arriving tomorrow does not undo that, and there is no reason to think it is the last time.

The safety argument is narrow and worth stating precisely: re-arming is only legitimate when the restored command is byte-identical to the one the observation was made against. That is the same principle the un-clearing rule rests on — a verdict belongs to a command, not to a test — and it is why this is a bookkeeping fix rather than a loosening.

**How it compares to its siblings.**
- "The sweep reports which tests already carry an instrument" and "Attaching an instrument to a test that has one is refused unless replacement is declared" both try to stop the write. Both leave every already-lost permit lost.
- This one stops nothing and would not have prevented the observed error. It is a complement, not an alternative, and it is the weakest of the three if only one can be built.

**Where it fails, stated so it can be judged.** It reintroduces, in a small way, the thing the un-clearing rule exists to prevent: a permit surviving a period in which the test carried a different command. If anything about the repository changed in between, re-arming hands back a verdict that was earned against different code, and byte-identity of the command does not establish identity of what it measured. That is a genuine hole and it is the assumption beneath this node.

Second failure worth naming: this makes replacement cheaper, and cheaper replacement is more replacement. A guard that makes the destructive act recoverable can raise how often it is attempted.

**Cost.** A history of prior commands per test, and the re-association rule. Largest of the three, and the only one that touches how permits are stored.

⚠️ Unvalidated. Agent-ideated by the surface that caused the loss it is proposing to make recoverable, which is a reason to trust the observation and discount the conviction.
