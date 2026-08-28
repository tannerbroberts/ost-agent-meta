---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Friction shapes are separable by a mechanical signature]]

**The idea.** At ingest, friction events are reduced to a signature — tool name plus the normalised refusal text, with paths and ids stripped. Items sharing a signature arrive in the queue as one entry carrying the number of times it was seen and the sessions it came from.

**Why this shape.** It asserts nothing about needs. It only says that two byte-similar refusals from the same tool are the same *observation*, which is a mechanical claim a fixture can check. The parent records that the 76-item backlog is "the same four needs observed 76 times"; this is the version of that finding a machine can reach without deciding what a need is.

**How it compares to its siblings.**
- "An evidence item can be filed as corroboration of a node that already exists" puts the frequency on the opportunity, where a reader will actually meet it. This puts it on the queue entry, where it is visible only while unmapped. Weaker placement, far weaker claim.
- "An unmapped item ages out of the queue into a digest" hides volume; this compresses it. Compression keeps the signal, so it is strictly better on that axis and strictly more code.

**Where it fails, stated so it can be judged.** Normalisation is where this dies. Strip too little and 76 items stay 76 because each carries a different session id and path; strip too much and two genuinely different refusals — a permission denial for `ost_check` and one for `ost_read_repo` — collapse into one entry, and the tree loses the fact that two distinct capabilities were withheld. There is no setting that is obviously right, and the failure is silent in the over-stripping direction.

It also does not clear the backlog. Four grouped items are still four unmapped items, and the parent's complaint — that corroboration has nowhere to go — is untouched.

**Cost.** A normaliser and a grouping key at ingest, plus fixtures built from the corpus's real strings.

⚠️ Unvalidated. Agent-ideated.

## Definition of done

"One normaliser collapses the read-before-write family and keeps three permission denials apart"

```
npx vitest run test/adapters/friction-signature.test.ts
```

Written without repo sight, so its first red is an absent file. The fixture strings must be taken from this vault's real corpus — invented strings would make both halves trivially satisfiable.

## The corpus strings this candidate's bar asks for, located — 2026-08-28

This node's definition of done requires "One normaliser collapses the read-before-write family and keeps three permission denials apart," and adds that "The fixture strings must be taken from this vault's real corpus — invented strings would make both halves trivially satisfiable." This pass went and found them. Both halves of the bar are constructible from stored records rather than invented, so the instrument is buildable without inventing a single string.

**The collapse half.** The read-before-write family is the literal tool error "File has not been read yet. Read it first before writing to it." — **374 events across 206 of 458 stored transcript records**. It is the corpus's single largest friction shape by a wide margin, and it arrives from at least two distinct tools, Write and Edit, which is the variation a normaliser has to absorb rather than a single repeated byte string.

**The keep-apart half, which is the one that was genuinely uncertain.** The permission-denial family — "Claude requested permissions to use X, but you haven't granted it yet" — is 209 events across 110 records, and X takes at least **eight** distinct values in the stored corpus: `mcp__ost-agent__ost_check`, `mcp__ost-agent__ost_status`, `mcp__ost-agent__ost_debt`, `mcp__ost-agent__ost_flag_humans_required`, `mcp__ost-agent__ost_ingest_inbox`, `mcp__ost-agent__ost_next_work`, `WebFetch` and `WebSearch`. A ninth shape is adjacent and differently worded — a denied read of a filesystem path, "requested permissions to read from …" — which a normaliser stripping paths would be at risk of folding into the tool-name family.

So the bar's three-denials-apart clause is not a hypothetical: eight are available, and the hardest adjacent pair to keep apart is a real one rather than a constructed one.

**What this measurement does not do.** It does not show the normaliser is possible, only that the fixture is. The node's own stated failure mode — "strip too little and 76 items stay 76 because each carries a different session id and path; strip too much and two genuinely different refusals collapse" — is untouched by a census, and the eight distinct denied names above are exactly the set an over-stripping normaliser would destroy. Nothing here argues the setting exists.

**Also worth the operator's attention, because it is about this vault rather than about the candidate.** The most frequently denied capability across the whole corpus is `mcp__ost-agent__ost_flag_humans_required`, and it is denied on the unattended surface by design. That is the one tool that would move a prose-only test into a labelled lane, which bears on why the instrument backlog does not drain. Recorded here only because this is where the count was taken; the argument belongs to the instrument-queue nodes.

**Method.** Literal and regex substring counts with ripgrep over the 458 files in `.ost-agent/evidence/`, during the 2026-08-28 unattended sweep. No product code executed, no test run, no result recorded. The full shape distribution for the corpus is recorded once on the sibling candidate "The transcript adapter rolls near-identical sessions into one record before storing them" rather than repeated here. Rung unchanged at the `assertion` floor: this counts the agent's own sessions and grounds usability, never demand.
