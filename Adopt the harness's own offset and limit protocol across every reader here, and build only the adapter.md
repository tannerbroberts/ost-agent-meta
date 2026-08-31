---
type: Solution
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-31'
evidence: assertion
killIf: >-
  The harness renames or changes the offset/limit contract once, and this
  product's readers keep speaking the old one with nothing failing to say so.
killBy: '2027-02-28'
authorship: machine
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: bought-vs-built. Position taken: the convention is adopted from outside unchanged; only the adapter is built here.**

The harness already defines a sizing and pagination contract, and states it in the very refusal that produced this node's evidence: "Use offset and limit parameters to read specific portions of the file." Rather than minting a third convention — a `probe` mode here, a `bytes` field there — make every reader on this surface speak that one. `ost_read_repo` and `ost_read_tree` accept `offset` and `limit`, report the total in the same terms, and a reader that has learned the pattern once uses it everywhere without checking which tool it is holding.

**Why this position and not another.** The two siblings each invent something: a per-entry size field, or a truncate-and-offset response shape. Both are this product's own idiom, and this product's own idiom is already three-way inconsistent — `ost_read_repo` truncates, `ost_read_tree` caps a listing but not a body, `probe: true` exists on one reader and nowhere else. A reader currently has to learn each surface separately, which is a cost this node's need is a symptom of. Adopting a convention the reader already knows removes that learning entirely, and the code written here is a parameter translation rather than a mechanism.

**What is genuinely built here, and it is small.** A translation from `offset`/`limit` onto the existing caps in `src/product/repo.ts` and the vault's node reader, plus whatever unit conversion the contract needs. `MAX_FILE_CHARS` and `MAX_LIST_ENTRIES` stay as ceilings; the parameters select a window inside them.

**What it gives up, plainly, and this tree has already been burned by exactly it.** Adopting an upstream convention means depending on an upstream that can change it without telling anyone. The node "The unattended run is scoped for tools nobody granted it, and it finds out one denial at a time" records the precedent in this repository: Claude Code renamed `SlashCommand` to `Skill`, an automation deny rule kept naming the old one, and for four days a guard that named something no longer existing read exactly like a guard that worked. A borrowed protocol fails the same silent way, and the kill criterion above is written against that specific failure rather than against the idea in general.

**A second give-up, more mundane and more certain.** The harness counts tokens; this product counts bytes and characters and has no tokenizer. So the adopted contract can be spoken only approximately — a `limit` honoured in characters is not the `limit` the refusal was denominated in, and a reader who trusts the units will occasionally still overrun. Either this product acquires a tokenizer it does not currently want, or the adoption is partial and says so.

**What would make this the wrong pick.** If the upstream contract is unstable, or if the unit mismatch means a reader still cannot predict a refusal, then adopting buys familiarity and not correctness — and the sibling that simply stops refusing is better, because it does not need the units to agree at all.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author; this surface holds no grant to run independent parallel ideators. Discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-08-30; a human to review.
