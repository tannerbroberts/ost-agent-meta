---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-agent-as-driver.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[An agent already in the operator's session can run a pass as well as a dedicated API driver]]

**Candidate solution (unvalidated).** Expose the append-only OST tools as a CLI and MCP server that the Claude agent *already running in the operator's session* drives directly. The ambient agent does the discovery reasoning; there is no separate API token to buy or manage. Safety guarantees (append-only, allowlist, git, never delete) hold regardless of who drives.

**Approach:** *reuse the intelligence already present*; zero new credential.

**Contrast with siblings:** unlike BYO-key (optional external key) it needs none; unlike a bundled local model it borrows a frontier-quality agent the operator already has.

_Addresses: "Don't want to buy a second AI credential just to try it". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Test can an ambient agent drive a pass at API-driver quality" — moved under "An agent already in the operator's session can run a pass as well as a dedicated API driver" — the belief this test measures now has a node of its own

## Founder preference (2026-07-25, human:conversation)

The founder stated as a standing opinion: "a human's interaction with the OST should be through an AI agent." This directly endorses this solution's thesis — the agent-as-driver is not just a zero-credential workaround but the intended primary interface. Assertion rung; recorded as design intent, not validation.

## Test

"Test can an ambient agent drive a pass at API-driver quality"

`npx vitest run test/loop/ambient-driver-parity.test.ts`

Green when one pass driven through the ambient path and one through the API-driver path produce matching node sets and edges over a fixture vault. Structural parity only — it cannot compare prose quality, which is most of a node's worth, and a fixture short enough to be a spec will never reach the failure this actually risks: a long pass that stops mid-sweep and reports a clean run.
