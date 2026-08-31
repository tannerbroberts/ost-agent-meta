---
type: AssumptionTest
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-31'
evidence: assertion
threshold: 'zero file entries missing bytes, and <= 500 stat calls per listing'
instrument: npx vitest run test/product/repo.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**What the spec must assert**, stated here rather than left to whoever opens the file, because a filename is not a test design:

1. Build a scratch repo containing more than `MAX_LIST_ENTRIES` files of differing sizes, call `readProductRepo` with a directory `path`, and assert that **every returned entry of `type: "file"` carries a numeric `bytes`** equal to that file's size on disk. Against today's code the listing maps to `{ name, type }` only, so `entries[0].bytes` is `undefined` and this assertion fails on its value — not on a missing file.
2. Spy on `fs.statSync` across that same call and assert the count is **at most `MAX_LIST_ENTRIES`** (500), so sizing is bounded by the cap that already trims the listing rather than by the directory's true size.
3. Assert a `type: "dir"` entry carries no `bytes`, so the field means a file's size and not a placeholder.

**Why it is red today and red about this specifically.** The file `test/product/repo.test.ts` exists and already exercises this function, so the run resolves a real suite; the failure comes from `bytes` being absent from the listing shape in `src/product/repo.ts`. Change the question and this assertion changes with it, which is the property that separates a real red from a missing file. Until the spec above is actually written, a run of this command will pass and record nothing — the deliverable here is the failing assertion, and naming the file is only where it goes.

**What a green here does not settle.** It proves the size can be carried cheaply. It says nothing about whether a reader shown the size stops issuing over-cap reads — that is this candidate's real bet, it is usability, and no exit code observes it. It also says nothing about the vault's node listing, which is a separate reader with a separate cap.

**Lane: not declared here, deliberately.** The question is mechanical and the instrument above is the whole of it, but the sweep that created this node lists it in the needs-a-person lane, and no call on the unattended surface can move it — the permissive label is a human's `ost-agent lane --set`. Stating "compute-only" in prose would assert a permission nothing granted and put the node's own body in conflict with its field.

## History
- 2026-08-31 body edited — The body opened with "**Lane: compute-only.**", which this surface cannot back. The sweep re-run immediately after creation lists this test under assumptionWork.needsHumans, so the prose declaration and the node's actual lane disagree — the exact two-answers-to-one-question state the ruleset's lane-conflict rule refuses, and this pass holds no ost_check to detect it and no call that can set the permissive lane (that is a human's `ost-agent lane --set`). Removing the claim rather than leaving prose asserting a permission nothing granted. Nothing else changed: the three assertions the spec must carry, the red-today reasoning and the what-this-does-not-settle paragraph are reproduced verbatim.
