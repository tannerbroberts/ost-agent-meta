---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-24-builder-transcript-harvester-shipped.md'
created: '2026-07-25'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[End-of-session retrospective the agent must write before the session closes]]
[[A model reads the raw transcript and files what the pattern scan cannot see]]
[[Detect the dead ends from the artifact trail rather than from the session]]

The struggles worth learning from are conceptual — a wrong framing, a rule misread, a dead-end approach — and they finish without leaving an error code, a retry, or any mechanical trace. A mechanical harvest of my sessions hands me shell-quoting trivia while the signal evaporates.

Grounding: the transcript harvester run over all three existing OST-Agent sessions produced 3 events, every one a shell-quoting mistake, and 0 items resembling product evidence — while the builder itself reports the real friction in those sessions was conceptual and left nothing behind (source report, section "What the builder noticed that the harvester cannot see"). The pre-committed threshold of the test "Hand-distil three past sessions" (>=5 real items) is not met by the mechanical channel alone.

Litmus (more than one way to address): agent self-files friction at the moment of pain; a model reads transcripts interpretively; a human hand-distils; a structured end-of-session reflection step. Distilled by the mapping agent from agent-self-reported observation; unvalidated.

## Corroborating evidence (mapped 2026-07-25)

- `TRANSCRIPT:5e5c119d-e5e8-4dbd-ab7c-c4bfc1247a18` — 3 mechanical events (tool_error x2, retry x1), all shell trivia, no product signal.
- `TRANSCRIPT:8fc8d6e3-7cae-41e0-a83b-e32346e352b1` — 1 mechanical event (tool_error x1), same shell-quoting mistake.

Both transcript harvests reveal no unmet need of their own; they are the noise floor that demonstrates this opportunity — the mechanical channel captures only trivia. Dispositioned here rather than into new nodes.

## The census this node predicted, now at twenty-five harvested records (2026-08-02)

When this node was written the whole transcript channel was three sessions and three events, and the claim was an inference from one builder's report. The channel has now produced **25 records — 24 distinct sessions, one of them harvested twice (see the duplicate-record annotation on the parent) — and 82 friction events.** The composition has not moved: shell quoting (`(eval):1: == not found`, `no matches found: …`), `Edit` old_string mismatches, a `Workflow` script written in TypeScript, a `git` divergent-branch hint, a `sed` against a moved path, a perl typo, an unknown skill id, a `cp` overwrite prompt, and — in nine separate sessions — `sleep N && gh pr checks`, blocked with the same correction each time.

**Not one of the 82 events is a failure of an `ost_*` tool.** Over five weeks, the channel built to watch this product work has captured the coding harness the agent happens to run inside, and nothing from the product's own surface.

Be precise about what that does and does not prove. It does **not** prove the product surface is painless: `USAGE:2026-07-26` recorded 62 failed calls in the same week, so the product surface does fail and a different channel sees it. What it proves is narrower and worse — the two mechanical channels observe disjoint subjects, and **neither of them observes a wrong framing.** The real friction of these five weeks (four passes that ran with no MCP tools and did not notice, an annotation written permanently as the literal text `undefined`, a wiki-link silently broken by a line wrap, five releases cut and unpublished) reached this tree only because a human or an agent sat down and wrote a note about it. Every one of those left no error code behind, which is exactly the claim of this node.

**Against the pre-committed threshold on [[Hand-distil three past sessions]]** — ≥5 items accepted as real product evidence across three sessions, ≥2 of them new — the mechanical channel has now had twenty-four sessions rather than three to clear a three-session bar, and has produced **zero** candidates a human would plausibly mark "real product evidence, and new". That does not retire the test: its whole point is that the *raw transcripts*, not the mechanical scan, are what a human should rate. But the mechanical arm of the question is answered, and the answer is the one this node predicted.

Recorded as corroboration, not as a new need. Rung `observed` on this vault's own sessions; explicitly not demand evidence.
