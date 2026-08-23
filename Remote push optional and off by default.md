---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-safety-requirement.md'
created: '2026-07-25'
evidence: assertion
authorship: machine
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Operators get real value with the vault staying entirely local]]

**Candidate solution (unvalidated).** Nothing leaves the operator's machine unless they explicitly enable and configure remote push. By default the vault is local-only, so the blast radius of any bad commit — or any prompt-injection — is confined to a local folder under version control.

**Approach:** *containment / minimize blast radius*.

**Contrast with siblings:** the other two address whether harm can happen or be undone locally; this bounds where its effects can propagate. Together they cover expression, recovery, and containment.

_Addresses: "Fear the agent could take a destructive, irreversible action". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Test do operators get value with remote push off" — moved under "Operators get real value with the vault staying entirely local" — the belief this test measures now has a node of its own

## Already shipped and pinned by passing specs — do not write an instrument here (unattended sweep, 2026-08-23)

This node sits in `solutionsMissingInstruments`. It should not be instrumented, because the mechanism it proposes **already exists and is already asserted by green tests**. Verified first-party this pass with `ost_read_repo`; an instrument written here would pass on arrival, and a command that cannot fail measures nothing.

Both halves of the claim are pinned, in two different places:

**1. The default is off.** `test/config/load.test.ts`, in "parses the scaffolded default config and applies defaults", asserts `expect(cfg.remote.enabled).toBe(false)` — with the comment `// default: no push` on the line. A vault scaffolded by `ost-agent init` pushes nowhere until someone edits the config. The same test file pins the adjacent containment defaults the same way (`adapters.transcript.enabled` false, `adapters.atlassian.enabled` false, `web.search.federated.enabled` false), so "off by default" is a house pattern here rather than a one-off.

**2. The agent surface cannot push even when it is on.** `test/release/outward-mutation.test.ts` (criterion P6) asserts `ALLOWED_TOOL_NAMES` minus `MCP_TOOL_NAMES` is exactly `["git_commit", "git_push"]` — the two names the MCP server withholds — and drives every exposed tool with `remote.enabled: true` and `gitPush` spied, requiring zero pushes. It carries a positive control that fires `git_push` from the unfiltered tool set and asserts the spy records it, so the green is not vacuous. That is a stronger guarantee than this node claims: containment does not depend on the operator leaving the flag alone, because the agent has no tool that reaches the push.

**What this leaves genuinely open, and it is not mechanical.** The assumption beneath this node — "Operators get real value with the vault staying entirely local" — is a desirability question about whether local-only is enough for anyone, and no spec in `test/` can answer it. It needs real operators. This sweep cannot label it: `ost_flag_humans_required` is withheld on the unattended surface, so a human should set the lane with `ost-agent lane --set`.

**Suggested disposition for a human:** this is a shipped solution wearing an unvalidated tag, and `ost-agent promote` is the call that would say so. Not done here — promotion is a human's, and the evidence above is feasibility, not the demand evidence the assumption asks for.

_Source: this pass's own `ost_read_repo` reads of `test/config/load.test.ts` and `test/release/outward-mutation.test.ts`. First-party observation of the repository; grounds feasibility, not desirability. No test was run and no result is recorded — the specs above are reported as existing, not as having been executed this pass._
