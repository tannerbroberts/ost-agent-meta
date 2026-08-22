---
type: Assumption
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**Efficacy belief, and the one that decides whether this candidate is worth building at all:** when a measured claim on this tree stops being true, the thing that made it stop is usually a record the vault subsequently ingested.

It held for the originating instance — the 2026-08-16 census was falsified by a transcript captured the next day, and an ingest-time tripwire would have named it within the hour. One instance is not the rate.

**Why it might be false.** Plenty of claims here rest on things ingest never touches: a config value changed by hand (the `product.repos` line, which invalidated a bar's stated remedy without producing any record), a shipped code change, a grant table edited outside the vault, or a claim that was simply wrong the day it was written and never had a falsifying record to wait for. If those are the majority, a tripwire at ingest catches the tail and the operator still cannot read an unflagged claim as current — which leaves this candidate solving the visible instance and not the need.

Note what this assumption is *not* about: whether the check can be built (that is the sibling assumption beside it) or whether an operator would act on the flag. It is about the population of stale claims, and it is answerable only by looking at claims that have already gone stale here.
