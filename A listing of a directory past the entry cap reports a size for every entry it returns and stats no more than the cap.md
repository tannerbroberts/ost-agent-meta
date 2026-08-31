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

**The instrument is GREEN today, and that is a defect in it — stated plainly rather than claimed otherwise.** `test/product/repo.test.ts` exists and passes, so running the command as it stands proves nothing and grants no permit. The three assertions above have not been written into it. The rule is that an instrument must be red when it is written; this one is not, and it becomes a real test only once assertion 1 is in that file, where it will fail on `bytes` being `undefined` in the listing shape returned by `src/product/repo.ts`.

**Why this form rather than a path that does not exist.** A command naming an unwritten spec file does go red — identically, for every question anyone could write on it — which is filed as `no-spec`, grants no permit either, and tells a builder only "create this file." Naming the existing suite that already covers `readProductRepo` at least puts the assertions where they belong and makes the red, once written, specific to this question: reword the question and assertion 1 changes with it. Neither form is a valid red from a surface that cannot write to the repository, and the deliverable here is the failing assertion, not the path.

**What a green here does not settle.** Once the assertions exist and pass, it proves the size can be carried cheaply. It says nothing about whether a reader shown the size stops issuing over-cap reads — that is this candidate's real bet, it is usability, and no exit code observes it. It also says nothing about the vault's node listing, which is a separate reader with a separate cap.

**Lane: not declared here, deliberately.** The question is mechanical and the instrument above is the whole of it, but the sweep that created this node lists it in the needs-a-person lane, and no call on the unattended surface can move it — the permissive label is a human's `ost-agent lane --set`. Stating "compute-only" in prose would assert a permission nothing granted and put the node's own body in conflict with its field.

## History
- 2026-08-31 body edited — The body opened with "**Lane: compute-only.**", which this surface cannot back. The sweep re-run immediately after creation lists this test under assumptionWork.needsHumans, so the prose declaration and the node's actual lane disagree — the exact two-answers-to-one-question state the ruleset's lane-conflict rule refuses, and this pass holds no ost_check to detect it and no call that can set the permissive lane (that is a human's `ost-agent lane --set`). Removing the claim rather than leaving prose asserting a permission nothing granted. Nothing else changed: the three assertions the spec must carry, the red-today reasoning and the what-this-does-not-settle paragraph are reproduced verbatim.
- 2026-08-31 body edited — Self-check before reporting caught a contradiction this pass introduced: the paragraph was headed "Why it is red today and red about this specifically" and the next sentence conceded the command currently passes. Both cannot be true. The instrument names a spec file that exists and is green, so the command is GREEN today, not red — a reader taking the heading at face value would believe a permit exists that does not. Replacing the false claim with an accurate statement of the instrument's state and why this form was chosen over a non-existent path. No assertion, threshold or limitation was altered.
