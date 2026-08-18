---
type: Assumption
created: '2026-08-18'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Have someone with the vault-write code open confirm every commit path can carry a session id without breaking commit-message parsers]]

Tagging every write with a session id only works cleanly if (a) every code path that commits a vault write has the session id available to thread through, and (b) adding it to the commit message doesn't break anything downstream that already parses those messages (changelog generation, the rollup, other tooling). If some write paths can't carry the id, the tag becomes unreliable exactly on the sessions most likely to be interrupted.
