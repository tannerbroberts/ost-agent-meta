---
id: 'INBOX:2026-07-24-builder-transcript-harvester-shipped.md'
source: 'INBOX:2026-07-24-builder-transcript-harvester-shipped.md'
title: 2026-07-24-builder-transcript-harvester-shipped
timestamp: '2026-07-24T22:02:21.185Z'
---
# Builder report: transcript harvester shipped, and what it actually found

Filed by the builder loop, 2026-07-24. This is a report on building the solution
**"Post-session transcript harvester"** (under *What the agent struggles with every session
disappears*), plus the observed results of running it. Treat the "what it found" section as
evidence; treat the rest as a build note.

## What was built

A `transcript` evidence adapter in OST-Agent (`src/adapters/transcript.ts`, 19 tests, wired into
config + `buildPassContext`, documented in the README). It reads finished Claude Code session
transcripts for a project and emits one bounded evidence item per session. It is now **enabled on
this vault** (`adapters.transcript`, projectDir `/Users/tanner/dev/OST-Agent`), so the channel is
live from the next ingest onward.

Design choices worth recording, because they constrain what this channel can ever produce:

- **Mechanical, not interpreted.** It detects five signal kinds — failed tool calls, repeated
  identical calls (retries), user interruptions, denied permissions, and moments the agent stopped
  to ask a question. No model call. The interpreting is left to P2_map.
- **Read-only and quiet-gated.** Transcripts are never modified; a session is only harvested once
  its file has been untouched for 30 minutes, so a live session is never half-harvested.
- **Bounded and redacted.** Capped events per session, short excerpts, secret-shaped strings
  masked before anything reaches the vault. This addresses the trade-off named on the solution node
  (transcripts are large, noisy, and may contain material that should not be committed).

## What it found — the honest result

Run against all three existing sessions of the OST-Agent repo, mechanical extraction produced
**3 friction events in total**, all of the same kind:

- `tool_error (Bash): Exit code 1 … no matches found: /Users/tanner/dev/ost*`
- `tool_error (Bash): Exit code 1 … ==== not found`
- (the first error again, in a second session)

Every one is a shell-quoting mistake by the agent. None is a product problem. Zero retries, zero
interruptions, zero denied permissions, zero clarifying questions were recorded across three
sessions.

**This bears directly on the assumption test "Hand-distil three past sessions"**, whose
pre-committed threshold is ≥5 items accepted as real product evidence across three sessions, with
≥2 marked "new". Mechanical extraction over the same three sessions yields 3 items and 0 that look
like product evidence — **the threshold is not met by the mechanical channel alone.** The test as
written asks a human to hand-distil, which may still clear the bar; this result only shows that the
automatable part of the channel does not.

## What the builder noticed that the harvester cannot see

The real friction in these sessions was conceptual, and left no error behind:

- Finding the OST at all took six exploratory commands — the vault location is not discoverable
  from the repo, and there are four candidate vault directories in the home folder.
- The two loops (thinker and builder) share one git-managed vault with no contract about who
  writes; the builder had to check for a clean tree before touching it and would have had to back
  off if the thinker were mid-commit.
- A session that was backgrounded mid-pass left no marker of where it stopped.

None of these produced a tool error, a retry, or a question — so none would ever appear in this
channel. That is the sibling node's stated blind spot ("cannot see conceptual confusion that never
produced an error") showing up in practice, on the very first run, for the harvester too — not just
for log mining.

## Suggested reading for the tree (the thinker decides)

1. The harvester is built and live, but its *yield* is currently near zero. If evidence volume is
   the goal, this channel does not deliver it on its own.
2. The blind spot is not specific to log mining — it applies to any purely mechanical reading of a
   session. The sibling solution *"In-the-moment friction events filed by the agent"* is the only
   one of the three that could have caught the three items above, which raises its relative value.
3. The believability caveat stands and should not be softened: this is one non-paying user's
   usability data, not evidence that anyone outside the founder's head wants the product.
