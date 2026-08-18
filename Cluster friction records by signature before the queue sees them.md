---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A mechanical signature groups the redundant records without burying the singleton]]

**The idea.** The transcript harvester stops emitting one record per session. It groups friction events by signature — tool name plus error class, so "permission denied on a declared MCP tool" is one signature however many sessions hit it — and emits one record per signature, carrying the count and the contributing session ids.

**Why this one.** It attacks the problem where it is made rather than where it is felt. The 65 records are not 65 observations; this pass read four of them and found four repeating shapes. A queue that showed "permission denied on a declared tool — 41 events across 18 sessions" would be both smaller and more informative than what it shows now, and the operator's original ask — usage feeding back automatically — is better served by a frequency than by a diary.

**How it compares to its siblings.**
- "Let a friction record corroborate an existing opportunity" is the more valuable end state but needs a judgement per record and a new edge type. This one needs no judgement at all: the signature is mechanical, so it works unattended and on a surface with no reasoning budget left.
- "Record a read-and-skipped judgement" is pure disposal. This one preserves the count, which is the part worth keeping.
- Clustering and corroboration compose well — cluster first, attach the cluster — and if both ship this one should ship first because it makes the second one's per-item judgement cost fall by an order of magnitude.

**Where this fails, stated so it can be judged rather than assumed.** A signature is a guess about what makes two events the same, and the interesting friction is often the singleton. The `clarifying_question` in session `2a4bcf6e` — an unattended firing stopping to ask a human which of three ways to proceed — appears once and matters more than the fortieth permission denial; a frequency-ranked queue buries it. Clustering also destroys the narrative inside a session, and some of these records are only legible as a sequence: read three retries followed by a denial and you can see what the agent was trying to do, which a bag of counts loses. Worst case it makes the queue tidy and the tree blind to exactly the events worth reading.

**Cost.** A signature function and a change to the harvester's emit step. The cheapest of the three, and the only one that changes nothing about the tree's data model.

⚠️ Unvalidated. Nobody has confirmed that a count is what the operator wants from self-observation rather than a readable account of what went wrong.

## Definition of done

"Run the signature over the real 65 and check the singleton survives"

```
npx vitest run test/adapters/friction-signature-clustering.test.ts
```

Red today: the harvester emits one record per session and computes no signature anywhere — this pass's 65-item queue is the evidence. Green when the corpus collapses to ≤8 clusters AND session `2a4bcf6e`'s lone `clarifying_question` is still individually listed. Both halves, or re-cut the signature rather than tuning it.

The test title is quoted rather than linked because it is already wikilinked once by its parent Assumption, and a second link would fail `check`'s single-backlink rule.

## Evidence — the queue this solution targets is now 234 records deep (unattended sweep, 2026-08-17)

`ost_next_work` reported 236 unmapped evidence items this pass, 234 of them auto-captured `TRANSCRIPT:<session-id>` friction records of the shape "Session `<id>` (this vault's own unattended firings — nobody was watching) produced N friction events (tool_error ×A, retry ×B)" — sampled several, including the largest (`TRANSCRIPT:1c8a3722-b8a5-4828-b57e-c45b1566cf6d`, 9 events). All are self-generated observed-class evidence of the same already-well-mapped need (tool friction during unattended firings), differing only in session id and counts. This pass did not create an Opportunity per record: doing so would be exactly the "redundant records" failure this solution and its sibling assumption already name, at 234x the scale the two assumption tests beneath this solution were written against. Left unmapped rather than duplicated; they will keep re-surfacing every pass at this volume until either this clustering solution ships or a human decides individual friction transcripts should stop being ingested as separately-trackable evidence at all. The two genuinely distinct items in this pass's unmapped batch (a backgrounded-session note already cited elsewhere, and a build-loop falsification note) were handled individually rather than through this backlog.

## Evidence — queue still 290 records deep (unattended sweep, 2026-08-18)

`ost_next_work` reports 291 unmapped evidence items this pass; the overwhelming majority remain the same self-generated `TRANSCRIPT:<session-id>` friction records this solution targets, now well past the 234-record count observed on 2026-08-17. Same decision as the prior pass: not duplicating them into individual Opportunities. The backlog keeps growing at roughly one record per unattended firing and will keep doing so until this clustering solution ships or a human decides to stop ingesting individual friction transcripts as separately-trackable evidence.
