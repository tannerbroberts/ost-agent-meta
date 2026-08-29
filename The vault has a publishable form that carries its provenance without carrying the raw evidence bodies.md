---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[A published vault carries every source id and none of the evidence bodies]]

**The belief, stated so it could be false.** This candidate's whole claim to being more than content marketing is that the artefact is "unusually legible — a tree with provenance, an evidence ladder, and a public history of what was refused ... a demonstration that cannot be faked by a screenshot." That requires publishing something that still *carries* the provenance. The belief is that such a form exists and is safe to post. It may not.

**The bind, and why it is a bind rather than a chore.** The two halves pull against each other:

- Publish the node files alone and every `source:` pointer dangles. `TRANSCRIPT:09ec7cd2-…` means nothing to a reader who cannot resolve it, so the evidence ladder becomes a set of unverifiable assertions — precisely the screenshot this candidate says it is not. This tree already records that the provenance resolves into `.ost-agent/`, which Obsidian hides, on the sibling candidate "Compete on the vault being plain files".
- Publish the sidecar too and you publish raw session transcripts. This vault's own evidence bodies contain absolute home paths (`/Users/tanner/.local/state/ost-build-loop/…`), verbatim command output, tool arguments, GitHub API responses and file contents captured mid-edit. None of it was written to be read by strangers.

The node's own closing line — "publishing a real vault means publishing real evidence" — names the risk and then treats it as a limit on *whose* vault, not as a question about whether a safe publishable form exists at all. That is the gap this assumption fills.

**Why it is in doubt, read off the repository this pass.** No export, publish, redact or share module exists anywhere in `src/` — the directories are `adapters, cli, compression, config, eval, fs, git, knowledge, loop, mcp, ost, processes, product, release, runner, security, telemetry, web`, and `src/ost/sanitize.ts`, which sounds like it might be this, is filename sanitization for path safety and nothing else. More telling than the absence of a module is the shape of the specs: every file in `test/security/` guards *inbound* safety — credential brokering, tainted arguments, tool allowlists, data framing, gate coverage. **Outbound disclosure is not tested anywhere.** The product has thought hard about what may enter it and not at all about what may leave.

**What would make the belief true cheaply.** The pieces are close to hand. Node files already separate a `source:` id from the body it points at, so a published form could carry the id, the actor, the rung and the date — enough for the ladder to mean something — while the body stays home. That is a redaction boundary the schema already implies rather than a new mechanism.

**Bound on the repository claim, stated so it is not over-read.** `src/cli/index.ts` is 158KB and was probed rather than read, so a publish command implemented inline in the command registry is not ruled out. What is established is that no dedicated module exists and no spec asserts any outbound-disclosure property. A reader with a shell should grep for `publish`, `export` and `redact` before building.

**What this does not claim.** Nothing here says publishing would bring anyone — that is the sibling assumption already on this node, "Publishing real discovery work brings strangers who try it", and it needs real readers. This is the mechanical floor beneath it: the sibling is worth testing only if there is something publishable to test with.

**Provenance.** Composed by an unattended pass from first-party `ost_read_repo` listings of `src`, `src/cli`, `src/security`, `test/security` and a full read of `src/ost/sanitize.ts`, plus evidence bodies served by `ost_next_work` this pass. Nothing was executed. Rung stays at the `assertion` floor.
