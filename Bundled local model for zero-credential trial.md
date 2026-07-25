---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-agent-as-driver.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault
[[Test is a bundled local model good enough for a pass]]

**Candidate solution (unvalidated).** Ship with a small local/bundled model sufficient for routine maintenance passes, so a first-time user can run the tool end-to-end with no external account or network dependency at all.

**Approach:** *remove the external dependency entirely* for the trial path.

**Contrast with siblings:** unlike ambient-agent (depends on the user already having one) and BYO-key (needs an account) this works fully offline, trading some reasoning quality for zero setup.

_Addresses: "Don't want to buy a second AI credential just to try it". Unvalidated — human to review._
