---
type: Opportunity
source: 'TRANSCRIPT:a615eb46-cc50-41a9-a77f-931c0dc67db0'
created: '2026-08-03'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[The tool surface offers the correct form so prominently that the failing form is not reached for]]
[[The tally is kept and the second occurrence is met with the count, not the correction]]
[[A shell-agnostic execution path that never hands a string to a shell at all]]

I make a mistake, the tool tells me the mistake, and then I make the identical mistake four more times inside the same session. The correction arrives every time and lands nowhere, because what comes back reads as a fact about one command rather than a fact about a habit I am in the middle of repeating.

What I want is to be told, on the second occurrence, that this is the second occurrence.

## What the evidence shows

- `TRANSCRIPT:a615eb46-cc50-41a9-a77f-931c0dc67db0` — five consecutive `tool_error` (Bash) events, every one of them `Exit code 1 … (eval):1: == not found`. Five identical failures, one session, nothing between them.
- `TRANSCRIPT:b7aae32d-150a-462f-9027-cdf7af12badd` — the same `== not found` three times in one session.
- `TRANSCRIPT:97546e2f-307a-46c7-a40e-64de3ec75f68` — `(eval):1: == not found` again.
- `TRANSCRIPT:5e5c119d-e5e8-4dbd-ab7c-c4bfc1247a18` and `TRANSCRIPT:8fc8d6e3-7cae-41e0-a83b-e32346e352b1` — `(eval):1: no matches found: /Users/tanner/dev/ost*`, the same zsh no-match rule, in two separate sessions.
- `TRANSCRIPT:470cb94a-d709-43b1-85aa-dedd917ac866` — `(eval):41: parse error near '\n'` and `": invalid command code 2"` in one session.
- `TRANSCRIPT:92cc492d-3bc1-4f30-abc3-4cae8f436c4e` — a quoting failure that swallowed the sentence being written.

Every one of these is the same underlying class: a command written for one shell's quoting and globbing rules, evaluated under another's.

## Why this is not the parent need

The parent is about a lesson that fails to survive from one session to the next. This one does not need to survive anything — the correction and the repetition are minutes apart in a single unbroken context. That makes it a different and cheaper problem: the parent needs somewhere to store a lesson, and this needs only to notice a repeat.

Evidence class: observed behaviour of the agent's own usage, captured mechanically from session transcripts. It grounds usability, not desirability, and is not outside-user evidence of want.

## Corroborating sessions (2026-07-24 → 2026-07-30)

Seven sessions, and the repetition is visible *within* a single one rather than only across them.

- `TRANSCRIPT:b7aae32d-150a-462f-9027-cdf7af12badd` — `(eval):1: == not found` three times in one session, unchanged between attempts.
- `TRANSCRIPT:97546e2f-307a-46c7-a40e-64de3ec75f68` — the same `(eval):1: == not found`, a session later.
- `TRANSCRIPT:5e5c119d-e5e8-4dbd-ab7c-c4bfc1247a18` — `(eval):1: ==== not found`, plus `no matches found: /Users/tanner/dev/ost*`.
- `TRANSCRIPT:8fc8d6e3-7cae-41e0-a83b-e32346e352b1` — the identical unquoted-glob failure, `no matches found: /Users/tanner/dev/ost*`, six days earlier.
- `TRANSCRIPT:516fdfb8-bab1-41a4-b1e5-92fde97bd90d` — `no matches found: test/tmp*`, same class, different glob.
- `TRANSCRIPT:470cb94a-d709-43b1-85aa-dedd917ac866` — `parse error near '\n'` and `": invalid command code 2`.
- `TRANSCRIPT:748498c4-31fb-4110-9012-464c441a463f` — `Undefined subroutine &main::pct` (a one-liner in the wrong language for the interpreter it was handed to).

The failures are three stable classes — zsh word-splitting on `==`, unquoted globs that zsh refuses rather than passes through, and multi-line/quoting mangling — and each recurs across sessions weeks apart. A per-invocation error message cannot say "you have done this before"; nothing in the loop is holding the class.

A second surface shows the same shape and is worth noting here rather than as its own need: `TRANSCRIPT:516fdfb8-…` and `TRANSCRIPT:4ff7b605-da1d-4f2e-8c05-ec6408118837` both submitted a Workflow script with TypeScript syntax in it and were told, twice, that the surface is plain JavaScript. Same structure — a surface whose constraint is learned only by tripping it, repeatedly.

Evidence class is observed behaviour of this agent using its own harness — usability, not demand.
