---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
threshold: >-
  zero of 3 seeded private strings survive into the published form, and at least
  1 source id still resolves to its actor and rung
instrument: npx vitest run test/security/publishable-vault-export.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Pre-committed threshold:** zero of 3 seeded private strings survive into the published form, and at least 1 source id still resolves to its actor and rung. Both halves must hold. A form that leaks nothing because it carries nothing fails the second clause, and that is the failure mode worth naming — the cheap way to pass a redaction test is to publish less than is useful.

**The fixture.** A scratch vault with a handful of nodes and an evidence sidecar holding three records, each seeded with a distinct private-shaped string drawn from the shapes this vault's own corpus actually contains: an absolute home path (`/Users/someone/.local/state/…`), a verbatim command output line, and a token-shaped literal.

**The assertion contract, written here because it cannot go in the command.** The instrument grammar accepts one spec path and refuses a `-t` case filter as shell punctuation, so no agent surface can point at an assertion inside a file. The contract lives in this prose:

- The published form contains none of the 3 seeded strings — asserted per-string, so a failure names which one leaked rather than reporting a bare false.
- It still carries, for at least one node, the `source:` id, the actor that id resolves to, and the rung that actor has earned. That is what makes the evidence ladder legible to a stranger, and it is the half a naive "strip the sidecar" implementation drops.
- **The positive control, without which the green is vacuous:** the same fixture published with redaction disabled *does* contain all 3 seeded strings. Without it, a spec that produced an empty file would pass the first clause perfectly.
- A node body that itself quotes a private string — evidence pasted into prose by hand — is covered too, or the test states plainly that it is out of scope. Redacting the sidecar while publishing a body that quotes it is the obvious hole.

**Why this command is red today, stated honestly.** `test/security/publishable-vault-export.test.ts` does not exist, so this is a `no-spec` red: it fails the way any question written on that path would fail, and by itself distinguishes nothing. It is a build permit only because the threshold above is a bound bar. What makes it worth a builder's time is the contract plus a repository fact — `test/security/` currently holds 27 specs and every one of them guards what may *enter* the product (credentials, tainted arguments, tool allowlists, data framing, gates). There is no outbound-disclosure spec at all, so this is not a gap in coverage of a built mechanism; it is a mechanism nobody has built.

**What a green here would NOT settle.** It answers feasibility only — that a publishable form can exist and can be checked. It says nothing about whether publishing brings anyone (the sibling assumption, which needs real readers), nothing about whether the redacted artefact is still persuasive to a stranger, and nothing about the case the parent candidate's own prose flags as the real limit: a *customer's* vault rather than the author's. A passing spec makes publishing safe; it does not make it work.

**Sequencing.** Strictly prior to the human half and cheap. There is no point counting strangers who arrive from six published pieces until there is a form of the vault the author can safely post.
