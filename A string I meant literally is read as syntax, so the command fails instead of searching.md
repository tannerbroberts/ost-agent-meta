---
type: Opportunity
status: unvalidated
source: 'TRANSCRIPT:5e5c119d-e5e8-4dbd-ab7c-c4bfc1247a18'
created: '2026-08-06'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Never let a malformed search be counted as an empty result]]
[[Search node text through a literal-only interface, so no escaping question ever arises]]

I ask for a search for something that is in my tree, and what comes back is a parser complaining about my punctuation.

The node titles in this vault contain braces, asterisks and quotes, because they are sentences a person wrote. When a run builds a search out of one, the brace stops being a character in a title and becomes an operator. Session `8a9777ad` recorded `rg: error parsing glob '{Charge': unclosed alternate group; missing '}'`. Session `6e66c934` recorded the same failure with a different title: `*{threshold`. Neither search ran. Neither reported "not found". Both reported that the question was malformed, which is a different answer and a more expensive one, because the run now has to work out whether the fault was the pattern or the target.

The shell does it too, and worse, because there it fails silently in the caller's favour. `no matches found: test/tmp*` and `no matches found: /Users/tanner/dev/ost*` are zsh refusing to run a command at all because a glob matched nothing. `ls: -d: No such file or directory` is a flag being read as a filename. `(eval):1: == not found` and `(eval):1: ==== not found` are separator lines from output being executed. In each of these the run intended a literal and the interpreter found an instruction.

The cost is not just the failed call. It is that a search which errors and a search which finds nothing look different only if you read the message carefully, and a sweep that treats "the pattern was malformed" as "there is nothing there" reports a clean result over a subject it never read.

What I want is for the things I ask about — titles, paths, phrases — to be carried to the tool as data, so a search that finds nothing says so, and a search that cannot run is impossible to mistake for one.

## Provenance

Cited record: `TRANSCRIPT:5e5c119d-e5e8-4dbd-ab7c-c4bfc1247a18`. Independently recorded in `8a9777ad-a1ca-47fc-ab8e-3bd4b001a5cd` and `6e66c934-24d8-4200-b6f2-7af23002c478` (the two ripgrep glob failures), `022e473f-670e-4455-ac06-6a7cfc60ba60` (`ls: -d`), `a0eb3fd4-5a36-44c1-93fc-ac8b48258cff` (`cd docs/reference` from the wrong directory), `97546e2f-307a-46c7-a40e-64de3ec75f68` (`== not found`), and `516fdfb8-bab1-41a4-b1e5-92fde97bd90d` (`no matches found: test/tmp*`). Frontmatter carries one id because citations are matched exactly.

The last line of this note is the same claim the bucket "A sweep that cannot read its subject reports a clean result" makes about sweeps generally; this node is the argument-level cause of it, not a second copy of it.

This is the agent's own usage captured mechanically. It grounds usability, not desirability.
