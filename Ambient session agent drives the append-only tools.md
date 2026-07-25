---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-agent-as-driver.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault
[[Test can an ambient agent drive a pass at API-driver quality]]

**Candidate solution (unvalidated).** Expose the append-only OST tools as a CLI and MCP server that the Claude agent *already running in the operator's session* drives directly. The ambient agent does the discovery reasoning; there is no separate API token to buy or manage. Safety guarantees (append-only, allowlist, git, never delete) hold regardless of who drives.

**Approach:** *reuse the intelligence already present*; zero new credential.

**Contrast with siblings:** unlike BYO-key (optional external key) it needs none; unlike a bundled local model it borrows a frontier-quality agent the operator already has.

_Addresses: "Don't want to buy a second AI credential just to try it". Unvalidated — human to review._
