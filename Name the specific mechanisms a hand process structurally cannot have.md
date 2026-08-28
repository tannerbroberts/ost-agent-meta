---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Practitioners recognise their own discipline as something that has failed them]]

Answer the question by pointing at things a person with a chat model and a notes app cannot have, however disciplined they are. A gate that refuses to clear on a test nobody ran. An evidence ceiling enforced at the call, so a node cannot describe itself into a rung its source has not earned. A status value that does not exist, so nothing can mark its own work validated. A check that fails on a wikilink hard-wrapped across two lines.

None of these are about intelligence, which is where a hand process is strongest. They are about a rule that holds when the person applying it is tired, invested in the answer, or in a hurry — which is exactly when discovery discipline fails.

**Compared to the alternatives.** Immediate, free, and it can be demonstrated by showing a refusal happening. It is also only an argument: a determined person could keep a checklist and get most of the way, and this asserts rather than measures the difference. The two-week comparison would produce evidence instead of a claim; positioning as a complement avoids the fight entirely.

**What would make this the wrong pick.** The buyer may not believe their own discipline is the problem — nobody thinks they are the one who overclaims — so the pitch describes a weakness the listener does not recognise as theirs. That framing risk is the thing to test, not whether the mechanisms exist.

## History
- 2026-08-05 unlinked "Ask ten practitioners whether their own discipline has ever failed them, before naming any mechanism" — moved under "Practitioners recognise their own discipline as something that has failed them" — the belief this test measures now has a node of its own

## The four named mechanisms, audited against the repository (unattended sweep, 2026-08-28)

This candidate is a pitch, and its credibility rests entirely on the four mechanisms its prose names being real. No pass had checked them. Read first-party this sweep with `ost_read_repo`; the audit is of *this node's own factual claims*, not of the assumption beneath it, which stays a question for practitioners.

**Confirmed — "a gate that refuses to clear on a test nobody ran".** `test/ost/results.test.ts` asserts `gateSolution(tree, "Sol").cleared` is `false` before any result and `true` only after `recordResult` writes one. A result refused for not stating what it failed to cover leaves the gate uncleared and no half-filed `## Results` behind. The file also carries a standing guard: for every name in `ALLOWED_TOOL_NAMES` and `MCP_TOOL_NAMES`, `expect(name).not.toMatch(/result|verdict/i)` — so the claim is not "the agent is told not to" but "no tool with that name exists". Safe to say out loud.

**Confirmed, and stronger than the prose claims — "an evidence ceiling enforced at the call".** `test/adapters/corroboration-actor-ceiling.test.ts` closes the route this pitch does not mention: thirty transcripts cited by thirty nodes render as "30 source(s) from 1 actor(s) … not 30 independent voices", and its last case pins that capturing one record and capturing thirty leave the actor's rung identical — standing is earned by recorded tests, never by how often a source spoke. `test/ost/evidence-class-on-every-node.test.ts` adds the floor half: one undeclared node drags the whole rollup to `assertion` rather than being skipped past. The sharper sentence for a listener is *volume cannot buy standing*, which is a failure mode every hand process has and none can see.

**Not confirmed — "a status value that does not exist".** Neither file read this pass covers the status enum, and no spec asserting `validated` is unreachable was located. The claim may well be true — it is stated throughout the ruleset — but it is the one of the four this audit cannot back, so it should not be said in a pitch until someone points at the spec. Cheap to settle; left open rather than assumed.

**Confirmed by a prior pass, not re-read here — the wrapped-wikilink check.** Recorded on "Append-only tool surface with no delete or shell tool" against `test/ost/vault-write-guard.test.ts`, which refuses a link split across a line break at every free-text write parameter. `test/ost/mutate.test.ts` shows the same rule holding where it would be easiest to forget: a History line naming a node quotes it rather than linking it, asserted explicitly so a merge cannot mint a second backlink.

**A fifth mechanism, and it is the best one in the box.** `test/ost/mutate.test.ts` exists to pin a property none of the four names: a human's `## Results` block survives an edit that rewrites every word around it, and survives the deletion of the file it lived in, because a merge carries reserved sections onto the survivor. The file's own header states the principle — *authoring a permit and revoking a human's are the same act pointed in opposite directions.* A person with a chat model and a notes app cannot have this at all. They can be disciplined about not fabricating a finding; they have no way to make a finding they already recorded survive their own later rewrite of the page it sits on. That is a cleaner instance of this candidate's thesis than any of the four, and it answers the "a determined person could keep a checklist" objection the prose itself raises, because no checklist survives the checklist-keeper.

_Source: first-party `ost_read_repo` reads of `test/ost/results.test.ts`, `test/adapters/corroboration-actor-ceiling.test.ts`, `test/ost/evidence-class-on-every-node.test.ts` and `test/ost/mutate.test.ts`. Grounds feasibility — that the mechanisms exist — and says nothing about whether any practitioner finds the pitch persuasive, which is the assumption beneath this node and still needs people. The specs are reported as present and asserting what is quoted; none was executed this pass and no result is recorded._

## The open item above, closed — and the claim is wrong as worded (same sweep, 2026-08-28)

The audit left one of the four unverified: "a status value that does not exist, so nothing can mark its own work validated." Settled by reading `src/ost/node.ts` first-party. **The status value exists.**

```
export const NODE_STATUSES = ["unvalidated", "validated", "in-discovery", "shipped", "deferred"] as const;
```

`validated` is in the vocabulary, in the type, and accepted by `deserialize`. Anyone who opens the model after hearing this pitch finds it in the first screen of the file, so the sentence as written is a claim that can be contradicted in under a minute — the worst property a pitch line can have, and worse than saying nothing.

**What is true, and it is a better line anyway.** The value exists; the *agent's route to it* does not, in three independent places:

- `ost_set_status`'s enum is `unvalidated | in-discovery | shipped | deferred` — `validated` is not a value any tool on any agent surface can pass.
- The `unvalidated` marker is stamped server-side at creation, and `src/ost/node.ts` says of it in terms: "no allowlisted tool can remove it — the only remover is `Vault.promoteToValidated`, off every surface."
- An invariant, `no-self-validation`, fires on the contradiction between that tag and `status: validated` — so even a file edited by hand into the contradictory state is caught by `check` rather than believed.

So the honest form is *not* "the word doesn't exist" but **"promotion is a value the agent has no tool to write, a tag it has no tool to remove, and an invariant that catches the state anyway"** — three mechanisms where the prose claimed one, and each one checkable. That is strictly stronger, and it survives the listener going and looking, which the current wording does not.

**Left for a human rather than edited in.** The fix is a one-sentence rewrite of the bullet in this node's opening paragraph, but that paragraph is the pitch itself and rewording a pitch is a positioning call, not a hygiene repair. The correction is recorded here so whoever owns the pitch makes it deliberately. Until then, the third bullet should not be said aloud.

_Source: first-party `ost_read_repo` read of `src/ost/node.ts`, plus the `ost_set_status` tool schema on this surface. Grounds feasibility only. No test was run and no result is recorded._
