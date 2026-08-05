---
type: Opportunity
source: 'INBOX:2026-07-26-builder-lazy-mcp-server-shipped.md'
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Derive the next version from the registry, never from the local file]]
[[Refuse to release from history that has not been pushed]]
[[The loop proposes a release and a human tags it]]

**The need (operator's voice):** "I had work sitting unpushed while the autonomous loop cut its own release. Both of us reached for the same next version number. I caught it on a rebase — but nothing in the process was going to catch it for me, and the next one lands on people who have already installed."

**What was observed:** A builder session on 2026-07-26 finished the lazy MCP server locally (commit `3b9cc5e`, two commits ahead of origin, unpublished). While that sat unpushed, the autonomous loop released v0.18.0 to npm on its own. The local work had to be rebased and renumbered — feature `822d5bb`, release `a10e75f` = v0.19.0. The builder's own filing names the mechanism plainly: two release trains, one version counter, no coordination, and nothing in the release path consults the registry or `origin/main` before choosing the next number.

**Why it matters:** This is a near-miss, not an incident — the collision was caught by a human doing a rebase, which is exactly the attention this product exists to stop spending. It compounds with "Improvements I ship never reach the agents already running": the plugin invokes `ost-agent@latest`, so whatever wins the version race is what every consumer silently gets. A wrong number published once cannot be unpublished cleanly, which makes this the rare failure in this tree that is not append-only-recoverable.

**Also carried by this evidence, recorded where it belongs rather than here:** the same note reports the first-run seam shipped (472/472, then 493/493 on the merged tree) and is explicit that it does not move the rung on "I can't tell another PM 'just run npm install' and have it work" — no outside PM has been handed the one-liner, and the release itself is blocked on the credential in "Every run ends blocked on a credential only I hold".

**Litmus test:** More than one way to address it — preflight the registry and `origin/main` before choosing a number; derive the version mechanically from what is published rather than from a local file; a release lock or single designated release owner; require push-before-release so no train runs on unshared history; publish under a dist-tag until a human promotes it. Distinct mechanisms, real trade-offs. Passes.

**Evidence rung:** `assertion` — a builder self-report from inside the building. The test-suite counts in it are observed, but the need stated here rests on the builder's account of the near-collision; floor rung per the ladder's rule.
