---
type: Solution
source: 'TRANSCRIPT:3b9eaea5-d098-4f47-ad0a-65871012d639'
created: '2026-08-10'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** Extend the disposition ledger's subject from one id to one *predicate*. `ost-agent dispose --kind evidence --matching <pattern> --by <who> --why <reason>` records the pattern, not the expansion, and `ost_next_work` withholds any record it matches — including records that arrive after the dismissal was written.

**Why the pattern and not the expansion.** Recording the ids it happened to match today would make this a batch loop with extra steps: tomorrow's forty identical transcripts are not covered, and the operator is back to a per-record cost with a longer history file. A live predicate is the only form in which the judgement — *"records of this shape are not worth distilling"* — is the thing actually stored.

**What it deliberately keeps.** Everything that makes the current command safe. It stays on the CLI, so it is a human's hands; it still refuses an unattributed or unexplained dismissal; the reversal is still one command and still appends rather than erases; and `ost-agent dispositions` still lists it. The unit of judgement changes; nothing about who may make it does.

**Contrast with siblings.** This is the only one of the three that treats the records as *not worth reading*. "A node may cite many sources" says the opposite — the class deserves distillation and the citation should carry the whole cluster. "Roll near-identical records up at the adapter" agrees with this node about worth but acts before storage, so the operator never sees the class and never gets to disagree.

**Where it fails.** A live predicate is a standing order to hide future evidence, and the failure mode is silence: a genuinely novel record whose text happens to match is withheld and nobody is told. The current per-id form cannot do that, and giving it up is the real price. Mitigations exist — report the match count each pass, expire a pattern after N days, refuse a pattern broader than some share of the corpus — but each is a guess and none is obviously right. A pattern written in a bad week could suppress the channel that finds the next real thing.

**Cost.** Small to medium — a predicate field on the ledger entry, a matcher, and one honest decision about how loudly matches are reported.

⚠️ Unvalidated. Agent-ideated.
