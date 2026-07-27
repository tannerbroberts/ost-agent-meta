---
type: Solution
created: '2026-07-27'
evidence: assertion
---
#Solution #evidence/assertion

**The idea.** Any sweep whose subject count is zero exits non-zero and says so, rather than reporting zero findings. "I looked at nothing and found nothing wrong" stops being expressible.

**Precedent already in the codebase.** The tetrix CORS sweep does exactly this — it guards against reading nothing, because a sweep over a moved directory would otherwise pass vacuously. The v0.17.0 schema check does the companion version: a test asserts every allowlisted tool declares a readable schema, because a validator with nothing to check reports the same "0 problems" as one that checked everything. The pattern is already believed here; it is just not systematic.

**Where it fails, and it is the exact case that occurred.** The em-dash sweep's subject was NOT empty — it read 302 of 306 entries. An all-or-nothing guard fires on total blindness and is silent on partial blindness, which is the more common and more dangerous shape. This is a floor, not a fix, and it is worth being honest that it would not have caught the failure that produced this branch.

⚠️ Unvalidated. Agent-ideated from an observed failure.
