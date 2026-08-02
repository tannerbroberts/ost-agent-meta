---
type: Opportunity
status: unvalidated
source: >-
  INBOX:friction/2026-08-01-friction-fourth-straight-scheduled-pass-15th-18th-with-no.md
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Creating a vault writes the tool-enabling config into the project beside it]]
[[A setup check that names the missing file and the exact line to add]]
[[Ship the vault and its tools as one unit, so there is no second step to miss]]

Four scheduled passes in a row ran with none of the vault's own tools available. The root cause was configuration that lives somewhere other than the vault: the plugin declares its server correctly, but the project directory carried nothing enabling that plugin, so the server was never launched. A sibling example vault has the enabling file; this one did not, and the difference is invisible from inside either.

The operator's mental model is that the vault is the thing being worked on and the tools come with it. In fact the tools are enabled by a file in the project that happens to be open, so a correctly-installed product and a correctly-created vault can still produce a session that cannot touch it. Nothing in the failing path names the missing file.

**The need:** I want opening my vault to be enough to get the tools that operate on it, or to be told plainly which file is missing.

More than one way to address this: ship the enabling configuration inside the vault when it is created, have the vault's own checks assert the tool surface and name the missing file, detect the vault at session start and prompt to enable, or document a single verified setup path and test it in CI.

## Provenance

Distilled from `INBOX:friction/2026-08-01-friction-fourth-straight-scheduled-pass-15th-18th-with-no.md` — filed by the session that located the root cause after the fourth toolless scheduled pass. Recorded at `assertion`: the inbox channel's earned ceiling.
