---
type: Solution
status: unvalidated
source: 'TRANSCRIPT:6e66c934-24d8-4200-b6f2-7af23002c478'
created: '2026-08-06'
evidence: observed
---
#Solution #unvalidated #evidence/observed

Keep the pattern languages and the shell, and close the gap where tree text reaches them unescaped.

A string that came from a node is not the same kind of thing as a string a person typed into a command, and every recorded failure here is those two being treated alike. The proposal is to mark the difference and enforce it: any value originating in the tree — a title, a path, a phrase from a body — is carried in a wrapper that cannot be concatenated into a command line, and the only way to get it out is a quoting call appropriate to the destination.

Enforcement is the whole proposal, not the quoter. A helper that callers are supposed to remember is a discipline, and this project has already concluded in writing that discipline alone has repeatedly not been enough — the wrapped-wikilink rule exists because asking people to keep links on one line did not work. So the unquoted path has to be absent rather than discouraged: if a raw title can still be interpolated, it eventually will be, at 3am, by a run nobody is watching.

The bet is that provenance survives. It may not. Once a title has been read out of frontmatter, passed through two function calls and formatted into a message, "this came from the tree" is a fact about its history rather than a property of the value, and a wrapper only holds if nothing along the way unwraps it for convenience. Every place that does is a hole, and holes in this kind of scheme are invisible until one is exercised.

Against its siblings. "Search node text through a literal-only interface" removes the destination rather than guarding the source, which is cleaner where it applies and does nothing for the shell — and the shell produced as many recorded failures as ripgrep did: `no matches found: test/tmp*`, `ls: -d`, `== not found`. This candidate is the only one of the three that covers both. "Never let a malformed search be counted as an empty result" is the safety net under whichever of these is built, and is worth having regardless.

The honest ranking, on today's evidence: build the miscount fix first because it is cheap and general, then decide between this and the literal interface on the basis of how many of a pass's searches genuinely need pattern semantics.
