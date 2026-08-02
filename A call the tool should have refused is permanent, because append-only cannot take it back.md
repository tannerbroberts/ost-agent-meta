---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-25-friction-an-empty-annotation-is-recorded-rather-than-refu.md'
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion

Append-only is what makes the vault trustworthy, and it is also what makes a malformed write unrecoverable. A call that passed an empty or undefined argument was accepted and written, so two entries whose entire body is the literal text `undefined` now sit permanently on a root node — the damage cannot be edited out and the original intent cannot be reconstructed.

The asymmetry is the point: in a system that can edit, a bad write costs a correction; here it costs a permanent scar on the node's history. Validation that would be a nicety elsewhere is load-bearing here, and its absence is only discovered after the record is already immutable.

**The need:** I want the tool to refuse a write that carries no meaning, because I cannot take it back once it lands.

More than one way to address it: refuse empty/undefined arguments at the tool boundary, require a minimum-substance check before any append, offer a supersede-with-reason entry that visibly retracts without deleting, or surface malformed entries as hygiene issues so a human can annotate over them.

## Provenance

Distilled from `INBOX:2026-07-25-friction-an-empty-annotation-is-recorded-rather-than-refu.md` — filed by the bootstrap loop after `ost_annotate` accepted an undefined issue string against the tetrix-ost root Outcome.

## History
- 2026-08-02 evidence: stated → assertion — Demoted from 'stated' for consistency: this rests on an inbox friction note, and the inbox channel's earned ceiling is 'assertion'. Sibling nodes distilled from identical notes were capped there by the ranker; the difference was that this item's actor was unrecorded, not that its evidence is stronger.

## Issues
- 2026-08-02 Likely merge candidate — flagged by the pass that created it. Its parent "A tool call I got slightly wrong destroyed the note I was filing" already carries "Refuse a write whose content is empty or literally undefined", which is precisely the fix this node's evidence calls for, alongside "Validate every tool call against the schema the tool already declares" and "Echo the written line back so a bad write is visible immediately". The child's one genuinely distinct claim is about append-only as an amplifier — that a malformed write here costs a permanent scar rather than a correction, so input validation is load-bearing in a way it would not be in an editable system. If a human does not think that distinction earns its own branch, this should be folded into the parent. No solutions were ideated here on purpose, to avoid duplicating the parent's three.
