---
type: Opportunity
status: unvalidated
source: 'TRANSCRIPT:5e5c119d-e5e8-4dbd-ab7c-c4bfc1247a18'
created: '2026-08-06'
evidence: observed
authorship: machine
---
#Opportunity #unvalidated #evidence/observed
[[Never let a malformed search be counted as an empty result]]
[[Search node text through a literal-only interface, so no escaping question ever arises]]
[[Route every data-derived argument through a quoter, and make the unquoted path unavailable]]

I ask for a search for something that is in my tree, and what comes back is a parser complaining about my punctuation.

The node titles in this vault contain braces, asterisks and quotes, because they are sentences a person wrote. When a run builds a search out of one, the brace stops being a character in a title and becomes an operator. Session `8a9777ad` recorded `rg: error parsing glob '{Charge': unclosed alternate group; missing '}'`. Session `6e66c934` recorded the same failure with a different title: `*{threshold`. Neither search ran. Neither reported "not found". Both reported that the question was malformed, which is a different answer and a more expensive one, because the run now has to work out whether the fault was the pattern or the target.

The shell does it too, and worse, because there it fails silently in the caller's favour. `no matches found: test/tmp*` and `no matches found: /Users/tanner/dev/ost*` are zsh refusing to run a command at all because a glob matched nothing. `ls: -d: No such file or directory` is a flag being read as a filename. `(eval):1: == not found` and `(eval):1: ==== not found` are separator lines from output being executed. In each of these the run intended a literal and the interpreter found an instruction.

The cost is not just the failed call. It is that a search which errors and a search which finds nothing look different only if you read the message carefully, and a sweep that treats "the pattern was malformed" as "there is nothing there" reports a clean result over a subject it never read.

What I want is for the things I ask about — titles, paths, phrases — to be carried to the tool as data, so a search that finds nothing says so, and a search that cannot run is impossible to mistake for one.

## Provenance

Cited record: `TRANSCRIPT:5e5c119d-e5e8-4dbd-ab7c-c4bfc1247a18`. Independently recorded in `8a9777ad-a1ca-47fc-ab8e-3bd4b001a5cd` and `6e66c934-24d8-4200-b6f2-7af23002c478` (the two ripgrep glob failures), `022e473f-670e-4455-ac06-6a7cfc60ba60` (`ls: -d`), `a0eb3fd4-5a36-44c1-93fc-ac8b48258cff` (`cd docs/reference` from the wrong directory), `97546e2f-307a-46c7-a40e-64de3ec75f68` (`== not found`), and `516fdfb8-bab1-41a4-b1e5-92fde97bd90d` (`no matches found: test/tmp*`). Frontmatter carries one id because citations are matched exactly.

The last line of this note is the same claim the bucket "A sweep that cannot read its subject reports a clean result" makes about sweeps generally; this node is the argument-level cause of it, not a second copy of it.

This is the agent's own usage captured mechanically. It grounds usability, not desirability.

## Corroboration — two more literal-as-syntax instances (unattended sweep, 2026-08-17)

`TRANSCRIPT:022e473f-670e-4455-ac06-6a7cfc60ba60` recorded `ls: -d: No such file or directory` — a flag-shaped literal read as a flag. `TRANSCRIPT:054b78fc-df16-44ff-b394-760b30f34cb3` recorded `rg: error parsing glob '{Import': unclosed alternate group; missing '}'` — the same brace-in-a-title failure already documented above, on a different node title. Both are the pattern this node names: a literal intended as data, read as an operator by the interpreter it was handed to.

_Source: `TRANSCRIPT:022e473f-670e-4455-ac06-6a7cfc60ba60`, `TRANSCRIPT:054b78fc-df16-44ff-b394-760b30f34cb3` — observed behavior, captured mechanically from the agent's own transcripts. Grounds usability, not desirability.

## Corroboration — still recurring six weeks on (unattended sweep, 2026-10-02)

`TRANSCRIPT:1791743b-4df4-48eb-b002-0d28083eaf66`, captured this morning, holds one event, and it is this node's exact failure: `rg: error parsing glob '{A': unclosed alternate group; missing '}'`. That makes at least four brace-in-glob refusals on record (`8a9777ad`, `6e66c934`, `054b78fc`, and this one), and this one is dated 2026-10-02, against a first record in mid-August. So the brace case has not stopped happening: none of the three solutions beneath this node has shipped in a form that reaches the Grep glob argument. The record says nothing about which of the three would have stopped it.

_Source: `TRANSCRIPT:1791743b-4df4-48eb-b002-0d28083eaf66`. This is observed behaviour, captured mechanically, and it grounds usability, not desirability. It does not drain `unmappedEvidence`, because that predicate reads only a node's frontmatter `source:` (see "I map evidence the way the method says — onto an existing node — and the queue counts it as untouched"). Minting a duplicate opportunity to clear it would be the wrong trade._

## Corroboration — a fifth brace-in-glob refusal, a day after the fourth (unattended sweep, 2026-10-03)

`TRANSCRIPT:57d649c8-c2a9-4495-95f2-13e1aba3a9a0`, captured 2026-10-03, holds one event: the Grep tool's glob argument refused `{A` with `unclosed alternate group; missing '}'`. That is the same text as `1791743b` (2026-10-02). Two unattended firings on consecutive days hit the same refusal on the same title prefix. That suggests one recurring call shape in the sweep's own prompt-following, not five unrelated accidents. It also says the fix has to reach the Grep **glob** argument specifically: the pattern argument is not where these failed.

_Source: `TRANSCRIPT:57d649c8-c2a9-4495-95f2-13e1aba3a9a0`. This is observed behaviour, captured mechanically, and grounds usability, not desirability. It does not drain `unmappedEvidence` (frontmatter `source:` only); not minted as a new node on purpose._

## Corroboration — a sixth brace-in-glob refusal, on a different title prefix (unattended sweep, 2026-10-04)

`TRANSCRIPT:13caf7b3-2d91-4712-8977-e9fd6462380a`, captured 2026-10-04, holds a Grep `tool_error`: `rg: error parsing glob '{Install': unclosed alternate group; missing '}'`. Same failure, same argument (the **glob**, not the pattern), third consecutive day. This one weakens the 2026-10-03 reading, though. That reading guessed the cause was one recurring call shape on the `{A` prefix. `{Install` is a different title prefix, so the trigger is general: any brace-led literal handed to the glob argument fails. It is not one prompt quirk.

_Source: `TRANSCRIPT:13caf7b3-2d91-4712-8977-e9fd6462380a` — observed behaviour, captured mechanically; grounds usability, not desirability. Not minted as a new node on purpose; it stays in `unmappedEvidence` because that predicate reads frontmatter `source:` only._

## Corroboration — the pattern argument fails too, not only the glob (unattended sweep, 2026-10-04, later firing)

`TRANSCRIPT:afc3f52c-a9fb-4771-abf1-7cd6f94dae05`, captured 2026-10-04, holds two Grep `tool_error`s. One is the seventh brace-in-glob refusal (`'{Replay': unclosed alternate group`), on a fourth title prefix. The other is new and corrects a claim above. Ripgrep rejected the **pattern** with `look-around, including look-ahead and look-behind, is not supported`. The 2026-10-03 section says "the pattern argument is not where these failed". As of this record that is no longer true.

The two failures have different causes. A brace in a glob is a literal being read as an operator, which is this node's original case. Look-around is an operator the caller meant, written for a regex dialect the engine does not speak. So the fix has to cover both arguments, and quoting alone does not cover the second. Only the solution that says which dialect the engine accepts (see "Name the engine's published dialect in the tool description and build no validator of our own", filed under a different opportunity) addresses the look-around case.

_Source: `TRANSCRIPT:afc3f52c-a9fb-4771-abf1-7cd6f94dae05`. This is observed behaviour, captured mechanically, and it grounds usability, not desirability. It was not minted as a new node, on purpose, so it stays in `unmappedEvidence`._

## Corroboration — an eighth brace-in-glob refusal, fifth title prefix (unattended sweep, 2026-10-08)

`TRANSCRIPT:76f39716-3458-4a3e-ad8c-c746989ef18d`, captured 2026-10-08, holds one Grep `tool_error`: `rg: error parsing glob '{The': unclosed alternate group; missing '}'`. It is the same argument (the glob) on a fifth title prefix (`{The`), four days after the last one. That fits the 2026-10-04 reading that the trigger is general and not tied to one prompt quirk. Nothing new beyond the count: the failure is still happening, and nothing beneath this node has reached the Grep glob argument yet.

_Source: `TRANSCRIPT:76f39716-3458-4a3e-ad8c-c746989ef18d`. Observed behaviour, captured mechanically; it grounds usability, not desirability. Not minted as a new node, so it stays in `unmappedEvidence` (frontmatter `source:` only)._
