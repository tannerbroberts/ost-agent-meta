---
type: Opportunity
source: 'TRANSCRIPT:9c00df65-1c8d-4171-a870-22efc103d834'
created: '2026-09-03'
evidence: observed
authorship: machine
---
#Opportunity #unvalidated #evidence/observed
[[The search surface takes a declared intent instead of a raw pattern, so there is no dialect to know]]

I write a search the way I know how to write searches, and the tool tells me the construct I used does not exist here.

`error: look-around, including look-ahead and look-behind, is not supported` — the pattern was well-formed, I meant every character of it as syntax, and it was refused because this engine implements a narrower regex than the one the pattern was written in. Nothing before the call said which dialect was on offer. The refusal is the first and only place the boundary is stated, and it is stated one construct at a time: I learn that look-ahead is missing, and I still do not know whether backreferences, named groups or possessive quantifiers are there until I spend another call finding out.

**How this differs from the node beside it.** "A string I meant literally is read as syntax, so the command fails instead of searching" is the opposite direction: there I meant a brace as a character and the interpreter read it as an operator. Here I meant the construct as syntax and the engine does not have it. The two are separable by their repairs, which is why they are two nodes: a literal-only interface — the sibling's own candidate — makes this failure *more* likely, because it removes the expressive path entirely rather than telling me where its edge is. Conversely, publishing the supported dialect does nothing whatever for a brace in a node title.

**What I want.** To know the boundary of the pattern language before I compose against it, so a rejected search is a mistake I could have avoided rather than a fact I could only discover by paying for it. Failing that, a refusal that names the whole edge at once rather than the single construct I happened to reach for first.

**Litmus test (more than one way to address this?):** Yes, and they are genuinely different. State the accepted dialect in the tool's own description, so it is read before composing rather than after failing. Validate the pattern up front and name every unsupported construct in it at once, with a supported rewrite where one exists. Translate the common look-around forms into the two-step search that gets the same answer. Fall back automatically and report that a narrower search was substituted. Passes.

## Provenance

Cited record: `TRANSCRIPT:9c00df65-1c8d-4171-a870-22efc103d834`, captured by this firing. The same rejection is independently recorded in five further sessions — `301aaed8-fe21-428e-9e1d-314877cf46d1`, `82c427bd-ace7-4594-9e9e-5c8996d37258`, `5eca05e6-4342-46bc-a310-4befd694d127`, `214fae1a-0bcc-4f67-b92e-a0a594571093` and `00908faf-a23c-4c02-a792-9c402a4df8ac` — so this is a recurring shape across six distinct sessions rather than a single slip. Frontmatter carries one id because citations are matched exactly.

**Method and its limit.** The six were found by one grep for the look-around error string across this vault's stored evidence, and the count is of files containing that string, not of separate hand-verified incidents; one body was read in full. No node in the tree cited any of the six before this one, which is why this is a new node rather than a corroboration appended to an existing one — that absence was checked by grepping the vault's node files for the same string and finding none.

This is the agent's own usage captured mechanically. It grounds usability, not desirability: it says the boundary is discovered expensively, not that anyone outside this building wants it moved.

**Deliberately not ideated under.** This node maps evidence only. The unattended pass that created it set no solutions beneath it, so it will appear in `underservedOpportunities` at 0 of 3 on the next sweep; that is the ordinary state of a newly mapped need, not a defect.
