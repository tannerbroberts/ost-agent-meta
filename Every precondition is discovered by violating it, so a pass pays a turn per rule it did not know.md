---
type: Opportunity
status: unvalidated
source: 'TRANSCRIPT:fe671285-5ba3-422e-9cbe-2ea1ac7e3714'
created: '2026-08-06'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[A preflight manifest states every tool precondition before the pass composes its first call]]
[[The surface satisfies a precondition it could have satisfied itself]]

When I hand a run a file to change, it does not fail because the change was wrong. It fails because it did not know it had to read the file first — and the only way it learned that was by trying to write.

Across four unattended sessions the same refusal appears eight times: "File has not been read yet. Read it first before writing to it." Session `fe671285` spent four of its five friction events on it in a row. Session `79032a63` hit it twice and each time re-issued the identical Edit. Session `a9d23c64` hit it on Edit and then again on Write, against a path outside the repo entirely. Session `20d3f9af`'s single friction event of the whole run was this one refusal.

The same shape shows up wherever a tool has a precondition the caller cannot see before calling: an argument the schema does not accept (Glob refused an unexpected `limit` parameter), a body that will not parse (a Read whose JSON carried a stray comma), an evidence rung the node's own provenance cannot support. In every case the contract exists, the caller is willing to honour it, and the only channel that communicates it is the failure.

What I want is for the cost of a rule to be paid once, when the run is composed, rather than a turn at a time in the middle of work I am not watching. The read-before-write handshake is not unreasonable; being told about it only after spending the turn is.

This is not the same need as "The same refusal is rediscovered every session, because nothing carries the lesson forward" — that one is about a lesson failing to survive between runs, and its remedy is a store. This one is about the first discovery inside a single run, and its remedy is declaration or preflight. A pass that remembered every refusal it ever hit would still pay full price for a rule it is meeting for the first time.

## Provenance

Cited record: `TRANSCRIPT:fe671285-5ba3-422e-9cbe-2ea1ac7e3714`. The same pattern is independently recorded in sessions `79032a63-70dc-460c-bc63-fece67b7ecd1`, `a9d23c64-bba1-4c4e-8764-0fbdec34cd79`, `20d3f9af-7d1b-4f4d-9f8f-fe3755ea5a1c`, and `8a9777ad-a1ca-47fc-ab8e-3bd4b001a5cd` (schema-rejected Glob parameter, refused evidence rung). Frontmatter carries one id because citations are matched exactly; the others are named here in plain text so a reader can find them.

This is the agent's own usage captured mechanically from its transcripts. It grounds usability, not desirability — it is not evidence that anyone outside this building wants the product.

## Corroboration from the second ingest, same pass

This node was distilled from four sessions. Re-ingesting an hour later captured eighteen more, and they thickened it considerably rather than adding anything new.

Session `1744f10a` is the sharpest single record in the vault for this need: nine friction events, and **seven** of them are "File has not been read yet. Read it first before writing to it." Six Edits and one Write, in a row, against `src/runner/context.ts` and a state file under `~/.local/state`. Between the second and third the run re-issued the identical Edit unchanged, which is what learning a rule by collision looks like from outside — the caller does not yet know what changed, so it tries the same thing again. That session was an unattended firing; nobody was there to say "read it first".

Sessions `030e5db3`, `3a54bb43`, `4bd3582d`, `57249c25`, `79d0471e`, `491c205c` and `31a2e8bb` are the same shape at lower counts. Across the full corpus the read-before-write refusal now stands at roughly twenty occurrences in eleven sessions, which makes it the single most frequent friction event this vault has recorded about itself.

One new instance of the general form, and it happened to the pass writing this: `ost_read_tree` returned 134,240 characters and was refused for exceeding the response limit, with the size discoverable only by asking. Session `28d14def` hit the same wall from the other direction — a Read refused at 73,874 tokens against a 25,000 cap. In both, the cost of the rule is paid by the call that trips it, and in both there was a cheaper path available to a caller who knew the size in advance.

That is the same disease as the read-before-write handshake and it is worth stating as one claim rather than two: a caller cannot plan around a limit it can only observe by exceeding it.

Provenance: this pass, 2026-08-06, reading records `TRANSCRIPT:1744f10a-e7ce-4e46-a573-a1d99c44960c` and `TRANSCRIPT:28d14def-76a2-4bbb-bd55-6f9b80c8ca8c` in full, plus the `ost_read_tree` refusal observed first-party. Frontmatter still cites the single record it was created from; ids are matched exactly, so the rest are named here in plain text.
