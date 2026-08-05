---
type: Solution
status: unvalidated
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The configuration gap that makes a session toolless is mechanically identifiable]]

A command that inspects the current session against the vault and reports the specific gap: which file is absent, what one line it needs, and where it belongs. The root cause in the observed case took four passes and a comparison against a sibling example vault to locate, and it is mechanically checkable in under a second.

**Compared with the alternatives:** this fixes the existing vaults that setup-time configuration cannot reach, and it is honest about ownership — it tells the operator what to do rather than editing their configuration for them. Its weakness is that it only helps someone who thinks to run it, which is not the person currently losing four scheduled passes in silence. It is the cheapest of the three to build and the one most dependent on being invoked at the right moment.

Unvalidated, agent-ideated: a candidate for comparison, not a recommendation.

## Definition of done

"Replay the four toolless passes and see whether the check names the right file"

```
npx vitest run test/config/setup-check-diagnosis.test.ts
```

Red today: the setup check does not exist. Green when four fixtures reconstructing the toolless passes each get the missing file and its location named, and a correctly configured fixture draws no accusation.

**What a green spec does not settle.** It proves the diagnosis is correct when the check runs. It cannot show the check runs at all inside a session that is missing its tools — that is the sibling question "Check whether a toolless session can even run the tool check", and if that one comes back negative this instrument is green on a check that never fires.

## History
- 2026-08-05 unlinked "Replay the four toolless passes and see whether the check names the right file" — moved under "The configuration gap that makes a session toolless is mechanically identifiable" — the belief this test measures now has a node of its own
