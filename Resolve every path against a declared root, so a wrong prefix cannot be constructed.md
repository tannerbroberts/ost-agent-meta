---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Check how many past failed paths fall inside a small set of nameable roots]]

The run is given named roots at the start — the project, the vault, the logs — and refers to things relative to those names rather than by assembling absolute paths itself. A caller asks for the vault's inbox, not for a string beginning `/Users/tanner/`. The prefix is supplied once, correctly, by whatever knows it.

Every miss in the evidence is a prefix error. `/Users/tanner/dev/ost-agent-meta` for `/Users/tanner/ost-agent-meta`; a log directory that does not exist; a source path from a different repository's layout. In each case the tail was right and the caller had no business constructing the head.

**Compared to the alternatives.** Prevents the class rather than describing or diagnosing it, and it survives the workspace moving — every path follows the root automatically. It only covers what the roots name, so anything outside them is constructed by hand exactly as before, and it needs a discipline the caller has to keep.

**What would make this the wrong pick.** Named roots are another thing to define and keep current, and a root pointing somewhere wrong produces confident, uniform, wrong paths everywhere at once — a worse failure than a scattering of individual bad guesses, because it looks systematic.

## Definition of done

[[Check how many past failed paths fall inside a small set of nameable roots]]

```
npx vitest run test/runner/path-root-coverage.test.ts
```

Green means a declared root vocabulary of at most four names covers at least 80% of the paths that actually failed in this vault's harvested transcript corpus. It is red today because no root vocabulary is declared anywhere in the repository and nothing extracts paths from the harvested records.

**Why coverage is the whole test and not a proxy for it.** Anything outside the named roots is constructed by hand exactly as before, so the share of real failures the roots capture *is* the value of the approach. A root set that covers half the failures halves the benefit and keeps all of the machinery.

**What green does NOT settle, and it is the more dangerous failure.** A root pointing somewhere wrong produces confident, uniform, wrong paths everywhere at once — worse than scattered bad guesses, because it looks systematic and nothing in a coverage number would show it. That risk needs its own check. Green also measures against paths that were reached for *without* a root vocabulary, so it cannot say how the habit changes once one exists.
